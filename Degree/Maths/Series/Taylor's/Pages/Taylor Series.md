---
tags:
  - degree/singlemathsa/series/taylor
---
![[Taylor's MOC 🌍]]

### Taylor Series

Given an infinitely differentiable function $f:\mathbb{R}\rightarrow\mathbb{R}$, we want to find a power series to represent $f$ near some reference point $x=a$.

E.g. $\frac{1}{1-x} = \sum_{n=0}^{\infty} x^{n}$ near $x=0$, namely $|x|<1$.

An appropriate function can be represented by a power series called a *Taylor Series*.

---
### Building a Taylor Series

We build a Taylor series by a sequence of polynomial approximations with increasing degrees.

##### First Taylor Polynomial
The best linear approximation of $f$ near $x=a$ is a straight line with slope $f'(a)$.
$$
y=f(a)+f'(a)(x-a)
$$
A linear function like this is the *first Taylor polynomial* of $f$ at $x=a$.
$$
P_{1}(x)=P_{1,a}(x)=f(a)+f'(a)(x-a)
$$

---
### Error
$$
\begin{align*}
f(x)-P_{1}(x) &= f(x)-f(a)-f'(a)(x-a)\\
&= (x-a)\left[\frac{f(x)-f(a)}{x-a}-f'(a)\right]
\end{align*}
$$

$$
\frac{f(x)-P_{1}(x)}{x-a}\rightarrow 0
$$
as $x\rightarrow a$.

---
### Higher Taylor Polynomials

The first Taylor polynomial is $P_{1}$, the higher order ones are $P_{2}$, $P_{3}$, $\dots$
$$
\lim_{x\rightarrow a} \frac{f(x)-P_{n}(x)}{(x-a)^{n}} = 0
$$
##### Derivation of $P_{2}(x)$
$$
f(x)=f(a)+\int^{x}_{a}f'(y)dy
$$
We use:
$$
\begin{align*}
f'(y) &\approx  f'(a)+f''(a)(y-a)\\
\\
f(x)&\approx f(a)+\int^{x}_{a}\left(f'(a)+f''(a)(y-a)\right)dy\\
&= f(a)+f'(a)(x-a)+f''(a)\frac{(x-a)^{2}}{2}
\end{align*}
$$

We define $P_{2}(x)=P_{2,a}(x)=f(a)+f'(a)(x-a)+f''(a)\frac{(x-a)^{2}}{2}$.

---
### Taylor Polynomial

In general, the Taylor polynomial of degree $N$ for $f(x)$ near $x=a$ is:
$$
\begin{align*}
P_{N}(x)=P_{N,a}(x)&= f(a)+f'(a)(x-a)+f''(a)\frac{(x-a)^{2}}{2}+f'''(a)\frac{(x-a)^{3}}{3!}+\dots+f^{(N)}(a)\frac{(x-a)^{N}}{N!}\\
&= \sum_{n=0}^{N}f^{(n)}(a)\frac{(x-a)^{n}}{n!}
\end{align*}
$$

---
### Example: $f(x)=e^{x}$ about $x=0$

$$f^{(n)}(x)=e^{x}\quad\forall n\implies f^{(n)}(0)=1$$

$$
\begin{align*}
P_{N,0}(x) &= 1 + x + \frac{x^{2}}{2} + \frac{x^{3}}{3!} + \frac{x^{4}}{4!}+\dots\\
&= \sum_{n=0}^{N} \frac{x^{n}}{n!}
\end{align*}
$$
---
### Example: $f(x)=\sin x$ about $x=0$

$$
\begin{align*}
f(0) &= 0 \\
\\
f'(x) &= \cos x\\
f'(0) &= 1 \\
\\
f''(x) &= -\sin x\\
f''(0) &= 0 \\
\\
f'''(x) &= -\cos x\\
f'''(0) &= -1 \\
\\
f^{(4)}(x) &= \sin x \\
f^{(4)}(x) &= 0
\end{align*}
$$

$$
\begin{align*}
P_{3,0}(x) &= f(0)+f'(0)(x-0)+f''(0)\frac{(x-0)^{2}}{2}+f'''(0)\frac{(x-0)^{3}}{3!}\\
&= x - \frac{x^{3}}{6}
\end{align*}
$$
Since $\sin x$ is an odd function, the Taylor polynomials have only odd powers of $x$.

---
### Taylor Series

For a function $f$ to have a Taylor series at $x=a$, we need that $f$ is infinitely differentiable at $a$.

Since $P_{a}(x)=\sum_{n=0}^{\infty}\frac{f^{(n)}}{n!}(x-a)^{n}$ is a power series, it has an interval of convergence, that is, $P_{a}(x)$ converges absolutely on the interval $(a-\mu,a+\mu)$ and diverges outside $[a-\mu,a+\mu]$.

In all imaginable cases, the Taylor series will be a power series representation of the function $f$ near $a$ within the interval of convergence.

There are, however, pathological cases, where this is not true. All functions where Taylor series represented them at all reference points are called "analytic".

---
### Taylor Series Examples:

Interval of convergence: $\mathbb{R}$
$$
e^{x}=\sum_{n=0}^{\infty} \frac{x^{n}}{n!}
$$

Interval of convergence: $\mathbb{R}$
$$
\sin x = \sum_{n=0}^{\infty}\frac{(-1)^{n}}{(2n+1)!} x^{2n+1}
$$

Interval of convergence: $(-1,1)$
$$
\ln(1+x) = \sum_{n=1}^{\infty}\frac{(-1)^{n+1}x^{n}}{n}
$$

---
### MacLaurin Series

A Taylor series about $x=0$, that is:
$$
\sum_{n=0}^{\infty}\frac{f^{(n)}(0)}{n!}x^{n}
$$

---
### Example Question 

Prove that 

$$
\frac{1}{n^{a+1}} < \frac{1}{a} \left(\frac{1}{(n-1)^{2}} - \frac{1}{n^{a}}\right)
$$

for $a>0$ and $n=2,3, \ldots$ using

$$
f(x) \approx f(x_{0}) + f'(x_{0})(x-x_{0}) + \frac{f''(x_{0})}{2!} (x-x_{0})^{2}
$$

Let's try using 

$$
f(x) = \frac{1}{x^{a}}
$$

as a function to input.
And its derivatives are

$$
\begin{aligned}
f'(x) &= - \frac{a}{x^{a+1}}\\
\\
f''(x) &= \frac{a(a+1)}{x^{a+2}}
\end{aligned}
$$

Using Taylor's theorem, by taking $f(x) = \frac{1}{x^{a}}$ where $x=n-1$ and $x_{0}=n$ we get

$$
\frac{1}{(n-1)^{a}} = \frac{1}{n^{a}} + (-1)\left(\frac{-a}{n^{a+1}}\right) + \frac{a (a+1)}{2 \xi^{a+2}}
$$

for some $\xi \in (who knows)$ 

So discarding the last term gets us 

$$
\frac{1}{(n-1)^{a}} > \frac{1}{n^{a}} + \frac{a}{n^{a+1}}
$$

$$

$$