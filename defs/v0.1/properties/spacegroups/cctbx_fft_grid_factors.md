# Cctbx Fft Grid Factors (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors.md)**  
**Definition name:** `cctbx_fft_grid_factors`

**Property name:** Cctbx Fft Grid Factors  
**Description:** FFT grid-factor recommendations derived from cctbx for the space group, its structure seminvariants, and its Euclidean normalizer.  
**Type:** dictionary  



**Examples:**

- `{"space_group": [1, 1], "seminvariant": [1, 1], "euclidean": [1, 1]}`
- `{"space_group": [1, 1], "seminvariant": [2, 2], "euclidean": [2, 2]}`

**Formats:** [[JSON](cctbx_fft_grid_factors.json)] [[MD](cctbx_fft_grid_factors.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/cctbx_fft_grid_factors",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
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
}
```