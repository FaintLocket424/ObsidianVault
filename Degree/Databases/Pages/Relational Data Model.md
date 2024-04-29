---
tags:
  - degree/compsys/databases
---
![[Databases MOC 🌍]]

### Relational Data Model

It's based on the concept of mathematical relations.

The schema of a relation R: $R(A_1,A_2,\dots,A_n)$
- Attributes $A_1,A_2,\dots,A_n$
- E.g. Student(*studentNo*, *prename*, *surname*)
- Ordering of the attributes does not matter.

All the data in a relational database is stored in relations (tables).

[[Three-Level ANSI-SPARC Architecture#Logical Design|Logical Design]] is how we decompose a database into relations.

---
### Terminology
- Relation: A table with rows and columns.
- Attribute: A named column in a table
- Tuple: A row / record in a table.
- Domain: Set of allowed values for an attribute.
- Cell: The value of an attribute in a record
- Degree: The number of attributes
- Cardinality: Number of records

![[Pasted image 20240117103549.png]]

A relational database is a collection of normalised relations.

---
### Domain of an Attribute

- Every attribute has a domain
- It defines meaning and allowed values of an attribute.
- Semantically incorrect operations can be avoided, like multiplying postcodes and street names.

---
### NULL

- Indicates the absence of a value.
- Represents an attribute value that is unknown or NA.
- Not a normal value
- Has to be handles in a special way.
- NULL is not the same as 0, False or "".
- Can cause implementation problems like when you compare normal values against NULL.

---
### Keys

- A method to uniquely identify a tuple in a relation (A record in a table).

| Key Type | Description |
| ---- | ---- |
| Key | A set of attributes which uniquely identify a tuple. |
| Candidate Key | The minimal set of attributes that is a key. |
| Primary Key | One candidate key selected to identify tuples. |
| Alternate Key | Any candidate key that isn't the primary. |
| Simple Key | A key that consists of a single attribute. |
| Composite Key | A key consisting of multiple attributes. |
| Foreign Key | A reference to the primary key of another entity. |

![[Pasted image 20240117110715.png]]
For this relation, we could use *surname*, or *(prename, surname)*, or *(prename, surname, DOB)* for our candidate key. But this would be a composite key.

We could use *studentNo* since it's unique and a simple key.

---
### Integrity Constraints

##### Domain Constraints
- Attribute values have to be within their domain.

##### Entity Integrity
- Attributes of the primary key cannot be NULL.
- Guarantees that each entity has a unique identifier.
- Ensures foreign key values form proper references.

##### Referential Integrity
- Foreign keys must match a primary key or be NULL.
- Ensures references to be valid.
- Prevents deleting a tuple if it is referenced somewhere else.

---
### Views

A view is a table that is derived from one or more tables.
It is generated on-demand, not physically stored.

Views are used to show customised information to every user, like hiding information. Or it can show new computed values like working out ages from dates of birth.

---
### Alternatives to the Relational Data Model

##### Network Data Model
- Record-based data model.
- Records are nodes in a graph.
- Relationships are edges in the graph.
![[Pasted image 20240124110559.png]]

##### Hierarchical Data Model
- Restricted type of network data model
- Each node can only have one parent.
- Can be represented as a tree graph.
![[Pasted image 20240124110616.png]]

---
### Additional Information 

- [[Comp Sys Part 3 Lecture 3 Relational Data Model.pdf|Computer Systems Part 3 Lecture 3 Relational Data Model]]

