---
tags:
  - degree/compsys/databases
---
![[Databases MOC 🌍]]

### Top-Down vs Bottom-Up Design

With the Top-Down approach, we use the Entity-Relationship Model
- Start from data requirements
- Graphical description of the DB
- Identifies entities in the world, their attributes and relations.

With the Bottom-Up approach, we use normalisation:
- Start with examples of actual data in tables
- Analyse relationships among attributes.
- Re-design the tables in a better way.
- Difficult for large DBs.

---
### What does a "better" way mean?

Re-designing a table in a better way means:
- Minimising the required space
- Avoiding data anomalies.

In particular, we need to have no redundancy.
- Wasteful for storage space
- Leads to inconsistencies.

###### Example:
A table that contains students, their college and the college address.

![[Pasted image 20240123142023.png]]

Storing the college and address every time is very wasteful, and can lead to inconsistencies if for example a college was to move site and change address. You'd then have to change every single row.

---
### Anomalies

With the example above, anomalies can arise from certain operations.

##### Insertion Anomaly
- Adding a new student would involve copying the college address into the new record.
- You cannot insert college data as it's all linked to the student data.

##### Modification Anomaly
- Modifying the records of one student can lead to inconsistencies.
- A college changing address would have to update all student records for that college.

##### Deletion Anomaly
- Deleting a record could lead to a deletion of other data.

---
### Decomposition

The way to avoid [[#Anomalies]] is to decompose tables.

Instead of one big table, you can split it into multiple tables storing their own data.

For our example, we could make a new table to store college information and then put a foreign key into the student table.

Go from:
Student(*id*, *prename*, *surname*, *college*, *collegeAddress*, *collegePhoneNumber*)

To:
Student(*id*, *prename*, *surname*, *college*)
College(*college*, *collegeAddress*, *collegePhoneNumber*)

---
### Functional Dependencies

- Describes the relationship among attributes in the same table.
- Determines candidate / primary / foreign keys.
- Determines which attributes to combine into new tables.

##### Definition:
If $A$ and $B$ are two sets of attributes in a relation, we say:
- "$B$ is functionally dependent on $A$ ($A\rightarrow B$)" or
- "$A$ functionally determines $B$"
If each value in $A$ is associated with exactly one value of $B$.

An important note is that $A$ and $B$ are sets, so they're collections of attributes.

Informally, $(A\rightarrow B)$ means:
- If you know the values of $A$, then you know the values of $B$.
- *id* $\rightarrow$ *college* means if you know the student ID, you know their college.

So $A$ is called the determinant of $B$.

A functional dependency has to hold at all times for all possible instances of the relation. So (*prename*, *surname*) $\rightarrow$ *college* would not work since two people can have the same name.

##### Full Functional Dependency
- $B$ is functionally dependent on $A$
- $B$ is not functionally dependent on any proper subset of $A$.
![[Pasted image 20240123154829.png]]
The student's name is functionally dependent on the student ID.

##### Partial Functional Dependency
- $B$ is functionally dependent on $A$.
- $B$ remains functionally dependent on at least one proper subset of $A$.
![[Pasted image 20240123154846.png]]
The college is partially functionally dependent on (id, prename, surname) as it is fully functionally dependent on just the id.

##### Transitive Functional Dependency
- If $A\rightarrow B$ and $B\rightarrow C$ then $A$ is transitively dependent on $A$ via $B$.
![[Pasted image 20240123154900.png]]

---
### Determining Functional Dependencies

Sometimes it's obvious from semantics like *id* $\rightarrow$ (*prename, surname*)

Sometimes it's from a specification or discussion with customers.

If we have a set of functional dependencies $F$, it's closure $F^{+}$ are all functional dependencies that are implied by the dependencies in $F$.

Computing $F^{+}$ can be done using [[Armstrong's Axioms]].

$F^{+}$ is computed by starting with all dependencies in $F$ and repeatedly applying [[Armstrong's Axioms]] and adding any new dependencies found.

An algorithm for this might look like:

```
F+ = F

repeat
	for every func. dep. f in F+
		apply the rules of reflexivity and augmentation to f
		add these new func. dep. to the set F+
	for each pair f1,f2 of func. dep. in F+
		if f1,f2 imply a func. dep. f3 using transitivity
			add f3 to F+
until the set F+ does not change
```

An example of deriving new dependencies:
![[Pasted image 20240123161806.png]]

---
### Additional Information

- [[Comp Sys Part 3 Lecture 5 Functional Dependencies.pdf|Computer Systems Part 3 Lecture 5 Functional Dependencies]]
