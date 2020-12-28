# Person Endpoints

> This document explains the methods you may use to work with the PERSON endpoints in the Federated Authority Document database.

## GET Person Endpoints

### Quick-start Knowledge

* The full JSON-LD Person object is defined at [https://grcschema.org/Person](https://grcschema.org/Person).
* Getting a list of Person object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person](https://grcschema.p.rapidapi.com/Person) endpoint using a REST **GET**.
* Getting a filtered list of Person objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person/](https://grcschema.p.rapidapi.com/Person/) endpoint using a REST **POST** with an  **application/x-www-form-urlencoded** content type.  

  \(Note this will be merging with GET /Person.\)

* Getting an existing Person object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person/:id](https://grcschema.p.rapidapi.com/Person/:id) endpoint using a REST **GET**.

### Get Person

* Getting a list of Person object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person](https://grcschema.p.rapidapi.com/Person) endpoint using a REST **GET**.
* Provides a list of all Person objects as stubs.

```javascript
{
    "@context": "http://grcschema.org/",
    "@type": "Stub",
    "id": 30711,
    "name": "Joe Smith"
}
```

### Get \(POST\) Person \(filtered\)

* Getting a filtered list of Person objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Person/](https://grcschema.p.rapidapi.com/Person/) endpoint using a REST **POST** with an **application/x-www-form-urlencoded** content type. \(Note this will be merging with GET /Person.\)
* These are the form fields you can optionally supply to the filter. These fields work as a logical AND.

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

* Adding a new Person object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/addPerson](https://grcschema.p.rapidapi.com/addPerson) endpoint as a REST **POST**.
* The full JSON-LD object is defined at [https://grcschema.org/Person](https://grcschema.org/Person), and the endpoint will accept the the entire object for processing. This includes array items \(\@set\).
* Duplicate email addresses are not allowed in the Person's data or in the system as whole.
* When posting an object, all ID fields are ignored and can be set to **null**. Any parameter \(key\) or sub-object not provided is considered **null**.
* When the Person object is created, Social Address information \(facebook, linkedin, etc\) is pulled automatically using Clearbit:tm: if available.

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

## PATCH Person Endpoint

### Quick-start Knowledge

* Updating a Person object is accomplished by sending an **application/json** content type object to the [https://grcschema.p.rapidapi.com/updatePerson](https://grcschema.p.rapidapi.com/updatePerson) endpoint as a REST **POST**.
* The full JSON-LD object is defined at [https://grcschema.org/Person](https://grcschema.org/Person), and the endpoint will accept an **existing** Person object \(with applicable changes\) for processing.
* Duplicate email addresses are not allowed in the Person's data or in the system as whole.
* When updating any object or sub-object, ID and FK fields cannot be changed.
* **Example sub-objects** in \@set arrays are ignored in the update. \(where all properties are null\)
* Some properties cannot be changed and are ignored.  \(e.g. fullname or any id or fk\)

### Performing a Property \(Key\) Value Update

* Change the properties of the object pulled from **GET /Person/:id** by sending an **application/json POST** to the [https://grcschema.org/Person](https://grcschema.org/Person) endpoint and the full Person object will be returned with the requested changes.

  > Here is an example with Joe.
  >
  > ```javascript
  > {
  > "@context": "http://grcschema.org/",
  > "@type": "Person",
  > "PostalAddress": {
  >     "@type": "PostalAddress",
  >     "address1": "123 West Avenue",
  >     "address2": "Suite 123",
  >     "city": "Las Vegas",
  >     "state_territory_province": "Nevada",
  >     "postal_code": "88901",
  >     "country": "United States of America",
  >     "country_code": "USA"
  > },
  > "SocialAddresses": {
  >     "@type": "SocialAddresses",
  >     "twitter": null,
  >     "facebook": null,
  >     "linkedin": null,
  >     "youtube": null
  > },
  > "PersonName": {
  >     "@type": "PersonName",
  >     "first_name": "Joe",
  >     "last_name": "Smith",
  >     "middle_initial": "E",
  >     "name_prefix": null,
  >     "name_suffix": null
  > },
  > "CoreMetaData": {
  >     "@type": "CoreMetaData",
  >     "date_created": "2020-12-23",
  >     "date_modified": "2020-12-23",
  >     "created_by": null,
  >     "modified_by": null,
  >     "live_status": null,
  >     "checksum": 0
  > },
  > "PersonMemberships": {
  >     "@type": "PersonMemberships",
  >     "PersonOrganizations": {
  >         "@type": "PersonOrganizations",
  >         "@set": [
  >             {
  >                 "name": null,
  >                 "id": null,
  >                 "person_fk": null,
  >                 "organization_fk": null
  >             }
  >         ]
  >     },
  >     "PersonGroups": {
  >         "@type": "PersonGroups",
  >         "@set": [
  >             {
  >                 "name": null,
  >                 "id": null,
  >                 "person_fk": null,
  >                 "group_fk": null
  >             }
  >         ]
  >     },
  >     "PersonInitiatives": {
  >         "@type": "PersonInitiatives",
  >         "@set": [
  >             {
  >                 "name": null,
  >                 "id": null,
  >                 "person_fk": null,
  >                 "initiative_fk": null
  >             }
  >         ]
  >     },
  >     "PersonTeams": {
  >         "@type": "PersonTeams",
  >         "@set": [
  >             {
  >                 "name": null,
  >                 "id": null,
  >                 "person_fk": null,
  >                 "team_fk": null
  >             }
  >         ]
  >     }
  > },
  > "AdditionalNames": {
  >     "@type": "AdditionalNames",
  >     "@set": [
  >         {
  >             "@type": "AdditionalName",
  >             "first_name": null,
  >             "last_name": null,
  >             "name_prefix": null,
  >             "name_suffix": null,
  >             "id": null,
  >             "person_fk": null,
  >             "middle_initial": null
  >         }
  >     ]
  > },
  > "AdditionalEmails": {
  >     "@type": "AdditionalEmails",
  >     "@set": [
  >         {
  >             "@type": "AdditionalEmail",
  >             "email": null,
  >             "id": null,
  >             "person_fk": null
  >         }
  >     ]
  > },
  > "AdditionalPostalAddresses": {
  >     "@type": "AdditionalPostalAddresses",
  >     "@set": [
  >         {
  >             "@type": "AdditionalPostalAddress",
  >             "address1": null,
  >             "address2": null,
  >             "city": null,
  >             "postal_code": null,
  >             "country": null,
  >             "country_code": null,
  >             "id": null,
  >             "person_fk": null,
  >             "state_territory_province": null
  >         }
  >     ]
  > },
  > "email": "joes-new-email@compliance-noreply.com",
  > "fullname": "Joe Smith",
  > "id": 30711
  > }
  > ```
  >
  > ### Updating Unordered Sets

* Updating \@set objects have **three** special rules.
* Add a new sub-object by supplying data to any property in any number of objects of \@type while leaving the id and fk parameters **null**.
* Change a sub-object instance by changing the property \(or properties\) without modifying the id or fk fields.
* Remove a sub-object instance by removing all the properties except for **\@type** and **id**.

  **Adding a Sub-Object**

  > This adds three additional AdditionalEmail objects into AdditionalEmails and the full Person object is returned with the id and fk for all sub-objects filled in.
  >
  > ```javascript
  > ...
  > "AdditionalEmails": {
  >  "@type": "AdditionalEmails",
  >  "@set": [
  >      {
  >          "@type": "AdditionalEmail",
  >          "email": "joe@personal-noreply.com",
  >          "id": null,
  >          "person_fk": null
  >      },
  >      {
  >          "@type": "AdditionalEmail",
  >          "email": "jsmith@compliance-noreply.com",
  >          "id": null,
  >          "person_fk": null
  >      },
  >      {
  >          "@type": "AdditionalEmail",
  >          "email": "js@compliance-noreply.com",
  >          "id": null,
  >          "person_fk": null
  >      }
  >  ]
  > },
  > ...
  > ```

### Changing a Sub-Object

> In this example, `jsmith@compliance-noreply.com` is changed to `jsmithCHANGED@compliance-noreply.com` and the full Person object is returned with the requested change.
>
> ```javascript
> ...
> "AdditionalEmails": {
>     "@type": "AdditionalEmails",
>     "@set": [
>         {
>             "@type": "AdditionalEmail",
>             "id": 256,
>             "email": "joe@personal-noreply.com",
>             "person_fk": 30711
>         },
>         {
>             "@type": "AdditionalEmail",
>             "id": 257,
>             "email": "jsmithCHANGED@compliance-noreply.com",
>             "person_fk": 30711
>         },
>         {
>             "@type": "AdditionalEmail",
>             "id": 258,
>             "email": "js@compliance-noreply.com",
>             "person_fk": 30711
>         }
>     ]
> },
> ...
> ```

### Removing a Sub-Object

> In this example, the sub-object with `id 258` is deleted by removing the properties and the full Person object is returned with the requested change.
>
> ```javascript
> ...
> "AdditionalEmails": {
>     "@type": "AdditionalEmails",
>     "@set": [
>         {
>             "@type": "AdditionalEmail",
>             "id": 256,
>             "email": "joe@personal-noreply.com",
>             "person_fk": 30711
>         },
>         {
>             "@type": "AdditionalEmail",
>             "id": 257,
>             "email": "jsmith@compliance-noreply.com",
>             "person_fk": 30711
>         },
>         {
>             "@type": "AdditionalEmail",
>             "id": 258
>         }
>     ]
> },
> ...
> ```
>
> ### Simultaneous Changes
>
> Note it is possible to add, change, and delete all at the same time and in any order and the full Person object is returned with the requested changes.
>
> In this example `id 256` is changed, `id 257` is deleted, and a `new record` is added.
>
> ```javascript
> ...
> "AdditionalEmails": {
>     "@type": "AdditionalEmails",
>     "@set": [
>         {
>             "@type": "AdditionalEmail",
>             "id": 256,
>             "email": "joeCHANGE2@personal-noreply.com",
>             "person_fk": 30711
>         },
>         {
>             "@type": "AdditionalEmail",
>             "id": 257
>         },
>         {
>             "@type": "AdditionalEmail",
>             "id": null,
>             "email": "jsmith-NEW@compliance-noreply.com",
>             "person_fk": null
>         }
>     ]
> },
> ...
> ```
>
> ### Special Note About `name_prefix` and `name_suffix`
>
> These values are integers based on IDs found in the Prefix and Suffix endpoints.

