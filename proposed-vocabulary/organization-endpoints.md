# Organization Endpoints

> This document explains the methods you may use to work with the Organization endpoints in the Federated Authority Document database.

## GET Organization Endpoints

### Quick-start Knowledge

* The full JSON-LD Organization object is defined at [https://grcschema.org/Organization](https://grcschema.org/Organization).
* Getting a list of Person object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Organization](https://grcschema.p.rapidapi.com/Organization) endpoint using a REST **GET**. Optional parameters may be provided to filter and paginate the result.
* Getting a single Organization object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Organization/:id](https://grcschema.p.rapidapi.com/Organization/:id) endpoint using a REST **GET**.

### Get Organization (basic)

* Getting a list of Organization object stubs from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Organization](https://grcschema.p.rapidapi.com/Person) endpoint using a REST **GET** with no optional parameters.
* Provides a list of all Organization objects as stubs. Stubs show the `property_name` and `property_value` targeted by the stub.
* Pagination is provided for the list where `count` is the total quantity of objects in the data-set, `limit` is how many objects are returned in the current list, and `offset` is the first object in the set from that offset point. This is configurable in the request, but the default is a limit of 50 objects starting from offset 0.

> In the below example, with a limit of 2, page 1 starts from offset 0 with two values (`limit`). Page 2 starts from `offset`= 2. Page 3 from `offset`= 4, etc. There would be 5 pages to display the data - two objects at a time. This is illustrative only, and the actual local pages will depend on your limit and count.

```json

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
