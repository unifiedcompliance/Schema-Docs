# Currency Endpoints

> This document explains the methods you may use to work with the Currency endpoints in the Federated Authority Document database.

## Getting Currency

### Quick-start Knowledge

* The full JSON-LD Currency object is defined at [https://grcschema.org/Currency](https://grcschema.org/Currency).
* Getting a list of Currency objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Currency](https://grcschema.p.rapidapi.com/Currency) endpoint using a REST **GET**. Optional parameters may be provided to filter and paginate the result.

### Currency List GET

* Getting a list of Currency object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Currency](https://grcschema.p.rapidapi.com/Currency) endpoint using a REST **GET** with no optional parameters.
* Provides a list of all Currency objects **as Universal Stubs**.
* Pagination is provided for the list where `count` is the total quantity of objects in the data-set, `limit` is how many objects are returned in the current list, and `offset` is the first object in the set from that offset point. This is configurable in the request, but the default is a limit of 50 objects starting from offset 0.

> In the below example, with a limit of 2, page 1 starts from offset 0 with two values \(`limit`\). Page 2 starts from `offset`= 2. Page 3 from `offset`= 4, etc. There would be 5 pages to display the data - two objects at a time. This is illustrative only, and the actual local pages will depend on your limit and count.

```javascript
{
    "Pagination": [
        {
            "@context": "http://grcschema.org/",
            "@type": "Pagination",
            "count": 259,
            "limit": 2,
            "offset": 0
        }
    ],
    "@set": [
        {
            "@context": "http://grcschema.org/",
            "@type": "Stub",
            "id": 1,
            "property_name": "name",
            "property_value": "The grapheme for the space character",
            "thing_type": "Currency"
        },
        {
            "@context": "http://grcschema.org/",
            "@type": "Stub",
            "id": 2,
            "property_name": "name",
            "property_value": "The grapheme for the exclamation mark character",
            "thing_type": "Currency"
        }
    ]
}
```

### Currency List GET \(filtered\)

* Getting a filtered list of Currency objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Currency/](https://grcschema.p.rapidapi.com/Currency/) endpoint using a REST **GET** with url parameters.
* These are the parameters you can optionally supply to the filter. These fields work as a logical AND.

| Field | Description |
| :--- | :--- |
| name | Filters by Currency name |
| search | Searches across all searchable fields. |
| sort\_dir | 0 = descending, 1 = ascending |
| limit | Combined with offset, provides pagination by limiting results. |
| offset | Combined with limit, provides pagination by shifting the first record. |

### Currency GET \(by ID\)

* Getting a single Currency object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Currency/:id](https://grcschema.p.rapidapi.com/Currency/:id) endpoint using a REST **GET**.

