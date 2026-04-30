# Klassengleiche subgroup subtype (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/k_subtype`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/k_subtype.md)**  
**Definition name:** `k_subtype`

**Property name:** Klassengleiche subgroup subtype  
**Description:** Subtype of a klassengleiche (`k`) subgroup relation. Values distinguish loss of centering translations from enlarged-unit-cell subgroups; the value is null for non-`k` relations.  
**Type:** string  



**Examples:**

- `"enlarged_unit_cell"`
- `"loss_of_centering_translation"`

**Formats:** [[JSON](k_subtype.json)] [[MD](k_subtype.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/k_subtype",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Klassengleiche subgroup subtype",
    "$comment": "Generated from data-generators JSON-LD fields without external definition URLs.",
    "x-optimade-type": "string",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "k_subtype",
        "label": "k_subtype_spacegroups"
    },
    "type": [
        "string",
        "null"
    ],
    "description": "Subtype of a klassengleiche (`k`) subgroup relation. Values distinguish loss of centering translations from enlarged-unit-cell subgroups; the value is null for non-`k` relations.",
    "x-optimade-unit": "inapplicable",
    "examples": [
        "enlarged_unit_cell",
        "loss_of_centering_translation"
    ]
}
```