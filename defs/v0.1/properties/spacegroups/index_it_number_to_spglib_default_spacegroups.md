# IT number to spglib default spacegroups index (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_it_number_to_spglib_default_spacegroups`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_it_number_to_spglib_default_spacegroups.md)**  
**Definition name:** `index_it_number_to_spglib_default_spacegroups`

**Property name:** IT number to spglib default spacegroups index  
**Description:** IT-number keyed lookup from the default spglib Hall setting to the corresponding row index in the top-level `spacegroups` list.  
**Type:** dictionary  

**Requirements/Conventions**:

- It MUST be a dictionary.
- Keys MUST be International Tables space-group numbers encoded as strings.
- Values MUST be list indices into the top-level `spacegroups` array of `symmetry_basics.json.gz`.

**Examples:**

- `{"1": 0}`
- `{"2": 1}`

**Formats:** [[JSON](index_it_number_to_spglib_default_spacegroups.json)] [[MD](index_it_number_to_spglib_default_spacegroups.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/index_it_number_to_spglib_default_spacegroups",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "IT number to spglib default spacegroups index",
    "$comment": "Indexed lookup into symmetry_basics spacegroups for the default spglib setting of each IT number.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "index_it_number_to_spglib_default_spacegroups",
        "label": "index_it_number_to_spglib_default_spacegroups_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "IT-number keyed lookup from the default spglib Hall setting to the corresponding row index in the top-level `spacegroups` list.\n\n**Requirements/Conventions**:\n\n- It MUST be a dictionary.\n- Keys MUST be International Tables space-group numbers encoded as strings.\n- Values MUST be list indices into the top-level `spacegroups` array of `symmetry_basics.json.gz`.",
    "properties": {},
    "examples": [
        {
            "1": 0
        },
        {
            "2": 1
        }
    ]
}
```