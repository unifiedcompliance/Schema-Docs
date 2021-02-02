# NamePrefix Endpoints

> This document explains the methods you may use to work with the NamePrefix endpoints in the Federated Authority Document database.

## Getting NamePrefix

### Quick-start Knowledge

* The full JSON-LD NamePrefix object is defined at [https://grcschema.org/NamePrefix](https://grcschema.org/NamePrefix).
* Getting a list of NamePrefix objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/NamePrefix](https://grcschema.p.rapidapi.com/NamePrefix) endpoint using a REST **GET**. Optional parameters may be provided to filter and paginate the result.

### NamePrefix List GET

* Getting a list of NamePrefix object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/NamePrefix](https://grcschema.p.rapidapi.com/NamePrefix) endpoint using a REST **GET** with no optional parameters.
* Provides a list of all NamePrefix objects.
* Pagination is provided for the list where `count` is the total quantity of objects in the data-set, `limit` is how many objects are returned in the current list, and `offset` is the first object in the set from that offset point. This is configurable in the request, but the default is a limit of 50 objects starting from offset 0.

> In the below example, with a limit of 2, page 1 starts from offset 0 with two values \(`limit`\). Page 2 starts from `offset`= 2. Page 3 from `offset`= 4, etc. There would be 5 pages to display the data - two objects at a time. This is illustrative only, and the actual local pages will depend on your limit and count.

```javascript
{
  "Pagination": {
    "@context": "http://grcschema.org/",
    "@type": "Pagination",
    "count": 10,
    "limit": 2,
    "offset": 0
  },
  "@set": [
    {
      "@context": "http://grcschema.org/",
      "@type": "NamePrefix",
      "CoreMetaData": {
        "@type": "CoreMetaData",
        "date_created": "2021-01-08T20:51:36.000Z",
        "date_modified": "0000-00-00 00:00:00",
        "created_by": null,
        "modified_by": null,
        "live_status": 0,
        "checksum": null,
        "validated": 1
      },
      "abbreviation": "Abbot",
      "id": 1,
      "prefix": "Abbot"
    },
    {
      "@context": "http://grcschema.org/",
      "@type": "NamePrefix",
      "CoreMetaData": {
        "@type": "CoreMetaData",
        "date_created": "2021-01-08T20:51:36.000Z",
        "date_modified": "0000-00-00 00:00:00",
        "created_by": null,
        "modified_by": null,
        "live_status": 0,
        "checksum": null,
        "validated": 1
      },
      "abbreviation": "Adm.",
      "id": 2,
      "prefix": "Admiral"
    }
  ]
}
```

### NamePrefix List GET \(filtered\)

* Getting a filtered list of NamePrefix objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/NamePrefix/](https://grcschema.p.rapidapi.com/NamePrefix/) endpoint using a REST **GET** with url parameters.
* These are the parameters you can optionally supply to the filter. These fields work as a logical AND.

| Field | Description |
| :--- | :--- |
| abbreviation | Searches by abbreviation. |
| prefix | Searches by prefix. |
| sort\_dir | 0 = descending, 1 = ascending |
| search | Searches across all searchable fields. |
| limit | Combined with offset, provides pagination by limiting results. |
| offset | Combined with limit, provides pagination by shifting the first record. |

### NamePrefix GET \(by ID\)

* Getting a single NamePrefix object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/NamePrefix/:id](https://grcschema.p.rapidapi.com/NamePrefix/:id) endpoint using a REST **GET**.

## POST NamePrefix Endpoint

### Quick-start Knowledge

* Adding a new NamePrefix object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/NamePrefix](https://grcschema.p.rapidapi.com/NamePrefix) endpoint as a REST **POST**.
* The full JSON-LD object is defined at [https://grcschema.org/NamePrefix](https://grcschema.org/NamePrefix), and the endpoint will accept the the entire object for processing. This includes array items \(@set\).
* When posting an object, all ID fields are ignored and can be set to **null**. Any parameter \(key\) or sub-object not provided is considered **skipped** and the value will come back **null**.
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing is maintained in some systems. \(See the `local_reference_id` section for more detail.\)
* All new objects require a person id performing the update which is accomplished via the `x-requester-person` header value.

### Created\_by Audit Record

* When you send a POST to create an object, you must supply an `x-requester-person` in the header as the person id making the request. This sets the created\_by field in the audit record to the person who added the object.

### Minimum Required Object

* Only prefix and abbreviation are required to create a NamePrefix object, however you may supply any other data that complies with the full schema.

```javascript
{
  "@context": "http://grcschema.org/",
  "@type": "NamePrefix",
  "abbreviation": "String",
  "prefix": "String"
}
```

### Response Object

* The response object that is returned is the FULL NamePrefix JSON object as defined by grcschema.

## PATCH NamePrefix Endpoint

### Quick-start Knowledge

* Updating a NamePrefix object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/NamePrefix/:id](https://grcschema.p.rapidapi.com/NamePrefix/:id) endpoint as a REST **PATCH**.
* The full JSON-LD object is defined at [https://grcschema.org/NamePrefix](https://grcschema.org/NamePrefix), and the endpoint will accept an **existing** NamePrefix object \(with applicable changes\) for processing.
* Some properties cannot be changed and are ignored.  \(e.g. id\)
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing required by some systems. \(See the `local_reference_id` section for more detail.\)

### Modified\_by Audit Record

* When you send a PATCH to modify an object, you must supply an `x-requester-person` in the header as the person id making the request. This sets the modified\_by field in the audit record to the person who modified the object.

### Performing a Property \(Key\) Value Update

* Change the properties of the object pulled from **GET /NamePrefix/:id** by sending an **application/json PATCH** to the [https://grcschema.org/NamePrefix/:id](https://grcschema.org/NamePrefix/:id) endpoint and the full NamePrefix object will be returned with the requested changes.

## How to Use `local_reference_id`

### Quick-start Knowledge

* For `POST` and `PATCH` operations, you may send an optional `local_reference_id` for the core object and any sub-objects in unordered lists \(@set arrays\).  This `local_reference_id` will be returned \(like an echo\) for that object.
* It is recommended you use a Type 4 UUID which is unique for that object in your system and tie the federated ID to your record for later use in querying the federated system for that object.

### POST Operation Example

> For the core object, you may place a `local_reference_id` at the object root level, and it will be returned in the response.

**SEND**

```javascript
...
{
  "@context": "http://grcschema.org/",
  "@type": "NamePrefix",
  "abbreviation": "Adm",
  "local_reference_id": "6d406061-1ef9-40f7-b644-f58ae98905f0",
  "prefix": "Admiral"
}
```

**RESPONSE**

```javascript
{
  "@context":"http://grcschema.org/",
  "@type": "NamePrefix",
  "abbreviation": "Adm",
  "id": 2,
  "prefix": "Admiral",
  "local_reference_id": "6d406061-1ef9-40f7-b644-f58ae98905f0"
}
```

### PATCH Operation Example

> For the core object, you may place a `local_reference_id` at the object root level, and it will be returned in the response. Do not add `local_reference_id` to the container objects like CoreMetaData.

**SEND & RESPONSE**

```javascript
{
  "@context":"http://grcschema.org/",
  "@type": "NamePrefix",
  "CoreMetaData": {
      "@type": "CoreMetaData",
      "date_created": "Date",
      "date_modified": "Date",
      "created_by": "Integer",
      "modified_by": "Integer",
      "live_status": "Boolean",
      "checksum": "Integer",
      "validated": "Boolean"
  },
  "abbreviation": "Adm.",
  "id": 2,
  "prefix": "Admiral",
  "local_reference_id": "6d406061-1ef9-40f7-b644-f58ae98905f0"
}
```

