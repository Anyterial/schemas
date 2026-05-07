# Anyterial space group symmetry fields (entrytype)

This page documents an [OPTIMADE](https://www.optimade.org/) [Entrytype Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/entrytypes/spacegroups`](https://schemas.anyterial.se/defs/v0.1/entrytypes/spacegroups.md)**  
**Definition name:** `spacegroups`

**Entrytype name:** Anyterial space group symmetry fields  
  

**Formats:** [[JSON](spacegroups.json)] [[MD](spacegroups.md)]

This entrytype defines the following properties:

* **[ID](https://schemas.optimade.org/defs/v1.2/properties/core/id.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/id`](https://schemas.optimade.org/defs/v1.2/properties/core/id.md)  
  A unique string referencing a specific entry in the database.

    **Requirements/Conventions:**  

    - **Support:** MUST be supported by all implementations, MUST NOT be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MUST always be included in the response.
    - Taken together, the ID and entry type MUST uniquely identify the entry.
    - Reasonably short IDs are encouraged and SHOULD NOT be longer than 255 characters.
    - IDs MAY change over time.


* **[type](https://schemas.optimade.org/defs/v1.2/properties/core/type.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/type`](https://schemas.optimade.org/defs/v1.2/properties/core/type.md)  
  The name of the type of an entry.

    **Requirements/Conventions:**  

    - **Support:** MUST be supported by all implementations, MUST NOT be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MUST always be included in the response.
    - MUST be an existing entry type.
    - The entry of type <type> and ID <id> MUST be returned in response to a request for /<type>/<id> under the versioned or unversioned base URL serving the API.


* **[immutable ID (immutable_id)](https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id`](https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id.md)  
  The entry's immutable ID (e.g., a UUID).

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MAY be included by default in the response.
    - This is important for databases having preferred IDs that point to "the latest version" of a record, but still offer access to older variants.
    - This ID maps to the version-specific record, in case it changes in the future.


* **[last modified (last_modified)](https://schemas.optimade.org/defs/v1.2/properties/core/last_modified.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/last_modified`](https://schemas.optimade.org/defs/v1.2/properties/core/last_modified.md)  
  Date and time representing when the entry was last modified.

    **Requirements/Conventions:**  

    - **Support:** SHOULD be supported by all implementations, i.e., SHOULD NOT be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MUST be included by default in the response.

* **[Asymmetric unit (asu)](../properties/spacegroups/asu.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu.md)  
  Direct-space asymmetric unit for the space-group setting, represented as a bounded non-recursive set of half-space cuts and boundary ownership rules.
The representation is equivalent to the recursive cctbx direct-space ASU cut expression documented by Grosse-Kunstleve et al., Acta Cryst. A67, 269 (2011), but stores the volume, face, edge, and vertex rules in separate fixed-depth tables.
A point is inside the ASU volume only if all `volume_cuts` pass.
Each volume cut tests an oriented plane from `planes`: a positive plane value includes the point, a negative value excludes it, and an exactly zero value uses `when_zero`.
Boundary rules are disjunctive normal form rule tables: the outer `dnf` list is OR, each inner list is AND, and each term tests one oriented plane and uses its own `on_zero` action.
Face rules may descend to edge rules on equality, edge rules may descend to vertex rules on equality, and vertex rules terminate with include or exclude actions.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The original cctbx-style recursive data structure can be recovered from this bounded representation with the following routine:
    
    ```python
    def bounded_asu_to_cctbx_recursive_data(bounded):
        planes = {plane["id"]: plane for plane in bounded["planes"]}
        rules = {level: {rule["id"]: rule for rule in bounded[f"{level}_rules"]}
                 for level in ("face", "edge", "vertex")}
    
        def expr_from_terms(terms, op):
            out = terms[0] if terms else None
            for term in terms[1:]:
                out = {"kind": "expr", "op": op, "lhs": out, "rhs": term}
            return out
    
        def expr_from_rule(level, rule_id):
            clauses = []
            for clause in rules[level][rule_id]["dnf"]:
                terms = [cut_from_action(t["plane_id"], t["on_zero"], level)
                         for t in clause]
                clauses.append(expr_from_terms(terms, "&"))
            return expr_from_terms(clauses, "|")
    
        def cut_from_action(plane_id, action, level):
            plane = planes[plane_id]
            if action["action"] in ("include", "exclude"):
                condition = None
                inclusive = action["action"] == "include"
            else:
                next_level = {"volume": "face", "face": "edge", "edge": "vertex"}[level]
                condition = expr_from_rule(next_level, action["rule_id"])
                inclusive = True
            return {
                "kind": "cut",
                "normal": plane["normal"],
                "const": plane["const"],
                "inclusive": inclusive,
                "condition": condition,
            }
    
        return {
            "cuts": [cut_from_action(cut["plane_id"], cut["when_zero"], "volume")
                     for cut in bounded["volume_cuts"]],
            "shape_only_cuts": [
                {
                    "kind": "cut",
                    "normal": planes[cut["plane_id"]]["normal"],
                    "const": planes[cut["plane_id"]]["const"],
                    "inclusive": True,
                    "condition": None,
                }
                for cut in bounded["volume_cuts"]
            ],
        }
    ```
    
    **Requirements/Conventions**:
    
    - It MUST be a dictionary with the following keys:
    
        - **planes**: REQUIRED; List of dictionaries.
          Registry of all oriented affine planes used by volume cuts and boundary rules.
          The plane value is `normal[0]*x + normal[1]*y + normal[2]*z + const` in fractional coordinates.
          The positive side of the plane is the inside half-space for the corresponding cut term.
    
        - **volume\_cuts**: REQUIRED; List of dictionaries.
          Top-level volume cuts combined as one conjunction.
          Each volume cut references one plane and gives explicit actions for positive, negative, and zero plane values.
    
        - **face\_rules**: REQUIRED; List of dictionaries.
          Rule table for two-dimensional face-boundary ownership.
          Face rules are evaluated only when a volume cut plane value is exactly zero.
    
        - **edge\_rules**: REQUIRED; List of dictionaries.
          Rule table for one-dimensional edge-boundary ownership.
          Edge rules are evaluated only after a volume cut and a face-level term both evaluate exactly to zero.
    
        - **vertex\_rules**: REQUIRED; List of dictionaries.
          Terminal rule table for zero-dimensional vertex-boundary ownership.
          Vertex rules cannot descend to another rule level.


* **[Asymmetric unit string (asu_str)](../properties/spacegroups/asu_str.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str.md)  
  Plain string rendering of the asymmetric-unit restrictions for the space-group setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Shape-only asymmetric unit string (asu_shape_only_str)](../properties/spacegroups/asu_shape_only_str.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_str`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_str.md)  
  Plain string rendering of the geometric shape part of the asymmetric-unit restrictions, without conditional refinements.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Bravais Type (bravais_type)](../properties/spacegroups/bravais_type.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type.md)  
  The Bravais type of the translational lattice.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The symbol consists of a lower-case crystal-system letter followed by an upper-case centring symbol, using setting-independent `mS` and `oS` for monoclinic and orthorhombic side-centred lattices.


* **[Cctbx Fft Grid Factors (cctbx_fft_grid_factors)](../properties/spacegroups/cctbx_fft_grid_factors.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors.md)  
  FFT grid-factor recommendations derived from cctbx for the space group, its structure seminvariants, and its Euclidean normalizer.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Centering translations (centering_translations)](../properties/spacegroups/centering_translations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations.md)  
  Centering translations of the conventional cell.
Each list member is one exact fractional-coordinate centering translation as defined by `/properties/symmetry/centering_translation`.
The zero translation `(0,0,0)` is listed first.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Centering translations as xyz strings (centering_translations_xyz)](../properties/spacegroups/centering_translations_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations_xyz.md)  
  Centering translations of the conventional cell, represented as `x,y,z`-style coordinate shifts. The zero translation is listed first.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Centring Type (centring_type)](../properties/spacegroups/centring_type.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type.md)  
  The lattice centring symbol for the crystallographic setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    This setting-dependent symbol identifies primitive, face-centred, body-centred, rhombohedral, or hexagonal centring as represented in the setting record.


* **[Crystal System (crystal_system)](../properties/spacegroups/crystal_system.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/crystal_system`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/crystal_system.md)  
  The crystal system of the space group or point group.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Values use the conventional crystallographic system names such as triclinic, monoclinic, orthorhombic, tetragonal, trigonal, hexagonal, and cubic.


* **[Hall Symbol (hall)](../properties/spacegroups/hall.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall.md)  
  The Hall symbol for a crystallographic space-group setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Hall symbols encode the generators and origin choice of a space-group setting in a form intended to identify the setting unambiguously. In the Anyterial symmetry data, this property is the plain ASCII Hall symbol corresponding to the Hall-keyed record.


* **[Hall Aliases (hall_aliases)](../properties/spacegroups/hall_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases.md)  
  Alternate ASCII Hall symbols or Hall-setting keys associated with the same generated setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Aliases capture duplicate or equivalent Hall-table forms that identify the same setting in the generated tables.
    
    **Requirements/Conventions**:
    
    - The preferred display symbol is stored in `hall`.
    - Alias values SHOULD NOT be assumed to be unique across all settings without also considering the setting key.


* **[Hall entry (hall_entry)](../properties/spacegroups/hall_entry.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry.md)  
  Normalized Hall-table entry key used internally by the generated datasets.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The value is derived from the Hall symbol by using lowercase letters and underscores in place of spaces. It is stable for lookup within these data files, while the display Hall symbol is provided separately by `hall` and its formatted variants.
    
    **Requirements/Conventions**:
    
    - This field identifies a concrete Hall setting, not only an IT space-group type.
    - The same value is normally used as the key of the containing `spacegroups` map.


* **[Hermann-Mauguin Entry (hm_entry)](../properties/spacegroups/hm_entry.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry.md)  
  The Hermann-Mauguin entry label for a conventional space-group setting from table A1.4.2.7 of the [International Tables for Crystallography (2006). Volume B, Reciprocal space. ISBN: 978-0-7923-6592-1, doi:10.1107/97809553602060000102](https://doi.org/10.1107/97809553602060000102).

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The symbol is a full Hermann-Mauguin-style setting label, except that:
    
    * The older glide-plane letters are used, rather than the newer `e` notation introduced in the Fourth Edition of the International Tables for Crystallography (1995) for the space groups Aem2 (39), Aea2 (41), Cmce (64), Cmme (67) and Ccce (68).
    * When necessary to disambiguate the 530 conventional settings, an origin-choice suffix (`:1`, `:2`) is used.
    
    **Requirements/Conventions**:
    
    - The value MUST be written as a plain string with spaces between Hermann-Mauguin symbol parts.
    - The disambiguation suffix MUST be a colon `:`  and an integer appended to the string without whitespace, for example `:1` or `:2`.


* **[Harker planes (harker_planes)](../properties/spacegroups/harker_planes.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/harker_planes`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/harker_planes.md)  
  Harker planes of the space group in fractional Patterson coordinates, as generated by cctbx.
Each entry describes one plane or special-position condition with an expression and optional exact normal, point, and constant data.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Hermann-Mauguin Cctbx Universal (hm_cctbx_universal)](../properties/spacegroups/hm_cctbx_universal.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_cctbx_universal`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_cctbx_universal.md)  
  Universal Hermann-Mauguin symbol returned by cctbx for this setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    This field records the cctbx-internal universal symbol used during generation. It is useful for diagnostics and for tracing generator behavior, but it is not the International Tables preferred symbol. Prefer `hm_short`, `hm_full`, and `hm_extended` for table-facing symbol data.


* **[Extended Hermann-Mauguin Symbol (hm_extended)](../properties/spacegroups/hm_extended.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended.md)  
  The setting-specific extended Hermann-Mauguin symbol for the space-group setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Extended Hermann-Mauguin symbols give additional symmetry-element information compared with the short symbol. Multi-line values preserve line breaks and spacing used to align the extended symbol components.


* **[Hermann-Mauguin Extended Aliases (hm_extended_aliases)](../properties/spacegroups/hm_extended_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases.md)  
  Alternate ASCII forms of `hm_extended` that are accepted for the same generated setting. The preferred symbol is stored in `hm_extended`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Hermann-Mauguin Extended Old (hm_extended_old)](../properties/spacegroups/hm_extended_old.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_old.md)  
  The older extended Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Hermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.
    
    **Requirements/Conventions**:
    
    - The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.
    - The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.
    - Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.


* **[Full Hermann-Mauguin Symbol (hm_full)](../properties/spacegroups/hm_full.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full.md)  
  The setting-specific full Hermann-Mauguin symbol for the space-group setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The full symbol expands the short Hermann-Mauguin notation to include the symmetry entries for all relevant crystallographic directions in the setting represented by the containing Hall record.


* **[Hermann-Mauguin Full Aliases (hm_full_aliases)](../properties/spacegroups/hm_full_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases.md)  
  Alternate ASCII forms of `hm_full` that are accepted for the same generated setting. The preferred symbol is stored in `hm_full`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Hermann-Mauguin Full Old (hm_full_old)](../properties/spacegroups/hm_full_old.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_old.md)  
  The older full Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Hermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.
    
    **Requirements/Conventions**:
    
    - The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.
    - The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.
    - Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.


* **[Hermann-Mauguin Full Std (hm_full_std)](../properties/spacegroups/hm_full_std.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std.md)  
  The International Tables standard full Hermann-Mauguin symbol for the space-group type.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Hermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.
    
    **Requirements/Conventions**:
    
    - The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.
    - The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.
    - Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.


* **[Short Hermann-Mauguin Symbol (hm_short)](../properties/spacegroups/hm_short.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short.md)  
  The setting-specific short Hermann-Mauguin symbol for the space-group setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    This field gives the concise Hermann-Mauguin notation used for the concrete Hall setting represented by the containing record. It is compatible with OPTIMADE's `space_group_symbol_hermann_mauguin` when used as the conventional short Hermann-Mauguin symbol.


* **[Hermann-Mauguin Short Aliases (hm_short_aliases)](../properties/spacegroups/hm_short_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases.md)  
  Alternate ASCII forms of `hm_short` that are accepted for the same generated setting. The preferred symbol is stored in `hm_short`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Hermann-Mauguin Short Old (hm_short_old)](../properties/spacegroups/hm_short_old.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old.md)  
  The older short Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Hermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.
    
    **Requirements/Conventions**:
    
    - The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.
    - The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.
    - Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.


* **[Hermann-Mauguin Short Std (hm_short_std)](../properties/spacegroups/hm_short_std.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std.md)  
  The International Tables standard short Hermann-Mauguin symbol for the space-group type.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Hermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.
    
    **Requirements/Conventions**:
    
    - The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.
    - The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.
    - Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.


* **[Is Centric (is_centric)](../properties/spacegroups/is_centric.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric.md)  
  Boolean flag indicating whether the cctbx space group is centric.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Is Chiral (is_chiral)](../properties/spacegroups/is_chiral.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral.md)  
  Boolean flag indicating whether the space group is chiral.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Is Enantiomorphic (is_enantiomorphic)](../properties/spacegroups/is_enantiomorphic.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic.md)  
  Boolean flag indicating whether the space-group type belongs to an enantiomorphic pair.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Is Reference Setting (is_reference_setting)](../properties/spacegroups/is_reference_setting.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting.md)  
  Boolean flag indicating whether this Hall setting is the selected reference setting for its International Tables space-group number.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[International Tables Coordinate-System Code (it_coordinate_system_code)](../properties/spacegroups/it_coordinate_system_code.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code.md)  
  The International Tables coordinate-system code for the setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The code distinguishes setting choices such as monoclinic unique-axis and cell choices, orthorhombic axis settings, tetragonal/cubic origin choices, and trigonal hexagonal or rhombohedral axes.


* **[International Tables Space-Group Number (it_number)](../properties/spacegroups/it_number.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number.md)  
  The International Tables space-group number.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    This integer identifies the space-group type numbered 1 through 230 in International Tables for Crystallography. Multiple Hall settings can share the same `it_number`.


* **[It Number Enantiomorphic (it_number_enantiomorphic)](../properties/spacegroups/it_number_enantiomorphic.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic.md)  
  International Tables number of the enantiomorphic partner space group, when one exists. The value is null for space groups without a distinct enantiomorphic partner.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Laue Class (laue_class)](../properties/spacegroups/laue_class.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/laue_class`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/laue_class.md)  
  The Laue class associated with the space group or point group.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The Laue class groups point groups that become equivalent when inversion symmetry is included.


* **[N Centering Translations (n_centering_translations)](../properties/spacegroups/n_centering_translations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_centering_translations`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_centering_translations.md)  
  Number of centering translations in the conventional cell of the space-group setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[N Pointgroup Symops (n_pointgroup_symops)](../properties/spacegroups/n_pointgroup_symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_pointgroup_symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_pointgroup_symops.md)  
  Number of point-group symmetry operations represented by the space group, excluding centering translations.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[N Symops (n_symops)](../properties/spacegroups/n_symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops.md)  
  Number of symmetry operations in the finite operation list of the generated entry.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Point-Group Hermann-Mauguin Symbol (point_group)](../properties/spacegroups/point_group.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group.md)  
  The Hermann-Mauguin point-group symbol associated with the space group.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    This field identifies the crystallographic point group obtained from the space group by removing translational components.


* **[Schoenflies Symbol (schoenflies)](../properties/spacegroups/schoenflies.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies.md)  
  The Schoenflies symbol for the space-group type.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The ASCII form follows the CIF convention for `_space_group.name_Schoenflies`, using a period to separate the Schoenflies point-group symbol from the superscript index.


* **[Setting](../properties/spacegroups/setting.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting.md)  
  Setting suffix or setting annotation extracted from the cctbx universal Hermann-Mauguin symbol.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    This value is a compact textual description of the coordinate setting portion of the cctbx symbol, for example an origin choice or axis-setting annotation. It is primarily an auxiliary generator field and SHOULD NOT be used as a substitute for the International Tables `setting_it_nc` identifier.


* **[International Tables setting code n:c (setting_it_nc)](../properties/spacegroups/setting_it_nc.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc.md)  
  International Tables setting identifier in `n:c` notation.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The part before the colon is the International Tables space-group number. The part after the colon is the coordinate-system or origin-choice qualifier used to distinguish settings that share the same IT number.
    
    **Requirements/Conventions**:
    
    - Triclinic, hexagonal, and many unique settings use only the IT number, for example `1`.
    - Monoclinic settings use qualifiers such as `b1`, `-b1`, `c2`, or `a3`.
    - Orthorhombic settings use qualifiers such as `abc`, `cab`, `1abc`, or `2bca` when needed.
    - Tetragonal and cubic origin choices use qualifiers such as `1` and `2`; trigonal axis choices use qualifiers such as `h` and `r`.


* **[International Tables setting-code aliases (setting_it_nc_aliases)](../properties/spacegroups/setting_it_nc_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases.md)  
  Alternative International Tables `n:c` setting identifiers that refer to the same Hall setting or are otherwise treated as aliases of `setting_it_nc` by the generator. This field is used only when the source tables expose more than one conventional label for the same generated setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Setting Plaintext (setting_plaintext)](../properties/spacegroups/setting_plaintext.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext.md)  
  Human-readable description of the International Tables coordinate-system setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    This field expands `setting_it_nc` into a short phrase such as a monoclinic unique-axis and cell-choice description, an orthorhombic axis permutation, or an origin-choice description.


* **[Space-group symbols (spacegroup_symbols)](../properties/spacegroups/spacegroup_symbols.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols.md)  
  Ordered table of conventional space-group symbol rows.
Each row describes one Hall setting where the International Tables symbol data is available, including the IT coordinate-system code, Hall symbol, IT number, and Hermann-Mauguin symbols.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary SHOULD contain the setting identifier `setting_it_nc`, the Hall symbol `hall`, the International Tables number `it_number`, and the setting-specific Hermann-Mauguin symbols `hm_short`, `hm_full`, and `hm_extended` when available.
    - The order SHOULD follow the conventional ITA/Hall setting order used by the generated `symmetry_basics` space-group table.


* **[Spglib Hall (spglib_hall)](../properties/spacegroups/spglib_hall.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall.md)  
  Hall setting selected by spglib for the space-group type or setting, represented as a normalized Hall key.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Spglib Hall Numbers (spglib_hall_numbers)](../properties/spacegroups/spglib_hall_numbers.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers.md)  
  spglib Hall numbers corresponding to the generated setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Structure Seminvariants (structure_seminvariants)](../properties/spacegroups/structure_seminvariants.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants.md)  
  Structure seminvariant vectors and moduli for the space-group setting. These characterize phase restrictions and FFT grid constraints associated with the symmetry.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Symmetry operations (symops)](../properties/spacegroups/symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops.md)  
  Full list of symmetry-operation descriptors for a space-group setting.
Each list member is a `op` object as defined by `/properties/symmetry/op`.
For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.


* **[Symmetry operations modulo centering translations (symops_mod_centering)](../properties/spacegroups/symops_mod_centering.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering.md)  
  Representative symmetry-operation descriptors modulo centering translations.
Each list member is a `op` object as defined by `/properties/symmetry/op`.
For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.


* **[Symmetry operations modulo centering in x,y,z notation (symops_mod_centering_xyz)](../properties/spacegroups/symops_mod_centering_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering_xyz.md)  
  Symmetry operations modulo centering translations in fractional `x,y,z` notation, ordered consistently with `symops_mod_centering`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Symmetry operation generators (symops_generators)](../properties/spacegroups/symops_generators.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators.md)  
  Minimal generator subset of the full symmetry-operation group for a space-group setting.
Each list member is a `op` object as defined by `/properties/symmetry/op`.
For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.


* **[Symops Generators Xyz (symops_generators_xyz)](../properties/spacegroups/symops_generators_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz.md)  
  Minimal generator subset of the full symmetry-operation group in fractional `x,y,z` notation, ordered consistently with `symops_generators`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Representative symmetry operations (symops_representative)](../properties/spacegroups/symops_representative.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative.md)  
  Representative symmetry-operation descriptors modulo centering translations.
Each list member is a `op` object as defined by `/properties/symmetry/op`.
For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.


* **[Symops Representative Xyz (symops_representative_xyz)](../properties/spacegroups/symops_representative_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative_xyz.md)  
  Representative symmetry operations modulo centering translations in fractional `x,y,z` notation, ordered consistently with `symops_representative`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Symmetry operations in x,y,z notation (symops_xyz)](../properties/spacegroups/symops_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_xyz.md)  
  Full list of symmetry operations for the space-group setting written in fractional `x,y,z` coordinate notation. Each expression acts on fractional coordinates in the setting represented by the containing Hall entry.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Wyckoff positions (wyckoff)](../properties/spacegroups/wyckoff.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff.md)  
  Wyckoff-position table for a specific space-group setting.
Each list item describes one Wyckoff position and includes the Wyckoff letter as ordinary data.
This list representation avoids using JSON dictionary keys as crystallographic data.
Items follow `/properties/symmetry/wyckoff_position`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each item MUST include `letter`, identifying the Wyckoff letter for that position in the setting.
    - `orbit_affine` and `orbit_xyz` contain the full orbit.
    - `orbit_mod_centering_affine` and `orbit_mod_centering_xyz` contain one representative modulo centering translations.


* **[Wyckoff Sets (wyckoff_sets)](../properties/spacegroups/wyckoff_sets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets.md)  
  Sets of Wyckoff letters related by normalizer operations. Each inner list groups Wyckoff positions that can be interchanged by the relevant normalizer action.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Asymmetric unit markups (asu_markup)](../properties/spacegroups/asu_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_markup.md)  
  Display-oriented renderings of the plain-string asymmetric-unit restrictions in `asu_str`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Shape-only asymmetric unit markups (asu_shape_only_markup)](../properties/spacegroups/asu_shape_only_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_markup.md)  
  Display-oriented renderings of the plain-string shape-only asymmetric-unit restrictions in `asu_shape_only_str`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Hall symbol markups (hall_markup)](../properties/spacegroups/hall_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_markup.md)  
  Display-oriented renderings of the Hall symbol in `hall`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Hall alias markups (hall_aliases_markup)](../properties/spacegroups/hall_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases_markup.md)  
  Display-oriented renderings corresponding element-by-element to the alternate Hall symbols in `hall_aliases`.
The plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Short Hermann-Mauguin symbol markups (hm_short_markup)](../properties/spacegroups/hm_short_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_markup.md)  
  Display-oriented renderings of the setting-specific short Hermann-Mauguin symbol in `hm_short`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Standard short Hermann-Mauguin symbol markups (hm_short_std_markup)](../properties/spacegroups/hm_short_std_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std_markup.md)  
  Display-oriented renderings of the ITA-standard short Hermann-Mauguin symbol in `hm_short_std`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Full Hermann-Mauguin symbol markups (hm_full_markup)](../properties/spacegroups/hm_full_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_markup.md)  
  Display-oriented renderings of the setting-specific full Hermann-Mauguin symbol in `hm_full`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Standard full Hermann-Mauguin symbol markups (hm_full_std_markup)](../properties/spacegroups/hm_full_std_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std_markup.md)  
  Display-oriented renderings of the ITA-standard full Hermann-Mauguin symbol in `hm_full_std`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Extended Hermann-Mauguin symbol markups (hm_extended_markup)](../properties/spacegroups/hm_extended_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_markup.md)  
  Display-oriented renderings of the extended Hermann-Mauguin symbol in `hm_extended`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Short Hermann-Mauguin alias markups (hm_short_aliases_markup)](../properties/spacegroups/hm_short_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases_markup.md)  
  Display-oriented renderings corresponding element-by-element to the alternate short Hermann-Mauguin symbols in `hm_short_aliases`.
The plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Full Hermann-Mauguin alias markups (hm_full_aliases_markup)](../properties/spacegroups/hm_full_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases_markup.md)  
  Display-oriented renderings corresponding element-by-element to the alternate full Hermann-Mauguin symbols in `hm_full_aliases`.
The plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Extended Hermann-Mauguin alias markups (hm_extended_aliases_markup)](../properties/spacegroups/hm_extended_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases_markup.md)  
  Display-oriented renderings corresponding element-by-element to the alternate extended Hermann-Mauguin symbols in `hm_extended_aliases`.
The plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Schoenflies symbol markups (schoenflies_markup)](../properties/spacegroups/schoenflies_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies_markup.md)  
  Display-oriented renderings of the Schoenflies symbol in `schoenflies`.
The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.


**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/entrytypes/spacegroups",
    "$schema": "https://schemas.optimade.org/meta/v1.2/optimade/entrytype_definition.json",
    "type": "object",
    "title": "Anyterial space group symmetry fields",
    "x-optimade-definition": {
        "kind": "entrytype",
        "format": "1.3",
        "version": "0.1.0",
        "name": "spacegroups",
        "label": "spacegroups_entrytype_anyterial"
    },
    "properties": {
        "id": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/id",
            "x-optimade-requirements": {
                "support": "must",
                "sortable": true,
                "query-support": "all mandatory",
                "response-level": "always"
            },
            "title": "ID",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "label": "id_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "id"
            },
            "type": [
                "string"
            ],
            "description": "A unique string referencing a specific entry in the database.\n\n**Requirements/Conventions:**\n\n- Taken together, the ID and entry type MUST uniquely identify the entry.\n- Reasonably short IDs are encouraged and SHOULD NOT be longer than 255 characters.\n- IDs MAY change over time.",
            "examples": [
                "db/1234567",
                "cod/2000000",
                "cod/2000000@1234567",
                "nomad/L1234567890",
                "42"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "type": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/type",
            "x-optimade-requirements": {
                "support": "must",
                "sortable": true,
                "query-support": "all mandatory",
                "response-level": "always"
            },
            "title": "type",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "label": "type_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "type"
            },
            "type": [
                "string"
            ],
            "description": "The name of the type of an entry.\n\n**Requirements/Conventions:**\n\n- MUST be an existing entry type.\n- The entry of type <type> and ID <id> MUST be returned in response to a request for /<type>/<id> under the versioned or unversioned base URL serving the API.",
            "examples": [
                "structures"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "immutable_id": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "all mandatory",
                "response-level": "may"
            },
            "title": "immutable ID",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "label": "immutable_id_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "immutable_id"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The entry's immutable ID (e.g., a UUID).\n\n**Requirements/Conventions:**\n\n- This is important for databases having preferred IDs that point to \"the latest version\" of a record, but still offer access to older variants.\n- This ID maps to the version-specific record, in case it changes in the future.",
            "examples": [
                "8bd3e750-b477-41a0-9b11-3a799f21b44f",
                "fjeiwoj,54;@=%<>#32"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "last_modified": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/last_modified",
            "x-optimade-requirements": {
                "support": "should",
                "sortable": false,
                "query-support": "all mandatory",
                "response-level": "must"
            },
            "title": "last modified",
            "x-optimade-type": "timestamp",
            "x-optimade-definition": {
                "label": "last_modified_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "last_modified"
            },
            "type": [
                "string",
                "null"
            ],
            "format": "date-time",
            "description": "Date and time representing when the entry was last modified.",
            "examples": [
                "2007-04-05T14:30:20Z"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "asu": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Asymmetric unit",
            "$comment": "Bounded non-recursive direct-space asymmetric-unit representation for one space-group setting.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "asu",
                "label": "asu_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Direct-space asymmetric unit for the space-group setting, represented as a bounded non-recursive set of half-space cuts and boundary ownership rules.\nThe representation is equivalent to the recursive cctbx direct-space ASU cut expression documented by Grosse-Kunstleve et al., Acta Cryst. A67, 269 (2011), but stores the volume, face, edge, and vertex rules in separate fixed-depth tables.\nA point is inside the ASU volume only if all `volume_cuts` pass.\nEach volume cut tests an oriented plane from `planes`: a positive plane value includes the point, a negative value excludes it, and an exactly zero value uses `when_zero`.\nBoundary rules are disjunctive normal form rule tables: the outer `dnf` list is OR, each inner list is AND, and each term tests one oriented plane and uses its own `on_zero` action.\nFace rules may descend to edge rules on equality, edge rules may descend to vertex rules on equality, and vertex rules terminate with include or exclude actions.\n\nThe original cctbx-style recursive data structure can be recovered from this bounded representation with the following routine:\n\n```python\ndef bounded_asu_to_cctbx_recursive_data(bounded):\n    planes = {plane[\"id\"]: plane for plane in bounded[\"planes\"]}\n    rules = {level: {rule[\"id\"]: rule for rule in bounded[f\"{level}_rules\"]}\n             for level in (\"face\", \"edge\", \"vertex\")}\n\n    def expr_from_terms(terms, op):\n        out = terms[0] if terms else None\n        for term in terms[1:]:\n            out = {\"kind\": \"expr\", \"op\": op, \"lhs\": out, \"rhs\": term}\n        return out\n\n    def expr_from_rule(level, rule_id):\n        clauses = []\n        for clause in rules[level][rule_id][\"dnf\"]:\n            terms = [cut_from_action(t[\"plane_id\"], t[\"on_zero\"], level)\n                     for t in clause]\n            clauses.append(expr_from_terms(terms, \"&\"))\n        return expr_from_terms(clauses, \"|\")\n\n    def cut_from_action(plane_id, action, level):\n        plane = planes[plane_id]\n        if action[\"action\"] in (\"include\", \"exclude\"):\n            condition = None\n            inclusive = action[\"action\"] == \"include\"\n        else:\n            next_level = {\"volume\": \"face\", \"face\": \"edge\", \"edge\": \"vertex\"}[level]\n            condition = expr_from_rule(next_level, action[\"rule_id\"])\n            inclusive = True\n        return {\n            \"kind\": \"cut\",\n            \"normal\": plane[\"normal\"],\n            \"const\": plane[\"const\"],\n            \"inclusive\": inclusive,\n            \"condition\": condition,\n        }\n\n    return {\n        \"cuts\": [cut_from_action(cut[\"plane_id\"], cut[\"when_zero\"], \"volume\")\n                 for cut in bounded[\"volume_cuts\"]],\n        \"shape_only_cuts\": [\n            {\n                \"kind\": \"cut\",\n                \"normal\": planes[cut[\"plane_id\"]][\"normal\"],\n                \"const\": planes[cut[\"plane_id\"]][\"const\"],\n                \"inclusive\": True,\n                \"condition\": None,\n            }\n            for cut in bounded[\"volume_cuts\"]\n        ],\n    }\n```\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **planes**: REQUIRED; List of dictionaries.\n      Registry of all oriented affine planes used by volume cuts and boundary rules.\n      The plane value is `normal[0]*x + normal[1]*y + normal[2]*z + const` in fractional coordinates.\n      The positive side of the plane is the inside half-space for the corresponding cut term.\n\n    - **volume\\_cuts**: REQUIRED; List of dictionaries.\n      Top-level volume cuts combined as one conjunction.\n      Each volume cut references one plane and gives explicit actions for positive, negative, and zero plane values.\n\n    - **face\\_rules**: REQUIRED; List of dictionaries.\n      Rule table for two-dimensional face-boundary ownership.\n      Face rules are evaluated only when a volume cut plane value is exactly zero.\n\n    - **edge\\_rules**: REQUIRED; List of dictionaries.\n      Rule table for one-dimensional edge-boundary ownership.\n      Edge rules are evaluated only after a volume cut and a face-level term both evaluate exactly to zero.\n\n    - **vertex\\_rules**: REQUIRED; List of dictionaries.\n      Terminal rule table for zero-dimensional vertex-boundary ownership.\n      Vertex rules cannot descend to another rule level.",
            "properties": {
                "planes": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Registry of oriented affine planes used by the ASU cuts and rules.",
                    "items": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object"
                        ],
                        "required": [
                            "id",
                            "normal",
                            "const"
                        ],
                        "description": "One oriented affine plane in fractional coordinates.",
                        "properties": {
                            "id": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "Stable identifier used by `volume_cuts` and rule terms to refer to this plane."
                            },
                            "normal": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_lattice"
                                    ],
                                    "sizes": [
                                        3
                                    ]
                                },
                                "type": [
                                    "array"
                                ],
                                "description": "The three exact rational coefficients multiplying `x`, `y`, and `z` in the plane equation.",
                                "items": {
                                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                    "title": "fraction",
                                    "x-optimade-type": "string",
                                    "x-optimade-definition": {
                                        "label": "fraction_core",
                                        "kind": "property",
                                        "version": "0.1.0",
                                        "format": "1.3",
                                        "name": "fraction"
                                    },
                                    "type": [
                                        "string",
                                        "null"
                                    ],
                                    "description": "A fraction represented as a string.",
                                    "examples": [
                                        "2/3",
                                        "5/42",
                                        "10",
                                        "0"
                                    ],
                                    "x-optimade-unit": "inapplicable"
                                }
                            },
                            "const": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                "title": "fraction",
                                "x-optimade-type": "string",
                                "x-optimade-definition": {
                                    "label": "fraction_core",
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "fraction"
                                },
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "A fraction represented as a string.",
                                "examples": [
                                    "2/3",
                                    "5/42",
                                    "10",
                                    "0"
                                ],
                                "x-optimade-unit": "inapplicable"
                            }
                        }
                    }
                },
                "volume_cuts": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Top-level ASU volume cuts, combined as an AND-list.",
                    "items": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object"
                        ],
                        "required": [
                            "id",
                            "plane_id",
                            "when_positive",
                            "when_negative",
                            "when_zero"
                        ],
                        "description": "One top-level oriented cut of the three-dimensional ASU volume.",
                        "properties": {
                            "id": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "Stable identifier for this volume cut."
                            },
                            "plane_id": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "Identifier of the plane tested by this volume cut."
                            },
                            "when_positive": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "enum": [
                                    "include"
                                ],
                                "description": "Action for positive plane values."
                            },
                            "when_negative": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "enum": [
                                    "exclude"
                                ],
                                "description": "Action for negative plane values."
                            },
                            "when_zero": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object"
                                ],
                                "required": [
                                    "action"
                                ],
                                "description": "Action for points exactly on the volume-cut plane.",
                                "properties": {
                                    "action": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "enum": [
                                            "include",
                                            "exclude",
                                            "evaluate_face_rule"
                                        ],
                                        "description": "Boundary action for this equality case."
                                    },
                                    "rule_id": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string",
                                            "null"
                                        ],
                                        "description": "Identifier of the face rule to evaluate when `action` is `evaluate_face_rule`."
                                    }
                                }
                            }
                        }
                    }
                },
                "face_rules": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Disjunctive-normal-form face-boundary ownership rules.",
                    "items": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object"
                        ],
                        "required": [
                            "id",
                            "dnf"
                        ],
                        "description": "One face-level ownership rule.",
                        "properties": {
                            "id": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "Stable identifier for this face rule."
                            },
                            "dnf": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array"
                                ],
                                "description": "OR-list of AND-lists of face-level terms.",
                                "items": {
                                    "x-optimade-type": "list",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "array"
                                    ],
                                    "description": "One AND-clause in the face-level rule.",
                                    "items": {
                                        "x-optimade-type": "dictionary",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "object"
                                        ],
                                        "required": [
                                            "plane_id",
                                            "on_zero"
                                        ],
                                        "description": "One face-level plane test.",
                                        "properties": {
                                            "plane_id": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string"
                                                ],
                                                "description": "Identifier of the plane tested by this term."
                                            },
                                            "on_zero": {
                                                "x-optimade-type": "dictionary",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "object"
                                                ],
                                                "required": [
                                                    "action"
                                                ],
                                                "description": "Action for points exactly on this face-level term plane.",
                                                "properties": {
                                                    "action": {
                                                        "x-optimade-type": "string",
                                                        "x-optimade-unit": "inapplicable",
                                                        "type": [
                                                            "string"
                                                        ],
                                                        "enum": [
                                                            "include",
                                                            "exclude",
                                                            "evaluate_edge_rule"
                                                        ],
                                                        "description": "Boundary action for this equality case."
                                                    },
                                                    "rule_id": {
                                                        "x-optimade-type": "string",
                                                        "x-optimade-unit": "inapplicable",
                                                        "type": [
                                                            "string",
                                                            "null"
                                                        ],
                                                        "description": "Identifier of the edge rule to evaluate when `action` is `evaluate_edge_rule`."
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                },
                "edge_rules": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Disjunctive-normal-form edge-boundary ownership rules.",
                    "items": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object"
                        ],
                        "required": [
                            "id",
                            "dnf"
                        ],
                        "description": "One edge-level ownership rule.",
                        "properties": {
                            "id": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "Stable identifier for this edge rule."
                            },
                            "dnf": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array"
                                ],
                                "description": "OR-list of AND-lists of edge-level terms.",
                                "items": {
                                    "x-optimade-type": "list",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "array"
                                    ],
                                    "description": "One AND-clause in the edge-level rule.",
                                    "items": {
                                        "x-optimade-type": "dictionary",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "object"
                                        ],
                                        "required": [
                                            "plane_id",
                                            "on_zero"
                                        ],
                                        "description": "One edge-level plane test.",
                                        "properties": {
                                            "plane_id": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string"
                                                ],
                                                "description": "Identifier of the plane tested by this term."
                                            },
                                            "on_zero": {
                                                "x-optimade-type": "dictionary",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "object"
                                                ],
                                                "required": [
                                                    "action"
                                                ],
                                                "description": "Action for points exactly on this edge-level term plane.",
                                                "properties": {
                                                    "action": {
                                                        "x-optimade-type": "string",
                                                        "x-optimade-unit": "inapplicable",
                                                        "type": [
                                                            "string"
                                                        ],
                                                        "enum": [
                                                            "include",
                                                            "exclude",
                                                            "evaluate_vertex_rule"
                                                        ],
                                                        "description": "Boundary action for this equality case."
                                                    },
                                                    "rule_id": {
                                                        "x-optimade-type": "string",
                                                        "x-optimade-unit": "inapplicable",
                                                        "type": [
                                                            "string",
                                                            "null"
                                                        ],
                                                        "description": "Identifier of the vertex rule to evaluate when `action` is `evaluate_vertex_rule`."
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                },
                "vertex_rules": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Disjunctive-normal-form terminal vertex-boundary ownership rules.",
                    "items": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object"
                        ],
                        "required": [
                            "id",
                            "dnf"
                        ],
                        "description": "One terminal vertex-level ownership rule.",
                        "properties": {
                            "id": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "Stable identifier for this vertex rule."
                            },
                            "dnf": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array"
                                ],
                                "description": "OR-list of AND-lists of terminal vertex-level terms.",
                                "items": {
                                    "x-optimade-type": "list",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "array"
                                    ],
                                    "description": "One AND-clause in the vertex-level rule.",
                                    "items": {
                                        "x-optimade-type": "dictionary",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "object"
                                        ],
                                        "required": [
                                            "plane_id",
                                            "on_zero"
                                        ],
                                        "description": "One terminal vertex-level plane test.",
                                        "properties": {
                                            "plane_id": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string"
                                                ],
                                                "description": "Identifier of the plane tested by this term."
                                            },
                                            "on_zero": {
                                                "x-optimade-type": "dictionary",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "object"
                                                ],
                                                "required": [
                                                    "action"
                                                ],
                                                "description": "Terminal action for points exactly on this vertex-level term plane.",
                                                "properties": {
                                                    "action": {
                                                        "x-optimade-type": "string",
                                                        "x-optimade-unit": "inapplicable",
                                                        "type": [
                                                            "string"
                                                        ],
                                                        "enum": [
                                                            "include",
                                                            "exclude"
                                                        ],
                                                        "description": "Terminal boundary action for this equality case."
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            },
            "examples": [
                {
                    "planes": [
                        {
                            "id": "p0",
                            "normal": [
                                "1",
                                "0",
                                "0"
                            ],
                            "const": "0"
                        },
                        {
                            "id": "p1",
                            "normal": [
                                "-1",
                                "0",
                                "0"
                            ],
                            "const": "1"
                        }
                    ],
                    "volume_cuts": [
                        {
                            "id": "v0",
                            "plane_id": "p0",
                            "when_positive": "include",
                            "when_negative": "exclude",
                            "when_zero": {
                                "action": "include"
                            }
                        },
                        {
                            "id": "v1",
                            "plane_id": "p1",
                            "when_positive": "include",
                            "when_negative": "exclude",
                            "when_zero": {
                                "action": "exclude"
                            }
                        }
                    ],
                    "face_rules": [],
                    "edge_rules": [],
                    "vertex_rules": []
                }
            ]
        },
        "asu_str": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Asymmetric unit string",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "asu_str",
                "label": "asu_str_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Plain string rendering of the asymmetric-unit restrictions for the space-group setting.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "x>=0; x<1; y>=0; y<1; z>=0; z<1",
                "x>=0 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]; x<=1/2 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]; y>=0; y<1; z>=0; z<1"
            ]
        },
        "asu_shape_only_str": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_str",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Shape-only asymmetric unit string",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "asu_shape_only_str",
                "label": "asu_shape_only_str_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Plain string rendering of the geometric shape part of the asymmetric-unit restrictions, without conditional refinements.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "x>=0; x<=1; y>=0; y<=1; z>=0; z<=1",
                "x>=0; x<=1/2; y>=0; y<=1; z>=0; z<=1"
            ]
        },
        "bravais_type": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Bravais Type",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.Bravais_type.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "bravais_type",
                "label": "bravais_type_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The Bravais type of the translational lattice.\n\nThe symbol consists of a lower-case crystal-system letter followed by an upper-case centring symbol, using setting-independent `mS` and `oS` for monoclinic and orthorhombic side-centred lattices.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "aP",
                "mS"
            ]
        },
        "cctbx_fft_grid_factors": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Cctbx Fft Grid Factors",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "cctbx_fft_grid_factors",
                "label": "cctbx_fft_grid_factors_spacegroups"
            },
            "type": [
                "object",
                "null"
            ],
            "description": "FFT grid-factor recommendations derived from cctbx for the space group, its structure seminvariants, and its Euclidean normalizer.",
            "x-optimade-unit": "inapplicable",
            "properties": {
                "space_group": {
                    "x-optimade-type": "list",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "FFT grid factors arising from the space-group translations.",
                    "items": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "One grid factor.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "x-optimade-unit": "inapplicable"
                },
                "seminvariant": {
                    "x-optimade-type": "list",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "FFT grid factors arising from structure seminvariants.",
                    "items": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "One grid factor.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "x-optimade-unit": "inapplicable"
                },
                "euclidean": {
                    "x-optimade-type": "list",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "FFT grid factors arising from Euclidean-normalizer considerations.",
                    "items": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "One grid factor.",
                        "x-optimade-unit": "inapplicable"
                    },
                    "x-optimade-unit": "inapplicable"
                }
            },
            "examples": [
                {
                    "space_group": [
                        1,
                        1
                    ],
                    "seminvariant": [
                        1,
                        1
                    ],
                    "euclidean": [
                        1,
                        1
                    ]
                },
                {
                    "space_group": [
                        1,
                        1
                    ],
                    "seminvariant": [
                        2,
                        2
                    ],
                    "euclidean": [
                        2,
                        2
                    ]
                }
            ]
        },
        "centering_translations": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Centering translations",
            "$comment": "Anyterial property definition using the common reusable centering-translation definition.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "centering_translations",
                "label": "centering_translations_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Centering translations of the conventional cell.\nEach list member is one exact fractional-coordinate centering translation as defined by `/properties/symmetry/centering_translation`.\nThe zero translation `(0,0,0)` is listed first.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/centering_translation",
                "title": "Centering translation",
                "$comment": "Reusable Anyterial definition for one conventional-cell centering translation.",
                "x-optimade-type": "list",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "centering_translation",
                    "label": "centering_translation_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "array",
                    "null"
                ],
                "description": "One centering translation of a conventional crystallographic cell.\nThe translation is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- The zero translation is included in centering-translation lists and is normally listed first.",
                "x-optimade-dimensions": {
                    "names": [
                        "dim_lattice"
                    ],
                    "sizes": [
                        3
                    ]
                },
                "items": {
                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                    "title": "fraction",
                    "x-optimade-type": "string",
                    "x-optimade-definition": {
                        "label": "fraction_core",
                        "kind": "property",
                        "version": "0.1.0",
                        "format": "1.3",
                        "name": "fraction"
                    },
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "A fraction represented as a string.",
                    "examples": [
                        "2/3",
                        "5/42",
                        "10",
                        "0"
                    ],
                    "x-optimade-unit": "inapplicable"
                },
                "examples": [
                    [
                        "0",
                        "0",
                        "0"
                    ],
                    [
                        "1/2",
                        "1/2",
                        "0"
                    ]
                ]
            },
            "examples": [
                [
                    [
                        "0",
                        "0",
                        "0"
                    ]
                ],
                [
                    [
                        "0",
                        "0",
                        "0"
                    ],
                    [
                        "1/2",
                        "1/2",
                        "0"
                    ]
                ]
            ]
        },
        "centering_translations_xyz": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations_xyz",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Centering translations as xyz strings",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "centering_translations_xyz",
                "label": "centering_translations_xyz_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Centering translations of the conventional cell, represented as `x,y,z`-style coordinate shifts. The zero translation is listed first.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string"
                ]
            },
            "examples": [
                [
                    "0,0,0"
                ],
                [
                    "0,0,0",
                    "1/2,1/2,0"
                ]
            ]
        },
        "centring_type": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Centring Type",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.centring_type.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "centring_type",
                "label": "centring_type_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The lattice centring symbol for the crystallographic setting.\n\nThis setting-dependent symbol identifies primitive, face-centred, body-centred, rhombohedral, or hexagonal centring as represented in the setting record.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P",
                "C"
            ]
        },
        "crystal_system": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/crystal_system",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Crystal System",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.crystal_system.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "crystal_system",
                "label": "crystal_system_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The crystal system of the space group or point group.\n\nValues use the conventional crystallographic system names such as triclinic, monoclinic, orthorhombic, tetragonal, trigonal, hexagonal, and cubic.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "triclinic",
                "monoclinic"
            ]
        },
        "hall": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hall Symbol",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hall"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hall",
                "label": "hall_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The Hall symbol for a crystallographic space-group setting.\n\nHall symbols encode the generators and origin choice of a space-group setting in a form intended to identify the setting unambiguously. In the Anyterial symmetry data, this property is the plain ASCII Hall symbol corresponding to the Hall-keyed record.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P 1",
                "C 2y"
            ]
        },
        "hall_aliases": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hall Aliases",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hall_aliases",
                "label": "hall_aliases_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Alternate ASCII Hall symbols or Hall-setting keys associated with the same generated setting.\n\nAliases capture duplicate or equivalent Hall-table forms that identify the same setting in the generated tables.\n\n**Requirements/Conventions**:\n\n- The preferred display symbol is stored in `hall`.\n- Alias values SHOULD NOT be assumed to be unique across all settings without also considering the setting key.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                [
                    "A -2yac"
                ],
                [
                    "C -2ybc"
                ]
            ],
            "items": {
                "x-optimade-type": "string",
                "type": [
                    "string",
                    "null"
                ],
                "description": "One alternate symbol string.",
                "x-optimade-unit": "inapplicable"
            }
        },
        "hall_entry": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hall entry",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hall_entry",
                "label": "hall_entry_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Normalized Hall-table entry key used internally by the generated datasets.\n\nThe value is derived from the Hall symbol by using lowercase letters and underscores in place of spaces. It is stable for lookup within these data files, while the display Hall symbol is provided separately by `hall` and its formatted variants.\n\n**Requirements/Conventions**:\n\n- This field identifies a concrete Hall setting, not only an IT space-group type.\n- The same value is normally used as the key of the containing `spacegroups` map.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "p_1",
                "-p_1"
            ]
        },
        "hm_entry": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Entry",
            "$comment": "Anyterial symmetry property definition based on International Tables for Crystallography Volume B table A1.4.2.7.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_entry",
                "label": "hm_entry_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The Hermann-Mauguin entry label for a conventional space-group setting from table A1.4.2.7 of the [International Tables for Crystallography (2006). Volume B, Reciprocal space. ISBN: 978-0-7923-6592-1, doi:10.1107/97809553602060000102](https://doi.org/10.1107/97809553602060000102).\n\nThe symbol is a full Hermann-Mauguin-style setting label, except that:\n\n* The older glide-plane letters are used, rather than the newer `e` notation introduced in the Fourth Edition of the International Tables for Crystallography (1995) for the space groups Aem2 (39), Aea2 (41), Cmce (64), Cmme (67) and Ccce (68).\n* When necessary to disambiguate the 530 conventional settings, an origin-choice suffix (`:1`, `:2`) is used.\n\n**Requirements/Conventions**:\n\n- The value MUST be written as a plain string with spaces between Hermann-Mauguin symbol parts.\n- The disambiguation suffix MUST be a colon `:`  and an integer appended to the string without whitespace, for example `:1` or `:2`.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P 1",
                "C c c a:1",
                "C c c b:2"
            ]
        },
        "harker_planes": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/harker_planes",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Harker planes",
            "$comment": "Anyterial property definition for Harker planes or special-position conditions.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "harker_planes",
                "label": "harker_planes_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Harker planes of the space group in fractional Patterson coordinates, as generated by cctbx.\nEach entry describes one plane or special-position condition with an expression and optional exact normal, point, and constant data.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One Harker plane or special-position condition.",
                "properties": {
                    "algebraic": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Algebraic expression for the condition when emitted by cctbx."
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Plane equation in `x,y,z` notation when available."
                    },
                    "normal": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Integer normal vector of the plane.",
                        "items": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer"
                            ],
                            "description": "One integer component of the normal vector."
                        }
                    },
                    "point": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Point on the plane.",
                        "items": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                            "title": "fraction",
                            "x-optimade-type": "string",
                            "x-optimade-definition": {
                                "label": "fraction_core",
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "fraction"
                            },
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "A fraction represented as a string.",
                            "examples": [
                                "2/3",
                                "5/42",
                                "10",
                                "0"
                            ],
                            "x-optimade-unit": "inapplicable"
                        }
                    },
                    "const": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                        "title": "fraction",
                        "x-optimade-type": "string",
                        "x-optimade-definition": {
                            "label": "fraction_core",
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "fraction"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "A fraction represented as a string.",
                        "examples": [
                            "2/3",
                            "5/42",
                            "10",
                            "0"
                        ],
                        "x-optimade-unit": "inapplicable"
                    }
                }
            },
            "examples": [
                [
                    {
                        "algebraic": "2*x,0,2*z",
                        "normal": [
                            0,
                            1,
                            0
                        ],
                        "point": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            ]
        },
        "hm_cctbx_universal": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_cctbx_universal",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Cctbx Universal",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_cctbx_universal",
                "label": "hm_cctbx_universal_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Universal Hermann-Mauguin symbol returned by cctbx for this setting.\n\nThis field records the cctbx-internal universal symbol used during generation. It is useful for diagnostics and for tracing generator behavior, but it is not the International Tables preferred symbol. Prefer `hm_short`, `hm_full`, and `hm_extended` for table-facing symbol data.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P 1",
                "P -1"
            ]
        },
        "hm_extended": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Extended Hermann-Mauguin Symbol",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hermann_mauguin_extended"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_extended",
                "label": "hm_extended_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The setting-specific extended Hermann-Mauguin symbol for the space-group setting.\n\nExtended Hermann-Mauguin symbols give additional symmetry-element information compared with the short symbol. Multi-line values preserve line breaks and spacing used to align the extended symbol components.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P 1",
                "C 1 2 1\n  21"
            ]
        },
        "hm_extended_aliases": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Extended Aliases",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_extended_aliases",
                "label": "hm_extended_aliases_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Alternate ASCII forms of `hm_extended` that are accepted for the same generated setting. The preferred symbol is stored in `hm_extended`.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                [
                    "A b m 2\n c c 21"
                ],
                [
                    "B m a 2\n c c 21"
                ]
            ],
            "items": {
                "x-optimade-type": "string",
                "type": [
                    "string",
                    "null"
                ],
                "description": "One alternate symbol string.",
                "x-optimade-unit": "inapplicable"
            }
        },
        "hm_extended_old": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_old",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Extended Old",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_extended_old",
                "label": "hm_extended_old_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The older extended Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "A b m 2\n c c 21",
                "C 2 m b\n 21 a a"
            ]
        },
        "hm_full": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Full Hermann-Mauguin Symbol",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.name_H-M_full.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_full",
                "label": "hm_full_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The setting-specific full Hermann-Mauguin symbol for the space-group setting.\n\nThe full symbol expands the short Hermann-Mauguin notation to include the symmetry entries for all relevant crystallographic directions in the setting represented by the containing Hall record.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P 1",
                "C 1 2 1"
            ]
        },
        "hm_full_aliases": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Full Aliases",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_full_aliases",
                "label": "hm_full_aliases_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Alternate ASCII forms of `hm_full` that are accepted for the same generated setting. The preferred symbol is stored in `hm_full`.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                [
                    "F 23"
                ],
                [
                    "I 23"
                ]
            ],
            "items": {
                "x-optimade-type": "string",
                "type": [
                    "string",
                    "null"
                ],
                "description": "One alternate symbol string.",
                "x-optimade-unit": "inapplicable"
            }
        },
        "hm_full_old": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_old",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Full Old",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_full_old",
                "label": "hm_full_old_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The older full Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "A b m 2",
                "C 2 m b"
            ]
        },
        "hm_full_std": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Full Std",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_full_std",
                "label": "hm_full_std_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The International Tables standard full Hermann-Mauguin symbol for the space-group type.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P 1",
                "P -1"
            ]
        },
        "hm_short": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Short Hermann-Mauguin Symbol",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hermann_mauguin"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_short",
                "label": "hm_short_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The setting-specific short Hermann-Mauguin symbol for the space-group setting.\n\nThis field gives the concise Hermann-Mauguin notation used for the concrete Hall setting represented by the containing record. It is compatible with OPTIMADE's `space_group_symbol_hermann_mauguin` when used as the conventional short Hermann-Mauguin symbol.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P 1",
                "C 2"
            ]
        },
        "hm_short_aliases": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Short Aliases",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_short_aliases",
                "label": "hm_short_aliases_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Alternate ASCII forms of `hm_short` that are accepted for the same generated setting. The preferred symbol is stored in `hm_short`.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                [
                    "C c c a",
                    "C c c b"
                ],
                [
                    "A b a a",
                    "A c a a"
                ]
            ],
            "items": {
                "x-optimade-type": "string",
                "type": [
                    "string",
                    "null"
                ],
                "description": "One alternate symbol string.",
                "x-optimade-unit": "inapplicable"
            }
        },
        "hm_short_old": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Short Old",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_short_old",
                "label": "hm_short_old_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The older short Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "A b m 2",
                "C 2 m b"
            ]
        },
        "hm_short_std": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hermann-Mauguin Short Std",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_short_std",
                "label": "hm_short_std_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The International Tables standard short Hermann-Mauguin symbol for the space-group type.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P 1",
                "P -1"
            ]
        },
        "is_centric": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Is Centric",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "boolean",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "is_centric",
                "label": "is_centric_spacegroups"
            },
            "type": [
                "boolean",
                "null"
            ],
            "description": "Boolean flag indicating whether the cctbx space group is centric.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                false,
                true
            ]
        },
        "is_chiral": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Is Chiral",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "boolean",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "is_chiral",
                "label": "is_chiral_spacegroups"
            },
            "type": [
                "boolean",
                "null"
            ],
            "description": "Boolean flag indicating whether the space group is chiral.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                true,
                false
            ]
        },
        "is_enantiomorphic": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Is Enantiomorphic",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "boolean",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "is_enantiomorphic",
                "label": "is_enantiomorphic_spacegroups"
            },
            "type": [
                "boolean",
                "null"
            ],
            "description": "Boolean flag indicating whether the space-group type belongs to an enantiomorphic pair.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                false,
                true
            ]
        },
        "is_reference_setting": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Is Reference Setting",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "boolean",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "is_reference_setting",
                "label": "is_reference_setting_spacegroups"
            },
            "type": [
                "boolean",
                "null"
            ],
            "description": "Boolean flag indicating whether this Hall setting is the selected reference setting for its International Tables space-group number.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                true,
                false
            ]
        },
        "it_coordinate_system_code": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "International Tables Coordinate-System Code",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.IT_coordinate_system_code.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "it_coordinate_system_code",
                "label": "it_coordinate_system_code_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The International Tables coordinate-system code for the setting.\n\nThe code distinguishes setting choices such as monoclinic unique-axis and cell choices, orthorhombic axis settings, tetragonal/cubic origin choices, and trigonal hexagonal or rhombohedral axes.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "b1",
                "2"
            ]
        },
        "it_number": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "International Tables Space-Group Number",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "integer",
            "x-compatibility": [
                "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_it_number"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "it_number",
                "label": "it_number_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "The International Tables space-group number.\n\nThis integer identifies the space-group type numbered 1 through 230 in International Tables for Crystallography. Multiple Hall settings can share the same `it_number`.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                5
            ]
        },
        "it_number_enantiomorphic": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "It Number Enantiomorphic",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "it_number_enantiomorphic",
                "label": "it_number_enantiomorphic_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "International Tables number of the enantiomorphic partner space group, when one exists. The value is null for space groups without a distinct enantiomorphic partner.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                78,
                76
            ]
        },
        "laue_class": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/laue_class",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Laue Class",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.Laue_class.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "laue_class",
                "label": "laue_class_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The Laue class associated with the space group or point group.\n\nThe Laue class groups point groups that become equivalent when inversion symmetry is included.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "-1",
                "2/m"
            ]
        },
        "n_centering_translations": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_centering_translations",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Centering Translations",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_centering_translations",
                "label": "n_centering_translations_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of centering translations in the conventional cell of the space-group setting.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                2
            ]
        },
        "n_pointgroup_symops": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_pointgroup_symops",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Pointgroup Symops",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_pointgroup_symops",
                "label": "n_pointgroup_symops_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of point-group symmetry operations represented by the space group, excluding centering translations.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                2
            ]
        },
        "n_symops": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Symops",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_symops",
                "label": "n_symops_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of symmetry operations in the finite operation list of the generated entry.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                1,
                2
            ]
        },
        "point_group": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Point-Group Hermann-Mauguin Symbol",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.point_group_H-M.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "point_group",
                "label": "point_group_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The Hermann-Mauguin point-group symbol associated with the space group.\n\nThis field identifies the crystallographic point group obtained from the space group by removing translational components.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "1",
                "2"
            ]
        },
        "schoenflies": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Schoenflies Symbol",
            "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
            "x-optimade-type": "string",
            "x-compatibility": [
                "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.name_Schoenflies.html"
            ],
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "schoenflies",
                "label": "schoenflies_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The Schoenflies symbol for the space-group type.\n\nThe ASCII form follows the CIF convention for `_space_group.name_Schoenflies`, using a period to separate the Schoenflies point-group symbol from the superscript index.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "C1.1",
                "C2.3"
            ]
        },
        "setting": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Setting",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "setting",
                "label": "setting_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Setting suffix or setting annotation extracted from the cctbx universal Hermann-Mauguin symbol.\n\nThis value is a compact textual description of the coordinate setting portion of the cctbx symbol, for example an origin choice or axis-setting annotation. It is primarily an auxiliary generator field and SHOULD NOT be used as a substitute for the International Tables `setting_it_nc` identifier.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "(c,a,b)",
                "(b,c,a)"
            ]
        },
        "setting_it_nc": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "International Tables setting code n:c",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "setting_it_nc",
                "label": "setting_it_nc_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "International Tables setting identifier in `n:c` notation.\n\nThe part before the colon is the International Tables space-group number. The part after the colon is the coordinate-system or origin-choice qualifier used to distinguish settings that share the same IT number.\n\n**Requirements/Conventions**:\n\n- Triclinic, hexagonal, and many unique settings use only the IT number, for example `1`.\n- Monoclinic settings use qualifiers such as `b1`, `-b1`, `c2`, or `a3`.\n- Orthorhombic settings use qualifiers such as `abc`, `cab`, `1abc`, or `2bca` when needed.\n- Tetragonal and cubic origin choices use qualifiers such as `1` and `2`; trigonal axis choices use qualifiers such as `h` and `r`.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "1",
                "2"
            ]
        },
        "setting_it_nc_aliases": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "International Tables setting-code aliases",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "setting_it_nc_aliases",
                "label": "setting_it_nc_aliases_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Alternative International Tables `n:c` setting identifiers that refer to the same Hall setting or are otherwise treated as aliases of `setting_it_nc` by the generator. This field is used only when the source tables expose more than one conventional label for the same generated setting.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "string",
                "type": [
                    "string",
                    "null"
                ],
                "description": "One alternate symbol string.",
                "x-optimade-unit": "inapplicable"
            },
            "examples": [
                [
                    "68:1ba-c"
                ],
                [
                    "68:1-cba"
                ]
            ]
        },
        "setting_plaintext": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Setting Plaintext",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "setting_plaintext",
                "label": "setting_plaintext_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Human-readable description of the International Tables coordinate-system setting.\n\nThis field expands `setting_it_nc` into a short phrase such as a monoclinic unique-axis and cell-choice description, an orthorhombic axis permutation, or an origin-choice description.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "unique axis b",
                "unique axis c"
            ]
        },
        "spacegroup_symbols": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Space-group symbols",
            "$comment": "Ordered Anyterial table of conventional space-group symbols.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "spacegroup_symbols",
                "label": "spacegroup_symbols_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Ordered table of conventional space-group symbol rows.\nEach row describes one Hall setting where the International Tables symbol data is available, including the IT coordinate-system code, Hall symbol, IT number, and Hermann-Mauguin symbols.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary SHOULD contain the setting identifier `setting_it_nc`, the Hall symbol `hall`, the International Tables number `it_number`, and the setting-specific Hermann-Mauguin symbols `hm_short`, `hm_full`, and `hm_extended` when available.\n- The order SHOULD follow the conventional ITA/Hall setting order used by the generated `symmetry_basics` space-group table.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One space-group symbol row.",
                "properties": {
                    "setting_it_nc": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc",
                        "title": "International Tables setting code n:c",
                        "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                        "x-optimade-type": "string",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "setting_it_nc",
                            "label": "setting_it_nc_spacegroups"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "International Tables setting identifier in `n:c` notation.\n\nThe part before the colon is the International Tables space-group number. The part after the colon is the coordinate-system or origin-choice qualifier used to distinguish settings that share the same IT number.\n\n**Requirements/Conventions**:\n\n- Triclinic, hexagonal, and many unique settings use only the IT number, for example `1`.\n- Monoclinic settings use qualifiers such as `b1`, `-b1`, `c2`, or `a3`.\n- Orthorhombic settings use qualifiers such as `abc`, `cab`, `1abc`, or `2bca` when needed.\n- Tetragonal and cubic origin choices use qualifiers such as `1` and `2`; trigonal axis choices use qualifiers such as `h` and `r`.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            "1",
                            "2"
                        ]
                    },
                    "hall_entry": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry",
                        "title": "Hall entry",
                        "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                        "x-optimade-type": "string",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "hall_entry",
                            "label": "hall_entry_spacegroups"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Normalized Hall-table entry key used internally by the generated datasets.\n\nThe value is derived from the Hall symbol by using lowercase letters and underscores in place of spaces. It is stable for lookup within these data files, while the display Hall symbol is provided separately by `hall` and its formatted variants.\n\n**Requirements/Conventions**:\n\n- This field identifies a concrete Hall setting, not only an IT space-group type.\n- The same value is normally used as the key of the containing `spacegroups` map.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            "p_1",
                            "-p_1"
                        ]
                    },
                    "hall": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall",
                        "title": "Hall Symbol",
                        "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                        "x-optimade-type": "string",
                        "x-compatibility": [
                            "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hall"
                        ],
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "hall",
                            "label": "hall_spacegroups"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "The Hall symbol for a crystallographic space-group setting.\n\nHall symbols encode the generators and origin choice of a space-group setting in a form intended to identify the setting unambiguously. In the Anyterial symmetry data, this property is the plain ASCII Hall symbol corresponding to the Hall-keyed record.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            "P 1",
                            "C 2y"
                        ]
                    },
                    "it_number": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number",
                        "title": "International Tables Space-Group Number",
                        "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                        "x-optimade-type": "integer",
                        "x-compatibility": [
                            "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_it_number"
                        ],
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "it_number",
                            "label": "it_number_spacegroups"
                        },
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "The International Tables space-group number.\n\nThis integer identifies the space-group type numbered 1 through 230 in International Tables for Crystallography. Multiple Hall settings can share the same `it_number`.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            1,
                            5
                        ]
                    },
                    "hm_short": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short",
                        "title": "Short Hermann-Mauguin Symbol",
                        "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                        "x-optimade-type": "string",
                        "x-compatibility": [
                            "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hermann_mauguin"
                        ],
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "hm_short",
                            "label": "hm_short_spacegroups"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "The setting-specific short Hermann-Mauguin symbol for the space-group setting.\n\nThis field gives the concise Hermann-Mauguin notation used for the concrete Hall setting represented by the containing record. It is compatible with OPTIMADE's `space_group_symbol_hermann_mauguin` when used as the conventional short Hermann-Mauguin symbol.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            "P 1",
                            "C 2"
                        ]
                    },
                    "hm_full": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full",
                        "title": "Full Hermann-Mauguin Symbol",
                        "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                        "x-optimade-type": "string",
                        "x-compatibility": [
                            "https://www.iucr.org/__data/iucr/cifdic_html/2/cif_sym.dic/Ispace_group.name_H-M_full.html"
                        ],
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "hm_full",
                            "label": "hm_full_spacegroups"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "The setting-specific full Hermann-Mauguin symbol for the space-group setting.\n\nThe full symbol expands the short Hermann-Mauguin notation to include the symmetry entries for all relevant crystallographic directions in the setting represented by the containing Hall record.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            "P 1",
                            "C 1 2 1"
                        ]
                    },
                    "hm_extended": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended",
                        "title": "Extended Hermann-Mauguin Symbol",
                        "$comment": "Anyterial symmetry property definition with compatible external crystallographic definition IRIs.",
                        "x-optimade-type": "string",
                        "x-compatibility": [
                            "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symbol_hermann_mauguin_extended"
                        ],
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "hm_extended",
                            "label": "hm_extended_spacegroups"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "The setting-specific extended Hermann-Mauguin symbol for the space-group setting.\n\nExtended Hermann-Mauguin symbols give additional symmetry-element information compared with the short symbol. Multi-line values preserve line breaks and spacing used to align the extended symbol components.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            "P 1",
                            "C 1 2 1\n  21"
                        ]
                    },
                    "hm_extended_old": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_old",
                        "title": "Hermann-Mauguin Extended Old",
                        "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                        "x-optimade-type": "string",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "hm_extended_old",
                            "label": "hm_extended_old_spacegroups"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "The older extended Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            "A b m 2\n c c 21",
                            "C 2 m b\n 21 a a"
                        ]
                    },
                    "hm_short_old": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old",
                        "title": "Hermann-Mauguin Short Old",
                        "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                        "x-optimade-type": "string",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "hm_short_old",
                            "label": "hm_short_old_spacegroups"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "The older short Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            "A b m 2",
                            "C 2 m b"
                        ]
                    },
                    "hm_full_old": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_old",
                        "title": "Hermann-Mauguin Full Old",
                        "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
                        "x-optimade-type": "string",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "hm_full_old",
                            "label": "hm_full_old_spacegroups"
                        },
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "The older full Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.\n\nHermann-Mauguin symbols describe crystallographic space groups using lattice-centering symbols and symmetry-element symbols. The setting-specific fields describe the concrete Hall/International Tables setting of the current record. The `*_std` fields describe the IT-standard setting for the space-group type and can therefore be identical across multiple settings with the same IT number.\n\n**Requirements/Conventions**:\n\n- The plain string form uses spaces between symbol parts where this is needed for unambiguous parsing.\n- The extended symbol MAY contain multiple lines; line breaks and spacing encode the alignment used in International Tables extended symbols.\n- Older-symbol fields are present only where an older International Tables form is retained for comparison or aliasing.",
                        "x-optimade-unit": "inapplicable",
                        "examples": [
                            "A b m 2",
                            "C 2 m b"
                        ]
                    }
                }
            },
            "examples": [
                [
                    {
                        "setting_it_nc": "1",
                        "hall": "P 1",
                        "it_number": 1,
                        "hm_short": "P 1",
                        "hm_full": "P 1",
                        "hm_extended": "P 1"
                    }
                ]
            ]
        },
        "spglib_hall": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Spglib Hall",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "spglib_hall",
                "label": "spglib_hall_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Hall setting selected by spglib for the space-group type or setting, represented as a normalized Hall key.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "P 1",
                "-P 1"
            ]
        },
        "spglib_hall_numbers": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Spglib Hall Numbers",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "spglib_hall_numbers",
                "label": "spglib_hall_numbers_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "spglib Hall numbers corresponding to the generated setting.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "integer",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "integer"
                ]
            },
            "examples": [
                [
                    1
                ],
                [
                    2
                ]
            ]
        },
        "structure_seminvariants": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Structure Seminvariants",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "structure_seminvariants",
                "label": "structure_seminvariants_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Structure seminvariant vectors and moduli for the space-group setting. These characterize phase restrictions and FFT grid constraints associated with the symmetry.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "dictionary",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One structure-seminvariant condition vector.",
                "properties": {
                    "vector": {
                        "x-optimade-type": "list",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Integer vector defining the seminvariant congruence.",
                        "items": {
                            "x-optimade-type": "integer",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "One vector component.",
                            "x-optimade-unit": "inapplicable"
                        },
                        "x-optimade-unit": "inapplicable"
                    },
                    "modulus": {
                        "x-optimade-type": "integer",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Modulus for the seminvariant congruence.",
                        "x-optimade-unit": "inapplicable"
                    }
                },
                "x-optimade-unit": "inapplicable"
            },
            "examples": [
                [
                    {
                        "vector": [
                            1,
                            0
                        ],
                        "modulus": 0
                    },
                    {
                        "vector": [
                            0,
                            1
                        ],
                        "modulus": 0
                    },
                    {
                        "vector": [
                            0,
                            0
                        ],
                        "modulus": 0
                    }
                ],
                [
                    {
                        "vector": [
                            1,
                            0
                        ],
                        "modulus": 2
                    },
                    {
                        "vector": [
                            0,
                            1
                        ],
                        "modulus": 2
                    },
                    {
                        "vector": [
                            0,
                            0
                        ],
                        "modulus": 2
                    }
                ]
            ]
        },
        "symops": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operations",
            "$comment": "Anyterial property definition using the common reusable op object definition.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops",
                "label": "symops_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Full list of symmetry-operation descriptors for a space-group setting.\nEach list member is a `op` object as defined by `/properties/symmetry/op`.\nFor space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op",
                "title": "Operation",
                "$comment": "Reusable Anyterial definition for one classified crystallographic operation descriptor.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "op",
                    "label": "op_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "A classified crystallographic operation acting within one coordinate setting.\nThe affine map itself is stored in the embedded `affine_transformation` field.\nThe remaining fields classify the operation crystallographically, for example by rotation type, axis, sense, and screw or glide component.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **affine\\_transformation**: REQUIRED; Dictionary.\n      Exact affine map for the operation.\n      It MUST follow `/defs/v0.1/properties/symmetry/affine_transformation`.\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.\n\n    - **type**: OPTIONAL; Integer.\n      Legacy numeric operation-type code used by point-group operation descriptors.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n    - **is\\_proper**: OPTIONAL; Boolean.\n      States whether the linear operation is proper, i.e., whether its determinant is +1.",
                "properties": {
                    "affine_transformation": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation",
                        "title": "Affine transformation",
                        "$comment": "Reusable Anyterial definition for the pure affine-map part of crystallographic transformation records.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "affine_transformation",
                            "label": "affine_transformation_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "One exact affine transformation acting on fractional crystallographic coordinates.\nThe transformation is represented by a 3 by 3 matrix and a 3-vector, both serialized with exact string entries.\nParent properties define the coordinate convention and semantic role of the transformation, for example whether it is an operation within one setting, a setting transform, a subgroup embedding, or a normalizer representative.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **matrix**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the affine transformation.\n      It MUST be represented as a list of three row lists, each containing three exact rational entries represented as strings.\n\n    - **vector**: REQUIRED; List of 3 Fractions (String).\n      Translation or origin-shift vector of the affine transformation in fractional coordinates.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the affine transformation in `x,y,z` notation when available.\n\n    - **det**: OPTIONAL; Integer.\n      Determinant of `matrix` when the generator emits it.\n\n    - **is\\_orthogonal**: OPTIONAL; Boolean.\n      Whether `matrix` is orthogonal in the exact representation used by the generator.",
                        "properties": {
                            "matrix": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_lattice",
                                        "dim_lattice"
                                    ],
                                    "sizes": [
                                        3,
                                        3
                                    ]
                                },
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Exact 3 by 3 matrix part of the affine transformation.",
                                "items": {
                                    "x-optimade-type": "list",
                                    "x-optimade-unit": "inapplicable",
                                    "x-optimade-dimensions": {
                                        "names": [
                                            "dim_lattice"
                                        ],
                                        "sizes": [
                                            3
                                        ]
                                    },
                                    "type": [
                                        "array"
                                    ],
                                    "description": "One row of the exact 3 by 3 matrix.",
                                    "items": {
                                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                        "title": "fraction",
                                        "x-optimade-type": "string",
                                        "x-optimade-definition": {
                                            "label": "fraction_core",
                                            "kind": "property",
                                            "version": "0.1.0",
                                            "format": "1.3",
                                            "name": "fraction"
                                        },
                                        "type": [
                                            "string",
                                            "null"
                                        ],
                                        "description": "A fraction represented as a string.",
                                        "examples": [
                                            "2/3",
                                            "5/42",
                                            "10",
                                            "0"
                                        ],
                                        "x-optimade-unit": "inapplicable"
                                    }
                                }
                            },
                            "vector": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_lattice"
                                    ],
                                    "sizes": [
                                        3
                                    ]
                                },
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Exact fractional-coordinate vector part of the affine transformation.",
                                "items": {
                                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                    "title": "fraction",
                                    "x-optimade-type": "string",
                                    "x-optimade-definition": {
                                        "label": "fraction_core",
                                        "kind": "property",
                                        "version": "0.1.0",
                                        "format": "1.3",
                                        "name": "fraction"
                                    },
                                    "type": [
                                        "string",
                                        "null"
                                    ],
                                    "description": "A fraction represented as a string.",
                                    "examples": [
                                        "2/3",
                                        "5/42",
                                        "10",
                                        "0"
                                    ],
                                    "x-optimade-unit": "inapplicable"
                                }
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the affine transformation in `x,y,z` notation."
                            },
                            "det": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Determinant of the matrix part when emitted by the generator."
                            },
                            "is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the matrix part is orthogonal."
                            }
                        },
                        "examples": [
                            {
                                "matrix": [
                                    [
                                        "-1",
                                        "0",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "-1",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "0",
                                        "1"
                                    ]
                                ],
                                "vector": [
                                    "0",
                                    "0",
                                    "0"
                                ],
                                "xyz": "-x,-y,z",
                                "det": 1,
                                "is_orthogonal": true
                            }
                        ]
                    },
                    "rot_type": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Symbolic crystallographic operation-type label for the linear part."
                    },
                    "type": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Legacy numeric point-group operation-type code."
                    },
                    "axis": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Integer-vector axis or invariant-direction descriptor for the operation.",
                        "items": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer"
                            ],
                            "description": "One integer component of the axis vector."
                        }
                    },
                    "sense": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Rotation sense/sign convention returned by the generator."
                    },
                    "screw_glide": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Screw-axis or glide-plane component represented exactly as a list of fraction strings.",
                        "items": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                            "title": "fraction",
                            "x-optimade-type": "string",
                            "x-optimade-definition": {
                                "label": "fraction_core",
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "fraction"
                            },
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "A fraction represented as a string.",
                            "examples": [
                                "2/3",
                                "5/42",
                                "10",
                                "0"
                            ],
                            "x-optimade-unit": "inapplicable"
                        }
                    },
                    "origin_shift": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Origin-shift descriptor represented exactly as a list of fraction strings.",
                        "items": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                            "title": "fraction",
                            "x-optimade-type": "string",
                            "x-optimade-definition": {
                                "label": "fraction_core",
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "fraction"
                            },
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "A fraction represented as a string.",
                            "examples": [
                                "2/3",
                                "5/42",
                                "10",
                                "0"
                            ],
                            "x-optimade-unit": "inapplicable"
                        }
                    },
                    "is_proper": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether the linear operation is proper."
                    }
                },
                "examples": [
                    {
                        "affine_transformation": {
                            "matrix": [
                                [
                                    "-1",
                                    "0",
                                    "0"
                                ],
                                [
                                    "0",
                                    "-1",
                                    "0"
                                ],
                                [
                                    "0",
                                    "0",
                                    "1"
                                ]
                            ],
                            "vector": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "-x,-y,z",
                            "det": 1,
                            "is_orthogonal": true
                        },
                        "rot_type": "2",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            1
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            },
            "examples": [
                [
                    {
                        "affine_transformation": {
                            "matrix": [
                                [
                                    "1",
                                    "0",
                                    "0"
                                ],
                                [
                                    "0",
                                    "1",
                                    "0"
                                ],
                                [
                                    "0",
                                    "0",
                                    "1"
                                ]
                            ],
                            "vector": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "x,y,z"
                        },
                        "rot_type": "1",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            ]
        },
        "symops_mod_centering": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operations modulo centering translations",
            "$comment": "Anyterial property definition using the common reusable op object definition.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops_mod_centering",
                "label": "symops_mod_centering_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Representative symmetry-operation descriptors modulo centering translations.\nEach list member is a `op` object as defined by `/properties/symmetry/op`.\nFor space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op",
                "title": "Operation",
                "$comment": "Reusable Anyterial definition for one classified crystallographic operation descriptor.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "op",
                    "label": "op_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "A classified crystallographic operation acting within one coordinate setting.\nThe affine map itself is stored in the embedded `affine_transformation` field.\nThe remaining fields classify the operation crystallographically, for example by rotation type, axis, sense, and screw or glide component.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **affine\\_transformation**: REQUIRED; Dictionary.\n      Exact affine map for the operation.\n      It MUST follow `/defs/v0.1/properties/symmetry/affine_transformation`.\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.\n\n    - **type**: OPTIONAL; Integer.\n      Legacy numeric operation-type code used by point-group operation descriptors.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n    - **is\\_proper**: OPTIONAL; Boolean.\n      States whether the linear operation is proper, i.e., whether its determinant is +1.",
                "properties": {
                    "affine_transformation": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation",
                        "title": "Affine transformation",
                        "$comment": "Reusable Anyterial definition for the pure affine-map part of crystallographic transformation records.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "affine_transformation",
                            "label": "affine_transformation_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "One exact affine transformation acting on fractional crystallographic coordinates.\nThe transformation is represented by a 3 by 3 matrix and a 3-vector, both serialized with exact string entries.\nParent properties define the coordinate convention and semantic role of the transformation, for example whether it is an operation within one setting, a setting transform, a subgroup embedding, or a normalizer representative.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **matrix**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the affine transformation.\n      It MUST be represented as a list of three row lists, each containing three exact rational entries represented as strings.\n\n    - **vector**: REQUIRED; List of 3 Fractions (String).\n      Translation or origin-shift vector of the affine transformation in fractional coordinates.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the affine transformation in `x,y,z` notation when available.\n\n    - **det**: OPTIONAL; Integer.\n      Determinant of `matrix` when the generator emits it.\n\n    - **is\\_orthogonal**: OPTIONAL; Boolean.\n      Whether `matrix` is orthogonal in the exact representation used by the generator.",
                        "properties": {
                            "matrix": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_lattice",
                                        "dim_lattice"
                                    ],
                                    "sizes": [
                                        3,
                                        3
                                    ]
                                },
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Exact 3 by 3 matrix part of the affine transformation.",
                                "items": {
                                    "x-optimade-type": "list",
                                    "x-optimade-unit": "inapplicable",
                                    "x-optimade-dimensions": {
                                        "names": [
                                            "dim_lattice"
                                        ],
                                        "sizes": [
                                            3
                                        ]
                                    },
                                    "type": [
                                        "array"
                                    ],
                                    "description": "One row of the exact 3 by 3 matrix.",
                                    "items": {
                                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                        "title": "fraction",
                                        "x-optimade-type": "string",
                                        "x-optimade-definition": {
                                            "label": "fraction_core",
                                            "kind": "property",
                                            "version": "0.1.0",
                                            "format": "1.3",
                                            "name": "fraction"
                                        },
                                        "type": [
                                            "string",
                                            "null"
                                        ],
                                        "description": "A fraction represented as a string.",
                                        "examples": [
                                            "2/3",
                                            "5/42",
                                            "10",
                                            "0"
                                        ],
                                        "x-optimade-unit": "inapplicable"
                                    }
                                }
                            },
                            "vector": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_lattice"
                                    ],
                                    "sizes": [
                                        3
                                    ]
                                },
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Exact fractional-coordinate vector part of the affine transformation.",
                                "items": {
                                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                    "title": "fraction",
                                    "x-optimade-type": "string",
                                    "x-optimade-definition": {
                                        "label": "fraction_core",
                                        "kind": "property",
                                        "version": "0.1.0",
                                        "format": "1.3",
                                        "name": "fraction"
                                    },
                                    "type": [
                                        "string",
                                        "null"
                                    ],
                                    "description": "A fraction represented as a string.",
                                    "examples": [
                                        "2/3",
                                        "5/42",
                                        "10",
                                        "0"
                                    ],
                                    "x-optimade-unit": "inapplicable"
                                }
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the affine transformation in `x,y,z` notation."
                            },
                            "det": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Determinant of the matrix part when emitted by the generator."
                            },
                            "is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the matrix part is orthogonal."
                            }
                        },
                        "examples": [
                            {
                                "matrix": [
                                    [
                                        "-1",
                                        "0",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "-1",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "0",
                                        "1"
                                    ]
                                ],
                                "vector": [
                                    "0",
                                    "0",
                                    "0"
                                ],
                                "xyz": "-x,-y,z",
                                "det": 1,
                                "is_orthogonal": true
                            }
                        ]
                    },
                    "rot_type": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Symbolic crystallographic operation-type label for the linear part."
                    },
                    "type": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Legacy numeric point-group operation-type code."
                    },
                    "axis": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Integer-vector axis or invariant-direction descriptor for the operation.",
                        "items": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer"
                            ],
                            "description": "One integer component of the axis vector."
                        }
                    },
                    "sense": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Rotation sense/sign convention returned by the generator."
                    },
                    "screw_glide": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Screw-axis or glide-plane component represented exactly as a list of fraction strings.",
                        "items": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                            "title": "fraction",
                            "x-optimade-type": "string",
                            "x-optimade-definition": {
                                "label": "fraction_core",
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "fraction"
                            },
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "A fraction represented as a string.",
                            "examples": [
                                "2/3",
                                "5/42",
                                "10",
                                "0"
                            ],
                            "x-optimade-unit": "inapplicable"
                        }
                    },
                    "origin_shift": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Origin-shift descriptor represented exactly as a list of fraction strings.",
                        "items": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                            "title": "fraction",
                            "x-optimade-type": "string",
                            "x-optimade-definition": {
                                "label": "fraction_core",
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "fraction"
                            },
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "A fraction represented as a string.",
                            "examples": [
                                "2/3",
                                "5/42",
                                "10",
                                "0"
                            ],
                            "x-optimade-unit": "inapplicable"
                        }
                    },
                    "is_proper": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether the linear operation is proper."
                    }
                },
                "examples": [
                    {
                        "affine_transformation": {
                            "matrix": [
                                [
                                    "-1",
                                    "0",
                                    "0"
                                ],
                                [
                                    "0",
                                    "-1",
                                    "0"
                                ],
                                [
                                    "0",
                                    "0",
                                    "1"
                                ]
                            ],
                            "vector": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "-x,-y,z",
                            "det": 1,
                            "is_orthogonal": true
                        },
                        "rot_type": "2",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            1
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            },
            "examples": [
                [
                    {
                        "affine_transformation": {
                            "matrix": [
                                [
                                    "1",
                                    "0",
                                    "0"
                                ],
                                [
                                    "0",
                                    "1",
                                    "0"
                                ],
                                [
                                    "0",
                                    "0",
                                    "1"
                                ]
                            ],
                            "vector": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "x,y,z"
                        },
                        "rot_type": "1",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            ]
        },
        "symops_mod_centering_xyz": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering_xyz",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operations modulo centering in x,y,z notation",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops_mod_centering_xyz",
                "label": "symops_mod_centering_xyz_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Symmetry operations modulo centering translations in fractional `x,y,z` notation, ordered consistently with `symops_mod_centering`.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string"
                ]
            },
            "examples": [
                [
                    "x,y,z"
                ],
                [
                    "-x,y,-z",
                    "x,y,z"
                ]
            ]
        },
        "symops_generators": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operation generators",
            "$comment": "Anyterial property definition using the common reusable op object definition.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops_generators",
                "label": "symops_generators_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Minimal generator subset of the full symmetry-operation group for a space-group setting.\nEach list member is a `op` object as defined by `/properties/symmetry/op`.\nFor space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op",
                "title": "Operation",
                "$comment": "Reusable Anyterial definition for one classified crystallographic operation descriptor.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "op",
                    "label": "op_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "A classified crystallographic operation acting within one coordinate setting.\nThe affine map itself is stored in the embedded `affine_transformation` field.\nThe remaining fields classify the operation crystallographically, for example by rotation type, axis, sense, and screw or glide component.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **affine\\_transformation**: REQUIRED; Dictionary.\n      Exact affine map for the operation.\n      It MUST follow `/defs/v0.1/properties/symmetry/affine_transformation`.\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.\n\n    - **type**: OPTIONAL; Integer.\n      Legacy numeric operation-type code used by point-group operation descriptors.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n    - **is\\_proper**: OPTIONAL; Boolean.\n      States whether the linear operation is proper, i.e., whether its determinant is +1.",
                "properties": {
                    "affine_transformation": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation",
                        "title": "Affine transformation",
                        "$comment": "Reusable Anyterial definition for the pure affine-map part of crystallographic transformation records.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "affine_transformation",
                            "label": "affine_transformation_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "One exact affine transformation acting on fractional crystallographic coordinates.\nThe transformation is represented by a 3 by 3 matrix and a 3-vector, both serialized with exact string entries.\nParent properties define the coordinate convention and semantic role of the transformation, for example whether it is an operation within one setting, a setting transform, a subgroup embedding, or a normalizer representative.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **matrix**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the affine transformation.\n      It MUST be represented as a list of three row lists, each containing three exact rational entries represented as strings.\n\n    - **vector**: REQUIRED; List of 3 Fractions (String).\n      Translation or origin-shift vector of the affine transformation in fractional coordinates.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the affine transformation in `x,y,z` notation when available.\n\n    - **det**: OPTIONAL; Integer.\n      Determinant of `matrix` when the generator emits it.\n\n    - **is\\_orthogonal**: OPTIONAL; Boolean.\n      Whether `matrix` is orthogonal in the exact representation used by the generator.",
                        "properties": {
                            "matrix": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_lattice",
                                        "dim_lattice"
                                    ],
                                    "sizes": [
                                        3,
                                        3
                                    ]
                                },
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Exact 3 by 3 matrix part of the affine transformation.",
                                "items": {
                                    "x-optimade-type": "list",
                                    "x-optimade-unit": "inapplicable",
                                    "x-optimade-dimensions": {
                                        "names": [
                                            "dim_lattice"
                                        ],
                                        "sizes": [
                                            3
                                        ]
                                    },
                                    "type": [
                                        "array"
                                    ],
                                    "description": "One row of the exact 3 by 3 matrix.",
                                    "items": {
                                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                        "title": "fraction",
                                        "x-optimade-type": "string",
                                        "x-optimade-definition": {
                                            "label": "fraction_core",
                                            "kind": "property",
                                            "version": "0.1.0",
                                            "format": "1.3",
                                            "name": "fraction"
                                        },
                                        "type": [
                                            "string",
                                            "null"
                                        ],
                                        "description": "A fraction represented as a string.",
                                        "examples": [
                                            "2/3",
                                            "5/42",
                                            "10",
                                            "0"
                                        ],
                                        "x-optimade-unit": "inapplicable"
                                    }
                                }
                            },
                            "vector": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_lattice"
                                    ],
                                    "sizes": [
                                        3
                                    ]
                                },
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Exact fractional-coordinate vector part of the affine transformation.",
                                "items": {
                                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                    "title": "fraction",
                                    "x-optimade-type": "string",
                                    "x-optimade-definition": {
                                        "label": "fraction_core",
                                        "kind": "property",
                                        "version": "0.1.0",
                                        "format": "1.3",
                                        "name": "fraction"
                                    },
                                    "type": [
                                        "string",
                                        "null"
                                    ],
                                    "description": "A fraction represented as a string.",
                                    "examples": [
                                        "2/3",
                                        "5/42",
                                        "10",
                                        "0"
                                    ],
                                    "x-optimade-unit": "inapplicable"
                                }
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the affine transformation in `x,y,z` notation."
                            },
                            "det": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Determinant of the matrix part when emitted by the generator."
                            },
                            "is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the matrix part is orthogonal."
                            }
                        },
                        "examples": [
                            {
                                "matrix": [
                                    [
                                        "-1",
                                        "0",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "-1",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "0",
                                        "1"
                                    ]
                                ],
                                "vector": [
                                    "0",
                                    "0",
                                    "0"
                                ],
                                "xyz": "-x,-y,z",
                                "det": 1,
                                "is_orthogonal": true
                            }
                        ]
                    },
                    "rot_type": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Symbolic crystallographic operation-type label for the linear part."
                    },
                    "type": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Legacy numeric point-group operation-type code."
                    },
                    "axis": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Integer-vector axis or invariant-direction descriptor for the operation.",
                        "items": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer"
                            ],
                            "description": "One integer component of the axis vector."
                        }
                    },
                    "sense": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Rotation sense/sign convention returned by the generator."
                    },
                    "screw_glide": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Screw-axis or glide-plane component represented exactly as a list of fraction strings.",
                        "items": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                            "title": "fraction",
                            "x-optimade-type": "string",
                            "x-optimade-definition": {
                                "label": "fraction_core",
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "fraction"
                            },
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "A fraction represented as a string.",
                            "examples": [
                                "2/3",
                                "5/42",
                                "10",
                                "0"
                            ],
                            "x-optimade-unit": "inapplicable"
                        }
                    },
                    "origin_shift": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Origin-shift descriptor represented exactly as a list of fraction strings.",
                        "items": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                            "title": "fraction",
                            "x-optimade-type": "string",
                            "x-optimade-definition": {
                                "label": "fraction_core",
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "fraction"
                            },
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "A fraction represented as a string.",
                            "examples": [
                                "2/3",
                                "5/42",
                                "10",
                                "0"
                            ],
                            "x-optimade-unit": "inapplicable"
                        }
                    },
                    "is_proper": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether the linear operation is proper."
                    }
                },
                "examples": [
                    {
                        "affine_transformation": {
                            "matrix": [
                                [
                                    "-1",
                                    "0",
                                    "0"
                                ],
                                [
                                    "0",
                                    "-1",
                                    "0"
                                ],
                                [
                                    "0",
                                    "0",
                                    "1"
                                ]
                            ],
                            "vector": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "-x,-y,z",
                            "det": 1,
                            "is_orthogonal": true
                        },
                        "rot_type": "2",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            1
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            },
            "examples": [
                [
                    {
                        "affine_transformation": {
                            "matrix": [
                                [
                                    "1",
                                    "0",
                                    "0"
                                ],
                                [
                                    "0",
                                    "1",
                                    "0"
                                ],
                                [
                                    "0",
                                    "0",
                                    "1"
                                ]
                            ],
                            "vector": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "x,y,z"
                        },
                        "rot_type": "1",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            ]
        },
        "symops_generators_xyz": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symops Generators Xyz",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops_generators_xyz",
                "label": "symops_generators_xyz_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Minimal generator subset of the full symmetry-operation group in fractional `x,y,z` notation, ordered consistently with `symops_generators`.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string"
                ]
            },
            "examples": [
                [
                    "-x,-y,-z"
                ],
                [
                    "-x,y,-z"
                ]
            ]
        },
        "symops_representative": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Representative symmetry operations",
            "$comment": "Anyterial property definition using the common reusable op object definition.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops_representative",
                "label": "symops_representative_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Representative symmetry-operation descriptors modulo centering translations.\nEach list member is a `op` object as defined by `/properties/symmetry/op`.\nFor space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST follow the schema inherited from `/properties/symmetry/op`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op",
                "title": "Operation",
                "$comment": "Reusable Anyterial definition for one classified crystallographic operation descriptor.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "op",
                    "label": "op_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "A classified crystallographic operation acting within one coordinate setting.\nThe affine map itself is stored in the embedded `affine_transformation` field.\nThe remaining fields classify the operation crystallographically, for example by rotation type, axis, sense, and screw or glide component.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **affine\\_transformation**: REQUIRED; Dictionary.\n      Exact affine map for the operation.\n      It MUST follow `/defs/v0.1/properties/symmetry/affine_transformation`.\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.\n\n    - **type**: OPTIONAL; Integer.\n      Legacy numeric operation-type code used by point-group operation descriptors.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n    - **is\\_proper**: OPTIONAL; Boolean.\n      States whether the linear operation is proper, i.e., whether its determinant is +1.",
                "properties": {
                    "affine_transformation": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation",
                        "title": "Affine transformation",
                        "$comment": "Reusable Anyterial definition for the pure affine-map part of crystallographic transformation records.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "affine_transformation",
                            "label": "affine_transformation_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "One exact affine transformation acting on fractional crystallographic coordinates.\nThe transformation is represented by a 3 by 3 matrix and a 3-vector, both serialized with exact string entries.\nParent properties define the coordinate convention and semantic role of the transformation, for example whether it is an operation within one setting, a setting transform, a subgroup embedding, or a normalizer representative.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **matrix**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the affine transformation.\n      It MUST be represented as a list of three row lists, each containing three exact rational entries represented as strings.\n\n    - **vector**: REQUIRED; List of 3 Fractions (String).\n      Translation or origin-shift vector of the affine transformation in fractional coordinates.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the affine transformation in `x,y,z` notation when available.\n\n    - **det**: OPTIONAL; Integer.\n      Determinant of `matrix` when the generator emits it.\n\n    - **is\\_orthogonal**: OPTIONAL; Boolean.\n      Whether `matrix` is orthogonal in the exact representation used by the generator.",
                        "properties": {
                            "matrix": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_lattice",
                                        "dim_lattice"
                                    ],
                                    "sizes": [
                                        3,
                                        3
                                    ]
                                },
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Exact 3 by 3 matrix part of the affine transformation.",
                                "items": {
                                    "x-optimade-type": "list",
                                    "x-optimade-unit": "inapplicable",
                                    "x-optimade-dimensions": {
                                        "names": [
                                            "dim_lattice"
                                        ],
                                        "sizes": [
                                            3
                                        ]
                                    },
                                    "type": [
                                        "array"
                                    ],
                                    "description": "One row of the exact 3 by 3 matrix.",
                                    "items": {
                                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                        "title": "fraction",
                                        "x-optimade-type": "string",
                                        "x-optimade-definition": {
                                            "label": "fraction_core",
                                            "kind": "property",
                                            "version": "0.1.0",
                                            "format": "1.3",
                                            "name": "fraction"
                                        },
                                        "type": [
                                            "string",
                                            "null"
                                        ],
                                        "description": "A fraction represented as a string.",
                                        "examples": [
                                            "2/3",
                                            "5/42",
                                            "10",
                                            "0"
                                        ],
                                        "x-optimade-unit": "inapplicable"
                                    }
                                }
                            },
                            "vector": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "x-optimade-dimensions": {
                                    "names": [
                                        "dim_lattice"
                                    ],
                                    "sizes": [
                                        3
                                    ]
                                },
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Exact fractional-coordinate vector part of the affine transformation.",
                                "items": {
                                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                    "title": "fraction",
                                    "x-optimade-type": "string",
                                    "x-optimade-definition": {
                                        "label": "fraction_core",
                                        "kind": "property",
                                        "version": "0.1.0",
                                        "format": "1.3",
                                        "name": "fraction"
                                    },
                                    "type": [
                                        "string",
                                        "null"
                                    ],
                                    "description": "A fraction represented as a string.",
                                    "examples": [
                                        "2/3",
                                        "5/42",
                                        "10",
                                        "0"
                                    ],
                                    "x-optimade-unit": "inapplicable"
                                }
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the affine transformation in `x,y,z` notation."
                            },
                            "det": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Determinant of the matrix part when emitted by the generator."
                            },
                            "is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the matrix part is orthogonal."
                            }
                        },
                        "examples": [
                            {
                                "matrix": [
                                    [
                                        "-1",
                                        "0",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "-1",
                                        "0"
                                    ],
                                    [
                                        "0",
                                        "0",
                                        "1"
                                    ]
                                ],
                                "vector": [
                                    "0",
                                    "0",
                                    "0"
                                ],
                                "xyz": "-x,-y,z",
                                "det": 1,
                                "is_orthogonal": true
                            }
                        ]
                    },
                    "rot_type": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Symbolic crystallographic operation-type label for the linear part."
                    },
                    "type": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Legacy numeric point-group operation-type code."
                    },
                    "axis": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Integer-vector axis or invariant-direction descriptor for the operation.",
                        "items": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer"
                            ],
                            "description": "One integer component of the axis vector."
                        }
                    },
                    "sense": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Rotation sense/sign convention returned by the generator."
                    },
                    "screw_glide": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Screw-axis or glide-plane component represented exactly as a list of fraction strings.",
                        "items": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                            "title": "fraction",
                            "x-optimade-type": "string",
                            "x-optimade-definition": {
                                "label": "fraction_core",
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "fraction"
                            },
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "A fraction represented as a string.",
                            "examples": [
                                "2/3",
                                "5/42",
                                "10",
                                "0"
                            ],
                            "x-optimade-unit": "inapplicable"
                        }
                    },
                    "origin_shift": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Origin-shift descriptor represented exactly as a list of fraction strings.",
                        "items": {
                            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                            "title": "fraction",
                            "x-optimade-type": "string",
                            "x-optimade-definition": {
                                "label": "fraction_core",
                                "kind": "property",
                                "version": "0.1.0",
                                "format": "1.3",
                                "name": "fraction"
                            },
                            "type": [
                                "string",
                                "null"
                            ],
                            "description": "A fraction represented as a string.",
                            "examples": [
                                "2/3",
                                "5/42",
                                "10",
                                "0"
                            ],
                            "x-optimade-unit": "inapplicable"
                        }
                    },
                    "is_proper": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether the linear operation is proper."
                    }
                },
                "examples": [
                    {
                        "affine_transformation": {
                            "matrix": [
                                [
                                    "-1",
                                    "0",
                                    "0"
                                ],
                                [
                                    "0",
                                    "-1",
                                    "0"
                                ],
                                [
                                    "0",
                                    "0",
                                    "1"
                                ]
                            ],
                            "vector": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "-x,-y,z",
                            "det": 1,
                            "is_orthogonal": true
                        },
                        "rot_type": "2",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            1
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            },
            "examples": [
                [
                    {
                        "affine_transformation": {
                            "matrix": [
                                [
                                    "1",
                                    "0",
                                    "0"
                                ],
                                [
                                    "0",
                                    "1",
                                    "0"
                                ],
                                [
                                    "0",
                                    "0",
                                    "1"
                                ]
                            ],
                            "vector": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "x,y,z"
                        },
                        "rot_type": "1",
                        "sense": 0,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "screw_glide": [
                            "0",
                            "0",
                            "0"
                        ],
                        "origin_shift": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            ]
        },
        "symops_representative_xyz": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative_xyz",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symops Representative Xyz",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops_representative_xyz",
                "label": "symops_representative_xyz_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Representative symmetry operations modulo centering translations in fractional `x,y,z` notation, ordered consistently with `symops_representative`.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string"
                ]
            },
            "examples": [
                [
                    "x,y,z"
                ],
                [
                    "-x,y,-z",
                    "x,y,z"
                ]
            ]
        },
        "symops_xyz": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_xyz",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operations in x,y,z notation",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "symops_xyz",
                "label": "symops_xyz_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Full list of symmetry operations for the space-group setting written in fractional `x,y,z` coordinate notation. Each expression acts on fractional coordinates in the setting represented by the containing Hall entry.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "string",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "string"
                ],
                "description": "One symmetry operation in x,y,z notation."
            },
            "examples": [
                [
                    "x,y,z"
                ],
                [
                    "-x,-y,-z",
                    "x,y,z"
                ]
            ],
            "x-compatibility": [
                "https://schemas.optimade.org/defs/v1.2/properties/optimade/structures/space_group_symmetry_operations_xyz"
            ]
        },
        "wyckoff": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Wyckoff positions",
            "$comment": "Anyterial Wyckoff-position list property using the common wyckoff-position record definition.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "wyckoff",
                "label": "wyckoff_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Wyckoff-position table for a specific space-group setting.\nEach list item describes one Wyckoff position and includes the Wyckoff letter as ordinary data.\nThis list representation avoids using JSON dictionary keys as crystallographic data.\nItems follow `/properties/symmetry/wyckoff_position`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each item MUST include `letter`, identifying the Wyckoff letter for that position in the setting.\n- `orbit_affine` and `orbit_xyz` contain the full orbit.\n- `orbit_mod_centering_affine` and `orbit_mod_centering_xyz` contain one representative modulo centering translations.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/wyckoff_position",
                "title": "Wyckoff position",
                "$comment": "Reusable Anyterial definition for one Wyckoff-position record in a space-group setting.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "wyckoff_position",
                    "label": "wyckoff_position_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One Wyckoff position in a space-group setting.\nThe record gives the multiplicity, oriented site-symmetry symbol, representative coordinate, full orbit, and orbit factorized modulo centering translations.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **letter**: REQUIRED; String.\n      Wyckoff letter for this position in the setting.\n\n    - **multiplicity**: REQUIRED; Integer.\n      Multiplicity of the Wyckoff position in the conventional cell.\n\n    - **sitesym**: REQUIRED; String.\n      Oriented site-symmetry symbol.\n\n    - **hasfreedom**: REQUIRED; List of booleans.\n      Flags indicating whether each fractional coordinate has a free parameter.\n\n    - **first\\_orbit**: REQUIRED; String.\n      First representative coordinate expression used by the generator.\n\n    - **orbit\\_affine**: REQUIRED; List.\n      Full orbit in affine matrix/vector representation.\n\n    - **orbit\\_xyz**: REQUIRED; List of strings.\n      Full orbit in `x,y,z` coordinate notation.\n\n    - **orbit\\_mod\\_centering\\_affine**: REQUIRED; List.\n      Orbit representatives modulo centering translations in affine representation.\n\n    - **orbit\\_mod\\_centering\\_xyz**: REQUIRED; List of strings.\n      Orbit representatives modulo centering translations in `x,y,z` notation.",
                "properties": {
                    "letter": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Wyckoff letter for this position in the setting."
                    },
                    "multiplicity": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Multiplicity of the Wyckoff position in the conventional cell."
                    },
                    "sitesym": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Oriented site-symmetry symbol."
                    },
                    "hasfreedom": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "x-optimade-dimensions": {
                            "names": [
                                "dim_lattice"
                            ],
                            "sizes": [
                                3
                            ]
                        },
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Three flags indicating whether each fractional coordinate contains a free parameter.",
                        "items": {
                            "x-optimade-type": "boolean",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "boolean"
                            ],
                            "description": "Whether the corresponding coordinate is free."
                        }
                    },
                    "first_orbit_ita": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Representative coordinate expression following the ITA source convention, when distinct from `first_orbit`."
                    },
                    "first_orbit": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Representative coordinate expression for the Wyckoff position."
                    },
                    "orbit_affine": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Full orbit represented as affine matrix/vector data.",
                        "items": {
                            "x-optimade-type": "list",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array"
                            ],
                            "description": "One generator-emitted affine orbit operation represented as nested exact lists.",
                            "items": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array"
                                ],
                                "description": "One row or component list of the affine orbit representation.",
                                "items": {
                                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                    "title": "fraction",
                                    "x-optimade-type": "string",
                                    "x-optimade-definition": {
                                        "label": "fraction_core",
                                        "kind": "property",
                                        "version": "0.1.0",
                                        "format": "1.3",
                                        "name": "fraction"
                                    },
                                    "type": [
                                        "string",
                                        "null"
                                    ],
                                    "description": "A fraction represented as a string.",
                                    "examples": [
                                        "2/3",
                                        "5/42",
                                        "10",
                                        "0"
                                    ],
                                    "x-optimade-unit": "inapplicable"
                                }
                            }
                        }
                    },
                    "orbit_xyz": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Full orbit represented as `x,y,z` coordinate expressions.",
                        "items": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string"
                            ],
                            "description": "One coordinate expression."
                        }
                    },
                    "orbit_mod_centering_affine": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Orbit representatives modulo centering translations in affine matrix/vector representation.",
                        "items": {
                            "x-optimade-type": "list",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array"
                            ],
                            "description": "One generator-emitted affine orbit operation represented as nested exact lists.",
                            "items": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array"
                                ],
                                "description": "One row or component list of the affine orbit representation.",
                                "items": {
                                    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/fraction",
                                    "title": "fraction",
                                    "x-optimade-type": "string",
                                    "x-optimade-definition": {
                                        "label": "fraction_core",
                                        "kind": "property",
                                        "version": "0.1.0",
                                        "format": "1.3",
                                        "name": "fraction"
                                    },
                                    "type": [
                                        "string",
                                        "null"
                                    ],
                                    "description": "A fraction represented as a string.",
                                    "examples": [
                                        "2/3",
                                        "5/42",
                                        "10",
                                        "0"
                                    ],
                                    "x-optimade-unit": "inapplicable"
                                }
                            }
                        }
                    },
                    "orbit_mod_centering_xyz": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Orbit representatives modulo centering translations as `x,y,z` coordinate expressions.",
                        "items": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string"
                            ],
                            "description": "One coordinate expression."
                        }
                    }
                },
                "examples": [
                    {
                        "letter": "e",
                        "multiplicity": 2,
                        "sitesym": "1",
                        "hasfreedom": [
                            true,
                            true,
                            true
                        ],
                        "first_orbit": "x,y,z",
                        "orbit_xyz": [
                            "x",
                            "y",
                            "z",
                            "-x",
                            "y",
                            "-z"
                        ],
                        "orbit_mod_centering_xyz": [
                            "x",
                            "y",
                            "z",
                            "-x",
                            "y",
                            "-z"
                        ]
                    }
                ]
            },
            "examples": [
                [
                    {
                        "letter": "e",
                        "multiplicity": 2,
                        "sitesym": "1",
                        "hasfreedom": [
                            true,
                            true,
                            true
                        ],
                        "first_orbit": "x,y,z",
                        "orbit_xyz": [
                            "x",
                            "y",
                            "z",
                            "-x",
                            "y",
                            "-z"
                        ],
                        "orbit_mod_centering_xyz": [
                            "x",
                            "y",
                            "z",
                            "-x",
                            "y",
                            "-z"
                        ]
                    }
                ]
            ]
        },
        "wyckoff_sets": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Wyckoff Sets",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "wyckoff_sets",
                "label": "wyckoff_sets_spacegroups"
            },
            "type": [
                "array",
                "null"
            ],
            "description": "Sets of Wyckoff letters related by normalizer operations. Each inner list groups Wyckoff positions that can be interchanged by the relevant normalizer action.",
            "x-optimade-unit": "inapplicable",
            "items": {
                "x-optimade-type": "list",
                "type": [
                    "array",
                    "null"
                ],
                "description": "One Wyckoff-set combination.",
                "items": {
                    "x-optimade-type": "string",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Wyckoff letter.",
                    "x-optimade-unit": "inapplicable"
                },
                "x-optimade-unit": "inapplicable"
            },
            "examples": [
                [
                    [
                        "a"
                    ]
                ],
                [
                    [
                        "i"
                    ],
                    [
                        "h"
                    ],
                    [
                        "g"
                    ]
                ]
            ]
        },
        "asu_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Asymmetric unit markups",
            "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "asu_markup",
                "label": "asu_markup_spacegroups"
            },
            "description": "Display-oriented renderings of the plain-string asymmetric-unit restrictions in `asu_str`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        },
        "asu_shape_only_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Shape-only asymmetric unit markups",
            "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "asu_shape_only_markup",
                "label": "asu_shape_only_markup_spacegroups"
            },
            "description": "Display-oriented renderings of the plain-string shape-only asymmetric-unit restrictions in `asu_shape_only_str`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        },
        "hall_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hall symbol markups",
            "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hall_markup",
                "label": "hall_markup_spacegroups"
            },
            "description": "Display-oriented renderings of the Hall symbol in `hall`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        },
        "hall_aliases_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hall alias markups",
            "$comment": "Anyterial symmetry property definition using the common string markup object for each list item.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hall_aliases_markup",
                "label": "hall_aliases_markup_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Display-oriented renderings corresponding element-by-element to the alternate Hall symbols in `hall_aliases`.\nThe plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups",
                "title": "String markups",
                "$comment": "Reusable Anyterial definition for alternate display renderings of an ASCII/text string.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "string_markups",
                    "label": "string_markups_core"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "Alternate markup renderings of a string whose plain-text or ASCII value is provided by a sibling property.\nThe object is intended for display-oriented variants only; the corresponding unsuffixed sibling property remains the canonical plain string value.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **html**: OPTIONAL; String.\n      HTML rendering of the sibling string, using inline HTML elements where needed for typographic structure such as subscripts, superscripts, overlines, fractions, and line breaks.\n\n    - **latex**: OPTIONAL; String.\n      LaTeX rendering of the sibling string, suitable for use with a LaTeX or MathJax-like renderer.\n\n    - **unicode**: OPTIONAL; String.\n      Unicode rendering of the sibling string, using Unicode code points for display features where practical.",
                "properties": {
                    "html": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "HTML rendering of the sibling string."
                    },
                    "latex": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "LaTeX rendering of the sibling string."
                    },
                    "unicode": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Unicode rendering of the sibling string."
                    }
                },
                "examples": [
                    {
                        "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                        "latex": "\\mathit{P}\\,2_{1}/c",
                        "unicode": "P2\u2081/c"
                    }
                ]
            },
            "examples": [
                [
                    {
                        "html": "<i>P</i> 1",
                        "latex": "\\mathrm{P} 1",
                        "unicode": "P 1"
                    }
                ]
            ]
        },
        "hm_short_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Short Hermann-Mauguin symbol markups",
            "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_short_markup",
                "label": "hm_short_markup_spacegroups"
            },
            "description": "Display-oriented renderings of the setting-specific short Hermann-Mauguin symbol in `hm_short`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        },
        "hm_short_std_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Standard short Hermann-Mauguin symbol markups",
            "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_short_std_markup",
                "label": "hm_short_std_markup_spacegroups"
            },
            "description": "Display-oriented renderings of the ITA-standard short Hermann-Mauguin symbol in `hm_short_std`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        },
        "hm_full_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Full Hermann-Mauguin symbol markups",
            "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_full_markup",
                "label": "hm_full_markup_spacegroups"
            },
            "description": "Display-oriented renderings of the setting-specific full Hermann-Mauguin symbol in `hm_full`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        },
        "hm_full_std_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Standard full Hermann-Mauguin symbol markups",
            "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_full_std_markup",
                "label": "hm_full_std_markup_spacegroups"
            },
            "description": "Display-oriented renderings of the ITA-standard full Hermann-Mauguin symbol in `hm_full_std`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        },
        "hm_extended_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Extended Hermann-Mauguin symbol markups",
            "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_extended_markup",
                "label": "hm_extended_markup_spacegroups"
            },
            "description": "Display-oriented renderings of the extended Hermann-Mauguin symbol in `hm_extended`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        },
        "hm_short_aliases_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Short Hermann-Mauguin alias markups",
            "$comment": "Anyterial symmetry property definition using the common string markup object for each list item.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_short_aliases_markup",
                "label": "hm_short_aliases_markup_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Display-oriented renderings corresponding element-by-element to the alternate short Hermann-Mauguin symbols in `hm_short_aliases`.\nThe plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups",
                "title": "String markups",
                "$comment": "Reusable Anyterial definition for alternate display renderings of an ASCII/text string.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "string_markups",
                    "label": "string_markups_core"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "Alternate markup renderings of a string whose plain-text or ASCII value is provided by a sibling property.\nThe object is intended for display-oriented variants only; the corresponding unsuffixed sibling property remains the canonical plain string value.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **html**: OPTIONAL; String.\n      HTML rendering of the sibling string, using inline HTML elements where needed for typographic structure such as subscripts, superscripts, overlines, fractions, and line breaks.\n\n    - **latex**: OPTIONAL; String.\n      LaTeX rendering of the sibling string, suitable for use with a LaTeX or MathJax-like renderer.\n\n    - **unicode**: OPTIONAL; String.\n      Unicode rendering of the sibling string, using Unicode code points for display features where practical.",
                "properties": {
                    "html": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "HTML rendering of the sibling string."
                    },
                    "latex": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "LaTeX rendering of the sibling string."
                    },
                    "unicode": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Unicode rendering of the sibling string."
                    }
                },
                "examples": [
                    {
                        "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                        "latex": "\\mathit{P}\\,2_{1}/c",
                        "unicode": "P2\u2081/c"
                    }
                ]
            },
            "examples": [
                [
                    {
                        "html": "<i>P</i> 1",
                        "latex": "\\mathrm{P} 1",
                        "unicode": "P 1"
                    }
                ]
            ]
        },
        "hm_full_aliases_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Full Hermann-Mauguin alias markups",
            "$comment": "Anyterial symmetry property definition using the common string markup object for each list item.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_full_aliases_markup",
                "label": "hm_full_aliases_markup_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Display-oriented renderings corresponding element-by-element to the alternate full Hermann-Mauguin symbols in `hm_full_aliases`.\nThe plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups",
                "title": "String markups",
                "$comment": "Reusable Anyterial definition for alternate display renderings of an ASCII/text string.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "string_markups",
                    "label": "string_markups_core"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "Alternate markup renderings of a string whose plain-text or ASCII value is provided by a sibling property.\nThe object is intended for display-oriented variants only; the corresponding unsuffixed sibling property remains the canonical plain string value.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **html**: OPTIONAL; String.\n      HTML rendering of the sibling string, using inline HTML elements where needed for typographic structure such as subscripts, superscripts, overlines, fractions, and line breaks.\n\n    - **latex**: OPTIONAL; String.\n      LaTeX rendering of the sibling string, suitable for use with a LaTeX or MathJax-like renderer.\n\n    - **unicode**: OPTIONAL; String.\n      Unicode rendering of the sibling string, using Unicode code points for display features where practical.",
                "properties": {
                    "html": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "HTML rendering of the sibling string."
                    },
                    "latex": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "LaTeX rendering of the sibling string."
                    },
                    "unicode": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Unicode rendering of the sibling string."
                    }
                },
                "examples": [
                    {
                        "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                        "latex": "\\mathit{P}\\,2_{1}/c",
                        "unicode": "P2\u2081/c"
                    }
                ]
            },
            "examples": [
                [
                    {
                        "html": "<i>P</i> 1",
                        "latex": "\\mathrm{P} 1",
                        "unicode": "P 1"
                    }
                ]
            ]
        },
        "hm_extended_aliases_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Extended Hermann-Mauguin alias markups",
            "$comment": "Anyterial symmetry property definition using the common string markup object for each list item.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hm_extended_aliases_markup",
                "label": "hm_extended_aliases_markup_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Display-oriented renderings corresponding element-by-element to the alternate extended Hermann-Mauguin symbols in `hm_extended_aliases`.\nThe plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups",
                "title": "String markups",
                "$comment": "Reusable Anyterial definition for alternate display renderings of an ASCII/text string.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "string_markups",
                    "label": "string_markups_core"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "Alternate markup renderings of a string whose plain-text or ASCII value is provided by a sibling property.\nThe object is intended for display-oriented variants only; the corresponding unsuffixed sibling property remains the canonical plain string value.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **html**: OPTIONAL; String.\n      HTML rendering of the sibling string, using inline HTML elements where needed for typographic structure such as subscripts, superscripts, overlines, fractions, and line breaks.\n\n    - **latex**: OPTIONAL; String.\n      LaTeX rendering of the sibling string, suitable for use with a LaTeX or MathJax-like renderer.\n\n    - **unicode**: OPTIONAL; String.\n      Unicode rendering of the sibling string, using Unicode code points for display features where practical.",
                "properties": {
                    "html": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "HTML rendering of the sibling string."
                    },
                    "latex": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "LaTeX rendering of the sibling string."
                    },
                    "unicode": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Unicode rendering of the sibling string."
                    }
                },
                "examples": [
                    {
                        "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                        "latex": "\\mathit{P}\\,2_{1}/c",
                        "unicode": "P2\u2081/c"
                    }
                ]
            },
            "examples": [
                [
                    {
                        "html": "<i>P</i> 1",
                        "latex": "\\mathrm{P} 1",
                        "unicode": "P 1"
                    }
                ]
            ]
        },
        "schoenflies_markup": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies_markup",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Schoenflies symbol markups",
            "$comment": "Anyterial symmetry property definition inheriting the common string markup object.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "schoenflies_markup",
                "label": "schoenflies_markup_spacegroups"
            },
            "description": "Display-oriented renderings of the Schoenflies symbol in `schoenflies`.\nThe plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.",
            "x-optimade-type": "dictionary",
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "properties": {
                "html": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "HTML rendering of the sibling string."
                },
                "latex": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "LaTeX rendering of the sibling string."
                },
                "unicode": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Unicode rendering of the sibling string."
                }
            },
            "examples": [
                {
                    "html": "<i>P</i> 2<sub>1</sub>/<i>c</i>",
                    "latex": "\\mathit{P}\\,2_{1}/c",
                    "unicode": "P2\u2081/c"
                }
            ]
        }
    }
}
```