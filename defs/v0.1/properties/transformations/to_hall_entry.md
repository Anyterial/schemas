# To Hall entry (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/transformations/to_hall_entry`](https://schemas.anyterial.se/defs/v0.1/properties/transformations/to_hall_entry.md)**  
**Definition name:** `to_hall_entry`

**Property name:** To Hall entry  
**Description:** Target Hall-entry key to which a setting transform maps the current Hall setting.  
**Type:** string  

The value is a normalized Hall-entry key following the same convention as `/defs/v0.1/properties/spacegroups/hall_entry`, i.e., derived from the Hall symbol by using lowercase letters and underscores in place of spaces.
The corresponding display Hall symbol can be recovered by looking up the key in the spacegroups dataset.

**Examples:**

- `"p_1"`
- `"-p_1"`

**Formats:** [[JSON](to_hall_entry.json)] [[MD](to_hall_entry.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/transformations/to_hall_entry",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "To Hall entry",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "to_hall_entry",
        "label": "to_hall_entry_transformations"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "Target Hall-entry key to which a setting transform maps the current Hall setting.\n\nThe value is a normalized Hall-entry key following the same convention as `/defs/v0.1/properties/spacegroups/hall_entry`, i.e., derived from the Hall symbol by using lowercase letters and underscores in place of spaces.\nThe corresponding display Hall symbol can be recovered by looking up the key in the spacegroups dataset.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "p_1",
        "-p_1"
    ]
}
```