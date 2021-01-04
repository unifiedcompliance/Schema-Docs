# 2021 Development Cycle

Following the content guidance from the various Authority Documents[1](), contribution through a centralized API roughly follows the data model shown below:

![](.gitbook/assets/federated-mapping%20%281%29.png)

## Breaking the data model down

For clarity, we will break the data model into its constituent parts, describing how a contribution would take place.

1. A **Person** who is
2. part of an **Organization** is
3. assigned a **Role** of contributor \(Author, Mapper, etc.\)
4. as part of a **Project** that contains an
5. **Authority Document** \(or as NIST OSCAL calls it a _catalog_\) that has various
6. **Citations** \(or SWID entries, or catalog entries, or reference elements\) that have identified
7. **Dictionary Terms** \(such as product names, tagged nouns or verbs\) and a possible match to a
8. **Reference Control** \(or focus control or Common Control\).

We will call this continuous process an **entry**.

A catalog of the following will be queryable via API:

* **Authority Documents** and **entries**,
* **organizations**, and
* **contributors** \(and associated persons\)

Furthermore, the API will allow **disambiguated persons** from **disambiguated organizations** to create entries.

In order to build out this data model and ensure that it works through a publicly published API, five steps need to be completed for each schema in the data model:

1. A schema will be proposed for comment.
2. The schema will be publicly distributed and discussion will be requested.
3. When the discussion has reached its logical conclusion, the schema will be voted on and locked.
4. Once the schema is locked, API building and testing will be undertaken, with alpha and beta versions of the API made available for testing and discussion.
5. When the discussion has reached its logical conclusion, the API’s possible versions will be voted on and locked. Once locked it will be made publicly available.

![Steps](https://d1qmdf3vop2l07.cloudfront.net/dear-squash.cloudvent.net/compressed/_min_/7e986ca26895da60482100920eca3e32.png)

This can be accomplished in a stair-step manner wherein we build out the schema and APIs from their logical progression as listed in the contribution scenario above. Once a schema has been voted on and locked, the next schema in the logical progression can be proposed.

![Development Cycle Proposal](https://d1qmdf3vop2l07.cloudfront.net/dear-squash.cloudvent.net/compressed/_min_/ad8876d3116894f99319311a72967ef1.png)

