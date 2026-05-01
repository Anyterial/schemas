# Maximal subgroup relations (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/maximal_subgroup_relations`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/maximal_subgroup_relations.md)**  
**Definition name:** `maximal_subgroup_relations`

**Property name:** Maximal subgroup relations  
**Description:** Maximal non-isomorphic subgroup relations for International Tables space-group types.
The dictionary is keyed by supergroup IT number and each value is a list of subgroup-relation records.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary whose dynamic keys are International Tables space-group numbers represented as strings.
- Each value MUST be a list of dictionaries.
- Each dictionary MUST describe one generated maximal subgroup relation and include the subgroup IT number, subgroup index, subgroup type, and optional klassengleiche subtype.

**Examples:**

- `{"5": [{"it_number": 1, "index": 2, "subgroup_type": "t"}, {"it_number": 3, "index": 2, "subgroup_type": "k", "k_subtype": "loss_of_centering_translation"}]}`

**Formats:** [[JSON](maximal_subgroup_relations.json)] [[MD](maximal_subgroup_relations.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/maximal_subgroup_relations",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Maximal subgroup relations",
    "$comment": "Anyterial property definition for maximal non-isomorphic subgroup relation metadata.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "maximal_subgroup_relations",
        "label": "maximal_subgroup_relations_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Maximal non-isomorphic subgroup relations for International Tables space-group types.\nThe dictionary is keyed by supergroup IT number and each value is a list of subgroup-relation records.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary whose dynamic keys are International Tables space-group numbers represented as strings.\n- Each value MUST be a list of dictionaries.\n- Each dictionary MUST describe one generated maximal subgroup relation and include the subgroup IT number, subgroup index, subgroup type, and optional klassengleiche subtype.",
    "properties": {},
    "examples": [
        {
            "5": [
                {
                    "it_number": 1,
                    "index": 2,
                    "subgroup_type": "t"
                },
                {
                    "it_number": 3,
                    "index": 2,
                    "subgroup_type": "k",
                    "k_subtype": "loss_of_centering_translation"
                }
            ]
        }
    ]
}
```