---
tags:
  - degree/compthink/logic
---
![[Logic MOC 🌍]]

### Rules of Inference 

An argument form in propositional logic is a sequence of formulae
$$
\upvarphi_{1}, \upvarphi_{2}, \ldots, \upvarphi_{n}, \uppsi
$$
and such an argument form is valid if under a truth assignment $f$ such that $\upvarphi_{1}, \upvarphi_{2}, \ldots, \upvarphi_{n}$ evaluate to true, then $\uppsi$ evaluates to true under $f$.

An argument form can also be written as 
$$
\upvarphi_{1}, \upvarphi_{2}, \ldots, \upvarphi_{n} \vdash \uppsi
$$
when it is referred to as a sequent.

The rule of inference corresponding to the above argument form is
$$
\upvarphi_{1}, \upvarphi_{2}, \ldots, \upvarphi_{n} \implies \uppsi
$$
and if the above argument form is valid then this rule of inference is a [[Tautology]].

##### Modus Ponens
The most well-known rule of inference for propositional logic is *modus ponens* aka the *Law of Detachment*.
$$
(p \land (p \implies q)) \implies q
$$
which is also written as
$$
\frac{p \quad\quad p \implies q}{q}
$$
It's strange but just take $p$ as $\upvarphi_{1}$ and $p \implies q$ as $\upvarphi_{2}$.

Any [[Tautology]] in the form $\upvarphi_{1}, \upvarphi_{2}, \ldots, \upvarphi_{n} \implies \uppsi$ gives rise to the rule of inference.

##### Modus Tollens
$$
\frac{\lnot q \quad\quad p \implies q}{\lnot p}
$$
##### Hypothetical Syllogism
$$
\frac{p \implies q \quad \quad q \implies r}{p \implies r}
$$
##### Resolution
$$
\frac{p \lor q \quad \quad \lnot p \lor r}{q \lor r}
$$
##### Example 
Prove that $\lnot D$ holds if these 5 axioms are true:
$$
\begin{align*}
A \land W \implies I\\
\lnot I\\
A \lor P\\
W \lor S\\
D \implies \lnot(P \lor S)
\end{align*}
$$
We could write down all possible truth assignments on $A$, $W$, $I$, $P$, $S$ and $D$. Then retain inly those for which the 5 axioms are true. Then check to see that for all those truth assignments, $\lnot D$ is also true.

This approach would work, but would require $2^{6}=64$ different truth assignments be checked. The proof-theoretic approach can be significantly more efficient than the truth-table approach, especially with large numbers of propositional variables.

Knowing which rules of inference to apply to which formulae so we get a "speedy" proof is difficult.

---
### Natural Deduction 

Consists of a collection of valid rules of inference and is used to obtain proofs of sequents of the form 
$$
\upvarphi_{1}, \upvarphi_{2}, \ldots, \upvarphi_{n} \vdash \uppsi
$$
we assume that we are given $\upvarphi_{1}, \upvarphi_{2}, \ldots, \upvarphi_{n}$ as [[Premises]].

---
### Rules for Conjunction 
##### $\land$-introduction 
$$
\frac{\upvarphi_{1} \quad \quad \upvarphi_{2}}{\upvarphi_{1} \land \upvarphi_{2}}
$$
This says that if $\upvarphi_{1}$ is true and $\upvarphi_{2}$ is true, then $\upvarphi_{1} \land \upvarphi_{2}$ is true.

In English:
- If it's true that the cat is inside and it's true that it's raining
- Then it is true that it's raining and the cat is inside.

##### $\land$-elimination
$$
\frac{\upvarphi_{1} \land \upvarphi_{2}}{\upvarphi_{1}}
$$
$$
\frac{\upvarphi_{1} \land \upvarphi_{2}}{\upvarphi_{2}}
$$
This says that if $\upvarphi_{1} \land \upvarphi_{2}$ is true, then $\upvarphi_{1}$ is true and $\upvarphi_{2}$ is true.

In English:
- It's raining and it's pouring
- Therefore it's raining.

---
### Rules for Disjunction 
##### $\lor$-Introduction 
$$
\frac{\upvarphi}{\upvarphi \lor \uppsi}
$$
$$
\frac{\upvarphi}{\uppsi \lor \upvarphi}
$$

###### $\lor$-Elimination
$$
\frac{\upvarphi \lor \uppsi \quad \boxed{\begin{gathered}
\upvarphi\\
\cdots\\
\upchi
\end{gathered}} \quad \boxed{\begin{gathered}
\uppsi\\
\cdots\\
\upchi
\end{gathered}}}{\upchi}
$$
In order to do this, we use [[#Proof using Boxes|Boxes]].
Each box needs to end with the same formula $\upchi$.

---
### Rules for Negation 

The symbol $\perp$ is known as *bottom* and represents a contradiction.
If you have a contradiction, one can infer any formula.
##### $\perp$-Elimination 
$$
\frac{\perp}{\upvarphi}
$$
##### $\lnot$-Elimination 
$$
\frac{\upvarphi \quad \lnot \upvarphi}{\perp}
$$
##### $\lnot$-Introduction
$$
\frac{\quad\boxed{\begin{gathered}
\upvarphi \\
\cdots \\
\perp
\end{gathered}}\quad}{\lnot \upvarphi}
$$
If we assume an expression to be true, and that creates a contradiction, then the opposite of that expression must be true. This is also *Reductio ad absurdum* which is proof by contradiction.

---
### Rules for Double Negation
##### $\lnot \lnot$-introduction
$$
\frac{\upvarphi}{\lnot \lnot \upvarphi}
$$
##### $\lnot \lnot$-elimination 
$$
\frac{\lnot \lnot \upvarphi}{\upvarphi}
$$

---
### Rules for Implication 
##### $\implies$-introduction 
$$
\frac{\boxed{
\begin{align*}
\upvarphi_{1}\\
\cdots\\
\upvarphi_{2}
\end{align*}
}}{\upvarphi_{1} \implies \upvarphi_{2}}
$$
For this, start with the premise $\upvarphi_{1}$
Continue until we get to $\upvarphi_{2}$
Then you can write $\upvarphi_{1} \implies \upvarphi_{2}$
##### $\implies$-elimination
$$
\frac{\upvarphi_{1} \quad \quad \upvarphi_{1} \implies \upvarphi_{2}}{\upvarphi_{2}}
$$
English Example:
- If today is Tuesday, then John will go to work.
- Today is Tuesday
- Therefore, John will go to work.

---
### Example 1
Here's a proof for the sequent $p, \lnot \lnot (q \land r) \vdash \lnot \lnot p \land r$ using the rules from before.

1. $p$ - premise 
2. $\lnot \lnot (q \land r)$ - premise 
3. $\lnot \lnot p$ - [[#$ lnot lnot$-introduction|Double Negation Introduction]] on 1
4. $q \land r$ - [[#$ lnot lnot$-elimination|Double Negation Elimination]] on 2
5. $r$ - [[#$ land$-elimination|Conjunction Elimination]] on 4
6. $\lnot \lnot p \land r$ - [[#$ land$-introduction|Conjunction Introduction]] on 3 and 5

---
### Example 2
Proof of the sequent $q \implies r \vdash (p \lor q) \implies (p \lor r)$
$$
\begin{align*}
& q \implies r\\
&\boxed{
\begin{align*}
& p \lor q\\
& \boxed{
\begin{align*}
& p\\
& p \lor r
\end{align*}
}\\
& \boxed{
\begin{align*}
& q\\
& r\\
& p \lor r
\end{align*}
}\\
& p \lor r
\end{align*}
}\\
& (p \lor q) \implies (p \lor r)
\end{align*}
$$
1. The sequent says $q \implies r$
	2. If we assume $p \lor q$ is true 
		3. If we assume $p$ is true 
		4. Then $p \lor r$ is true using [[#$ lor$-Introduction|Disjunction Introduction]] on 3
		
		5. If we assume $q$ is true 
		6. Then $r$ is true by [[#$ implies$-elimination|Implication Elimination]] on 1 and 5
		7. Then $p \lor r$ is true using [[#$ lor$-Introduction|Disjunction Introduction]] on 6
	8. Then $p \lor r$ is true using [[#$ lor$-Elimination|Disjunction Elimination]] on 2 to 7
9. Then $(p \lor q) \implies (p \lor r)$ using [[#$ implies$-introduction|Implication Introduction]] on 2-8.

---
### Example 3
Proof of the sequent $x \implies (y \implies z), x, \lnot z \vdash \lnot y$
$$
\begin{align*}
& x \implies (y \implies z)\\
& x\\
& \lnot z\\
& \boxed{\begin{align*}
& y\\
& y \implies z\\
& z\\
& \perp
\end{align*}}\\
& \lnot y
\end{align*}
$$

1. The sequent says $x \implies (y \implies z)$ is true
2. The sequent says $x$ is true
3. The sequent says $\lnot z$ is true
	4. If we assume $y$ is true
	5. Then $y \implies z$ by [[#$ implies$-elimination|Implication Elimination]] on 1 and 2.
	6. Then $z$ is true by [[#$ implies$-elimination|Implication Elimination]] on 4 and 5.
	7. Then we have a contradiction $\perp$ by doing [[#$ lnot$-Elimination|Negation Elimination]] on 3 and 6.
8. Then $\lnot y$ is true by [[#$ lnot$-Introduction|Negation Introduction]] on 4-7


---
### Proof using Boxes 

Here's a proof for the sequent $p \implies q, q \implies r \vdash p \implies r$.
$$
\begin{align*}
& p \implies q\\
& q \implies r\\
&
\boxed{
\begin{align*}
p &\\
q &\\
r &
\end{align*}
}\\
&p \implies r
\end{align*}
$$

It is possible for a proof to involve more than one box and to have boxes nested within each other.

But, boxes **cannot** overlap.

Here's a proof of the sequent $(p \land q) \implies r \vdash p \implies (q \implies r)$
$$
\begin{align*}
& p \land q \implies r\\
& \boxed{
\begin{align*}
& p\\
&\boxed{
\begin{align*}
& q\\
& p \land q\\
& r
\end{align*}
}\\
&q \implies r
\end{align*}
}\\
& p \implies (q \implies r)
\end{align*}
$$

Translated to English:
1. The sequent says $p \land q \implies r$
	2. If we assume $p$ is true
		3. If we assume $q$ is true 
		4. Then $p \land q$ is true by [[#$ land$-introduction|Conjunction Introduction]] on 2 and 3
		5. Then $r$ is true by [[#$ implies$-elimination|Implication Elimination]] on 1 and 4.
	6. Then $q \implies r$ by [[#$ implies$-introduction|Implication Introduction]] on 3 and 5.
7. Then $p \implies (q \implies r)$ by [[#$ implies$-introduction|Implication Introduction]] on 2 and 6.






---
### Additional Information

- [Rule of Inference Wikipedia](https://en.wikipedia.org/wiki/Rule_of_inference)
- [Lecture Notes]
- [Maybe Practical Q and As]
