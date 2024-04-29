---
tags:
  - degree/compthink/logic
aliases:
  - Maxterms
  - POS
  - Product of Sums
  - CNF
---
![[Logic MOC 🌍]]

### Calculating Maxterms

![[IMAGE Truth Table 2.png]]

For a given truth table, we can write the function as a product of sums, where the maxterms are ANDed together.

Maxterms are where the output of the function is 0.

E.g. for line 2, the maxterm would be $X\lor Y\lor\overline{Z}$ since that expression evaluates to 0.

So the POS of this table is:
$$\begin{aligned}
f(X,Y,Z)=
(X\lor Y\lor\overline{Z})\land
(X\lor \overline{Y}\lor\ Z)\land
(\overline{X}\lor Y\lor\ Z)\land
(\overline{X}\lor \overline{Y}\lor\overline{Z})
\end{aligned}$$

Now this almost certainly won't be the simplest form but it will at least be true.