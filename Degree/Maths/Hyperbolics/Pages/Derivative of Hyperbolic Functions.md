---
tags:
  - degree/singlemathsa/hyperbolics
  - incomplete
---
![[Hyperbolics MOC 🌍]]

$$
\DeclareMathOperator{sech}{sech}
\DeclareMathOperator{arcsinh}{arcsinh}
\DeclareMathOperator{arccosh}{arccosh}
\DeclareMathOperator{arctanh}{arctanh}
\begin{align*}
\frac{d}{dx} [\arctanh x] &= \frac{1}{1-x^{2}}
\end{align*}
$$

### sinh x
$$
\frac{d}{dx} [\sinh x] = \cosh x
$$
### cosh x

$$
\frac{d}{dx} [\cosh x] = \sinh x
$$
### tanh x
$$
\frac{d}{dx} [\tanh x] = \sech^{2} x
$$
### arcsinh x
$$
\frac{d}{dx} [\arcsinh x] = \frac{1}{\sqrt{1+x^{2}}}
$$
##### Proof 
If we let $y = \arcsinh x$, then $\sinh y = x$.

Differentiating implicitly we get
$$\frac{dy}{dx} \cosh y = 1$$
And rearranging gets us 
$$
\frac{dy}{dx} = \frac{1}{\cosh y}
$$
But we can't leave it in terms of $y$, so we use $\cosh^{2} y - \sinh^{2} y \equiv 1$.
$$
\begin{align*}
&\cosh^{2} y - \sinh^{2} y \equiv 1\\
\\
&\cosh y = \sqrt{1 + \sinh^{2} y}
\end{align*}
$$
So 
$$
\frac{dy}{dx} = \frac{1}{\sqrt{1 + \sinh^{2} y}}
$$
And using our original substitution gets us
$$
\frac{dy}{dx} = \frac{1}{\sqrt{1 + x^{2}}}
$$

### arccosh
$$
\frac{d}{dx} [\arccosh x] = \frac{1}{\sqrt{1-x^{2}}}
$$

---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]
