---
tags:
  - degree/ads/asymptoticnotation
---
![[Asymptotic Notation MOC 🌍]]

### Big Omega

Big Omega notation is how we express the lower bound for an algorithm's time/space complexity.

>*"I can pay you at least one pound" - Big-Omega*

To help with this we have Big Omega which tells us the lower bound on a function.
$$\begin{aligned}
|f(x)|&\ge C\times |g(x)| \\\\
x&\ge k
\end{aligned}$$
If Big-O is a function that is always above the given one, then Big-Omega is a function that is always below the given one.

This also implies that if $f(x)$ is $\Omega (g(x))$ then $g(x)$ is $O(f(x))$.

