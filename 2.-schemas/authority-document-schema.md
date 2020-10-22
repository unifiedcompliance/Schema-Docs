# § 2.5 Authority Document Schema

When we say that we are “complying”, we are saying that we are complying with authoritative rules that are not of our own creation. These authoritative rules can come in the form of regulations, principles, standards, guidelines, best practices, policies, and procedures. Collectively, these are called **Authority Documents** within this schema. For the purposes of this standard, we will refrain from a full discussion, especially since there is a wealth of information about what Authority Documents are that can be found online [HERE](https://short.grcschema.org/OyytRN).

To "catalog" a book or other form of library material involves several interrelated processes which all contribute to the achievement of Charles Ammi Cutter’s “objects” for a catalog[\[1\]]():

* To enable a person to find a book of which the author, title, or subject is known;
* To show what the library has by a given author, on a given subject, or in a given kind of literature; and
* To assist in the choice of a book.

Thus, catalogers prepare a description of the Authority Document, assign subject headings, determine a classification system, provide a link to the electronic item, and code that information with both metadata so that it may be displayed in online catalogs.

When analyzing current schemas, the only catalog, per se, is that provided by the UCF’s Common Controls Hub, and STIGViewer.com. However, the UCF’s current catalog structure doesn’t account for all the various Authority Document types and reference structures necessary. Therefore, the catalog structure has been expanded with the help from the folks at Zotero to include various forms of documents:

* Authority Documents
* eBook from a Bookseller \(Kindle, iBooks\)
* eBook from a database
* eBook from a Website
* Journal Article from a database
* Journal Article from Website
* Secure Technical Implementation Guides
* OSCAL

## § 2.5 AuthorityDocument

A document duly adopted implementing the powers, functions, and activities of an Authority.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| ADMapping | Thing | Relating AD to mapping Team. |
| ADStructure | Thing | This defines Authority Document specific structures. |
| Authors | Thing | A collection of Authors. |
| availability | String | The Authority Document availability. |
| blog\_title | String | The title of the blog the document was found on. |
| citation\_format | String | The Authority Document citation format. |
| CommonNames | Thing | A collection of CommonName. |
| CoreMetaData | Thing | Metadata documenting the ID and core information about a JSON Thing. |
| description | Text | This describes a Thing or Property. |
| di\_fk | Integer or Null | This is the id of the DI \(Dictionary ID\) |
| Editors | Thing | A collection of Editors. |
| effective\_date | Date | The effective date of the document |
| HierarchicalMetaData | Thing | MetaData about a JSON Type's hierarchical information. If the record is in a non-hierarchical array this will be nulled. |
| id | Integer | A unique and persistent identifier for the record. |
| Identifiers | Thing | These are unique points of reference for the document. |
| language | String or Null | A system of communication used by a particular country. |
| official\_name | String | The official name of the document. |
| Originator | Thing | The company/entity that created the Authority Document. |
| pages | Integer | The total number of pages in the document. |
| parent\_category | Integer | The category of the parent record in the document's hierarchy. |
| periodical\_title | String | The title of the periodical that the document was found in. |
| publication\_place | String | Where the document was published if that is known. |
| published\_date | Date | The date an item was published. |
| published\_name | String | The published name of the document. |
| published\_version | String | The published version of the document. |
| request\_id | String | The Authority Document request id. |
| SubjectMattersStub | Thing | Stub response for Subject Matters. |
| subtitle | String | The subtitle of the document. |
| supercede\_id | Integer | The Authority Document id that will supercede. |
| type | String | The Authority Document type. |
| url | URL | The Uniform Resource Locator of an internet address. |
| volume\_issue | String | The volume or issue identifier of the periodical that the document was found in. |
| website\_publisher | String | The website publisher's name the document was found on. |
| website\_title | String | The title of the website itself and not to be confused with the title of the publisher. |

### § 2.5.1 ADMapping

Information related to which team mapped the Authority Document, when it became available, and how to find it in that system.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| authority\_document\_fk | Integer | Authority document foreign key. |
| id | Integer | A unique and persistent identifier for the record. |
| license\_info | URL | The license information of the document. |
| release\_date | Date | The Authority Document release date. |
| status | String | This item status. |
| Team | Thing | The Mapping team on a project. |
| url | URL | The Uniform Resource Locator of an internet address. |

### § 2.5.1.1 Team

Information specifically about the team involved in the AD Mapping.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| id | Integer | A unique and persistent identifier for the record. |
| admapping\_fk | Integer | Authority Mapping foreign key. |
| Member | Thing | A Team Member. |

### § 2.5.1.1.1 Member

Information about each team member that participated in the mapping project.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| organization | String | The Organization a member belongs to. |
| role | String | The Role a member belongs to. |
| organization\_id | Integer | Organization id. |
| person\_id | Integer | ID of a user/person. |
| role\_id | Integer | Role id. |
| person\_name | String | The full name of a Person. |
| team\_id\_fk | Integer | The reference id of a Team. |

### § 2.5.2 ADStructure

This defines Authority Document specific structures.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| deprecated\_by | Integer or Null | This is the id of the Person that deprecated this item. |
| deprecated\_notes | Text or Null | This is notes about the deprecated item. |

### § 2.5.2 Authors

A collection of Authors.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| authority\_document\_fk | Integer | Authority document foreign key. |
| email | Email or Null | Electronic Mail address. |
| first\_name | Text | The person's first name. |
| last\_name | Text | The person's last name. |
| organization\_id | Integer |  |
| person\_id | Integer | A unique and persistent identifier for the record. |

### § 2.5.3 CommonNames

A collection of common names, or simplified names that an Authority Document might be searched by.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| name | String | The name of the item. |
| id | Integer | A unique and persistent identifier for the record. |

### § 2.5.4 Editors

A collection of Editors.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| email | Email or Null | Electronic Mail address. |
| first\_name | Text | The person's first name. |
| last\_name | Text | The person's last name. |
| person\_id | Integer | A unique and persistent identifier for the record. |
| organization\_id | Integer |  |
| authority\_document\_fk | Integer | Authority document foreign key. |

### § 2.5.5 Identifiers

These are unique points of reference for finding the original document.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| id | Integer | A unique and persistent identifier for the record. |
| search\_information | String | This is database search information for finding the record. |
| doi | String | The Digital Object Identifier record locator. |
| database | String | The database that houses the record. |
| date\_accessed | String | The date the record was last accessed. |
| isbn | String | The ISBN number for the record. |
| uuid | String | The Unique ID of the record in a database system. |
| epub\_type | String | The type of electronic publication this was found in. |
| publisher\_promulgator\_organizations\_id\_fk | Integer | The publisher id of the document or in the case of laws the promulgator of the document. |
| authority\_document\_fk | Integer | Authority document foreign key. |

### § 2.5.6 SubjetMatterStub

Stub response for Subject Matters.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| authority\_document\_fk | Integer | Authority document foreign key. |
| sm\_id | Integer | Subject Matter Id. |
| sm\_name | String | Subject Matter name. |

1.  \(Cutter 1876\) [↑]()

