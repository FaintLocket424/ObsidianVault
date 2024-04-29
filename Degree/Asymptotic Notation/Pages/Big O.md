---
tags:
  - degree/ads/asymptoticnotation
---
![[Asymptotic Notation MOC 🌍]]

### Big $\mathcal{O}$ Notation

Big $\mathcal{O}$ notation is how we express the upper bound for an algorithm's time/space complexity.

>*"The delivery will be there within your lifetime" - Big-$\mathcal{O}$*

If we have function $f$ and $g$, then we can say $f$ is $\mathcal{O}(g)$ if we can show that at some input value $x$, $g$ surpasses $f$ and never looks back.

$$\begin{aligned}
|f(x)|\le C\times|g(x)|
\end{aligned}$$
whenever $x\ge k$

We say that $f$ is big-$\mathcal{O}$ of $g$.

![[Pasted image 20231127152914.png]]

Once you surpass $x=k$, $f$ will always be below $C\times g(x)$

The constants $C$ and $k$ are called **witnesses** to the relationship $f(x)$ is $\mathcal{O}(g(x))$.

If there is a pair of witnesses to the relationship then there are infinitely many pairs of witnesses.

We would say something like $T(n)=\mathcal{O}(n^2)$ which is and I quote:

>*A horrible abuse of notation*

It's the standard tho so we use that.

We use big-$\mathcal{O}$ notation because it simplifies showing the growth of a function. It shows the dominant term and how it grows with larger inputs.

It's not about showing the exact time, it's about showing how that time changes with input size.

---
##### An Example:
If $f(x)=x^2+2x+1$. Then $f(x)=\mathcal{O}(x^2)$

For $x\ge1$, we have $1\le x \le x^2$. That gives:
$$f(x)=x^2+2x+1\le x^2+2x^2+x^2=4x^2$$
for $x\ge1$. Because the above inequality holds for every positive $x\ge1$, using $k=1$ and $C=4$ as witnesses, we get:
$$\begin{aligned}
f(x)\le C\times x^2
\end{aligned}$$
for every $x\ge k$.

### Disproving by contradiction

Show that $3^x$ is not $\mathcal{O}(2^x)$

Assume $3^x$ is $\mathcal{O}(2^x)$.

By definition of big-$\mathcal{O}$, there exist $C,k>0$ so that $3^x\le C\times 2^x$ when $x\ge k$. Then
$$\begin{aligned}
\left(\frac{3}{2}\right)^x\le C
\end{aligned}$$
whenever $x\ge k$.

But any exponential function $a^x$ grows infinitely whenever $a>1$; a contradiction.

---
### Convention

| Big O Form | Name |
| - | - |
|$\mathcal{O}(1)$ | Constant |
|$\mathcal{O}(\log n)$ | Logarithmic |
|$\mathcal{O}(n)$|Linear|
|$\mathcal{O}(n\log n)$|$n\log n$ |
|$\mathcal{O}(n^2)$ | Quadratic |
|$\mathcal{O}(n^3)$ | Cubic |
|$\mathcal{O}(n^k)$ for $k\in\mathbb{N}$ | Polynomial |
|$\mathcal{O}(c^n)$ for $c>1$ | Exponential |

---
### Sum Rule

If $f_1(x)$ is $\mathcal{O}(g_1(x))$ and $f_2(x)$ is $\mathcal{O}(g_2(x))$, then $f_1(x)+f_2(x)$ is $\mathcal{O}(\max\left\{|g_1(x)|,|g_2(x)|\right\})$.

In English, if you're summing two functions, the big-$\mathcal{O}$ of the sum is the big-$\mathcal{O}$ of the worse function.

---
### Product Rule

If $f_1(x)$ is $\mathcal{O}(g_1(x))$ and $f_2(x)$ is $\mathcal{O}(g_2(x))$, then $f_1(x)\times f_2(x)$ is $\mathcal{O}(g_1(x) \times g_2(x))$.

---
### Big Rules

$$\begin{aligned}
	\le&: \mathcal{O} \\
	\ge&: \Omega \\
	=&: \Theta \\
	<&: \mathcal{o} \\
	>&: \omega
\end{aligned}$$

Big-O is for finding what the function will always be less than or equal to.

Big-Omega is for finding what the function will always be greater than or equal to.

Big-Theta is for finding what the function is equal to. When $\mathcal{O}\equiv\Omega$.

Little-O is for finding what the function is definitely less than.

Little-Omega is for finding what the function is definitely greater than.