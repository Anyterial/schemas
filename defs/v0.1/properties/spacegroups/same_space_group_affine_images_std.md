# Same space group affine images std (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std.md)**  
**Definition name:** `same_space_group_affine_images_std`

**Property name:** Same space group affine images std  
**Description:** IT-number keyed same-space-group affine-image records for the International Tables standard settings.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary.
- Keys MUST be International Tables space-group numbers encoded as strings.
- Values MUST be dictionaries containing the Hall reference setting and the list of affine images for that IT number.

**Examples:**

- `{"1": {"it_number": 1, "hall": "p_1", "affine_images": [{"pmat": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]], "pvec": ["0", "0", "0"]}]}}`

**Formats:** [[JSON](same_space_group_affine_images_std.json)] [[MD](same_space_group_affine_images_std.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/same_space_group_affine_images_std",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
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
```