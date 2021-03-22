# Organization Endpoints

> This document explains the methods you may use to work with the Organization endpoints in the Federated Authority Document database.

## GET Organization Endpoints

### Quick-start Knowledge

* The full JSON-LD Organization object is defined at [https://grcschema.org/Organization](https://grcschema.org/Organization).
* Getting a list of Organization object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Organization](https://grcschema.p.rapidapi.com/Organization) endpoint using a REST **GET**. Optional parameters may be provided to filter and paginate the result.
* Getting a single Organization object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Organization/:id](https://grcschema.p.rapidapi.com/Organization/:id) endpoint using a REST **GET**.

### Get Organization \(basic & pagination\)

* Getting a list of Organization object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Organization](https://grcschema.p.rapidapi.com/Organization) endpoint using a REST **GET** with no optional parameters.
* Provides a list of all Organization objects as stubs. Stubs show the `property_name` and `property_value` targeted by the stub.
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
        "@type": "Stub",
        "id": 2,
        "property_name": "name",
        "property_value": "Microsoft",
        "thing_type": "Organization"
    },
    {
        "@context": "http://grcschema.org/",
        "@type": "Stub",
        "id": 3,
        "property_name": "name",
        "property_value": "Cisco",
        "thing_type": "Organization"
    }
  ]
}
```

### Get Organization \(filtered & pagination\)

* Getting a filtered list of Organization objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Organization/](https://grcschema.p.rapidapi.com/Organization/) endpoint using a REST **GET** with URL parameters.
* These are the parameters you can optionally supply to the filter. Name and search fields work as a logical AND.

| Field | Description |
| :--- | :--- |
| name | Searches all or a portion of a organization's name. |
| search | Searches across all searchable fields. |
| sort\_dir | 0 = descending, 1 = ascending |
| limit | Combined with offset, provides pagination by limiting results. |
| offset | Combined with limit, provides pagination by shifting the first record. |

### Get Organization By ID

* Getting an existing Organization object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Organization/:id](https://grcschema.p.rapidapi.com/Organization/:id) endpoint using a REST **GET**.

## POST Organization Endpoint

### Quick-start Knowledge

* Adding a new Organization object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/Organization](https://grcschema.p.rapidapi.com/Organization) endpoint as a REST **POST**.
* The full JSON-LD object is defined at [https://grcschema.org/Organization](https://grcschema.org/Organization), and the endpoint will accept the the entire object for processing. This includes array items \(@set\).
* Duplicate email addresses are not allowed in the Organization's data or in the system as whole.
* When posting an object, all ID fields are ignored and can be set to **null**. Any parameter \(key\) or sub-object not provided is considered **null**.
* When the Organization object is created, Social Address information \(facebook, linkedin, etc\) and other organization data \(by domain\) is pulled automatically using Clearbit:tm: if available.
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing is maintained in some systems. \(See the `local_reference_id` section for more detail.\)
* All new objects require a person id performing the update which is accomplished via the `x-requester-person` header value.

### Created\_by Audit Record

* When you send a POST to create an object, you MUST supply an `x-requester-person` in the header as the person id making the request. This sets the created\_by field in the audit record to the person who added the object.

### Minimum Required Object

* Only one primary name and one primary email are required to create an Organization object, however you may supply any other data that complies with the full schema object.
* If you supply a valid domain name, the organization will be populated with lookup data from Clearbit:tm:.

```javascript
{
  "@context": "http://grcschema.org/",
  "@type": "Organization",
  "description": null,
    "Emails": {
    "@type": "Emails",
    "@set": [
      {
        "@type": "Email",
        "email": "compliance@testcompliance-test.com",
        "id": null,
        "organization_fk": null,
        "local_reference_id": "email-ref-id",
        "primary": true
      }
    ]
  },
  "domain": "testcompliance-test.com",
  "id": null,
  "name": "Test Compliance Test",
  "local_reference_id": "organization-ref-id"
}
```

### Response Object

* The minimum response object that is returned is the FULL Organization JSON object as defined by grcschema.
* Where an array of objects exists with no records, the **default example object** is returned. This can be determined by the response having an **"id": null** key/value pair. The other parameters for that object will also be null as seen in the following example.

```text
{
    "@context": "http://grcschema.org/",
    "@type": "Organization",
    "PostalAddresses": {
        "@type": "PostalAddresses",
        "@set": [
            {
                "primary": null,
                "@type": "PostalAddress",
                "address1": null,
                "address2": null,
                "city": null,
                "postal_code": null,
                "country": null,
                "id": null,
                "country_code": null,
                "person_fk": null,
                "organization_fk": null,
                "state_territory_province": null,
                "local_reference_id": null
            }
        ]
    },
    "SocialAddresses": {
        "@type": "SocialAddresses",
        "twitter": null,
        "facebook": null,
        "linkedin": null,
        "youtube": null
    },
    "CoreMetaData": {
        "@type": "CoreMetaData",
        "date_created": "2021-02-11",
        "date_modified": "2021-02-11",
        "created_audit_id": 110,
        "modified_audit_id": null,
        "live_status": false,
        "validated": false
    },
    "PhoneNumbers": {
        "@type": "PhoneNumbers",
        "@set": [
            {
                "@type": "PhoneNumber",
                "phone_number": null,
                "id": null,
                "organization_fk": null
            }
        ]
    },
    "Emails": {
        "@type": "Emails",
        "@set": [
            {
                "@type": "Email",
                "id": 524,
                "email": "compliance@testcompliance-test.com",
                "person_fk": null,
                "organization_fk": 9357,
                "primary": 1
            }
        ]
    },
    "OrganizationCategory": {
        "@type": "OrganizationCategory",
        "Tags": {
            "@type": "Tags",
            "@set": [
                {
                    "@type": "Tag",
                    "id": null,
                    "tag": null,
                    "organization_fk": null,
                    "tag_category": null
                }
            ]
        }
    },
    "OrganizationRoles": {
        "@type": "OrganizationRoles",
        "@set": [
            {
                "@type": "OrganizationRole",
                "name": null,
                "id": null,
                "role_fk": null,
                "organization_fk": null,
                "local_reference_id": null
            }
        ]
    },
    "AdditionalDomains": {
        "@type": "AdditionalDomains",
        "@set": [
            {
                "@type": "AdditionalDomain",
                "domain": null,
                "id": null,
                "organization_fk": null
            }
        ]
    },
    "NonStandardNames": {
        "@type": "NonStandardNames",
        "@set": [
            {
                "@type": "NonStandardName",
                "name": null,
                "id": null,
                "organization_fk": null
            }
        ]
    },
    "name": "Test Compliance Test",
    "id": 9357,
    "parent_id": null,
    "legal_name": null,
    "domain": "testcompliance-test.com",
    "phone_number": null,
    "founded": null,
    "description": null,
    "organization_type": 1,
    "email": "compliance@testcompliance-test.com"
}
```

## PATCH Organization Endpoint

### Quick-start Knowledge

* Updating an Organization object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/Organization/:id](https://grcschema.p.rapidapi.com/Organization/:id) endpoint as a REST **PATCH**.
* The full JSON-LD object is defined at [https://grcschema.org/Organization](https://grcschema.org/Organization), and the endpoint will accept an **existing** Organization object \(with applicable changes\) for processing.
* Duplicate email addresses are not allowed in the Organization's data or in the system as whole.
* When updating any object or sub-object, ID and FK fields cannot be changed.
* **Example sub-objects** in @set arrays are ignored in the update. \(where all properties are null\)
* Some properties cannot be changed and are ignored.
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing required by some systems. \(See the `local_reference_id` section for more detail.\)

### Modified\_by Audit Record

* When you send a PATCH to modify an object, you must supply an `x-requester-person` in the header as the person id making the request. This sets the modified\_by field in the audit record to the person who modified the object.

### Performing a Property \(Key\) Value Update

* Change the properties of the object pulled from **GET /Person/:id** by sending an **application/json PATCH** to the [https://grcschema.org/Organization/:id](https://grcschema.org/Organization/:id) endpoint and the full Person object will be returned with the requested changes.
* Container objects like SocialAddresses are part of the core person record and are displayed as objects for data organization purposes only.

> Here is an example of updating `legal_name` for the organization example above.

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Organization",
    "PostalAddresses": {
        "@type": "PostalAddresses",
        "@set": [
            {
                "primary": null,
                "@type": "PostalAddress",
                "address1": null,
                "address2": null,
                "city": null,
                "postal_code": null,
                "country": null,
                "id": null,
                "country_code": null,
                "person_fk": null,
                "organization_fk": null,
                "state_territory_province": null,
                "local_reference_id": null
            }
        ]
    },
    "SocialAddresses": {
        "@type": "SocialAddresses",
        "twitter": null,
        "facebook": null,
        "linkedin": null,
        "youtube": null
    },
    "CoreMetaData": {
        "@type": "CoreMetaData",
        "date_created": "2021-02-11",
        "date_modified": "2021-02-11",
        "created_audit_id": 110,
        "modified_audit_id": 111,
        "live_status": false,
        "validated": false
    },
    "PhoneNumbers": {
        "@type": "PhoneNumbers",
        "@set": [
            {
                "@type": "PhoneNumber",
                "phone_number": null,
                "id": null,
                "organization_fk": null
            }
        ]
    },
    "Emails": {
        "@type": "Emails",
        "@set": [
            {
                "@type": "Email",
                "id": 524,
                "email": "compliance@testcompliance-test.com",
                "person_fk": null,
                "organization_fk": 9357,
                "primary": 1
            }
        ]
    },
    "OrganizationCategory": {
        "@type": "OrganizationCategory",
        "Tags": {
            "@type": "Tags",
            "@set": [
                {
                    "@type": "Tag",
                    "id": null,
                    "tag": null,
                    "organization_fk": null,
                    "tag_category": null
                }
            ]
        }
    },
    "OrganizationRoles": {
        "@type": "OrganizationRoles",
        "@set": [
            {
                "@type": "OrganizationRole",
                "name": null,
                "id": null,
                "role_fk": null,
                "organization_fk": null,
                "local_reference_id": null
            }
        ]
    },
    "AdditionalDomains": {
        "@type": "AdditionalDomains",
        "@set": [
            {
                "@type": "AdditionalDomain",
                "domain": null,
                "id": null,
                "organization_fk": null
            }
        ]
    },
    "NonStandardNames": {
        "@type": "NonStandardNames",
        "@set": [
            {
                "@type": "NonStandardName",
                "name": null,
                "id": null,
                "organization_fk": null
            }
        ]
    },
    "name": "Test Compliance Test",
    "id": 9357,
    "parent_id": null,
    "legal_name": "Test Compliance Test Corporation",
    "domain": "testcompliance-test.com",
    "phone_number": null,
    "founded": null,
    "description": null,
    "organization_type": 1,
    "email": "compliance@testcompliance-test.com"
}
```

### Updating Unordered Sets

* Updating @set objects have **three** special rules.
* Add a new sub-object by supplying data to any property in any number of objects of @type while leaving the id and fk parameters **null**.
* Change a sub-object instance by changing the property \(or properties\) without modifying the id or fk fields.
* Remove a sub-object instance by removing all the properties except for **@type** and **id**.

### Adding a Sub-Object

> This adds two additional, non-primary Email objects into Emails and the full Organization object is returned with the id and fk for all sub-objects filled in.

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 524,
            "email": "compliance@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": 9357,
            "primary": 1
        },
        {
            "@type": "Email",
            "id": null,
            "email": "compliance2@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": null,
            "primary": false
        },
        {
            "@type": "Email",
            "id": null,
            "email": "compliance3@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": null,
            "primary": false
        }
    ]
},
...
```

### Changing a Sub-Object

> In this example, `compliance3@testcompliance-test.com` is changed to `compliance3-changed@testcompliance-test.com` and the full Organization object is returned with the requested change.

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 525,
            "email": "compliance2@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": 9357,
            "primary": null
        },
        {
            "@type": "Email",
            "id": 526,
            "email": "compliance3-changed@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": 9357,
            "primary": null
        },
        {
            "@type": "Email",
            "id": 524,
            "email": "compliance@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": 9357,
            "primary": 1
        }
    ]
},
...
```

> In this example, the sub-object with `id 525` is deleted by removing the properties and the full Organization object is returned with the requested change.

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 525
        },
        {
            "@type": "Email",
            "id": 526,
            "email": "compliance3-changed@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": 9357,
            "primary": 0
        },
        {
            "@type": "Email",
            "id": 524,
            "email": "compliance@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": 9357,
            "primary": 1
        }
    ]
},
```

### Simultaneous Changes

> Note it is possible to add, change, and delete all at the same time and in any order and the full Organization object is returned with the requested changes.
>
> In this example `id 524` is changed, `id 526` is deleted, and a `new record` is added.

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 526
        },
        {
            "@type": "Email",
            "id": 524,
            "email": "compliance-changed2@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": 9357,
            "primary": 1
        },
        {
            "@type": "Email",
            "id": null,
            "email": "compliance-new@testcompliance-test.com",
            "person_fk": null,
            "organization_fk": null,
            "primary": false
        }
    ]
},
...
```

## How to Use `local_reference_id` - Person Example

### Quick-start Knowledge

* For all endpoints with `POST` and `PATCH` operations, you may send an optional `local_reference_id` for the core object and any sub-objects in unordered lists \(@set arrays\).  This `local_reference_id` will be returned \(like an echo\) for that object.
* It is recommended you use a Type 4 UUID which is unique for that object in your system and tie the federated ID to your record for later use in querying the federated system for that object.

### POST Operation Example

> For the core object, you may place a `local_reference_id` at the object root level, and it will be returned in the response. Do not add `local_reference_id` to the container objects like PersonName. For sub-object, unordered lists \(@set arrays\), you may place a `local_reference_id` in each object, and it will be returned to you in the response.

**SEND**

```javascript
...
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
    "Names": {
        "@type": "Names",
        "@set": [
            {
                "@type": "Name",
                "id": 650,
                "first_name": "John",
                "last_name": "Smith",
                "name_prefix_fk": null,
                "name_suffix_fk": null,
                "person_fk": 30825,
                "middle_initial": null,
                "primary": 1,
            }
        ]
    },  
    "Emails": {
        "@type": "Emails",
        "@set": [
            {
                "@type": "Email",
                "id": null,
                "email": "jsmith-changed@gmail.com",
                "person_fk": null,
                "primary": 1,
                "local_reference_id": "5e98ced6-786e-4488-9186-32a4b57924ae"
            }
        ]
    },
    "email": "jsmith@gmail.com",
    "local_reference_id": "1808bd7f-c99d-4ed0-8310-87483427041f"
}
```

**RESPONSE \(Abbreviated\)**

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
...
"Names": {
    "@type": "Names",
    "@set": [
        {
            "@type": "Name",
            "id": 650,
            "first_name": "John",
            "last_name": "Smith",
            "name_prefix_fk": null,
            "name_suffix_fk": null,
            "person_fk": 30825,
            "middle_initial": null,
            "primary": 1,
        }
    ]
},
...
    "Emails": {
        "@type": "Emails",
        "@set": [
            {
                "@type": "Email",
                "id": 325,
                "email": "jsmith-changed@gmail.com",
                "person_fk": 30755,
                "primary": 1,
                "local_reference_id": "5e98ced6-786e-4488-9186-32a4b57924ae"
            }
        ]
    },
...
    "email": "jsmith-changed@gmail.com",
    "fullname": "John Smith",
    "id": 30755,
    "local_reference_id": "1808bd7f-c99d-4ed0-8310-87483427041f"
}
```

### PATCH Operation Example

> For the core object, you may place a `local_reference_id` at the object root level, and it will be returned in the response. Do not add `local_reference_id` to the container objects like PersonName.

**SEND & RESPONSE**

```javascript
...
"email": "jsmith-changed@gmail.com",
"fullname": "Joe E Smith",
"id": 30711,
"local_reference_id": "ae411a78-fa0d-446e-a47c-2e03fc07bd3b"
}
```

> For sub-object, unordered lists \(@set arrays\), you may place a `local_reference_id` in each object, and it will be returned to you in the response.  
> Note: When a `local_reference_id` is used during delete operation, the object will be returned with no properties but with your `local_reference_id` denoting the object was deleted. If you do not require a returned object denoting the deletion, do not send the `local_reference_id` key and value.

**SEND**

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 256,
            "email": "joeCHANGE4@personal-noreply.com",
            "person_fk": 30711,
            "local_reference_id": "54f30b24-1d1d-4d73-9152-706a0c165f4b"
        },
        {
            "@type": "Email",
            "id": 305,
            "local_reference_id": "6efe8712-6670-4c4e-b2c4-9399b9a4b0a6"
        },
        {
            "@type": "Email",
            "id": null,
            "email": "joe-NEW-EMAIL@personal-noreply.com",
            "person_fk": null,
            "local_reference_id": "56f83375-080b-4b3f-a974-e72f8d77609d"
        }
    ]
},
...
```

**RESPONSE**

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 256,
            "email": "joeCHANGE4@personal-noreply.com",
            "person_fk": 30711,
            "local_reference_id": "54f30b24-1d1d-4d73-9152-706a0c165f4b"
        },
        {
            "@type": "Email",
            "id": 305,
            "local_reference_id": "6efe8712-6670-4c4e-b2c4-9399b9a4b0a6"
        },
        {
            "@type": "Email",
            "id": 323,
            "email": "joe-NEW-EMAIL@personal-noreply.com",
            "person_fk": 30711,
            "local_reference_id": "56f83375-080b-4b3f-a974-e72f8d77609d"
        }
    ]
},
...
```

