# Anyterial altermagnet screening result entry type (entrytype)

This page documents an [OPTIMADE](https://www.optimade.org/) [Entrytype Definition](https://schemas.optimade.org/#definitions). See [https://schemas.optimade.org/](https://schemas.optimade.org/) for more information.

**ID: [`https://schemas.anyterial.se/defs/v0.1/entrytypes/altermagnet_screening_results`](https://schemas.anyterial.se/defs/v0.1/entrytypes/altermagnet_screening_results.md)**  
**Definition name:** `altermagnet_screening_results`

**Entrytype name:** Anyterial altermagnet screening result entry type  
**Description:** An altermagnet screening result is the Anyterial altermagnets database's provider-specific main entity: one screened candidate material together with the high-throughput screening science determined for it (classification, spin-splitting metrics, electronic type, crustal abundance, magnetic phase and wave-class assignments, and the linked MAGNDATA symmetry variants), its generated band-structure/crystal-structure/Brillouin-zone figures, and the total energy of the workflow run that produced it.
The screened crystal structure itself is a separate standard OPTIMADE structures entry, linked from this entry through a structures relationship; the reference DOIs are linked through a references relationship.
The science, figure, and energy properties served on this entry type are declared through property definitions and are not enumerated here.  

**Formats:** [[JSON](altermagnet_screening_results.json)] [[MD](altermagnet_screening_results.md)]

This entrytype defines the following properties:

* **[ID](https://schemas.optimade.org/defs/v1.2/properties/core/id.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/id`](https://schemas.optimade.org/defs/v1.2/properties/core/id.md)  
  A unique string referencing a specific entry in the database.

    **Requirements/Conventions:**  

    - **Support:** MUST be supported by all implementations, MUST NOT be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MUST always be included in the response.
    - Taken together, the ID and entry type MUST uniquely identify the entry.
    - Reasonably short IDs are encouraged and SHOULD NOT be longer than 255 characters.
    - IDs MAY change over time.


* **[type](https://schemas.optimade.org/defs/v1.2/properties/core/type.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/type`](https://schemas.optimade.org/defs/v1.2/properties/core/type.md)  
  The name of the type of an entry.

    **Requirements/Conventions:**  

    - **Support:** MUST be supported by all implementations, MUST NOT be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MUST always be included in the response.
    - MUST be an existing entry type.
    - The entry of type <type> and ID <id> MUST be returned in response to a request for /<type>/<id> under the versioned or unversioned base URL serving the API.


* **[immutable ID (immutable_id)](https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id`](https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id.md)  
  The entry's immutable ID (e.g., a UUID).

    **Requirements/Conventions:**  

    - **Support:** OPTIONAL support in implementations, i.e., MAY be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MAY be included by default in the response.
    - This is important for databases having preferred IDs that point to "the latest version" of a record, but still offer access to older variants.
    - This ID maps to the version-specific record, in case it changes in the future.


* **[last modified (last_modified)](https://schemas.optimade.org/defs/v1.2/properties/core/last_modified.md)** (property) - [`https://schemas.optimade.org/defs/v1.2/properties/core/last_modified`](https://schemas.optimade.org/defs/v1.2/properties/core/last_modified.md)  
  Date and time representing when the entry was last modified.

    **Requirements/Conventions:**  

    - **Support:** SHOULD be supported by all implementations, i.e., SHOULD NOT be `null`.
    - **Query:** MUST be a queryable property with support for all mandatory filter features.
    - **Response:** MUST be included by default in the response.


**JSON definition:**

``` json
{
    "$id": "https://schemas.anyterial.se/defs/v0.1/entrytypes/altermagnet_screening_results",
    "$schema": "https://schemas.optimade.org/meta/v1.2/optimade/entrytype_definition.json",
    "type": "object",
    "title": "Anyterial altermagnet screening result entry type",
    "x-optimade-definition": {
        "kind": "entrytype",
        "format": "1.3",
        "version": "0.1.0",
        "name": "altermagnet_screening_results",
        "label": "altermagnet_screening_results_entrytype_altermagnets"
    },
    "description": "An altermagnet screening result is the Anyterial altermagnets database's provider-specific main entity: one screened candidate material together with the high-throughput screening science determined for it (classification, spin-splitting metrics, electronic type, crustal abundance, magnetic phase and wave-class assignments, and the linked MAGNDATA symmetry variants), its generated band-structure/crystal-structure/Brillouin-zone figures, and the total energy of the workflow run that produced it.\nThe screened crystal structure itself is a separate standard OPTIMADE structures entry, linked from this entry through a structures relationship; the reference DOIs are linked through a references relationship.\nThe science, figure, and energy properties served on this entry type are declared through property definitions and are not enumerated here.",
    "properties": {
        "id": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/id",
            "x-optimade-requirements": {
                "support": "must",
                "sortable": true,
                "query-support": "all mandatory",
                "response-level": "always"
            },
            "title": "ID",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "label": "id_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "id"
            },
            "type": [
                "string"
            ],
            "description": "A unique string referencing a specific entry in the database.\n\n**Requirements/Conventions:**\n\n- Taken together, the ID and entry type MUST uniquely identify the entry.\n- Reasonably short IDs are encouraged and SHOULD NOT be longer than 255 characters.\n- IDs MAY change over time.",
            "examples": [
                "db/1234567",
                "cod/2000000",
                "cod/2000000@1234567",
                "nomad/L1234567890",
                "42"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "type": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/type",
            "x-optimade-requirements": {
                "support": "must",
                "sortable": true,
                "query-support": "all mandatory",
                "response-level": "always"
            },
            "title": "type",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "label": "type_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "type"
            },
            "type": [
                "string"
            ],
            "description": "The name of the type of an entry.\n\n**Requirements/Conventions:**\n\n- MUST be an existing entry type.\n- The entry of type <type> and ID <id> MUST be returned in response to a request for /<type>/<id> under the versioned or unversioned base URL serving the API.",
            "examples": [
                "structures"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "immutable_id": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/immutable_id",
            "x-optimade-requirements": {
                "support": "may",
                "sortable": false,
                "query-support": "all mandatory",
                "response-level": "may"
            },
            "title": "immutable ID",
            "x-optimade-type": "string",
            "x-optimade-definition": {
                "label": "immutable_id_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "immutable_id"
            },
            "type": [
                "string",
                "null"
            ],
            "description": "The entry's immutable ID (e.g., a UUID).\n\n**Requirements/Conventions:**\n\n- This is important for databases having preferred IDs that point to \"the latest version\" of a record, but still offer access to older variants.\n- This ID maps to the version-specific record, in case it changes in the future.",
            "examples": [
                "8bd3e750-b477-41a0-9b11-3a799f21b44f",
                "fjeiwoj,54;@=%<>#32"
            ],
            "x-optimade-unit": "inapplicable"
        },
        "last_modified": {
            "$id": "https://schemas.optimade.org/defs/v1.2/properties/core/last_modified",
            "x-optimade-requirements": {
                "support": "should",
                "sortable": false,
                "query-support": "all mandatory",
                "response-level": "must"
            },
            "title": "last modified",
            "x-optimade-type": "timestamp",
            "x-optimade-definition": {
                "label": "last_modified_core",
                "kind": "property",
                "version": "1.2.0",
                "format": "1.2",
                "name": "last_modified"
            },
            "type": [
                "string",
                "null"
            ],
            "format": "date-time",
            "description": "Date and time representing when the entry was last modified.",
            "examples": [
                "2007-04-05T14:30:20Z"
            ],
            "x-optimade-unit": "inapplicable"
        }
    }
}
```