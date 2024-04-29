---
tags:
  - degree/compsys/databases
---
![[Databases MOC 🌍]]

So far we've had one central DBMS, with users interacting with DBMS using an application program.

### Teleprocessing Architecture 

- This is the traditional and most basic architecture.
- It has one central computer with a single CPU.
- It has many end user terminals, which are all connected to the central computer.
- All data processing is done on the central computer. Terminals send requests, processing is done, then the response is displayed.

- It has tremendous burden on the central computer, which decreases performance.
- The trend is towards downsizing. Replacing expensive mainframe computers with cost effective networks of personal computers.

---
### File-Server Architecture 

Processing is distributed around the local network.
- Has one central file server.
- Every workstation has its own DBMS.
- Workstations request files from the file server.
- File server acts like a shared hard disk, with no DBMS.

Example: *Find the names of staff who work in the branch at 163 Main St*.

The SQL query would be:
```sQL
SELECT fName, lName 
FROM Branch JOIN Staff USING branchNo 
WHERE Branch.street = '163 Main St.'
```

The user's DBMS would request the whole tables Branch and Staff.
- This uses a large amount of network traffic, especially if the tables are large.
- A full copy of the tables is required on each workstation.
- Concurrency / recovery / integrity control is more difficult, especially with multiple DBMSs accessing the same file simultaneously.
A solution to these problems would be the [[#Client-Server Architecture]]

---
### Client-Server Architecture 

This is a two-tier architecture.

The 1st tier is the client
- Requires some resource. 
- Provides user interface.
- Main data processing logic.

The 2nd tier is the server 
- Provides the resource.
- Performs validations and checks.
- Handles database access.

This two tier approach has many advantages 
- Increased performance since many client CPUs work in parallel.
- Reduced hardware costs since only the server needs increased storage and computation.
- Reduced communication costs since less data traffic as only the required data is transmitted.

But the database is still centralised, which makes it not a distributed database.

There are also many problems with the two tier architecture
- Hundreds or thousands of users.
- Many different and complex applications .
- "fat clients" to run all applications.
- It prevents scalability.

An alternative could be the three-tier architecture
- Tier 1 Client - UI
- Tier 2 Application - Data processing/application logic 
- Tier 3 Database - Validation and DB access

##### $n$-Tier Architecture 

It can be extended, separating tasks into $n$ intermediate tiers, to increased flexibility / scalability.

The best example for a client is a web browser.

The advantages:
- Lower hardware cost for the thin clients.
- Easier application maintenance.
- Easier to modify/replace one tier without affecting the others.
- Easier load balancing between the different tiers.
- Maps naturally to web applications.

---
### Distributed DBMS 

- So far, the databases have been centralised database systems, with a single database.

- We can improve database performance with decentralised approach, using networks of computers.

- It can mirror the organisational structure, with it logically distributed into divisions, but physically distributed.

- Its main objectives are to make all data accessible to all units, but to store data near the location where it is most frequently used.

A single logical database that is physically split into fragments.

Each fragment is
- Stored on one or more computers/sites.
- Controlled by a separate DBMS.
- All computers/sites are connected in a network.

Each site has 
- Local autonomy
- Access to global applications.

Not all sites have local applications or data.
All sites have access to global applications.
Data fragments may be replicated at more than one site.

##### Design of a Distributed DBMS 

In addition to ER modelling, we have to consider 
- Fragmentation 
	- How to break a relation into fragments 
	- Fragments can be horizontal / vertical / mixed 
- Allocation 
	- How fragments are allocated at the several sites.
	- Aim is to reach an "optimal" distribution (efficient, reliable...)
- Replication 
	- Which fragments are stored in multiple sites.
- Qualitative information (for fragmentation)
	- The relations/attributes/tuples required for transactions.
	- The type of access (read / write)
- Quantitative information 
	- the frequency with which specific transactions are performed.
	- the usual sites from which transactions are performed.
	- Desired performance criteria for the transactions.
- Strategic objectives 
	1. Locality of reference
		- data to be stored close to where it is used 
		- if a fragment is used at several sites, replication is used.
	2. Reliability and availability 
		- Improved by replication 
		- If one site fails, there are other fragment copies available.
	3. Acceptable performance 
		- bad allocation results in "bottleneck" effects.
		- Bad allocation causes underutilised resources.
	4. Cost of storage capacities
		- Affordable mass storage to be used by sites whenever possible.
		- but must be balanced against locality of reference.
	5. Minimal communication costs 
		- Minimal retrieval costs when max locality of reference.
		- but when replicated data are updated, all copies must be updated and increased network traffic costs.

There are also 4 alternative strategies for the placement of data:
- Centralised 
	- Single database and DBMS 
	- Stored at one site with users distributed across the network.
	- Not a distributed database.
- Fragmented 
	- Database partitions into disjoint fragments.
	- each data item assigned to exactly one site
	- No replication 
- Complete Replication 
	- Complete copy of the database at each site.
- Selective Replication
	- Combination of partitioning, replication and centralisation.

There are three rules for correctness for the fragment placement without replication.
1. Completeness
	- If relation $R$ is decomposed into fragments $R_{1}, R_{2}, \ldots, R_{n}$, each data item that can be found in $R$ must appear in at least one fragment $R_{i}$.
2. Reconstruction 
	- It must be possible to define a relational algebra expression that can reconstruct $R$ from its fragments.
3. Disjointness
	- If a data item appears in $R_{i}$, it should not appear in other fragment.
	- Except for vertical fragmentation, primary key attributes must be repeated for reconstruction.

##### Types of Fragmentation

The three main types of fragmentation 

###### Horizontal
- Fragments contain a subset of the tuples in the relation 
![[Pasted image 20240215130238.png]]

Example:
A relation *Property* contains two property types *'Flat'* and *'House'*.

A horizontal fragmentation is:
- $P_{1} = \sigma_{\text{type} = \text{'House'}} (\text{Property})$
- $P_{2} = \sigma_{\text{type} = \text{'Flat'}} (\text{Property})$
These select a subset of the tuples.

This fragmentation may be useful if we have separate applications dealing with flats and houses.

And it is *correct*:
- Completeness: every tuple is in either $P_{1}$ or $P_{2}$.
- Reconstruction: *Property* can be reconstructed from the fragments $P_{1}$, $P_{2}$ with $\text{Property} = P_{1} \cup P_{2}$
- Disjointness: There is no property that is both a flat and a house.

###### Vertical 
- Fragments contain a subset of the attributes of the relation 
![[Pasted image 20240215130243.png]]

Example: 
*For every staff member at a company:*
- *The payroll department requires `staffNo, position, gender, salary`*
- *The personnel department requires `staffNo, Name, DOB, branchNo`*
*The relation `Staff` contains all members of staff*.

A vertical fragmentation of `Staff` is:
- $S_{1} = \Pi_{\text{staffNo}, \text{position}, \text{gender}, \text{salary}} (\text{Staff})$
- $S_{2} = \Pi_{\text{staffNo}, \text{Name}, \text{DOB}, \text{branchNo}} (\text{Staff})$
Both fragments must include the primary key *staffNo*. This allows for the reconstruction of `Staff` from $S_{1}$ and $S_{2}$.

This fragmentation is useful.
- Fragments are stored at the department that are needed.
- Performance for every department is improved, as the fragments are smaller.

It's also correct:
- Completeness: the primary key belongs to both $S_{1}$ and $S_{2}$. All the other attributes are either in $S_{1}$ or $S_{2}$.
- Reconstruction: `Staff` can be reconstructed from the fragments $S_{1}$, $S_{2}$ using the natural join $S_{1} \innerjoin S_{2}$.
- Disjointness: The fragments have disjoint attributes except for the primary key, which is required for reconstruction.

###### Mixed 
- A vertical fragment that is then horizontally fragmented
- Or a horizontal fragment that is then vertically fragmented.
![[Pasted image 20240215130247.png]]

##### Advantages and Disadvantages of DBMS 

Advantages:
- Reflects organisational structure 
- Improved shareability and local autonomy 
- Improved availability and reliability 
- Improved performance 
- Lower hardware cost 
- Scalability

Disadvantages:
- Complexity 
- Higher maintenance cost 
- Security 
- Integrity control more difficult 
- Design more complex 
- Lack of experience in the industry.



---
### Additional Information

- [[Comp Sys Part 3 Lecture 10 Multi-User and Distributed Architectures.pdf]]
