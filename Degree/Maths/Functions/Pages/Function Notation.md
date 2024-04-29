---
tags:
  - degree/mathsforcs/functions
---
![[Functions MOC 🌍]]

### Functions

A function $f:A\rightarrow B$ is an assignment of a *unique* element of $B$ to every element of A.

Examples of functions are:
$$\begin{aligned}
f:\mathbb{N}\rightarrow\mathbb{N}\text{ where }f(n)=n^2+3
\end{aligned}$$

---
### Function Domain

The domain of the function is the set of inputs.

It would be $A$ in $f:A\rightarrow B$.

Take the function $f(x)=x^2$.

---
### Function Codomain

The codomain is the domain that the function maps to.

It would be $B$ in $f:A\rightarrow B$.

---
### Image

The image of any given input $a$ is $f(a)$.

---
### Function Pre-Image

The pre-image of an output are the inputs that will give you that output.

---
### Function Image / Range

The image or range of the function is the set of values that are mapped to by the function.

---
### Applying these to a real function

Take the function $f(x)=x^2$.

If we only input integers $\mathbb{Z}$, then our **domain** is $\mathbb{Z}$.
Since an integer squared is always a positive integer, our **codomain** would be $\mathbb{Z}^+$.

This can be written as $f:\mathbb{Z}\rightarrow\mathbb{Z}^+$.

When we input the number $2$ into our function, the **image** of 2 would be $2^2=4$.

But if we look at the output $4$, it's possible to get $4$ from $2$ and $-2$, so the **pre-image** of $4$ would be $\left\{-2,2\right\}$.

Now if we look at our set of inputs (domain), we can see that we can only get positive square numbers out of our function. So the range of $f$ would be $\left\{0,1,4,9,16,25\dots\right\}$.

Note that even though the number $3$ is a valid member of our codomain of $\mathbb{Z}^+$, it isn't a possible output of the function. This is what separates the codomain from the range.

---
### Injective Functions

Functions in which every value in the domain has a corresponding value in the codomain.

$f(x)=x^2$ would be injective as for all values of $x$ you can compute $x^2$.

$f(x)=\sqrt{x}$ would not be injective as negative values of $x$ cannot be mapped onto the function, assuming a domain of $\mathbb{R}$.

---
### Surjective Functions

A surjective function is one where all values in the codomain are reachable by an input in the domain.

---
### Bijective Functions

Each element in the domain maps to one element in the codomain, with no gaps.

A function which is both injective and surjective.

---
### Inverse Functions

For a function to have an inverse, it must be a bijection.

If we have $f:A\rightarrow B$, then $f^{-1}:B\rightarrow A$ is the function where if $f(a)=b$ then $f^{-1}(b)=a$.