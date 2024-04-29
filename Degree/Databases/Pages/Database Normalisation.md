---
tags:
  - degree/compsys/databases
---
![[Databases MOC 🌍]]

### Why we Normalise

The biggest issues are redundancy and anomalies.

##### Insertion Anomaly 
- New records duplicate existing data 
- Cannot add partial records (NULL [[Relational Data Model#Keys|Primary Key]])

##### Modification Anomaly 
- Modifying one value leads to inconsistencies 

##### Deletion Anomaly 
- Losing other data as a side effect of deleting one.

---
### Normal Forms 

- 1st Normal Form 
- 2nd Normal Form 
- 3rd Normal Form 
- Boyce-Codd Normal Form 
- 4th Normal Form 
- 5th Normal Form 

---
### 1st Normal Form 

A table is in 1st Normal Form if it has 
- No repeating groups 

A repeating group is an attribute with multiple values.

If the number of repetitions, you may use separate attributes.
e.g. splitting a *name* into *first name* and *last name*.

##### Solutions
There are two general solutions to making something first normal form.
- Flattening which is filling empty cells with repeating values.
- Creating separate relations with primary / foreign keys.

---
### 2nd Normal Form 

A table is in 2nd normal form if
- It's in [[#1st Normal Form]]
- It has no partial functional dependencies. Every non-key attribute is dependent on the whole primary key.

2NF is only relevant for relations with composite keys.

##### Solution
The solution to making something 2NF is
- Remove the partially dependent attribute.
- Place them in a new relation along with a copy of their determinant.

1NF Table with a lot of duplicate data.
![[Pasted image 20240207125011.png]]

We change that into
![[Pasted image 20240207125052.png]]
![[Pasted image 20240207125104.png]]
![[Pasted image 20240207125115.png]]
This still has some redundancy.

---
### 3rd Normal Form

A table is in 3rd Normal Form if
- It is in [[#2nd Normal Form]]
- It has no [[Functional Dependencies#Transitive Functional Dependency|Transitive Functional Dependencies]]

You cannot have $A \to B$ and $B \to C$.
Must be $A \to C$, without any $B$ in between.

![[Pasted image 20240207155106.png]]
Here, the *ownerNo* depends on the *propertyNo*.
And the *oName* depends on the *propertyNo*.
But the *oName* also depends on the *ownerNo*.

This is a violation of 3rd Normal Form.

##### Solution 
To resolve this, we 
1. Remove the transitively dependent attributes and
2. Place them in a new relation along with a copy of their determinant.

![[Pasted image 20240207155335.png]]



---
### Additional Information

- [Wikipedia]
- [[Comp Sys Part 3 Lecture 6 Normalisation.pdf|Computer Systems Part 3 Lecture 6 Normalisation]]
- [Maybe Practical Q and As]
