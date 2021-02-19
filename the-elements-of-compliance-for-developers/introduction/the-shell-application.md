# The Shell application

The federated mapping application we describe utilizes a multi-tenant architecture. The shell that we’ve designed, is designed to fit within the confines of a laptop or an iPad Pro. As such, the _suggested_ window proportions are 1368 wide x 996 high. Below are basics for the window’s shell:

![Window basics](../../.gitbook/assets/0%20%283%29.png)

1. The top left of the window is for branding and logos.

2. If the window will be a sign-in window, this is where the active User’s name will go. The dropdown will show

* the user’s name,
* a button to go to the user’s profile, and
* a button to sign the user out.

3. This is the area for the main vertical menu, if there is to be one. When the top icon is clicked it will expand to show the names of the vertical icons. When closed, it is 85 px wide. This is 80 px wide.

4. If there is pagination, the current page is shown on the bottom left.

5. If there is pagination, the navigation for the pagination is shown on the bottom right.

## Basic Navigation

Basic navigation in our demonstration file follows the same format we’ve designed for many of our websites, such as the [CommonControlsHub.com](https://cch.commoncontrolshub.com/) website.

![Basic navigation](../../.gitbook/assets/1%20%282%29.png)

1. Left vertical navigation has the following items which _must_ be a part of any federated mapping application:

* Personnel
* Orgs & Activities
* Authority Documents
* Dictionary
* Citations
* Common Controls
* Assets
* Records
* Events
* Corpora Management 
* cog at the bottom is settings

2. Subnavigation is found in-between the top two horizontal rules. Selected navigation will have a red underscore below it.

### Expanded Basic Navigation

As with our other applications, the left-hand navigation opens and closes for readability and sub-contents.

![Expanded basic navigation](../../.gitbook/assets/2%20%282%29.png)

1. All names of primary menu items will be in bold. The fonts will be sized no less than 14 points for readability. When expanded, the vertical menu will show disclosure triangles for those items that have sub-menus. Sub-menu items will be indented and not in bold but at the same font size. The selected items will always be in the product’s primary highlight color.

## Adding the API Keys

As explained in the section about Rapid API, each application can have multiple API keys. Therefore, you’ll want to have a table where you record those API keys so that you can associate them with the various API calls, teams, etc.

![Adding the API Keys](../../.gitbook/assets/3%20%282%29.png)

## Registering an Account

An account with Rapid API must be established in order to receive data as well as add or update data within the Federated Mapping system. This information should be added to the **Setup Info** area within the Settings section of the application.

![Initial Setup](../../.gitbook/assets/4%20%282%29.png)

1. The Federated Mapping application needs to set up three items before any content can be passed both from and to the system.

* The client must obtain an API key from Rapid API.
* The client must register the primary administrator’s email account as Person0 for this account.
* The client then also automatically registers the domain as a group or organization for this account.

2. If the application is also going to share information with the Common Controls Hub, the Common Controls Hub’s API Key must be entered in as well.

* Once the API key is entered and then validated, the API will return the user’s CCH Account ID and the “valid until” date for the API key’s license.

### Setting up the User0 initial account

Before you can do _anything_, you first need to register the administrator of the account with the federated database. The minimum information you’ll need to register an account is the administrator’s

* first name;
* last name; and
* email address.

The diagram below shows the sequence that needs to be followed for the initial account setup.

![User0 sequence](../../.gitbook/assets/5%20%281%29.png)

1. The user must have a valid sign-in to the WebApp.

2. The user must then enter the basic information for their account, as described above. _The WebApp_ _must give this record an id of 0_.

3. The WebApp then performs a check with the FederatedApp to see if the email address is on file. For the User0 process, the email address is the search key. The WebApp uses the [GET Person LIST](https://short.grcschema.org/GETPersonList) api call with the query parameter of email/email address.

4. If nothing is found, a json value of “\[\]” will be returned.

5. At that point, the WebApp creates a [POST Person](https://short.grcschema.org/POSTPerson) api call with all of the administrator’s information.

6. If, after the query, the user’s email was found, _or_ after the POST Person call, the FederatedApp will return the user’s record _with a federated id_.

7. At that point, the WebApp then updates the user’s ID with the returned information.

