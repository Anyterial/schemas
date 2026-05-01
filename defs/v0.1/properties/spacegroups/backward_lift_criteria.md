# Backward lift criteria (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/backward_lift_criteria`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/backward_lift_criteria.md)**  
**Definition name:** `backward_lift_criteria`

**Property name:** Backward lift criteria  
**Description:** Criteria table for one supergroup IT number used to lift occupied Wyckoff data from a subgroup back to that supergroup along a chosen Bärnighausen transform.
The map is keyed by subgroup IT number.
Values are lists of transform records carrying a basis transform and a dictionary of Wyckoff-letter criteria.  
**Type:** dictionary  

**Requirements/Conventions**:

- Dynamic keys MUST be subgroup IT numbers represented as strings.
- Transform records SHOULD include `index`, `pmat`, `pvec`, and `criteria`.

**Examples:**

- `{"2": [{"index": 2, "pmat": [["1", "0", "0"], ["0", "1", "0"], ["0", "0", "2"]], "pvec": ["0", "0", "0"], "criteria": {"a": [{"roles": [["a", 0]], "coeffs": [[["1", "0", "0"]]], "target": ["0", "0", "0"]}]}}]}`

**Formats:** [[JSON](backward_lift_criteria.json)] [[MD](backward_lift_criteria.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/backward_lift_criteria",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
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
    "description": "Criteria table for one supergroup IT number used to lift occupied Wyckoff data from a subgroup back to that supergroup along a chosen B\u00e4rnighausen transform.\nThe map is keyed by subgroup IT number.\nValues are lists of transform records carrying a basis transform and a dictionary of Wyckoff-letter criteria.\n\n**Requirements/Conventions**:\n\n- Dynamic keys MUST be subgroup IT numbers represented as strings.\n- Transform records SHOULD include `index`, `pmat`, `pvec`, and `criteria`.",
    "properties": {},
    "examples": [
        {
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
    ]
}
```