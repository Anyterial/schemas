# Bärnighausen subgroup transforms (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/baernighausen`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/baernighausen.md)**  
**Definition name:** `baernighausen`

**Property name:** Bärnighausen subgroup transforms  
**Description:** Bärnighausen subgroup transform table for one parent setting or space-group type.
Entries describe generated embeddings of subgroup settings into the containing parent setting.
Transform records use `matrix` and `vector` according to `/properties/symmetry/affine_transformation`.  
**Type:** dictionary  

**Requirements/Conventions**:

- Dynamic keys identify target subgroup settings or target subgroup space-group types according to the containing dataset.
- Values are lists of transform records.
- Each transform record SHOULD follow `/properties/symmetry/affine_transformation` for its matrix and vector fields.

**Examples:**

- `{"p_1": [{"index": 2, "matrix": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "2"]], "vector": ["0", "0", "0"]}]}`

**Formats:** [[JSON](baernighausen.json)] [[MD](baernighausen.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/baernighausen",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "B\u00e4rnighausen subgroup transforms",
    "$comment": "Anyterial transform collection property using the common affine-transformation definition for transform items.",
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
    "description": "B\u00e4rnighausen subgroup transform table for one parent setting or space-group type.\nEntries describe generated embeddings of subgroup settings into the containing parent setting.\nTransform records use `matrix` and `vector` according to `/properties/symmetry/affine_transformation`.\n\n**Requirements/Conventions**:\n\n- Dynamic keys identify target subgroup settings or target subgroup space-group types according to the containing dataset.\n- Values are lists of transform records.\n- Each transform record SHOULD follow `/properties/symmetry/affine_transformation` for its matrix and vector fields.",
    "properties": {},
    "examples": [
        {
            "p_1": [
                {
                    "index": 2,
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
                            "2"
                        ]
                    ],
                    "vector": [
                        "0",
                        "0",
                        "0"
                    ]
                }
            ]
        }
    ]
}
```