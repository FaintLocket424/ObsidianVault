---
tags:
  - degree/singlemathsa/proof/induction
  - degree/mathsforcs/proof/induction
---
![[Proof by Induction MOC 🌍]]

### General Formula

##### Statement
$S(n)$ which holds for all integers $n\ge 1$.
You don't have to start at 1.
##### Base Case
Check that $S(1)$ holds.
##### Induction Step
Prove that if $S(k)$ holds for some value $k \ge 1$, then $S(k+1)$ also holds.
##### Conclusion
The base case and inductive step together prove that $S(n)$ holds for some value $k$, and that if it holds for some value $k$, it also holds for $k+1$.

---
### Example: If $n\in\mathbb{N}$, then $\sum^{n}_{i=1} i = \frac{n(n+1)}{2}$

##### Base Case
If $n=1$, then $\frac{n(n+1)}{2}=1$, and also $\sum^{1}_{i=1} i=1$, so the base case holds.

##### Induction Step
Suppose $\sum^{k}_{i=1} i =\frac{k(k+1)}{2}$ and let $n=k+1$.
$$
\begin{align*}
\sum^{n}_{i=1} i &= \sum^{k}_{i=1} i+(k+1)\\
\\
&=\frac{k(k+1)}{2}+\frac{2(k+1)}{2}\\
\\
&=\frac{(k+1)(k+2)}{2}\\
\\
&=\frac{n(n+1)}{2}
\end{align*}
$$
And so, if the statement holds for $n=k$, it also holds for $n=k+1$.

Therefore, by induction, the statement holds true $\forall n\in \mathbb{N}$

---
### Example: $\forall n\in\mathbb{N}$, $n\le 2^{n}$

##### Base Case
If $n=0$, then $2^{n}=2^{0}=1$, so $n\le 2^{n}$ holds since $0\le1$.

##### Induction Step
Let $k\ge 1$ be an integer.
The inductive hypothesis tells us that $k\le 2^{k}$
$$
\begin{align*}
k&\le 2^{k}\\
k+1 &\le 2^{k}+1\\
k+1 &\le 2^{k}+2^{k}\\
k+1 &\le 2^{k+1}
\end{align*}
$$

##### Conclusion
Since the statement is valid for $n=0$, and it is valid for $k+1$ if it is valid for $k$, we conclude that it is valid $\forall n\in\mathbb{N}$, by induction.

### Variations

You can have an inductive step that increments by more than one.
E.g. If $S(0)$, $S(1)$ and $S(2)$ hold, you can prove that $S(n+3)$ holds.