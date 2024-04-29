---
tags:
  - degree/compthink/logic
---
![[Logic MOC 🌍]]

### Resolution

In [[Natural Deduction]] we have the rule of inference known as resolution.

![[Natural Deduction#Resolution]]

This forms the basis of the proof system for [[Propositional Logic]] known as Resolution.

However, the basic rule of Resolution is more general than shown above.
![[Pasted image 20240221094837.png]]
This is the only rule for Resolution.

[[Natural Deduction]] proves theorems from scratch, but Resolution takes a given formula and decides if it's a theorem or not.

The formula $\upvarphi \Rightarrow \uppsi$ is [[Propositional Logic#Logical Equivalence|Logically Equivalent]] to $\lnot \upvarphi \lor \uppsi$.

Steps for Resolution
- We are given a propositional formula $\upvarphi$
- We take $\lnot \upvarphi$ and write it in [[Conjunctive Normal Form]] as $C_{1} \land C_{2} \land \ldots \land C_{m}$
- We start with the clauses $C_{1}, C_{2}, \ldots, C_{m}$
- We continually apply the resolution rule to infer new clauses.
	- If we infer the empty clause $\emptyset$, $\upvarphi$ is a theorem.
	- If we cannot infer any new clauses, $\upvarphi$ is not a theorem.

When resolving, we are allowed to delete repeated literals in any clause.

Resolution is sound and complete.

But the worst case Resolution involves an exponential number of applications.

##### Example 1
Consider the propositional formula $\upvarphi$
$$
\small{
\begin{gathered}
(((A \land W) \Rightarrow I) \land (\lnot A \Rightarrow P) \land \\
(\lnot W \Rightarrow S) \land \lnot I \land (D \Rightarrow (\lnot P \land \lnot S))) \Rightarrow \lnot D
\end{gathered}
}
$$
Now we'll remove the $\Rightarrow$ at the end.
$$
\small{
\begin{gathered}
\lnot(((A \land W) \Rightarrow I) \land (\lnot A \Rightarrow P) \land \\
(\lnot W \Rightarrow S) \land \lnot I \land (D \Rightarrow (\lnot P \land \lnot S))) \lor \lnot D
\end{gathered}
}
$$
Now take $\lnot \upvarphi$
$$
\small{
\begin{gathered}
(((A \land W) \Rightarrow I) \land (\lnot A \Rightarrow P) \land \\
(\lnot W \Rightarrow S) \land \lnot I \land (D \Rightarrow (\lnot P \land \lnot S))) \land D
\end{gathered}
}
$$
Now we write $\lnot \upvarphi$ in [[Conjunctive Normal Form]]
$$
\small{
\begin{align*}
(\lnot A \lor \lnot W \lor I) \land (A \lor P) \land (W \lor S)\\ \land \lnot I \land (\lnot D \lor \lnot P) \land (\lnot D \lor \lnot S) \land D
\end{align*}
}
$$
This gives us the set of clauses to apply resolution to
1. $\lnot A \lor \lnot W \lor I$
2. $A \lor P$
3. $W \lor S$
4. $\lnot I$
5. $\lnot D \lor \lnot P$
6. $\lnot D \lor \lnot S$
7. $D$

Our new clauses
8. $\lnot A \lor \lnot W$ - 1 and 4
9. $P \lor \lnot W$ - 2 and 8
10. $P \lor S$ - 3 and 9
11. $\lnot D \lor S$ - 5 and 10
12. $\lnot D \lor \lnot D$ - 6 and 11
13. $\lnot D$ - 7 and 12
14. $\emptyset$ - 7 and 13

Since we have inferred the empty clause, $\upvarphi$ is a theorem and therefore a [[Tautology]].

##### Example 2

Let $\upvarphi$ be the formula
$$
((p \lor q) \land (\lnot p \lor \lnot q) \land (r \Rightarrow (p \land q))) \Rightarrow r
$$
So $\lnot \upvarphi$ is
$$
\lnot (((p \lor q) \land (\lnot p \lor \lnot q) \land (r \Rightarrow (p \land q))) \Rightarrow r)
$$
So $\lnot \upvarphi$ in [[Conjunctive Normal Form]] is
$$
(p \lor q) \land (\lnot p \lor \lnot q) \land (\lnot r \lor p) \land (\lnot r \lor q) \land \lnot r
$$
So now we have our clauses to apply Resolution to
1. $p \lor q$
2. $\lnot p \lor \lnot q$
3. $\lnot r \lor p$
4. $\lnot r \lor q$
5. $\lnot r$

And now we can create new clauses 
6. $q \lor \lnot q$ - 1 and 2 over $p$
7. $p \lor \lnot p$ - 1 and 2 over $q$
8. $\lnot q \lor \lnot r$ - 2 and 3 over $p$
9. $\lnot p \lor \lnot r$ - 2 and 4 over $q$
10. $p \lor \lnot r$ - 3 and 7 over $p$
11. $\lnot r \lor \lnot r$ - 3 and 9 over $p$
12. $q \lor \lnot r$ - 4 and 6 over $q$
13. $\lnot r \lor \lnot r$ - 4 and 8 over $q$

These clauses do not help us get closer to anything.
- 6 and 7 will not yield any new clauses
- 10 and 12 are clauses that exist already 
- 11 and 13 are $\lnot r$ which already exists.

So $\upvarphi$ is not a theorem and is not a [[Tautology]].

---
### Additional Information

- [[Comp Think Part 2 Lecture 6 Resolution for Prop Logic.pdf]]
- [[Comp Think Part 2 Lecture 7 Resolution for Prop Logic Cont.pdf]]

