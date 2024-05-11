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
A necessary condition for a series $\sum_{n=1}^{\infty} a_{n}$ is that $a_{k}$ tends towards zero as $n \to \infty$. So, $\lim_{n \to \infty} a_{n}=0$.

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
### Divergence Test 
If $\lim_{n \to \infty} a_{n} \ne 0$ then $\sum^{\infty}_{n=1} a_{n}$ is a divergent series.

The sequence must tend to zero.

Take the series 

$$
\sum^{\infty}_{n=1} (-1)^{n} \ln(n)
$$

Taking the limit of the sequence, we see that $\lim_{n \to \infty} (-1)^{n}\ln(n) \ne 0$ and so this sequence is divergent.

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
##### Application 
These tests are best performed on geometric and p-series.

Take the series 

$$
\sum^{\infty}_{n=1} \frac{n}{n^{3}+1}
$$



---
### Ratio Test
Let $\sum_{n=1}^{\infty} a_{n}$ be a series where $a_{n} \ne 0$ and such that $\lim_{n\rightarrow \infty} \left|\frac{a_{n+1}}{a_{n}}\right|=L$.

Then:
If $L<1$, the series absolutely converges.
If $L>1$, it's a divergent series.
If $L=1$, we get no information.

---
### The nth Root Test
Consider the series $\sum_{n=1}^{\infty} a_{n}$ such that $\lim_{n \rightarrow \infty}\sqrt[n]{\left|a_{n}\right|}=L$.

If $L < 1$, the series absolutely converges.
If $L>1$, the series diverges.
If $L=1$, we get not information.

---
### Alternating Series Test
The series $\sum_{n=1}^{\infty} (-1)^{n+1} b_{n}$ or $\sum^{\infty}_{n=1} (-1)^{n}b_{n}$ converges if:
- $b_{n}>0$ and
- $b_{n}$ is a decreasing sequence, so $b_{n+1} \le b_{n}$ $\forall n$ 
- $\lim_{n \to \infty} b_{n} = 0$

This test is usually good for series with a $(-1)^{n}$ term like 

$$
\sum^{\infty}_{n=1} \frac{(-1)^{n}}{\sqrt{n}}
$$

Since $\frac{1}{\sqrt{n}}$ is a decreasing sequence with $\lim_{n \to \infty} \frac{1}{\sqrt{n}} = 0$, this series converges.

Conversely, take the series 

$$
\sum^{\infty}_{n=1} (-1)^{n} \ln(n)
$$

The alternating series test does not work here as $\ln(n)$ is not a decreasing function and $\lim_{n \to \infty} \ln(n) = \infty$.

---
### Geometric Series 
A geometric series 

$$
\sum^{\infty}_{n=1} a r^{n-1}
$$

converges to $\frac{a}{1-r}$ if $|r| < 1$. Otherwise, it diverges.

Useful on series like 

$$
\sum^{\infty}_{n=1} \frac{2^{n-1}}{5^{n+1}}
$$

which we can factorise into 

$$
\sum^{\infty}_{n=1} \frac{1}{25} \cdot \left(\frac{2}{5}\right)^{n-1}
$$

and can see that since $\frac{2}{5} < 1$, this series converges.

---
### Integral Test 
A series $\sum^{\infty}_{n=1} a_{n}$ converges if $\int^{\infty}_{1} f(x)\,dx$ converges.

Most series will be difficult to integrate so this is a last resort.

This can be useful on a series like 

$$
\sum^{\infty}_{n=1} n e^{-n^{2}}
$$

where we have to prove $\int^{\infty}_{1} xe^{-x^{2}}\,dx$ converges.

---
### Subsequences 
Every subsequence of a convergent sequence converges to the same limit as the original sequence.

---
### Grouping Terms 
If $\sum^{\infty}_{n=1} a_{n}$ converges, then we can insert brackets/groupings without altering the sum.
