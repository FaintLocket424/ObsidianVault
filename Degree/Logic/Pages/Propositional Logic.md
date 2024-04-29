---
tags:
  - degree/compthink/logic
---
![[Logic MOC 🌍]]

### The Rules of Propositional Logic

It's the most fundamental logic, and lies at the heart of many other logics.

It's a formalisation of day-to-day, common-sense reasoning.

A key part of it is [[Proposition|Propositions]]

Propositions are represented by [[Propositional Variable|Propositional Variables]].

Syntax
- New Propositions are called:
	- Formulae
	- Boolean formulae
	- Propositional formulae
	- Compound Propositions
- They're formed from [[Propositional Variable|Propositional Variables]] and formulae by repeated use of the [[Logical Operator|Logical Operators]].

---
### Construction

You take the logical operators with two [[Proposition|Propositions]] and yield a new one.

- $\phi \land \psi$ 
- $\phi \lor \psi$
- $\phi \implies \psi$
- $\phi\iff\psi$

The operator $\lnot$ only takes one [[Proposition]]
- $\lnot \phi$

You can also use parentheses like you normally would.

- $(\phi\land\psi)\lor\omega$

---
### More Notation

If we have a propositional formula $\phi(x_{1},x_{2},\dots,x_{n})$ then we can call an assignment $f$ of either $T$ or $F$ to each $x_{1}$, $x_{2}$, $x_{n}$.
$$f:\{x_{1},x_{2},\dots,x_{n}\}\rightarrow \{T,F\}$$
We call this a truth assignment for $\phi$.

We say that $\phi$ evaluates to $T$ or $F$ under $f$.

If $f$ evaluates $\phi$ to $T$ then $f$ satisfies $\phi$.

If $\phi$ evaluates to $T$ for every $f$ then $\phi$ is a [[Tautology]].
If $\phi$ evaluates to $F$ for every $f$ then $\phi$ is a [[Contradiction]]

We also have [[Literal|Literals]].

---
### Truth Tables
| $p$ | $q$ | $p\land q$ | $p \lor q$ | $\lnot p$ | $p \implies q$ | $p \iff q$ |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| $T$ | $T$ | $T$ | $T$ | $F$ | $T$ | $T$ |
| $T$ | $F$ | $F$ | $T$ | $F$ | $F$ | $F$ |
| $F$ | $T$ | $F$ | $T$ | $T$ | $T$ | $F$ |
| $F$ | $F$ | $F$ | $F$ | $T$ | $T$ | $T$ |

We can find what a formula evaluates to for each input using this method:

![[Pasted image 20240123211447.png]]
![[Pasted image 20240123211511.png]]
![[Pasted image 20240123211528.png]]
![[Pasted image 20240123211540.png]]
![[Pasted image 20240123211549.png]]
![[Pasted image 20240123211604.png]]
So this expression evaluates to false.

The rest evaluate to:
![[Pasted image 20240123211635.png]]

---
### Logical Equivalence

If two [[Proposition|Propositional Formulae]] have identical truth tables, they are logically equivalent.

If $\psi$ and $\Phi$ are logically equivalent, then $\psi\equiv\Phi$.

---
### De Morgan's Law

$$
\begin{align*}
\lnot (A \land B \land \ldots \land Z) &\equiv \lnot A \lor \lnot B \lor \ldots \lor \lnot Z\\
\\
\lnot (A \lor B \lor \ldots \lor Z) & \equiv \lnot A \land \lnot B \land \ldots \land \lnot Z
\end{align*}
$$
Often used to simplify formulae with regard to negations.

The law can be applied to parts within a formula, not just the whole thing.

---
### Distribution Laws

$$
\begin{align*}
a \lor (b \land c \land \ldots \land z) &\equiv (a \lor b) \land (a \lor c)\land \ldots \land (a \lor z)\\
\\
a \land (b \lor c \lor \ldots \lor z) &\equiv (a \land b) \lor (a \land c) \lor \ldots \lor (a \land z)
\end{align*}
$$

---
### Functional Completeness

Propositional logic uses the [[Logical Operator|Logical Connectives]] like $\{\land,\lor,\lnot,\implies,\iff \}$.

We say a set $\xi$ of [[Logical Operator|Logical Connectives]] is functionally complete if any propositional formula can be constructed using only the connectives from $\xi$.

$\{\land,\lor,\lnot\}$ is functionally complete.

This is because any truth table can be represented in [[Conjunctive Normal Form]] and [[Disjunctive Normal Form]].

