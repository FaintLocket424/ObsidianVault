---
tags:
  - incomplete
  - degree/mathsforcs/calculus/integration
---
![[Integration MOC 🌍]]
### Question 
Let $f:[a,b] \to \mathbb{R}$ be a continuous function with $f(x) \ge 0$ for all $x \in [a,b]$. Show that $\int^{b}_{a} f(x) dx = 0$ iff $f(x)=0$ for all $x \in [a,b]$.
### Answer 
Firstly, let's pick apart the question. We know that:
- $f$ is a continuous function, so there are no sudden jumps in it's value. This will be important later.
- $f$ is always positive, so there's no cancelling areas.

It's clear to say that the reverse of the question is true, that if $f(x)=0$, then $\int^{b}_{a}f(x)dx = 0$. We need to show that if the integral is zero, the function must be zero.

Let's start by assuming that our integral does equal 0
$$
\int^{b}_{a} f(x) dx = 0
$$
And let's assume, for the sake of contradiction, that there's a value $x_{0}$ where $f(x_{0}) > 0$.

Now think back to the continuity we established $f$ has. If $f$ is positive at $x_{0}$, there must be a (however small) region around $x_{0}$ which is also positive.

![[Pasted image 20240510195207.png]]

And we can select $x_{0}$ to be any value within $a < x_{0} < b$.

Now let's consider $\epsilon = \frac{f(x_{0})}{2}$. Since $f(x_{0})$ is positive, so will $\epsilon$.

Using the continuity of $f$ again, we know that there is a $\delta > 0$ such that $a < x_{0} - \delta < x_{0} + \delta < b$ and that in this region $[x_{0} - \delta, x_{0} + \delta]$, 

$$
|f(x) - f(x_{0})| < \epsilon
$$

And following on from that, in this region,

$$
f(x) > \frac{f(x_{0})}{2}
$$

Using this information, we have

$$
\int^{b}_{a} f(x) dx = \int^{x_{0} - \delta}_{a} f(x) dx + \int^{x_{0} + \delta}_{x_{0} - \delta} f(x) dx + \int^{b}_{x_{0} + \delta} f(x) dx
$$

So,

$$
\int^{b}_{a} f(x) dx \ge \int^{x_{0} + \delta}_{x_{0} - \delta} f(x) dx
$$

We know that in the region $[x_{0} - \delta, x_{0} + \delta]$, $f(x) > \epsilon$.
So there must be an rectangular area beneath $\epsilon$ which is included in the area.
![[Pasted image 20240510202216.png]]

So our area must be at least this

$$
\begin{aligned}
\int^{b}_{a} f(x) &\ge \int^{x_{0} + \delta}_{x_{0} - \delta}f(x) dx \ge 2\delta \epsilon\\
\\
\int^{b}_{a} f(x) &\ge 2\delta \epsilon
\end{aligned}
$$

And since $\delta > 0$ and $\epsilon > 0$,

$$
\int^{b}_{a} f(x) \ge 0
$$

Which is a violation of our original assumption.

Therefore, $f(x) = 0$ for all $x \in [a,b]$.


---
### Additional Information
- [[COMP1021_MCS_Questions_Solutions_2324.pdf
