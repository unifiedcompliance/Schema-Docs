# Managing Groups

All wireframes for this portion of the Compliance as Code project are available at:

[https://balsamiq.cloud/srj76i4/pmjrirq](https://balsamiq.cloud/srj76i4/pmjrirq)

The scope of this portion of the project is to allow _the administrator_ of a known account and to fill out additional information about the groups assigned to the organization and to other organizations.

When filling out information about the _local_ groups _assigned to an account_, nothing will be filled out. For those Groups that are public, mof the information about the organization will be derived from the initial sign-up process. During the sign-up process, we query Clearbit and other APIs to glean information about the organization. That information is then returned through the API and should be displayed in the various fields.

## Schema

The schema for a group is listed here: [http://grcschema.org/](http://grcschema.org/Group)[Group](http://grcschema.org/Group).

The ERD for working with a group looks like the diagram that follows:

![Group ERD](../../.gitbook/assets/0%20%287%29.png)

## Navigation

Main navigation for group is accessed _below_ the group icon \(1\) as shown in the following diagram.

Within the group section of the shell, sub-navigation must include capabilities to switch between _this account’s groups_ and _all groups_ \(2\).

![Group subnavigation](../../.gitbook/assets/1%20%285%29.png)

## Basic Info

Basic information for the group will _only_ exist from the Clearbit and other queries that were performed when the group was created _if_ this is a public group and not a group associated with an account.

![Basic Info](../../.gitbook/assets/2%20%285%29.png)

1. **Core Metadata** should exist and is automatically created.

2. **Legal Name** will exist _if Clearbit data was found_. If not, this should be disabled as account-related groups do not have a legal name.

3. **Names** – this is an array for additional names. Additional names can be added to manually or they can be removed _for public groups_. Account-related groups are allowed _only a single name_.

4. **Social Addresses** – these will exist if they were found in Clearbit data. If not, they can be manually added or removed _for public groups_. Account-related groups _do not have social addresses_ and therefore this should be disable for them.

5. **Organizational Hierarchy** – How this is handled is different for public and account-related groups.

* For public groups, a parent group can be selected _from existing public groups or organizations_.
* For account-related groups, a parent group can be selected _from existing account-related groups_.

Any child of _this_ organization will be listed in the subsidiary list.

## Character

_This only applies to account-related groups_. This should be disabled for public groups.

![Group Character](../../.gitbook/assets/3%20%285%29.png)

1. **Group Character settings** – these are options settings wherein the user selects a number from 1 to 10 for each of the four characterizations. Selections from 1-5 will create a _formal_ setting and 6-10 will create an _informal_ setting. There are images associated with each of the formal and informal settings for each of the four characterizations.

2. **Organizational Character Index** – this is an optional field to be filled out for the _the account_. If it was filled out at the account level, that information will show up here.

## Social Addresses

_Some_ information about social addresses will be returned by Clearbit and others _if this is a public group_. The rest can be added manually _for public groups only_. If this is an account-related group _this should be disabled._

![Social Information](../../.gitbook/assets/4%20%285%29.png)

1. **Email Addresses** – only addresses _from the same domain as the organization, or those in the domains list_ can be added to the Email Address array. They can be removed at will.

2. **Telephone Numbers** – can be manually added or removed at will.

3. **Domains** – can be added and removed at will.

## Postal Addresses

The primary postal address was already created during the sign-up process _if this is a public group_. The rest can be added manually _for public groups only_. If this is an account-related group _this should be disabled._

![Postal addresses](../../.gitbook/assets/5%20%283%29.png)

When filled out, they must be filled out in the order of _country_, _state_, _city_, and then the rest of the information. This is because _country_, _state_, and _city_ are all pop-ups, one deriving its list from the other.

1. **Country** **API** – [https://short.grcschema.org/API-Country List](https://short.grcschema.org/API-Country%20List)

2. **State API** - [https://short.grcschema.org/API-State List](https://short.grcschema.org/API-State%20List3)

[3](https://short.grcschema.org/API-State%20List3). **City API** - [https://short.grcschema.org/API-City List](https://short.grcschema.org/API-City%20List)

## Members

This is a listing of members. Members are added/managed through the Staff layout. Members can be navigated to by clicking on their name.

![Group Members](../../.gitbook/assets/6%20%282%29.png)

