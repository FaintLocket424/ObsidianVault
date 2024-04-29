---
tags:
  - incomplete
  - degree/singlemathsa/trigonometry
---
![[Trigonometry MOC 🌍]]

### $\cos (n \pi)$
$$
\cos(n \pi) = (-1)^{n} \quad \forall n \in \mathbb{N}
$$
### $\sin (n \pi)$
$$
\sin (n \pi) = 0 \quad \forall n \in \mathbb{N}, n \ne 0
$$
### $\int^{\pi}_{-\pi} \sin(nx)$
$$
\int^{\pi}_{-\pi} \sin(nx) = 0
$$
Proof:
$$
\begin{align*}
\int^{\pi}_{-\pi} \sin(nx) &= \left[ - \frac{1}{n} \cos(nx) \right]^{\pi}_{-\pi}\\
\\
&= \left(- \frac{1}{n} \cos(n \pi)\right) - \left(- \frac{1}{n} \cos(-n \pi)\right)\\
\\
&= - \frac{1}{\pi} \cos(n \pi) + \frac{1}{\pi} \cos(-n \pi)\\
\\
&= 0
\end{align*}
$$
### $\int^{\pi}_{-\pi} \cos(nx)$
$$
\int^{\pi}_{-\pi} \cos(nx) = 0
$$
Proof:
$$
\begin{align*}
\int^{\pi}_{- \pi} \cos(nx) &= \left[ \frac{1}{n} \sin(nx) \right]^{\pi}_{-\pi}\\
\\
&= \left(\frac{1}{n} \sin(n \pi)\right) - \left(\frac{1}{n} \sin(-n \pi)\right)\\
\\
&= \frac{1}{n} \sin(n \pi) + \frac{1}{n} \sin(n \pi)\\
\\
&= \frac{2}{n} \sin(n \pi)\\
\\
&= 0
\end{align*}
$$
Note: See [[#$ sin (n pi)$|above]] for explanation of last step.