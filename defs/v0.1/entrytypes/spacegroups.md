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

* **[Affine images (affine_images)](../properties/spacegroups/affine_images.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images.md)  
  Same-space-group affine images for a standard setting.
The list combines Euclidean normalizer operations and isomorphic subgroup transforms to enumerate alternative affine images of the same space group used by runtime search code.
Matrix/vector transform fields use `pmat` and `pvec` according to `/properties/symmetry/basis_transform`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Affine normalizer (affine_normalizer)](../properties/spacegroups/affine_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer.md)  
  Bounded affine normalizer coset representatives modulo the space group, generated from bounded unimodular integer linear parts. This is a finite representative table, not a complete infinite affine normalizer.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary with the following keys:
    
        - **items**: REQUIRED; List of dictionaries.
          Listed normalizer operations or coset representatives.
          Each item follows `/properties/symmetry/normalizer_representative`.
    
        - **n\_cosets**: OPTIONAL; Integer.
          Number of listed coset representatives when the parent table is a coset table.
    
        - **n\_orthogonal\_cosets**: OPTIONAL; Integer.
          Number of listed representatives whose linear part is orthogonal.
    
        - **candidate\_set**: OPTIONAL; String.
          Name of the candidate set used for generation.
    
        - **candidate\_sets**: OPTIONAL; List of strings.
          Candidate-set names used for generation.
    
        - **bounds**: OPTIONAL; Dictionary.
          Generator bounds for finite bounded candidate searches.


* **[Affine normalizer coset data (affine_normalizer_coset_data)](../properties/spacegroups/affine_normalizer_coset_data.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_coset_data`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_coset_data.md)  
  Ordered table of affine normalizer coset representative data by Hall setting.
Each row contains the finite listed coset representatives used by the symmetry-finder runtime for one Hall setting, plus counts and candidate-set metadata.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary MUST contain a `hall_entry` value that can be used with `hall_symbol_to_affine_normalizer_coset_data` to locate the same row.
    - The `affine_normalizer_cosets` field contains bounded unimodular-integer affine normalizer coset representatives modulo the space group.
    - The `orthogonal_affine_normalizer_cosets` field contains the signed-permutation subset retained for the orthogonal retry mode.
    - These are bounded finite representative tables, not complete infinite affine normalizers.


* **[Affine normalizer cosets (affine_normalizer_cosets)](../properties/spacegroups/affine_normalizer_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_cosets.md)  
  Runtime list of bounded affine normalizer coset representatives modulo the space group.
Each item is one finite listed representative and follows `/properties/symmetry/normalizer_representative`.
The list is a bounded representative table, not a complete infinite affine normalizer.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Asu](../properties/spacegroups/asu.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu.md)  
  Structured asymmetric-unit description for the space-group setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    The asymmetric unit is represented as a list of half-space cuts and logical cut expressions in fractional coordinates. Together these cuts define a representative region of the unit cell from which the full space group can generate all equivalent positions.
    
    **Requirements/Conventions**:
    
    - `cuts` contains the complete serialized cut tree.
    - `shape_only_cuts` contains only the geometric shape restrictions, omitting some conditional refinements.
    - The formatted `asu_*` fields provide compact textual renderings of the same information.


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

* **[Backward lift criteria (backward_lift_criteria)](../properties/spacegroups/backward_lift_criteria.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/backward_lift_criteria`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/backward_lift_criteria.md)  
  Criteria table used to lift occupied Wyckoff data from a subgroup back to a supergroup along a chosen Bärnighausen transform.
The outer map is keyed by supergroup IT number and the next map is keyed by subgroup IT number.
Values are lists of transform records carrying a basis transform and a dictionary of Wyckoff-letter criteria.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - Dynamic outer keys MUST be supergroup IT numbers represented as strings.
    - Dynamic second-level keys MUST be subgroup IT numbers represented as strings.
    - Transform records SHOULD include `index`, `pmat`, `pvec`, and `criteria`.


* **[Bärnighausen subgroup transforms (baernighausen)](../properties/spacegroups/baernighausen.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/baernighausen`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/baernighausen.md)  
  Bärnighausen subgroup transform table. Entries describe generated embeddings of a subgroup setting into a supergroup setting.
The outer dictionary is keyed by the parent table convention, for example Hall entries or IT numbers.
Transform records use `pmat` and `pvec` as defined by `/properties/symmetry/basis_transform`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - Dynamic outer keys identify parent settings or space groups according to the containing dataset.
    - Values are either dictionaries containing an `items` list of transform records or direct maps to lists of transform records.
    - Each transform record SHOULD follow `/properties/symmetry/basis_transform` for its matrix and vector fields.


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


* **[Continuous Euclidean normalizer (continuous_euclidean_normalizer)](../properties/spacegroups/continuous_euclidean_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_euclidean_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_euclidean_normalizer.md)  
  Continuous Euclidean normalizer subspace before aggregation into the public transformation tables. It records the dimension and basis vectors of allowed continuous origin shifts.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary with the following keys:
    
        - **dimension**: OPTIONAL; Integer.
          Dimension of the continuous parameter subspace.
    
        - **basis\_vectors**: REQUIRED; List of vectors.
          Basis vectors spanning the continuous normalizer parameter space.
          Each basis vector is represented as exact fractional-coordinate components.
    
        - **coordinate\_system**: OPTIONAL; String.
          Coordinate system used for the parameter vectors.
    
        - **representation**: OPTIONAL; String.
          Textual description of the parameterized representation.


* **[Continuous normalizer (continuous_normalizer)](../properties/spacegroups/continuous_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_normalizer.md)  
  Parameterized continuous normalizer subspace for a setting. It describes continuous origin-shift freedoms by dimension and fractional-coordinate basis vectors rather than by enumerating infinitely many operations.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary with the following keys:
    
        - **dimension**: OPTIONAL; Integer.
          Dimension of the continuous parameter subspace.
    
        - **basis\_vectors**: REQUIRED; List of vectors.
          Basis vectors spanning the continuous normalizer parameter space.
          Each basis vector is represented as exact fractional-coordinate components.
    
        - **coordinate\_system**: OPTIONAL; String.
          Coordinate system used for the parameter vectors.
    
        - **representation**: OPTIONAL; String.
          Textual description of the parameterized representation.


* **[Crystal System (crystal_system)](../properties/spacegroups/crystal_system.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/crystal_system`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/crystal_system.md)  
  The crystal system of the space group or point group.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    Values use the conventional crystallographic system names such as triclinic, monoclinic, orthorhombic, tetragonal, trigonal, hexagonal, and cubic.


* **[Euclidean normalizer (euclidean_normalizer)](../properties/spacegroups/euclidean_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/euclidean_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/euclidean_normalizer.md)  
  Finite Euclidean normalizer operations of a Hall setting, generated from cctbx. These are metric-preserving operations that normalize the space group in the chosen setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary with the following keys:
    
        - **items**: REQUIRED; List of dictionaries.
          Listed normalizer operations or coset representatives.
          Each item follows `/properties/symmetry/normalizer_representative`.
    
        - **n\_cosets**: OPTIONAL; Integer.
          Number of listed coset representatives when the parent table is a coset table.
    
        - **n\_orthogonal\_cosets**: OPTIONAL; Integer.
          Number of listed representatives whose linear part is orthogonal.
    
        - **candidate\_set**: OPTIONAL; String.
          Name of the candidate set used for generation.
    
        - **candidate\_sets**: OPTIONAL; List of strings.
          Candidate-set names used for generation.
    
        - **bounds**: OPTIONAL; Dictionary.
          Generator bounds for finite bounded candidate searches.


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


* **[Hall-symbol to affine normalizer coset data index (hall_symbol_to_affine_normalizer_coset_data)](../properties/spacegroups/hall_symbol_to_affine_normalizer_coset_data.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_symbol_to_affine_normalizer_coset_data`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_symbol_to_affine_normalizer_coset_data.md)  
  Index from normalized Hall entries to row positions in the top-level `affine_normalizer_coset_data` table.
It allows consumers to look up affine normalizer coset data by Hall entry while keeping `affine_normalizer_coset_data` as a compact ordered list.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.
    - Each value MUST be a zero-based integer index into the top-level `affine_normalizer_coset_data` list.
    - For every key-value pair, `affine_normalizer_coset_data[value].hall_entry` MUST equal the key.


* **[Index Hall entry to space-group symbols (index_hall_entry_to_spacegroup_symbols)](../properties/spacegroups/index_hall_entry_to_spacegroup_symbols.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroup_symbols`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroup_symbols.md)  
  Index from normalized Hall entries to row positions in the top-level `spacegroup_symbols` table.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.
    - Values MUST be non-negative integer row indices into `data.spacegroup_symbols`.


* **[Hall-entry to spacegroups index (index_hall_entry_to_spacegroups)](../properties/spacegroups/index_hall_entry_to_spacegroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroups.md)  
  Index from normalized Hall entries to row positions in the top-level `spacegroups` table.
It allows consumers to look up a space-group setting by Hall entry while keeping `spacegroups` as a compact ordered list.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.
    - Each value MUST be a zero-based integer index into the top-level `spacegroups` list.
    - For every key-value pair, `spacegroups[value].hall_entry` MUST equal the key.


* **[IT number to spglib default spacegroups index (index_it_number_to_spglib_default_spacegroups)](../properties/spacegroups/index_it_number_to_spglib_default_spacegroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_it_number_to_spglib_default_spacegroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_it_number_to_spglib_default_spacegroups.md)  
  IT-number keyed lookup from the default spglib Hall setting to the corresponding row index in the top-level `spacegroups` list.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary.
    - Keys MUST be International Tables space-group numbers encoded as strings.
    - Values MUST be list indices into the top-level `spacegroups` array of `symmetry_basics.json.gz`.


* **[IT number to std spacegroups index (index_it_number_to_std_spacegroups)](../properties/spacegroups/index_it_number_to_std_spacegroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_it_number_to_std_spacegroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_it_number_to_std_spacegroups.md)  
  IT-number keyed lookup from the International Tables standard setting to the corresponding row index in the top-level `spacegroups` list.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary.
    - Keys MUST be International Tables space-group numbers encoded as strings.
    - Values MUST be list indices into the top-level `spacegroups` array of `symmetry_basics.json.gz`.


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


* **[Hall to IT std transform (hall_to_it_std_transform)](../properties/spacegroups/hall_to_it_std_transform.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_to_it_std_transform`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_to_it_std_transform.md)  
  Hall-keyed exact change-of-basis transforms from each Hall setting to the IT-standard Hall reference setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary.
    - Keys MUST be Hall-entry identifiers encoded in computer notation.
    - Values MUST be dictionaries describing one exact basis transform to the IT standard Hall reference setting.


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


* **[Index](../properties/spacegroups/index.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index.md)  
  Subgroup or transform index. For subgroup transforms it is the crystallographic subgroup index `[G:H]`, equal to the determinant factor of the basis transformation when applicable.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

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

* **[Isomorphic subgroup transforms (isomorphic_subgroups)](../properties/spacegroups/isomorphic_subgroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups.md)  
  Isomorphic subgroup transforms of bounded index. These transforms map a space group to a subgroup of the same space-group type, usually corresponding to an enlarged unit cell.
The outer dictionary is keyed by the parent table convention, for example Hall entries or IT numbers.
Transform records use `pmat` and `pvec` as defined by `/properties/symmetry/basis_transform`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - Dynamic outer keys identify parent settings or space groups according to the containing dataset.
    - Values are either dictionaries containing an `items` list of transform records or direct maps to lists of transform records.
    - Each transform record SHOULD follow `/properties/symmetry/basis_transform` for its matrix and vector fields.


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

* **[Items](../properties/spacegroups/items.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/items`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/items.md)  
  Generic ordered data-list container used by several generated JSON-LD datasets.
The item schema is defined by the containing dataset or parent property.
This property is intentionally generic because `items` is used for symbol rows, transform rows, and normalizer rows in different contexts.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Klassengleiche subgroup subtype (k_subtype)](../properties/spacegroups/k_subtype.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/k_subtype`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/k_subtype.md)  
  Subtype of a klassengleiche (`k`) subgroup relation. Values distinguish loss of centering translations from enlarged-unit-cell subgroups; the value is null for non-`k` relations.

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

* **[N Coset Representatives (n_coset_representatives)](../properties/spacegroups/n_coset_representatives.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_coset_representatives`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_coset_representatives.md)  
  Number of nontrivial coset representatives retained after deduplication modulo the space group.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[N Cosets (n_cosets)](../properties/spacegroups/n_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_cosets.md)  
  Number of affine normalizer coset representatives stored for the setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[N Linear Parts (n_linear_parts)](../properties/spacegroups/n_linear_parts.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_linear_parts`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_linear_parts.md)  
  Number of distinct linear matrix parts represented in a normalizer or transform table.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[N Orthogonal Cosets (n_orthogonal_cosets)](../properties/spacegroups/n_orthogonal_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_orthogonal_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_orthogonal_cosets.md)  
  Number of orthogonal affine normalizer coset representatives stored for the setting.

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

* **[N Raw Candidates (n_raw_candidates)](../properties/spacegroups/n_raw_candidates.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_raw_candidates`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_raw_candidates.md)  
  Number of candidate affine operations considered before filtering and deduplication.

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

* **[N Unique Candidates (n_unique_candidates)](../properties/spacegroups/n_unique_candidates.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_unique_candidates`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_unique_candidates.md)  
  Number of candidate affine operations remaining after exact duplicate removal.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Orthogonal affine normalizer (orthogonal_affine_normalizer)](../properties/spacegroups/orthogonal_affine_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer.md)  
  Orthogonal affine normalizer coset representatives modulo the space group from the signed-permutation subset of affine candidates.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary with the following keys:
    
        - **items**: REQUIRED; List of dictionaries.
          Listed normalizer operations or coset representatives.
          Each item follows `/properties/symmetry/normalizer_representative`.
    
        - **n\_cosets**: OPTIONAL; Integer.
          Number of listed coset representatives when the parent table is a coset table.
    
        - **n\_orthogonal\_cosets**: OPTIONAL; Integer.
          Number of listed representatives whose linear part is orthogonal.
    
        - **candidate\_set**: OPTIONAL; String.
          Name of the candidate set used for generation.
    
        - **candidate\_sets**: OPTIONAL; List of strings.
          Candidate-set names used for generation.
    
        - **bounds**: OPTIONAL; Dictionary.
          Generator bounds for finite bounded candidate searches.


* **[Orthogonal affine normalizer cosets (orthogonal_affine_normalizer_cosets)](../properties/spacegroups/orthogonal_affine_normalizer_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets.md)  
  Runtime list of orthogonal signed-permutation affine normalizer coset representatives modulo the space group.
Each item is one finite listed representative and follows `/properties/symmetry/normalizer_representative`.
The list is a bounded representative table, not a complete infinite affine normalizer.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Basis transformation matrix (pmat)](../properties/spacegroups/pmat.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pmat`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pmat.md)  
  Matrix part of a crystallographic basis or setting transformation.
This emitted space-group property uses the common `/properties/symmetry/pmat` definition for its nested value shape and dimensional metadata.

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


* **[Basis transformation origin shift (pvec)](../properties/spacegroups/pvec.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pvec`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pvec.md)  
  Translation or origin-shift vector of a crystallographic basis or setting transformation.
This emitted space-group property uses the common `/properties/symmetry/pvec` definition for its nested value shape and dimensional metadata.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Maximal subgroup relations (maximal_subgroup_relations)](../properties/spacegroups/maximal_subgroup_relations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/maximal_subgroup_relations`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/maximal_subgroup_relations.md)  
  Maximal non-isomorphic subgroup relations for International Tables space-group types.
The dictionary is keyed by supergroup IT number and each value is a list of subgroup-relation records.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary whose dynamic keys are International Tables space-group numbers represented as strings.
    - Each value MUST be a list of dictionaries.
    - Each dictionary MUST describe one generated maximal subgroup relation and include the subgroup IT number, subgroup index, subgroup type, and optional klassengleiche subtype.


* **[Symmetry operation linear matrix (rmat)](../properties/spacegroups/rmat.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat.md)  
  Linear matrix part of a same-setting affine operation.
This emitted space-group property uses the common `/properties/symmetry/rmat` definition for its nested value shape and dimensional metadata.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Symmetry operation rotation determinant (rmat_det)](../properties/spacegroups/rmat_det.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_det`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_det.md)  
  Determinant of the `rmat` linear matrix part of a same-setting operation.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Symmetry operation rotation is orthogonal (rmat_is_orthogonal)](../properties/spacegroups/rmat_is_orthogonal.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_is_orthogonal`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_is_orthogonal.md)  
  Boolean flag indicating whether `rmat` is orthogonal in the conventional coordinate basis.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

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


* **[Space groups (spacegroups)](../properties/spacegroups/spacegroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroups.md)  
  Ordered table of crystallographic space-group setting records.
Each item describes one concrete Hall/International Tables setting of a space group, including symbols, classifications, symmetry operations, asymmetric-unit information, Wyckoff positions, and related auxiliary data.
The companion `index_hall_entry_to_spacegroups` property maps normalized Hall entries to indices in this list.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - Items MUST be ordered in the same setting order as `spacegroup_symbols.json.gz`, with additional cctbx-only Hall settings kept in their IT-number block.
    - A single IT number can occur in several items.
    - The `setting_it_nc` property gives the corresponding International Tables `n:c` setting code when applicable.


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

* **[Maximal subgroup type (subgroup_type)](../properties/spacegroups/subgroup_type.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/subgroup_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/subgroup_type.md)  
  International Tables maximal subgroup class: `t` for translationengleiche or `k` for klassengleiche.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Symmetry operations (symops)](../properties/spacegroups/symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops.md)  
  Full list of symmetry-operation descriptors for a space-group setting.
Each list member is a `symop` object as defined by `/properties/symmetry/symop`.
For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary MUST follow the schema inherited from `/properties/symmetry/symop`.


* **[Symmetry operation generators (symops_generators)](../properties/spacegroups/symops_generators.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators.md)  
  Minimal generator subset of the full symmetry-operation group for a space-group setting.
Each list member is a `symop` object as defined by `/properties/symmetry/symop`.
For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary MUST follow the schema inherited from `/properties/symmetry/symop`.


* **[Symops Generators Xyz (symops_generators_xyz)](../properties/spacegroups/symops_generators_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz.md)  
  Minimal generator subset of the full symmetry-operation group in fractional `x,y,z` notation, ordered consistently with `symops_generators`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Representative symmetry operations (symops_representative)](../properties/spacegroups/symops_representative.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative.md)  
  Representative symmetry-operation descriptors modulo centering translations.
Each list member is a `symop` object as defined by `/properties/symmetry/symop`.
For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a list of dictionaries.
    - Each dictionary MUST follow the schema inherited from `/properties/symmetry/symop`.


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

* **[Target](../properties/spacegroups/target.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/target`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/target.md)  
  Target vector or target value in a generated linear criterion.
In current generated criteria it is usually represented as exact rational components serialized as strings.
The semantic meaning of `target` is parent-specific and should not be reused as a broad standalone concept.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[To Hall (to_hall)](../properties/spacegroups/to_hall.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall.md)  
  Reference Hall-entry key to which a setting transform maps the current Hall setting.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[To Hall Symbol (to_hall_symbol)](../properties/spacegroups/to_hall_symbol.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall_symbol`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall_symbol.md)  
  Display Hall symbol corresponding to `to_hall`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Symmetry operation translation vector (tvec)](../properties/spacegroups/tvec.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/tvec`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/tvec.md)  
  Translation vector of a same-setting affine operation.
This emitted space-group property uses the common `/properties/symmetry/tvec` definition for its nested value shape and dimensional metadata.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Wyckoff positions (wyckoff)](../properties/spacegroups/wyckoff.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff.md)  
  Wyckoff-position table for a specific space-group setting.
Each key is a Wyckoff letter and each value describes one Wyckoff position.
Values follow `/properties/symmetry/wyckoff_position`.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - Dynamic keys MUST be Wyckoff letters for the setting.
    - Each value MUST be a dictionary describing the corresponding Wyckoff position.
    - `orbit_affine` and `orbit_xyz` contain the full orbit.
    - `orbit_mod_centering_affine` and `orbit_mod_centering_xyz` contain one representative modulo centering translations.


* **[Wyckoff Sets (wyckoff_sets)](../properties/spacegroups/wyckoff_sets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets.md)  
  Sets of Wyckoff letters related by normalizer operations. Each inner list groups Wyckoff positions that can be interchanged by the relevant normalizer action.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.

* **[Wyckoff splitting (wyckoff_splitting)](../properties/spacegroups/wyckoff_splitting.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_splitting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_splitting.md)  
  Wyckoff-position splitting data associated with a subgroup or same-space-group transform.
The map is keyed by parent Wyckoff letter.
Each value is an ordered list of subgroup Wyckoff-position assignments or coordinate expressions as emitted by the generator.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - Dynamic keys MUST be parent Wyckoff letters.
    - Values MUST be lists.
    - Each listed item is currently a compact generator record whose exact shape is defined by the parent transform table.


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

* **[Same space group affine images std (same_space_group_affine_images_std)](../properties/spacegroups/same_space_group_affine_images_std.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std.md)  
  IT-number keyed same-space-group affine-image records for the International Tables standard settings.

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** Support for queries on this property is OPTIONAL.
    - **Response:** MAY be included by default in the response.
    - It MUST be a dictionary.
    - Keys MUST be International Tables space-group numbers encoded as strings.
    - Values MUST be dictionaries containing the Hall reference setting and the list of affine images for that IT number.



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
        "affine_images": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Affine images",
            "$comment": "Anyterial property definition for same-space-group affine images.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "affine_images",
                "label": "affine_images_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Same-space-group affine images for a standard setting.\nThe list combines Euclidean normalizer operations and isomorphic subgroup transforms to enumerate alternative affine images of the same space group used by runtime search code.\nMatrix/vector transform fields use `pmat` and `pvec` according to `/properties/symmetry/basis_transform`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/basis_transform",
                "title": "Basis transformation",
                "$comment": "Reusable Anyterial definition for one crystallographic change-of-basis or setting transform.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "basis_transform",
                    "label": "basis_transform_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One crystallographic basis or setting transformation represented by an exact matrix and an exact origin shift.\nParent tables use this object for B\u00e4rnighausen transforms, isomorphic subgroup transforms, Hall-to-standard transforms, and related setting maps.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **pmat**: REQUIRED; Exact 3x3 matrix.\n      Matrix part of the basis or setting transformation.\n\n    - **pvec**: REQUIRED; List of 3 Fractions (String).\n      Translation or origin-shift vector of the basis or setting transformation.\n\n    - **index**: OPTIONAL; Integer.\n      Subgroup index or cell-index metadata when the parent table defines such an index.\n\n    - **target**: OPTIONAL; String or integer.\n      Target setting, Hall entry, IT number, or other target identifier as defined by the parent table.\n\n    - **wyckoff\\_splitting**: OPTIONAL; Dictionary.\n      Wyckoff-position splitting metadata associated with the transform when available.",
                "properties": {
                    "pmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pmat",
                        "title": "Basis transformation matrix",
                        "$comment": "Reusable Anyterial definition for the matrix part of a crystallographic basis or setting transformation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "pmat",
                            "label": "pmat_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Matrix part of a crystallographic basis or setting transformation.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings so that exact rational or algebraic values can be preserved without floating-point rounding.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- The parent transform definition specifies the coordinate convention and whether the matrix maps from a source setting to a target setting or conversely.",
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
                            "description": "One row of the 3 by 3 basis-transformation matrix.",
                            "items": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "One exact matrix entry."
                            }
                        },
                        "examples": [
                            [
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
                            [
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
                                    "2"
                                ]
                            ]
                        ]
                    },
                    "pvec": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
                        "title": "Basis transformation origin shift",
                        "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "pvec",
                            "label": "pvec_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
                                "1/4",
                                "1/4",
                                "0"
                            ]
                        ]
                    },
                    "index": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Optional subgroup or cell index associated with the transform."
                    },
                    "target": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Optional target identifier whose interpretation is supplied by the parent table."
                    },
                    "wyckoff_splitting": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "Optional Wyckoff-position splitting metadata associated with the transform.",
                        "properties": {}
                    }
                },
                "examples": [
                    {
                        "index": 2,
                        "pmat": [
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
                                "2"
                            ]
                        ],
                        "pvec": [
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
                        "pmat": [
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
                        "pvec": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                ]
            ]
        },
        "affine_normalizer": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Affine normalizer",
            "$comment": "Anyterial normalizer collection property using the common normalizer-representative definition.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "affine_normalizer",
                "label": "affine_normalizer_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Bounded affine normalizer coset representatives modulo the space group, generated from bounded unimodular integer linear parts. This is a finite representative table, not a complete infinite affine normalizer.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **items**: REQUIRED; List of dictionaries.\n      Listed normalizer operations or coset representatives.\n      Each item follows `/properties/symmetry/normalizer_representative`.\n\n    - **n\\_cosets**: OPTIONAL; Integer.\n      Number of listed coset representatives when the parent table is a coset table.\n\n    - **n\\_orthogonal\\_cosets**: OPTIONAL; Integer.\n      Number of listed representatives whose linear part is orthogonal.\n\n    - **candidate\\_set**: OPTIONAL; String.\n      Name of the candidate set used for generation.\n\n    - **candidate\\_sets**: OPTIONAL; List of strings.\n      Candidate-set names used for generation.\n\n    - **bounds**: OPTIONAL; Dictionary.\n      Generator bounds for finite bounded candidate searches.",
            "properties": {
                "items": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Listed normalizer operations or coset representatives.",
                    "items": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/normalizer_representative",
                        "title": "Normalizer representative",
                        "$comment": "Reusable Anyterial definition for one listed Euclidean or affine normalizer representative.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "normalizer_representative",
                            "label": "normalizer_representative_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "One listed representative of a Euclidean or affine normalizer operation or coset.\nIn affine-normalizer tables the representative is taken modulo the space group, so it should be read as one representative of an equivalence class rather than as the only operation in that class.\nBounded affine-normalizer tables enumerate only the finite candidate set documented by the generator.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Linear part when the representative is expressed as a same-setting affine operation.\n\n    - **tvec**: OPTIONAL; List of 3 Fractions (String).\n      Translation part when the representative is expressed as a same-setting affine operation.\n\n    - **pmat**: OPTIONAL; Exact 3x3 matrix.\n      Matrix part when the representative is expressed as a basis or setting transform.\n\n    - **pvec**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift when the representative is expressed as a basis or setting transform.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for display and debugging.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which a bounded affine candidate is compatible.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Generator classification of the operation.\n\n    - **normalizer\\_kind**: OPTIONAL; String.\n      Classification of the normalizer contribution.",
                        "properties": {
                            "rmat": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/rmat",
                                "title": "Symmetry operation linear matrix",
                                "$comment": "Reusable Anyterial definition for the linear part of a same-setting affine operation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "rmat",
                                    "label": "rmat_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Linear matrix part of a same-setting affine operation acting on fractional coordinates.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings in transformation tables because affine-normalizer candidates may be generated and serialized through exact arithmetic.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- For point-group operation matrices that are emitted as integers under the legacy key `matrix`, the parent property describes that separate shape.",
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
                                    "description": "One row of the 3 by 3 operation matrix.",
                                    "items": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "description": "One exact matrix entry."
                                    }
                                },
                                "examples": [
                                    [
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
                                    [
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
                                    ]
                                ]
                            },
                            "tvec": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/tvec",
                                "title": "Symmetry operation translation vector",
                                "$comment": "Reusable Anyterial definition for the translation part of a same-setting affine operation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "tvec",
                                    "label": "tvec_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Translation part of a same-setting affine operation acting on fractional coordinates.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- Together with `rmat`, this vector represents an affine operation within one coordinate setting.",
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
                            "pmat": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pmat",
                                "title": "Basis transformation matrix",
                                "$comment": "Reusable Anyterial definition for the matrix part of a crystallographic basis or setting transformation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "pmat",
                                    "label": "pmat_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Matrix part of a crystallographic basis or setting transformation.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings so that exact rational or algebraic values can be preserved without floating-point rounding.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- The parent transform definition specifies the coordinate convention and whether the matrix maps from a source setting to a target setting or conversely.",
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
                                    "description": "One row of the 3 by 3 basis-transformation matrix.",
                                    "items": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "description": "One exact matrix entry."
                                    }
                                },
                                "examples": [
                                    [
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
                                    [
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
                                            "2"
                                        ]
                                    ]
                                ]
                            },
                            "pvec": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
                                "title": "Basis transformation origin shift",
                                "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "pvec",
                                    "label": "pvec_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
                                        "1/4",
                                        "1/4",
                                        "0"
                                    ]
                                ]
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the representative in `x,y,z` notation."
                            },
                            "rmat_det": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Determinant of the same-setting linear part, when supplied."
                            },
                            "rmat_is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether `rmat` is orthogonal, when supplied."
                            },
                            "pmat_is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether `pmat` is orthogonal, when supplied."
                            },
                            "compatible_systems": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Crystal metric systems compatible with the candidate representative.",
                                "items": {
                                    "x-optimade-type": "string",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "string"
                                    ],
                                    "description": "One compatible crystal-system label."
                                }
                            },
                            "operation_kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Generator classification of the operation."
                            },
                            "normalizer_kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Classification of the normalizer contribution."
                            }
                        },
                        "examples": [
                            {
                                "rmat": [
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
                                "tvec": [
                                    "0",
                                    "0",
                                    "0"
                                ],
                                "xyz": "-x,-y,z",
                                "rmat_det": 1,
                                "rmat_is_orthogonal": true,
                                "compatible_systems": [
                                    "monoclinic",
                                    "orthorhombic"
                                ]
                            }
                        ]
                    }
                },
                "n_cosets": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Number of listed coset representatives."
                },
                "n_orthogonal_cosets": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Number of listed representatives whose linear part is orthogonal."
                },
                "candidate_set": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Name of the candidate set used for generation."
                },
                "candidate_sets": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Candidate-set names used for generation.",
                    "items": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "One candidate-set label."
                    }
                },
                "bounds": {
                    "x-optimade-type": "dictionary",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "object",
                        "null"
                    ],
                    "description": "Generator bounds for the finite candidate search.",
                    "properties": {
                        "max_abs_linear_entry": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "Maximum absolute value allowed for entries of candidate linear matrices."
                        },
                        "det_abs": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "Absolute determinant required for candidate matrices."
                        }
                    }
                }
            },
            "examples": [
                {
                    "items": [
                        {
                            "rmat": [
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
                            "tvec": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "-x,-y,z",
                            "rmat_det": 1,
                            "rmat_is_orthogonal": true
                        }
                    ],
                    "n_cosets": 1
                }
            ]
        },
        "affine_normalizer_coset_data": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_coset_data",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Affine normalizer coset data",
            "$comment": "Ordered Anyterial table of affine normalizer coset data by Hall setting.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "affine_normalizer_coset_data",
                "label": "affine_normalizer_coset_data_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Ordered table of affine normalizer coset representative data by Hall setting.\nEach row contains the finite listed coset representatives used by the symmetry-finder runtime for one Hall setting, plus counts and candidate-set metadata.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST contain a `hall_entry` value that can be used with `hall_symbol_to_affine_normalizer_coset_data` to locate the same row.\n- The `affine_normalizer_cosets` field contains bounded unimodular-integer affine normalizer coset representatives modulo the space group.\n- The `orthogonal_affine_normalizer_cosets` field contains the signed-permutation subset retained for the orthogonal retry mode.\n- These are bounded finite representative tables, not complete infinite affine normalizers.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One Hall-setting affine normalizer coset data row.",
                "properties": {}
            },
            "examples": [
                [
                    {
                        "hall_entry": "p_1",
                        "it_number": 1,
                        "crystal_system": "triclinic",
                        "affine_normalizer_cosets": [],
                        "orthogonal_affine_normalizer_cosets": [],
                        "n_cosets": 0,
                        "n_orthogonal_cosets": 0
                    }
                ]
            ]
        },
        "affine_normalizer_cosets": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_cosets",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Affine normalizer cosets",
            "$comment": "Anyterial normalizer-coset list property using the common normalizer-representative definition.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "affine_normalizer_cosets",
                "label": "affine_normalizer_cosets_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Runtime list of bounded affine normalizer coset representatives modulo the space group.\nEach item is one finite listed representative and follows `/properties/symmetry/normalizer_representative`.\nThe list is a bounded representative table, not a complete infinite affine normalizer.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/normalizer_representative",
                "title": "Normalizer representative",
                "$comment": "Reusable Anyterial definition for one listed Euclidean or affine normalizer representative.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "normalizer_representative",
                    "label": "normalizer_representative_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One listed representative of a Euclidean or affine normalizer operation or coset.\nIn affine-normalizer tables the representative is taken modulo the space group, so it should be read as one representative of an equivalence class rather than as the only operation in that class.\nBounded affine-normalizer tables enumerate only the finite candidate set documented by the generator.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Linear part when the representative is expressed as a same-setting affine operation.\n\n    - **tvec**: OPTIONAL; List of 3 Fractions (String).\n      Translation part when the representative is expressed as a same-setting affine operation.\n\n    - **pmat**: OPTIONAL; Exact 3x3 matrix.\n      Matrix part when the representative is expressed as a basis or setting transform.\n\n    - **pvec**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift when the representative is expressed as a basis or setting transform.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for display and debugging.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which a bounded affine candidate is compatible.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Generator classification of the operation.\n\n    - **normalizer\\_kind**: OPTIONAL; String.\n      Classification of the normalizer contribution.",
                "properties": {
                    "rmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/rmat",
                        "title": "Symmetry operation linear matrix",
                        "$comment": "Reusable Anyterial definition for the linear part of a same-setting affine operation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "rmat",
                            "label": "rmat_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Linear matrix part of a same-setting affine operation acting on fractional coordinates.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings in transformation tables because affine-normalizer candidates may be generated and serialized through exact arithmetic.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- For point-group operation matrices that are emitted as integers under the legacy key `matrix`, the parent property describes that separate shape.",
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
                            "description": "One row of the 3 by 3 operation matrix.",
                            "items": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "One exact matrix entry."
                            }
                        },
                        "examples": [
                            [
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
                            [
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
                            ]
                        ]
                    },
                    "tvec": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/tvec",
                        "title": "Symmetry operation translation vector",
                        "$comment": "Reusable Anyterial definition for the translation part of a same-setting affine operation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "tvec",
                            "label": "tvec_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Translation part of a same-setting affine operation acting on fractional coordinates.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- Together with `rmat`, this vector represents an affine operation within one coordinate setting.",
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
                    "pmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pmat",
                        "title": "Basis transformation matrix",
                        "$comment": "Reusable Anyterial definition for the matrix part of a crystallographic basis or setting transformation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "pmat",
                            "label": "pmat_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Matrix part of a crystallographic basis or setting transformation.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings so that exact rational or algebraic values can be preserved without floating-point rounding.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- The parent transform definition specifies the coordinate convention and whether the matrix maps from a source setting to a target setting or conversely.",
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
                            "description": "One row of the 3 by 3 basis-transformation matrix.",
                            "items": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "One exact matrix entry."
                            }
                        },
                        "examples": [
                            [
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
                            [
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
                                    "2"
                                ]
                            ]
                        ]
                    },
                    "pvec": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
                        "title": "Basis transformation origin shift",
                        "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "pvec",
                            "label": "pvec_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
                                "1/4",
                                "1/4",
                                "0"
                            ]
                        ]
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Coordinate expression for the representative in `x,y,z` notation."
                    },
                    "rmat_det": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Determinant of the same-setting linear part, when supplied."
                    },
                    "rmat_is_orthogonal": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether `rmat` is orthogonal, when supplied."
                    },
                    "pmat_is_orthogonal": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether `pmat` is orthogonal, when supplied."
                    },
                    "compatible_systems": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Crystal metric systems compatible with the candidate representative.",
                        "items": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string"
                            ],
                            "description": "One compatible crystal-system label."
                        }
                    },
                    "operation_kind": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Generator classification of the operation."
                    },
                    "normalizer_kind": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Classification of the normalizer contribution."
                    }
                },
                "examples": [
                    {
                        "rmat": [
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
                        "tvec": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,-y,z",
                        "rmat_det": 1,
                        "rmat_is_orthogonal": true,
                        "compatible_systems": [
                            "monoclinic",
                            "orthorhombic"
                        ]
                    }
                ]
            },
            "examples": [
                [
                    {
                        "rmat": [
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
                        "tvec": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,-y,z",
                        "rmat_det": 1,
                        "rmat_is_orthogonal": true
                    }
                ]
            ]
        },
        "asu": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Asu",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "asu",
                "label": "asu_spacegroups"
            },
            "type": [
                "object",
                "null"
            ],
            "description": "Structured asymmetric-unit description for the space-group setting.\n\nThe asymmetric unit is represented as a list of half-space cuts and logical cut expressions in fractional coordinates. Together these cuts define a representative region of the unit cell from which the full space group can generate all equivalent positions.\n\n**Requirements/Conventions**:\n\n- `cuts` contains the complete serialized cut tree.\n- `shape_only_cuts` contains only the geometric shape restrictions, omitting some conditional refinements.\n- The formatted `asu_*` fields provide compact textual renderings of the same information.",
            "x-optimade-unit": "inapplicable",
            "properties": {
                "cuts": {
                    "x-optimade-type": "list",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Complete serialized asymmetric-unit cut tree.",
                    "items": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_cut",
                        "title": "Asymmetric-unit cut",
                        "$comment": "Reusable Anyterial source definition for one serialized asymmetric-unit cut expression.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "asu_cut",
                            "label": "asu_cut_spacegroups"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "One serialized asymmetric-unit half-space cut or logical cut expression.\nCut objects may recursively refer to other cut objects through `condition`, `lhs`, and `rhs`.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **kind**: REQUIRED; String.\n      Kind of cut expression, for example a half-space cut or a logical expression.\n\n    - **ascii**: OPTIONAL; String.\n      Compact plain-text rendering of the cut expression.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the cut in fractional `x,y,z` notation.\n\n    - **inclusive**: OPTIONAL; Boolean.\n      Whether the cut boundary is included.\n\n    - **normal**: OPTIONAL; List of 3 Fractions (String).\n      Normal vector of a half-space cut.\n\n    - **const**: OPTIONAL; Fraction (String).\n      Right-hand-side constant of a half-space cut.\n\n    - **condition**, **lhs**, **rhs**: OPTIONAL; Dictionary.\n      Recursive cut-expression objects.",
                        "properties": {
                            "kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Kind of cut expression."
                            },
                            "ascii": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Plain-text rendering of the cut expression."
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the cut in `x,y,z` notation."
                            },
                            "inclusive": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the cut boundary is included."
                            },
                            "base_symbol": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Base symbolic inequality or coordinate label used for the cut."
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
                                "description": "Normal vector of a half-space cut.",
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
                            },
                            "op": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Logical operator used when the expression combines two subexpressions."
                            },
                            "lhs": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object",
                                    "null"
                                ],
                                "description": "Left-hand operand for a logical cut expression.",
                                "properties": {}
                            },
                            "rhs": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object",
                                    "null"
                                ],
                                "description": "Right-hand operand for a logical cut expression.",
                                "properties": {}
                            },
                            "condition": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object",
                                    "null"
                                ],
                                "description": "Optional conditional cut expression that refines when this cut applies.",
                                "properties": {}
                            }
                        },
                        "examples": [
                            {
                                "kind": "cut",
                                "ascii": "x0",
                                "xyz": "x>=0",
                                "inclusive": true,
                                "base_symbol": "x0",
                                "normal": [
                                    "1",
                                    "0",
                                    "0"
                                ],
                                "const": "0"
                            }
                        ]
                    },
                    "x-optimade-unit": "inapplicable"
                },
                "shape_only_cuts": {
                    "x-optimade-type": "list",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Geometric cut tree with conditional refinements omitted.",
                    "items": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_cut",
                        "title": "Asymmetric-unit cut",
                        "$comment": "Reusable Anyterial source definition for one serialized asymmetric-unit cut expression.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "asu_cut",
                            "label": "asu_cut_spacegroups"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "One serialized asymmetric-unit half-space cut or logical cut expression.\nCut objects may recursively refer to other cut objects through `condition`, `lhs`, and `rhs`.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **kind**: REQUIRED; String.\n      Kind of cut expression, for example a half-space cut or a logical expression.\n\n    - **ascii**: OPTIONAL; String.\n      Compact plain-text rendering of the cut expression.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the cut in fractional `x,y,z` notation.\n\n    - **inclusive**: OPTIONAL; Boolean.\n      Whether the cut boundary is included.\n\n    - **normal**: OPTIONAL; List of 3 Fractions (String).\n      Normal vector of a half-space cut.\n\n    - **const**: OPTIONAL; Fraction (String).\n      Right-hand-side constant of a half-space cut.\n\n    - **condition**, **lhs**, **rhs**: OPTIONAL; Dictionary.\n      Recursive cut-expression objects.",
                        "properties": {
                            "kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Kind of cut expression."
                            },
                            "ascii": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Plain-text rendering of the cut expression."
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the cut in `x,y,z` notation."
                            },
                            "inclusive": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether the cut boundary is included."
                            },
                            "base_symbol": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Base symbolic inequality or coordinate label used for the cut."
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
                                "description": "Normal vector of a half-space cut.",
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
                            },
                            "op": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Logical operator used when the expression combines two subexpressions."
                            },
                            "lhs": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object",
                                    "null"
                                ],
                                "description": "Left-hand operand for a logical cut expression.",
                                "properties": {}
                            },
                            "rhs": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object",
                                    "null"
                                ],
                                "description": "Right-hand operand for a logical cut expression.",
                                "properties": {}
                            },
                            "condition": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object",
                                    "null"
                                ],
                                "description": "Optional conditional cut expression that refines when this cut applies.",
                                "properties": {}
                            }
                        },
                        "examples": [
                            {
                                "kind": "cut",
                                "ascii": "x0",
                                "xyz": "x>=0",
                                "inclusive": true,
                                "base_symbol": "x0",
                                "normal": [
                                    "1",
                                    "0",
                                    "0"
                                ],
                                "const": "0"
                            }
                        ]
                    },
                    "x-optimade-unit": "inapplicable"
                }
            },
            "examples": [
                {
                    "cuts": [
                        {
                            "kind": "cut",
                            "ascii": "x0",
                            "xyz": "x>=0",
                            "inclusive": true,
                            "base_symbol": "x0",
                            "normal": [
                                "1",
                                "0"
                            ],
                            "const": "0"
                        },
                        {
                            "kind": "cut",
                            "ascii": "+x1",
                            "xyz": "x<1",
                            "inclusive": false,
                            "base_symbol": "x1",
                            "normal": [
                                "-1",
                                "0"
                            ],
                            "const": "1"
                        }
                    ],
                    "shape_only_cuts": [
                        {
                            "kind": "cut",
                            "ascii": "x0",
                            "xyz": "x>=0",
                            "inclusive": true,
                            "base_symbol": "x0",
                            "normal": [
                                "1",
                                "0"
                            ],
                            "const": "0"
                        },
                        {
                            "kind": "cut",
                            "ascii": "x1",
                            "xyz": "x<=1",
                            "inclusive": true,
                            "base_symbol": "x1",
                            "normal": [
                                "-1",
                                "0"
                            ],
                            "const": "1"
                        }
                    ]
                },
                {
                    "cuts": [
                        {
                            "kind": "cut",
                            "ascii": "x0(y0(z2) & y2(z2))",
                            "xyz": "x>=0 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]",
                            "inclusive": true,
                            "base_symbol": "x0",
                            "normal": [
                                "1",
                                "0"
                            ],
                            "const": "0",
                            "condition": {
                                "kind": "expr",
                                "ascii": "y0(z2) & y2(z2)",
                                "xyz": "y>=0 [z<=1/2] & y<=1/2 [z<=1/2]",
                                "op": "&",
                                "lhs": {
                                    "kind": "cut",
                                    "ascii": "y0(z2)",
                                    "xyz": "y>=0 [z<=1/2]",
                                    "inclusive": true,
                                    "base_symbol": "y0",
                                    "normal": [
                                        "0",
                                        "1"
                                    ],
                                    "const": "0",
                                    "condition": {
                                        "kind": "cut",
                                        "ascii": "z2"
                                    }
                                },
                                "rhs": {
                                    "kind": "cut",
                                    "ascii": "y2(z2)",
                                    "xyz": "y<=1/2 [z<=1/2]",
                                    "inclusive": true,
                                    "base_symbol": "y2",
                                    "normal": [
                                        "0",
                                        "-1"
                                    ],
                                    "const": "1/2",
                                    "condition": {
                                        "kind": "cut",
                                        "ascii": "z2"
                                    }
                                }
                            }
                        },
                        {
                            "kind": "cut",
                            "ascii": "x2(y0(z2) & y2(z2))",
                            "xyz": "x<=1/2 [y>=0 [z<=1/2] & y<=1/2 [z<=1/2]]",
                            "inclusive": true,
                            "base_symbol": "x2",
                            "normal": [
                                "-1",
                                "0"
                            ],
                            "const": "1/2",
                            "condition": {
                                "kind": "expr",
                                "ascii": "y0(z2) & y2(z2)",
                                "xyz": "y>=0 [z<=1/2] & y<=1/2 [z<=1/2]",
                                "op": "&",
                                "lhs": {
                                    "kind": "cut",
                                    "ascii": "y0(z2)",
                                    "xyz": "y>=0 [z<=1/2]",
                                    "inclusive": true,
                                    "base_symbol": "y0",
                                    "normal": [
                                        "0",
                                        "1"
                                    ],
                                    "const": "0",
                                    "condition": {
                                        "kind": "cut",
                                        "ascii": "z2"
                                    }
                                },
                                "rhs": {
                                    "kind": "cut",
                                    "ascii": "y2(z2)",
                                    "xyz": "y<=1/2 [z<=1/2]",
                                    "inclusive": true,
                                    "base_symbol": "y2",
                                    "normal": [
                                        "0",
                                        "-1"
                                    ],
                                    "const": "1/2",
                                    "condition": {
                                        "kind": "cut",
                                        "ascii": "z2"
                                    }
                                }
                            }
                        }
                    ],
                    "shape_only_cuts": [
                        {
                            "kind": "cut",
                            "ascii": "x0",
                            "xyz": "x>=0",
                            "inclusive": true,
                            "base_symbol": "x0",
                            "normal": [
                                "1",
                                "0"
                            ],
                            "const": "0"
                        },
                        {
                            "kind": "cut",
                            "ascii": "x2",
                            "xyz": "x<=1/2",
                            "inclusive": true,
                            "base_symbol": "x2",
                            "normal": [
                                "-1",
                                "0"
                            ],
                            "const": "1/2"
                        }
                    ]
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
        "backward_lift_criteria": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/backward_lift_criteria",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Backward lift criteria",
            "$comment": "Anyterial property definition for backward-lift criteria grouped by supergroup and subgroup IT number.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "backward_lift_criteria",
                "label": "backward_lift_criteria_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Criteria table used to lift occupied Wyckoff data from a subgroup back to a supergroup along a chosen B\u00e4rnighausen transform.\nThe outer map is keyed by supergroup IT number and the next map is keyed by subgroup IT number.\nValues are lists of transform records carrying a basis transform and a dictionary of Wyckoff-letter criteria.\n\n**Requirements/Conventions**:\n\n- Dynamic outer keys MUST be supergroup IT numbers represented as strings.\n- Dynamic second-level keys MUST be subgroup IT numbers represented as strings.\n- Transform records SHOULD include `index`, `pmat`, `pvec`, and `criteria`.",
            "properties": {},
            "examples": [
                {
                    "1": {
                        "2": [
                            {
                                "index": 2,
                                "pmat": [
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
                                        "2"
                                    ]
                                ],
                                "pvec": [
                                    "0",
                                    "0",
                                    "0"
                                ],
                                "criteria": {
                                    "a": [
                                        {
                                            "roles": [
                                                [
                                                    "a",
                                                    0
                                                ]
                                            ],
                                            "coeffs": [
                                                [
                                                    [
                                                        "1",
                                                        "0",
                                                        "0"
                                                    ]
                                                ]
                                            ],
                                            "target": [
                                                "0",
                                                "0",
                                                "0"
                                            ]
                                        }
                                    ]
                                }
                            }
                        ]
                    }
                }
            ]
        },
        "baernighausen": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/baernighausen",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "B\u00e4rnighausen subgroup transforms",
            "$comment": "Anyterial transform collection property using the common basis-transform definition for transform items.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "baernighausen",
                "label": "baernighausen_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "B\u00e4rnighausen subgroup transform table. Entries describe generated embeddings of a subgroup setting into a supergroup setting.\nThe outer dictionary is keyed by the parent table convention, for example Hall entries or IT numbers.\nTransform records use `pmat` and `pvec` as defined by `/properties/symmetry/basis_transform`.\n\n**Requirements/Conventions**:\n\n- Dynamic outer keys identify parent settings or space groups according to the containing dataset.\n- Values are either dictionaries containing an `items` list of transform records or direct maps to lists of transform records.\n- Each transform record SHOULD follow `/properties/symmetry/basis_transform` for its matrix and vector fields.",
            "properties": {},
            "examples": [
                {
                    "c_2y": {
                        "items": [
                            {
                                "index": 2,
                                "pmat": [
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
                                        "2"
                                    ]
                                ],
                                "pvec": [
                                    "0",
                                    "0",
                                    "0"
                                ]
                            }
                        ]
                    }
                }
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
        "continuous_euclidean_normalizer": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_euclidean_normalizer",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Continuous Euclidean normalizer",
            "$comment": "Anyterial continuous-normalizer property definition.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "continuous_euclidean_normalizer",
                "label": "continuous_euclidean_normalizer_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Continuous Euclidean normalizer subspace before aggregation into the public transformation tables. It records the dimension and basis vectors of allowed continuous origin shifts.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **dimension**: OPTIONAL; Integer.\n      Dimension of the continuous parameter subspace.\n\n    - **basis\\_vectors**: REQUIRED; List of vectors.\n      Basis vectors spanning the continuous normalizer parameter space.\n      Each basis vector is represented as exact fractional-coordinate components.\n\n    - **coordinate\\_system**: OPTIONAL; String.\n      Coordinate system used for the parameter vectors.\n\n    - **representation**: OPTIONAL; String.\n      Textual description of the parameterized representation.",
            "properties": {
                "dimension": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Dimension of the continuous parameter subspace."
                },
                "basis_vectors": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Basis vectors spanning the continuous normalizer parameter space.",
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
                        "description": "One basis vector in fractional coordinates.",
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
                "coordinate_system": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Coordinate system used for the parameter vectors."
                },
                "representation": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Textual description of the parameterized representation."
                }
            },
            "examples": [
                {
                    "dimension": 3,
                    "coordinate_system": "fractional",
                    "basis_vectors": [
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
                    ]
                }
            ]
        },
        "continuous_normalizer": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_normalizer",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Continuous normalizer",
            "$comment": "Anyterial continuous-normalizer property definition.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "continuous_normalizer",
                "label": "continuous_normalizer_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Parameterized continuous normalizer subspace for a setting. It describes continuous origin-shift freedoms by dimension and fractional-coordinate basis vectors rather than by enumerating infinitely many operations.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **dimension**: OPTIONAL; Integer.\n      Dimension of the continuous parameter subspace.\n\n    - **basis\\_vectors**: REQUIRED; List of vectors.\n      Basis vectors spanning the continuous normalizer parameter space.\n      Each basis vector is represented as exact fractional-coordinate components.\n\n    - **coordinate\\_system**: OPTIONAL; String.\n      Coordinate system used for the parameter vectors.\n\n    - **representation**: OPTIONAL; String.\n      Textual description of the parameterized representation.",
            "properties": {
                "dimension": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Dimension of the continuous parameter subspace."
                },
                "basis_vectors": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Basis vectors spanning the continuous normalizer parameter space.",
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
                        "description": "One basis vector in fractional coordinates.",
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
                "coordinate_system": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Coordinate system used for the parameter vectors."
                },
                "representation": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Textual description of the parameterized representation."
                }
            },
            "examples": [
                {
                    "dimension": 3,
                    "coordinate_system": "fractional",
                    "basis_vectors": [
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
                    ]
                }
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
        "euclidean_normalizer": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/euclidean_normalizer",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Euclidean normalizer",
            "$comment": "Anyterial normalizer collection property using the common normalizer-representative definition.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "euclidean_normalizer",
                "label": "euclidean_normalizer_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Finite Euclidean normalizer operations of a Hall setting, generated from cctbx. These are metric-preserving operations that normalize the space group in the chosen setting.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **items**: REQUIRED; List of dictionaries.\n      Listed normalizer operations or coset representatives.\n      Each item follows `/properties/symmetry/normalizer_representative`.\n\n    - **n\\_cosets**: OPTIONAL; Integer.\n      Number of listed coset representatives when the parent table is a coset table.\n\n    - **n\\_orthogonal\\_cosets**: OPTIONAL; Integer.\n      Number of listed representatives whose linear part is orthogonal.\n\n    - **candidate\\_set**: OPTIONAL; String.\n      Name of the candidate set used for generation.\n\n    - **candidate\\_sets**: OPTIONAL; List of strings.\n      Candidate-set names used for generation.\n\n    - **bounds**: OPTIONAL; Dictionary.\n      Generator bounds for finite bounded candidate searches.",
            "properties": {
                "items": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Listed normalizer operations or coset representatives.",
                    "items": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/normalizer_representative",
                        "title": "Normalizer representative",
                        "$comment": "Reusable Anyterial definition for one listed Euclidean or affine normalizer representative.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "normalizer_representative",
                            "label": "normalizer_representative_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "One listed representative of a Euclidean or affine normalizer operation or coset.\nIn affine-normalizer tables the representative is taken modulo the space group, so it should be read as one representative of an equivalence class rather than as the only operation in that class.\nBounded affine-normalizer tables enumerate only the finite candidate set documented by the generator.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Linear part when the representative is expressed as a same-setting affine operation.\n\n    - **tvec**: OPTIONAL; List of 3 Fractions (String).\n      Translation part when the representative is expressed as a same-setting affine operation.\n\n    - **pmat**: OPTIONAL; Exact 3x3 matrix.\n      Matrix part when the representative is expressed as a basis or setting transform.\n\n    - **pvec**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift when the representative is expressed as a basis or setting transform.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for display and debugging.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which a bounded affine candidate is compatible.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Generator classification of the operation.\n\n    - **normalizer\\_kind**: OPTIONAL; String.\n      Classification of the normalizer contribution.",
                        "properties": {
                            "rmat": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/rmat",
                                "title": "Symmetry operation linear matrix",
                                "$comment": "Reusable Anyterial definition for the linear part of a same-setting affine operation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "rmat",
                                    "label": "rmat_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Linear matrix part of a same-setting affine operation acting on fractional coordinates.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings in transformation tables because affine-normalizer candidates may be generated and serialized through exact arithmetic.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- For point-group operation matrices that are emitted as integers under the legacy key `matrix`, the parent property describes that separate shape.",
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
                                    "description": "One row of the 3 by 3 operation matrix.",
                                    "items": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "description": "One exact matrix entry."
                                    }
                                },
                                "examples": [
                                    [
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
                                    [
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
                                    ]
                                ]
                            },
                            "tvec": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/tvec",
                                "title": "Symmetry operation translation vector",
                                "$comment": "Reusable Anyterial definition for the translation part of a same-setting affine operation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "tvec",
                                    "label": "tvec_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Translation part of a same-setting affine operation acting on fractional coordinates.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- Together with `rmat`, this vector represents an affine operation within one coordinate setting.",
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
                            "pmat": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pmat",
                                "title": "Basis transformation matrix",
                                "$comment": "Reusable Anyterial definition for the matrix part of a crystallographic basis or setting transformation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "pmat",
                                    "label": "pmat_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Matrix part of a crystallographic basis or setting transformation.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings so that exact rational or algebraic values can be preserved without floating-point rounding.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- The parent transform definition specifies the coordinate convention and whether the matrix maps from a source setting to a target setting or conversely.",
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
                                    "description": "One row of the 3 by 3 basis-transformation matrix.",
                                    "items": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "description": "One exact matrix entry."
                                    }
                                },
                                "examples": [
                                    [
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
                                    [
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
                                            "2"
                                        ]
                                    ]
                                ]
                            },
                            "pvec": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
                                "title": "Basis transformation origin shift",
                                "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "pvec",
                                    "label": "pvec_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
                                        "1/4",
                                        "1/4",
                                        "0"
                                    ]
                                ]
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the representative in `x,y,z` notation."
                            },
                            "rmat_det": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Determinant of the same-setting linear part, when supplied."
                            },
                            "rmat_is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether `rmat` is orthogonal, when supplied."
                            },
                            "pmat_is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether `pmat` is orthogonal, when supplied."
                            },
                            "compatible_systems": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Crystal metric systems compatible with the candidate representative.",
                                "items": {
                                    "x-optimade-type": "string",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "string"
                                    ],
                                    "description": "One compatible crystal-system label."
                                }
                            },
                            "operation_kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Generator classification of the operation."
                            },
                            "normalizer_kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Classification of the normalizer contribution."
                            }
                        },
                        "examples": [
                            {
                                "rmat": [
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
                                "tvec": [
                                    "0",
                                    "0",
                                    "0"
                                ],
                                "xyz": "-x,-y,z",
                                "rmat_det": 1,
                                "rmat_is_orthogonal": true,
                                "compatible_systems": [
                                    "monoclinic",
                                    "orthorhombic"
                                ]
                            }
                        ]
                    }
                },
                "n_cosets": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Number of listed coset representatives."
                },
                "n_orthogonal_cosets": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Number of listed representatives whose linear part is orthogonal."
                },
                "candidate_set": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Name of the candidate set used for generation."
                },
                "candidate_sets": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Candidate-set names used for generation.",
                    "items": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "One candidate-set label."
                    }
                },
                "bounds": {
                    "x-optimade-type": "dictionary",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "object",
                        "null"
                    ],
                    "description": "Generator bounds for the finite candidate search.",
                    "properties": {
                        "max_abs_linear_entry": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "Maximum absolute value allowed for entries of candidate linear matrices."
                        },
                        "det_abs": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "Absolute determinant required for candidate matrices."
                        }
                    }
                }
            },
            "examples": [
                {
                    "items": [
                        {
                            "rmat": [
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
                            "tvec": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "-x,-y,z",
                            "rmat_det": 1,
                            "rmat_is_orthogonal": true
                        }
                    ],
                    "n_cosets": 1
                }
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
        "hall_symbol_to_affine_normalizer_coset_data": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_symbol_to_affine_normalizer_coset_data",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hall-symbol to affine normalizer coset data index",
            "$comment": "Anyterial top-level index from Hall entries to rows in the affine normalizer coset data table.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hall_symbol_to_affine_normalizer_coset_data",
                "label": "hall_symbol_to_affine_normalizer_coset_data_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Index from normalized Hall entries to row positions in the top-level `affine_normalizer_coset_data` table.\nIt allows consumers to look up affine normalizer coset data by Hall entry while keeping `affine_normalizer_coset_data` as a compact ordered list.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.\n- Each value MUST be a zero-based integer index into the top-level `affine_normalizer_coset_data` list.\n- For every key-value pair, `affine_normalizer_coset_data[value].hall_entry` MUST equal the key.",
            "properties": {},
            "examples": [
                {
                    "p_1": 0,
                    "-p_1": 1
                }
            ]
        },
        "index_hall_entry_to_spacegroup_symbols": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroup_symbols",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Index Hall entry to space-group symbols",
            "$comment": "Anyterial top-level index from Hall entries to rows in the space-group symbols table.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "index_hall_entry_to_spacegroup_symbols",
                "label": "index_hall_entry_to_spacegroup_symbols_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Index from normalized Hall entries to row positions in the top-level `spacegroup_symbols` table.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.\n- Values MUST be non-negative integer row indices into `data.spacegroup_symbols`.",
            "properties": {},
            "examples": [
                {
                    "p_1": 0
                }
            ]
        },
        "index_hall_entry_to_spacegroups": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_hall_entry_to_spacegroups",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hall-entry to spacegroups index",
            "$comment": "Anyterial top-level index from Hall entries to rows in the spacegroups table.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "index_hall_entry_to_spacegroups",
                "label": "index_hall_entry_to_spacegroups_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Index from normalized Hall entries to row positions in the top-level `spacegroups` table.\nIt allows consumers to look up a space-group setting by Hall entry while keeping `spacegroups` as a compact ordered list.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.\n- Each value MUST be a zero-based integer index into the top-level `spacegroups` list.\n- For every key-value pair, `spacegroups[value].hall_entry` MUST equal the key.",
            "properties": {},
            "examples": [
                {
                    "p_1": 0,
                    "-p_1": 1
                }
            ]
        },
        "index_it_number_to_spglib_default_spacegroups": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_it_number_to_spglib_default_spacegroups",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "IT number to spglib default spacegroups index",
            "$comment": "Indexed lookup into symmetry_basics spacegroups for the default spglib setting of each IT number.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "index_it_number_to_spglib_default_spacegroups",
                "label": "index_it_number_to_spglib_default_spacegroups_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "IT-number keyed lookup from the default spglib Hall setting to the corresponding row index in the top-level `spacegroups` list.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary.\n- Keys MUST be International Tables space-group numbers encoded as strings.\n- Values MUST be list indices into the top-level `spacegroups` array of `symmetry_basics.json.gz`.",
            "properties": {},
            "examples": [
                {
                    "1": 0
                },
                {
                    "2": 1
                }
            ]
        },
        "index_it_number_to_std_spacegroups": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_it_number_to_std_spacegroups",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "IT number to std spacegroups index",
            "$comment": "Indexed lookup into symmetry_basics spacegroups for the IT-standard setting of each IT number.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "index_it_number_to_std_spacegroups",
                "label": "index_it_number_to_std_spacegroups_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "IT-number keyed lookup from the International Tables standard setting to the corresponding row index in the top-level `spacegroups` list.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary.\n- Keys MUST be International Tables space-group numbers encoded as strings.\n- Values MUST be list indices into the top-level `spacegroups` array of `symmetry_basics.json.gz`.",
            "properties": {},
            "examples": [
                {
                    "1": 0
                },
                {
                    "2": 1
                }
            ]
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
        "hall_to_it_std_transform": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_to_it_std_transform",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Hall to IT std transform",
            "$comment": "Hall-keyed exact change-of-basis transforms to the IT standard Hall setting.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "hall_to_it_std_transform",
                "label": "hall_to_it_std_transform_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Hall-keyed exact change-of-basis transforms from each Hall setting to the IT-standard Hall reference setting.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary.\n- Keys MUST be Hall-entry identifiers encoded in computer notation.\n- Values MUST be dictionaries describing one exact basis transform to the IT standard Hall reference setting.",
            "properties": {},
            "examples": [
                {
                    "p_1": {
                        "hall_entry": "p_1",
                        "it_number": 1,
                        "to_hall": "p_1",
                        "to_hall_symbol": "P 1",
                        "index": 1,
                        "pmat": [
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
                        "pvec": [
                            "0",
                            "0",
                            "0"
                        ]
                    }
                }
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
        "index": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Index",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "index",
                "label": "index_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Subgroup or transform index. For subgroup transforms it is the crystallographic subgroup index `[G:H]`, equal to the determinant factor of the basis transformation when applicable.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                2,
                4
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
        "isomorphic_subgroups": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Isomorphic subgroup transforms",
            "$comment": "Anyterial transform collection property using the common basis-transform definition for transform items.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "isomorphic_subgroups",
                "label": "isomorphic_subgroups_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Isomorphic subgroup transforms of bounded index. These transforms map a space group to a subgroup of the same space-group type, usually corresponding to an enlarged unit cell.\nThe outer dictionary is keyed by the parent table convention, for example Hall entries or IT numbers.\nTransform records use `pmat` and `pvec` as defined by `/properties/symmetry/basis_transform`.\n\n**Requirements/Conventions**:\n\n- Dynamic outer keys identify parent settings or space groups according to the containing dataset.\n- Values are either dictionaries containing an `items` list of transform records or direct maps to lists of transform records.\n- Each transform record SHOULD follow `/properties/symmetry/basis_transform` for its matrix and vector fields.",
            "properties": {},
            "examples": [
                {
                    "c_2y": {
                        "items": [
                            {
                                "index": 2,
                                "pmat": [
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
                                        "2"
                                    ]
                                ],
                                "pvec": [
                                    "0",
                                    "0",
                                    "0"
                                ]
                            }
                        ]
                    }
                }
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
        "items": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/items",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Items",
            "$comment": "Generic Anyterial ordered data-list container used by several generated datasets.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "items",
                "label": "items_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Generic ordered data-list container used by several generated JSON-LD datasets.\nThe item schema is defined by the containing dataset or parent property.\nThis property is intentionally generic because `items` is used for symbol rows, transform rows, and normalizer rows in different contexts.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One parent-defined item object.",
                "properties": {}
            },
            "examples": [
                [
                    {
                        "setting_it_nc": "1",
                        "hall": "P 1",
                        "it_number": 1
                    }
                ]
            ]
        },
        "k_subtype": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/k_subtype",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Klassengleiche subgroup subtype",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "k_subtype",
                "label": "k_subtype_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Subtype of a klassengleiche (`k`) subgroup relation. Values distinguish loss of centering translations from enlarged-unit-cell subgroups; the value is null for non-`k` relations.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "enlarged_unit_cell",
                "loss_of_centering_translation"
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
        "n_coset_representatives": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_coset_representatives",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Coset Representatives",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_coset_representatives",
                "label": "n_coset_representatives_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of nontrivial coset representatives retained after deduplication modulo the space group.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                47,
                23
            ]
        },
        "n_cosets": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_cosets",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Cosets",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_cosets",
                "label": "n_cosets_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of affine normalizer coset representatives stored for the setting.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                63,
                31
            ]
        },
        "n_linear_parts": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_linear_parts",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Linear Parts",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_linear_parts",
                "label": "n_linear_parts_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of distinct linear matrix parts represented in a normalizer or transform table.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                2,
                4
            ]
        },
        "n_orthogonal_cosets": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_orthogonal_cosets",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Orthogonal Cosets",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_orthogonal_cosets",
                "label": "n_orthogonal_cosets_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of orthogonal affine normalizer coset representatives stored for the setting.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                47,
                23
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
        "n_raw_candidates": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_raw_candidates",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Raw Candidates",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_raw_candidates",
                "label": "n_raw_candidates_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of candidate affine operations considered before filtering and deduplication.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                48,
                6960
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
        "n_unique_candidates": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_unique_candidates",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "N Unique Candidates",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "n_unique_candidates",
                "label": "n_unique_candidates_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Number of candidate affine operations remaining after exact duplicate removal.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                48,
                16
            ]
        },
        "orthogonal_affine_normalizer": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Orthogonal affine normalizer",
            "$comment": "Anyterial normalizer collection property using the common normalizer-representative definition.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "orthogonal_affine_normalizer",
                "label": "orthogonal_affine_normalizer_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Orthogonal affine normalizer coset representatives modulo the space group from the signed-permutation subset of affine candidates.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **items**: REQUIRED; List of dictionaries.\n      Listed normalizer operations or coset representatives.\n      Each item follows `/properties/symmetry/normalizer_representative`.\n\n    - **n\\_cosets**: OPTIONAL; Integer.\n      Number of listed coset representatives when the parent table is a coset table.\n\n    - **n\\_orthogonal\\_cosets**: OPTIONAL; Integer.\n      Number of listed representatives whose linear part is orthogonal.\n\n    - **candidate\\_set**: OPTIONAL; String.\n      Name of the candidate set used for generation.\n\n    - **candidate\\_sets**: OPTIONAL; List of strings.\n      Candidate-set names used for generation.\n\n    - **bounds**: OPTIONAL; Dictionary.\n      Generator bounds for finite bounded candidate searches.",
            "properties": {
                "items": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Listed normalizer operations or coset representatives.",
                    "items": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/normalizer_representative",
                        "title": "Normalizer representative",
                        "$comment": "Reusable Anyterial definition for one listed Euclidean or affine normalizer representative.",
                        "x-optimade-type": "dictionary",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "normalizer_representative",
                            "label": "normalizer_representative_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object",
                            "null"
                        ],
                        "description": "One listed representative of a Euclidean or affine normalizer operation or coset.\nIn affine-normalizer tables the representative is taken modulo the space group, so it should be read as one representative of an equivalence class rather than as the only operation in that class.\nBounded affine-normalizer tables enumerate only the finite candidate set documented by the generator.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Linear part when the representative is expressed as a same-setting affine operation.\n\n    - **tvec**: OPTIONAL; List of 3 Fractions (String).\n      Translation part when the representative is expressed as a same-setting affine operation.\n\n    - **pmat**: OPTIONAL; Exact 3x3 matrix.\n      Matrix part when the representative is expressed as a basis or setting transform.\n\n    - **pvec**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift when the representative is expressed as a basis or setting transform.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for display and debugging.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which a bounded affine candidate is compatible.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Generator classification of the operation.\n\n    - **normalizer\\_kind**: OPTIONAL; String.\n      Classification of the normalizer contribution.",
                        "properties": {
                            "rmat": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/rmat",
                                "title": "Symmetry operation linear matrix",
                                "$comment": "Reusable Anyterial definition for the linear part of a same-setting affine operation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "rmat",
                                    "label": "rmat_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Linear matrix part of a same-setting affine operation acting on fractional coordinates.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings in transformation tables because affine-normalizer candidates may be generated and serialized through exact arithmetic.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- For point-group operation matrices that are emitted as integers under the legacy key `matrix`, the parent property describes that separate shape.",
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
                                    "description": "One row of the 3 by 3 operation matrix.",
                                    "items": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "description": "One exact matrix entry."
                                    }
                                },
                                "examples": [
                                    [
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
                                    [
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
                                    ]
                                ]
                            },
                            "tvec": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/tvec",
                                "title": "Symmetry operation translation vector",
                                "$comment": "Reusable Anyterial definition for the translation part of a same-setting affine operation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "tvec",
                                    "label": "tvec_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Translation part of a same-setting affine operation acting on fractional coordinates.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- Together with `rmat`, this vector represents an affine operation within one coordinate setting.",
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
                            "pmat": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pmat",
                                "title": "Basis transformation matrix",
                                "$comment": "Reusable Anyterial definition for the matrix part of a crystallographic basis or setting transformation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "pmat",
                                    "label": "pmat_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Matrix part of a crystallographic basis or setting transformation.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings so that exact rational or algebraic values can be preserved without floating-point rounding.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- The parent transform definition specifies the coordinate convention and whether the matrix maps from a source setting to a target setting or conversely.",
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
                                    "description": "One row of the 3 by 3 basis-transformation matrix.",
                                    "items": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "description": "One exact matrix entry."
                                    }
                                },
                                "examples": [
                                    [
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
                                    [
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
                                            "2"
                                        ]
                                    ]
                                ]
                            },
                            "pvec": {
                                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
                                "title": "Basis transformation origin shift",
                                "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
                                "x-optimade-type": "list",
                                "x-optimade-definition": {
                                    "kind": "property",
                                    "version": "0.1.0",
                                    "format": "1.3",
                                    "name": "pvec",
                                    "label": "pvec_symmetry"
                                },
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
                                        "1/4",
                                        "1/4",
                                        "0"
                                    ]
                                ]
                            },
                            "xyz": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Coordinate expression for the representative in `x,y,z` notation."
                            },
                            "rmat_det": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "integer",
                                    "null"
                                ],
                                "description": "Determinant of the same-setting linear part, when supplied."
                            },
                            "rmat_is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether `rmat` is orthogonal, when supplied."
                            },
                            "pmat_is_orthogonal": {
                                "x-optimade-type": "boolean",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "boolean",
                                    "null"
                                ],
                                "description": "Whether `pmat` is orthogonal, when supplied."
                            },
                            "compatible_systems": {
                                "x-optimade-type": "list",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "array",
                                    "null"
                                ],
                                "description": "Crystal metric systems compatible with the candidate representative.",
                                "items": {
                                    "x-optimade-type": "string",
                                    "x-optimade-unit": "inapplicable",
                                    "type": [
                                        "string"
                                    ],
                                    "description": "One compatible crystal-system label."
                                }
                            },
                            "operation_kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Generator classification of the operation."
                            },
                            "normalizer_kind": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Classification of the normalizer contribution."
                            }
                        },
                        "examples": [
                            {
                                "rmat": [
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
                                "tvec": [
                                    "0",
                                    "0",
                                    "0"
                                ],
                                "xyz": "-x,-y,z",
                                "rmat_det": 1,
                                "rmat_is_orthogonal": true,
                                "compatible_systems": [
                                    "monoclinic",
                                    "orthorhombic"
                                ]
                            }
                        ]
                    }
                },
                "n_cosets": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Number of listed coset representatives."
                },
                "n_orthogonal_cosets": {
                    "x-optimade-type": "integer",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "integer",
                        "null"
                    ],
                    "description": "Number of listed representatives whose linear part is orthogonal."
                },
                "candidate_set": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string",
                        "null"
                    ],
                    "description": "Name of the candidate set used for generation."
                },
                "candidate_sets": {
                    "x-optimade-type": "list",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "array",
                        "null"
                    ],
                    "description": "Candidate-set names used for generation.",
                    "items": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "One candidate-set label."
                    }
                },
                "bounds": {
                    "x-optimade-type": "dictionary",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "object",
                        "null"
                    ],
                    "description": "Generator bounds for the finite candidate search.",
                    "properties": {
                        "max_abs_linear_entry": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "Maximum absolute value allowed for entries of candidate linear matrices."
                        },
                        "det_abs": {
                            "x-optimade-type": "integer",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "integer",
                                "null"
                            ],
                            "description": "Absolute determinant required for candidate matrices."
                        }
                    }
                }
            },
            "examples": [
                {
                    "items": [
                        {
                            "rmat": [
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
                            "tvec": [
                                "0",
                                "0",
                                "0"
                            ],
                            "xyz": "-x,-y,z",
                            "rmat_det": 1,
                            "rmat_is_orthogonal": true
                        }
                    ],
                    "n_cosets": 1
                }
            ]
        },
        "orthogonal_affine_normalizer_cosets": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Orthogonal affine normalizer cosets",
            "$comment": "Anyterial normalizer-coset list property using the common normalizer-representative definition.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "orthogonal_affine_normalizer_cosets",
                "label": "orthogonal_affine_normalizer_cosets_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Runtime list of orthogonal signed-permutation affine normalizer coset representatives modulo the space group.\nEach item is one finite listed representative and follows `/properties/symmetry/normalizer_representative`.\nThe list is a bounded representative table, not a complete infinite affine normalizer.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/normalizer_representative",
                "title": "Normalizer representative",
                "$comment": "Reusable Anyterial definition for one listed Euclidean or affine normalizer representative.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "normalizer_representative",
                    "label": "normalizer_representative_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One listed representative of a Euclidean or affine normalizer operation or coset.\nIn affine-normalizer tables the representative is taken modulo the space group, so it should be read as one representative of an equivalence class rather than as the only operation in that class.\nBounded affine-normalizer tables enumerate only the finite candidate set documented by the generator.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Linear part when the representative is expressed as a same-setting affine operation.\n\n    - **tvec**: OPTIONAL; List of 3 Fractions (String).\n      Translation part when the representative is expressed as a same-setting affine operation.\n\n    - **pmat**: OPTIONAL; Exact 3x3 matrix.\n      Matrix part when the representative is expressed as a basis or setting transform.\n\n    - **pvec**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift when the representative is expressed as a basis or setting transform.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for display and debugging.\n\n    - **compatible\\_systems**: OPTIONAL; List of strings.\n      Crystal metric systems for which a bounded affine candidate is compatible.\n\n    - **operation\\_kind**: OPTIONAL; String.\n      Generator classification of the operation.\n\n    - **normalizer\\_kind**: OPTIONAL; String.\n      Classification of the normalizer contribution.",
                "properties": {
                    "rmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/rmat",
                        "title": "Symmetry operation linear matrix",
                        "$comment": "Reusable Anyterial definition for the linear part of a same-setting affine operation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "rmat",
                            "label": "rmat_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Linear matrix part of a same-setting affine operation acting on fractional coordinates.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings in transformation tables because affine-normalizer candidates may be generated and serialized through exact arithmetic.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- For point-group operation matrices that are emitted as integers under the legacy key `matrix`, the parent property describes that separate shape.",
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
                            "description": "One row of the 3 by 3 operation matrix.",
                            "items": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "One exact matrix entry."
                            }
                        },
                        "examples": [
                            [
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
                            [
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
                            ]
                        ]
                    },
                    "tvec": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/tvec",
                        "title": "Symmetry operation translation vector",
                        "$comment": "Reusable Anyterial definition for the translation part of a same-setting affine operation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "tvec",
                            "label": "tvec_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Translation part of a same-setting affine operation acting on fractional coordinates.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- Together with `rmat`, this vector represents an affine operation within one coordinate setting.",
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
                    "pmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pmat",
                        "title": "Basis transformation matrix",
                        "$comment": "Reusable Anyterial definition for the matrix part of a crystallographic basis or setting transformation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "pmat",
                            "label": "pmat_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Matrix part of a crystallographic basis or setting transformation.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings so that exact rational or algebraic values can be preserved without floating-point rounding.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- The parent transform definition specifies the coordinate convention and whether the matrix maps from a source setting to a target setting or conversely.",
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
                            "description": "One row of the 3 by 3 basis-transformation matrix.",
                            "items": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "One exact matrix entry."
                            }
                        },
                        "examples": [
                            [
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
                            [
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
                                    "2"
                                ]
                            ]
                        ]
                    },
                    "pvec": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/pvec",
                        "title": "Basis transformation origin shift",
                        "$comment": "Reusable Anyterial definition for the translation/origin-shift part of a crystallographic basis or setting transformation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "pvec",
                            "label": "pvec_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Translation or origin-shift part of a crystallographic basis or setting transformation.\nThe vector is represented in fractional coordinates using exact fraction strings.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of three exact fractional-coordinate components.\n- Each component MUST be represented as a fraction string.\n- The parent transform definition specifies the source and target setting convention for the transformation.",
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
                                "1/4",
                                "1/4",
                                "0"
                            ]
                        ]
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Coordinate expression for the representative in `x,y,z` notation."
                    },
                    "rmat_det": {
                        "x-optimade-type": "integer",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "integer",
                            "null"
                        ],
                        "description": "Determinant of the same-setting linear part, when supplied."
                    },
                    "rmat_is_orthogonal": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether `rmat` is orthogonal, when supplied."
                    },
                    "pmat_is_orthogonal": {
                        "x-optimade-type": "boolean",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "boolean",
                            "null"
                        ],
                        "description": "Whether `pmat` is orthogonal, when supplied."
                    },
                    "compatible_systems": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Crystal metric systems compatible with the candidate representative.",
                        "items": {
                            "x-optimade-type": "string",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "string"
                            ],
                            "description": "One compatible crystal-system label."
                        }
                    },
                    "operation_kind": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Generator classification of the operation."
                    },
                    "normalizer_kind": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Classification of the normalizer contribution."
                    }
                },
                "examples": [
                    {
                        "rmat": [
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
                        "tvec": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,-y,z",
                        "rmat_det": 1,
                        "rmat_is_orthogonal": true,
                        "compatible_systems": [
                            "monoclinic",
                            "orthorhombic"
                        ]
                    }
                ]
            },
            "examples": [
                [
                    {
                        "rmat": [
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
                        "tvec": [
                            "0",
                            "0",
                            "0"
                        ],
                        "xyz": "-x,-y,z",
                        "rmat_det": 1,
                        "rmat_is_orthogonal": true
                    }
                ]
            ]
        },
        "pmat": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pmat",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Basis transformation matrix",
            "$comment": "Anyterial space-group property definition inheriting the common semantic `pmat` definition.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "pmat",
                "label": "pmat_spacegroups"
            },
            "description": "Matrix part of a crystallographic basis or setting transformation.\nThis emitted space-group property uses the common `/properties/symmetry/pmat` definition for its nested value shape and dimensional metadata.",
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
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
                "description": "One row of the 3 by 3 basis-transformation matrix.",
                "items": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string"
                    ],
                    "description": "One exact matrix entry."
                }
            },
            "examples": [
                [
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
                [
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
                        "2"
                    ]
                ]
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
        "pvec": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/pvec",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Basis transformation origin shift",
            "$comment": "Anyterial space-group property definition inheriting the common semantic `pvec` definition.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "pvec",
                "label": "pvec_spacegroups"
            },
            "description": "Translation or origin-shift vector of a crystallographic basis or setting transformation.\nThis emitted space-group property uses the common `/properties/symmetry/pvec` definition for its nested value shape and dimensional metadata.",
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
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
                    "1/4",
                    "1/4",
                    "0"
                ]
            ]
        },
        "maximal_subgroup_relations": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/maximal_subgroup_relations",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Maximal subgroup relations",
            "$comment": "Anyterial property definition for maximal non-isomorphic subgroup relation metadata.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "maximal_subgroup_relations",
                "label": "maximal_subgroup_relations_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Maximal non-isomorphic subgroup relations for International Tables space-group types.\nThe dictionary is keyed by supergroup IT number and each value is a list of subgroup-relation records.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary whose dynamic keys are International Tables space-group numbers represented as strings.\n- Each value MUST be a list of dictionaries.\n- Each dictionary MUST describe one generated maximal subgroup relation and include the subgroup IT number, subgroup index, subgroup type, and optional klassengleiche subtype.",
            "properties": {},
            "examples": [
                {
                    "5": [
                        {
                            "it_number": 1,
                            "index": 2,
                            "subgroup_type": "t"
                        },
                        {
                            "it_number": 3,
                            "index": 2,
                            "subgroup_type": "k",
                            "k_subtype": "loss_of_centering_translation"
                        }
                    ]
                }
            ]
        },
        "rmat": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operation linear matrix",
            "$comment": "Anyterial space-group property definition inheriting the common semantic `rmat` definition.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "rmat",
                "label": "rmat_spacegroups"
            },
            "description": "Linear matrix part of a same-setting affine operation.\nThis emitted space-group property uses the common `/properties/symmetry/rmat` definition for its nested value shape and dimensional metadata.",
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
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
                "description": "One row of the 3 by 3 operation matrix.",
                "items": {
                    "x-optimade-type": "string",
                    "x-optimade-unit": "inapplicable",
                    "type": [
                        "string"
                    ],
                    "description": "One exact matrix entry."
                }
            },
            "examples": [
                [
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
                [
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
                ]
            ]
        },
        "rmat_det": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_det",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operation rotation determinant",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "integer",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "rmat_det",
                "label": "rmat_det_spacegroups"
            },
            "type": [
                "integer",
                "null"
            ],
            "description": "Determinant of the `rmat` linear matrix part of a same-setting operation.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                -1,
                1
            ]
        },
        "rmat_is_orthogonal": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/rmat_is_orthogonal",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operation rotation is orthogonal",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "boolean",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "rmat_is_orthogonal",
                "label": "rmat_is_orthogonal_spacegroups"
            },
            "type": [
                "boolean",
                "null"
            ],
            "description": "Boolean flag indicating whether `rmat` is orthogonal in the conventional coordinate basis.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                true,
                false
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
                "properties": {}
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
        "spacegroups": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroups",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Space groups",
            "$comment": "Anyterial top-level ordered space-group setting table.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "spacegroups",
                "label": "spacegroups_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Ordered table of crystallographic space-group setting records.\nEach item describes one concrete Hall/International Tables setting of a space group, including symbols, classifications, symmetry operations, asymmetric-unit information, Wyckoff positions, and related auxiliary data.\nThe companion `index_hall_entry_to_spacegroups` property maps normalized Hall entries to indices in this list.\n\n**Requirements/Conventions**:\n\n- Items MUST be ordered in the same setting order as `spacegroup_symbols.json.gz`, with additional cctbx-only Hall settings kept in their IT-number block.\n- A single IT number can occur in several items.\n- The `setting_it_nc` property gives the corresponding International Tables `n:c` setting code when applicable.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "One space-group setting record.",
                "properties": {}
            },
            "examples": [
                [
                    {
                        "setting_it_nc": "5:b1",
                        "it_number": 5,
                        "hall_entry": "c_2y"
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
        "subgroup_type": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/subgroup_type",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Maximal subgroup type",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "subgroup_type",
                "label": "subgroup_type_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "International Tables maximal subgroup class: `t` for translationengleiche or `k` for klassengleiche.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "k",
                "t"
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
            "$comment": "Anyterial property definition using the common reusable symop object definition.",
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
            "description": "Full list of symmetry-operation descriptors for a space-group setting.\nEach list member is a `symop` object as defined by `/properties/symmetry/symop`.\nFor space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST follow the schema inherited from `/properties/symmetry/symop`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/symop",
                "title": "Symmetry operation",
                "$comment": "Reusable Anyterial source definition for one crystallographic symmetry-operation descriptor used inside point-group and space-group operation lists.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "symop",
                    "label": "symop_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "A single crystallographic symmetry-operation descriptor.\nSpace-group operation lists currently store the operation type, axis, sense, and screw/glide decomposition.\nPoint-group operation lists currently store the full integer operation matrix under the legacy key `matrix` together with an integer operation-type code under `type`.\nFuture generated data may also use the semantic `rmat` key for the linear matrix part.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.\n      This is the preferred symbolic operation-type field in space-group operation descriptors.\n\n    - **type**: OPTIONAL; Integer.\n      Legacy numeric operation-type code used by point-group operation descriptors.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n    - **matrix**: OPTIONAL; Integer 3x3 matrix.\n      Legacy full point-group operation matrix.\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Semantic linear matrix part of an affine operation when emitted by a parent table.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the operation in `x,y,z` notation when available.\n\n    - **is\\_proper**: OPTIONAL; Boolean.\n      States whether the linear operation is proper, i.e., whether its determinant is +1.",
                "properties": {
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
                        "description": "Legacy integer 3 by 3 operation matrix used by point-group symops.",
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
                            "description": "One row of the integer operation matrix.",
                            "items": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "dimensionless",
                                "type": [
                                    "integer"
                                ],
                                "description": "One integer matrix entry."
                            }
                        }
                    },
                    "rmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/rmat",
                        "title": "Symmetry operation linear matrix",
                        "$comment": "Reusable Anyterial definition for the linear part of a same-setting affine operation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "rmat",
                            "label": "rmat_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Linear matrix part of a same-setting affine operation acting on fractional coordinates.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings in transformation tables because affine-normalizer candidates may be generated and serialized through exact arithmetic.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- For point-group operation matrices that are emitted as integers under the legacy key `matrix`, the parent property describes that separate shape.",
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
                            "description": "One row of the 3 by 3 operation matrix.",
                            "items": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "One exact matrix entry."
                            }
                        },
                        "examples": [
                            [
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
                            [
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
                            ]
                        ]
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Operation in `x,y,z` coordinate notation."
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
                        "rot_type": "2",
                        "sense": 0,
                        "axis": [
                            0,
                            1,
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
                    },
                    {
                        "matrix": [
                            [
                                1,
                                0,
                                0
                            ],
                            [
                                0,
                                1,
                                0
                            ],
                            [
                                0,
                                0,
                                1
                            ]
                        ],
                        "xyz": "x,y,z",
                        "type": 1,
                        "is_proper": true,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "sense": 0
                    }
                ]
            },
            "examples": [
                [
                    {
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
        "symops_generators": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operation generators",
            "$comment": "Anyterial property definition using the common reusable symop object definition.",
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
            "description": "Minimal generator subset of the full symmetry-operation group for a space-group setting.\nEach list member is a `symop` object as defined by `/properties/symmetry/symop`.\nFor space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST follow the schema inherited from `/properties/symmetry/symop`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/symop",
                "title": "Symmetry operation",
                "$comment": "Reusable Anyterial source definition for one crystallographic symmetry-operation descriptor used inside point-group and space-group operation lists.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "symop",
                    "label": "symop_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "A single crystallographic symmetry-operation descriptor.\nSpace-group operation lists currently store the operation type, axis, sense, and screw/glide decomposition.\nPoint-group operation lists currently store the full integer operation matrix under the legacy key `matrix` together with an integer operation-type code under `type`.\nFuture generated data may also use the semantic `rmat` key for the linear matrix part.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.\n      This is the preferred symbolic operation-type field in space-group operation descriptors.\n\n    - **type**: OPTIONAL; Integer.\n      Legacy numeric operation-type code used by point-group operation descriptors.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n    - **matrix**: OPTIONAL; Integer 3x3 matrix.\n      Legacy full point-group operation matrix.\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Semantic linear matrix part of an affine operation when emitted by a parent table.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the operation in `x,y,z` notation when available.\n\n    - **is\\_proper**: OPTIONAL; Boolean.\n      States whether the linear operation is proper, i.e., whether its determinant is +1.",
                "properties": {
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
                        "description": "Legacy integer 3 by 3 operation matrix used by point-group symops.",
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
                            "description": "One row of the integer operation matrix.",
                            "items": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "dimensionless",
                                "type": [
                                    "integer"
                                ],
                                "description": "One integer matrix entry."
                            }
                        }
                    },
                    "rmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/rmat",
                        "title": "Symmetry operation linear matrix",
                        "$comment": "Reusable Anyterial definition for the linear part of a same-setting affine operation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "rmat",
                            "label": "rmat_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Linear matrix part of a same-setting affine operation acting on fractional coordinates.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings in transformation tables because affine-normalizer candidates may be generated and serialized through exact arithmetic.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- For point-group operation matrices that are emitted as integers under the legacy key `matrix`, the parent property describes that separate shape.",
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
                            "description": "One row of the 3 by 3 operation matrix.",
                            "items": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "One exact matrix entry."
                            }
                        },
                        "examples": [
                            [
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
                            [
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
                            ]
                        ]
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Operation in `x,y,z` coordinate notation."
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
                        "rot_type": "2",
                        "sense": 0,
                        "axis": [
                            0,
                            1,
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
                    },
                    {
                        "matrix": [
                            [
                                1,
                                0,
                                0
                            ],
                            [
                                0,
                                1,
                                0
                            ],
                            [
                                0,
                                0,
                                1
                            ]
                        ],
                        "xyz": "x,y,z",
                        "type": 1,
                        "is_proper": true,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "sense": 0
                    }
                ]
            },
            "examples": [
                [
                    {
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
            "$comment": "Anyterial property definition using the common reusable symop object definition.",
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
            "description": "Representative symmetry-operation descriptors modulo centering translations.\nEach list member is a `symop` object as defined by `/properties/symmetry/symop`.\nFor space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.\n\n**Requirements/Conventions**:\n\n- It MUST be a list of dictionaries.\n- Each dictionary MUST follow the schema inherited from `/properties/symmetry/symop`.",
            "items": {
                "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/symop",
                "title": "Symmetry operation",
                "$comment": "Reusable Anyterial source definition for one crystallographic symmetry-operation descriptor used inside point-group and space-group operation lists.",
                "x-optimade-type": "dictionary",
                "x-optimade-definition": {
                    "kind": "property",
                    "version": "0.1.0",
                    "format": "1.3",
                    "name": "symop",
                    "label": "symop_symmetry"
                },
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object",
                    "null"
                ],
                "description": "A single crystallographic symmetry-operation descriptor.\nSpace-group operation lists currently store the operation type, axis, sense, and screw/glide decomposition.\nPoint-group operation lists currently store the full integer operation matrix under the legacy key `matrix` together with an integer operation-type code under `type`.\nFuture generated data may also use the semantic `rmat` key for the linear matrix part.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **rot\\_type**: OPTIONAL; String.\n      Crystallographic operation-type label for the linear part, such as `1`, `-1`, `2`, `m`, `-3`, `4`, `-4`, `6`, or `-6`.\n      This is the preferred symbolic operation-type field in space-group operation descriptors.\n\n    - **type**: OPTIONAL; Integer.\n      Legacy numeric operation-type code used by point-group operation descriptors.\n\n    - **axis**: OPTIONAL; List of 3 Integers.\n      Operation axis or invariant direction using the integer-vector convention returned by the generator.\n\n    - **sense**: OPTIONAL; Integer.\n      Rotation sense/sign convention returned by the generator; `0` is used when no handed rotation sense is applicable.\n\n    - **screw\\_glide**: OPTIONAL; List of 3 Fractions (String).\n      Screw-axis or glide-plane component associated with a space-group affine operation.\n\n    - **origin\\_shift**: OPTIONAL; List of 3 Fractions (String).\n      Origin shift associated with the screw/glide decomposition of a space-group affine operation.\n\n    - **matrix**: OPTIONAL; Integer 3x3 matrix.\n      Legacy full point-group operation matrix.\n\n    - **rmat**: OPTIONAL; Exact 3x3 matrix.\n      Semantic linear matrix part of an affine operation when emitted by a parent table.\n\n    - **xyz**: OPTIONAL; String.\n      Coordinate expression for the operation in `x,y,z` notation when available.\n\n    - **is\\_proper**: OPTIONAL; Boolean.\n      States whether the linear operation is proper, i.e., whether its determinant is +1.",
                "properties": {
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
                        "description": "Legacy integer 3 by 3 operation matrix used by point-group symops.",
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
                            "description": "One row of the integer operation matrix.",
                            "items": {
                                "x-optimade-type": "integer",
                                "x-optimade-unit": "dimensionless",
                                "type": [
                                    "integer"
                                ],
                                "description": "One integer matrix entry."
                            }
                        }
                    },
                    "rmat": {
                        "$id": "https://schemas.anyterial.se/defs/v0.1/properties/symmetry/rmat",
                        "title": "Symmetry operation linear matrix",
                        "$comment": "Reusable Anyterial definition for the linear part of a same-setting affine operation.",
                        "x-optimade-type": "list",
                        "x-optimade-definition": {
                            "kind": "property",
                            "version": "0.1.0",
                            "format": "1.3",
                            "name": "rmat",
                            "label": "rmat_symmetry"
                        },
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array",
                            "null"
                        ],
                        "description": "Linear matrix part of a same-setting affine operation acting on fractional coordinates.\nThe matrix is represented exactly as three rows with three entries per row.\nEntries are strings in transformation tables because affine-normalizer candidates may be generated and serialized through exact arithmetic.\n\n**Requirements/Conventions**:\n\n- It MUST be a 3 by 3 matrix represented as a list of three row lists.\n- Each row MUST contain three exact matrix entries represented as strings.\n- For point-group operation matrices that are emitted as integers under the legacy key `matrix`, the parent property describes that separate shape.",
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
                            "description": "One row of the 3 by 3 operation matrix.",
                            "items": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "description": "One exact matrix entry."
                            }
                        },
                        "examples": [
                            [
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
                            [
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
                            ]
                        ]
                    },
                    "xyz": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string",
                            "null"
                        ],
                        "description": "Operation in `x,y,z` coordinate notation."
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
                        "rot_type": "2",
                        "sense": 0,
                        "axis": [
                            0,
                            1,
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
                    },
                    {
                        "matrix": [
                            [
                                1,
                                0,
                                0
                            ],
                            [
                                0,
                                1,
                                0
                            ],
                            [
                                0,
                                0,
                                1
                            ]
                        ],
                        "xyz": "x,y,z",
                        "type": 1,
                        "is_proper": true,
                        "axis": [
                            0,
                            0,
                            0
                        ],
                        "sense": 0
                    }
                ]
            },
            "examples": [
                [
                    {
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
        "target": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/target",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Target",
            "$comment": "Anyterial local target vector property used in generated linear criteria.",
            "x-optimade-type": "list",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "target",
                "label": "target_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Target vector or target value in a generated linear criterion.\nIn current generated criteria it is usually represented as exact rational components serialized as strings.\nThe semantic meaning of `target` is parent-specific and should not be reused as a broad standalone concept.",
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
                    "0",
                    "0"
                ]
            ]
        },
        "to_hall": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "To Hall",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "to_hall",
                "label": "to_hall_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Reference Hall-entry key to which a setting transform maps the current Hall setting.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "p_1",
                "-p_1"
            ]
        },
        "to_hall_symbol": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall_symbol",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "To Hall Symbol",
            "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "to_hall_symbol",
                "label": "to_hall_symbol_spacegroups"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "Display Hall symbol corresponding to `to_hall`.",
            "x-optimade-unit": "inapplicable",
            "examples": [
                "p 1",
                "-p 1"
            ]
        },
        "tvec": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/tvec",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Symmetry operation translation vector",
            "$comment": "Anyterial space-group property definition inheriting the common semantic `tvec` definition.",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "tvec",
                "label": "tvec_spacegroups"
            },
            "description": "Translation vector of a same-setting affine operation.\nThis emitted space-group property uses the common `/properties/symmetry/tvec` definition for its nested value shape and dimensional metadata.",
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
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
        "wyckoff": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Wyckoff positions",
            "$comment": "Anyterial Wyckoff-position map property using the common wyckoff-position record definition.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "wyckoff",
                "label": "wyckoff_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Wyckoff-position table for a specific space-group setting.\nEach key is a Wyckoff letter and each value describes one Wyckoff position.\nValues follow `/properties/symmetry/wyckoff_position`.\n\n**Requirements/Conventions**:\n\n- Dynamic keys MUST be Wyckoff letters for the setting.\n- Each value MUST be a dictionary describing the corresponding Wyckoff position.\n- `orbit_affine` and `orbit_xyz` contain the full orbit.\n- `orbit_mod_centering_affine` and `orbit_mod_centering_xyz` contain one representative modulo centering translations.",
            "properties": {},
            "examples": [
                {
                    "e": {
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
                }
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
        "wyckoff_splitting": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_splitting",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Wyckoff splitting",
            "$comment": "Anyterial property definition for Wyckoff-position splitting data attached to subgroup transforms.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "wyckoff_splitting",
                "label": "wyckoff_splitting_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "Wyckoff-position splitting data associated with a subgroup or same-space-group transform.\nThe map is keyed by parent Wyckoff letter.\nEach value is an ordered list of subgroup Wyckoff-position assignments or coordinate expressions as emitted by the generator.\n\n**Requirements/Conventions**:\n\n- Dynamic keys MUST be parent Wyckoff letters.\n- Values MUST be lists.\n- Each listed item is currently a compact generator record whose exact shape is defined by the parent transform table.",
            "properties": {},
            "examples": [
                {
                    "c": [
                        [
                            "e",
                            "x",
                            "y",
                            "z"
                        ],
                        [
                            "e",
                            "-x",
                            "y",
                            "-z"
                        ]
                    ]
                }
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
        },
        "same_space_group_affine_images_std": {
            "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "none",
                "response-level": "may"
            },
            "title": "Same space group affine images std",
            "$comment": "IT-number keyed same-space-group affine-image records for standard settings.",
            "x-optimade-type": "dictionary",
            "x-optimade-definition": {
                "kind": "property",
                "version": "0.1.0",
                "format": "1.3",
                "name": "same_space_group_affine_images_std",
                "label": "same_space_group_affine_images_std_spacegroups"
            },
            "x-optimade-unit": "inapplicable",
            "type": [
                "object",
                "null"
            ],
            "description": "IT-number keyed same-space-group affine-image records for the International Tables standard settings.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary.\n- Keys MUST be International Tables space-group numbers encoded as strings.\n- Values MUST be dictionaries containing the Hall reference setting and the list of affine images for that IT number.",
            "properties": {},
            "examples": [
                {
                    "1": {
                        "it_number": 1,
                        "hall": "p_1",
                        "affine_images": [
                            {
                                "pmat": [
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
                                "pvec": [
                                    "0",
                                    "0",
                                    "0"
                                ]
                            }
                        ]
                    }
                }
            ]
        }
    }
}
```