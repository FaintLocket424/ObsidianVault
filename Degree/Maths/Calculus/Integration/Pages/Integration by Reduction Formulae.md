---
tags:
  - degree/singlemathsa/integration
  - degree/mathsforcs/calculus/integration
---
![[Integration MOC 🌍]]

$$
\begin{align*}
I_{m} &= \int \cos^{m} (\theta) d \theta\\
\\
&= \int \cos^{m-1} (\theta) \frac{d(\sin \theta)}{d \theta} d \theta
\end{align*}
$$
We can then use [[Integration by Parts]] with $u= \cos^{m-1} (\theta)$ and $v' = \frac{d(\sin \theta)}{d \theta}$.
$$
I_{m} = \cos^{m-1} \theta \sin \theta - \int \sin (\theta) (m-1) \cos^{m-2} \theta (-\sin \theta) d \theta
$$
Now we can collect the $\sin \theta$, turn it into $(1 - \cos^{2} \theta)$ and expand the brackets.
$$
\begin{align*}
I_{m} &= \cos^{m-1} \theta \sin \theta + \int \sin^{2} (\theta) (m-1) \cos^{m-2} \theta d \theta\\
\\
&= \cos^{m-1} \theta \sin \theta + \int (1 - \cos^{2} \theta) (m-1) \cos^{m-2} \theta d \theta\\
\\
&= \cos^{m-1} \theta \sin \theta + \int (m-1) \cos^{m-2} (\theta) - (m-1) \cos^{m} \theta d \theta\\
\\
&= \cos^{m-1} \theta \sin \theta + (m-1) \int \cos^{m-2} (\theta) d \theta - (m-1) \int \cos^{m} \theta d \theta\\
\\
&= \cos^{m-1} \theta \sin \theta + (m-1)I_{m-2} - (m-1)I_{m}
\end{align*}
$$
And with some more rearranging we get
$$
\begin{align*}
I_{m} &= \cos^{m-1} \theta \sin \theta + (m-1)I_{m-2} - (m-1)I_{m}\\
\\
I_{m} + (m-1) I_{m} &= \cos^{m-1} \theta \sin \theta + (m-1)I_{m-2}\\
\\
m I_{m} &= \cos^{m-1} \theta \sin \theta + (m-1)I_{m-2}\\
\\
I_{m} &= \frac{1}{m} \cos^{m-1} \theta \sin \theta + \frac{m-1}{m} I_{m-2}
\end{align*}
$$
This gives us the formula 
$$
I_{m} = \frac{1}{m} \cos^{m-1} \theta \sin \theta + \frac{m-1}{m} I_{m-2}
$$
Then an example would be finding $I_{7}$
$$
\begin{align*}
I_{7} &= \frac{1}{7} \cos^{6} \theta \sin \theta + \frac{6}{7} I_{5}\\
\\
&= \frac{1}{7} \cos^{6} \theta \sin \theta + \frac{6}{35} \cos^{4} \theta \sin \theta + \frac{24}{35} I_{3}\\
\\
&= \frac{1}{7} \cos^{6} \theta \sin \theta + \frac{6}{35} \cos^{4} \theta \sin \theta + \frac{8}{35} \cos^{2} \theta \sin \theta + \frac{16}{35} I_{1}\\
\\
&= \frac{1}{7} \cos^{6} \theta \sin \theta + \frac{6}{35} \cos^{4} \theta \sin \theta + \frac{8}{35} \cos^{2} \theta \sin \theta + \frac{16}{35} \sin \theta
\end{align*}
$$
Daym

---
### Additional Information

- [Wikipedia]
- [[Maths for CS Calculus Topic 13 Integration Part 2.pdf]]
- [Maybe Practical Q and As]
