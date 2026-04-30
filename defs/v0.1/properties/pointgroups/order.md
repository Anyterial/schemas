# Order (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order`](https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order.md)**  
**Definition name:** `order`

**Property name:** Order  
**Description:** Order of the point group, i.e. the number of operations in the finite point group.  
**Type:** integer  



**Examples:**

- `1`
- `2`

**Formats:** [[JSON](order.json)] [[MD](order.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/pointgroups/order",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Order",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "integer",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "order",
        "label": "order_pointgroups"
    },
    "type": [
        "integer",
        "null"
    ],
    "description": "Order of the point group, i.e. the number of operations in the finite point group.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        1,
        2
    ]
}
```