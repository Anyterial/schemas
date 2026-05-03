# Asymmetric unit (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu.md)**  
**Definition name:** `asu`

**Property name:** Asymmetric unit  
**Description:** Direct-space asymmetric unit for the space-group setting, represented as a bounded non-recursive set of half-space cuts and boundary ownership rules.
The representation is equivalent to the recursive cctbx direct-space ASU cut expression documented by Grosse-Kunstleve et al., Acta Cryst. A67, 269 (2011), but stores the volume, face, edge, and vertex rules in separate fixed-depth tables.
A point is inside the ASU volume only if all `volume_cuts` pass.
Each volume cut tests an oriented plane from `planes`: a positive plane value includes the point, a negative value excludes it, and an exactly zero value uses `when_zero`.
Boundary rules are disjunctive normal form rule tables: the outer `dnf` list is OR, each inner list is AND, and each term tests one oriented plane and uses its own `on_zero` action.
Face rules may descend to edge rules on equality, edge rules may descend to vertex rules on equality, and vertex rules terminate with include or exclude actions.  
**Type:** dictionary  

The original cctbx-style recursive data structure can be recovered from this bounded representation with the following routine:

```python
def bounded_asu_to_cctbx_recursive_data(bounded):
    planes = {plane["id"]: plane for plane in bounded["planes"]}
    rules = {level: {rule["id"]: rule for rule in bounded[f"{level}_rules"]}
             for level in ("face", "edge", "vertex")}

    def expr_from_terms(terms, op):
        out = terms[0] if terms else None
        for term in terms[1:]:
            out = {"kind": "expr", "op": op, "lhs": out, "rhs": term}
        return out

    def expr_from_rule(level, rule_id):
        clauses = []
        for clause in rules[level][rule_id]["dnf"]:
            terms = [cut_from_action(t["plane_id"], t["on_zero"], level)
                     for t in clause]
            clauses.append(expr_from_terms(terms, "&"))
        return expr_from_terms(clauses, "|")

    def cut_from_action(plane_id, action, level):
        plane = planes[plane_id]
        if action["action"] in ("include", "exclude"):
            condition = None
            inclusive = action["action"] == "include"
        else:
            next_level = {"volume": "face", "face": "edge", "edge": "vertex"}[level]
            condition = expr_from_rule(next_level, action["rule_id"])
            inclusive = True
        return {
            "kind": "cut",
            "normal": plane["normal"],
            "const": plane["const"],
            "inclusive": inclusive,
            "condition": condition,
        }

    return {
        "cuts": [cut_from_action(cut["plane_id"], cut["when_zero"], "volume")
                 for cut in bounded["volume_cuts"]],
        "shape_only_cuts": [
            {
                "kind": "cut",
                "normal": planes[cut["plane_id"]]["normal"],
                "const": planes[cut["plane_id"]]["const"],
                "inclusive": True,
                "condition": None,
            }
            for cut in bounded["volume_cuts"]
        ],
    }
```

**Requirements/Conventions**:

- It MUST be a dictionary with the following keys:

    - **planes**: REQUIRED; List of dictionaries.
      Registry of all oriented affine planes used by volume cuts and boundary rules.
      The plane value is `normal[0]*x + normal[1]*y + normal[2]*z + const` in fractional coordinates.
      The positive side of the plane is the inside half-space for the corresponding cut term.

    - **volume\_cuts**: REQUIRED; List of dictionaries.
      Top-level volume cuts combined as one conjunction.
      Each volume cut references one plane and gives explicit actions for positive, negative, and zero plane values.

    - **face\_rules**: REQUIRED; List of dictionaries.
      Rule table for two-dimensional face-boundary ownership.
      Face rules are evaluated only when a volume cut plane value is exactly zero.

    - **edge\_rules**: REQUIRED; List of dictionaries.
      Rule table for one-dimensional edge-boundary ownership.
      Edge rules are evaluated only after a volume cut and a face-level term both evaluate exactly to zero.

    - **vertex\_rules**: REQUIRED; List of dictionaries.
      Terminal rule table for zero-dimensional vertex-boundary ownership.
      Vertex rules cannot descend to another rule level.

**Examples:**

- `{"planes": [{"id": "p0", "normal": ["1", "0", "0"], "const": "0"}, {"id": "p1", "normal": ["-1", "0", "0"], "const": "1"}], "volume_cuts": [{"id": "v0", "plane_id": "p0", "when_positive": "include", "when_negative": "exclude", "when_zero": {"action": "include"}}, {"id": "v1", "plane_id": "p1", "when_positive": "include", "when_negative": "exclude", "when_zero": {"action": "exclude"}}], "face_rules": [], "edge_rules": [], "vertex_rules": []}`

**Formats:** [[JSON](asu.json)] [[MD](asu.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/asu",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Asymmetric unit",
    "$comment": "Bounded non-recursive direct-space asymmetric-unit representation for one space-group setting.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "asu",
        "label": "asu_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Direct-space asymmetric unit for the space-group setting, represented as a bounded non-recursive set of half-space cuts and boundary ownership rules.\nThe representation is equivalent to the recursive cctbx direct-space ASU cut expression documented by Grosse-Kunstleve et al., Acta Cryst. A67, 269 (2011), but stores the volume, face, edge, and vertex rules in separate fixed-depth tables.\nA point is inside the ASU volume only if all `volume_cuts` pass.\nEach volume cut tests an oriented plane from `planes`: a positive plane value includes the point, a negative value excludes it, and an exactly zero value uses `when_zero`.\nBoundary rules are disjunctive normal form rule tables: the outer `dnf` list is OR, each inner list is AND, and each term tests one oriented plane and uses its own `on_zero` action.\nFace rules may descend to edge rules on equality, edge rules may descend to vertex rules on equality, and vertex rules terminate with include or exclude actions.\n\nThe original cctbx-style recursive data structure can be recovered from this bounded representation with the following routine:\n\n```python\ndef bounded_asu_to_cctbx_recursive_data(bounded):\n    planes = {plane[\"id\"]: plane for plane in bounded[\"planes\"]}\n    rules = {level: {rule[\"id\"]: rule for rule in bounded[f\"{level}_rules\"]}\n             for level in (\"face\", \"edge\", \"vertex\")}\n\n    def expr_from_terms(terms, op):\n        out = terms[0] if terms else None\n        for term in terms[1:]:\n            out = {\"kind\": \"expr\", \"op\": op, \"lhs\": out, \"rhs\": term}\n        return out\n\n    def expr_from_rule(level, rule_id):\n        clauses = []\n        for clause in rules[level][rule_id][\"dnf\"]:\n            terms = [cut_from_action(t[\"plane_id\"], t[\"on_zero\"], level)\n                     for t in clause]\n            clauses.append(expr_from_terms(terms, \"&\"))\n        return expr_from_terms(clauses, \"|\")\n\n    def cut_from_action(plane_id, action, level):\n        plane = planes[plane_id]\n        if action[\"action\"] in (\"include\", \"exclude\"):\n            condition = None\n            inclusive = action[\"action\"] == \"include\"\n        else:\n            next_level = {\"volume\": \"face\", \"face\": \"edge\", \"edge\": \"vertex\"}[level]\n            condition = expr_from_rule(next_level, action[\"rule_id\"])\n            inclusive = True\n        return {\n            \"kind\": \"cut\",\n            \"normal\": plane[\"normal\"],\n            \"const\": plane[\"const\"],\n            \"inclusive\": inclusive,\n            \"condition\": condition,\n        }\n\n    return {\n        \"cuts\": [cut_from_action(cut[\"plane_id\"], cut[\"when_zero\"], \"volume\")\n                 for cut in bounded[\"volume_cuts\"]],\n        \"shape_only_cuts\": [\n            {\n                \"kind\": \"cut\",\n                \"normal\": planes[cut[\"plane_id\"]][\"normal\"],\n                \"const\": planes[cut[\"plane_id\"]][\"const\"],\n                \"inclusive\": True,\n                \"condition\": None,\n            }\n            for cut in bounded[\"volume_cuts\"]\n        ],\n    }\n```\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary with the following keys:\n\n    - **planes**: REQUIRED; List of dictionaries.\n      Registry of all oriented affine planes used by volume cuts and boundary rules.\n      The plane value is `normal[0]*x + normal[1]*y + normal[2]*z + const` in fractional coordinates.\n      The positive side of the plane is the inside half-space for the corresponding cut term.\n\n    - **volume\\_cuts**: REQUIRED; List of dictionaries.\n      Top-level volume cuts combined as one conjunction.\n      Each volume cut references one plane and gives explicit actions for positive, negative, and zero plane values.\n\n    - **face\\_rules**: REQUIRED; List of dictionaries.\n      Rule table for two-dimensional face-boundary ownership.\n      Face rules are evaluated only when a volume cut plane value is exactly zero.\n\n    - **edge\\_rules**: REQUIRED; List of dictionaries.\n      Rule table for one-dimensional edge-boundary ownership.\n      Edge rules are evaluated only after a volume cut and a face-level term both evaluate exactly to zero.\n\n    - **vertex\\_rules**: REQUIRED; List of dictionaries.\n      Terminal rule table for zero-dimensional vertex-boundary ownership.\n      Vertex rules cannot descend to another rule level.",
    "properties": {
        "planes": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Registry of oriented affine planes used by the ASU cuts and rules.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object"
                ],
                "required": [
                    "id",
                    "normal",
                    "const"
                ],
                "description": "One oriented affine plane in fractional coordinates.",
                "properties": {
                    "id": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "Stable identifier used by `volume_cuts` and rule terms to refer to this plane."
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
                            "array"
                        ],
                        "description": "The three exact rational coefficients multiplying `x`, `y`, and `z` in the plane equation.",
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
            }
        },
        "volume_cuts": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Top-level ASU volume cuts, combined as an AND-list.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object"
                ],
                "required": [
                    "id",
                    "plane_id",
                    "when_positive",
                    "when_negative",
                    "when_zero"
                ],
                "description": "One top-level oriented cut of the three-dimensional ASU volume.",
                "properties": {
                    "id": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "Stable identifier for this volume cut."
                    },
                    "plane_id": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "Identifier of the plane tested by this volume cut."
                    },
                    "when_positive": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "enum": [
                            "include"
                        ],
                        "description": "Action for positive plane values."
                    },
                    "when_negative": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "enum": [
                            "exclude"
                        ],
                        "description": "Action for negative plane values."
                    },
                    "when_zero": {
                        "x-optimade-type": "dictionary",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "object"
                        ],
                        "required": [
                            "action"
                        ],
                        "description": "Action for points exactly on the volume-cut plane.",
                        "properties": {
                            "action": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string"
                                ],
                                "enum": [
                                    "include",
                                    "exclude",
                                    "evaluate_face_rule"
                                ],
                                "description": "Boundary action for this equality case."
                            },
                            "rule_id": {
                                "x-optimade-type": "string",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "string",
                                    "null"
                                ],
                                "description": "Identifier of the face rule to evaluate when `action` is `evaluate_face_rule`."
                            }
                        }
                    }
                }
            }
        },
        "face_rules": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Disjunctive-normal-form face-boundary ownership rules.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object"
                ],
                "required": [
                    "id",
                    "dnf"
                ],
                "description": "One face-level ownership rule.",
                "properties": {
                    "id": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "Stable identifier for this face rule."
                    },
                    "dnf": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array"
                        ],
                        "description": "OR-list of AND-lists of face-level terms.",
                        "items": {
                            "x-optimade-type": "list",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array"
                            ],
                            "description": "One AND-clause in the face-level rule.",
                            "items": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object"
                                ],
                                "required": [
                                    "plane_id",
                                    "on_zero"
                                ],
                                "description": "One face-level plane test.",
                                "properties": {
                                    "plane_id": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "description": "Identifier of the plane tested by this term."
                                    },
                                    "on_zero": {
                                        "x-optimade-type": "dictionary",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "object"
                                        ],
                                        "required": [
                                            "action"
                                        ],
                                        "description": "Action for points exactly on this face-level term plane.",
                                        "properties": {
                                            "action": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string"
                                                ],
                                                "enum": [
                                                    "include",
                                                    "exclude",
                                                    "evaluate_edge_rule"
                                                ],
                                                "description": "Boundary action for this equality case."
                                            },
                                            "rule_id": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string",
                                                    "null"
                                                ],
                                                "description": "Identifier of the edge rule to evaluate when `action` is `evaluate_edge_rule`."
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            }
        },
        "edge_rules": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Disjunctive-normal-form edge-boundary ownership rules.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object"
                ],
                "required": [
                    "id",
                    "dnf"
                ],
                "description": "One edge-level ownership rule.",
                "properties": {
                    "id": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "Stable identifier for this edge rule."
                    },
                    "dnf": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array"
                        ],
                        "description": "OR-list of AND-lists of edge-level terms.",
                        "items": {
                            "x-optimade-type": "list",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array"
                            ],
                            "description": "One AND-clause in the edge-level rule.",
                            "items": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object"
                                ],
                                "required": [
                                    "plane_id",
                                    "on_zero"
                                ],
                                "description": "One edge-level plane test.",
                                "properties": {
                                    "plane_id": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "description": "Identifier of the plane tested by this term."
                                    },
                                    "on_zero": {
                                        "x-optimade-type": "dictionary",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "object"
                                        ],
                                        "required": [
                                            "action"
                                        ],
                                        "description": "Action for points exactly on this edge-level term plane.",
                                        "properties": {
                                            "action": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string"
                                                ],
                                                "enum": [
                                                    "include",
                                                    "exclude",
                                                    "evaluate_vertex_rule"
                                                ],
                                                "description": "Boundary action for this equality case."
                                            },
                                            "rule_id": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string",
                                                    "null"
                                                ],
                                                "description": "Identifier of the vertex rule to evaluate when `action` is `evaluate_vertex_rule`."
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            }
        },
        "vertex_rules": {
            "x-optimade-type": "list",
            "x-optimade-unit": "inapplicable",
            "type": [
                "array",
                "null"
            ],
            "description": "Disjunctive-normal-form terminal vertex-boundary ownership rules.",
            "items": {
                "x-optimade-type": "dictionary",
                "x-optimade-unit": "inapplicable",
                "type": [
                    "object"
                ],
                "required": [
                    "id",
                    "dnf"
                ],
                "description": "One terminal vertex-level ownership rule.",
                "properties": {
                    "id": {
                        "x-optimade-type": "string",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "string"
                        ],
                        "description": "Stable identifier for this vertex rule."
                    },
                    "dnf": {
                        "x-optimade-type": "list",
                        "x-optimade-unit": "inapplicable",
                        "type": [
                            "array"
                        ],
                        "description": "OR-list of AND-lists of terminal vertex-level terms.",
                        "items": {
                            "x-optimade-type": "list",
                            "x-optimade-unit": "inapplicable",
                            "type": [
                                "array"
                            ],
                            "description": "One AND-clause in the vertex-level rule.",
                            "items": {
                                "x-optimade-type": "dictionary",
                                "x-optimade-unit": "inapplicable",
                                "type": [
                                    "object"
                                ],
                                "required": [
                                    "plane_id",
                                    "on_zero"
                                ],
                                "description": "One terminal vertex-level plane test.",
                                "properties": {
                                    "plane_id": {
                                        "x-optimade-type": "string",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "string"
                                        ],
                                        "description": "Identifier of the plane tested by this term."
                                    },
                                    "on_zero": {
                                        "x-optimade-type": "dictionary",
                                        "x-optimade-unit": "inapplicable",
                                        "type": [
                                            "object"
                                        ],
                                        "required": [
                                            "action"
                                        ],
                                        "description": "Terminal action for points exactly on this vertex-level term plane.",
                                        "properties": {
                                            "action": {
                                                "x-optimade-type": "string",
                                                "x-optimade-unit": "inapplicable",
                                                "type": [
                                                    "string"
                                                ],
                                                "enum": [
                                                    "include",
                                                    "exclude"
                                                ],
                                                "description": "Terminal boundary action for this equality case."
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    },
    "examples": [
        {
            "planes": [
                {
                    "id": "p0",
                    "normal": [
                        "1",
                        "0",
                        "0"
                    ],
                    "const": "0"
                },
                {
                    "id": "p1",
                    "normal": [
                        "-1",
                        "0",
                        "0"
                    ],
                    "const": "1"
                }
            ],
            "volume_cuts": [
                {
                    "id": "v0",
                    "plane_id": "p0",
                    "when_positive": "include",
                    "when_negative": "exclude",
                    "when_zero": {
                        "action": "include"
                    }
                },
                {
                    "id": "v1",
                    "plane_id": "p1",
                    "when_positive": "include",
                    "when_negative": "exclude",
                    "when_zero": {
                        "action": "exclude"
                    }
                }
            ],
            "face_rules": [],
            "edge_rules": [],
            "vertex_rules": []
        }
    ]
}
```