---
tags:
  - degree/singlemathsa/binomial
---
![[Binomial MOC 🌍]]

### The Binomial Coefficient
The binomial coefficient is defined as for integers $n$ and $k$ in $\mathbb{N}$ we define:
$$
\binom{n}{k}=\frac{n!}{k!(n-k)!}
$$
This is pronounced as *"$n$ choose $k$"*, where it describes the number of combinations of $k$ items in a collection of $n$ items. For example: In a collection of 3 items, there are 3 different ways you can choose just 2 items from that collection. So $\binom{3}{2}=3$.

---
### Pascal's Triangle

The binomial coefficients are often written as a triangle.
$$
\begin{matrix}
\binom{0}{0}\\
\binom{1}{0}\quad \binom{1}{1}\\
\binom{2}{0}\quad \binom{2}{1}\quad \binom{2}{2}\\
\binom{3}{0}\quad \binom{3}{1}\quad \binom{3}{2}\quad \binom{3}{3}\\
\binom{4}{0}\quad \binom{4}{1}\quad \binom{4}{2}\quad \binom{4}{3}\quad \binom{4}{4}\\
\binom{5}{0}\quad \binom{5}{1} \quad \binom{5}{2}\quad \binom{5}{3} \quad \binom{5}{4}\quad \binom{5}{5}
\end{matrix}
\quad=\quad
\begin{matrix}
1\\
1\quad 1\\
1\quad 2\quad 1\\
1\quad 3\quad 3\quad 1\\
1\quad 4\quad 6\quad 4\quad 1\\
1\quad 5 \quad 10\quad 10 \quad 5\quad 1
\end{matrix}

$$

Pascal's triangle exposes a number of important properties of the binomial coefficient.

$$
\binom{n}{0}=\binom{n}{n}=1;\quad\binom{n}{1}=\binom{n}{n-1}=n;\quad\binom{n}{k}=\binom{n}{n-k}
$$
This just means:
- The edges are equal to 1.
- The ones next to the edge are just the row number. Any $n$ choose 1 is just $n$.
- The triangle is symmetrical.

It also exposes another property. The 2 coefficients above any coefficient add to make that one.
$$\binom{n}{k-1}+\binom{n}{k}=\binom{n+1}{k}$$
*Proof.*
$$
\begin{align*}
\binom{n}{k-1}+\binom{n}{k}&=\frac{n!}{(k-1)!(n-k+1)!}+\frac{n!}{k!(n-k)!} \\\\
&=\frac{n!}{(k-1)!(n-k)!}+\left[\frac{1}{n-k+1}+\frac{1}{k}\right] \\\\
&=\frac{n!}{(k-1)!(n-k)!}+\left[\frac{k+(n-k+1)}{(n-k+1)k}\right] \\\\
&=\frac{(n+1)!}{k!(n-k+1)!}\\\\
&=\binom{n+1}{k}
\end{align*}
$$

### The Binomial Theorem

$$
\begin{aligned}
(a+b)^n&=a^n+\binom{n}{1}a^{n-1}b+\binom{n}{2}a^{n-2}b^2+...\binom{n}{k}a^{n-k}{k}+...+b^n \\ &=\sum_{k=0}^{n}{\binom{n}{k}a^{n-k}b^k}
\end{aligned}
$$

You know what it is lol.

You can do fun stuff like expand $(1-x)^5$ easily because why not.

---
### Proving the binomial theorem

It can be proved via [[Proof by Induction - Binomial Theorem|Induction]]
