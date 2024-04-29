---
tags:
  - degree/singlemathsa/binomial
  - degree/singlemathsa/proof/induction
  - degree/mathsforcs/proof/induction
---
![[Proof by Induction MOC 🌍]]

### Statement
$$
(a+b)^n=\sum_{k=0}^{n}{a^{n-k}b^k}
$$
For all $n\in\mathbb{N}$.

---
### Base Case
Case $n=0$.
$$\begin{aligned}
(a+b)^0&=1\\\\
\sum_{k=0}^{0}{\binom{0}{0}a^0b^0}&=1
\end{aligned}$$
---
### Inductive Step
Assume the statement works for some $n=N$. Then for some $n=N+1$.

$$\begin{aligned}
(a+b)^{N+1}&=(a+b)(a+b)^N \\
&=(a+b)\sum_{k=0}^{N}{\binom{N}{k}a^{N-k}b^k} \\
&=a\sum_{k=0}^{N}{\binom{N}{k}a^{N-k}b^k}+b\sum_{k=0}^{N}{\binom{N}{k}a^{N-k}b^k} \\
&=\sum_{k=0}^{N}{\binom{N}{k}a^{N-k+1}b^k}+\sum_{k=0}^{N}{\binom{N}{k}a^{N-k}b^{k+1}}
\end{aligned}
$$
We need to try and recombine these sums so we need them looking similar. We can achieve this by [[Index Shifting]] our right sum by 1 since on the right both $k$ are 1 larger than on the left. Using $j=k+1$:
$$\begin{aligned}
(a+b)^{N+1}&=\sum_{k=0}^{N}{\binom{N}{k}a^{N-k+1}b^k}+\sum_{j=1}^{N+1}{\binom{N}{j-1}a^{N-(j-1)}b^{j-1+1}} \\
&=\sum_{k=0}^{N}{\binom{N}{k}a^{N-k+1}b^k}+\sum_{j=1}^{N+1}{\binom{N}{j-1}a^{N-j+1}b^{j}} \\
\end{aligned}$$
We can now see that the two sums look far more similar now. We can now do a little trolling and rename our $j$ variable back to $k$ since it's a dummy variable.
$$\begin{aligned}
(a+b)^{N+1}&=\sum_{k=0}^{N}{\binom{N}{k}a^{N-k+1}b^k}+\sum_{k=1}^{N+1}{\binom{N}{k-1}a^{N-k+1}b^{k}}
\end{aligned}$$
We're very close to being able to combine these sums but one issue is the limits of the sums. In order to combine these sums, we need them to have the same limits. To make them the same, we can [[Separating Terms|Separate the term]] $k=0$ from the 1st sum and the $N+1$ term from the 2nd.
$$\begin{aligned}
(a+b)^{N+1}&=a^{N+1}+\sum_{k=1}^{N}{\binom{N}{k}a^{N-k+1}b^k}+\sum_{k=1}^{N}{\binom{N}{k-1}a^{N-k+1}b^{k}} + b^{N+1} \\
\end{aligned}$$
Now that the sums have the same limits we can combine them together.
$$
\begin{aligned}
(a+b)^{N+1}&=a^{N+1}+\sum_{k=1}^{N}{\left[\binom{N}{k}+\binom{N}{k-1}\right]a^{N-k+1}b^k} + b^{N+1} \\
\end{aligned}
$$
Recall the [[The Binomial Theorem|Properties of Pascal's Triangle]] where $\binom{n}{k-1}+\binom{n}{k}=\binom{n+1}{k}$. This allows us to combine the binomial coefficients into one.
$$
\begin{aligned}
(a+b)^{N+1}&=a^{N+1}+\sum_{k=1}^{N}{\binom{N+1}{k}a^{N-k+1}b^k} + b^{N+1} \\
\end{aligned}
$$
And finally we need to collect those terms back into the sum. Notice that if we put $k=0$ into our sum, we get $a^{N+1}$. So we can collect that and change our limit to $k=0$. Also notice if we put $N+1$ into our sum, we get $b^{N+1}$. So we can collect that and change our top limit to $N+1$. Leaving us with:
$$
\begin{aligned}
(a+b)^{N+1}&=\sum_{k=0}^{N+1}{\binom{N+1}{k}a^{N-k+1}b^k}
\end{aligned}
$$
Which is the binomial theorem from before.

---
### Conclusion
Since the statement is true for any $N+1$, given it works for $N$, and we have proven that is works for $n=0$, we have proven by induction that the binomial theorem is true for all $n\in\mathbb{N}$.
