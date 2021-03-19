# Managing Organizations

All wireframes for this portion of the Compliance as Code project are available at:

[https://balsamiq.cloud/srj76i4/p8qqe69](https://balsamiq.cloud/srj76i4/p8qqe69)

The scope of this portion of the project is to allow _the administrator_ of a known account and to fill out additional information about the account assigned to the Organization.

Much of the information about the organization will be derived from the initial sign-up process. During the sign-up process, we query Clearbit and other APIs to glean information about the organization. That information is then returned through the API and should be displayed in the various fields.

## Schema

The schema for an organization is listed here: [http://grcschema.org/Organization](http://grcschema.org/Organization).

The ERD for working with an organization looks like the diagram that follows:

![Organization ERD](../../.gitbook/assets/0%20%289%29.png)

## Navigation

Main navigation for Organization is accessed by the group icon \(1\) as shown in the following diagram.

Within the Organization section of the shell, sub-navigation must include capabilities to switch between _this account_, _this organization_, and _all organizations_ \(2\).

![Organization subnavigation](../../.gitbook/assets/1%20%287%29.png)

## Basic Info

Basic information for the organization should already exist from the Clearbit and other queries that were performed when the organization was created.

![Basic Info](../../.gitbook/assets/2%20%287%29.png)

1. **Core Metadata** should exist and is automatically created.

2. **Legal Name** will exist _if Clearbit data was found_.

3. **Names** – this is an array for additional names. Additional names can be added to manually or they can be removed.

4. **Social Addresses** – these will exist if they were found in Clearbit data. If not, they can be manually added.

5. **Organizational Hierarchy** – A parent organization can be selected _from existing organizations_. Any child of _this_ organization will be listed in the subsidiary list.

## Classification

For _now_, classification is automatically applied via the returned information from Clearbit and others. _At some time in the future_ we will create APIs for getting classification information for an organization.

![Classification information](../../.gitbook/assets/3%20%286%29.png)

## Social Addresses

_Some_ information about social addresses will be returned by Clearbit and others. The rest can be added manually.

![Social Information](../../.gitbook/assets/4%20%287%29.png)

1. **Email Addresses** – only addresses _from the same domain as the organization, or those in the domains list_ can be added to the Email Address array. They can be removed at will.

2. **Telephone Numbers** – can be manually added or removed at will.

3. **Domains** – can be added and removed at will.

## Postal Addresses

The primary postal address was already created during the sign-up process. It can be changed here, as well as any additional addresses can be added here.

![Postal addresses](../../.gitbook/assets/5%20%284%29.png)

When filled out, they must be filled out in the order of _country_, _state_, _city_, and then the rest of the information. This is because _country_, _state_, and _city_ are all pop-ups, one deriving its list from the other.

1. **Country** **API** – [https://short.grcschema.org/API-Country List](https://short.grcschema.org/API-Country%20List)

2. **State API** - [https://short.grcschema.org/API-State List](https://short.grcschema.org/API-State%20List3)

[3](https://short.grcschema.org/API-State%20List3). **City API** - [https://short.grcschema.org/API-City List](https://short.grcschema.org/API-City%20List)

## Members

This is a listing of members. Members are added/managed through the Staff layout. Members can be navigated to by clicking on their name.

![Members](../../.gitbook/assets/6%20%281%29.png)

