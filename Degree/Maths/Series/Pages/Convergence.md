---
tags:
  - incomplete
  - degree/singlemathsa/series
---
![[Series MOC 🌍]]
### Convergence

A finite series always has a well-defined finite sum.

For an infinite series, we desire it's partial sum $S_{k}$ as the sum of the first $k$ terms.
$$
S_{k}=\sum_{j=0}^{k-1} a_{j} = a_{0} + a_{1} + a_{k-1}
$$
We then define the sequence of partial sums $S_{1}, S_{2}, S_{3}$.

An infinite series converges if its sequence of partial sums has a limit, eg
$$
S = \lim_{K \rightarrow \infty} S_{K}
$$
If this limit does not exist, then it's divergent.

---
### Remainders

For any infinite series $\sum^{\infty}_{n=0}a_{n}$ we can define the partial sum:
$$
\begin{align*}
S_{n}=\sum^{n}_{r=0}a_{r}=a_{0}+a_{1}+\dots+a_{n}
\end{align*}
$$
And so the remainder is:
$$
R_{n}=\sum^{\infty}_{r=n+1}a_{r}=a_{n+1}+a_{n+2}+\dots
$$
We can now also say a series is convergent if:
$$
\begin{align*}
\lim_{n\rightarrow\infty}R_{n}=0
\end{align*}
$$

---
### The Necessary Condition for Convergence

A necessary condition for a series $\sum_{k=1}^{\infty} a_{k}$ is that $a_{k}$ tends towards zero as $k\rightarrow \infty$. So, $\lim_{k\rightarrow \infty} a_{k}=0$.

If this condition is not met, the series is divergent.

**BUT**, meeting this condition does not guarantee convergence. Only that it is possible.

---
### Sum and Difference of Convergent Series

If the series $\sum_{n=0}^{\infty} a_{n} = \alpha$ and the series $\sum_{n=0}^{\infty} b_{n} = \beta$ are convergent, then:
$$
\begin{align*}
\sum_{n=0}^{\infty} (a_{n} + b_{n}) &= \alpha + \beta\\
\\
\sum_{n=0}^{\infty} (a_{n} - b_{n}) &= \alpha - \beta
\end{align*}
$$

---
### Absolute Convergence

If $\sum_{n=1}^{\infty} \left|a_{n}\right|$ converges then $\sum_{n=1}^{\infty} a_{n}$ converges as well.

---
### Comparison Test

##### Convergence
Let's say we have a convergent series $\sum_{n=1}^{\infty} b_{n}$ of positive terms.
And we have the series $\sum_{n=1}^{\infty} a_{n}$.

If $\left|a_{n}\right| \le b_{n}$ for all $n\ge N$, then $\sum_{n=1}^{\infty} a_{n}$ absolutely converges.

##### Divergence
Let's say we have a divergent series $\sum_{n=1}^{\infty} b_{n}$ of positive terms.
And we have the series $\sum_{n=1}^{\infty} a_{n}$.

If $0 \le b_{n} \le a_{n}$ for all $n > N$, then $\sum_{n=1}^{\infty} a_{n}$ is divergent.

---
### Ratio Test

Let $\sum_{n=1}^{\infty} a_{n}$ be a series where $a_{n} \ne 0$ and such that $\lim_{n\rightarrow \infty} \left|\frac{a_{n+1}}{a_{n}}\right|=L$.

Then:
If $L<1$, the series absolutely converges.
If $L>1$, it's a divergent series.
If $L=1$, we get no information.

---
### The $n^{\text{th}}$ Root Test

Consider the series $\sum_{n=1}^{\infty} a_{n}$ such that $\lim_{n \rightarrow \infty}\sqrt[n]{\left|a_{n}\right|}=L$.

If $L < 1$, the series absolutely converges.
If $L>1$, the series diverges.
If $L=1$, we get not information.

---
### Alternating Series Test

The series $\sum_{n=1}^{\infty} (-1)^{n+1} a_{n}$ converges if:
- $a_{n}>0$ and
- $a_{n+1} \le a_{n}$ $\forall n$ and
- $\lim_{n \rightarrow \infty} a_{n} = 0$

---
### Subsequences 

Every subsequence of a convergent sequence converges to the same limit as the original sequence.

---
### Grouping Terms 

If $\sum^{\infty}_{n=1} a_{n}$ converges, then we can insert brackets/groupings without altering the sum.