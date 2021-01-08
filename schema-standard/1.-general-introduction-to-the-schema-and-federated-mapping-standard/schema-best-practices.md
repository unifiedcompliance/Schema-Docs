# § 1.2 Schema Best Practices

The use of characters and data types can be updated dynamically as the needs of the schema change. These two portions of the schema are under less onerous change management rules than the other portions. Therefore, coverage of them here is abbreviated.

## Acceptable Characters

`1.2.1 All characters used in federated compliance mapping data structures will conform to the GRCschema.org character table’s rules.`

Mapping products must enter text into several different JSON data types. Some of those datatypes, such as term definitions for the dictionary, or URLs, only accept certain characters. Therefore, the federated compliance mapping model maintains a character table of acceptable characters to be used in the framework.

Instead of listing all the characters here \(since this list can be updated from time to time\), we’ll present one row of the table and explain that row. The full list is maintained online at [https://grcschema.org/CharTable](https://grcschema.org/CharTable). The table below is a representation and is comprised of the following fields:

| **Char** | **Unicode** | **Dec** | **Hex** | **Binary** | **HTML** | **Definition** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ! | U+0021 | 33 | 21 | 100001 | ! | The grapheme for the exclamation mark character. It is represented by the following codes: Unicode U+0021; Dec 33; Hex 21; HTML !. This character is compatible with all known dictionary entries. |

**Char** – the actual grapheme or special character code \(such as TAB for a tab character\) of the character in question.

**Unicode** _through_ **HTML** – the various representations of the character in different formats.

**Definition** – describes how the character is used, and whether it should be substituted when using it in dictionary entries, URLs, or Markdown language.

## Data Types

`1.2.2 All data types used in federated compliance mapping model will conform to the datatypes documented at GRCschema.org.`

There are various datatypes that each of the JSON objects must follow. The federated compliance mapping model has moved beyond the basic JSON datatypes of null, text, string, etc. and also allows specific datatypes for such things as HostName, TelephoneNumber, Datetime-with-Timezone, etc.

The list of datatypes is maintained online at [http://grcschema.org/DataType](http://grcschema.org/DataType).

## Schema naming

Schema naming will follow a standardized approach to field and table names, and will also follow all restrictions for SQL keywords as SQL databases are the most used in the industry.

`1.2.3 Schema property nodes start with a lowercase character.`

`1.2.4 Schema data types begin with an uppercase character.`

`1.2.5 Properties are lowercase.`

`1.2.6 DataTypes and Things are camelCase.`

`1.2.7 Properties may separate words with underscores “_”.`

`1.2.7.a Refrain from using spaces “ “ and dashes “-“ in any node name.`

### Reserved Keywords

`1.2.7.b Refrain from using reserved keywords in any JSON “thing” or “datatype”.`

SQL Servers use reserved keywords for defining, manipulating, and accessing databases. Re-served keywords are part of the grammar of the Transact-SQL language that is used by SQL Servers to parse and understand Transact-SQL statements and batches. While it is syntactically possible to use reserved keywords by adding special identifiers in Transact-SQL scripts, it is not advisable. Therefore, the following strings are forbidden as field, object, types, and table names.

| TERM | TERM | TERM |
| :--- | :--- | :--- |
| ABSOLUTE | FETCH | PRIVILEGES |
| ACTION | FILE | PROC |
| ADD | FILLFACTOR | PROCEDURE |
| ALL | FIRST | PUBLIC |
| ALLOCATE | FLOAT | RAISERROR |
| ALTER | FOR | READ |
| AND | FOREIGN | READTEXT |
| ANY | FOUND | REAL |
| ARE | FREETEXT | RECONFIGURE |
| AS | FREETEXTTABLE | REFERENCES |
| ASC | FROM | RELATIVE |
| ASSERTION | FULL | REPLICATION |
| AT | FUNCTION | RESTORE |
| AUTHORIZATION | GET | RESTRICT |
| AVG | GLOBAL | RETURN |
| BACKUP | GO | REVERT |
| BEGIN | GOTO | REVOKE |
| BETWEEN | GRANT | RIGHT |
| BINARY | GROUP | ROLLBACK |
| BIT | HAVING | ROUND |
| BIT\_LENGTH | HOLDLOCK | ROW |
| BLOB | HOUR | ROWCOUNT |
| BOOLEAN | IDENTITY | ROWGUIDCOL |
| BOTH | IDENTITY\_INSERT | ROWID |
| BREAK | IDENTITYCOL | ROWS |
| BROWSE | IF | RTRIM |
| BULK | IMMEDIATE | RULE |
| BY | IN | SAVE |
| CASCADE | INDEX | SCHEMA |
| CASCADED | INDICATOR | SCROLL |
| CASE | INITIALLY | SECOND |
| CAST | INNER | SECTION |
| CATALOG | INPUT | SECURITYAUDIT |
| CHAR | INSENSITIVE | SELECT |
| CHAR\_LENGTH | INSERT | SEMANTICKEYPHRASETABLE |
| CHARACTER | INT | SEMANTICSIMILARITYDETAILSTABLE |
| CHARACTER\_LENGTH | INTEGER | SEMANTICSIMILARITYTABLE |
| CHECK | INTERSECT | SESSION |
| CHECKPOINT | INTERVAL | SESSION\_USER |
| CHR | INTO | SET |
| CLOSE | IS | SETUSER |
| CLUSTERED | ISOLATION | SHUTDOWN |
| COALESCE | JOIN | SIZE |
| COLLATE | KEY | SMALLINT |
| COLLATION | KILL | SOME |
| COLUMN | LANGUAGE | SPACE |
| COMMIT | LAST | SQL |
| COMPUTE | LEADING | SQLCODE |
| CONNECT | LEFT | SQLERROR |
| CONNECTION | LENGTH | SQLSTATE |
| CONSTRAINT | LEVEL | STATISTICS |
| CONSTRAINTS | LIKE | STRVAL |
| CONTAINS | LINENO | SUBSTRING |
| CONTAINSTABLE | LOAD | SUM |
| CONTINUE | LOCAL | SYSTEM\_USER |
| CONVERT | LONGVARBINARY | TABLE |
| CORRESPONDING | LOWER | TABLESAMPLE |
| COUNT | LTRIM | TEMPORARY |
| CREATE | MATCH | TEXTSIZE |
| CROSS | MAX | THEN |
| CURDATE | MERGE | TIES |
| CURRENT | MIN | TIME |
| CURRENT\_DATE | MINUTE | TIMESTAMP |
| CURRENT\_TIME | MODULE | TIMESTAMPVAL |
| CURRENT\_TIMESTAMP | MONTH | TIMEVAL |
| CURRENT\_USER | MONTHNAME | TIMEZONE\_HOUR |
| CURSOR | NAMES | TIMEZONE\_MINUTE |
| CURTIME | NATIONAL | TO |
| CURTIMESTAMP | NATURAL | TODAY |
| DATABASE | NCHAR | TOP |
| DATE | NEXT | TRAILING |
| DATEVAL | NO | TRAN |
| DAY | NOCHECK | TRANSACTION |
| DAYNAME | NONCLUSTERED | TRANSLATE |
| DAYOFWEEK | NOT | TRANSLATION |
| DBCC | NULL | TRIGGER |
| DEALLOCATE | NULLIF | TRIM |
| DEC | NUMERIC | TRUNCATE |
| DECIMAL | NUMVAL | TRY\_CONVERT |
| DECLARE | OCTET\_LENGTH | TSEQUAL |
| DEFAULT | OF | UNION |
| DEFERRABLE | OFF | UNIQUE |
| DEFERRED | OFFSET | UNKNOWN |
| DELETE | OFFSETS | UNPIVOT |
| DENY | ON | UPDATE |
| DESC | ONLY | UPDATETEXT |
| DESCRIBE | OPEN | UPPER |
| DESCRIPTOR | OPENDATASOURCE | USAGE |
| DIAGNOSTICS | OPENQUERY | USE |
| DISCONNECT | OPENROWSET | USER |
| DISK | OPENXML | USERNAME |
| DISTINCT | OPTION | USING |
| DISTRIBUTED | OR | VALUE |
| DOMAIN | ORDER | VALUES |
| DOUBLE | OUTER | VARBINARY |
| DROP | OUTPUT | VARCHAR |
| DUMP | OVER | VARYING |
| ELSE | OVERLAPS | VIEW |
| END | PAD | WAITFOR |
| END\_EXEC | PART | WHEN |
| ERRLVL | PARTIAL | WHENEVER |
| ESCAPE | PERCENT | WHERE |
| EVERY | PIVOT | WHILE |
| EXCEPT | PLAN | WITH |
| EXCEPTION | POSITION | WITHIN GROUP |
| EXEC | PRECISION | WORK |
| EXECUTE | PREPARE | WRITE |
| EXISTS | PRESERVE | WRITETEXT |
| EXIT | PRIMARY | YEAR |
| EXTERNAL | PRINT | ZONE |
| EXTRACT | PRIOR |  |

## Schema Structure

Establishing any data format for an API is a common problem – especially when trying to make the API easy to use so anyone can use short strings to reference common things, while also providing a robust interchange format to use in federated projects. Leveraging information from multiple APIs becomes problematic due to namespace or document format conventions that may differ between API endpoints. Moreover, the same principles are often repeated across different endpoints using arbitrary identifiers \(name, email, website, etc.\); a federated project community needs to stop repeating itself \(DRY concept\) and reuse common conventions. This model is based on the principles of separation of data model from syntax, the use of discoverable identifiers describing document contents, and general organizing principles that allow documents to be machine understandable \(read, interpreted as JSON-LD using Linked Data\). Key among these is the notion of vocabulary re-use, so that each endpoint does not need to separately describe the properties and structure of their JSON documents.

### **Schema Context**

`1.2.8 All keys used within a JSON document can have unambiguous meaning, being bound to URLs which describe their meaning.`

`1.2.8.a The context for the schema structure will be defined at grcschema.org, with the top level context being “Thing”.` 

An example of the bound, unambiguous context is shown below that uses IRIs \(Internationalized Resource Identifiers as described in RFC3987\) for unambiguous identification. The idea is to use IRIs to assign unambiguous identifiers to data that may be of use to other developers:

`{ "@context":{ "schema": "`[`http://grcschema.org/`](http://grcschema.org/)`", "rdf": "`[`http://www.w3.org/1999/02/22-rdf-syntax-ns#`](http://www.w3.org/1999/02/22-rdf-syntax-ns#)`", "rdfa": "`[`http://www.w3.org/ns/rdfa#`](http://www.w3.org/ns/rdfa#)`", "rdfs": "`[`http://www.w3.org/2000/01/rdf-schema#`](http://www.w3.org/2000/01/rdf-schema#)`" }, "@id": "Thing", "@type": "schema:Thing", "rdfs:comment": "The most generic type of item.", "rdfs:label": "Thing" }` 

`1.2.9 Each JSON object will be placed in a hierarchy with a single top-level object (type) with cascading, subordinate objects (types) as necessary.`

`1.2.10 Multiple array values are presumed unordered.` 

`1.2.11 Every JSON object will have core meta data (`[`coreMetaData`](https://grcschema.org/CoreMetaData)`) associated with it.` 

`1.2.11.a Core meta data will include date_created to record the creation date of the record.` 

`1.2.11.b Core meta data will include date_modified to record the date the record was last modi-fied (this will be the same as the creation date when an object is first created).` 

`1.2.11.c Core meta data will include created_by to record the id of the person or agent that cre-ated the object.` 

`1.2.11.d Core meta data will include modified_by to record the id of the person or agent that last modified the object.` 

`1.2.11.e Core meta data will include a live status (live_status) that is a Boolean value, and if the object is no longer live, it will not be removed from the database but only marked as dep-recated (Boolean value of 0).` 

`1.2.11.f Core meta data will include the name of the table that contains the object.`

When creating the checksum for the RESTful record validation, the Verhoeff calculation will be used to create the initial checksum from a combination of these three fields:

* **date\_modified**: This is the most recent modification date of the record.
* **id**: This is the ID field of the record in question.
* **live\_status**: This is a Boolean field indicating if the record is live \(1\) or deprecated \(0\).

In combination, these three tell the user _which_ record they are dealing with, when it was last modified, and whether it remains live and ready for use.

The checksum will return a dihedral check integer of those three values that can be used on the receiving end to verify that the record of _that_ ID was last modified on _that_ date and has _that_ live status.

#### When creating or updating a record in the system

When creating or updating a record, the system will calculate the checksum based on the input and will record the checksum in the checksum node. Given the modification\_date of 6/17/2020, ID of 1 and live\_status of 1, Verhoeff \( 6/17/2020 & 1 & 1 ; 0 ; 0 \) returns the value **5**.

#### Testing the checksum

Upon receiving data from the system, the user will be to calculate a boolean value by simply _reversing_ the calculation. Given the modification\_date of 6/17/2020, ID of 1 and live\_status of 1, NOT Verhoeff \( 6/17/2020 & 1 & 1 ; 0 ; 0 \) returns the value **1**. Modification of any of the values \(date, ID, live\_status\) returns 0.

### **The checksum calculation**

Returns the Verhoeff dihedral check digit of numericString. Use this function to verify a numeric string protected by Verhoeff check digit, or to generate the correct Verhoeff check digit for a given numeric string.

#### **Format**

Verhoeff \( numericString ; index ; checkSum \)

#### Parameters

**numericString** - a string of numeric characters \(digits\) or field containing numeric characters. In this case, the string is comprised of the following: **date\_created** & **id** & **live\_status**.

**index** - indicates the digit position of the current **iteration** - needs to be initialized to zero \(0\) when calling the function. 

**checkSum** - indicates the check digit of the current iteration. This needs to be initialized to zero \(0\) when calling the function 

**Data type returned** = number

#### Calculation

_Let \( \[    
          n = Right \( numericString ; 1 \) ;   
          p = Let \( \[   
          array =                 "01234567891576283094580379614289160435279453126870428657390127938064157046913258" ;    
          start = 10 \* Mod \( index ; 8 \) + n + 1 \] ;   
                       Middle \( array ; start ; 1 \)  \) ;   
          d = Let \( \[   
          array = "0123456789123406789523401789563401289567401239567859876043216598710432765982104387659321049876543210" ;   
          start = 10  \* checkSum + p + 1 \] ;   
                       Middle \( array ; start ; 1 \) \) ;    
          len = Length \( numericString \) ;   
          nextString = Left \( numericString ; len - 1 \)  \] ;   
          Case \( len &gt; 1 ; Verhoeff \( nextString ; index + 1 ; d \) ; d \)  
 \)_ 

`1.2.11.g Core meta data will include a Verhoeff checksum (checksum) that is a positive integer.`

`1.2.12 All nested arrays will include the unique identifier (id) for each nested object as well as the id of the related table in the format of the foreign table name followed by an underscore and "fk" (foreigntablename_fk).`

An example of a nested table with its id as well as the id of the related table is shown below. 

_{ "@context":  
                        { "schema": "_[_http://grcschema.org/_](http://grcschema.org/)_",  
                        "rdf": "_[_http://www.w3.org/1999/02/22-rdf-syntax-ns\#_](http://www.w3.org/1999/02/22-rdf-syntax-ns#)_",  
                        "rdfa": "_[_http://www.w3.org/ns/rdfa\#_](http://www.w3.org/ns/rdfa#)_",   
                        "rdfs": "_[_http://www.w3.org/2000/01/rdf-schema\#_](http://www.w3.org/2000/01/rdf-schema#)_"   
                        },   
"id": "96",   
"@type": "Person",   
"name": "Barack Obama",   
"givenName": "Barack",   
"familyName": "Obama",   
"jobTitle": "44th President of the United States",   
"spouse":   
                        { "id": "13133",   
                        "@type": "Person",   
                        "name": "Michelle Obama",   
                        "Person\_fk": "96"   
                        }   
}_

`§ 1.2.13 When using a property intended to reference another entity or external reference, those properties will be represented as full URLs.`

### Specification of Arrays

Arrays are specified by the keyword @set followed by JSON’s array brackets “\[ \]”. The objects that follow denote the individual objects \(fields\) within the array. 

_"@set": \[  
        { "@type": "NonStandardName",   
         "name": "String",  
        "id": "Integer",  
        "organization\_fk": "Integer"  
        }  
         \]_

`§ 1.2.14 When including arrays within objects, the @set will precede the array brackets “[ ]”.`

### Specification of Types

The @type keyword is used to set the type of a node or the datatype of a typed value \(a value, which is a string, and a type, which is an IRI\). In Linked Data, it is common to specify the type of a graph node; in many cases, this can be inferred based on the properties used within a given node object, or the property for which a node is a value. 

`1.2.15 The use of @type immediately following @context sets the 5.15 The use of @type immediately following @context sets the name of the table.` 

An example of this is shown below: 

"@context":"[http://grcschema.org/](http://grcschema.org/)" ,  
"@type":"Role" 

`1.2.16 When @type follows an object name and isn’t preceding an array it names a predefined group of fields.` 

Example below: 

_"coreMetaData":   
  {  
  "@type": "CoreMetaData"  
  "date\_created":"2014-10-05"  
  "date\_modified":"2014-10-05"  
  "live\_status":1  
  "table":"Language"  
  }_ 

`1.2.17 When @type follows an object name and precedes an array it names the related table that should be added.` 

Example below: 

_"nonStandardNames":  
  {  
  "@type":"NonStandardNames"  
  "Names":  
    \[  
    0:  
      {  
      "id":1  
      "name":"افغانستان"  
      }  
    \]  
  }_

Here is an example where you’ve got @type meaning all of the above.

_"geoLocation":  
  {  
  "@type":"GeoLocation" &lt;- That describes this grouping of data  
  "borders":  
    {  
    "@type":"Borders" &lt;— That describes the related subtable and fields  
    "border":  
      \[...\]  
    }  
  "term":  
    {  
    "@type":"Term" &lt;- That just describes a field from a related table  
    "term.id":32131  
    }  
  "callingCodes":  
    {  
    "@type":"CallingCodes" &lt;— That describes the related subtable and fields  
    "calling\_codes":  
      \[  
      0:  
        {...  
        }  
      \]  
     "timeZones":  
       {...  
       }  
      "latitude":"33"  
      "longitude":"65"  
    }_

### Local Reference Identifiers

When creating new records \(POST\), or updating existing records \(PATCH\), an additional level of validation and non-repudiation is presented as an optional key-value pair. We suggest using a hash-based algorithm such as an md5 hash based on the contents of the fields being passed to the API for creation or updating, such as the one below:

local\_reference\_id": "81dc9bdb52d04dc20036dbd8313ed055"

`§ 1.2.19 For POST and PATCH operations, you may send an optional local_reference_id for the core object and any sub-objects in unordered lists (\@set arrays). This lo-cal_reference_id will be returned (like an echo) for that object.`

`§ 1.2.20 It is recommended you use a Type 4 UUID which is unique for that object in your sys-tem and tie the federated ID to your record for later use in querying the federated system for that object.`

#### POST Operation Example

For the core object, you may place a local\_reference\_id at the object root level, and it will be re-turned in the response.

**SEND**

_{  
   "@context": "_[_http://grcschema.org/_](http://grcschema.org/)_",   
   "@type": "NameSuffix",   
   "abbreviation": "Adm",   
   "local\_reference\_id": "81dc9bdb52d04dc20036dbd8313ed055",   
   "suffix": "Admiral"   
}_

**RESPONSE**

_{   
   "@context":"_[_http://grcschema.org/_](http://grcschema.org/)_",   
   "@type": "NameSuffix",   
   "abbreviation": "Adm",   
   "id": 2,   
   "suffix": "Admiral",   
   "local\_reference\_id": "81dc9bdb52d04dc20036dbd8313ed055"   
}_

**PATCH Operation Example**

For the core object, you may place a local\_reference\_id at the object root level, and it will be returned in the response. Do not add local\_reference\_id to the container objects like CoreMetaDa-ta.

**SEND & RESPONSE**

_{   
   "@context":"_[_http://grcschema.org/_](http://grcschema.org/)_",   
   "@type": "NameSuffix",   
   "CoreMetaData": {   
                                    "@type": "CoreMetaData",   
                                   "date\_created": "Date",   
                                   "date\_modified": "Date",   
                                   "created\_by": "Integer",   
                                   "modified\_by": "Integer",   
                                   "live\_status": "Boolean",   
                                   "checksum": "Integer",   
                                   "validated": "Boolean"   
                                   },   
   "abbreviation": "Adm.",   
   "id": 2,   
   "suffix": "Admiral",   
   "local\_reference\_id": "81dc9bdb52d04dc20036dbd8313ed055"   
}_

