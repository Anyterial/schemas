# Wyckoff positions (property)

This page documents an [OPTIMADE](https://www.optimade.org/) [Property Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff`](https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff.md)**  
**Definition name:** `wyckoff`

**Property name:** Wyckoff positions  
**Description:** Wyckoff-position table for a specific space-group setting.
Each key is a Wyckoff letter and each value describes one Wyckoff position.
Values follow `/properties/symmetry/wyckoff_position`.  
**Type:** dictionary  

**Requirements/Conventions**:

- Dynamic keys MUST be Wyckoff letters for the setting.
- Each value MUST be a dictionary describing the corresponding Wyckoff position.
- `orbit_affine` and `orbit_xyz` contain the full orbit.
- `orbit_mod_centering_affine` and `orbit_mod_centering_xyz` contain one representative modulo centering translations.

**Examples:**

- `{"e": {"multiplicity": 2, "sitesym": "1", "hasfreedom": [true, true, true], "first_orbit": "x,y,z", "orbit_xyz": ["x", "y", "z", "-x", "y", "-z"], "orbit_mod_centering_xyz": ["x", "y", "z", "-x", "y", "-z"]}}`

**Formats:** [[JSON](wyckoff.json)] [[MD](wyckoff.md)]

**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/properties/spacegroups/wyckoff",
    "$schema": "https://schemas.optimade.org/meta/v1.3/optimade/property_definition.json",
    "title": "Wyckoff positions",
    "$comment": "Anyterial Wyckoff-position map property using the common wyckoff-position record definition.",
    "x-optimade-type": "dictionary",
    "x-optimade-definition": {
        "kind": "property",
        "version": "0.1.0",
        "format": "1.3",
        "name": "wyckoff",
        "label": "wyckoff_spacegroups"
    },
    "x-optimade-unit": "inapplicable",
    "type": [
        "object",
        "null"
    ],
    "description": "Wyckoff-position table for a specific space-group setting.\nEach key is a Wyckoff letter and each value describes one Wyckoff position.\nValues follow `/properties/symmetry/wyckoff_position`.\n\n**Requirements/Conventions**:\n\n- Dynamic keys MUST be Wyckoff letters for the setting.\n- Each value MUST be a dictionary describing the corresponding Wyckoff position.\n- `orbit_affine` and `orbit_xyz` contain the full orbit.\n- `orbit_mod_centering_affine` and `orbit_mod_centering_xyz` contain one representative modulo centering translations.",
    "properties": {},
    "examples": [
        {
            "e": {
                "multiplicity": 2,
                "sitesym": "1",
                "hasfreedom": [
                    true,
                    true,
                    true
                ],
                "first_orbit": "x,y,z",
                "orbit_xyz": [
                    "x",
                    "y",
                    "z",
                    "-x",
                    "y",
                    "-z"
                ],
                "orbit_mod_centering_xyz": [
                    "x",
                    "y",
                    "z",
                    "-x",
                    "y",
                    "-z"
                ]
            }
        }
    ]
}
```