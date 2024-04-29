---
tags:
  - degree/compsys/databases
---
![[Databases MOC 🌍]]

### Three-Level Architecture

![[Pasted image 20240109142302.png]]

- Has 3 levels: the external, the conceptual and the internal.
- It's like an API in software development.
- Realises data abstraction
	- Users can have the same data but different customised views.
	- Users can change view without affecting other users
	- The internal structure can be changed without affecting the users.

---
### The Three Levels
#### External Level
- The users' view of the database
- Can have multiple different views of the same data. E.g. formatting dates differently based on country ('murica).
- Can be adapted to specific needs
- Can show different entities, attributes and relationships
- Can show derived information like getting an age from a date to birth.

#### Conceptual Level

- Community view of the database.
- Shared by all users
- Describes what data is stored in the database
	- Has the entities, attributes, relationships
	- constraints
	- security/integrity information.
- The logical structure of the entire database
- Must support external views
- Contains no storage-specific details on how to store the database.

#### Internal Level

- The physical representation of the database.
- Describes how the data is stored.
- Achieve optimal runtime performance and storage space utilisation.
- Interface to the OS
- Handles compression and encryption
- Not clearly separate from physical organisation.

#### Physical Organisation

The DBMS also handles physical organisation but we don't look much at that.

![[Pasted image 20240117095210.png]]

---
### Schema vs Instance

If you think of schema as classes and instances as objects then you pretty much understand everything.
#### Schema
- The complete description of the database.
- It results from the database design process
- It should not change
- Has multiple external schemata (different views)
- One conceptual schema
- One internal schema

#### Instance
- An instance of a database lol
- The data within a database at any one time.
- Changes frequently with queries.
- Many instances of databases can follow the same schema.

---
### Data Independence

#### Logical Data Independence

The external schemata (views) remain the same if we change the logical structure on the conceptual level.

#### Physical Data Independence

The conceptual schema remains the same if we change the internal schema.

---
### Database Design

The three phases: conceptual, logical and physical.

![[Pasted image 20240117100052.png]]

#### Conceptual Design

- Construct a first, high-level model of the data.
	- Use [[Entity-Relationship Modelling]]
	- Identify appropriate entities, attributes, relationships and constraints.
- Based on the user's requirements specification
- Independent of any physical considerations
- Relevant for conceptual and external level.
- Serves as the fundamental understanding of the system.

#### Logical Design

- Construct a relational data model of the data.
- Use the conceptual design.
- Use normalisation techniques to eliminate data redundancies and anomalies.

#### Physical Design

- Describing the implementation of of the logical design.
- It's the how instead of the what.
- Defines storage structures, access methods and security protection.
- Consider concrete usage / transactions.
- Optimise for performance.