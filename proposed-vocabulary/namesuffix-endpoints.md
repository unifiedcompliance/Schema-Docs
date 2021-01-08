# NameSuffix Endpoints

> This document explains the methods you may use to work with the NameSuffix endpoints in the Federated Authority Document database.

## Getting NameSuffix

### Quick-start Knowledge

* The full JSON-LD NameSuffix object is defined at [https://grcschema.org/NameSuffix](https://grcschema.org/NameSuffix).
* Getting a list of NameSuffix objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/NameSuffix](https://grcschema.p.rapidapi.com/NameSuffix) endpoint using a REST **GET**. Optional parameters may be provided to filter and paginate the result.

### NameSuffix List GET

* Getting a list of NameSuffix object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/NameSuffix](https://grcschema.p.rapidapi.com/NameSuffix) endpoint using a REST **GET** with no optional parameters.
* Provides a list of all NameSuffix objects.

```javascript
{
  "@context": "http://grcschema.org/",
  "@type": "NameSuffix",
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
  "suffix": "Admiral"
}
```

### NameSuffix List GET \(filtered\)

* Getting a filtered list of NameSuffix objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/NameSuffix/](https://grcschema.p.rapidapi.com/NameSuffix/) endpoint using a REST **GET** with url parameters.
* These are the parameters you can optionally supply to the filter. These fields work as a logical AND.

| Field | Description |
| :--- | :--- |
| abbreviation | Searches by abbreviation. |
| suffix | Searches by suffix. |
| sort\_dir | 0 = descending, 1 = ascending |
| search | Searches across all searchable fields. |
| limit | Combined with offset, provides pagination by limiting results. |
| offset | Combined with limit, provides pagination by shifting the first record. |

### NameSuffix GET \(by ID\)

* Getting a single NameSuffix object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/NameSuffix/:id](https://grcschema.p.rapidapi.com/NameSuffix/:id) endpoint using a REST **GET**.

## POST NameSuffix Endpoint

### Quick-start Knowledge

* Adding a new NameSuffix object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/NameSuffix](https://grcschema.p.rapidapi.com/NameSuffix) endpoint as a REST **POST**.
* The full JSON-LD object is defined at [https://grcschema.org/NameSuffix](https://grcschema.org/NameSuffix), and the endpoint will accept the the entire object for processing. This includes array items \(\@set\).
* When posting an object, all ID fields are ignored and can be set to **null**. Any parameter \(key\) or sub-object not provided is considered **skipped** and the value will come back **null**.
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing is maintained in some systems. \(See the `local_reference_id` section for more detail.\)

### Minimum Required Object

* Only suffix and abbreviation are required to create a NameSuffix object, however you may supply any other data that complies with the full schema.

```javascript
{
  "@context": "http://grcschema.org/",
  "@type": "NameSuffix",
  "abbreviation": "String",
  "suffix": "String"
}
```

### Response Object

* The response object that is returned is the FULL NameSuffix JSON object as defined by grcschema.

## PATCH NameSuffix Endpoint

### Quick-start Knowledge

* Updating a NameSuffix object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/NameSuffix/:id](https://grcschema.p.rapidapi.com/NameSuffix/:id) endpoint as a REST **PATCH**.
* The full JSON-LD object is defined at [https://grcschema.org/NameSuffix](https://grcschema.org/NameSuffix), and the endpoint will accept an **existing** NameSuffix object \(with applicable changes\) for processing.
* Some properties cannot be changed and are ignored.  \(e.g. id\)
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing required by some systems. \(See the `local_reference_id` section for more detail.\)

### Performing a Property \(Key\) Value Update

* Change the properties of the object pulled from **GET /NameSuffix/:id** by sending an **application/json PATCH** to the [https://grcschema.org/NameSuffix/:id](https://grcschema.org/NameSuffix/:id) endpoint and the full NameSuffix object will be returned with the requested changes.

## How to Use `local_reference_id`

### Quick-start Knowledge

* For `POST` and `PATCH` operations, you may send an optional `local_reference_id` for the core object and any sub-objects in unordered lists \(\@set arrays\).  This `local_reference_id` will be returned \(like an echo\) for that object.
* It is recommended you use a Type 4 UUID which is unique for that object in your system and tie the federated ID to your record for later use in querying the federated system for that object.

### POST Operation Example

> For the core object, you may place a `local_reference_id` at the object root level, and it will be returned in the response.

**SEND**

```javascript
...
{
  "@context": "http://grcschema.org/",
  "@type": "NameSuffix",
  "abbreviation": "Adm",
  "local_reference_id": "6d406061-1ef9-40f7-b644-f58ae98905f0",
  "suffix": "Admiral"
}
```

**RESPONSE**

```javascript
{
  "@context":"http://grcschema.org/",
  "@type": "NameSuffix",
  "abbreviation": "Adm",
  "id": 2,
  "suffix": "Admiral",
  "local_reference_id": "6d406061-1ef9-40f7-b644-f58ae98905f0"
}
```

### PATCH Operation Example

> For the core object, you may place a `local_reference_id` at the object root level, and it will be returned in the response. Do not add `local_reference_id` to the container objects like CoreMetaData.

**SEND & RESPONSE**

```javascript
{
  "@context":"http://grcschema.org/",
  "@type": "NameSuffix",
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
  "suffix": "Admiral",
  "local_reference_id": "6d406061-1ef9-40f7-b644-f58ae98905f0"
}
```

