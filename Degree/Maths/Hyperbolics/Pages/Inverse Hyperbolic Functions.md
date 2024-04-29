---
tags:
  - degree/singlemathsa/hyperbolics
---
![[Hyperbolics MOC 🌍]]

### The $\DeclareMathOperator{arcsinh}{arcsinh}\arcsinh$ function

$\arcsinh$ is the inverse function of $\sinh$ such that:
$$\sinh(\arcsinh{x})=x$$
Since $\sinh$ is a function of $\exp$, you can write $\arcsinh$ as a function of $\ln$.
$$
\begin{align*}
\sinh y &= x \\
\frac{1}{2}\left(e^y-e^{-y}\right)&=x \\
e^y-e^{-y}-2x&=0 \\
e^{2y}-2xe^y-1&=0
\end{align*}
$$
$$\begin{aligned}
e^y&=\frac{2x\pm\sqrt{4x^2-4(1)(-1)}}{2} \\
e^y&=\frac{2x\pm\sqrt{4(x^2+1)}}{2} \\
e^y&=x\pm\sqrt{x^2+1} \\
y&=\ln(x\pm\sqrt{x^2+1}) \\
y&=\ln(x+\sqrt{x^2+1})
\end{aligned}$$
Since $\ln$ is only defined for $x>0$, we choose the positive solution here since $\sqrt{x^2+1}>x$.

---
### The $\DeclareMathOperator{arccosh}{arccosh}\arccosh$ Function

$\arccosh$ is the inverse function of $\cosh$ such that:
$$\cosh(\arccosh x)=x$$
