# Relation details (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/relation_details`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/relation_details.md)**  
**Definition name:** `relation_details`

**Property name:** Relation details  
**Description:** Detailed metadata for generated maximal non-isomorphic subgroup relations.
The map is keyed by supergroup IT number and each value is a list of subgroup-relation records.  
**Type:** dictionary  

**Requirements/Conventions**:

- Dynamic keys MUST be International Tables space-group numbers represented as strings.
- Each value MUST be a list of dictionaries.
- Each dictionary MUST identify the subgroup IT number, subgroup index, subgroup type, and optional klassengleiche subtype.

**Examples:**

- `{"5": [{"it_number": 1, "index": 2, "subgroup_type": "t"}, {"it_number": 3, "index": 2, "subgroup_type": "k", "k_subtype": "loss_of_centering_translation"}]}`

**Formats:** [[JSON](relation_details.json)] [[MD](relation_details.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/relation_details",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Relation details",
    "$comment": "Anyterial property definition for detailed maximal-subgroup relation metadata.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "relation_details",
        "label": "relation_details_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Detailed metadata for generated maximal non-isomorphic subgroup relations.\nThe map is keyed by supergroup IT number and each value is a list of subgroup-relation records.\n\n**Requirements/Conventions**:\n\n- Dynamic keys MUST be International Tables space-group numbers represented as strings.\n- Each value MUST be a list of dictionaries.\n- Each dictionary MUST identify the subgroup IT number, subgroup index, subgroup type, and optional klassengleiche subtype.",
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