# Index

* **v0.1**
    * **entrytypes**
        * **[Anyterial point group symmetry fields](v0.1/entrytypes/pointgroups.md)** (entrytype) - [`https://schemas.anyterial.se/defs/v0.1/entrytypes/pointgroups`](https://schemas.anyterial.se/defs/v0.1/entrytypes/pointgroups.md)
            

        * **[Anyterial space group symmetry fields](v0.1/entrytypes/spacegroups.md)** (entrytype) - [`https://schemas.anyterial.se/defs/v0.1/entrytypes/spacegroups`](https://schemas.anyterial.se/defs/v0.1/entrytypes/spacegroups.md)
            

    * **properties**
        * **core**
            * **[fraction](v0.1/properties/core/fraction.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/core/fraction`](https://schemas.anyterial.se/defs/v0.1/properties/core/fraction.md)
                
                A fraction represented as a string.

            * **[String markups](v0.1/properties/core/string_markups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups`](https://schemas.anyterial.se/defs/v0.1/properties/core/string_markups.md)
                
                Alternate markup renderings of a string whose plain-text or ASCII value is provided by a sibling property.
                The object is intended for display-oriented variants only; the corresponding unsuffixed sibling property remains the canonical plain string value.

        * **pointgroups**
            * **[Character Table Complex](v0.1/properties/pointgroups/character_table_complex.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_complex`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_complex.md)
                
                Complex irreducible character table of the crystallographic point group. Rows correspond to complex irreducible representations and columns follow the order of `conjugacy_classes`.

            * **[Character Table Real](v0.1/properties/pointgroups/character_table_real.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_real`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/character_table_real.md)
                
                Real irreducible character table of the crystallographic point group. Rows correspond to real irreducible representations and columns follow the order of `conjugacy_classes`.

            * **[Conjugacy Classes](v0.1/properties/pointgroups/conjugacy_classes.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/conjugacy_classes`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/conjugacy_classes.md)
                
                Conjugacy classes of a crystallographic point group. Each class lists its member operation indices, a representative operation, a conventional class label, and operation-type metadata used by the character tables.

            * **[Crystal System](v0.1/properties/pointgroups/crystal_system.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/crystal_system.md)
                
                The crystal system of the space group or point group.

            * **[Hermann-Mauguin Symbol](v0.1/properties/pointgroups/hm_symbol.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/hm_symbol.md)
                
                Hermann-Mauguin point-group symbol used as the key and display symbol for a point-group record.

            * **[Is Centrosymmetric](v0.1/properties/pointgroups/is_centrosymmetric.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/is_centrosymmetric`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/is_centrosymmetric.md)
                
                Boolean flag indicating whether the point group contains inversion symmetry.

            * **[Laue Class](v0.1/properties/pointgroups/laue_class.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/laue_class.md)
                
                The Laue class associated with the space group or point group.

            * **[N Conjugacy Classes](v0.1/properties/pointgroups/n_conjugacy_classes.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/n_conjugacy_classes.md)
                
                Number of conjugacy classes in the crystallographic point group.

            * **[Order](v0.1/properties/pointgroups/order.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order.md)
                
                Order of the point group, i.e. the number of operations in the finite point group.

            * **[Point groups](v0.1/properties/pointgroups/pointgroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/pointgroups`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/pointgroups.md)
                
                Ordered table of crystallographic point-group records.
                Each item contains point-group classification, finite point-group operations, conjugacy classes, and real and complex character tables generated from cctbx and spgrep.

            * **[Schoenflies Symbol](v0.1/properties/pointgroups/schoenflies.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies.md)
                
                The Schoenflies symbol for the space-group type.

            * **[Schoenflies symbol markups](v0.1/properties/pointgroups/schoenflies_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/schoenflies_markup.md)
                
                Display-oriented renderings of the Schoenflies symbol in `schoenflies`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Symmetry operations](v0.1/properties/pointgroups/symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/symops`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/symops.md)
                
                Full list of symmetry-operation descriptors for a point group.
                Each list member is a `op` object as defined by `/properties/symmetry/op`.
                For point-group operations, generated data currently uses `matrix` and `type`.

        * **spacegroups**
            * **[Affine images](v0.1/properties/spacegroups/affine_images.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_images.md)
                
                Same-space-group affine images for a standard setting.
                The list combines Euclidean normalizer operations and isomorphic subgroup transforms to enumerate alternative affine images of the same space group used by runtime search code.
                Matrix/vector transform fields follow `/properties/symmetry/basis_transform`.

            * **[Affine normalizer](v0.1/properties/spacegroups/affine_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer.md)
                
                Affine normalizer coset representatives for one crystallographic space-group setting.
                The representatives are listed modulo the space group itself, so each listed operation represents an equivalence class of affine normalizer operations rather than every operation in that class.
                This property contains representatives generated from bounded unimodular integer linear parts. It is a finite bounded representative table, not a complete infinite affine normalizer.

            * **[Affine normalizer coset data](v0.1/properties/spacegroups/affine_normalizer_coset_data.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_coset_data`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_coset_data.md)
                
                Ordered table of bounded affine normalizer coset-representative data for crystallographic space groups, with one item for each Hall setting.
                The affine normalizer of a space group describes affine mappings that send the space group to itself.
                In practical algorithms this information is useful after a candidate space-group setting has been identified, because additional normalizer representatives can be applied to explore equivalent descriptions, equivalent origin choices, or equivalent embeddings without changing the underlying space group.
                The representatives are listed modulo the space group itself, so each listed operation represents an equivalence class of normalizer operations rather than every operation in that class.

            * **[Affine normalizer cosets](v0.1/properties/spacegroups/affine_normalizer_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/affine_normalizer_cosets.md)
                
                Runtime list of bounded affine normalizer coset representatives modulo the space group.
                Each item is one finite listed representative and follows `/properties/symmetry/basis_transform`.
                The list is a bounded representative table, not a complete infinite affine normalizer.

            * **[Asu](v0.1/properties/spacegroups/asu.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu.md)
                
                Structured asymmetric-unit description for the space-group setting.

            * **[Asymmetric-unit cut](v0.1/properties/spacegroups/asu_cut.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_cut`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_cut.md)
                
                One serialized asymmetric-unit half-space cut or logical cut expression.
                Cut objects may recursively refer to other cut objects through `condition`, `lhs`, and `rhs`.

            * **[Asymmetric unit markups](v0.1/properties/spacegroups/asu_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_markup.md)
                
                Display-oriented renderings of the plain-string asymmetric-unit restrictions in `asu_str`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Shape-only asymmetric unit markups](v0.1/properties/spacegroups/asu_shape_only_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_markup.md)
                
                Display-oriented renderings of the plain-string shape-only asymmetric-unit restrictions in `asu_shape_only_str`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Shape-only asymmetric unit string](v0.1/properties/spacegroups/asu_shape_only_str.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_str`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_shape_only_str.md)
                
                Plain string rendering of the geometric shape part of the asymmetric-unit restrictions, without conditional refinements.

            * **[Asymmetric unit string](v0.1/properties/spacegroups/asu_str.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu_str.md)
                
                Plain string rendering of the asymmetric-unit restrictions for the space-group setting.

            * **[Backward lift criteria](v0.1/properties/spacegroups/backward_lift_criteria.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/backward_lift_criteria`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/backward_lift_criteria.md)
                
                Criteria table for one supergroup IT number used to lift occupied Wyckoff data from a subgroup back to that supergroup along a chosen Bärnighausen transform.
                Each list item groups transform records for one target subgroup IT number.
                The target subgroup IT number is stored in `target_it_number` rather than as a JSON dictionary key.

            * **[Bärnighausen subgroup transforms](v0.1/properties/spacegroups/baernighausen.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/baernighausen`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/baernighausen.md)
                
                Bärnighausen subgroup transform table for one parent setting or space-group type.
                Entries describe generated embeddings of subgroup settings into the containing parent setting.
                Each list item groups transform records for one target subgroup, with the target stored as ordinary data rather than as a JSON dictionary key.
                Transform records follow `/properties/symmetry/basis_transform`.

            * **[Bravais Type](v0.1/properties/spacegroups/bravais_type.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/bravais_type.md)
                
                The Bravais type of the translational lattice.

            * **[Cctbx Fft Grid Factors](v0.1/properties/spacegroups/cctbx_fft_grid_factors.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors.md)
                
                FFT grid-factor recommendations derived from cctbx for the space group, its structure seminvariants, and its Euclidean normalizer.

            * **[Centering translations](v0.1/properties/spacegroups/centering_translations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations.md)
                
                Centering translations of the conventional cell.
                Each list member is one exact fractional-coordinate centering translation as defined by `/properties/symmetry/centering_translation`.
                The zero translation `(0,0,0)` is listed first.

            * **[Centering translations as xyz strings](v0.1/properties/spacegroups/centering_translations_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centering_translations_xyz.md)
                
                Centering translations of the conventional cell, represented as `x,y,z`-style coordinate shifts. The zero translation is listed first.

            * **[Centring Type](v0.1/properties/spacegroups/centring_type.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/centring_type.md)
                
                The lattice centring symbol for the crystallographic setting.

            * **[Continuous Euclidean normalizer](v0.1/properties/spacegroups/continuous_euclidean_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_euclidean_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_euclidean_normalizer.md)
                
                Continuous Euclidean normalizer subspace before aggregation into the public transformation tables. It records the dimension and basis vectors of allowed continuous origin shifts.

            * **[Continuous normalizer](v0.1/properties/spacegroups/continuous_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_normalizer.md)
                
                Parameterized continuous normalizer subspace for a setting. It describes continuous origin-shift freedoms by dimension and fractional-coordinate basis vectors rather than by enumerating infinitely many operations.

            * **[Crystal System](v0.1/properties/spacegroups/crystal_system.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/crystal_system`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/crystal_system.md)
                
                The crystal system of the space group or point group.

            * **[Euclidean normalizer](v0.1/properties/spacegroups/euclidean_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/euclidean_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/euclidean_normalizer.md)
                
                Finite Euclidean normalizer operations for one crystallographic space-group setting.
                The Euclidean normalizer consists of metric-preserving affine operations that normalize the space group in the chosen setting.
                These operations are useful for algorithms that need to compare or enumerate equivalent descriptions of the same setting under rigid crystallographic changes of coordinates.

            * **[Hall Symbol](v0.1/properties/spacegroups/hall.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall.md)
                
                The Hall symbol for a crystallographic space-group setting.

            * **[Hall Aliases](v0.1/properties/spacegroups/hall_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases.md)
                
                Alternate ASCII Hall symbols or Hall-setting keys associated with the same generated setting.

            * **[Hall alias markups](v0.1/properties/spacegroups/hall_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_aliases_markup.md)
                
                Display-oriented renderings corresponding element-by-element to the alternate Hall symbols in `hall_aliases`.
                The plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.

            * **[Hall entry](v0.1/properties/spacegroups/hall_entry.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_entry.md)
                
                Normalized Hall-table entry key used internally by the generated datasets.

            * **[Hall symbol markups](v0.1/properties/spacegroups/hall_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_markup.md)
                
                Display-oriented renderings of the Hall symbol in `hall`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Hall to IT standard transform](v0.1/properties/spacegroups/hall_to_it_std_transform.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_to_it_std_transform`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_to_it_std_transform.md)
                
                Exact basis and origin transform from one stored Hall setting to the International Tables standard Hall setting of the same space-group type.
                This transform is useful when data generated or detected in an arbitrary Hall setting needs to be compared with a conventional IT-standard reference setting.
                The transform is represented by `matrix` and `vector`, following the same affine-transformation convention as the other generated transformation tables.

            * **[Harker planes](v0.1/properties/spacegroups/harker_planes.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/harker_planes`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/harker_planes.md)
                
                Harker planes of the space group in fractional Patterson coordinates, as generated by cctbx.
                Each entry describes one plane or special-position condition with an expression and optional exact normal, point, and constant data.

            * **[Hermann-Mauguin Cctbx Universal](v0.1/properties/spacegroups/hm_cctbx_universal.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_cctbx_universal`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_cctbx_universal.md)
                
                Universal Hermann-Mauguin symbol returned by cctbx for this setting.

            * **[Extended Hermann-Mauguin Symbol](v0.1/properties/spacegroups/hm_extended.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended.md)
                
                The setting-specific extended Hermann-Mauguin symbol for the space-group setting.

            * **[Hermann-Mauguin Extended Aliases](v0.1/properties/spacegroups/hm_extended_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases.md)
                
                Alternate ASCII forms of `hm_extended` that are accepted for the same generated setting. The preferred symbol is stored in `hm_extended`.

            * **[Extended Hermann-Mauguin alias markups](v0.1/properties/spacegroups/hm_extended_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_aliases_markup.md)
                
                Display-oriented renderings corresponding element-by-element to the alternate extended Hermann-Mauguin symbols in `hm_extended_aliases`.
                The plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.

            * **[Extended Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_extended_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_markup.md)
                
                Display-oriented renderings of the extended Hermann-Mauguin symbol in `hm_extended`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Hermann-Mauguin Extended Old](v0.1/properties/spacegroups/hm_extended_old.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_extended_old.md)
                
                The older extended Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.

            * **[Full Hermann-Mauguin Symbol](v0.1/properties/spacegroups/hm_full.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full.md)
                
                The setting-specific full Hermann-Mauguin symbol for the space-group setting.

            * **[Hermann-Mauguin Full Aliases](v0.1/properties/spacegroups/hm_full_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases.md)
                
                Alternate ASCII forms of `hm_full` that are accepted for the same generated setting. The preferred symbol is stored in `hm_full`.

            * **[Full Hermann-Mauguin alias markups](v0.1/properties/spacegroups/hm_full_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_aliases_markup.md)
                
                Display-oriented renderings corresponding element-by-element to the alternate full Hermann-Mauguin symbols in `hm_full_aliases`.
                The plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.

            * **[Full Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_full_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_markup.md)
                
                Display-oriented renderings of the setting-specific full Hermann-Mauguin symbol in `hm_full`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Hermann-Mauguin Full Old](v0.1/properties/spacegroups/hm_full_old.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_old.md)
                
                The older full Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.

            * **[Hermann-Mauguin Full Std](v0.1/properties/spacegroups/hm_full_std.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std.md)
                
                The International Tables standard full Hermann-Mauguin symbol for the space-group type.

            * **[Standard full Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_full_std_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_full_std_markup.md)
                
                Display-oriented renderings of the ITA-standard full Hermann-Mauguin symbol in `hm_full_std`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Short Hermann-Mauguin Symbol](v0.1/properties/spacegroups/hm_short.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short.md)
                
                The setting-specific short Hermann-Mauguin symbol for the space-group setting.

            * **[Hermann-Mauguin Short Aliases](v0.1/properties/spacegroups/hm_short_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases.md)
                
                Alternate ASCII forms of `hm_short` that are accepted for the same generated setting. The preferred symbol is stored in `hm_short`.

            * **[Short Hermann-Mauguin alias markups](v0.1/properties/spacegroups/hm_short_aliases_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_aliases_markup.md)
                
                Display-oriented renderings corresponding element-by-element to the alternate short Hermann-Mauguin symbols in `hm_short_aliases`.
                The plain string values are stored in the corresponding unsuffixed alias list; this list only provides alternate markup forms for display.

            * **[Short Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_short_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_markup.md)
                
                Display-oriented renderings of the setting-specific short Hermann-Mauguin symbol in `hm_short`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Hermann-Mauguin Short Old](v0.1/properties/spacegroups/hm_short_old.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_old.md)
                
                The older short Hermann-Mauguin symbol retained as an alias for symbols superseded by newer `e`-glide notation.

            * **[Hermann-Mauguin Short Std](v0.1/properties/spacegroups/hm_short_std.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std.md)
                
                The International Tables standard short Hermann-Mauguin symbol for the space-group type.

            * **[Standard short Hermann-Mauguin symbol markups](v0.1/properties/spacegroups/hm_short_std_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hm_short_std_markup.md)
                
                Display-oriented renderings of the ITA-standard short Hermann-Mauguin symbol in `hm_short_std`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Index](v0.1/properties/spacegroups/index.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index.md)
                
                Subgroup or transform index. For subgroup transforms it is the crystallographic subgroup index `[G:H]`, equal to the determinant factor of the basis transformation when applicable.

            * **[Is Centric](v0.1/properties/spacegroups/is_centric.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_centric.md)
                
                Boolean flag indicating whether the cctbx space group is centric.

            * **[Is Chiral](v0.1/properties/spacegroups/is_chiral.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_chiral.md)
                
                Boolean flag indicating whether the space group is chiral.

            * **[Is Enantiomorphic](v0.1/properties/spacegroups/is_enantiomorphic.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_enantiomorphic.md)
                
                Boolean flag indicating whether the space-group type belongs to an enantiomorphic pair.

            * **[Is Reference Setting](v0.1/properties/spacegroups/is_reference_setting.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/is_reference_setting.md)
                
                Boolean flag indicating whether this Hall setting is the selected reference setting for its International Tables space-group number.

            * **[Isomorphic subgroup transforms](v0.1/properties/spacegroups/isomorphic_subgroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups.md)
                
                Isomorphic subgroup transforms of bounded index for one parent setting or space-group type.
                An isomorphic subgroup has the same space-group type as the parent but is embedded with a finite index, usually corresponding to an enlarged unit cell or a sublattice choice.
                These transforms are useful for algorithms that need to enumerate same-type subgroup embeddings, compare structures under supercell changes, or construct bounded same-space-group refinement paths.

            * **[International Tables Coordinate-System Code](v0.1/properties/spacegroups/it_coordinate_system_code.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_coordinate_system_code.md)
                
                The International Tables coordinate-system code for the setting.

            * **[International Tables Space-Group Number](v0.1/properties/spacegroups/it_number.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number.md)
                
                The International Tables space-group number.

            * **[It Number Enantiomorphic](v0.1/properties/spacegroups/it_number_enantiomorphic.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/it_number_enantiomorphic.md)
                
                International Tables number of the enantiomorphic partner space group, when one exists. The value is null for space groups without a distinct enantiomorphic partner.

            * **[Klassengleiche subgroup subtype](v0.1/properties/spacegroups/k_subtype.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/k_subtype`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/k_subtype.md)
                
                Subtype of a klassengleiche (`k`) subgroup relation. Values distinguish loss of centering translations from enlarged-unit-cell subgroups; the value is null for non-`k` relations.

            * **[Laue Class](v0.1/properties/spacegroups/laue_class.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/laue_class`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/laue_class.md)
                
                The Laue class associated with the space group or point group.

            * **[Maximal subgroup relations](v0.1/properties/spacegroups/maximal_subgroup_relations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/maximal_subgroup_relations`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/maximal_subgroup_relations.md)
                
                Maximal non-isomorphic subgroup relations for International Tables space-group types.
                Each list item describes all known maximal non-isomorphic subgroup relations for one supergroup IT number.
                The supergroup IT number is stored in `supergroup_it_number` rather than as a JSON dictionary key.

            * **[N Centering Translations](v0.1/properties/spacegroups/n_centering_translations.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_centering_translations`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_centering_translations.md)
                
                Number of centering translations in the conventional cell of the space-group setting.

            * **[N Coset Representatives](v0.1/properties/spacegroups/n_coset_representatives.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_coset_representatives`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_coset_representatives.md)
                
                Number of nontrivial coset representatives retained after deduplication modulo the space group.

            * **[N Cosets](v0.1/properties/spacegroups/n_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_cosets.md)
                
                Number of affine normalizer coset representatives stored for the setting.

            * **[N Linear Parts](v0.1/properties/spacegroups/n_linear_parts.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_linear_parts`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_linear_parts.md)
                
                Number of distinct linear matrix parts represented in a normalizer or transform table.

            * **[N Orthogonal Cosets](v0.1/properties/spacegroups/n_orthogonal_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_orthogonal_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_orthogonal_cosets.md)
                
                Number of orthogonal affine normalizer coset representatives stored for the setting.

            * **[N Pointgroup Symops](v0.1/properties/spacegroups/n_pointgroup_symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_pointgroup_symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_pointgroup_symops.md)
                
                Number of point-group symmetry operations represented by the space group, excluding centering translations.

            * **[N Raw Candidates](v0.1/properties/spacegroups/n_raw_candidates.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_raw_candidates`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_raw_candidates.md)
                
                Number of candidate affine operations considered before filtering and deduplication.

            * **[N Symops](v0.1/properties/spacegroups/n_symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_symops.md)
                
                Number of symmetry operations in the finite operation list of the generated entry.

            * **[N Unique Candidates](v0.1/properties/spacegroups/n_unique_candidates.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_unique_candidates`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/n_unique_candidates.md)
                
                Number of candidate affine operations remaining after exact duplicate removal.

            * **[Orthogonal affine normalizer](v0.1/properties/spacegroups/orthogonal_affine_normalizer.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer.md)
                
                Orthogonal affine normalizer coset representatives for one crystallographic space-group setting.
                The representatives are listed modulo the space group itself, so each listed operation represents an equivalence class of affine normalizer operations rather than every operation in that class.
                This property contains the signed-permutation subset of affine normalizer representatives.

            * **[Orthogonal affine normalizer cosets](v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/orthogonal_affine_normalizer_cosets.md)
                
                Runtime list of orthogonal signed-permutation affine normalizer coset representatives modulo the space group.
                Each item is one finite listed representative and follows `/properties/symmetry/basis_transform`.
                The list is a bounded representative table, not a complete infinite affine normalizer.

            * **[Point-Group Hermann-Mauguin Symbol](v0.1/properties/spacegroups/point_group.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/point_group.md)
                
                The Hermann-Mauguin point-group symbol associated with the space group.

            * **[Same space group affine images std](v0.1/properties/spacegroups/same_space_group_affine_images_std.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std.md)
                
                Same-space-group affine-image record for one International Tables standard setting.

            * **[Schoenflies Symbol](v0.1/properties/spacegroups/schoenflies.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies.md)
                
                The Schoenflies symbol for the space-group type.

            * **[Schoenflies symbol markups](v0.1/properties/spacegroups/schoenflies_markup.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies_markup`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/schoenflies_markup.md)
                
                Display-oriented renderings of the Schoenflies symbol in `schoenflies`.
                The plain string value is stored in the corresponding unsuffixed property; this object only provides alternate markup forms for display.

            * **[Setting](v0.1/properties/spacegroups/setting.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting.md)
                
                Setting suffix or setting annotation extracted from the cctbx universal Hermann-Mauguin symbol.

            * **[International Tables setting code n:c](v0.1/properties/spacegroups/setting_it_nc.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc.md)
                
                International Tables setting identifier in `n:c` notation.

            * **[International Tables setting-code aliases](v0.1/properties/spacegroups/setting_it_nc_aliases.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases.md)
                
                Alternative International Tables `n:c` setting identifiers that refer to the same Hall setting or are otherwise treated as aliases of `setting_it_nc` by the generator. This field is used only when the source tables expose more than one conventional label for the same generated setting.

            * **[Setting Plaintext](v0.1/properties/spacegroups/setting_plaintext.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_plaintext.md)
                
                Human-readable description of the International Tables coordinate-system setting.

            * **[Space-group symbols](v0.1/properties/spacegroups/spacegroup_symbols.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroup_symbols.md)
                
                Ordered table of conventional space-group symbol rows.
                Each row describes one Hall setting where the International Tables symbol data is available, including the IT coordinate-system code, Hall symbol, IT number, and Hermann-Mauguin symbols.

            * **[Space groups](v0.1/properties/spacegroups/spacegroups.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spacegroups.md)
                
                Ordered table of crystallographic space-group setting records.
                Each item describes one concrete Hall/International Tables setting of a space group, including symbols, classifications, symmetry operations, asymmetric-unit information, Wyckoff positions, and related auxiliary data.
                The companion top-level `indicies.index_hall_entry_to_spacegroups` lookup maps normalized Hall entries to indices in this list; it is not an OPTIMADE property.

            * **[Spglib Hall](v0.1/properties/spacegroups/spglib_hall.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall.md)
                
                Hall setting selected by spglib for the space-group type or setting, represented as a normalized Hall key.

            * **[Spglib Hall Numbers](v0.1/properties/spacegroups/spglib_hall_numbers.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/spglib_hall_numbers.md)
                
                spglib Hall numbers corresponding to the generated setting.

            * **[Structure Seminvariants](v0.1/properties/spacegroups/structure_seminvariants.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/structure_seminvariants.md)
                
                Structure seminvariant vectors and moduli for the space-group setting. These characterize phase restrictions and FFT grid constraints associated with the symmetry.

            * **[Maximal subgroup type](v0.1/properties/spacegroups/subgroup_type.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/subgroup_type`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/subgroup_type.md)
                
                International Tables maximal subgroup class: `t` for translationengleiche or `k` for klassengleiche.

            * **[Symmetry operations](v0.1/properties/spacegroups/symops.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops.md)
                
                Full list of symmetry-operation descriptors for a space-group setting.
                Each list member is a `op` object as defined by `/properties/symmetry/op`.
                For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

            * **[Symmetry operation generators](v0.1/properties/spacegroups/symops_generators.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators.md)
                
                Minimal generator subset of the full symmetry-operation group for a space-group setting.
                Each list member is a `op` object as defined by `/properties/symmetry/op`.
                For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

            * **[Symops Generators Xyz](v0.1/properties/spacegroups/symops_generators_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_generators_xyz.md)
                
                Minimal generator subset of the full symmetry-operation group in fractional `x,y,z` notation, ordered consistently with `symops_generators`.

            * **[Representative symmetry operations](v0.1/properties/spacegroups/symops_representative.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative.md)
                
                Representative symmetry-operation descriptors modulo centering translations.
                Each list member is a `op` object as defined by `/properties/symmetry/op`.
                For space-group operations, generated data currently uses `rot_type`, `axis`, `sense`, `screw_glide`, and `origin_shift`.

            * **[Symops Representative Xyz](v0.1/properties/spacegroups/symops_representative_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_representative_xyz.md)
                
                Representative symmetry operations modulo centering translations in fractional `x,y,z` notation, ordered consistently with `symops_representative`.

            * **[Symmetry operations in x,y,z notation](v0.1/properties/spacegroups/symops_xyz.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_xyz`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/symops_xyz.md)
                
                Full list of symmetry operations for the space-group setting written in fractional `x,y,z` coordinate notation. Each expression acts on fractional coordinates in the setting represented by the containing Hall entry.

            * **[Target](v0.1/properties/spacegroups/target.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/target`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/target.md)
                
                Target vector or target value in a generated linear criterion.
                In current generated criteria it is usually represented as exact rational components serialized as strings.
                The semantic meaning of `target` is parent-specific and should not be reused as a broad standalone concept.

            * **[To Hall](v0.1/properties/spacegroups/to_hall.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall.md)
                
                Reference Hall-entry key to which a setting transform maps the current Hall setting.

            * **[To Hall Symbol](v0.1/properties/spacegroups/to_hall_symbol.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall_symbol`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/to_hall_symbol.md)
                
                Display Hall symbol corresponding to `to_hall`.

            * **[Transformations per Hall entry](v0.1/properties/spacegroups/transformations_per_hall.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/transformations_per_hall`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/transformations_per_hall.md)
                
                Transformation data grouped by Hall entry.
                Each list item contains the Hall entry as ordinary data together with all transformation sections generated for that setting.
                This representation avoids using Hall entries as JSON dictionary keys in the OPTIMADE-described payload.

            * **[Transformations per IT number](v0.1/properties/spacegroups/transformations_per_it_number.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/transformations_per_it_number`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/transformations_per_it_number.md)
                
                Standard-setting transformation data grouped by International Tables space-group number.
                Each list item contains the IT number as ordinary data together with all standard-setting transformation sections generated for that space-group type.
                This representation avoids using IT numbers as JSON dictionary keys in the OPTIMADE-described payload.

            * **[Wyckoff positions](v0.1/properties/spacegroups/wyckoff.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff.md)
                
                Wyckoff-position table for a specific space-group setting.
                Each list item describes one Wyckoff position and includes the Wyckoff letter as ordinary data.
                This list representation avoids using JSON dictionary keys as crystallographic data.
                Items follow `/properties/symmetry/wyckoff_position`.

            * **[Wyckoff Sets](v0.1/properties/spacegroups/wyckoff_sets.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_sets.md)
                
                Sets of Wyckoff letters related by normalizer operations. Each inner list groups Wyckoff positions that can be interchanged by the relevant normalizer action.

            * **[Wyckoff splitting](v0.1/properties/spacegroups/wyckoff_splitting.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_splitting`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff_splitting.md)
                
                Wyckoff-position splitting data associated with a subgroup or same-space-group transform.
                Each list item gives the split of one parent Wyckoff position.
                The parent Wyckoff letter is stored in the `parent` field rather than as a JSON dictionary key.

        * **symmetry**
            * **[Affine transformation](v0.1/properties/symmetry/affine_transformation.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/affine_transformation.md)
                
                One exact affine transformation acting on fractional crystallographic coordinates.
                The transformation is represented by a 3 by 3 matrix and a 3-vector, both serialized with exact string entries.
                Parent properties define the coordinate convention and semantic role of the transformation, for example whether it is an operation within one setting, a setting transform, a subgroup embedding, or a normalizer representative.

            * **[Basis transformation](v0.1/properties/symmetry/basis_transform.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/basis_transform`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/basis_transform.md)
                
                One crystallographic transform between coordinate descriptions, settings, cells, or related group embeddings.
                The affine map itself is stored in the embedded `affine_transformation` field.
                Parent tables use this object for Hall-to-standard transforms, Bärnighausen subgroup transforms, isomorphic subgroup transforms, normalizer representatives, and same-space-group affine images.

            * **[Centering translation](v0.1/properties/symmetry/centering_translation.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/centering_translation`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/centering_translation.md)
                
                One centering translation of a conventional crystallographic cell.
                The translation is represented in fractional coordinates using exact fraction strings.

            * **[Operation](v0.1/properties/symmetry/op.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/op.md)
                
                A classified crystallographic operation acting within one coordinate setting.
                The affine map itself is stored in the embedded `affine_transformation` field.
                The remaining fields classify the operation crystallographically, for example by rotation type, axis, sense, and screw or glide component.

            * **[Wyckoff position](v0.1/properties/symmetry/wyckoff_position.md)** (property) - [`https://schemas.anyterial.se/defs/v0.1/properties/symmetry/wyckoff_position`](https://schemas.anyterial.se/defs/v0.1/properties/symmetry/wyckoff_position.md)
                
                One Wyckoff position in a space-group setting.
                The record gives the multiplicity, oriented site-symmetry symbol, representative coordinate, full orbit, and orbit factorized modulo centering translations.

    * **standards**
        * **[Anyterial definition provider standard](v0.1/standards/anyterial.md)** (standard) - [`https://schemas.anyterial.se/defs/v0.1/standards/anyterial`](https://schemas.anyterial.se/defs/v0.1/standards/anyterial.md)
            
            Anyterial definition provider standard

