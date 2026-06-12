# Index

* **v0.1**
    * **datasets**
        * **[Point groups](v0.1/datasets/pointgroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/datasets/pointgroups`](https://schemas.anyterial.se/defs/v0.1/datasets/pointgroups.md)
            
            Ordered table of crystallographic point-group records.
            Each item contains point-group classification, finite point-group operations, conjugacy classes, and real and complex character tables generated from cctbx and spgrep.

        * **[Space groups](v0.1/datasets/spacegroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/datasets/spacegroups`](https://schemas.anyterial.se/defs/v0.1/datasets/spacegroups.md)
            
            Ordered table of crystallographic space-group setting records.
            Each item describes one concrete Hall/International Tables setting of a space group, including symbols, classifications, symmetry operations, asymmetric-unit information, Wyckoff positions, and related auxiliary data.
            The companion top-level `indicies.index_hall_entry_to_spacegroups` lookup maps normalized Hall entries to indices in this list; it is not an OPTIMADE property.

        * **[Transformations](v0.1/datasets/transformations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/datasets/transformations`](https://schemas.anyterial.se/defs/v0.1/datasets/transformations.md)
            
            Ordered table of crystallographic transformation records.
            Each item describes transformations and normalizer information for one concrete International Tables H-M entry.
            In `transformations_hm_entry.json.gz`, items are keyed for lookup by the companion top-level `indicies.index_hm_entry_to_transformations_per_hm_entry` object; that index is not an OPTIMADE property.

    * **entrytypes**
        * **[Anyterial point group symmetry fields](v0.1/entrytypes/pointgroups.md)** (entrytype) - [`https://schemas.anyterial.se/defs/v0.1/entrytypes/pointgroups`](https://schemas.anyterial.se/defs/v0.1/entrytypes/pointgroups.md)
            

        * **[Anyterial space group symmetry fields](v0.1/entrytypes/spacegroups.md)** (entrytype) - [`https://schemas.anyterial.se/defs/v0.1/entrytypes/spacegroups`](https://schemas.anyterial.se/defs/v0.1/entrytypes/spacegroups.md)
            

        * **[Anyterial transformation fields](v0.1/entrytypes/transformations.md)** (entrytype) - [`https://schemas.anyterial.se/defs/v0.1/entrytypes/transformations`](https://schemas.anyterial.se/defs/v0.1/entrytypes/transformations.md)
            

    * **properties**
        * **core**
            * **[Fraction](v0.1/properties/core/fraction.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/core/fraction`](https://schemas.anyterial.se/defs/v0.1/properties/core/fraction.md)
                
                A numerical representation formed as the quotient of two numbers represented as a string.

            * **[String markups](v0.1/properties/core/string_markups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups`](https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups.md)
                
                Strings with alternate markup and/or encoding for display rendering.

        * **pointgroups**
            * **[Complex character table](v0.1/properties/pointgroups/character_table_complex.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_complex`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_complex.md)
                
                Complex irreducible character table of the crystallographic point group.

            * **[Real character table](v0.1/properties/pointgroups/character_table_real.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_real`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_real.md)
                
                Real irreducible character table of the crystallographic point group.

            * **[Conjugacy classes](v0.1/properties/pointgroups/conjugacy_classes.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/conjugacy_classes`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/conjugacy_classes.md)
                
                Conjugacy classes of a crystallographic point group.

            * **[Crystal system](v0.1/properties/pointgroups/crystal_system.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system.md)
                
                The crystal system of the space group or point group.

            * **[Hermann-Mauguin symbol](v0.1/properties/pointgroups/hm_symbol.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol.md)
                
                Hermann-Mauguin point-group symbol used as the key and display symbol for a point-group record.

            * **[is centrosymmetric](v0.1/properties/pointgroups/is_centrosymmetric.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/is_centrosymmetric`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/is_centrosymmetric.md)
                
                Boolean flag indicating whether the point group contains inversion symmetry.

            * **[Laue class](v0.1/properties/pointgroups/laue_class.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class.md)
                
                The Laue class associated with the space group or point group.

            * **[Number of conjugacy classes](v0.1/properties/pointgroups/n_conjugacy_classes.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes.md)
                
                Number of conjugacy classes in the crystallographic point group.

            * **[Number of pointgroup symops](v0.1/properties/pointgroups/n_pointgroup_symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops.md)
                
                Number of point-group symmetry operations.

            * **[Order of the point group](v0.1/properties/pointgroups/order.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order.md)
                
                Order of the point group, i.e. the number of operations in the finite point group.

            * **[Schoenflies symbol](v0.1/properties/pointgroups/schoenflies.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies.md)
                
                The Schoenflies symbol for the crystallographic point group.

            * **[Schoenflies symbol markups](v0.1/properties/pointgroups/schoenflies_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup.md)
                
                Display-oriented renderings of the Schoenflies symbol in `schoenflies`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Symmetry operations](v0.1/properties/pointgroups/symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/symops`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/symops.md)
                
                Full list of symmetry-operation descriptors for a point group.
                Each list member is an `op` object as defined by `/defs/v0.1/properties/symmetry/op`.
                Point-group operations have a zero translation part, so the `screw_glide` and `origin_shift` classification fields are omitted.

        * **spacegroups**
            * **[Asymmetric unit](v0.1/properties/spacegroups/asu.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu.md)
                
                Direct-space asymmetric unit for the space-group setting, represented as a bounded non-recursive set of half-space cuts and boundary ownership rules.

            * **[Asymmetric-unit cut](v0.1/properties/spacegroups/asu_cut.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_cut`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_cut.md)
                
                One serialized asymmetric-unit half-space cut or logical cut expression in the recursive cctbx source representation.

            * **[Asymmetric unit markups](v0.1/properties/spacegroups/asu_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_markup.md)
                
                Display-oriented renderings of the plain-string asymmetric-unit restrictions in `asu_str`.

            * **[Shape-only asymmetric unit markups](v0.1/properties/spacegroups/asu_shape_only_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_markup.md)
                
                Display-oriented renderings of the plain-string shape-only asymmetric-unit restrictions in `asu_shape_only_str`.

            * **[Shape-only asymmetric unit string](v0.1/properties/spacegroups/asu_shape_only_str.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_str`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_str.md)
                
                Plain string rendering of the geometric shape part of the asymmetric-unit restrictions, without conditional refinements.

            * **[Asymmetric unit string](v0.1/properties/spacegroups/asu_str.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str.md)
                
                Plain string rendering of the asymmetric-unit restrictions for the space-group setting.

            * **[Bravais type](v0.1/properties/spacegroups/bravais_type.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type.md)
                
                The Bravais type of the translational lattice.

            * **[Cctbx FFT grid factors](v0.1/properties/spacegroups/cctbx_fft_grid_factors.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors.md)
                
                FFT grid-factor requirements derived from cctbx for the space group, its structure seminvariants, and its Euclidean normalizer.

            * **[Centering translations](v0.1/properties/spacegroups/centering_translations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations.md)
                
                Centering translations of the conventional cell.

            * **[Centring type](v0.1/properties/spacegroups/centring_type.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type.md)
                
                The lattice centring symbol for the crystallographic setting.

            * **[Crystal system](v0.1/properties/spacegroups/crystal_system.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system.md)
                
                The crystal system of the space group or point group.

            * **[Hall symbol](v0.1/properties/spacegroups/hall.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall.md)
                
                The Hall symbol for a crystallographic space-group setting.

            * **[Hall symbol aliases](v0.1/properties/spacegroups/hall_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases.md)
                
                Alternate ASCII Hall symbols or Hall-setting keys associated with the same generated setting.

            * **[Hall alias markups](v0.1/properties/spacegroups/hall_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases_markup.md)
                
                Display-oriented renderings corresponding element-by-element to the alternate Hall symbols in `hall_aliases`.

            * **[Hall entry](v0.1/properties/spacegroups/hall_entry.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry.md)
                
                Normalized Hall-table entry key used internally by the generated datasets.

            * **[Hall symbol markups](v0.1/properties/spacegroups/hall_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_markup.md)
                
                Display-oriented renderings of the Hall symbol in `hall`.

            * **[Harker planes](v0.1/properties/spacegroups/harker_planes.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/harker_planes`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/harker_planes.md)
                
                Harker planes of the space group in fractional Patterson coordinates.

            * **[Universal cctbx Hermann-Mauguin symbol](v0.1/properties/spacegroups/hm_cctbx_universal.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_cctbx_universal`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_cctbx_universal.md)
                
                Universal Hermann-Mauguin symbol returned by cctbx for this setting.

            * **[Hermann-Mauguin entry](v0.1/properties/spacegroups/hm_entry.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry.md)
                
                The Hermann-Mauguin entry label for a conventional space-group setting from table A1.4.2.7 of the [International Tables for Crystallography (2006). Volume B, Reciprocal space. ISBN: 978-0-7923-6592-1, doi:10.1107/97809553602060000102](https://doi.org/10.1107/97809553602060000102).

            * **[Hermann-Mauguin entry aliases](v0.1/properties/spacegroups/hm_entry_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry_aliases.md)
                
                Alternative Hermann-Mauguin entry labels from International Tables for Crystallography Volume B table A1.4.2.7 that identify the same generated Hall-symbol row as `hm_entry`.

            * **[Hermann-Mauguin entry markups](v0.1/properties/spacegroups/hm_entry_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_entry_markup.md)
                
                Display-oriented renderings of the Hermann-Mauguin entry label in `hm_entry`.

            * **[Extended Hermann-Mauguin symbol](v0.1/properties/spacegroups/hm_extended.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended.md)
                
                The setting-specific extended Hermann-Mauguin symbol for the space-group setting.

            * **[Extended Hermann-Mauguin symbol aliases](v0.1/properties/spacegroups/hm_extended_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases.md)
                
                Alternate ASCII forms of `hm_extended` that are accepted for the same generated setting.

            * **[Extended Hermann-Mauguin alias markups](v0.1/properties/spacegroups/hm_extended_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases_markup.md)
                
                Display-oriented renderings corresponding element-by-element to the alternate extended Hermann-Mauguin symbols in `hm_extended_aliases`.

            * **[Extended Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_extended_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_markup.md)
                
                Display-oriented renderings of the extended Hermann-Mauguin symbol in `hm_extended`.

            * **[Extended Hermann-Mauguin symbol in old notation](v0.1/properties/spacegroups/hm_extended_old.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_old.md)
                
                The older extended Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.

            * **[Full Hermann-Mauguin symbol](v0.1/properties/spacegroups/hm_full.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full.md)
                
                The setting-specific full Hermann-Mauguin symbol for the space-group setting.

            * **[Full Hermann-Mauguin symbol aliases](v0.1/properties/spacegroups/hm_full_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases.md)
                
                Alternate ASCII forms of `hm_full` that are accepted for the same generated setting.

            * **[Full Hermann-Mauguin alias markups](v0.1/properties/spacegroups/hm_full_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases_markup.md)
                
                Display-oriented renderings corresponding element-by-element to the alternate full Hermann-Mauguin symbols in `hm_full_aliases`.

            * **[Full Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_full_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_markup.md)
                
                Display-oriented renderings of the setting-specific full Hermann-Mauguin symbol in `hm_full`.

            * **[Full Hermann-Mauguin symbol in old notation](v0.1/properties/spacegroups/hm_full_old.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_old.md)
                
                The older full Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.

            * **[Standard full Hermann-Mauguin symbol](v0.1/properties/spacegroups/hm_full_std.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std.md)
                
                The International Tables standard full Hermann-Mauguin symbol for the space-group type.

            * **[Standard full Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_full_std_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std_markup.md)
                
                Display-oriented renderings of the ITA-standard full Hermann-Mauguin symbol in `hm_full_std`.

            * **[Short Hermann-Mauguin symbol](v0.1/properties/spacegroups/hm_short.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short.md)
                
                The setting-specific short Hermann-Mauguin symbol for the space-group setting.

            * **[Short Hermann-Mauguin symbol aliases](v0.1/properties/spacegroups/hm_short_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases.md)
                
                Alternate ASCII forms of `hm_short` that are accepted for the same generated setting.

            * **[Short Hermann-Mauguin alias markups](v0.1/properties/spacegroups/hm_short_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases_markup.md)
                
                Display-oriented renderings corresponding element-by-element to the alternate short Hermann-Mauguin symbols in `hm_short_aliases`.

            * **[Short Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_short_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_markup.md)
                
                Display-oriented renderings of the setting-specific short Hermann-Mauguin symbol in `hm_short`.

            * **[Short Hermann-Mauguin symbol in old notation](v0.1/properties/spacegroups/hm_short_old.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old.md)
                
                The older short Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.

            * **[Standard short Hermann-Mauguin symbol](v0.1/properties/spacegroups/hm_short_std.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std.md)
                
                The International Tables standard short Hermann-Mauguin symbol for the space-group type.

            * **[Standard short Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_short_std_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std_markup.md)
                
                Display-oriented renderings of the ITA-standard short Hermann-Mauguin symbol in `hm_short_std`.

            * **[is centric](v0.1/properties/spacegroups/is_centric.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric.md)
                
                Boolean flag indicating whether the space group is centric.

            * **[is chiral](v0.1/properties/spacegroups/is_chiral.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral.md)
                
                Boolean flag indicating whether the space group is chiral.

            * **[is enantiomorphic](v0.1/properties/spacegroups/is_enantiomorphic.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic.md)
                
                Boolean flag indicating whether the space-group type belongs to an enantiomorphic pair.

            * **[is reference setting](v0.1/properties/spacegroups/is_reference_setting.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting.md)
                
                Boolean flag indicating whether this Hall setting is the selected reference setting for its International Tables space-group number.

            * **[International Tables coordinate-system code](v0.1/properties/spacegroups/it_coordinate_system_code.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code.md)
                
                The International Tables coordinate-system code for the setting.

            * **[International Tables space-group number](v0.1/properties/spacegroups/it_number.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number.md)
                
                The International Tables space-group number.

            * **[International Tables number of the enantiomorph](v0.1/properties/spacegroups/it_number_enantiomorphic.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic.md)
                
                International Tables number of the enantiomorphic partner space group, when one exists.

            * **[Laue class](v0.1/properties/spacegroups/laue_class.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class.md)
                
                The Laue class associated with the space group or point group.

            * **[Number of centering translations](v0.1/properties/spacegroups/n_centering_translations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_centering_translations`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_centering_translations.md)
                
                Number of centering translations in the conventional cell of the space-group setting.

            * **[Number of pointgroup symops](v0.1/properties/spacegroups/n_pointgroup_symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_pointgroup_symops.md)
                
                Number of point-group symmetry operations.

            * **[Number of symops](v0.1/properties/spacegroups/n_symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops.md)
                
                Number of symmetry operations in the finite operation list of the generated entry.

            * **[Point-group Hermann-Mauguin symbol](v0.1/properties/spacegroups/point_group.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group.md)
                
                The Hermann-Mauguin point-group symbol for the crystallographic point group of the space group.

            * **[Schoenflies symbol](v0.1/properties/spacegroups/schoenflies.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies.md)
                
                The Schoenflies symbol for the space-group type.

            * **[Schoenflies symbol markups](v0.1/properties/spacegroups/schoenflies_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies_markup.md)
                
                Display-oriented renderings of the space-group Schoenflies symbol in `schoenflies`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Setting annotation](v0.1/properties/spacegroups/setting.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting.md)
                
                Setting suffix or setting annotation extracted from the cctbx universal Hermann-Mauguin symbol in `hm_cctbx_universal`.

            * **[International Tables setting code n:c](v0.1/properties/spacegroups/setting_it_nc.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc.md)
                
                International Tables setting identifier in `n:c` notation.

            * **[International Tables setting-code aliases](v0.1/properties/spacegroups/setting_it_nc_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases.md)
                
                A list of International Tables `n:c` setting identifiers that are alternatives to the one designated as the main one.

            * **[Setting plaintext](v0.1/properties/spacegroups/setting_plaintext.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext.md)
                
                Human-readable description of the International Tables coordinate-system setting.

            * **[Space-group symbols](v0.1/properties/spacegroups/spacegroup_symbols.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols.md)
                
                Ordered table of conventional space-group symbol rows.

            * **[Spglib Hall symbol](v0.1/properties/spacegroups/spglib_hall.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall.md)
                
                The Hall symbol for this setting as spelled by the spglib library.

            * **[Spglib Hall numbers](v0.1/properties/spacegroups/spglib_hall_numbers.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers.md)
                
                The spglib Hall numbers corresponding to this Hall setting.

            * **[Structure seminvariants](v0.1/properties/spacegroups/structure_seminvariants.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants.md)
                
                Structure seminvariant vectors and moduli for the space-group setting.

            * **[Symmetry operations](v0.1/properties/spacegroups/symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops.md)
                
                Full list of symmetry-operation descriptors for a space-group setting.

            * **[Symmetry operation generators](v0.1/properties/spacegroups/symops_generators.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators.md)
                
                Minimal generator subset of the full symmetry-operation group for a space-group setting.

            * **[Symmetry operations modulo centering translations](v0.1/properties/spacegroups/symops_mod_centering.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_mod_centering.md)
                
                Representative symmetry-operation descriptors modulo centering translations.

            * **[Representative symmetry operations](v0.1/properties/spacegroups/symops_representative.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative.md)
                
                Representative symmetry-operation descriptors modulo centering translations.

            * **[Wyckoff positions](v0.1/properties/spacegroups/wyckoff.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff.md)
                
                Wyckoff-position table for a specific space-group setting.

            * **[Wyckoff sets](v0.1/properties/spacegroups/wyckoff_sets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets.md)
                
                Sets of Wyckoff letters related by normalizer operations.

        * **symmetry**
            * **[Affine transformation](v0.1/properties/symmetry/affine_transformation.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation.md)
                
                An affine transformation acting on fractional crystallographic coordinates.

            * **[Basis transformation](v0.1/properties/symmetry/basis_transform.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/basis_transform`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/basis_transform.md)
                
                One crystallographic transform between coordinate descriptions, settings, cells, or related group embeddings.

            * **[Centering translation](v0.1/properties/symmetry/centering_translation.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/centering_translation`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/centering_translation.md)
                
                One centering translation of a conventional crystallographic cell.

            * **[Operation](v0.1/properties/symmetry/op.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op.md)
                
                Information related to a crystallographic operation acting within one coordinate setting.

            * **[Operation xyz](v0.1/properties/symmetry/op_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op_xyz.md)
                
                Coordinate operation expressed in the algebraic xyz form, also known as Jones' faithful representation (Bradley & Cracknell, 1972: pp. 35-37; adapted for computer strings).

            * **[Wyckoff position](v0.1/properties/symmetry/wyckoff_position.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/wyckoff_position`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/wyckoff_position.md)
                
                Information related to a Wyckoff position in a space-group setting.

        * **transformations**
            * **[Affine images](v0.1/properties/transformations/affine_images.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/affine_images`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/affine_images.md)
                
                Same-space-group affine images for a standard setting.

            * **[Affine normalizer](v0.1/properties/transformations/affine_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/affine_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/affine_normalizer.md)
                
                Affine normalizer coset representatives for one crystallographic space-group setting.

            * **[Affine normalizer coset data](v0.1/properties/transformations/affine_normalizer_coset_data.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/affine_normalizer_coset_data`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/affine_normalizer_coset_data.md)
                
                Ordered table of bounded affine normalizer coset-representative data for crystallographic space groups, with one item for each Hall setting.

            * **[Affine normalizer cosets](v0.1/properties/transformations/affine_normalizer_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/affine_normalizer_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/affine_normalizer_cosets.md)
                
                Runtime list of bounded affine normalizer coset representatives modulo the space group.

            * **[Backward lift criteria](v0.1/properties/transformations/backward_lift_criteria.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/backward_lift_criteria`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/backward_lift_criteria.md)
                
                Criteria table for one supergroup IT number used to lift occupied Wyckoff data from a subgroup back to that supergroup along a chosen Bärnighausen transform.

            * **[Bärnighausen subgroup transforms](v0.1/properties/transformations/baernighausen.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/baernighausen`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/baernighausen.md)
                
                Bärnighausen subgroup transform table for one parent setting or space-group type.

            * **[Continuous normalizer](v0.1/properties/transformations/continuous_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/continuous_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/continuous_normalizer.md)
                
                Parameterized continuous normalizer subspace for a setting.

            * **[Euclidean normalizer](v0.1/properties/transformations/euclidean_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/euclidean_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/euclidean_normalizer.md)
                
                Finite Euclidean normalizer operations for one crystallographic space-group setting.

            * **[Hall to IT standard transform](v0.1/properties/transformations/hall_to_it_std_transform.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/hall_to_it_std_transform`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/hall_to_it_std_transform.md)
                
                Exact basis and origin transform from one stored Hall setting to the International Tables standard Hall setting of the same space-group type.

            * **[Subgroup or transform index](v0.1/properties/transformations/index.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/index`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/index.md)
                
                Subgroup or transform index.

            * **[Isomorphic subgroup transforms](v0.1/properties/transformations/isomorphic_subgroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/isomorphic_subgroups`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/isomorphic_subgroups.md)
                
                Isomorphic subgroup transforms of bounded index for one parent setting or space-group type.

            * **[Klassengleiche subgroup subtype](v0.1/properties/transformations/k_subtype.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/k_subtype`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/k_subtype.md)
                
                Subtype of a klassengleiche (`k`) subgroup relation.

            * **[Maximal subgroup relations](v0.1/properties/transformations/maximal_subgroup_relations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/maximal_subgroup_relations`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/maximal_subgroup_relations.md)
                
                Maximal non-isomorphic subgroup relations for International Tables space-group types.

            * **[Number of coset representatives](v0.1/properties/transformations/n_coset_representatives.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_coset_representatives`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_coset_representatives.md)
                
                Number of nontrivial coset representatives retained after deduplication modulo the space group.

            * **[Number of cosets](v0.1/properties/transformations/n_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_cosets.md)
                
                Number of affine normalizer coset representatives stored for the setting.

            * **[Number of linear parts](v0.1/properties/transformations/n_linear_parts.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_linear_parts`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_linear_parts.md)
                
                Number of distinct linear matrix parts represented in a normalizer or transform table.

            * **[Number of orthogonal cosets](v0.1/properties/transformations/n_orthogonal_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_orthogonal_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_orthogonal_cosets.md)
                
                Number of orthogonal affine normalizer coset representatives stored for the setting.

            * **[Number of raw candidates](v0.1/properties/transformations/n_raw_candidates.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_raw_candidates`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_raw_candidates.md)
                
                Number of candidate affine operations considered before filtering and deduplication.

            * **[Number of unique candidates](v0.1/properties/transformations/n_unique_candidates.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_unique_candidates`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/n_unique_candidates.md)
                
                Number of candidate affine operations remaining after exact duplicate removal.

            * **[Orthogonal affine normalizer](v0.1/properties/transformations/orthogonal_affine_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/orthogonal_affine_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/orthogonal_affine_normalizer.md)
                
                Orthogonal affine normalizer coset representatives for one crystallographic space-group setting.

            * **[Orthogonal affine normalizer cosets](v0.1/properties/transformations/orthogonal_affine_normalizer_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/orthogonal_affine_normalizer_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/orthogonal_affine_normalizer_cosets.md)
                
                Runtime list of orthogonal signed-permutation affine normalizer coset representatives modulo the space group.

            * **[Same space group affine images std](v0.1/properties/transformations/same_space_group_affine_images_std.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/same_space_group_affine_images_std`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/same_space_group_affine_images_std.md)
                
                Same-space-group affine-image record for one International Tables standard setting.

            * **[Maximal subgroup type](v0.1/properties/transformations/subgroup_type.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/subgroup_type`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/subgroup_type.md)
                
                International Tables maximal subgroup class.

            * **[Criterion target](v0.1/properties/transformations/target.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/target`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/target.md)
                
                Exact target vector or scalar of a generated linear criterion.

            * **[To Hall entry](v0.1/properties/transformations/to_hall_entry.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/to_hall_entry`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/to_hall_entry.md)
                
                Target Hall-entry key to which a setting transform maps the current Hall setting.

            * **[Transformations per H-M entry](v0.1/properties/transformations/transformations_per_hm_entry.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/transformations_per_hm_entry`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/transformations_per_hm_entry.md)
                
                Transformation data grouped by H-M entry.

            * **[Transformations per IT number](v0.1/properties/transformations/transformations_per_it_number.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/transformations_per_it_number`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/transformations_per_it_number.md)
                
                Standard-setting transformation data grouped by International Tables space-group number.

            * **[Wyckoff splitting](v0.1/properties/transformations/wyckoff_splitting.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/wyckoff_splitting`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/wyckoff_splitting.md)
                
                Wyckoff-position splitting data associated with a subgroup or same-space-group transform.

    * **standards**
        * **[Anyterial definition provider standard](v0.1/standards/anyterial.md)** (standard) - [`https://schemas.anyterial.se/defs/v0.1/standards/anyterial`](https://schemas.anyterial.se/defs/v0.1/standards/anyterial.md)
            
            The Anyterial definition provider standard, comprising the spacegroups, pointgroups, and transformations entry types for crystallographic symmetry data.

