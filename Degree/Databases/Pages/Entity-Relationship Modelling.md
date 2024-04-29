---
tags:
  - degree/compsys/databases
---
![[Databases MOC 🌍]]

### Properties 

- It's a conceptual database design 
- Has entities with attributes 
- Has relationships between entities 
- Has constraints on entities / attributes / relationships 
- It's not identical to the Relational Data model
- It's a top-down approach to database design 

---
### Entities 

An entity is a thing to be explicitly represented.

For example, in a university database the entities may be
- A student 
- A college 
- A course 
- A teacher 

Visually, they're represented as a labelled rectangle.

Think about OOP.
- An OOP class is like an entity type 
- An OOP object is an entity occurrence

---
### Relationships 

An association between two or more entity types.

For example:
- A *student* "attends" a *course* 
- A *person* "is a citizen of" a *country*

It's visually represented as a labelled line between entities.

##### Constraints 
They have constraints on the number of entity occurrences that can participate in a relationship.

Most commonly a range "min..max", with \* being unconstrained/infinity.

##### Cardinality 
- *one-to-one* (1:1)
- *one-to-many* (1:\*)
- *many-to-many* (\*:\*)

##### Participation 
The participation goes on the other end of the relationship line.

- *Optional* ($0$) $\to$ e.g. giving a course is optional for a teacher.
- *Mandatory* ($\ge 1$) $\to$ e.g. attending a course is mandatory for a student.

##### Example 

![[Pasted image 20240207094528.png]]

Take the teachers giving courses relationship.
- $1..1$ tells us we have 1 teacher in this relationship.
- $\text{gives}\to$ tells us its teachers giving courses, not courses giving teachers.
- $0..*$ tells us we have 0 to infinity courses in this relationship.
- So this is a *one-to-many* relationship, in which 1 teacher can give 0 to infinity courses.

Or take the "*teacher is head of school*" relationship.
- $1..1$ tells us we have 1 teacher in this relationship.
- $0..1$ tells us we have 0 to 1 schools in this relationship.
- So this is a *one-to-one* relationship, in which 1 teacher can be head of 0 or 1 schools.

---
### Attributes 

The properties of an entity type.

An entity type *person* may have a *name*, *address* etc.
An attribute domain is the allowable values.

Attributes to in a lower part of the entity rectangle.
A primary key is underlined.
Named using camelCase

There are many types of attributes:
##### Simple Attribute 
Only has a single component
- age 
- sex 

##### Composite Attribute 
Has multiple components 
- An address with a street name, city, postcode 
- A name with a first name and lastname.

##### Single-Valued 
Only one value for each entity occurrence.
- Person name 
- School Address 

##### Multi-Valued 
Multiple values for each occurrence.
- A school with many phone numbers.

##### Derived 
Computed from other attributes.
Prefixed with a "/"
- Deriving a person's age from their date of birth.

---
### Transforming ER Modelling to [[Relational Data Model]]

This is the process of [[Three-Level ANSI-SPARC Architecture#Logical Design|Logical Design]].

It's not always that you have one table per entity.

[[Relational Data Model#Keys|Foreign Keys]] are used to represent relationships.

##### Resolving a *one-to-one* Relationship
It's decided based on [[#Participation]]
- Add a foreign key to the mandatory entity.
- If both are mandatory, try combining them into one relation.
- If both are optional, then either entity is fine to have the key.

##### Resolving a *one-to-many* Relationship 
It's decided based on [[#Cardinality]]
- Add foreign key of "one" side to the "many" side.
- E.g. adding a *teacherNo* key to a *course* relation.

##### Resolving a *many-to-many* Relationship 
Create a separate relation with two foreign keys.

This can be represented in the ER Model.
- Introduce a new entity
- Connect with two *one-to-many* relationships 
- Old constraints go to new entity 
- Old entities get (1..1) constraints.

Example:
![[Pasted image 20240207102513.png]]
becomes
![[Pasted image 20240207102525.png]]

---
### Step-by-Step Construction of ER Model 

1. Identify entities and relationships from the scenario / real world 
2. Draw a rough ER diagram 
3. Add constraints (min/max and participation/cardinality)
4. Resolve and *many-to-many* relationships.
5. Add attributes and define primary keys 
6. Check if it reflects the real world.
7. Repeat and refine.

A finished Entity-Relationship Model could look like this 
![[Pasted image 20240207155629.png]]
With its [[Database Normalisation|Normalised]] relations.

---
### Additional Information

- [[Comp Sys Part 3 Lecture 4 Entity Relationship Modelling.pdf|Computer Systems Part 3 Lecture 4 Entity Relationship Modelling]]
