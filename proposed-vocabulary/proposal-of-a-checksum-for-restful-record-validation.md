# Proposal of a Checksum for RESTful record validation

## 

How do we know a record in a RESTful database, queried via API, and returned via JSON, is **valid**? How do we _know_ that the record’s reported last modification is correct? To ensure that the records maintained by the system have integrity during input as well as distribution through the API, each record should have its own checksum value stored in a checksum field. Currently, the best methodology we can find for creating and verifying the checksum follows the Verhoeff calculation format. A Dutch mathematician named Jacobus Verhoeff conducted a study of 12,000 numerical errors and from that, proposed a check digit calculation scheme that catches all single errors as well as all adjacent transpositions and most other errors.

### The checksum use case

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

Let \( \[    
n = Right \( numericString ; 1 \) ;   
p = Let \( \[   
array =  "01234567891576283094580379614289160435279453126870428657390127938064157046913258" ;    
start = 10 \* _Mod \( index ; 8 \) + n + 1 \] ;   
Middle \( array ; start ; 1 \)  \) ;   
d = Let \( \[   
array = "0123456789123406789523401789563401289567401239567859876043216598710432765982104387659321049876543210" ;   
start = 10_  \* checkSum + p + 1 \] ;   
Middle \( array ; start ; 1 \) \) ;    
len = Length \( numericString \) ;   
nextString = Left \( numericString ; len - 1 \)  \] ;   
Case \( len &gt; 1 ; Verhoeff \( nextString ; index + 1 ; d \) ; d \)  
 \)

