---
tags:
  - degree/compsys/databases
---
![[Databases MOC 🌍]]

SQL is declarative.
Declarative queries are transformed to a procedural form.

The declarative specifies what data to retrieve, while the procedural specifies how to retrieve the data.

Relations are considered as sets of elements
- An element is a tuple of attribute values 
- each row in a table is one element of the set.

Relational Calculus (declarative part)
- uses set theoretic expressions 
- defines a new set based on existing ones.

Relational Algebra (procedural part)
- uses operators to construct a new set from existing ones.

Relational Algebra are:
- Equivalent languages. They can define/create the same sets. For each calculus expression there is an algebraic expression.
- Non-user-friendly. They're used as a formal basis for defining and comparing querying languages.
- Modern ones:
	- Are relationally complete 
	- Have additional operations 
	- Not Turing complete.

### Relational Calculus 

![[Predicate]]

![[Proposition]]

Let $P(x)$ and $Q(x)$ be two predicates.

The set of all $x$ such that both $P(x)$ and $Q(x)$ are true is
$$
\{x | P(x) \land Q(x)\}
$$

The set of all $x$ such that either $P(x)$ or $Q(x)$ are true is
$$
\{x | P(x) \lor Q(x)\}
$$

The set of all $x$ such that $P(x)$ is not true is
$$
\{x | \sim P(x)\}
$$

##### Domain Relational Calculus 

Variables values are attribute values.

Notation:
$$
\{a_{1}, \ldots, a_{n} | P(a_{1}, \ldots, a_{n})\}
$$

Example: *Select all tuples from relation $R$, for which all predicate $P$ holds*
$$
\{ a_{1}, \ldots, a_{n} | R(a_{1}, \ldots, a_{n}) \land P(a_{1}, \ldots, a_{n}) \}
$$
Example: *Select all $A$ from relation $R(A,B)$, for which the value of $B$ is greater than $0$*
$$
\{ a | (\exists b) (R(a,b) \land b > 0) \}
$$

##### Tuple Relational Calculus 

Variables values are tuples.

Notation: 
$$\{t | P(t)\}$$

To specify that tuple $s$ should be in relation *Staff*, use as a predicate
$$
\text{Staff}(s)
$$
Use `s.name` to for named elements in tuple $s$.

Use quantifiers for more complex predicates: for all $\forall$ and exists $\exists$.

Example: *Select all tuples from relation $R$, for which all predicate $P$ holds*
$$\{t | R(t) \land P(t)\}$$

Example: *Select all $A$ from relation $R(A,B)$, for which the value of $B$ is greater than $0$*
$$
\{ t.A | R(t) \land t.B > 0 \}
$$

Example: *All tuples $s$ of the relation `Staff` with attribute `salary > 10000`*
$$
\{ s | \text{Staff} \land s.\text{salary} > 10000 \}
$$

Example: *The salaries of all members of staff who earn more than 10k*
$$
\{ s.\text{salary} | \text{Staff}(s) \land s.\text{salary} > 10000 \}
$$

Example: *The names of all staff who work in a branch in London*
$$
\begin{align*}
\{ s.\text{name} | \text{Staff}(s) &\land (\exists b)(\text{Branch}(b) \\
&\land (b.\text{branchNo} = s.\text{branchNo}) \\
&\land (b.\text{city} = \text{'London'})) \}
\end{align*}
$$

The relational calculus only describes what conditions have to be fulfilled. It says nothing about how the tuples are actually found.  

---
### Relational Algebra

This is the procedural part, specifying operations to construct a new set from existing ones.

The basic unary operations (operate on one set):
- [[#Selection]] ($\sigma$)
- [[#Projection]] ($\pi$)
- [[#Rename]] ($\varrho$)

The basic binary operations (operates on two sets): 
- [[#Union]] ($\cup$)
- [[#Set Difference]] ($-$)
- [[#Cartesian Product]] ($\times$)

There are also some derived operations. These can be expressed in terms of the basic operations.
- Intersection ($\cap$)
- Division ($\div$)
- Join ($\bowtie$)

---
##### Selection ($\sigma$)

$$
\sigma_{\text{condition}} (R)
$$
This is a unary operation.

It selects the subset of tuples/rows from $R$ that satisfy the specified condition/predicate.

The corresponding SQL:
```sQL
SELECT * FROM R WHERE <condition>
```

Example: *List all staff whose salary is greater than 12000*
$$
\sigma_{\text{salary} > 12000} (\text{Staff})
$$

---
##### Projection 

$$
\Pi_{\text{col1}, \text{col2}, \ldots} (R)
$$
This is a unary operation.

It selects the specified subset of attributes/columns from $R$.
It eliminates duplicates.

The corresponding SQL:
```sQL
SELECT DISTINCT col1, col2, [, ...]
FROM R
```

Example: *For all staff, list staffNo, fName, lName and salary*
$$
\Pi_{\text{staffNo}, \text{fName}, \text{lName}, \text{salary}} (\text{Staff})
$$

---
##### Combining Selection and Projection

$$
\begin{align*}
&\Pi_{\text{col1}, \text{col2}, \ldots} (\sigma_{\text{predicate}} (R))\\
\\
&\sigma_{\text{predicate}} (\Pi_{\text{col1}, \text{col2}, \ldots} (R))
\end{align*}
$$

The outer operation is applied to the result of the inner operation.

The corresponding SQL
```sQL
SELECT DISTINCT col1, col2 [, ...]
FROM R
WHERE <condition>
```

Example: *List staffNo, fName, lName and salary of all staff with a salary greater than 12000*.
$$
\Pi_{\text{staffNo}, \text{fName}, \text{lName}, \text{salary}} (\sigma_{\text{salary} > 12000} (\text{Staff}))
$$

---
##### Union

$$
A \cup B
$$
This is a binary operation.

It selects tuples that are in $A$ or in $B$.
It eliminates duplicates.

The corresponding SQL
```sQL
SELECT ...
UNION [ALL]
SELECT ...
```

Example: *List all cities where there is either a branch or a property.*
$$
\Pi_{\text{city}} (\text{Branch}) \cup \Pi_{\text{city}} (\text{Property})
$$

---
##### Set Difference 

$$
A - B
$$
This is a binary operation.

Selects tuples that are in $A$ but not in $B$.
Removes all tuples from $A$ that are also in $B$.

The corresponding SQL 
```sQL
SELECT ...
{ MINUS | EXCEPT }
SELECT ...
```

Example: *List all cities where there is a property but not a branch.*
$$
\Pi_{\text{city}} (\text{Property}) - \Pi_{\text{city}} (\text{Branch})
$$

---
##### Intersection

$$
A \cap B
$$
This is a binary operation.

Selects tuples that are in $A$ and in $B$.

The corresponding SQL 
```sQL
SELECT ...
INTERSECT
SELECT ...
```

Example: *List all cities where there is both a branch and a property.*
$$
\Pi_{\text{city}} (\text{Property}) \cap \Pi_{\text{city}} (\text{Branch})
$$

Intersection is a derived operation:
$$
\begin{align*}
A \cap B &= A - (A - B)\\
&= B-(B-A)
\end{align*}
$$

---
##### Union Compatibility 

To compute $A \cap B$, $A - B$ or $A \cup B$, the schemata of $A$ and $B$ must match.

To be union compatible:
- They must have the same number of attributes.
- Each pair of matching attributes must have the same domain.
- Attributes names are ignored.

If one of the relations has additional attributes, use projection $\Pi$ to create union-compatible relations.
$$
\begin{align*}
\Pi_{\text{city}} (\text{Property}) &\cup \Pi_{\text{city}} (\text{Branch})\\
\\
\Pi_{\text{city}} (\text{Property}) &- \Pi_{\text{city}} (\text{Branch})\\
\\
\Pi_{\text{city}} (\text{Property}) &\cap \Pi_{\text{city}} (\text{Branch})
\end{align*}
$$

---
##### Cartesian Product 

$$
A \times B
$$
This is a binary operation

It generates all possible combinations of tuples in $A$ and in $B$ by concatenating them.

Results in $r_{A} \times r_{B}$ tuples with $c_{A} + c_{B}$ attributes, where $r$ is the number of rows and $c$ is the number of columns.

It has no compatibility requirements.

The corresponding SQL
```sQL
SELECT * FROM A,B
```
or
```sQL
SELECT * FROM A CROSS JOIN B
```

If the property table and branch table look like this:

| propertyNo | city |
| ---- | ---- |
| P15 | Aberdeen |
| P98 | London |
| P21 | Glasgow |

| branchNo | city |
| ---- | ---- |
| B005 | London |
| B007 | Glasgow |
| B003 | Bristol |

Then, Property $\times$ Branch will be

| propertyNo | Property.city | branchNo | Branch.city |
| ---- | ---- | ---- | ---- |
| P15 | Aberdeen | B005 | London |
| P98 | London | B005 | London |
| P21 | Glasgow | B005 | London |
| P15 | Aberdeen | B007 | Glasgow |
| P98 | London | B007 | Glasgow |
| P21 | Glasgow | B007 | Glasgow |
| P15 | Aberdeen | B003 | Bristol |
| P98 | London | B003 | Bristol |
| B21 | Glasgow | B003 | Bristol |

Often we are only interested in specific combinations, in which we use the select operation to filter criterion.

SQL 
```sQL
SELECT *
FROM A CROSS JOIN B
WHERE <criterion>
```
or
```sQL
SELECT *
FROM A JOIN B ON <criterion>
```

Example: *List all combinations of properties and branches in the same city*
$$
\sigma_{\text{Property.city} = \text{Branch.city}} (\text{Property} \times \text{Branch})
$$

---
##### Rename

- Algebraic expressions very quickly become very complex.

- We can decompose them into a series of smaller operations, then give names to those intermediate operations to reuse them.

- We can use the assignment operation $\text{Name} \leftarrow \text{<expression>}$.

- But this creates multiple expressions.

An alternative is the rename operation.
- $\rho_{Y} (X)$ returns $X$ renamed as $Y$.
- $\rho_{Y(A,B, C, \ldots)} (X)$ returns $X$ renamed as $Y$, with attributes renamed as $A, B, C, \ldots$

This is useful for reusing the same relation in different roles.

Example: *Who are the grandparents of Thomas*.
$$
\small{
\Pi_\text{A.Parent} (\sigma_{(\text{A.Child} = \text{B.Parent} \land \text{B.Child} = \text{'Thomas'})} (\rho_{A} (\text{Family}) \times \rho_{B} (\text{Family})))
}
$$

Example: *Find the largest salary*
$$
\small{
\begin{align*}
&\text{NotLargest} \leftarrow \Pi_{\text{Staff.salary}} (\sigma_{\text{Staff.salary} < \text{Other.salary}} (\text{Staff} \times \rho_{\text{Other}} (\text{Staff})))
\\
\\
&\Pi_{\text{Staff.salary}} (\text{Staff}) - \text{NotLargest}
\end{align*}
}
$$
Here we find all the salaries that are not the largest.
Then we remove them.

---
##### Division

$$
A \div B
$$
A binary operation.
Only keeps tuples from $A$ that exist in all possible combinations with $B$.

Non-basic and not part of SQL but appears often in applications.

$B$ has a subset of attributes from $A$.
$$
\begin{align*}
&A(X_{1}, X_{2}, \ldots, Y_{1}, Y_{2}, \ldots)\\
&B(Y_{1}, Y_{2}, \ldots)
\end{align*}
$$

$$
A \div B = \Pi_{X_{1}, X_{2}, \ldots} (A) - \Pi_{X_{1}, X_{2}, \ldots} ((\Pi_{X_{1}, X_{2}, \ldots} (A) \times B) - A )
$$

---
##### Joins 
$\DeclareMathOperator{innerjoin}{\Join}\DeclareMathOperator{leftjoin}{⟕}\DeclareMathOperator{rightjoin}{⟖}\DeclareMathOperator{fulljoin}{⟗}$
$$
A \innerjoin_{\text{attr1} = \text{attr2}} B
$$
```sQL
A JOIN B ON <criterion>
```

$$
A \leftjoin_{\text{attr1} = \text{attr2}} B
$$
```sQL
A LEFT JOIN B ON <criterion>
```

$$
A \rightjoin_{\text{attr1} = \text{attr2}} B
$$
```sQL
A RIGHT JOIN B ON <criterion>
```

$$
A \fulljoin_{\text{attr1}=\text{attr2}} B
$$
```sQL
A FULL JOIN B ON <criterion>
```





---
### Additional Information

- [[Comp Sys Part 3 Lecture 9 Relational Calculus and Algebra.pdf]]
