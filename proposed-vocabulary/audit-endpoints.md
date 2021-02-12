# AuditData Endpoints

> This document explains the methods you may use to work with the AuditData endpoints in the Federated Authority Document database.

## Getting AuditData

### Quick-start Knowledge

* The full JSON-LD AuditData object is defined at [https://grcschema.org/AuditData](https://grcschema.org/AuditData).
* Getting a list of AuditData objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/AuditData](https://grcschema.p.rapidapi.com/AuditData) endpoint using a REST **GET**. Optional parameters may be provided to filter and paginate the result.

### AuditData List GET

* Getting a list of AuditData object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/AuditData](https://grcschema.p.rapidapi.com/AuditData) endpoint using a REST **GET** with no optional parameters.
* Provides a list of all AuditData objects.
* Pagination is provided for the list where `count` is the total quantity of objects in the data-set, `limit` is how many objects are returned in the current list, and `offset` is the first object in the set from that offset point. This is configurable in the request, but the default is a limit of 50 objects starting from offset 0.

> In the below example, with a limit of 2, page 1 starts from offset 0 with two values \(`limit`\). Page 2 starts from `offset`= 2. Page 3 from `offset`= 4, etc. There would be 5 pages to display the data - two objects at a time. This is illustrative only, and the actual local pages will depend on your limit and count.

```javascript
{
    "Pagination": [
        {
            "@context": "http://grcschema.org/",
            "@type": "Pagination",
            "count": 44,
            "limit": 2,
            "offset": 0
        }
    ],
    "@set": [
        {
            "@context": "http://grcschema.org/",
            "@type": "AuditData",
            "id": 73,
            "endpoint": "Person",
            "object_id": 30824,
            "person_fk": 30824,
            "organization_fk": null,
            "team_fk": null,
            "type": "POST",
            "provider_data": {
                "x-real-ip": "72.193.74.52",
                "x-forwarded-for": "72.193.74.52, 72.193.74.52",
                "host": "grcschema.org:3002",
                "connection": "close",
                "content-length": "1216",
                "accept": "*/*",
                "accept-encoding": "deflate, gzip",
                "content-type": "application/json",
                "usequerystring": "1",
                "user-agent": "FileMaker/19.2",
                "x-rapidapi-host": "grcschema.p.rapidapi.com",
                "x-requester-person": "0",
                "x-forwarded-port": "443",
                "x-forwarded-proto": "https",
                "x-mashape-version": "1.2.7",
                "x-rapidapi-version": "1.2.7",
                "x-mashape-user": "unified-compliance-unified-compliance-default",
                "x-mashape-subscription": "CUSTOM-PowerUser",
                "x-rapidapi-user": "unified-compliance-unified-compliance-default",
                "x-rapidapi-subscription": "CUSTOM-PowerUser"
            },
            "previous_object": null,
            "current_object": {
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
                    "date_created": "2021-02-01",
                    "date_modified": "2021-02-01",
                    "created_audit_id": null,
                    "modified_audit_id": null,
                    "live_status": null,
                    "checksum": 0,
                    "validated": 0
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
                            "id": 500,
                            "email": "jtdoolitle@doolitle.org",
                            "person_fk": 30824,
                            "organization_fk": null,
                            "primary": 1,
                            "local_reference_id": null
                        }
                    ]
                },
                "Names": {
                    "@type": "Names",
                    "@set": [
                        {
                            "@type": "Name",
                            "id": 649,
                            "first_name": "James",
                            "last_name": "Doolitle",
                            "name_prefix_fk": 21,
                            "name_suffix_fk": 19,
                            "person_fk": 30824,
                            "middle_initial": "T",
                            "primary": 1,
                            "local_reference_id": null
                        }
                    ]
                },
                "email": "jtdoolitle@doolitle.org",
                "fullname": "Dr. James T Doolitle Esquire",
                "id": 30824
            },
            "timestamp": "2021-02-01T14:18:40.000Z"
        },
        {
            "@context": "http://grcschema.org/",
            "@type": "AuditData",
            "id": 74,
            "endpoint": "Person",
            "object_id": 30825,
            "person_fk": 38,
            "organization_fk": null,
            "team_fk": null,
            "type": "POST",
            "provider_data": {
                "x-real-ip": "85.76.162.25",
                "x-forwarded-for": "85.76.162.25, 85.76.162.25",
                "host": "grcschema.org:3002",
                "connection": "close",
                "content-length": "423",
                "accept": "*/*",
                "accept-encoding": "gzip, deflate, br",
                "cache-control": "no-cache",
                "content-type": "application/json",
                "cookie": "grcapi=s%3AVp5V0pyofLbATnFZSXOxZsc1szArsot4.IvNlW9hnu8Ox0Gk%2FLaX3IrQai8rWVU%2B0xX4lAeOTEVs",
                "postman-token": "f48c5aae-b058-4564-8760-a95bc9229567",
                "user-agent": "PostmanRuntime/7.26.8",
                "x-requester-person": "38",
                "x-forwarded-port": "443",
                "x-forwarded-proto": "https",
                "x-mashape-version": "1.2.7",
                "x-rapidapi-version": "1.2.7",
                "x-mashape-user": "unified-compliance-unified-compliance-default",
                "x-mashape-subscription": "CUSTOM-PowerUser",
                "x-rapidapi-user": "unified-compliance-unified-compliance-default",
                "x-rapidapi-subscription": "CUSTOM-PowerUser"
            },
            "previous_object": null,
            "current_object": {
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
                    "date_created": "2021-02-02",
                    "date_modified": "2021-02-02",
                    "created_audit_id": null,
                    "modified_audit_id": null,
                    "live_status": null,
                    "checksum": 0,
                    "validated": 0
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
                            "id": 501,
                            "email": "jsmith@no-reply.org",
                            "person_fk": 30825,
                            "organization_fk": null,
                            "primary": 1,
                            "local_reference_id": null
                        }
                    ]
                },
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
                            "local_reference_id": null
                        }
                    ]
                },
                "email": "jsmith@no-reply.org",
                "fullname": "John Smith",
                "id": 30825
            },
            "timestamp": "2021-02-02T14:21:07.000Z"
        }
    ]
}
```

### AuditData List GET \(filtered\)

* Getting a filtered list of AuditData objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/AuditData/](https://grcschema.p.rapidapi.com/AuditData/) endpoint using a REST **GET** with url parameters.
* These are the parameters you can optionally supply to the filter. These fields work as a logical AND.

| Field | Description |
| :--- | :--- |
| object\_id | Filters by object\_id. \(both creation and changes\) |
| person\_id | Filters by the person id. \(both creation and changes\) |
| organization\_id | Filters by the organiation id. \(Future Use\) |
| team\_id | Filters by the team id. \(Future Use\) |
| type | Filters by the type of the modification. \(e.g. POST, PATCH\) |
| endpoint | Filters by the API endpoint. \(e.g. Person, Organization\) |
| search | Searches across all searchable fields. |
| sort\_dir | 0 = descending, 1 = ascending |
| limit | Combined with offset, provides pagination by limiting results. |
| offset | Combined with limit, provides pagination by shifting the first record. |

### AuditData GET \(by ID\)

* Getting a single AuditData object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/AuditData/:id](https://grcschema.p.rapidapi.com/AuditData/:id) endpoint using a REST **GET**.

