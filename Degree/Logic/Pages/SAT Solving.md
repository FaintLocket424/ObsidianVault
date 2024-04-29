---
tags:
  - incomplete
  - degree/compthink/logic
---
![[Logic MOC 🌍]]

### The Motivation
Suppose we design a complex system, which may contain various components like sensors, networks computers etc. All these components are using software.

We have requirements on how the system should function, for example safety, reliability, security, availability, absence of deadlocks etc.

How can we ensure the system satisfies these requirements?

##### Example 
Say we have a circuit C1 which we want to replace with the circuit C2. We want to be sure C2 is correct.
If we know C1 is correct, it is sufficient to prove that C2 is [[Propositional Logic#Logical Equivalence|Logically Equivalent]] to C1.

---
### Automated Reasoning 

Formal proofs proceed via reasoning, deriving conclusions from facts.

The applications for automated reasoning:
- SAT solvers 
- Software and hardware verification 
- Artificial Intelligence 
- Circuit Design 
- Cryptography 
- Databases 
- Theorem proving in mathematics 

There are different logics we can use:
- Classical logic
- Temporal logic
- Modal logic
- Many-valued logics 
- Fuzzy logic 
- Non-monotonic logic 
But in this we mainly consider [[Propositional Logic]].

---
### Satisfaction and Consequence 

Let $\alpha$ and $\beta$ be two [[Proposition|Propositional Formulae]]. Then $\beta$ is a logical consequence of $\alpha$, denoted $\alpha \vDash \beta$ if every truth assignment that [[Satisfiable|Satisfies]] $\alpha$ also satisfies $\beta$.

Also said that $\alpha$ entails $\beta$.

For two [[Proposition|Propositional Formulae]] $\alpha$ and $\beta$, we have $\alpha \vDash \beta$ iff the formula $\alpha \land \lnot \beta$ is [[Unsatisfiable]].

Similarly, $\alpha_{1}, \ldots, \alpha_{n} \vDash \beta$ iff $\alpha_{1} \land \ldots \land \alpha_{n} \land \lnot \beta$ is [[Unsatisfiable]].

So, checking for entailment is the same as checking for [[Unsatisfiable|Unsatisfiability]]. 

---
### Clauses 

Literals are our variables $x, y, z$ and their negations $\bar{x}, \bar{y}, \bar{z}$.

Clauses are formulas in the form $\ell_{1} \lor \ldots \lor \ell_{n}$ where $\ell_{i}$ is a literal.

[[Conjunctive Normal Form]] is $C_{1} \land \ldots \land C_{m}$ where each $C_{i}$ is a clause.

A clause-set is a set of clauses. Each [[Conjunctive Normal Form|CNF]] can be thought of as a clause-set $\{ C_{1}, \ldots, C_{m} \}$

Take the clause-set $F$
$$
F = \{ \{u, \bar{v}, \bar{y}\}, \{\bar{u}, z\}, \{\bar{v}, \bar{w}\}, \{w, \bar{x}\}, \{x, y, \bar{z}\} \}
$$
We can take $\operatorname{var}(F)$ 
$$
\operatorname{var}(F) = \{u, v, w, x, y, z \}
$$
Also, since $F$ is a set, the order of the clauses does not matter.

---
### DIMACS Format

DIMACS stands for *Centre for Discrete Mathematics and Theoretical Computer Science*.

The format was introduced in 1993 as a simple text format for representing clause-sets.
- Variables are indicated as positive integers, negative literals by negative integers.
- Any line starting with a $c$ is a comment.
- At the top of the file is a line of form `p cnf N M` where `N` is the number of the largest variable and `M` is the total number of clauses in the clause-set.
- Clauses are separated by a zero "0".

Here is an example for set $F$
$$
F = \{ \{u, \bar{v}, \bar{y}\}, \{\bar{u}, z\}, \{\bar{v}, \bar{w}\}, \{w, \bar{x}\}, \{x, y, \bar{z}\} \}
$$
written in DIMACS format
```DIMACS
c This is an example 
c NOTE: Satisfiable 
c
p cnf 6 5
1 -2 -5 0
-1 6 0
-2 -3 0
3 -4 0
-4 5 -6 0
```

---
### Converting to CNF 

Let $\uppsi_{n}$ be the formula
$$
(x_{1} \land y_{1}) \lor \cdots \lor (x_{n} \land y_{n})
$$
When converted to CNF, it gets very large.

For every $n>1$, there is a [[Proposition|Propositional Formulae]] of length $2n$ which at least $2^{n}$ clauses.

---
### Tseitin's Algorithm

Input a propositional formula $\uppsi$. Assume all double negations are eliminated. Initially, put $F = \emptyset$.

While $\uppsi$ has the sub-formula $\ell \circ m$ where $\circ$ is any binary [[Logical Operator|Logical Connective]] and $\ell, m$ are literals:
- Replace in $\uppsi$ the sub-formula $\ell \circ m$ with a new variable $x_{\ell \circ m}$.
- Extend the clause set $F \cup F_{\ell \circ m}$ and use this as the new $F$. And $F_{\ell \circ m}$ is a clause-set [[Propositional Logic#Logical Equivalence|Logically Equivalent]] to the propositional formula $x_{\ell \circ m} \iff (\ell \circ m)$.

Now $\uppsi$ is a single literal $\ell$. Add the unit clause $\{ \ell \}$ to $F$ and halt.

The output is the clause-set $F$.

Note that we can stop as soon as $\uppsi$ is in [[Conjunctive Normal Form|CNF]] and add the clauses of $F_{\uppsi}$ to $F$.

---
### Defining Clause-Sets
##### $F_{\ell \land m}$

The clause-set $F_{\ell \land m}$ needs to be logically equivalent to the formula 
$$
x \equiv \ell \land m
$$
We derive $F_{\ell \land m}$ using the "slow" method:
- $x \equiv \ell \land m$
- $[x \implies (\ell \land m)] \land [(\ell \land m) \implies x]$
- $[\lnot x \lor (\ell \land m)] \land [\lnot(\ell \land m) \lor x]$
- $(\lnot x \lor \ell) \land (\lnot x \lor m) \land (\lnot \ell \lor \lnot m \lor x)$
Hence
$$
F_{\ell \land m} = \{ \{\bar{x}, \ell\}, \{\bar{x}, m\}, \{\bar{\ell}, \bar{m}, x\} \}
$$
##### $F_{\ell \lor m}$
$$
F_{\ell \lor m} = \{ \{\overline{\ell}, x_{\ell \lor m}\}, \{\overline{m}, x_{\ell \lor m}\}, \{ \ell, m, \overline{x_{\ell \lor m}} \} \}
$$
##### $F_{\ell \Rightarrow m}$
$$
F_{\ell \Rightarrow m} = \{ \{ \ell, x_{\ell \Rightarrow m} \}, \{ \overline{m}, x_{\ell \Rightarrow m} \}, \{ \overline{\ell}, m, \overline{x_{\ell \Rightarrow m}} \} \}
$$
##### $F_{\ell \Leftrightarrow m}$ 
$$
F_{\ell \Leftrightarrow m} = \{ \{ \ell, m, x_{\ell \Leftrightarrow m} \}, \{ \overline{\ell}, \overline{m}, x_{\ell \Leftrightarrow m} \}, \{ \overline{\ell}, m, \overline{\ell \Leftrightarrow m} \}, \{ \ell, \overline{m}, \overline{x_{\ell \Leftrightarrow m}}\} \}
$$
##### $F_{\ell \oplus m}$
$$
F_{\ell \oplus m} = \{ \{ \overline{\ell}, m, x_{\ell \oplus m} \}, \{ \ell, \overline{m}, x_{\ell \oplus m} \}, \{ \ell, m, \overline{x_{\ell \oplus m}} \}, \{ \overline{\ell}, \overline{m}, \overline{x_{\ell \oplus m}} \} \}
$$

#### Example 
$$
\begin{align*}
\uppsi &= \lnot (x \Rightarrow (y \Rightarrow z)))\\
F &= \emptyset\\
\\
\uppsi &= \lnot (x \Rightarrow u)\\
F &= \{ \{ y, u \}, \{ \overline{x}, u \}, \{ \overline{y}, x, \overline{u} \} \}\\
\\
\uppsi &= \lnot v\\
F &= \{ \{ y, u \}, \{ \overline{x}, u \}, \{ \overline{y}, x, \overline{u} \}, \{ x, v \}, \{ \overline{u}, v \}, \{ \overline{x}, u, \overline{v} \} \}
\end{align*}
$$

---
### Results 

Let $\uppsi$ be a [[Proposition|Propositional Formulae]] and $T(\uppsi)$ the clause-set obtained using the fast transformation.
- $\uppsi$ and $T(\uppsi)$ are equisatisfiable.
- $\uppsi$ is a tautology iff $T(\lnot \uppsi)$ is [[Unsatisfiable]].
- Let $n$ be the number of occurrences of [[Logical Operator|Logical Connectives]] in $\uppsi$. Then $T(\uppsi)$ contains at most $4n + 1$ clauses, with each clause containing at most 3 literals. Thus $| T(\uppsi) | = O(n)$, so the number of clauses in $T(\uppsi)$ is linear in the number $n$ of occurrences of binary connectives in $\uppsi$.
- $\uppsi$ and $T(\uppsi)$ are equisatisfiable but not [[Propositional Logic#Logical Equivalence|Logically Equivalent]].

---
### A Search Algorithm 

An algorithm $A(F)$ which outputs *sat* or *unsat*.

```Pseudocode
if var(F) = empty set then
	if F = empty set then
		return sat 
	else 
		return unsat 
	endif 
else
	choose x in var(F)
	// X is the branching variable 
	if A(F[x=0]) == sat then 
		return sat 
	else if A(F[x=1]) == sat then 
		return sat 
	else 
		return unsat 
	endif
endif
```

---
### Pure Literal Elimination

Let $F'$ be the clause-set obtained from $F$ by removing all clauses that contain [[Pure Literal|Pure Literals]].

Then $F$ and $F'$ are equisatisfiable.

We denote $PL(F)$ to be the smallest clause-set that can be obtained from $F$ by repeated applications of pure literal elimination.

##### Example 
$$
F = \{ \{ x, y \}, \{ \overline{y}, \overline{z} \}, \{ z, x \}, \{ u, \overline{z} \} \}
$$
Applying pure literal elimination we get 
$$
F' = \{ \{ \overline{y}, \overline{z} \} \}
$$
Now $\overline{y}$ and $\overline{z}$ are pure literals of $F'$, and we can apply pure literal elimination again.
$$
PL(F) = \emptyset
$$
$F$ and $PL(F)$ are always equisatisfiable.

---
### Unit Propagation 

When a clause-set $F$ contains a unit clause $\{ \ell \}$, we can obtain by unit propagation the clause-set $F[\ell=1]$ from $F$.

We write $UP(F)$ for the clause-set obtained from $F$ by applying unit propagation.

$F$ and $UP(F)$ are always equisatisfiable.
##### Example 
$$
F = \{ \{ x, y \}, \{ \overline{y} \}, \{ z, \overline{x}, v \} \}
$$
By unit propagation, we obtain 
$$
F' = \{ \{ x \}, \{ z, \overline{x}, v \} \}
$$
With another unit propagation we get 
$$
UP(F) = F'' = \{ \{ z, v \} \}
$$
---
### UP vs PL

It's not clear whether we should apply UP or PL first.

For any clause-set $F$, we have 
$$
UP(PL(UP(F))) = PL(UP(F))
$$
And there is a clause-set $F$ such that
$$
PL(UP(PL(F))) \ne UP(PL(F))
$$

##### DPLL Algorithm 
An algorithm DPLL(F) which outputs *sat* or *unsat*.

```Pseudocode
F := UP(F)
F := PL(F)
if var(F) = empty set then 
	if F = empty set then 
		return sat 
	else 
		return unsat 
	endif 
else 
	choose x in var(F) 
	// x is the branching variable 
	if A(F[x=0]) == sat 
		return sat 
	else if A(F[x=1]) == sat 
		return sat 
	else 
		return unsat 
	endif
endif
```

---
### Conflict-Driven Clause Learning (CDCL)

- CDCL is based on an iterative version of DPLL.
- Clauses of conflict are cached and learnt.
- Learnt clauses allow us to prune the search space in different parts of the search encountered later.

Initially:
- $F$ is the given clause set 
- $\tau$ is the empty assignment.

![[Pasted image 20240227171534.png]]

![[Pasted image 20240227171540.png]]

The subroutines `CONFLICT-CLAUSE`, `BACKTRACK`, `CHOOSE VARIABLE` and `VALUE` are based the heuristics and strategy of the particular solver.

The current assignment $\tau$ is associated with the set $D$ of literals that are true under $\tau$. So, if $\tau = \{ (x,1), (y,0) \}$ then $D = \{ x, \overline{y} \}$. The literals in $D$ are called decision literals.

The algorithm also remembers the order in which decisions literals are added to $D$.

In the step `BACKTRACK`, one or more most recent variable assignment is undone. This causes a backtracking.

Instead of UP the solver can use more sophisticated propagation techniques known as Boolean constraint propagation (BCP).
##### Example 
$$
\begin{align*}
F &= \{ \{ x,y \}, \{ \overline{x},y \}, \{ x \overline{y} \}, \{ \overline{x}, \overline{y} \} \}\\
\tau &= \emptyset\\
\end{align*}
$$
Then `CHOOSE` $x,1$ and set $\tau = \{ (x,1) \}$

- $\square \in UP(F[\tau])$
- $\{ \overline{x} \} = \text{CONFLICT-CLAUSE}(F, \tau)$
- $F = \{ \{ \overline{x} \}, \{ x,y \}, \{ \overline{x},y \}, \{ x \overline{y} \}, \{ \overline{x}, \overline{y} \} \}$
- $\tau = \emptyset = \text{BACKTRACK} (\{ (x,1) \})$ 

$\square \in UP(F[\tau])$
Since $\tau = \emptyset$ return `unsat`.






---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]
