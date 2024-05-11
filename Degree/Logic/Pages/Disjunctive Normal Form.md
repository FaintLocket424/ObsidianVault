---
tags:
  - degree/compthink/logic
aliases:
  - SOP
  - Sum of Products
  - Minterms
---
![[Logic MOC 🌍]]
### Calculating Minterms

![[IMAGE Truth Table 2.png]]

For a given truth table, we can write the function as a sum of products, where the minterms are ORed together.

Minterms are where the output of the function is 1.

E.g. for line 1, the minterm would be $\overline{X}\land\overline{Y}\land\overline{Z}$ since that expression evaluates to 1.

So the SOP of this table is:

$$\begin{aligned}
f(X,Y,Z)=(\overline{X}\land\overline{Y}\land\overline{Z})\lor(\overline{X}\land Y\land\ Z)\lor(X\land\overline{Y}\land\ Z)\lor (X\land Y\land\overline{Z})
\end{aligned}$$

Now this almost certainly won't be the simplest form but it will at least be true.

This is also known as the disjunctive normal form.