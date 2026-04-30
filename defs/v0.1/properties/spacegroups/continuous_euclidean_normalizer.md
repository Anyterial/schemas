# Continuous Euclidean normalizer (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_euclidean_normalizer`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_euclidean_normalizer.md)**  
**Definition name:** `continuous_euclidean_normalizer`

**Property name:** Continuous Euclidean normalizer  
**Description:** Continuous Euclidean normalizer subspace before aggregation into the public transformation tables. It records the dimension and basis vectors of allowed continuous origin shifts.  
**Type:** dictionary  

**Requirements/Conventions**:

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

**Examples:**

- `{"dimension": 3, "coordinate_system": "fractional", "basis_vectors": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "1"]]}`

**Formats:** [[JSON](continuous_euclidean_normalizer.json)] [[MD](continuous_euclidean_normalizer.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/continuous_euclidean_normalizer",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
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
}
```