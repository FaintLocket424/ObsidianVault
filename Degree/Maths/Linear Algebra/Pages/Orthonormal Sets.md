---
tags:
  - degree/mathsforcs/linearalgebra
---
![[Linear Algebra MOC 🌍]]
$\DeclareMathOperator{proj}{proj}\DeclareMathOperator{span}{span}$
### Orthonormal Sets
The set of vectors in an [[Inner Product]] space is called orthogonal if all pairs of distinct vectors in the set are orthogonal. An orthogonal set of unit vectors is called orthonormal.

Example in $\mathbb{R}^{3}$ using the Euclidean inner product:
$$
\begin{align*}
v_{1} &= (0,1,0)\\
v_{2} &= (1,0,1)\\
v_{3} &= (1,0,-1)
\end{align*}
$$
The set $\{v_{1}, v_{2}, v_{3} \}$ is orthogonal, since
$$
\langle v_{1}, v_{3} \rangle = \langle v_{1}, v_{2} \rangle = \langle v_{2}, v_{3} \rangle = 0
$$
The [[Inner Product#Norm and Distance|Norms]] of the vectors are
$$
\begin{align*}
\| v_{1} \| &= 1\\
\| v_{2} \| &= \sqrt{2}\\
\| v_{3} \| &= \sqrt{2}
\end{align*}
$$
We can then create an orthonormal set $\{ q_{1}, q_{2}, q_{3} \}$
$$
\begin{align*}
q_{1} &= (0,1,0)\\
q_{2} &= \left(\frac{1}{\sqrt{2}}, 0, \frac{1}{\sqrt{2}}\right)\\
q_{3} &= \left(\frac{1}{\sqrt{2}}, 0, - \frac{1}{\sqrt{2}}\right)
\end{align*}
$$

>[!important] 
>If $S=\{ v_{1}, \ldots, v_{n} \}$ is an orthogonal set of non-zero vectors, then $S$ is linearly independent.

If $S= \{ v_{1}, \ldots, v_{n} \}$ is an orthonormal basis in $V$ then for any $\mathbf{u}$
$$
\mathbf{u} = \frac{\langle \mathbf{u}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1} + \frac{\langle \mathbf{u}, \mathbf{v}_{2} \rangle}{\| \mathbf{v}_{2} \|^{2}} \mathbf{v}_{2} + \ldots + \frac{\langle \mathbf{u}, \mathbf{v}_{n} \rangle}{\| \mathbf{v}_{n} \|^{2}} \mathbf{v}_{n}
$$
$$
\mathbf{u} = \langle \mathbf{u}, \mathbf{v}_{1} \rangle \mathbf{v}_{1} + \langle \mathbf{u}, \mathbf{v}_{2} \rangle \mathbf{v}_{2} + \ldots + \langle \mathbf{u}, \mathbf{v}_{n} \rangle \mathbf{v}_{n}
$$

---
### Orthogonal Projections 

If $W$ is a subspace in an inner product space $V$ then every vector $\mathbf{u} \in V$ can be uniquely expressed as $\mathbf{u} = \mathbf{w}_{1} + \mathbf{w}_{2}$ where $\mathbf{w}_{1} \in W$ and $\mathbf{w}_{2} \in W^{\perp}$.

This makes $\mathbf{w}_{1}$ the orthogonal projection of $\mathbf{u}$ onto $W$.
$$
\begin{align*}
\mathbf{w}_{1} &= \proj_{W} \mathbf{u}\\
\mathbf{w}_{2} &= \proj_{W^{\perp}} \mathbf{u}
\end{align*}
$$
We use the principles from [[#Orthonormal Sets]] to compute $\proj_{W}\mathbf{u}$.

So, if $\{ \mathbf{v}_{1} , \ldots, \mathbf{v}_{r} \}$ is an orthonormal basis for $W$ and $\mathbf{w}_{1} = c_{1} \mathbf{v}_{1} + c_{2} \mathbf{v}_{2} + \ldots + c_{r} \mathbf{v}_{r}$, then
$$
\proj_{W} \mathbf{u} = \frac{\langle \mathbf{u}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1} + \frac{\langle \mathbf{u}, \mathbf{v}_{2} \rangle}{\| \mathbf{v}_{2} \|^{2}} \mathbf{v}_{2} + \ldots + \frac{\langle \mathbf{u}, \mathbf{v}_{r} \rangle}{\| \mathbf{v}_{r} \|^{2}} \mathbf{v}_{r}
$$
And, if $\{ \mathbf{v}_{1} , \ldots, \mathbf{v}_{r} \}$ is an orthonormal basis in $W$ then
$$
\proj_{W} \mathbf{u} = \langle \mathbf{u}, \mathbf{v}_{1} \rangle \mathbf{v}_{1} + \langle \mathbf{u}, \mathbf{v}_{2} \rangle \mathbf{v}_{2} + \ldots + \langle \mathbf{u}, \mathbf{v}_{r} \rangle \mathbf{v}_{r}
$$

##### Example 
Consider $\mathbb{R}^{3}$ with the Euclidean inner product. Let $W$ be the subspace formed by $\span(\mathbf{v}_{1}, \mathbf{v}_{2})$ where $\mathbf{v}_{1}=(0,1,0)$ and $\mathbf{v}_{2} = (-4,0,3)$. Express $\mathbf{u} = (1,1,1)$ in the form $\mathbf{u} = \mathbf{w}_{1} + \mathbf{w}_{2}$, where $\mathbf{w}_{1} \in W$ and $\mathbf{w}_{2} \in W^{\perp}$.

Step 1:
$$
\begin{align*}
\mathbf{w}_{1} = \proj_{W} \mathbf{u} &= \frac{\langle \mathbf{u}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1} + \frac{\langle \mathbf{u}, \mathbf{v}_{2} \rangle}{\| \mathbf{v}_{2} \|^{2}} \mathbf{v}_{2} \\\\
&= \frac{1}{1}(0,1,0) - \frac{1}{25} (-4,0,3) \\\\
&= \left(\frac{4}{25}, 1, - \frac{3}{25}\right)
\end{align*}
$$
Step 2:
$$
\begin{align*}
\mathbf{w}_{2} = \proj_{W^{\perp}} \mathbf{u} &= \mathbf{u} - \mathbf{w_{1}} \\
&= (1,1,1) - \left(\frac{4}{25}, 1, - \frac{3}{25}\right) \\
&= \left(\frac{21}{25}, 0, \frac{28}{25}\right)
\end{align*}
$$
Step 3:
$$
\mathbf{u} = \left(\frac{4}{25}, 1, - \frac{3}{25}\right) + \left(\frac{21}{25}, 0, \frac{28}{25}\right)
$$

---
### Gram-Schmidt Orthogonalisation Process 

Every non-zero finite-dimensional inner product space $V$ has an orthonormal basis.

Let $W$ be a subspace of $V$ and let $\{ \mathbf{u}_{1}, \ldots, \mathbf{u}_{n} \}$ be a basis of $W$.
Consider the subspaces $W_{r} = \span(\mathbf{u}_{1}, \ldots, \mathbf{u}_{r})$ with $r = 1, \ldots, n$ in $W$.

The Gram-Schmidt process inductively constructs orthogonal bases for the subspaces $W_{i}$, eventually constructing an orthogonal basis for $W_{n} = W$.
Once we have an orthogonal basis for $W$, we can normalise all vectors in it.

###### Step 1
Let $\mathbf{v}_{1} = \mathbf{u}_1$. Clearly, $\{ \mathbf{v}_{1} \}$ is an orthogonal basis for $W_{1} = \span(\mathbf{u}_{1})$.

###### Step $r \in [2,n]$
If $\{ \mathbf{v}_{1}, \ldots, \mathbf{v}_{r-1} \}$ is an orthogonal basis for $W_{r-1} = \span(\mathbf{u}_{1}, \ldots, \mathbf{u}_{r-1})$, find a vector $\mathbf{v}_{r}$ such that $\{ \mathbf{v}_{1}, \ldots, \mathbf{v}_{r-1}, \mathbf{v}_{r} \}$ is an orthogonal basis for $W_{r}$

Apply the projection theorem to $\mathbf{u}_{r} \in W_{r}$ and $W_{r-1}$
$$
\mathbf{u}_{r} = \proj_{W_{r-1}} \mathbf{u}_{r} + \proj_{W_{r-1}^{\perp}} \mathbf{u}_{r}
$$
This gives us 
$$
\small{
\begin{align*}
\mathbf{v}_{r} = \proj_{W_{r-1}^{\perp}} \mathbf{u}_{r} = \mathbf{u}_{r} - \frac{\langle \mathbf{u}_{r}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1} - \frac{\langle \mathbf{u}_{r}, \mathbf{v}_{2} \rangle}{\| \mathbf{v}_{2} \|^{2}} \mathbf{v}_{2} - \ldots - \frac{\langle \mathbf{u}_{r}, \mathbf{v}_{r-1} \rangle}{\| \mathbf{v}_{r-1} \|^{2}} \mathbf{v}_{r-1}
\end{align*}
}
$$
Since $\mathbf{v}_{r} \in W_{r-1}^{\perp}$, the set $\{ \mathbf{v}_{1}, \ldots, \mathbf{v}_{r-1}, \mathbf{v}_{r} \}$ is orthogonal.

##### Gram-Schmidt Summary 
To convert a linearly independent set $S = \{\mathbf{u}_{1}, \ldots, \mathbf{u}_{n}\}$ into an orthogonal basis for $\span(S)$, do the following:
###### Step 1
$$
\mathbf{v}_{1} = \mathbf{u}_{1}
$$
###### Step 2
$$
\mathbf{v}_{2} = \mathbf{u}_{2} - \proj_{W_{1}} \mathbf{u}_{2} = \mathbf{u}_{2} - \frac{\langle \mathbf{u}_{2}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1}
$$
###### Step 3
$$
\mathbf{v}_{3} = \mathbf{u}_{3} - \proj_{W_{2}} \mathbf{u}_{3} = \mathbf{u}_{3} - \frac{\langle \mathbf{u}_{3}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1} - \frac{\langle \mathbf{u}_{3}, \mathbf{v}_{2} \rangle}{\| \mathbf{v}_{2} \|^{2}} \mathbf{v}_{2}
$$
###### Step 4
$$
\small{
\mathbf{v}_{4} = \mathbf{u}_{4} - \proj_{W_{3}} \mathbf{u}_{4} = \mathbf{u}_{4} - \frac{\langle \mathbf{u}_{4}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1} - \frac{\langle \mathbf{u}_{4}, \mathbf{v}_{2} \rangle}{\| \mathbf{v}_{2} \|^{2}} \mathbf{v}_{2} - \frac{\langle \mathbf{u}_{4}, \mathbf{v}_{3} \rangle}{\| \mathbf{v}_{3} \|^{2}} \mathbf{v}_{3}
}
$$
Continue this for $n$ steps.

An optional step is to normalise all vectors $\mathbf{v}_{i}$, if an orthonormal basis is needed.

##### Example in $\mathbf{R}^{3}$
Consider $\mathbb{R}^{3}$ with the Euclidean inner product. Find an orthonormal basis of $W = \span(\mathbf{u}_{1}, \mathbf{u}_{2}, \mathbf{u}_{3})$ where 
$$
\begin{align*}
\mathbf{u}_{1} &= (1,1,1)\\
\mathbf{u}_{2} &= (0,1,1)\\
\mathbf{u}_{3} &= (0,0,1)
\end{align*}
$$

###### Step 1
$$
\mathbf{v}_{1} = \mathbf{u}_{1} = (1,1,1)
$$
###### Step 2
$$
\begin{align*}
\mathbf{v}_{2} = \mathbf{u}_{2} - \proj{W_{1}} \mathbf{u}_{2} &= \mathbf{u}_{2} - \frac{\langle \mathbf{u}_{2}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1} \\
&= (0,0,1) - \frac{2}{3}(1,1,1) \\
&= \left(- \frac{2}{3}, \frac{1}{3}, \frac{1}{3}\right)
\end{align*}
$$
###### Step 3
$$
\begin{align*}
\mathbf{v}_{3} = \mathbf{u}_{3} - \proj_{W_{2}} \mathbf{u}_{3} &= \mathbf{u}_{3} - \frac{\langle \mathbf{u}_{3}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1} - \frac{\langle \mathbf{u}_{3}, \mathbf{v}_{2} \rangle}{\| \mathbf{v}_{2} \|^{2}} \mathbf{v}_{2}\\
&= (0,0,1) - \frac{1}{3}(1,1,1) - \frac{\frac{1}{3}}{\frac{2}{3}} \left(- \frac{2}{3}, \frac{1}{3}, \frac{1}{3}\right)\\
&= \left(0, - \frac{1}{2}, \frac{1}{2}\right)
\end{align*}
$$

###### Solution 
Putting these together, we get an orthogonal basis for $W$
$$
\left\{ \mathbf{v}_{1} = (1,1,1), \mathbf{v}_{2} = \left(- \frac{2}{3}, \frac{1}{3}, \frac{1}{3}\right), \mathbf{v}_{3} = \left(0, - \frac{1}{2}, \frac{1}{2}\right) \right\}$$
And normalising these we get an orthonormal basis for $W$
$$
\left\{ \left(\frac{1}{\sqrt{3}}, \frac{1}{\sqrt{3}}, \frac{1}{\sqrt{3}}\right), \left(- \frac{2}{\sqrt{6}}, \frac{1}{\sqrt{6}}, \frac{1}{\sqrt{6}}\right), \left(0, - \frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}}\right) \right\}
$$

##### Example in $C[-1,1]$
Find an orthogonal basis of $W = \span(\mathbf{u}_{1}, \mathbf{u}_{2}, \mathbf{u}_{3})$ where
$$
\begin{align*}
\mathbf{u}_{1} &= 1\\
\mathbf{u}_{2} &= x\\
\mathbf{u}_{3} &= x^{2}
\end{align*}
$$
###### Step 1
$$
\mathbf{v}_{1} = \mathbf{u}_{1} = 1
$$
###### Step 2
$$
\mathbf{v}_{2} = \mathbf{u}_{2} - \proj_{W_{1}} \mathbf{u}_{2} = \mathbf{u}_{2} - \frac{\langle \mathbf{u}_{2}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1}
$$
We know from [[Inner Product#Inner Product on the Space $C[a,b]$|Inner Products on C]] that 
$$
\langle \mathbf{u}_{2}, \mathbf{v}_{1} \rangle = \int^{1}_{-1} x dx = 0
$$
and 
$$
\| \mathbf{v}_{1} \|^{2} = \langle \mathbf{v}_{1}, \mathbf{v}_{1} \rangle = \int^{1}_{-1} 1 dx = 2
$$
So
$$
\mathbf{v}_{2} = \mathbf{u}_{2} - 0 \mathbf{v}_{1} = x
$$
###### Step 3 
$$
\begin{align*}
\mathbf{v}_{3} = \mathbf{u}_{3} - \proj_{W_{2}} \mathbf{u}_{3} &= \mathbf{u}_{3} - \frac{\langle \mathbf{u}_{3}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1} - \frac{\langle \mathbf{u}_{3}, \mathbf{v}_{2} \rangle}{\| \mathbf{v}_{2} \|^{2}} \mathbf{v}_{2}\\
&= x^{2} - \frac{\frac{2}{3}}{2} \mathbf{v}_{1} - 0 \mathbf{v}_{2} \\\\
&= x^{2} - \frac{1}{3}
\end{align*}
$$
So
$$
\left\{ 1, x, x^{2} - \frac{1}{3} \right\}
$$
is an orthogonal basis for $W$.

---
### Extending an Orthogonal Set to an Orthogonal Basis 

If $V$ is an [[Inner Product#Inner Product Space|Inner Product Space]] then
- Any orthogonal set of vectors in $V$ can be extended to an orthogonal basis 
- Any orthonormal set of vectors in $V$ can be extended to an orthonormal basis.

---
### Additional Information

- [Wikipedia]
- [[Maths for CS Linear Algebra Topic 15 QR Decomposition.pdf]]
- [Maybe Practical Q and As]
