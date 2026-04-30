# Isomorphic subgroup transforms (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups.md)**  
**Definition name:** `isomorphic_subgroups`

**Property name:** Isomorphic subgroup transforms  
**Description:** Isomorphic subgroup transforms of bounded index. These transforms map a space group to a subgroup of the same space-group type, usually corresponding to an enlarged unit cell.
The outer dictionary is keyed by the parent table convention, for example Hall entries or IT numbers.
Transform records use `pmat` and `pvec` as defined by `/properties/symmetry/basis_transform`.  
**Type:** dictionary  

**Requirements/Conventions**:

- Dynamic outer keys identify parent settings or space groups according to the containing dataset.
- Values are either dictionaries containing an `items` list of transform records or direct maps to lists of transform records.
- Each transform record SHOULD follow `/properties/symmetry/basis_transform` for its matrix and vector fields.

**Examples:**

- `{"c_2y": {"items": [{"index": 2, "pmat": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "2"]], "pvec": ["0", "0", "0"]}]}}`

**Formats:** [[JSON](isomorphic_subgroups.json)] [[MD](isomorphic_subgroups.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/isomorphic_subgroups",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
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
}
```