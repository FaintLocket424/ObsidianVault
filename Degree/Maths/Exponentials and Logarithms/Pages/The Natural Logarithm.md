---
tags:
  - degree/singlemathsa/exponentialfunction
---
![[Exponentials and Logarithms MOC 🌍]]

### The $\ln$ Function

The $\ln$ function is the [[Inverse Functions|Inverse Function]] of the $\exp$ function.

![[IMAGE ex and lnx mirrored.png|350]]

Here we have $\exp{\left(x\right)}$ and $\ln{x}$ plotted on the same graph.
Since $\ln{x}$ is the inverse, you can see it's a mirror of $\exp{(x)}$ in the line $y=x$.

From factors we know about the $\exp$ function, we can infer information about $\ln$.

$\exp$ has:
- Domain: $x\in\mathbb{R}$
- Range: $x>0$

So from this we know $\ln$ has:
- Domain: $x>0$
- Range: $x\in\mathbb{R}$

Also since it's an inverse function we know that:
$$\begin{aligned}
\ln{(\exp{(x)})}&=x \\\\
\exp{(\ln{(x)})}&=x 
\end{aligned}$$
The $\exp$ and $\ln$ functions are special that it doesn't matter which way they go. This is not the case for all inverse functions.

---
### Properties of the $\ln$ function

##### $\ln(1)=0$

$$\begin{aligned}
1&=\exp(0) \\
\ln(1)&=\ln(\exp(0)) \\
\ln(1)&=0
\end{aligned}$$
---
##### $\ln(x)+\ln(y)=\ln(xy)$

$$\begin{aligned}
\ln{x}+\ln{y}&=\ln(\exp(\ln{x}+\ln{y})) \\\\
&= \ln(\exp(\ln{x})\exp(\ln{y})) \\\\
&=\ln(xy)
\end{aligned}$$
---
##### $\ln\left(\frac{1}{x}\right)=-\ln(x)$

(Idk I cba to prove it)

---
##### $\ln(x^n)=n\ln(x)$

(cba to prove it)

---
### $x^s$ where $s\in\mathbb{R}$

We have already know what $x^n$ is where $n\in\mathbb{N}$. It's just $x\times x\times x\times ...$ but what if the power is any real number.

Well have no fear because there's a formula.
$$
x^s=\exp(s\ln(x))
$$

We can prove this is the same as our definition for $x^n$:
$$\begin{aligned}
x^n&=\exp(n\ln(x))=\exp\left(\ln(x)+\ln(x)+...+\ln(x)\right) \\\\
&=\exp(\ln(x))\times\exp(\ln(x))\times\exp(\ln(x))\times...\exp(\ln(x)) \\\\
&=x\times x\times x\times ...\times x
\end{aligned}$$

---
### Derivative of $\ln x$

$$
\frac{d(\ln g(x))}{dx} = \frac{g'(x)}{g(x)}
$$
