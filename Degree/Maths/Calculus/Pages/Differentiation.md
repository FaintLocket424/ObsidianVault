---
tags:
  - degree/mathsforcs/calculus
---
![[Calculus MOC 🌍]]
### The Basics

A derivative of a function $f(x)$ at the point $x=x_{0}$ is the instantaneous rate of change of $f$ at the point $x_{0}$.

This is also known as the gradient in normal words.

The gradient at $x_{0}$ can be approximated by $\frac{f(x)-f(x_{0})}{x-x_{0}}$

The closer $x$ is to $x_{0}$, the better the approximation is.\

Formally, $f$ is differentiable at $x=x_{0}$ if and only if $\lim_{x\rightarrow x_{0}}\frac{f(x)-f(x_{0})}{x-x_{0}}$ exists. This can also be written as $\lim_{h\rightarrow 0} \frac{f(x_{0}+h)-f(x_{0})}{h}$.

The derivative at $x_{0}$ is denoted $f'(x_{0})$ or $\frac{df}{dx}(x_{0})$.

---
### Basic Derivatives

If $f(x)=c$ for some constant $c$, then $f'(x)=0$.
$$f'(x)=\lim_{h\rightarrow0}\frac{f(x+h)-f(x)}{h}=\lim_{h\rightarrow0}\frac{c-c}{h}=\lim_{h\rightarrow0}\frac{0}{h}=\lim_{h\rightarrow0}0=0$$

If $f(x)=x$ then $f'(x)=1$
$$
f'(x)=\lim_{h\rightarrow0}\frac{f(x+h)-f(x)}{h}=\lim_{h\rightarrow0}\frac{x+h-x}{h}=\lim_{h\rightarrow0}\frac{h}{h}=\lim_{h\rightarrow0}1=1
$$

If $f(x)=x^{n}$ for some $n\in\mathbb{N}^{+}$, then $f'(x)=n x^{n+1}$.
$$
\begin{align*}
\lim_{h\rightarrow 0} \frac{f(x+h)-f(x)}{h}&=\lim_{h\rightarrow 0} \frac{(x+h)^{n}-x^{n}}{h}\\
\\
(x+h)^{n}&=x^{n}+n x^{n-1}h+\binom{n}{2}x^{n-2}h^{2}+\dots+\binom{n}{n}h^{n}\\
\frac{(x+h)^{n}-x^{n}}{h}&=nx^{n-1}+h(\binom{n}{2}x^{n-2}+\dots+\binom{n}{n}h^{n-1})\\
\\
\therefore \lim_{h\rightarrow 0}\frac{(x+h)^{n}-x^{n}}{h}&=nx^{n-1}
\end{align*}
$$

If $f(x)=\sin \alpha x$, then $f'(x)=\alpha \cos \alpha x$

If $f(x)=\cos \alpha x$, then $f'(x)=-\alpha \sin \alpha x$

If $f(x)=g(x)+h(x)$, then $f'(x)=g'(x)+h'(x)$

---
### Kinky Functions

![[Pasted image 20240122223628.png|550]]

$$
f(x)=
\begin{cases}
2-x, &x<1 \\
x^{2} &x \ge 1 \\
\end{cases}
$$
Taking the limit at $x=1$ when $h>0$, we get
$$
\frac{f(1+h)-f(1)}{h}=\frac{(1+h)^{2}-1}{h}=2+h
$$
But when $h<0$
$$
\frac{f(1+h)-f(1)}{h}=\frac{2-(1+h)-1}{h}=\frac{-h}{h}=-1
$$
Unless specified, $h$ can be positive or negative in a limit. When $x\rightarrow x_{0}$, $x$ can come up to $x_0$ just like we usually assumes it comes down to $x_0$.

We can write $\lim_{h\rightarrow 0^{+}}$ for a limit approaching 'from above' or 'from the right'.

We can write $\lim_{h\rightarrow 0^{-}}$ for a limit approaching 'from below' or 'from the left'.

For $f$, $\lim_{h\rightarrow 0^{+}}=2$ and $\lim_{h\rightarrow 0^{-}}=-1$ so the limit does not exist and so the derivative does not exist.

---
### Continuity

A function $f:\mathbb{R}\rightarrow \mathbb{R}$ is continuous at $x=a$ if:
- $\lim_{x\rightarrow a^{-}}=\lim_{x\rightarrow a^{+}}=L$
- $f(a)=L$
So there cannot be jumps in value.
![[Pasted image 20240122223628.png|500]]
![[Pasted image 20240122224737.png|500]]
These are two non-continuous functions.

---
### Higher Order Derivatives

The derivative of $f$ is $f'$.

If $f'$ is differentiable, then the derivative of $f'$ is $f''$. The second derivative.

We can repeat this to get the third derivative $f'''$, the fourth $f''''$ etc.

If you can infinitely differentiate a function, it is called a **smooth** function.

---
### Non-Continuous Functions

Take $\tan x=\frac{\sin x}{\cos x}$
$$
\begin{align*}
\lim_{x\rightarrow \frac{\pi}{2}} \sin (x)&=1 \\
\lim_{x\rightarrow \frac{\pi}{2}} \cos (x)&=0
\end{align*}
$$
So as we approach $\frac{\pi}{2}$ from below, $\cos x$ is positive, so $\tan x$ gets arbitrarily positively large.

As we approach $\frac{\pi}{2}$ from above, $\cos x$ is negative, so $\tan x$ gets arbitrarily negatively large.

Even though it's not differentiable at $\frac{\pi}{2}$, it's still smooth on $\left(-\frac{\pi}{2},\frac{\pi}{2}\right)$

---
### Product Rule

If $f(x)$ and $g(x)$ is differentiable, then so is $f(x)g(x)$.
$$
\frac{df(x)g(x)}{dx}=f'(x)g(x)+f(x)g'(x)
$$
##### Proof:
$$
\begin{align*}
\frac{df(x)g(x)}{dx} &= \lim_{x\rightarrow x_{0}}\frac{f(x)g(x)-f(x_{0})g(x_{0})}{x-x_{0}}
\end{align*}
$$
So:
$$
\begin{align*}
\frac{f(x)g(x)-f(x_{0})g(x_{0})}{x-x_{0}} &= \frac{f(x)g(x)-f(x_{0})g(x)+f(x_{0})g(x)-f(x_{0})g(x_{0})}{x-x_{0}}\\
\\
&= \frac{f(x)-f(x_{0})}{x-x_{0}}g(x)+\frac{g(x)-g(x_{0})}{x-x_{0}}f(x_{0})
\end{align*}
$$

So:
$$
\begin{align*}
\frac{df(x)g(x)}{dx} &= f'(x_{0})\lim_{x\rightarrow x_{0}}g(x)+g'(x_{0})f(x_{0}) \\
\\
&=f'(x_{0})g(x_{0})+g'(x_{0})f(x_{0})
\end{align*}
$$

---
### Chain Rule

If $f(x)$ and $g(x)$ are differentiable at $x_{0}$ and $g(x_{0})$, then $\frac{dfg(x)}{dx}$ at $x_{0}$ is $f'(g(x_{0})) g'(x_{0})$.
$$
\begin{align*}
\frac{d(f \circ g(x))}{dx} &= \lim_{x\rightarrow x_{0}} \frac{f(g(x))-f(g(x_{0}))}{x-x_{0}} \\\\&=  \lim_{x\rightarrow x_{0}} \frac{f(g(x)) - f(g(x_{0}))}{g(x)-g(x_{0})} \cdot \lim_{x \rightarrow x_{0}} \frac{g(x)-g(x_{0})}{x-x_{0}}
\end{align*}
$$
As $x \rightarrow x_{0}$, $g(x)\rightarrow g(x_{0})$ then:
$$
\begin{align*}
\lim_{x\rightarrow x_{0}} \frac{f(g(x)) - f(g(x_{0}))}{g(x)-g(x_{0})} &= \lim_{g(x)\rightarrow g(x_{0})} \frac{f(g(x)) - f(g(x_{0}))}{g(x)-g(x_{0})}=f'(g(x))
\end{align*}
$$

When using composite functions it's cleaner to use a new variable $u$. The function $f\circ g(x)=f(u)$ where $u=g(x)$. You can then write
$$\frac{df}{dx} = \frac{df}{du} \frac{du}{dx}$$
##### Example: $\frac{d(\sin (x^{2}+3))}{dx}$

Let's say $u=x^{2}+3$ and $f(u)=\sin(u)$.

So then $f'(u)=\cos u$ and $u'(x)=2x$.

Chain rule tells us $\frac{df}{dx} = \frac{df}{du} \frac{du}{dx}$ so:
$$
f'(x)=\cos(u) \times 2x=2x\cos(x^{2}+3)
$$
##### Example: $\frac{d(\sin \sqrt{x^{2}+1})}{dx}$

Let's say $v=x^{2}+1$, and $u=\sqrt{v}$ and $f=\sin u$.

$f'(x)=\cos u$
$u'(x) = \frac{1}{2} v^{-\frac{1}{2}}$
$v'(x)=2x$

Chain rule tells us $\frac{df}{dx} = \frac{df}{du} \frac{du}{dv} \frac{dv}{dx}$
$$
\begin{align*}
f'(x) &= 2x \times \frac{1}{2}v^{- \frac{1}{2}} \times \cos u \\
\\
&= \frac{x \cos u}{\sqrt{v}}\\
\\
&= \frac{x \cos \sqrt{x^{2}+1}}{\sqrt{x^{2}+1}}
\end{align*}
$$
---
### Quotient Rule

If $f(x)$ and $g(x)$ are differentiable at $x_{0}$ and $g(x_{0}) \ne 0$, then:
$$
\frac{d\left(\frac{f}{g}\right)}{dx} = \frac{f'(x)g(x) - g'(x)f(x)}{g(x)^{2}}
$$
##### Example: $\frac{d\left(\frac{3x+1}{x^{2}-2}\right)}{dx}$

Using quotient rule, $f(x)=3x=1$ and $g(x)=x^{2}-2$.
$$
\begin{align*}
h'(x) &= \frac{3(x^{2}-2) - (3x+1)2x}{(x^{2}-2)^{2}}\\
\\
&= \frac{-3x^{2}-2x-6}{(x^{2}-2)^{2}}
\end{align*}
$$
