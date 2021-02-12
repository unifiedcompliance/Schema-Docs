# Character Endpoints


> This document explains the methods you may use to work with the Character endpoints in the Federated Authority Document database.

## Getting Character

### Quick-start Knowledge

* The full JSON-LD Character object is defined at [https://grcschema.org/Character](https://grcschema.org/Character).
* Getting a list of Character objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Character](https://grcschema.p.rapidapi.com/Character) endpoint using a REST **GET**. Optional parameters may be provided to filter and paginate the result.

### Character List GET

* Getting a list of Character object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Character](https://grcschema.p.rapidapi.com/Character) endpoint using a REST **GET** with no optional parameters.
* Provides a list of all Character objects.
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
            "@type": "Character",
            "CoreMetaData": {
                "@type": "CoreMetaData",
                "date_created": "2020-06-16",
                "date_modified": "2021-01-18",
                "created_by": null,
                "modified_by": null,
                "live_status": 1,
                "checksum": 5,
                "validated": true
            },
            "id": 1,
            "char": " ",
            "binary": "100000",
            "dec": "32",
            "definition": "The grapheme for the space character. It is represented by the following codes: Unicode U+0020; Dec 32; Hex 20; HTML &#32. When creating a URL this character should be replaced with \"%20\". When entering dictionary terms, replace this character with the unicode character \"_\" (U+005F).",
            "html": "&#32;",
            "hex": "20",
            "unicode": "U+0020"
        },
        {
            "@context": "http://grcschema.org/",
            "@type": "Character",
            "CoreMetaData": {
                "@type": "CoreMetaData",
                "date_created": "2020-06-16",
                "date_modified": "2021-01-18",
                "created_by": null,
                "modified_by": null,
                "live_status": 1,
                "checksum": 5,
                "validated": true
            },
            "id": 2,
            "char": "!",
            "binary": "100001",
            "dec": "33",
            "definition": "The grapheme for the exclamation mark character. It is represented by the following codes: Unicode U+0021; Dec 33; Hex 21; HTML &#33. When creating a URL this character should be replaced with \"%21\". This character is compatible with all known dictionary entries.",
            "html": "&#33;",
            "hex": "21",
            "unicode": "U+0021"
        }
    ]
}
```

### Character List GET \(filtered\)

* Getting a filtered list of Character objects from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Character/](https://grcschema.p.rapidapi.com/Character/) endpoint using a REST **GET** with url parameters.
* These are the parameters you can optionally supply to the filter. These fields work as a logical AND.

| Field | Description |
| :--- | :--- |
| name | Filters by Character name |
| search | Searches across all searchable fields. |
| sort\_dir | 0 = descending, 1 = ascending |
| limit | Combined with offset, provides pagination by limiting results. |
| offset | Combined with limit, provides pagination by shifting the first record. |

### Character GET \(by ID\)

* Getting a single Character object from the Federated Authority Document Database is accomplished by querying the [https://grcschema.p.rapidapi.com/Character/:id](https://grcschema.p.rapidapi.com/Character/:id) endpoint using a REST **GET**.
