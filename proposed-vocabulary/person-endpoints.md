# Person Endpoints

> This document explains the methods you may use to work with the PERSON endpoints in the Federated Authority Document database.

## GET Person Endpoints

### Quick-start Knowledge

* The full JSON-LD Person object is defined at [https://grcschema.org/Person](https://grcschema.org/Person).
* Getting a list of Person object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person](https://grcschema.p.rapidapi.com/Person) endpoint using a REST **GET**. Optional parameters may be provided to filter and paginate the result.
* Getting a single Person object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person/:id](https://grcschema.p.rapidapi.com/Person/:id) endpoint using a REST **GET**.

### Get Person

* Getting a list of Person object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person](https://grcschema.p.rapidapi.com/Person) endpoint using a REST **GET** with no optional parameters.
* Provides a list of all Person objects as stubs.

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Stub",
    "id": 30711,
    "name": "Joe Smith"
}
```

### Get Person \(filtered\)

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
* The full JSON-LD object is defined at [https://grcschema.org/Person](https://grcschema.org/Person), and the endpoint will accept the the entire object for processing. This includes array items \(\@set\).
* Duplicate email addresses are not allowed in the Person's data or in the system as whole.
* When posting an object, all ID fields are ignored and can be set to **null**. Any parameter \(key\) or sub-object not provided is considered **null**.
* When the Person object is created, Social Address information \(facebook, linkedin, etc\) is pulled automatically using Clearbit:tm: if available.
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing is maintained in some systems. \(See the `local_reference_id` section for more detail.\)

### Minimum Required Object

* Only first name, last name, and email are required to create a Person object, however you may supply any other data that complies with the full schema.

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
    "PersonName": {
        "@type": "PersonName",
        "first_name": "Joe",
        "last_name": "Smith"
    },
    "email": "joe@compliance-noreply.com"
}
```

### Response Object

* The response object that is returned is the FULL Person JSON object as defined by grcschema.
* Where an array of objects exists with no records, the **default example object** is returned. This can be determined by the response having an **"id": null** key/value pair. The other parameters for that object will also be null as seen in the following example.

```javascript
"AdditionalEmails": {
    "@type": "AdditionalEmails",
    "@set": [
        {
            "@type": "AdditionalEmail",
            "email": null,
            "id": null,
            "person_fk": null
        }
    ]
}
```

* This is the full JSON object for the Joe Smith example above. Please note how the arrays have "example" sub-objects. These are provided for easier understanding of the overall object structure and allows the full object to be further modified through the patch endpoint.

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
    "PostalAddress": {
        "@type": "PostalAddress",
        "address1": null,
        "address2": null,
        "city": null,
        "state_territory_province": null,
        "postal_code": null,
        "country": null,
        "country_code": null
    },
    "SocialAddresses": {
        "@type": "SocialAddresses",
        "twitter": null,
        "facebook": null,
        "linkedin": null,
        "youtube": null
    },
    "PersonName": {
        "@type": "PersonName",
        "first_name": "Joe",
        "last_name": "Smith",
        "middle_initial": null,
        "name_prefix": null,
        "name_suffix": null
    },
    "CoreMetaData": {
        "@type": "CoreMetaData",
        "date_created": "2020-12-23",
        "date_modified": "2020-12-23",
        "created_by": null,
        "modified_by": null,
        "live_status": null,
        "checksum": 0
    },
    "PersonMemberships": {
        "@type": "PersonMemberships",
        "PersonOrganizations": {
            "@type": "PersonOrganizations",
            "@set": [
                {
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
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "initiative_fk": null
                }
            ]
        },
        "PersonTeams": {
            "@type": "PersonTeams",
            "@set": [
                {
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "team_fk": null
                }
            ]
        }
    },
    "AdditionalNames": {
        "@type": "AdditionalNames",
        "@set": [
            {
                "@type": "AdditionalName",
                "first_name": null,
                "last_name": null,
                "name_prefix": null,
                "name_suffix": null,
                "id": null,
                "person_fk": null,
                "middle_initial": null
            }
        ]
    },
    "AdditionalEmails": {
        "@type": "AdditionalEmails",
        "@set": [
            {
                "@type": "AdditionalEmail",
                "email": null,
                "id": null,
                "person_fk": null
            }
        ]
    },
    "AdditionalPostalAddresses": {
        "@type": "AdditionalPostalAddresses",
        "@set": [
            {
                "@type": "AdditionalPostalAddress",
                "address1": null,
                "address2": null,
                "city": null,
                "postal_code": null,
                "country": null,
                "country_code": null,
                "id": null,
                "person_fk": null,
                "state_territory_province": null
            }
        ]
    },
    "email": "joe@compliance-noreply.com",
    "fullname": "Joe Smith",
    "id": 30711
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
* **Example sub-objects** in \@set arrays are ignored in the update. \(where all properties are null\)
* Some properties cannot be changed and are ignored.  \(e.g. fullname or any id or fk\)
* A `local_reference_id` may be supplied to any core object or sub-object which will be echoed within the object response.  This allows tagging of any object to ensure accurate processing required by some systems. \(See the `local_reference_id` section for more detail.\)

### Performing a Property \(Key\) Value Update

* Change the properties of the object pulled from **GET /Person/:id** by sending an **application/json PATCH** to the [https://grcschema.org/Person/:id](https://grcschema.org/Person/:id) endpoint and the full Person object will be returned with the requested changes.
* Container objects like PostalAddress, SocialAddresses, and PersonName are part of the core person record and are displayed as objects for data organization purposes only.

> Here is an example with Joe.

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
    "PostalAddress": {
        "@type": "PostalAddress",
        "address1": "123 West Avenue",
        "address2": "Suite 123",
        "city": "Las Vegas",
        "state_territory_province": "Nevada",
        "postal_code": "88901",
        "country": "United States of America",
        "country_code": "USA"
    },
    "SocialAddresses": {
        "@type": "SocialAddresses",
        "twitter": null,
        "facebook": null,
        "linkedin": null,
        "youtube": null
    },
    "PersonName": {
        "@type": "PersonName",
        "first_name": "Joe",
        "last_name": "Smith",
        "middle_initial": "E",
        "name_prefix": null,
        "name_suffix": null
    },
    "CoreMetaData": {
        "@type": "CoreMetaData",
        "date_created": "2020-12-23",
        "date_modified": "2020-12-23",
        "created_by": null,
        "modified_by": null,
        "live_status": null,
        "checksum": 0
    },
    "PersonMemberships": {
        "@type": "PersonMemberships",
        "PersonOrganizations": {
            "@type": "PersonOrganizations",
            "@set": [
                {
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
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "initiative_fk": null
                }
            ]
        },
        "PersonTeams": {
            "@type": "PersonTeams",
            "@set": [
                {
                    "name": null,
                    "id": null,
                    "person_fk": null,
                    "team_fk": null
                }
            ]
        }
    },
    "AdditionalNames": {
        "@type": "AdditionalNames",
        "@set": [
            {
                "@type": "AdditionalName",
                "first_name": null,
                "last_name": null,
                "name_prefix": null,
                "name_suffix": null,
                "id": null,
                "person_fk": null,
                "middle_initial": null
            }
        ]
    },
    "AdditionalEmails": {
        "@type": "AdditionalEmails",
        "@set": [
            {
                "@type": "AdditionalEmail",
                "email": null,
                "id": null,
                "person_fk": null
            }
        ]
    },
    "AdditionalPostalAddresses": {
        "@type": "AdditionalPostalAddresses",
        "@set": [
            {
                "@type": "AdditionalPostalAddress",
                "address1": null,
                "address2": null,
                "city": null,
                "postal_code": null,
                "country": null,
                "country_code": null,
                "id": null,
                "person_fk": null,
                "state_territory_province": null
            }
        ]
    },
    "email": "joes-new-email@compliance-noreply.com",
    "fullname": "Joe Smith",
    "id": 30711
}
```

### Updating Unordered Sets

* Updating \@set objects have **three** special rules.
* Add a new sub-object by supplying data to any property in any number of objects of \@type while leaving the id and fk parameters **null**.
* Change a sub-object instance by changing the property \(or properties\) without modifying the id or fk fields.
* Remove a sub-object instance by removing all the properties except for **\@type** and **id**.

### Adding a Sub-Object

> This adds three additional AdditionalEmail objects into AdditionalEmails and the full Person object is returned with the id and fk for all sub-objects filled in.

```javascript
...
"AdditionalEmails": {
    "@type": "AdditionalEmails",
    "@set": [
        {
            "@type": "AdditionalEmail",
            "email": "joe@personal-noreply.com",
            "id": null,
            "person_fk": null
        },
        {
            "@type": "AdditionalEmail",
            "email": "jsmith@compliance-noreply.com",
            "id": null,
            "person_fk": null
        },
        {
            "@type": "AdditionalEmail",
            "email": "js@compliance-noreply.com",
            "id": null,
            "person_fk": null
        }
    ]
},
...
```

### Changing a Sub-Object

> In this example, `jsmith@compliance-noreply.com` is changed to `jsmithCHANGED@compliance-noreply.com` and the full Person object is returned with the requested change.

```javascript
...
"AdditionalEmails": {
    "@type": "AdditionalEmails",
    "@set": [
        {
            "@type": "AdditionalEmail",
            "id": 256,
            "email": "joe@personal-noreply.com",
            "person_fk": 30711
        },
        {
            "@type": "AdditionalEmail",
            "id": 257,
            "email": "jsmithCHANGED@compliance-noreply.com",
            "person_fk": 30711
        },
        {
            "@type": "AdditionalEmail",
            "id": 258,
            "email": "js@compliance-noreply.com",
            "person_fk": 30711
        }
    ]
},
...
```

### Removing a Sub-Object

> In this example, the sub-object with `id 258` is deleted by removing the properties and the full Person object is returned with the requested change.

```javascript
...
"AdditionalEmails": {
    "@type": "AdditionalEmails",
    "@set": [
        {
            "@type": "AdditionalEmail",
            "id": 256,
            "email": "joe@personal-noreply.com",
            "person_fk": 30711
        },
        {
            "@type": "AdditionalEmail",
            "id": 257,
            "email": "jsmith@compliance-noreply.com",
            "person_fk": 30711
        },
        {
            "@type": "AdditionalEmail",
            "id": 258
        }
    ]
},
...
```

### Simultaneous Changes

> Note it is possible to add, change, and delete all at the same time and in any order and the full Person object is returned with the requested changes.
>
> In this example `id 256` is changed, `id 257` is deleted, and a `new record` is added.

```javascript
...
"AdditionalEmails": {
    "@type": "AdditionalEmails",
    "@set": [
        {
            "@type": "AdditionalEmail",
            "id": 256,
            "email": "joeCHANGE2@personal-noreply.com",
            "person_fk": 30711
        },
        {
            "@type": "AdditionalEmail",
            "id": 257
        },
        {
            "@type": "AdditionalEmail",
            "id": null,
            "email": "jsmith-NEW@compliance-noreply.com",
            "person_fk": null
        }
    ]
},
...
```

### Special Note About `name_prefix` and `name_suffix`

> These values are integers based on IDs found in the Prefix and Suffix endpoints.

## How to Use `local_reference_id`

### Quick-start Knowledge

* For `POST` and `PATCH` operations, you may send an optional `local_reference_id` for the core object and any sub-objects in unordered lists \(\@set arrays\).  This `local_reference_id` will be returned \(like an echo\) for that object.
* It is recommended you use a Type 4 UUID which is unique for that object in your system and tie the federated ID to your record for later use in querying the federated system for that object.

### POST Operation Example

> For the core object, you may place a `local_reference_id` at the object root level, and it will be returned in the response. Do not add `local_reference_id` to the container objects like PersonName. For sub-object, unordered lists \(\@set arrays\), you may place a `local_reference_id` in each object, and it will be returned to you in the response.

**SEND**

```javascript
...
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
    "PersonName": {
        "@type": "PersonName",
        "first_name": "Bob",
        "last_name": "Roberts"
    },    
    "AdditionalEmails": {
        "@type": "AdditionalEmails",
        "@set": [
            {
                "@type": "AdditionalEmail",
                "id": null,
                "email": "bobr123@gmail.com",
                "person_fk": null,
                "local_reference_id": "5e98ced6-786e-4488-9186-32a4b57924ae"
            }
        ]
    },
    "email": "bobr@compliance-noreply.com",
    "local_reference_id": "1808bd7f-c99d-4ed0-8310-87483427041f"
}
```

**RESPONSE \(Abbreviated\)**

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Person",
...
    "PersonName": {
        "@type": "PersonName",
        "first_name": "Bob",
        "last_name": "Roberts",
        "middle_initial": null,
        "name_prefix": null,
        "name_suffix": null
    },
...
    "AdditionalEmails": {
        "@type": "AdditionalEmails",
        "@set": [
            {
                "@type": "AdditionalEmail",
                "id": 325,
                "email": "bobr123@gmail.com",
                "person_fk": 30755,
                "local_reference_id": "5e98ced6-786e-4488-9186-32a4b57924ae"
            }
        ]
    },
...
    "email": "bobr@compliance-noreply.com",
    "fullname": "Bob Roberts",
    "id": 30755,
    "local_reference_id": "1808bd7f-c99d-4ed0-8310-87483427041f"
}
```

### PATCH Operation Example

> For the core object, you may place a `local_reference_id` at the object root level, and it will be returned in the response. Do not add `local_reference_id` to the container objects like PersonName.

**SEND & RESPONSE**

```javascript
...
"email": "joes-new-email@compliance-noreply.com",
"fullname": "Joe E Smith",
"id": 30711,
"local_reference_id": "ae411a78-fa0d-446e-a47c-2e03fc07bd3b"
}
```

> For sub-object, unordered lists \(\@set arrays\), you may place a `local_reference_id` in each object, and it will be returned to you in the response.  
> Note: When a `local_reference_id` is used during delete operation, the object will be returned with no properties but with your `local_reference_id` denoting the object was deleted. If you do not require a returned object denoting the deletion, do not send the `local_reference_id` key and value.

**SEND**

```javascript
...
"AdditionalEmails": {
    "@type": "AdditionalEmails",
    "@set": [
        {
            "@type": "AdditionalEmail",
            "id": 256,
            "email": "joeCHANGE4@personal-noreply.com",
            "person_fk": 30711,
            "local_reference_id": "54f30b24-1d1d-4d73-9152-706a0c165f4b"
        },
        {
            "@type": "AdditionalEmail",
            "id": 305,
            "local_reference_id": "6efe8712-6670-4c4e-b2c4-9399b9a4b0a6"
        },
        {
            "@type": "AdditionalEmail",
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
"AdditionalEmails": {
    "@type": "AdditionalEmails",
    "@set": [
        {
            "@type": "AdditionalEmail",
            "id": 256,
            "email": "joeCHANGE4@personal-noreply.com",
            "person_fk": 30711,
            "local_reference_id": "54f30b24-1d1d-4d73-9152-706a0c165f4b"
        },
        {
            "@type": "AdditionalEmail",
            "id": 305,
            "local_reference_id": "6efe8712-6670-4c4e-b2c4-9399b9a4b0a6"
        },
        {
            "@type": "AdditionalEmail",
            "id": 323,
            "email": "joe-NEW-EMAIL@personal-noreply.com",
            "person_fk": 30711,
            "local_reference_id": "56f83375-080b-4b3f-a974-e72f8d77609d"
        }
    ]
},
...
```

