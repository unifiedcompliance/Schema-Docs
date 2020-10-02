---
description: >-
  In order to ensure that data is kept up to date, the first bit of vocabulary
  that must be established is the audit log for each changed record
---

# Auditlog information

## [https://grcschema.org/AuditLog](https://grcschema.org/AuditLog)

Metadata that allows us to track the changes of any record's JSON objects by describing each object changed, its previous value and its current value. Properties from [AuditLog](https://grcschema.org/AuditLog):

| Property | Expected Type | Description |
| :--- | :--- | :--- |
| [id](https://grcschema.org/id) | [Integer](https://grcschema.org/Integer) | A unique and persistent identifier for the record. |
| [date\_modified](https://grcschema.org/date_modified) | [Datetime](https://grcschema.org/Datetime) | The date the record was created. |
| [modified\_by](https://grcschema.org/modified_by) | [Integer](https://grcschema.org/Integer) | The ID of the person or agent that last modified the record. |
| [live\_status](https://grcschema.org/live_status) | [Boolean](https://grcschema.org/Boolean) | A Boolean field of "live" \(1\) or "deprecated" \(0\). |
| [modified\_property](https://grcschema.org/modified_property) | [String](https://grcschema.org/String) | The JSON property that has been modified. |
| [previous\_value](https://grcschema.org/previous_value) | [String](https://grcschema.org/String) | The value of the modified\_property \*prior to\* modification. For a new record, this value will be "null". |
| [current\_value](https://grcschema.org/current_value) | [String](https://grcschema.org/String) | The value of the JSON property \*after\* modification. For a record that was deleted, this value will be "null." |
| [audited\_record\_id](https://grcschema.org/audited_record_id) | [Integer](https://grcschema.org/Integer) | The record ID of the record that created the audit trail. |
| [errata\_reason](https://grcschema.org/errata_reason) | [Text](https://grcschema.org/Text) | The reason an edit was made. |
| [change\_type](https://grcschema.org/change_type) | [String](https://grcschema.org/String) | The type of change that was made. |
| [approval\_state](https://grcschema.org/approval_state) | [String](https://grcschema.org/String) | The state a change is in. |



