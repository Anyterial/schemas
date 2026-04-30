# Hall-symbol to affine normalizer coset data index (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_symbol_to_affine_normalizer_coset_data`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_symbol_to_affine_normalizer_coset_data.md)**  
**Definition name:** `hall_symbol_to_affine_normalizer_coset_data`

**Property name:** Hall-symbol to affine normalizer coset data index  
**Description:** Index from normalized Hall entries to row positions in the top-level `affine_normalizer_coset_data` table.
It allows consumers to look up affine normalizer coset data by Hall entry while keeping `affine_normalizer_coset_data` as a compact ordered list.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary whose keys are normalized Hall entries using the same computer notation as the `hall_entry` field, with underscores replacing spaces.
- Each value MUST be a zero-based integer index into the top-level `affine_normalizer_coset_data` list.
- For every key-value pair, `affine_normalizer_coset_data[value].hall_entry` MUST equal the key.

**Examples:**

- `{"p_1": 0, "-p_1": 1}`

**Formats:** [[JSON](hall_symbol_to_affine_normalizer_coset_data.json)] [[MD](hall_symbol_to_affine_normalizer_coset_data.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/hall_symbol_to_affine_normalizer_coset_data",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
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
}
```