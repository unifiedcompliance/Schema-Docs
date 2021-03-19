# Managing Accounts

All wireframes for this portion of the Compliance as Code project are available at:

[https://balsamiq.cloud/srj76i4/ple67oc](https://balsamiq.cloud/srj76i4/ple67oc)

The scope of this portion of the project is to allow _the administrator_ of a known account and to fill out additional information about the account assigned to the Organization.

The layouts expressed in this documentation are for _communication purposes only_. They are not meant to provide branding guidance or even an official look-and-feel. They exist merely to convey the technical aspects of the project. _Real_ designers will create something much more effective.

## Schema

The schema for an account is found in multiple locations:

* [http://grcschema.org/Account](http://grcschema.org/Account), which provides the core schema for an account; and
* [http://grcschema.org/Organization](http://grcschema.org/Organization), which provides the schema for the domain to organization match.

The ERD for working with an account looks like the diagram that follows:

![Account ERD](../../.gitbook/assets/0%20%286%29.png)

## Navigation

Main navigation for accounts, organizations, groups, etc. is accessed by the Group icon \(1\) as shown in the following diagram.

Within the Person section of the shell, sub-navigation must include capabilities to switch between _this_ account, _the account’s organization_, and all organizations \(2\).

![Account subnavigation](../../.gitbook/assets/1%20%288%29.png)

## Basic Info

Basic information for the account isn’t much. Just the account name \(which should already exist\), the meta data \(which also should exist\), and the optional description and telephone numbers.

![Account Basic Info](../../.gitbook/assets/2%20%286%29.png)

### Deleting the account

An account can only be deleted once _all_ of the members of the account have been deleted _except_ for the administrator. Once the account has been deleted, the administrator of the account will also be deleted.

Therefore, if there are still members of the account that are active, a dialog should warn the administrator that the users will be deleted _only after notifying the users_ that they will be deleted so that those users can approve or disapprove their deletion.

If _any_ user disapproves of being deleted, the _account cannot be deleted_.

## Postal Addresses

The primary postal address was already created during the sign-up process. It can be changed here, as well as any additional addresses can be added here.

![Postal addresses](../../.gitbook/assets/3%20%288%29.png)

When filled out, they must be filled out in the order of _country_, _state_, _city_, and then the rest of the information. This is because _country_, _state_, and _city_ are all pop-ups, one deriving its list from the other.

1. **Country** **API** – [https://short.grcschema.org/API-Country List](https://short.grcschema.org/API-Country%20List)

2. **State API** - [https://short.grcschema.org/API-State List](https://short.grcschema.org/API-State%20List3)

[3](https://short.grcschema.org/API-State%20List3). **City API** - [https://short.grcschema.org/API-City List](https://short.grcschema.org/API-City%20List)

## Members

This is a listing of members. Members are added/managed through the Staff layout. Members can be navigated to by clicking on their name.

![Members](../../.gitbook/assets/4%20%284%29.png)

