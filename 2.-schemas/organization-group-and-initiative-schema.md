# § Organization, Group, and Initiative Schema

NISTIR 8278, SWID documentation, and the UCF all have schema identifiers for content contributors as organizations. However, in further research, we have found that there is a slight difference between organizations, groups, and initiatives that have all created content. Here are the working definitions we are using to differentiate between them on this standard:

* **Organization**: A legal entity with both a headquarters and online domain with a particular purpose, especially a business, society, association, etc.
* **Group**: A formalized collection of people acting in accord with each other without forming a legal entity in and of itself. A Group can be a stand-alone group, or it can be a part of an Organization.
* **Initiative**: A formalized collection of people acting in accord with each other without forming a legal entity in and of itself _brought together for a specific purpose and a limited timeframe_. An Initiative is always a a part of an Organization or a part of a Group.

As such, the standard is designed to allow the same structure for all three described above.

## § 2.4 Organization, Group, and Initiative

The defining characteristics of an organization, group, or initiative are shown below. Some of this information will be automatically verified and updated through a collaboration with Clearbit.

| **Property** | **Expected Type** | **Description** | **Clearbit** |
| :--- | :--- | :--- | :--- |
| AdditionalDomains | Thing | Additional domain names used by an Organization. | Yes |
| CoreMetaData | Thing | Metadata documenting the ID and core information about a JSON Thing. |  |
| description | Text | This describes a Thing or Property. | Yes |
| domain | String | Legally registered internet domain name of Organization. |  |
| email | Email or Null | Electronic Mail address. |  |
| EmailAddresses | Thing | A collection of EmailAddress. |  |
| founded | Integer or Null | The year an Organization was founded. | Yes |
| id | Integer | A unique and persistent identifier for the record. |  |
| Locations | Thing | A collection of addresses. | Yes |
| legal\_name | String | The name of the item. | Yes |
| NonStandardNames | Thing | Additional legal names used by an item. |  |
| organization\_type | Integer | This differentiates between a 1 - Organization, 2- Group, 3- Initiative. |  |
| OrganizationCategory | Thing | The category an Organization belongs to which includes additional characteristics. | Yes |
| parent\_id | Integer | ID of the associated parent for this record. | Yes |
| phone\_number | TelephoneNumber | The main phone number registered to an Organization. |  |
| PhoneNumbers | Thing | A collection of phone numbers. | Yes |
| PostalAddress | Thing or Null | The address to which physical mail and packages are delivered. | Yes |
| SocialAddresses | Thing or Null | The various Internet locations that help disambiguate a person, such as their FaceBook, LinkedIn, YouTube and Twitter Address. | Yes |

### § 2.4.1 AdditionalDomains

Additional domain names used by an organization, group, or initiative.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| id | Integer | A unique and persistent identifier for the record. |
| domain | String | Legally registered internet domain name of Organization |
| organization\_fk | Integer | Organization foreign key |

### § 2.4.2 EmailAddresses

A collection of email addresses.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| email | Email or Null | Electronic Mail address. |
| id | Integer | A unique and persistent identifier for the record. |
| organization\_fk | Integer | Organization foreign key |

### § 2.4.3 Locations

A collection of addresses.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| address1 | String | The first part of a postal address such as the building number and street name |
| address2 | String or Null | The second part of a postal address, usually denoting a suite. |
| city | String | The city the address is located in. |
| state | String | The state/province for the address. |
| postal\_code | String | The postal/zip code for the address. |
| country | String | The country the address is located in. |
| id | Integer | A unique and persistent identifier for the record. |
| country\_code | String | This is a geographical code that represent countries. |
| organization\_fk | Integer | Organization foreign key |

### § 2.4.4 OrganizationCategory

The category an Organization belongs to which includes additional characteristics.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| industry | String or Null | This is the industry an Organization belongs to. |
| industry\_group | String or Null | A group of Organization industries. |
| naics\_code | Integer or Null | This is the North American Industry Classification System code assigned to an Organization. |
| sector | String or Null | A distinct area an Organization operates in. |
| sic\_code | Integer or Null | This is the Standard Industrial Classification code assigned to an Organization. |
| sub\_industry | String or Null | A subset of Organization industries. |
| Tags | Thing | These are keywords that describes an item. |
| unspsc\_code | Integer or Null | The United Nations Standard Products and Services code of an Organization. |

### § 2.4.5 PhoneNumbers

A collection of phone numbers.

| **Property** | **Expected Type** | **Description** |
| :--- | :--- | :--- |
| id | Integer | A unique and persistent identifier for the record. |
| organization\_fk | Integer | Organization foreign key. |
| phone\_number | TelephoneNumber | The main phone number registered to an Organization. |

