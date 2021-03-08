# Person Endpoints

> This document explains the methods you may use to work with the PERSON endpoints in the Federated Authority Document database.

## GET Person Endpoints

### Quick-start Knowledge

* The full JSON-LD Person object is defined at [https://grcschema.org/Person](https://grcschema.org/Person).
* Getting a list of Person object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person](https://grcschema.p.rapidapi.com/Person) endpoint using a REST **GET**. Optional parameters may be provided to filter and paginate the result.
* Getting a single Person object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person/:id](https://grcschema.p.rapidapi.com/Person/:id) endpoint using a REST **GET**.

### Get Person \(basic\)

* Getting a list of Person object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person](https://grcschema.p.rapidapi.com/Person) endpoint using a REST **GET** with no optional parameters.
* Provides a list of all Person objects as stubs. Stubs show the `property_name` and `property_value` targeted by the stub.
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
      "id": 30711,
      "property_name": "fullname",
      "property_value": "Joe Smith",
      "thing_type": "Person"
    },
    {
      "@context": "http://grcschema.org/",
      "@type": "Stub",
      "id": 30712,
      "property_name": "fullname",
      "property_value": "Bob Johnson",
      "thing_type": "Person"
    }
  ]
}
```

### Get Person \(filtered & pagination\)

* Getting a filtered list of Person objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person/](https://grcschema.p.rapidapi.com/Person/) endpoint using a REST **GET** with url parameters.
* These are the parameters you can optionally supply to the filter. These fields work as a logical AND.

| Field | Description |
| :--- | :--- |
| first\_name | Searches all or a portion of a person's first name. |
| last\_name | Searches all or a portion of a person's last name. |
| email | Searches all or a portion of a person's email address. |
| sort\_dir | 0 = descending, 1 = ascending |
| search | Searches across all searchable fields. |
| limit | Combined with offset, provides pagination by limiting results. |
| offset | Combined with limit, provides pagination by shifting the first record. |

### Get Person By ID

* Getting an existing Person object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person/:id](https://grcschema.p.rapidapi.com/Person/:id) endpoint using a REST **GET**.

## POST Person Endpoint

### Quick-start Knowledge

* Adding a new Person object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/Person](https://grcschema.p.rapidapi.com/Person) endpoint as a REST **POST**.
* The full JSON-LD object is defined at [https://grcschema.org/Person](https://grcschema.org/Person), and the endpoint will accept the the entire object for processing. This includes array items \(@set\).
* Duplicate email addresses are not allowed in the Person's data or in the system as whole.
* When posting an object, all ID fields are ignored and can be set to **null**. Any parameter \(key\) or sub-object not provided is considered **null**.
* When the Person object is created, Social Address information \(facebook, linkedin, etc\) is pulled automatically using Clearbit:tm: if available.
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing is maintained in some systems. \(See the `local_reference_id` section for more detail.\)
* All new objects require a person id performing the update which is accomplished via the `x-requester-person` header value.

### Created\_by Audit Record and Person 0

* When you send a POST to create an object, you must supply an `x-requester-person` in the header as the person id making the request. This sets the created\_by field in the audit record to the person who added the object.
* In the case where a Person \(as a user of your application\) is adding themselves, `x-requester-person` may be set to 0 for the POST.  This will create the Person and assign the change to the newly created Person. Any subsequent calls from that Person should use their ID.

### Minimum Required Object

* Only one primary name \(`first_name` and `last_name`\) or one `freeform_name` are required to create a Person object, however you may supply any other data that complies with the full schema object.
* The primary name \(where `primary` is true\) is used to populate the `Person.fullname` read only property.  This value is used in the stub list.

```javascript
{
  "@context": "https://grcschema.org",
  "@type": "Person",
  "Names": {
    "@type": "Names",
    "@set": [
      {
        "@type": "Name",
        "first_name": "John",
        "last_name": "Smith",
        "freeform_name": null,
        "primary": true
      }
    ]
  },
  "id": null
}
```

> Alternatively, you may use freeform\_name for names, aliases, etc that do not fit the structured naming format.

```javascript
{
  "@context": "https://grcschema.org",
  "@type": "Person",
  "Names": {
    "@type": "Names",
    "@set": [
      {
        "@type": "Name",
        "first_name": null,
        "last_name": null,
        "freeform_name": "J. Smith (Smitty)",
        "primary": true
      }
    ]
  },
  "id": null
}
```

### Constraints

* When a structured name is added, `firstname` and `lastname` are required.
* A Person may be added with only a Name object, but only one Person of any given name may exist like this.  You cannot add two John Smith Persons with only a `Person.Names.Name`
* A name can duplicate when an email address is provided that differs from any email address in the system for a Person. \(e.g. John Smith with jsmith@abc.com is considered a different Person than jsmith@xyz.com\)

### Response Object

* The response object that is returned is the FULL Person JSON object as defined by grcschema.
* Where an array of objects exists with no records, the **default example object** is returned. This can be determined by the response having an **"id": null** key/value pair. The other parameters for that object will also be null as seen in the following example.

```javascript
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
}
```

* This is the full JSON object for the John Smith example above. Please note how the arrays have "example" sub-objects. These are provided for easier understanding of the overall object structure and allows the full object to be further modified through the patch endpoint.

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
    "PhoneNumbers": {
        "@type": "PhoneNumbers",
        "@set": [
            {
                "@type": "PhoneNumber",
                "id": null,
                "phone_number": null,
                "person_fk": null,
                "organization_fk": null,
                "local_reference_id": null,
                "primary": null
            }
        ]
    },
    "PersonRoles": {
        "@type": "PersonRoles",
        "@set": [
            {
                "@type": "PersonRole",
                "name": null,
                "id": null,
                "role_fk": null,
                "person_fk": null,
                "local_reference_id": null
            }
        ]
    },
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
        "date_created": "2021-03-03",
        "date_modified": "2021-03-03",
        "created_audit_id": 171,
        "modified_audit_id": null,
        "live_status": null,
        "checksum": 0,
        "validated": true,
        "deprecated_notes": null,
        "superceded_by": null
    },
    "PersonMemberships": {
        "@type": "PersonMemberships",
        "PersonOrganizations": {
            "@type": "PersonOrganizations",
            "@set": [
                {
                    "@type": "PersonOrganization",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "organization_fk": null
                }
            ]
        },
        "PersonGroups": {
            "@type": "PersonGroups",
            "@set": [
                {
                    "@type": "PersonGroup",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "group_fk": null
                }
            ]
        },
        "PersonInitiatives": {
            "@type": "PersonInitiatives",
            "@set": [
                {
                    "@type": "PersonInitiative",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "initiative": null
                }
            ]
        },
        "PersonTeams": {
            "@type": "PersonTeams",
            "@set": [
                {
                    "@type": "PersonTeam",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "team_fk": null
                }
            ]
        }
    },
    "Emails": {
        "@type": "Emails",
        "@set": [
            {
                "@type": "Email",
                "email": null,
                "id": null,
                "person_fk": null,
                "organization_fk": null,
                "local_reference_id": null,
                "primary": null
            }
        ]
    },
    "Names": {
        "@type": "Names",
        "@set": [
            {
                "@type": "Name",
                "id": 689,
                "first_name": "John",
                "last_name": "Smith",
                "name_prefix_fk": null,
                "name_suffix_fk": null,
                "freeform_name": null,
                "person_fk": 30863,
                "middle_initial": null,
                "primary": true,
                "local_reference_id": "name-1"
            }
        ]
    },
    "email": null,
    "fullname": "John Smith",
    "id": 30863
}
```

### Special Note About `name_prefix` and `name_suffix`

> These values are integers based on IDs found in the Prefix and Suffix endpoints.

## PATCH Person Endpoint

### Quick-start Knowledge

* Updating a Person object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/Person/:id](https://grcschema.p.rapidapi.com/Person/:id) endpoint as a REST **PATCH**.
* The full JSON-LD object is defined at [https://grcschema.org/Person](https://grcschema.org/Person), and the endpoint will accept an **existing** Person object \(with applicable changes\) for processing.
* Duplicate email addresses are not allowed in the Person's data or in the system as whole.
* When updating any object or sub-object, ID and FK fields cannot be changed.
* **Example sub-objects** in @set arrays are ignored in the update. \(where all properties are null\)
* Some properties cannot be changed and are ignored.  \(e.g. fullname or any id or fk\)
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing required by some systems. \(See the `local_reference_id` section for more detail.\)

### Modified\_by Audit Record

* When you send a PATCH to modify an object, you must supply an `x-requester-person` in the header as the person id making the request. This sets the modified\_by field in the audit record to the person who modified the object.

### Performing a Property \(Key\) Value Update

* Change the properties of the object pulled from **GET /Person/:id** by sending an **application/json PATCH** to the [https://grcschema.org/Person/:id](https://grcschema.org/Person/:id) endpoint and the full Person object will be returned with the requested changes.
* Container objects like PostalAddress, SocialAddresses, and PersonName are part of the core person record and are displayed as objects for data organization purposes only.

> Here is an example with John - adding an email, telephone, a role, and an address.

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
    "PhoneNumbers": {
        "@type": "PhoneNumbers",
        "@set": [
            {
                "@type": "PhoneNumber",
                "id": null,
                "phone_number": "623-555-1212",
                "person_fk": null,
                "organization_fk": null,
                "local_reference_id": "phonenumber-1",
                "primary": true
            }
        ]
    },
    "PersonRoles": {
        "@type": "PersonRoles",
        "@set": [
            {
                "@type": "PersonRole",
                "name": null,
                "id": null,
                "role_fk": 245,
                "person_fk": null,
                "local_reference_id": "role-1"
            }
        ]
    },
    "PostalAddresses": {
        "@type": "PostalAddresses",
        "@set": [
            {
                "primary": null,
                "@type": "PostalAddress",
                "address1": "123 West East Street",
                "address2": "#107",
                "city": "Phoenix",
                "postal_code": "85340",
                "country": "United States of America",
                "id": null,
                "country_code": "USA",
                "person_fk": null,
                "organization_fk": null,
                "state_territory_province": null,
                "local_reference_id": "postal-1"
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
        "date_created": "2021-03-03",
        "date_modified": "2021-03-03",
        "created_audit_id": 171,
        "modified_audit_id": null,
        "live_status": null,
        "checksum": 0,
        "validated": true,
        "deprecated_notes": null,
        "superceded_by": null
    },
    "PersonMemberships": {
        "@type": "PersonMemberships",
        "PersonOrganizations": {
            "@type": "PersonOrganizations",
            "@set": [
                {
                    "@type": "PersonOrganization",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "organization_fk": null
                }
            ]
        },
        "PersonGroups": {
            "@type": "PersonGroups",
            "@set": [
                {
                    "@type": "PersonGroup",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "group_fk": null
                }
            ]
        },
        "PersonInitiatives": {
            "@type": "PersonInitiatives",
            "@set": [
                {
                    "@type": "PersonInitiative",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "initiative": null
                }
            ]
        },
        "PersonTeams": {
            "@type": "PersonTeams",
            "@set": [
                {
                    "@type": "PersonTeam",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "team_fk": null
                }
            ]
        }
    },
    "Emails": {
        "@type": "Emails",
        "@set": [
            {
                "@type": "Email",
                "email": "jsmith@no-reply.org",
                "id": null,
                "person_fk": null,
                "organization_fk": null,
                "local_reference_id": null,
                "primary": true
            }
        ]
    },
    "Names": {
        "@type": "Names",
        "@set": [
            {
                "@type": "Name",
                "id": 689,
                "first_name": "John",
                "last_name": "Smith",
                "name_prefix_fk": null,
                "name_suffix_fk": null,
                "freeform_name": null,
                "person_fk": 30863,
                "middle_initial": null,
                "primary": true,
                "local_reference_id": "name-1"
            }
        ]
    },
    "email": null,
    "fullname": "John Smith",
    "id": 30863
}
```

> Here is the response

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
    "PhoneNumbers": {
        "@type": "PhoneNumbers",
        "@set": [
            {
                "@type": "PhoneNumber",
                "id": 1197,
                "phone_number": "623-555-1212",
                "person_fk": 30863,
                "organization_fk": null,
                "primary": true
            }
        ]
    },
    "PersonRoles": {
        "@type": "PersonRoles",
        "@set": [
            {
                "@type": "PersonRole",
                "id": 5,
                "role_fk": 245,
                "person_fk": 30863,
                "name": "Chief Information Officer"
            }
        ]
    },
    "PostalAddresses": {
        "@type": "PostalAddresses",
        "@set": [
            {
                "@type": "PostalAddress",
                "id": 8304,
                "address1": "123 West East Street",
                "address2": "#107",
                "city": "Phoenix",
                "state_territory_province": null,
                "postal_code": "85340",
                "country": "United States of America",
                "country_code": "USA",
                "person_fk": 30863,
                "organization_fk": null,
                "primary": false,
                "local_reference_id": "postal-1"
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
        "date_created": "2021-03-03",
        "date_modified": "2021-03-03",
        "created_audit_id": 171,
        "modified_audit_id": 172,
        "live_status": 1,
        "checksum": 0,
        "validated": true,
        "deprecated_notes": null,
        "superceded_by": null
    },
    "PersonMemberships": {
        "@type": "PersonMemberships",
        "PersonOrganizations": {
            "@type": "PersonOrganizations",
            "@set": [
                {
                    "@type": "PersonOrganization",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "organization_fk": null
                }
            ]
        },
        "PersonGroups": {
            "@type": "PersonGroups",
            "@set": [
                {
                    "@type": "PersonGroup",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "group_fk": null
                }
            ]
        },
        "PersonInitiatives": {
            "@type": "PersonInitiatives",
            "@set": [
                {
                    "@type": "PersonInitiative",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "initiative": null
                }
            ]
        },
        "PersonTeams": {
            "@type": "PersonTeams",
            "@set": [
                {
                    "@type": "PersonTeam",
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "team_fk": null
                }
            ]
        }
    },
    "Emails": {
        "@type": "Emails",
        "@set": [
            {
                "@type": "Email",
                "id": 610,
                "email": "jsmith@no-reply.org",
                "person_fk": 30863,
                "organization_fk": null,
                "primary": true,
                "local_reference_id": null
            }
        ]
    },
    "Names": {
        "@type": "Names",
        "@set": [
            {
                "@type": "Name",
                "id": 689,
                "first_name": "John",
                "last_name": "Smith",
                "name_prefix_fk": null,
                "name_suffix_fk": null,
                "freeform_name": null,
                "person_fk": 30863,
                "middle_initial": null,
                "primary": true,
                "local_reference_id": "name-1"
            }
        ]
    },
    "email": "jsmith@no-reply.org",
    "fullname": "John Smith",
    "id": 30863
}
```

### Updating Unordered Sets

* Updating @set objects have **three** special rules.
* Add a new sub-object by supplying data to any property in any number of objects of @type while leaving the id and fk parameters **null**.
* Change a sub-object instance by changing the property \(or properties\) without modifying the id or fk fields.
* Remove a sub-object instance by removing all the properties except for **@type** and **id**.

### Adding a Sub-Object

> This adds three additional Email objects into Emails and the full Person object is returned with the id and fk for all sub-objects filled in.

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 610,
            "email": "jsmith@no-reply.org",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": true
        },
        {
            "@type": "Email",
            "email": "joe@personal-noreply.com",
            "id": null,
            "person_fk": null,
            "primary": false
        },
        {
            "@type": "Email",
            "email": "jsmith@compliance-noreply.com",
            "id": null,
            "person_fk": null,
            "primary": false
        },
        {
            "@type": "Email",
            "email": "js@compliance-noreply.com",
            "id": null,
            "person_fk": null,
            "primary": false
        }
    ]
},
...
```

### Changing a Sub-Object

> In this example, `jsmith@compliance-noreply.com` is changed to `jsmithCHANGED@compliance-noreply.com` and the full Person object is returned with the requested change.

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 610,
            "email": "jsmith@no-reply.org",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": true
        },
        {
            "@type": "Email",
            "id": 612,
            "email": "joe@personal-noreply.com",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": false
        },
        {
            "@type": "Email",
            "id": 613,
            "email": "jsmithCHANGED@compliance-noreply.com",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": false
        },
        {
            "@type": "Email",
            "id": 614,
            "email": "js@compliance-noreply.com",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": false
        }
    ]
},
...
```

### Removing a Sub-Object

> In this example, the sub-object with `id 614` is deleted by removing the properties and the full Person object is returned with the requested change.

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 610,
            "email": "jsmith@no-reply.org",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": true
        },
        {
            "@type": "Email",
            "id": 612,
            "email": "joe@personal-noreply.com",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": false
        },
        {
            "@type": "Email",
            "id": 613,
            "email": "jsmithCHANGED@compliance-noreply.com",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": false
        },
        {
            "@type": "Email",
            "id": 614
        }
    ]
},
...
```

### Simultaneous Changes

> Note it is possible to add, change, and delete all at the same time and in any order and the full Person object is returned with the requested changes.
>
> In this example `id 613` is changed, `id 612` is deleted, and a `new record` is added.

```javascript
...
"Emails": {
    "@type": "Emails",
    "@set": [
        {
            "@type": "Email",
            "id": 610,
            "email": "jsmith@no-reply.org",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": true
        },
        {
            "@type": "Email",
            "id": 612
        },
        {
            "@type": "Email",
            "id": 613,
            "email": "jsmithCHANGED2@compliance-noreply.com",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": false
        },
        {
            "@type": "Email",
            "id": null,
            "email": "jsmithNEW@compliance-noreply.com",
            "person_fk": 30863,
            "organization_fk": null,
            "primary": false
        }
    ]
},
...
```

### Special Note About `name_prefix` and `name_suffix`

> These values are integers based on IDs found in the Prefix and Suffix endpoints.

## How to Use `local_reference_id`

### Quick-start Knowledge

* For `POST` and `PATCH` operations, you may send an optional `local_reference_id` for the core object and any sub-objects in unordered lists \(@set arrays\).  This `local_reference_id` will be returned \(like an echo\) for that object.
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

