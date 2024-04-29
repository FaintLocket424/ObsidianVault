---
tags:
  - degree/compthink/logic
  - coursework
---

### Question 1

A complete set of connectives is one in which any truth table can be represented using only connectives in the set.

On slide 5 of lecture 3 "*More on Propositional Logic*", it proves that $\{ \land, \lor, \lnot \}$ is a functionally complete set. I will use this to prove the following sets.

##### Part i
> *Show $\{ \lnot, \land \}$ is a complete set of connectives.*

Since we know $\{ \land, \lor, \lnot \}$ is functionally complete, if we can represent $A \lor B$ in terms of $\land$ and $\lnot$, then $\{\lnot, \land\}$ is also functionally complete.

| $A$ | $\lnot A$ |
| --- | --------- |
| 0   | 1         |
| 1   | 0         |
<br>

| $A$ | $B$ | $A \land B$ |
| --- | --- | ----------- |
| 0   | 0   | 0           |
| 0   | 1   | 0           |
| 1   | 0   | 0           |
| 1   | 1   | 1           |
<br>

| $A$ | $B$ | $A \lor B$ |
| --- | --- | ---------- |
| 0   | 0   | 0          |
| 0   | 1   | 1          |
| 1   | 0   | 1          |
| 1   | 1   | 1          |

Applying De Morgan's rule to $A \lor B$, we get
$$
\lnot (\lnot A \land \lnot B)
$$
And the truth table for this expression is

| $A$ | $B$ | $\lnot (\lnot A \land \lnot B)$ |
| --- | --- | ------------------------------- |
| 0   | 0   | 0                               |
| 0   | 1   | 1                               |
| 1   | 0   | 1                               |
| 1   | 1   | 1                               |

As this matches the truth table for $A \lor B$, it proves these two expressions are functionally equivalent.

Therefore, this proves that since $\{ \land, \lor, \lnot \}$ is functionally complete, then so is $\{ \lnot, \land \}$.

##### Part ii
> *Show $\{ \rightarrow, \text{XOR} \}$ is functionally complete set of connectives.*

Similar to before, if we can create $\land$, $\lor$ and $\lnot$ using just these connectives, then that will prove it's also a complete set.


| $A$ | $B$ | $A \oplus B$ |
| --- | --- | ------------ |
| 0   | 0   | 0            |
| 0   | 1   | 1            |
| 1   | 0   | 1            |
| 1   | 1   | 0            |
<br>

| $A$ | $B$ | $A \rightarrow B$ |
| --- | --- | ----------------- |
| 0   | 0   | 1                 |
| 0   | 1   | 1                 |
| 1   | 0   | 0                 |
| 1   | 1   | 1                 |
<br>

| $A$ | $B$ | $A \oplus (B \rightarrow A)$ |
| --- | --- | ---------------------------- |
| 0   | 0   | 1                            |
| 0   | 1   | 0                            |
| 1   | 0   | 0                            |
| 1   | 1   | 0                            |

This is functionally equivalent to A NAND B, or $A \overline{\land} B$, which is functionally complete.

$\DeclareMathOperator{nand}{\overline{\land}}\lnot A = A \nand A$

| $A$ | $\lnot A$ |
| --- | --------- |
| 0   | 1         |
| 1   | 0         |
<br>

| $A$ | $A \nand B$ |
| --- | ----------- |
| 0   | 1           |
| 1   | 0           |

$A \land B = \lnot(A \nand B)$

| $A$ | $B$ | $A \land B$ |
| --- | --- | ----------- |
| 0   | 0   | 0           |
| 0   | 1   | 0           |
| 1   | 0   | 0           |
| 1   | 1   | 1           |
<br>

| $A$ | $B$ | $\lnot (A \nand B)$ |
| --- | --- | ------------------- |
| 0   | 0   | 0                   |
| 0   | 1   | 0                   |
| 1   | 0   | 0                   |
| 1   | 1   | 1                   |

And since $\{ \lnot, \land \}$ is a functionally complete set from earlier, we know that $\{ \rightarrow, \oplus \}$ is also a functionally complete set.

##### Part iii
> *Is $\{ NOR, \lor \}$ a complete set of connectives?*

I will write NOR as $\DeclareMathOperator{nor}{\overline{\lor}}\nor$.


| $A$ | $\lnot A$ |
| --- | --------- |
| 0   | 1         |
| 1   | 0         |
<br>

| $A$ | $A \nor A$ |
| --- | ---------- |
| 0   | 1          |
| 1   | 0          |
As these have the same truth table, they are functionally equivalent. So, we can represent $\lnot A$ in terms of $\nor$.


| $A$ | $B$ | $A \land B$ |
| --- | --- | ----------- |
| 0   | 0   | 0           |
| 0   | 1   | 0           |
| 1   | 0   | 0           |
| 1   | 1   | 1           |
<br>

| $A$ | $B$ | $(\lnot A) \nor (\lnot B)$ |
| --- | --- | -------------------------- |
| 0   | 0   | 0                          |
| 0   | 1   | 0                          |
| 1   | 0   | 0                          |
| 1   | 1   | 1                          |
As these have the same truth table, they are functionally equivalent. So, $\land$ can be represented with $\nor$.

This means that $\{ \nor, \lor \}$ can be used to represent $\{ \lnot, \land, \lor \}$ which is functionally complete, therefore $\{ \nor, \lor \}$ is a functionally complete set.

##### Part iv
> *Is $\{ \land, \lor \}$ a complete set of connectives?*

No it is not a complete set.

Take the truth table 

| $A$ | $B$ | $Q$ |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 0   |

Also take the truth tables for $\land$ and $\lor$.

| $A$ | $B$ | $A \land B$ |
| --- | --- | ----------- |
| 0   | 0   | 0           |
| 0   | 1   | 0           |
| 1   | 0   | 0           |
| 1   | 1   | 1           |
<br>

| $A$ | $B$ | $A \lor B$ |
| --- | --- | ---------- |
| 0   | 0   | 0          |
| 0   | 1   | 1          |
| 1   | 0   | 1          |
| 1   | 1   | 1          |

In order to satisfy $Q$ when $A=0$ and $B=0$, the output needs to be $Q=1$.

But with both $A \land B$ and $A \lor B$, the inputs cannot be inverted when $A=B$.
$$
\begin{align*}
0 \land 0 &= 0\\
1 \land 1 &= 1\\
0 \lor 0 &= 0\\
1 \lor 1 &= 1
\end{align*}
$$
This makes it impossible to satisfy $Q=1$ when $A=0$ and $B=0$.

### Question 2
$$
Q = ((p \rightarrow q) \rightarrow (r \rightarrow s)) \rightarrow t
$$
The truth table for $Q$ is

| $p$ | $q$ | $r$ | $s$ | $t$ | $Q$ |
| --- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | 0   | 0   |
| 0   | 0   | 0   | 0   | 1   | 1   |
| 0   | 0   | 0   | 1   | 0   | 0   |
| 0   | 0   | 0   | 1   | 1   | 1   |
| 0   | 0   | 1   | 0   | 0   | 1   |
| 0   | 0   | 1   | 0   | 1   | 1   |
| 0   | 0   | 1   | 1   | 0   | 0   |
| 0   | 0   | 1   | 1   | 1   | 1   |
| 0   | 1   | 0   | 0   | 0   | 0   |
| 0   | 1   | 0   | 0   | 1   | 1   |
| 0   | 1   | 0   | 1   | 0   | 0   |
| 0   | 1   | 0   | 1   | 1   | 1   |
| 0   | 1   | 1   | 0   | 0   | 1   |
| 0   | 1   | 1   | 0   | 1   | 1   |
| 0   | 1   | 1   | 1   | 0   | 0   |
| 0   | 1   | 1   | 1   | 1   | 1   |
| 1   | 0   | 0   | 0   | 0   | 0   |
| 1   | 0   | 0   | 0   | 1   | 1   |
| 1   | 0   | 0   | 1   | 0   | 0   |
| 1   | 0   | 0   | 1   | 1   | 1   |
| 1   | 0   | 1   | 0   | 0   | 0   |
| 1   | 0   | 1   | 0   | 1   | 1   |
| 1   | 0   | 1   | 1   | 0   | 0   |
| 1   | 0   | 1   | 1   | 1   | 1   |
| 1   | 1   | 0   | 0   | 0   | 0   |
| 1   | 1   | 0   | 0   | 1   | 1   |
| 1   | 1   | 0   | 1   | 0   | 0   |
| 1   | 1   | 0   | 1   | 1   | 1   |
| 1   | 1   | 1   | 0   | 0   | 1   |
| 1   | 1   | 1   | 0   | 1   | 1   |
| 1   | 1   | 1   | 1   | 0   | 0   |
| 1   | 1   | 1   | 1   | 1   | 1   |

##### Part i
>*Convert $Q$ to Conjunctive Normal Form*

So taking the truth table and taking the lines which are zero we get the conjunctive normal form.
$$
\begin{align*}
Q &= (p \lor q \lor r \lor s \lor t)\\
&\land (p \lor q \lor r \lor \overline{s} \lor t)\\
&\land (p \lor q \lor \overline{r} \lor \overline{s} \lor t)\\
&\land (p \lor \overline{q} \lor r \lor s \lor t)\\
&\land (p \lor \overline{q} \lor r \lor \overline{s} \lor t)\\
&\land (p \lor \overline{q} \lor \overline{r} \lor \overline{s} \lor t)\\
&\land (\overline{p} \lor q \lor r \lor s \lor t)\\
&\land (\overline{p} \lor q \lor r \lor \overline{s} \lor t)\\
&\land (\overline{p} \lor q \lor \overline{r} \lor s \lor t)\\
&\land (\overline{p} \lor q \lor \overline{r} \lor \overline{s} \lor t)\\
&\land (\overline{p} \lor \overline{q} \lor r \lor s \lor t)\\
&\land (\overline{p} \lor \overline{q} \lor r \lor \overline{s} \lor t)\\
&\land (\overline{p} \lor \overline{q} \lor \overline{r} \lor \overline{s} \lor t)
\end{align*}
$$

##### Part ii
> *Convert $Q$ to Disjunctive Normal Form*

Taking the truth table and taking the lines which are one we get the disjunctive normal form.
$$
\begin{align*}
Q &= (\overline{p} \land \overline{q} \land \overline{r} \land \overline{s} \land t)\\
&\lor (\overline{p} \land \overline{q} \land \overline{r} \land s \land t)\\
&\lor (\overline{p} \land \overline{q} \land r \land \overline{s} \land \overline{t})\\
&\lor (\overline{p} \land \overline{q} \land r \land \overline{s} \land t)\\
&\lor (\overline{p} \land \overline{q} \land r \land s \land t)\\
&\lor (\overline{p} \land q \land \overline{r} \land \overline{s} \land t)\\
&\lor (\overline{p} \land q \land \overline{r} \land s \land t)\\
&\lor (\overline{p} \land q \land r \land \overline{s} \land \overline{t})\\
&\lor (\overline{p} \land q \land r \land \overline{s} \land t)\\
&\lor (\overline{p} \land q \land r \land s \land t)\\
&\lor (p \land \overline{q} \land \overline{r} \land \overline{s} \land t)\\
&\lor (p \land \overline{q} \land \overline{r} \land s \land t)\\
&\lor (p \land \overline{q} \land r \land \overline{s} \land t)\\
&\lor (p \land \overline{q} \land r \land s \land t)\\
&\lor (p \land q \land \overline{r} \land \overline{s} \land t)\\
&\lor (p \land q \land \overline{r} \land s \land t)\\
&\lor (p \land q \land r \land \overline{s} \land \overline{t})\\
&\lor (p \land q \land r \land \overline{s} \land t)\\
&\lor (p \land q \land r \land s \land t)
\end{align*}
$$

### Question 3

>*What is the purpose of Tseitin's Algorithm?*

Tseitin's Algorithm takes a propositional formula $\uppsi$ and produces a clause set $F$ that is in CNF and equisatisfiable to $\uppsi$.

>*Apply Tseitin's Algorithm to turn the propositional formula $\uppsi = ((p \rightarrow q) \rightarrow (r \rightarrow s)) \rightarrow t$ to CNF*

First, for this we will need a clause set for $F_{\ell \to m}$, which would need to be functionally equivalent to $x \equiv \ell \to m$
- $x_{\ell \to m} \equiv \ell \to m$
- $x_{\ell \to m} \equiv \lnot \ell \lor m$
- $(x_{\ell \to m} \to (\lnot \ell \lor m)) \land ((\lnot \ell \lor m) \to x_{\ell \to m})$
- $(\lnot x_{\ell \to m} \lor (\lnot \ell \lor m)) \land (\lnot(\lnot \ell \lor m) \lor x_{\ell \to m})$ 
- $(\lnot x_{\ell \to m} \lor \lnot \ell \lor m) \land ((\ell \land \lnot m) \lor x_{\ell \to m})$ 
- $(\lnot x_{\ell \to m} \lor \lnot \ell \lor m) \land (\ell \lor x_{\ell \to m}) \land (\lnot m \lor x_{\ell \to m})$
Hence, $F_{\ell \to m} = \{ \{ \overline{x_{\ell \to m}}, \overline{\ell}, m \}, \{ \ell, x_{\ell \to m} \}, \{ \overline{m}, x_{\ell \to m} \} \}$.

Now with this we can use Tseitin's Algorithm on $\uppsi$.
$$
\begin{align*}
\uppsi &= ((p \to q) \to (r \to s)) \to t\\
F &= \emptyset\\
\\
\uppsi &= ((p \to q) \to u_{r \to s}) \to t\\
F &= \{ \{ r, u_{r \to s} \}, \{ \overline{s}, u_{r \to s} \}, \{ \overline{r}, s, \overline{u_{r \to s}} \} \}\\
\\
\uppsi &= (v_{p \to q} \to u_{r \to s}) \to t\\
F &= \{ \{ r, u_{r \to s} \}, \{ \overline{s}, u_{r \to s} \}, \{ \overline{r}, s, \overline{u_{r \to s}} \}, \\
&\{ p, v_{p \to q} \}, \{ \overline{q}, v_{p \to q} \}, \{ \overline{p}, q, \overline{v_{p \to q}} \} \}\\
\\
\uppsi &= w_{v \to u} \to t\\
F &= \{ \{ r, u_{r \to s} \}, \{ \overline{s}, u_{r \to s} \}, \{ \overline{r}, s, \overline{u_{r \to s}} \}, \\
&\{ p, v_{p \to q} \}, \{ \overline{q}, v_{p \to q} \}, \{ \overline{p}, q, \overline{v_{p \to q}} \},\\
&\{ v, w_{v \to u} \}, \{ \overline{u}, w_{v \to u} \}, \{ \overline{v}, u, \overline{w_{v \to u}} \} \}\\
\\
\uppsi &= x_{w \to t}\\
F &= \{ \{ r, u_{r \to s} \}, \{ \overline{s}, u_{r \to s} \}, \{ \overline{r}, s, \overline{u_{r \to s}} \}, \\
&\{ p, v_{p \to q} \}, \{ \overline{q}, v_{p \to q} \}, \{ \overline{p}, q, \overline{v_{p \to q}} \},\\
&\{ v, w_{v \to u} \}, \{ \overline{u}, w_{v \to u} \}, \{ \overline{v}, u, \overline{w_{v \to u}} \},\\
&\{ w, x_{w \to t} \}, \{ \overline{t}, x_{w \to t} \}, \{ \overline{w}, t, \overline{x_{w \to t}} \} \}\\
\\
F &= \{ \{ r, u_{r \to s} \}, \{ \overline{s}, u_{r \to s} \}, \{ \overline{r}, s, \overline{u_{r \to s}} \}, \\
&\{ p, v_{p \to q} \}, \{ \overline{q}, v_{p \to q} \}, \{ \overline{p}, q, \overline{v_{p \to q}} \},\\
&\{ v, w_{v \to u} \}, \{ \overline{u}, w_{v \to u} \}, \{ \overline{v}, u, \overline{w_{v \to u}} \},\\
&\{ w, x_{w \to t} \}, \{ \overline{t}, x_{w \to t} \}, \{ \overline{w}, t, \overline{x_{w \to t}} \}\\
&\{ x_{w \to t} \} \}
\end{align*}
$$

And $F$ is now in conjunctive normal form.

### Question 4

##### Part i 
>*State with justification if $(\forall x \exists y \exists z S(x,y,z)) \to (\forall x \forall y \exists z S(x,y,z))$*



##### Part ii
>*State with justification if $(\forall x \exists y \forall z S(x,y,z)) \to (\forall x \exists y \exists z S(x,y,z))$*


##### Part iii
>*State with justification if $(\forall x \forall y \exists z S(x,y,z)) \to (\forall x \exists y \forall z S(x,y,z))$*


##### Part iv
>*State with justification if $(\forall x \exists y \forall z S(x,y,z)) \to (\forall x \forall y \exists z S(x,y,z))$*


### Question 5
>*Evaluate the given sentence on the respective relations $S$ over the domain $\{0,1\}$.*

##### Part i
>*$\forall w \exists x \forall y \exists z R(w,x,y,z)$ on $\{ (0,1,0,1), (0,1,1,0), (1,0,0,0), (1,0,1,1) \}$*


##### Part ii
>*$\exists w \forall x \exists y \forall z R(w,x,y,z)$ on $\{ (1,0,0,1), (1,0,0,0), (1,1,0,0), (1,1,0,1) \}$*


##### Part iii
>*$\forall x \exists y \forall z R(x,y) \lor R(y,z)$ on $\{ (0,1,1), (0,1,0), (1,1,1) \}$*


##### Part iv
>*$\forall x \exists y \forall z R(x,y) \lor R(y,z)$ on $\{ (0,1,1), (0,0,1) \}$*

