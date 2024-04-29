---
tags:
  - degree/singlemathsa/series/taylor
---
![[Taylor's MOC 🌍]]

### Taylor's Theorem
Want to bound the error in the approximation of $f(x)$ by $P_{N,a}(x)=\sum_{n=0}^{N} \frac{f^{(N)}(a)}{n!}(x-a)^{n}$

Let $f(x)$ be $(N+1)$ times differentiable with $f^{(N+1)}(x)$ being continuous.

Let $P_{N,a}(x)$ be the $N$-th order Taylor polynomial of $f(x)$ about $a$. Let $R_{N+1,a}(x)$ be the error, that is:
$$
\begin{align*}
f(x)=P_{N,a}(x)+R_{N+1,a}(x)
\end{align*}
$$
Then there exists a $\psi$ between $x$ and $a$ such that:
$$
R_{N+1,a}(x)=\frac{f^{(N+1)}(\psi)}{(N+1)!}(x-a)^{N+1}
$$

We call $R_{N+1,a}(x)$ the $N$-th remainder term.

The right hand side of 
$$R_{N+1,a}(x)=\frac{f^{(N+1)}(\psi)}{(N+1)!}(x-a)^{N+1}$$
is called the Lagrange term of the remainder.

If $f$ is a polynomial of degree $N$, then $P_{N,a}(x)$ agrees with $f(x)$ and the $N$-th reminder term disappears. This is in accordance with the fact that the $(N+1)$-st derivative of such a polynomial vanishes and
$$
\frac{f^{(N+1)}(\psi)}{(N+1)!}(x-a)^{N+1}\equiv0
$$
The crucial part is, while we do not know the value of $\psi\in(a,x)$, we can still utilise Taylor's Theorem if we find a bound on $|f^{(N+1)}|$ on all of $(a,x)$.
If $|f^{N+1}(\psi)|\le M\forall \psi\in(a,x)$ then 
$$
|f(x)-P_{N,a}(x)|\le \frac{M}{(N+1)!}(x-a)^{N+1}
$$

---
### Example: $f(x)=\cos x$

Find a Taylor polynomial approximation of $\cos(0.5)$ accurate to $\pm0.01$.

Take $f(x)=\cos x$ and $a=0$.
We have:
$f(0)=1$

$f'(x)=-\sin x$
$f'(0)=0$

$f''(x)=-\cos x$
$f''(0)=-1$

$f'''(x)=\sin x$
$f'''(0)=0$

etc.

So:
$P_{1}(x)=f(0)+f'(0)(x-0)=1$
$P_{2}(x)=P_{3}(x)=f(0)+f'(0)+\frac{f''(0)}{2}x^{2}=1-\frac{x^{2}}{2}$

The error is $R_{2}(x)=\frac{f''(\psi)}{2}x^{2}$ if we choose $P_{1}(x)$.
Which is $\frac{-\cos(\psi)}{2}x^{2}$ so $|\cos \psi| \le 1$

So $|R_{2}(x)| \le \frac{x^{2}}{2}$
So $|R_{2}(0.5)| \le \frac{1}{2}(0.5)^{2}=\frac{1}{8}>0.01$

If we choose $P_{3}(x)=1 - \frac{x^{2}}{2}$ as approximation, error is:
$$
R_{4}(x)=\frac{f^{(4)}(\psi)}{4!}x^{4}=\frac{\cos(\psi)}{4!}x^{4}
$$
$|R_{4}(0.5)\le \frac{1}{4!}(0.5)^{4}\approx 0.0026$

---
### Example: $f(x)=e^{\cos x}$

Find $P_{2}(x)$ about $x=\frac{\pi}{2}$ and get a bound on the error.

$$
\begin{align*}
f\left(\frac{\pi}{2}\right) &= e^{0}=1\\
\\
f'(x) &= -\sin x e^{\cos x}\\
f'\left(\frac{\pi}{2}\right)&= -1\\
\\
f''(x) &= (-\cos x + \sin^{2}x) e^{\cos x}\\
f''\left(\frac{\pi}{2}\right) &= 1\\
\\
f'''(x) &= (\sin x + 3\sin x \cos x - \sin^{3}x) e^{\cos x}
\end{align*}
$$

$$
\begin{align*}
P_{2,\frac{\pi}{2}} &= f\left(\frac{\pi}{2}\right)+f'\left(\frac{\pi}{2}\right)\left(x - \frac{\pi}{2}\right)+ f''\left(\frac{\pi}{2}\right)(x - \frac{\pi}{2})^{2}\\
\\
&= 1-\left(x - \frac{\pi}{2}\right)+ \frac{1}{2} \left(x - \frac{\pi}{2}\right)^{2}
\end{align*}
$$

With remainder:
$$
\begin{align*}
R_{3 , \frac{\pi}{2}}(x) &= \frac{f^{(3)}(\psi)}{3!} \left(x - \frac{\pi}{2}\right)^{3}\\
\\
&= \frac{(\sin \psi + 3\sin \psi \cos \psi - \sin^{3}\psi) e^{\cos \psi}}{3!}\left(x - \frac{\pi}{2}\right)^{3}
\end{align*}
$$
Since $|\sin \psi|,|\cos \psi|\le1$, we have:
$$
\begin{align*}
\left|\sin \psi + 3\sin \psi \cos \psi - \sin^{3}\psi\right|e^{\cos \psi}&\le 5e
\end{align*}
$$

So $|R_{3, \frac{\pi}{2}}(x)| \le \frac{5e}{6}(x- \frac{\pi}{2})^{3}$.

But we can do better than that for a bound with some trig manipulations.

$$
\begin{align*}
\sin \psi + 3\sin \psi \cos \psi - \sin^{3}\psi &= \sin \psi (1-\sin^{2}\psi)+3\sin \psi \cos \psi\\
&= \sin\psi \cos^{2}\psi+3\sin \psi \cos \psi\\
&= \sin \psi \cos \psi(\cos \psi +3)\\
&= \frac{1}{2}\sin(2\psi)(\cos\psi+3)
\end{align*}
$$
And so:
$$
\begin{align*}
\frac{1}{2}\sin(2\psi)(\cos\psi + 3) &\le \frac{1}{2}(1)(1+3)=2
\end{align*}
$$

So:
$|R_{3, \frac{\pi}{2}}(x)| \le \frac{e}{3}(x- \frac{\pi}{2})^{3}$

