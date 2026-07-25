# Length precision (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/core/length_precision`](https://schemas.anyterial.se/defs/v0.1/properties/core/length_precision.md)**  
**Definition name:** `length_precision`

**Property name:** Length precision  
**Description:** The absolute precision of a stated length, in ångström.  
**Type:** float  

This describes how precisely a length was *stated* by the source it came from, rather
than the precision of the number as stored. A cell edge written `5.6402` claims a
precision of about `0.0001` ångström; one written `5.6402(3)` claims `0.0003`, since an
explicitly stated uncertainty overrides what the digits alone would imply.

**Requirements/Conventions**:

- The value is an **absolute** bound on the deviation from the intended value, in the same
  units as the length it describes, and is neither a relative precision nor a count of
  significant figures.
- Where a set of lengths is described by a single value, it SHOULD be the **coarsest**
  precision among them.
- Where a source states both a number of digits and an explicit standard uncertainty, the
  value SHOULD be the larger of the two, that being the weaker and therefore the safer
  claim.
- Precisions of quantities in other units, such as the angles of a unit cell, MUST NOT be
  combined into this value; they are not lengths and combining them would produce a
  quantity in no units at all.
- The value MUST be strictly positive. A value of zero would assert exactness, which is a
  different claim; `null` MUST be used where the precision is unknown.

**Examples:**

- `0.0001`
- `0.0003`

**Formats:** [[JSON](length_precision.json)] [[MD](length_precision.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/core/length_precision",
    "$schema": "https://schemas.optimade.org/meta/v1.2/optimade/property_definition.json",
    "title": "Length precision",
    "x-optimade-type": "float",
    "x-optimade-definition": {
        "label": "length_precision_core",
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "length_precision"
    },
    "type": [
        "number",
        "null"
    ],
    "description": "The absolute precision of a stated length, in \u00e5ngstr\u00f6m.\n\nThis describes how precisely a length was *stated* by the source it came from, rather\nthan the precision of the number as stored. A cell edge written `5.6402` claims a\nprecision of about `0.0001` \u00e5ngstr\u00f6m; one written `5.6402(3)` claims `0.0003`, since an\nexplicitly stated uncertainty overrides what the digits alone would imply.\n\n**Requirements/Conventions**:\n\n- The value is an **absolute** bound on the deviation from the intended value, in the same\n  units as the length it describes, and is neither a relative precision nor a count of\n  significant figures.\n- Where a set of lengths is described by a single value, it SHOULD be the **coarsest**\n  precision among them.\n- Where a source states both a number of digits and an explicit standard uncertainty, the\n  value SHOULD be the larger of the two, that being the weaker and therefore the safer\n  claim.\n- Precisions of quantities in other units, such as the angles of a unit cell, MUST NOT be\n  combined into this value; they are not lengths and combining them would produce a\n  quantity in no units at all.\n- The value MUST be strictly positive. A value of zero would assert exactness, which is a\n  different claim; `null` MUST be used where the precision is unknown.",
    "examples": [
        0.0001,
        0.0003
    ],
    "x-optimade-unit": "angstrom"
}
```