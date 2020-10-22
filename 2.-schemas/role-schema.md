# § 2.3 Role Schema

A role is a set of responsibilities defined in a process and assigned to a person or team. In this instance, ISO 19770-8, NISTIR 8278, and the UCF have employed schemas depicting roles for contributors. The UCF’s schema is more advanced than the other two in that it’s particular schema calls for three levels of contributors during the mapping process:

* **Mapper**: the initial contributor for the content;
* **Reviewer**: the person who follows the same steps as the Mapper and either accepts the Mapper’s outcome or disputes it; and the
* **Approver**: who is the person who follows the Reviewer and either accepts the joint outcome or disputes it.

In future versions, the Roles table might be expanded to accommodate the research listed [HERE](https://short.grcschema.org/DagT9T).

## § 2.3 Role

This defines additional attributes or permissions assigned to a Person.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| name | String | The name of the item. |
| id | Integer | A unique and persistent identifier for the record. |
| description | Text | This describes a Thing or Property. |
| CoreMetaData | Thing | Metadata documenting the ID and core information about a JSON Thing. |
| RoleStructure | Thing | This defines Role specific structures. |

Because some role definitions are more involved than others, we’ve included a sub-element of RoleStructure as well.

### § 2.3.1 RoleStructure

This defines Role specific structures.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| deprecated\_by | Integer or Null | This is the id of the Person that deprecated this item. |
| deprecated\_notes | Text or Null | This is notes about the deprecated item. |
| position\_type | String or Null | This is the position type of the Role. |
| reports\_to\_id | Integer or Null | This is the id of the Person this Role reports to. |
| dotted\_line\_reports\_to\_id | Integer or Null | This is the id of the Person this Role reports to directly. |

