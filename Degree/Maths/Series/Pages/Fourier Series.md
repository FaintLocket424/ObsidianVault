---
tags:
  - incomplete
  - degree/mathsforcs/series
---
![[Series MOC 🌍]]

Recall the [[Taylor's MOC 🌍|Taylor Series]] where if $f(x)$ is **infinitely differentiable**, the Taylor series representation is

$$
f(x) = \sum^{\infty}_{n=0} f^{(n)} (x_{0}) \frac{(x-x_{0})^{n}}{n!}
$$

and this converges to $f(x)$ on $(x_{0} - r, x_{0} + r)$ where $r$ is the radius of convergence.

The Taylor series requires that the function is infinitely differentiable at the point $x=x_{0}$.
This works for some functions but no luck for less friendly functions.
![[Pasted image 20240422161935.png]]

A Fourier series expansion expresses a function as an infinite sum of sines and cosines such that the series converges to the function at almost any point.

Where it doesn't exactly converge, it converges to a "sensible" value.

### Trigonometry Background 
Firstly, note that 

$$
\int^{\pi}_{-\pi} \cos(mx) dx = \int^{\pi}_{- \pi} \sin(nx) dx = 0
$$

These trigonometric identities will be important.

$$
\begin{aligned}
\sin A \cos B &= \frac{1}{2}(\sin(A-B) + \sin(A+B))\\
\\
\sin A \sin B &= \frac{1}{2} (\cos(A-B) - \cos(A+B))\\
\\
\cos A \cos B &= \frac{1}{2}(\cos(A-B) + \cos(A+B))
\end{aligned}
$$

With these we can show

$$
\begin{aligned}
\int^{\pi}_{-\pi} \sin nx \cos mx dx &= \frac{1}{2} \int^{\pi}_{-\pi} \sin(n-m)x dx + \frac{1}{2} \int^{\pi}_{-\pi} \sin (n+m) x dx \\
\\
&= 0 \quad \forall n, m
\end{aligned}
$$

And we can show that 

$$
\int^{\pi}_{-\pi} \sin(nx) \sin(mx) dx = \frac{1}{2} \int^{\pi}_{-\pi} \cos((n-m)x) dx - \frac{1}{2} \int^{\pi}_{-\pi} \cos((n+m)x) dx
$$

And this equals
- 0 if $m \ne \pm n$ or $m=n=0$
- $\pi$ if $m=n \ne 0$
- $-\pi$ if $m=-n \ne 0$

And we can show 

$$
\int^{\pi}_{-\pi} \cos(nx) \cos(mx) dx = \frac{1}{2} \int^{\pi}_{-\pi} \cos((n-m)x) dx + \frac{1}{2} \int^{\pi}_{-\pi} \cos((n+m)x) dx
$$

And this equals 
- 0 if $m \ne \pm n$
- $\pi$ if $m = \pm n \ne 0$
- $2\pi$ if $m=n=0$ 

---
### Fourier Series 

For a function $f(x)$ where $-\pi < x < \pi$, we will construct a series for $f$ in the form 

$$
f(x) \approx \frac{a_{0}}{2} + \sum^{\infty}_{n=1} \left[ a_{n} \cos(nx) + b_{n} \sin(nx) \right]
$$

The $\cos nx$ and $\sin nx$ terms get higher and higher frequencies.

The function is restricted to $[-\pi,\pi]$ but we can scale an arbitrary function $f$ on a range $[a,b]$ by setting 

$$
f(x) = g\left(\left(x - \frac{b+a}{2}\right) \frac{2\pi}{(b-a)}\right)
$$

where $g$ is a function on $[-\pi,\pi]$.
We "move each point to the left" by $\frac{b+a}{2}$ and scale it by $\frac{2\pi}{b-a}$.

---
### Fourier Coefficients 

If 

$$
f(x) = \frac{a_{0}}{2} + \sum^{\infty}_{n=1} a_{n} \cos(nx) + b_{n} \sin(nx)
$$

then multiplying by $\cos(mx)$ and integrating over the range $[-\pi,\pi]$ gets us:

$$
\int^{\pi}_{-\pi} f(x) \cos (mx) dx = \int^{\pi}_{-\pi} \left( \frac{a_{0}}{2} + \sum^{\infty}_{n=1} \left[ a_{n} \cos(nx) + b_{n} \sin(nx) \right] \right) \cos(mx) dx
$$

Expanding this gets us three terms.

$$
\begin{aligned}
&\frac{a_{0}}{2} \int^{\pi}_{-\pi} \cos(mx) dx\\
\\
+ &\sum^{\infty}_{n=1} a_{n} \int^{\pi}_{-\pi} \cos(nx) \cos(mx) dx \\
\\
+ &\sum^{\infty}_{n=1} b_{n} \int^{\pi}_{-\pi} \sin(nx) \cos(mx) dx
\end{aligned}
$$

We can analyse each of these individually.

$$
\frac{a_{0}}{2} \int^{\pi}_{-\pi} \cos(mx) dx = 0
$$

The next one has only one term of it's sequence that is not zero. 
$\int^{\pi}_{-\pi} \cos nx \cos mx dx = \pi$ when $m=n$.

$$
\sum^{\infty}_{n=1} a_{n} \int^{\pi}_{-\pi} \cos(nx) \cos(mx) dx = \pi a_{m}
$$

And the final one is always equal to zero.

$$
\sum^{\infty}_{n=1} b_{n} \int^{\pi}_{-\pi} \sin(nx) \cos(mx) dx = 0
$$

And it equals $\pi a_{m}$.

Multiplying by $\sin(mx)$ instead and integrating over $[-\pi, \pi]$ gets us:

$$
\int^{\pi}_{-\pi} f(x) \sin(mx) dx = \int^{\pi}_{-\pi} \left( \frac{a_{0}}{2} + \sum^{\infty}_{n=1} a_{n} \cos(nx) + b_{n} \sin(nx) \right) \sin (mx) dx
$$

which expands to 

$$
\begin{aligned}
&\frac{a_{0}}{2} \int^{\pi}_{-\pi} \sin(mx) dx \\
\\
+ &\sum^{\infty}_{n=1} a_{n} \int^{\pi}_{-\pi} \cos(nx) \sin(mx) dx\\
\\
+ &\sum^{\infty}_{n=1} b_{n} \int^{\pi}_{-\pi} \sin(nx) \sin(mx) dx
\end{aligned}
$$

And equals $\pi b_{m}$.

From this work, we can see that 

$$
\begin{aligned}
a_{n} &= \frac{1}{\pi} \int^{\pi}_{-\pi} f(x) \cos(nx) dx\\
\\
b_{n} &= \frac{1}{\pi} \int^{\pi}_{-\pi} f(x) \sin (nx) dx
\end{aligned}
$$

---
### Fourier Series Theorem 
If $f$ is piecewise continuous and $\int^{\pi}_{-\pi}[f(x)]^{2} dx$ exists, then the Fourier series converges.

For all points $x$ at which $f$ is continuous, the series converges to $f(x)$.
For points $y$ at which there is a jump discontinuity the series converges to 

$$
\frac{1}{2} \left(\lim_{x \to y^{-}} f(x) + \lim_{x \to y^{+}} f(x)\right)
$$

##### Example 1 
Represent $y = x^{2}$ as a Fourier series.

Remembering the equation for the Fourier series 

$$
f(x) \approx \frac{a_{0}}{2} + \sum^{\infty}_{n=1} a_{n} \cos(nx) + b_{n} \sin(nx)
$$

where 

$$
\begin{aligned}
a_{n} &= \frac{1}{\pi} \int^{\pi}_{-\pi} f(x) \cos(nx) dx\\
\\
b_{n} &= \frac{1}{\pi} \int^{\pi}_{-\pi} f(x) \sin(nx) dx
\end{aligned}
$$

For this question, it would be good to be familiar with the [[Useful Trig Function Properties]].

###### Finding $a_{0}$ 
First, we find a value for $a_{0}$ 

$$
a_{0} = \frac{1}{\pi} \int^{\pi}_{-\pi} x^{2} dx = \frac{1}{\pi} \left[ \frac{x^{3}}{3} \right]^{\pi}_{-\pi} = \frac{2\pi^{2}}{3}
$$

###### Finding $a_{n}$ 
Then we find an equation for $a_{n}$ by plugging our function into the formula

$$
a_{n} = \frac{1}{\pi} \int^{\pi}_{-\pi} x^{2} \cos(nx) dx
$$

From here we use [[Integration by Parts]] to integrate this, with $u=x^{2}$ and $v'=\cos(nx)$ 

$$
a_{n} = \frac{1}{\pi} \left[ \frac{x^{2} \sin(nx)}{n} \right]^{\pi}_{-\pi} - \frac{1}{\pi} \int^{\pi}_{- \pi} \frac{2x}{n} \sin (nx) dx
$$

After factoring out the constants we get

$$
a_{n} = \frac{1}{\pi n} \left[ x^{2} \sin(nx) \right]^{\pi}_{-\pi} - \frac{2}{\pi n} \int^{\pi}_{- \pi} x\sin (nx) dx
$$

Next let's look at the definite integral on the left.

$$
\begin{aligned}
\frac{1}{\pi n} \left[ x^{2} \sin(nx) \right]^{\pi}_{-\pi}
&= \frac{1}{\pi n} \left[ \left(\pi^{2} \sin (n \pi)\right) - \left( \pi^{2} \sin(-n \pi) \right) \right]
\end{aligned}
$$

We can use the fact that $\sin x$ is an [[Odd Function]] to simplify this further.

$$
\begin{aligned}
\frac{1}{\pi n} \left[ x^{2} \sin(nx) \right]^{\pi}_{-\pi}
&= \frac{1}{\pi n} \left[ \left(\pi^{2} \sin (n \pi)\right) + \left( \pi^{2} \sin(n \pi) \right) \right]\\
\\
&= \frac{2 \pi}{n} \sin(n \pi)
\end{aligned}
$$

Something to notice here is that $\sin(n \pi)=0$ for all integer values of $n$ (Check [[Useful Trig Function Properties#$ sin (n pi)$|Useful Trig Function Properties]]). So this whole term cancels out and this integral evaluates to 0.

With that, we turn our attention to the second part which we again do [[Integration by Parts]] on with $u=x$ and $v' = \sin(-n \pi)$, making $u'=1$ and $v = - \frac{1}{n} \cos(nx)$ 

$$
a_{n} = - \frac{2}{\pi n} \left[ - \frac{x}{n} \cos(nx) \right]^{\pi}_{- \pi} - \frac{2}{\pi n} \int^{\pi}_{-\pi} - \frac{1}{n} \cos(nx) dx
$$

With that we can pull out the negative signs and the constants. Remember that $n$ is a constant here.

$$
a_{n} = \frac{2}{\pi n^{2}} \left[ x \cos(nx) \right]^{\pi}_{-\pi} + \frac{2}{\pi n^{2}} \int^{\pi}_{- \pi} \cos(nx) dx
$$

Now, turn your attention to the right hand integral. Notice that $\int^{\pi}_{- \pi} \cos(nx) dx = 0$ for all integer values of $n \ne 0$ (check [[Useful Trig Function Properties#$ int { pi}_{- pi} cos(nx)$|Useful Trig Function Properties]]). We can discard that term and only focus on the left hand side.

$$
\begin{aligned}
a_{n} &= \frac{2}{\pi n^{2}} \left[ (\pi \cos(n \pi)) - (-\pi \cos(-n \pi)) \right]\\
\\
&= \frac{2}{n^{2}} (2 \cos(n \pi))\\
\\
&= \frac{4 \cos(n \pi)}{n^{2}}
\end{aligned}
$$
While this is maybe correct, we can simplify it even more by using the [[Useful Trig Function Properties#$ cos (n pi)$|Useful Trig Function Properties]] which state that $\cos(n \pi) = (-1)^{n}$ for all $n \in \mathbb{N}$.

$$
a_{n} = \frac{4(-1)^{n}}{n^{2}}
$$

###### Finding $b_{n}$ 
Now we do the same process for $b_{n}$ 

$$
b_{n} = \frac{1}{\pi} \int^{\pi}_{-\pi} x^{2} \sin(nx) dx
$$

Integrating [[Integration by Parts|By Parts]] with $u=x^{2}$ and $v'=\sin(nx)$

$$
\begin{aligned}
b_{n}&= \frac{1}{\pi} \left[ - \frac{x^{2}}{n} \cos(nx) \right]^{\pi}_{-\pi} - \frac{1}{\pi} \int^{\pi}_{-\pi} - \frac{2x}{n} \cos(nx) dx\\
\\
&= - \frac{1}{n \pi} \left[ x^{2} \cos(nx) \right]^{\pi}_{-\pi} + \frac{2}{n \pi} \int^{\pi}_{-\pi} x \cos(nx) dx
\end{aligned}
$$

Evaluating the left hand definite integral

$$
\begin{aligned}
- \frac{1}{n \pi} \left[ x^{2} \cos(nx) \right]^{\pi}_{-\pi} &= - \frac{1}{n \pi} \left[ (\pi^{2} \cos(n \pi)) - ((- \pi)^{2} \cos(-n \pi)) \right]\\
\\
&= - \frac{1}{n \pi} \left[ \pi^{2} \cos(n \pi) - \pi^{2} \cos(n \pi) \right]\\
\\
&= 0
\end{aligned}
$$

So now we just focus on the right hand integral 

$$
b_{n} = \frac{2}{n \pi} \int^{\pi}_{-\pi} x \cos(nx) dx
$$

Integrating [[Integration by Parts|By Parts]] with $u=x$ and $v'=\cos(nx)$

$$
\begin{aligned}
b_{n} &= \frac{2}{n \pi} \left[ \frac{x}{n} \sin(nx) \right]^{\pi}_{- \pi} - \frac{2}{n \pi} \int^{\pi}_{-\pi} \frac{1}{n} \sin(nx) dx\\
\\
&= \frac{2}{n^{2} \pi} \left[ x \sin(nx) \right]^{\pi}_{-\pi} - \frac{2}{n^{2} \pi} \int^{\pi}_{-\pi} \sin(nx) dx
\end{aligned}
$$

Now evaluating the left hand side 

$$
\begin{aligned}
\frac{2}{n^{2} \pi} \left[ x \sin(nx) \right]^{\pi}_{-\pi} &= \frac{2}{n^{2} \pi} \left[ (\pi \sin(n \pi)) - (- \pi \sin(- n \pi)) \right]\\
\\
&= \frac{2}{n^{2} \pi} \left[ \pi \sin(n \pi) - \pi \sin(n \pi) \right]\\
\\
&= 0
\end{aligned}
$$

So that equals zero, we can move to the right hand side.

$$
\begin{aligned}
b_{n} &= - \frac{2}{n^{2} \pi} \int^{\pi}_{-\pi} \sin(nx) dx\\
\\
&= - \frac{2}{n^{2} \pi} \left[ - \frac{1}{n} \cos(nx) \right]^{\pi}_{-\pi}\\
\\
&= \frac{2}{n^{3} \pi} \left[ \cos(nx) \right]^{\pi}_{-\pi}\\
\\
&= \frac{2}{n^{3} \pi} \left[ \cos(n \pi) - \cos(n \pi) \right]\\
\\
b_{n} &= 0
\end{aligned}
$$

###### Final Fourier Series 
Remembering our Fourier series equation is

$$
f(x) \approx \frac{a_{0}}{2} + \sum^{\infty}_{n=1} a_{n} \cos(nx) + b_{n} \sin(nx)
$$

We can put our numbers into the equation 

$$
f(x) \approx \frac{\pi^{2}}{3} + \sum^{\infty}_{n=1} \frac{4 (-1)^{n}}{n^{2}} \cos(nx)
$$
And on a graph, with 10 terms in the series, we get
![[Pasted image 20240429023046.png]]












---
### Additional Information

- [Wikipedia]
- [[Maths for CS Calculus Topic 14 Fourier Series.pdf|Fourier Series Lecture Notes]]
- [Maybe Practical Q and As]



