# Completing the Sign-up

The initial sign-up sequence gives us the following information:

1\. Rapid API Key

2\. Administrator’s first name (a), last name (b), and e-mail address (c)

3\. Organizational domain

4\. Organization Name & ID

5\. Account Name & ID

The above information is then used when filling out additional critical information about the account, as described below.

**It should be noted** that items 3 – 5 are automatically added to each new user’s record when creating their user profiles for this account.

## API Keys

Any additional API keys that need to be associated with the account should be stored in an API key table.

![API Keys](<../../../.gitbook/assets/0 (2).png>)

## Admin contact

The default administrative contact for an account is the person who set up the account. Most of that person’s information has already been gathered in the initial sign-up process. However, additional information must be gathered, as shown below.

![Registering the Admin](<../../../.gitbook/assets/1 (11).png>)

2a. The first name from the sign-up will already exist.

2b. The last name from the sign-up will already exist.

2c. The e-mail address will already exist.

2d. The name prefix must be added from a drop-down list (more about this below).

2e. The middle initial must be added.

2f. The name suffix must be added from a drop-down list (more about this below).

3\. The domain will already exist.

4\. The organization name will already exist.

5\. The account name will already exist.

6\. The checkbox for Admin will be pre-checked. However, it should also be determined whether this person is also the billing contact. If this is checked, information for the billing contact will be unnecessary. The contributor checkbox can be ignored for now.

7-9. This is automated data. The calculation for full name will be explained below.

### Name prefixes and suffixes

For standardization purposes all name prefixes and suffixes are added via a predefined list, using the ID of the prefix and suffix to tie the text to the ID. The application _must_ maintain tables of these references and _must_ update those tables on a regular basis to ensure parity with the federated system.

**Name Prefix** **schema** - [http://grcschema.org/NamePrefixes](http://grcschema.org/NamePrefixes)

**Name Prefix API** - [https://short.grcschema.org/API-NamePrefix List](https://short.grcschema.org/API-NamePrefix%20List)

**Name Suffix schema** - [http://grcschema.org/NameSuffixes](http://grcschema.org/NameSuffixes)

**Name Suffix API** - [https://short.grcschema.org/API-NameSuffix List](https://short.grcschema.org/API-NameSuffix%20List)

### Calculating the full name

The full name is calculated as

`if(prefix≠null;prefix & “ “) & first name & “ “ & if(middle initial≠null;middle initial & “ “) & last name & if(suffix≠null;” “ & suffix)`

## Billing contact

If the admin contact is also the billing contact, this will be skipped. If not, only three items will be necessary to add as the other items will automatically be added.

![Billing Contact](<../../../.gitbook/assets/2 (12).png>)

1\. The full name information will be added.

2\. The e-mail address will be added.

3\. The Billing Contact checkmark will _automatically_ be added.

## Addresses

Between 1 and 3 addresses are necessary for any account within the Federated Mapping system:

primary

billing

shipping

![Shipping Address](<../../../.gitbook/assets/3 (1).png>)

**It should be noted** that both the State and Country drop-downs must be provided.

**Country** – This is the three-digit country code provided by the Country API (below). It _must_ be filled out first in order to populate the list of states (this is worldwide).

**Country Schema** - [http://grcschema.org/Country](http://grcschema.org/Country)

**Country API** - [https://short.grcschema.org/API-Country List](https://short.grcschema.org/API-Country%20List)

**State** – this is the code provided by the State API (forthcoming).
