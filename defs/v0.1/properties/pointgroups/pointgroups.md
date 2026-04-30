# Point groups (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/pointgroups`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/pointgroups.md)**  
**Definition name:** `pointgroups`

**Property name:** Point groups  
**Description:** Ordered table of crystallographic point-group records.
Each item contains point-group classification, finite point-group operations, conjugacy classes, and real and complex character tables generated from cctbx and spgrep.  
**Type:** list  

**Requirements/Conventions**:

- The table covers the 32 crystallographic point groups.
- The point-group records are independent of any particular space-group setting.
- Character-table rows use Mulliken labels and include formatted label variants when available.

**Examples:**

- `[{"hm_symbol": "2/m", "order": 4}]`

**Formats:** [[JSON](pointgroups.json)] [[MD](pointgroups.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/pointgroups",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Point groups",
    "$comment": "Anyterial top-level ordered point-group table.",
    "x-optimade-type": "list",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "pointgroups",
        "label": "pointgroups_pointgroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "array",
        "null"
    ],
    "description": "Ordered table of crystallographic point-group records.\nEach item contains point-group classification, finite point-group operations, conjugacy classes, and real and complex character tables generated from cctbx and spgrep.\n\n**Requirements/Conventions**:\n\n- The table covers the 32 crystallographic point groups.\n- The point-group records are independent of any particular space-group setting.\n- Character-table rows use Mulliken labels and include formatted label variants when available.",
    "items": {
        "x-optimade-type": "dictionary",
        "x-optimade-unit": "inapplicable",
        "type": [
            "object",
            "null"
        ],
        "description": "One crystallographic point-group record.",
        "properties": {}
    },
    "examples": [
        [
            {
                "hm_symbol": "2/m",
                "order": 4
            }
        ]
    ]
}
```