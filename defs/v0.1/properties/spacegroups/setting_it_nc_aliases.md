# International Tables setting-code aliases (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases.md)**  
**Definition name:** `setting_it_nc_aliases`

**Property name:** International Tables setting-code aliases  
**Description:** A list of International Tables `n:c` setting identifiers that are alternatives to the one designated as the main one.  
**Type:** list  

This field is used only when the source tables expose more than one conventional label for the same setting.

**Examples:**

- `["68:1ba-c"]`
- `["68:1-cba"]`

**Formats:** [[JSON](setting_it_nc_aliases.json)] [[MD](setting_it_nc_aliases.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/setting_it_nc_aliases",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "International Tables setting-code aliases",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "setting_it_nc_aliases",
        "label": "setting_it_nc_aliases_spacegroups"
    },
    "type": [
        "array",
        "null"
    ],
    "description": "A list of International Tables `n:c` setting identifiers that are alternatives to the one designated as the main one.\n\nThis field is used only when the source tables expose more than one conventional label for the same setting.",
    "x-optimade-unit": "inapplicable",
    "items": {
        "x-optimade-type": "string",
        "type": [
            "string",
            "null"
        ],
        "description": "One alternate symbol string.",
        "x-optimade-unit": "inapplicable"
    },
    "examples": [
        [
            "68:1ba-c"
        ],
        [
            "68:1-cba"
        ]
    ]
}
```