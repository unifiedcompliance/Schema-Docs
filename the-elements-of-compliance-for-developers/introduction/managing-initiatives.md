# Managing Initiatives

All wireframes for this portion of the Compliance as Code project are available at:

[https://balsamiq.cloud/srj76i4/pldajl7](https://balsamiq.cloud/srj76i4/pldajl7)

The scope of this portion of the project is to allow _the administrator_ of a known account and to fill out additional information about the initiatives assigned to the organization.

Initiatives differ from groups in that initiatives are

* always \(insofar as we know\) local to an organization,
* have a specific purpose, and
* have a begin and end date.

## Schema

The schema for a group is listed here: [http://grcschema.org/Initiative](http://grcschema.org/Initiative).

The ERD for working with an initiative looks like the diagram that follows:

![Initiative ERD](../../.gitbook/assets/0%20%2810%29.png)

## Navigation

Main navigation for group is accessed _below_ the group icon \(1\) as shown in the following diagram.

Within the group section of the shell, sub-navigation must include capabilities to switch between _this account’s initiatives_ and _all initiatives_ \(2\).

![Initiative subnavigation](../../.gitbook/assets/1%20%289%29.png)

## Basic Info

Basic information for the initiative won’t exist until added. Because of the dearth of information for an initiative, most of the other layout items were put onto this one.

![Basic Info](../../.gitbook/assets/2%20%289%29.png)

1. **Core Metadata** – should exist and is automatically created.

2. **Name** –is mandatory when creating an initiative.

3. **Description** – while not mandatory, _should_ be filled out.

4. **Begin** and **End dates** – _must_ be set for an initiative, as this is one of the primary things that separate an organizational initiative from a group.

5. **Email addresses** – are optional as some initiatives will have them and others won’t.

6. **Group Hierarchy** – can be set by selecting an existing group \(not another initiative\).

7. **Telephone Numbers** – some initiatives will have them.

## Character

While not necessary, it helps to understand the character of an initiative.

![Initiative Character](../../.gitbook/assets/3%20%289%29.png)

1. **Character settings** – these are options settings wherein the user selects a number from 1 to 10 for each of the four characterizations. Selections from 1-5 will create a _formal_ setting and 6-10 will create an _informal_ setting. There are images associated with each of the formal and informal settings for each of the four characterizations.

2. **Organizational Character Index** – this is an optional field to be filled out for the _the account_. If it was filled out at the account level, that information will show up here.

## Members

This is a listing of members. Members are added/managed through the Staff layout. Members can be navigated to by clicking on their name.

![Members](../../.gitbook/assets/4%20%288%29.png)

