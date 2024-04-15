# § 2 Schemas & Endpoints

The core data model for a federated compliance mapping schema is shown below:

![Core data model for a federated mapping schema](<../.gitbook/assets/0 (1) (2).png>)

The process of mapping follows these steps:

1. A **Person** who is
2. part of an **Organization** is
3. **assigned a Role** of contributor (Author, Mapper, etc.)
4. as part of a **Project** that contains an
5. **Authority Document** that has various
6. **Citations** (or SWID entries, or catalog entries, or reference elements) that have identified
7. **Dictionary Terms** (such as product names, tagged nouns or verbs) and a possible match to a
8. **Reference Control** (or focus control or Common Control).

We will call this continuous process an **entry. In this section we will document each of the existing schemas for the data model shown above, annotating how they work together to create a compliance framework mapping entry.**
