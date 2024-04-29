---
tags:
  - degree/mathsforcs/proof/induction
  - degree/singlemathsa/proof/induction
---
![[Proof by Induction MOC 🌍]]

$$\sum_{k=1}^{n}k^{2}=\frac{1}{6}n\left(2n+1\right)\left(n+1\right)$$

---
### Proof by Induction

#### Statement
*Prove that $P\left(n\right):=\sum_{k=1}^{n}k^{2}$ is equal to $Q\left(n\right):=\frac{1}{6}n\left(2n+1\right)\left(n+1\right)$ for any non-negative integer $n$.*

#### Base Case
For $n=1$ the statement is $P(1)=Q(1)$.
$$\begin{aligned}
P\left(1\right)&=\sum_{k=1}^{1}k^{2}=1 \\\\
Q\left(1\right)&=\frac{1}{6}\left(2+1\right)\left(1+1\right)=1
\end{aligned}$$
So clearly $P(1)=Q(1)$.

---
#### Inductive Step
Assume the statement holds for $n=N$, so $P(N)=Q(N)$. Then for $n=N+1$

$$P\left(N+1\right)=\sum_{k=1}^{N+1}k^{2}=\sum_{k=1}^{N}k^{2}+\left(N+1\right)^{2}$$
Here we [[Separating Terms|separate the last term]] out of the summation which leaves us with a familiar sum.
$$\begin{aligned}
&=P(n)+(N+1)^2 \\\\
&=Q(n)+(N+1)^2
\end{aligned}$$
Here we used our assumption that $P(N)=Q(N)$.
$$\begin{aligned}
&=\frac{1}{6}N\left(2N+1\right)\left(N+1\right)+(N+1)^2 \\
&=\left(N+1\right)\left(\frac{1}{6}N\left(2N+1\right)+\left(N+1\right)\right) \\
&=\frac{1}{6}\left(N+1\right)\left(2N+3\right)\left(N+2\right)
\end{aligned}$$
Now we have this mess, instead of trying to get this into the form we want, we could just make the form we're looking for look like this.
$$\begin{aligned}
Q\left(N+1\right)&=\frac{1}{6}\left(N+1\right)\left(2\left(N+1\right)+1\right)\left(\left(N+1\right)+1\right)\\&=\frac{1}{6}\left(N+1\right)\left(2N+3\right)\left(N+2\right)
\end{aligned}$$

---
#### Conclusion
So now we have proved that if $P(N)=Q(N)$ then $P(N+1)=Q(N+1)$.

Hence, by induction, the result is true for all positive integers $n$.