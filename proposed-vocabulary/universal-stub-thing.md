# Universal Stub Thing

> This document explains how **Stubs** are structured for lists of objects in grcschema.

## Quick-start Knowledge

* A **Stub** is a Thing (object) representing another Thing (object) in a list.
* In order to know the type of Thing the **Stub** represents, the `thing_type` property is provided.
* The properties `property_name` and `property_value` are provided from the associated Thing record for identification of the record.
* Distinct url parameters for each **Stub** list may be provided to enable list filtering via query string. The documentation for each list endpoint will provide the list of acceptable query string parameters.    

## Stub - Schema Object Definition

```javascript
{
  "@context": "http://grcschema.org/",
  "@type": "Stub",
  "id": "Integer",
  "property_name": "String",
  "property_value": "String",
  "thing_type": "String"
}
```

> Where `property_name` is the property IN the target object, `property_value` is the value of that property, and `thing_type` is the type of object the stub represents.

## Stub - Schema Object Example

```javascript
{
  "@context": "http://grcschema.org/",
  "@type": "Stub",
  "id": 38,
  "property_name": "full_name",
  "property_value": "Dorian Cougias",
  "thing_type": "Person"
}
```

> The Stub represents a **Person** Thing (object) using the `Person.full_name` property.
