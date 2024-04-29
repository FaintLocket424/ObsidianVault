---
tags:
  - degree/mathsforcs/proof
  - incomplete
---
![[Proof by Contradiction MOC 🌍]]

### General Formula

1. We have theorem $p$,
2. We assume *not* $p$
3. Show that *not* $p$ implies $q$ which is known to be false.
4. If *not* $p$ implies $q$, then *not* $p$ cannot hold.
5. Therefore $p$ must be true.

### Example: $\sqrt{2}\notin\mathbb{Q}$

Assume $\sqrt{2}\in\mathbb{Q}$.

This implies $\sqrt{2}=\frac{m}{n}$, where $\frac{m}{n}$ is a simplified fraction.

So $\frac{m^{2}}{n^{2}}=2$, so $m^{2}=2n^{2}$ and $m$ therefore must be even.

Let $m=2k$. Then $4k^{2}=2n^{2}$, and $2k^{2}=n^{2}$, so $n$ is also even.

Hence $\frac{m}{n}$ is not a simplified fraction, which contradicts the assumption.

Therefore the assumption must be wrong, so $\sqrt{2}\notin\mathbb{Q}$.