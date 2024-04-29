---
tags:
  - degree/singlemathsa/series/taylor
---
![[Taylor's MOC 🌍]]

We can use Taylor series to evaluate limits of the form 
$$
\lim_{x\rightarrow c}\frac{f(x)}{g(x)}
$$
Where both $f(x)$ and $g(x)$ are functions which have [[Taylor Series#Taylor Series|Taylor Series]] expansions at $x=c$ and where $f(c)=g(c)=0$.

Write 
$$
\begin{align*}
f(x) &= \sum_{n=0}^{\infty}a_{n}(x-c)^{n} = \sum_{n=N}^{\infty}a_{n}(x-c)^{n}\\\\
&= a_{N}(x-c)^{N}+a_{N+1}(x-c)^{N+1}+\dots\\
&= (x-c)^{N}(a_{N}+a_{N+1}(x-c)+\dots)
\end{align*}
$$

$$
\begin{align*}
g(x) &= \sum_{n=0}^{\infty} b_{n}(x-c)^{n}=\sum_{m=M}^{\infty} b_{m}(x-c)^{m}\\
&= b_{M}(x-c)^{M}+b_{M+1}(x-c)^{M+1}+\dots\\
&= (x-c)^{M}(b_{M}+b_{M+1}(x-c)+\dots)
\end{align*}
$$

$$
\begin{align*}
\implies \lim_{x \rightarrow c}\frac{f(x)}{g(x)}&= \lim_{x\rightarrow c}\frac{(x-c)^{N}(a_N +a_{N+1}(x-c)+\dots)}{(x-c)^{M}(b_{M}+b_{M+1}(x-c)+\dots)}\\
\\
&= \lim_{x \rightarrow c}(x-c)^{N-M}\frac{a_{N}}{b_{M}}
\end{align*}
$$

If $N>M$, $\lim_{x\rightarrow c} \frac{f(x)}{g(x)}=\lim_{x \rightarrow c}(x-c)^{\text{Positive}}\frac{a_{N}}{b_{M}}=0$

If $N<M$, $\lim_{x\rightarrow c} \frac{f(x)}{g(x)}=\lim_{x \rightarrow c}(x-c)^{\text{Negative}}\frac{a_{N}}{b_{M}}=\text{Does Not Exist!}$

If $N=M$, $\lim_{x\rightarrow c} \frac{f(x)}{g(x)}=\frac{a_{N}}{b_{N}}\implies \frac{a_{n}}{b_{n}}=\frac{f^{(N)}(c)}{N!}\frac{N!}{g^{(N)}(c)}=\frac{f^{(N)}(c)}{g^{(N)}(c)}$
This is in line with L'Hôpital's rule.

---
### Example: Calculate $\lim_{x\rightarrow 0} \frac{\sin x}{x}$

Taylor series for $\sin x$:
$$
\begin{align*}
\sin x &= \sum_{n=0}^{\infty}\frac{(-1)^{n}}{(2n+1)!}x^{2n+1}\\
&= x - \frac{x^{3}}{3!} + \frac{x^{5}}{5!}\mp \dots\\
\end{align*}
$$

$$
\begin{align*}
\lim_{x\rightarrow 0} \frac{\sin x}{x}=\lim_{x \rightarrow 0} 1 - \frac{x^{2}}{3!} + \frac{x^{4}}{5!} \mp \dots = 1
\end{align*}
$$

---
### Example: Calculate $\lim_{x \rightarrow 0} \frac{f(x)-(x+1)}{x \cos x - \ln(1+x)}$, $f(x)=\exp\frac{(\sin x)}{(1-3x)}$

L'Hôpital's rule becomes messy for this.

###### Numerator:
$$
\sin x = x - \frac{x^{3}}{3!} + \frac{x^{5}}{5!}+\dots
$$

$$
\begin{align*}
\frac{1}{1-x} &= 1+x+x^{2}+\dots\\
\\
\frac{1}{1-3x} &= 1+3x + 9x^{2}+27x^{3}+\dots\\
\\
\frac{\sin x}{1-3x} &= \left(x - \frac{x^{3}}{3!} + \frac{x^{5}}{5!}+\dots\right)(1+3x+9x^{2}+27x^{3})\\
&= x + 3x^{2} + 9x^{3} + \dots -\frac{x^{3}}{6}+\dots\\
&= x+3x^{2} + \frac{56}{6}x^{3} + \dots
\end{align*}
$$

$$
\begin{align*}
e^{x} &= \sum_{n=0}^{\infty} \frac{x^{n}}{n!} = 1 + x + \frac{x^{2}}{2!} + \frac{x^{3}}{{3!}} + \dots\\
\end{align*}
$$

$$
\begin{align*}
\implies f(x) = \exp\left(\frac{\sin x}{1-3x}\right) &= 1 + \left(x + 3x^{2} + \frac{53}{6}x^{3} + \dots\right) +\\& \frac{1}{2!}\left(x + 3x^{2} + \frac{53}{6}x^{3} + \dots\right)^{2}+\\& \frac{1}{3!} (x + 3x^{2} + \frac{53}{6} x^{3} + \dots)^{3}+\dots\\
\end{align*}
$$
$$
\begin{align*}
f(x) &= 1 + x + [3 + \frac{1}{2}]x^{2} + \left[\frac{53}{6} x^{3} + \frac{1}{2} 6x^{3} + \frac{1}{6} x^{3}\right] + \dots\\
&= 1 + x + \frac{7}{2}x^{2} + 12x^{3}+\dots
\end{align*}
$$

So our numerator is $f(x)-(x+1)=\frac{7}{2}x^{2} + 12x^{3} + \dots$

###### Denominator
The denominator is $x \cos x - \ln(1+x)$

$$
\begin{align*}
\cos x &= \sum_{n=0}^{\infty}\frac{(-1)^{2n}}{(2n)!} x^{2n} = 1 - \frac{x^{2}}{2!} + \frac{x^{4}}{4} \pm \dots \\
\\
x \cos x &= x - \frac{1}{2}x^{3} + \frac{1}{4!}x^{5} + \dots\\
\\
\ln(1+x) &= \sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n}x^{n} \\
&= x - \frac{x^{2}}{2} + \frac{x^{3}}{3} + \dots\\
\\
x \cos x - \ln(1+x) &= \left(x - \frac{1}{2}x^{3} + \frac{1}{4!}x^{5} + \dots\right)-\left(x - \frac{x^{2}}{2} + \frac{^{3}}{3} + \dots\right)\\
\\
&= x^{2}+\dots
\end{align*}
$$




$$
\begin{align*}
\lim_{x \rightarrow 0} \frac{f(x)-(x+1)}{x \cos x - \ln(1+x)} = \lim_{x \rightarrow 0} \frac{\frac{7}{2}x^{2}+12x^{3}+\dots}{\frac{x^{2}}{2}+\dots}=\frac{\frac{7}{2}}{\frac{1}{2}}=7
\end{align*}
$$

##### Find a good approximation for $\ln \left(\frac{3}{2}\right)$

###### Approach 1:

$$
\begin{align*}
\ln(1+x) &= \sum_{n=1}^{\infty} \frac{(-1)^{n-1}}{n} x^{n}\\
&= x - \frac{x^{2}}{2} + \frac{x^{3}}{3} \pm \dots \quad |x|<1
\end{align*}
$$
$$
\begin{align*}
\ln \left(\frac{3}{2}\right) &\approx \frac{1}{2} - \frac{\left(\frac{1}{2}\right)^{2}}{2} + \frac{\left(\frac{1}{2}\right)^{3}}{3}=\frac{5}{12}=0.416666\\
\ln\left(\frac{3}{2}\right) &= 0.4054651081\\
\text{Error} &= 0.0112
\end{align*}
$$

###### Approach 2:

$$
\begin{align*}
\ln (1-x) &= \sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n} (-x)^{n} = -\sum_{n=1}^{\infty} \frac{x^{n}}{n}\\
&= -x - \frac{x^{2}}{2} - \frac{x^{3}}{3} - \dots \quad |x|<1\\
\\
\ln\left(\frac{1+x}{1-x}\right) &= \ln(1+x) - \ln(1-x) = 2x + \frac{2x^{3}}{3} + \frac{2x^{5}}{5} + \dots
\end{align*}
$$

We're looking for $\ln \left(\frac{3}{2}\right)$, so let's say we have $\ln(z)$ where $z=\frac{3}{2}$.
$$
\begin{align*}
z &= \frac{1+x}{1-x}\\
z-zx &= (1+z)x\\
x &= \frac{z-1}{z+1} = \frac{\frac{1}{2}}{\frac{5}{2}}=\frac{1}{5}
\end{align*}
$$
$$
\begin{align*}
\ln\left(\frac{3}{2}\right) &= \ln \left(\frac{1 + \frac{1}{5}}{1 - \frac{1}{5}}\right) = 2\left(\frac{1}{5}\right) + \frac{2 \left(\frac{1}{5}\right)^{3}}{3}=\frac{152}{375} = 0.4026666\\
\text{Error} &= 0.00013
\end{align*}
$$

