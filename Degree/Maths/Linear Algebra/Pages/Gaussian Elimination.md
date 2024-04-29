---
tags:
  - degree/mathsforcs/linearalgebra
aliases:
---
![[Linear Algebra MOC 🌍]]

### Elementary Row Operations (EROs)

The augmented matrix of the linear system is $(A|\boldsymbol{b})$
$$
(A|\boldsymbol{b}) =
\begin{bmatrix}
\begin{array}{cccc|c}
a_{11} & a_{12} & \cdots & a_{1n} & b_{1} \\ 
a_{21} & a_{22} & \cdots & a_{2n} & b_{2} \\ 
\vdots & \vdots & \ddots & \vdots & \vdots \\ 
a_{m1} & a_{m2} & \cdots & a_{mn} & b_{m}
\end{array}
\end{bmatrix}
$$
The goal is now to do row operations on the matrix that don't alter the solution set but produce simpler systems.

The EROs are:
- Multiply an row by a non-zero constant.
- Swap two rows.
- Add a constant times one row, to another row.

---
### Row Echelon Form (ref)

If we transform an augmented matrix of the variables $x$, $y$ and $z$ into the form
$$
\begin{bmatrix}
\begin{array}{ccc|c}
1 & 0 & 0 & 1 \\ 
0 & 1 & 0 & 2 \\ 
0 & 0 & 1 & 3
\end{array}
\end{bmatrix}
$$
Then we'd know the solution is $x=1$, $y=2$ and $z=3$.
This augmented matrix is in REF.

A matrix in row echelon form has these properties:
- If a row is not all 0s then the first number is 1.
- The rows that are all 0s are together at the bottom.
- A row's leading 1 cannot be inline or before the ones above it.

Examples of ref matrices are:
$$
\begin{align*}
&\begin{bmatrix}
\begin{array}{ccc|c}
1 & 0 & 0 & 1 \\ 
0 & 1 & 0 & 2 \\ 
0 & 0 & 1 & 3
\end{array}
\end{bmatrix}\\
\\
&\begin{bmatrix}
\begin{array}{ccc|c}
1 & 0 & 0 & 2 \\ 
0 & 1 & 0 & 5 \\ 
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0
\end{array}
\end{bmatrix}\\
\\
&\begin{bmatrix}
\begin{array}{ccc|c}
1 & -1 & 0 & 2 \\ 
0 & 0 & 1 & 5 \\ 
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{array}
\end{bmatrix}
\end{align*}
$$

##### Reduced Row Echelon Form (rref)

rref has one additional property:
- Each column that contains a leading 1 has 0s everywhere else.

This matrix would not be in rref
$$
\begin{bmatrix}
\begin{array}{ccc|c}
1 & 0 & 0 & 2 \\ 
0 & 1 & 0 & 5 \\ 
0 & 0 & 0 & 1
\end{array}
\end{bmatrix}
$$
because the bottom row has a leading one but it's column is not zero for the rest.

##### Extracting Solutions

There are 3 possibilities when you have a (r)ref matrix.

###### There's a leading one in the last column
$$
\begin{bmatrix}
\begin{array}{ccc|c}
1 & 0 & 0 & 2 \\ 
0 & 1 & 0 & 5 \\ 
0 & 0 & 0 & 1 \\ 
0 & 0 & 0 & 0
\end{array}
\end{bmatrix}
$$
This implies $0=1$, which means this system have no solutions.

###### Number of leading 1s is equal to number of variables
$$
\begin{bmatrix}
\begin{array}{ccc|c}
1 & 0 & 0 & 2 \\ 
0 & 1 & 0 & 5 \\ 
0 & 0 & 1 & 1 \\ 
0 & 0 & 0 & 0
\end{array}
\end{bmatrix}
$$
This means the system has one unique solution, $x_{1}=2$, $x_{2}=5$ and $x_{3}=1$.

###### Number of leading 1s is less than number of variables
$$
\begin{bmatrix}
\begin{array}{ccc|c}
1 & -1 & 0 & 2 \\ 
0 & 0 & 1 & 5 \\ 
0 & 0 & 0 & 0 \\ 
0 & 0 & 0 & 0
\end{array}
\end{bmatrix}
$$
This means the system has infinitely many solutions. The variables corresponding to the leading 1s are the leading variables, $x_{1}$ and $x_{3}$ here.
The others are the free variables.

The solution is to express the leading variables in terms of the free variables.
$$
\begin{align*}
x_{1} &= x_{2}+2\\
x_{3} &= 5
\end{align*}
$$
where $x_{2}$ is an arbitrary number.

---
### Gaussian Elimination Method

##### Step 1:
$$
\begin{bmatrix}
0 & 0 & -2 & 0 & 7 & 12 \\ 
2 & 4 & -10 & 6 & 12 & 28 \\ 
2 & 4 & -5 & 6 & -5 & -1
\end{bmatrix}
$$
First, locate the pivot column which is the first column with a non-zero element.

##### Step 2:
$$
\begin{bmatrix}
2 & 4 & -10 & 6 & 12 & 28 \\ 
0 & 0 & -2 & 0 & 7 & 12 \\ 
2 & 4 & -5 & 6 & -5 & -1
\end{bmatrix}
$$
Choose a pivot row, the first one with a non-zero, and move the row to the top if it's not already.

##### Step 3:
$$
\begin{bmatrix}
1 & 2 & -5 & 3 & 6 & 14 \\ 
0 & 0 & -2 & 0 & 7 & 12 \\ 
2 & 4 & -5 & 6 & -5 & -1
\end{bmatrix}
$$
If the first in the pivot is $a$, then multiply the pivot row by $\frac{1}{a}$, which creates a leading 1.

##### Step 4:
$$
\begin{bmatrix}
1 & 2 & -5 & 3 & 6 & 14 \\ 
0 & 0 & -2 & 0 & 7 & 12 \\ 
0 & 0 & 5 & 0 & -17 & -29
\end{bmatrix}
$$
Next, add multiples of the top row to the lower rows to get zeros into the column under the leading 1.

##### Step 5:
$$
\begin{align*}
\begin{bmatrix}
1 & 2 & -5 & 3 & 6 & 14 \\ 
0 & 0 & 1 & 0 & -\frac{7}{2} & -6 \\ 
0 & 0 & 0 & 0 & \frac{1}{2} & 1
\end{bmatrix}\\
\\
\begin{bmatrix}
1 & 2 & -5 & 3 & 6 & 14 \\ 
0 & 0 & 1 & 0 & -\frac{7}{2} & -6 \\ 
0 & 0 & 0 & 0 & 1 & 2
\end{bmatrix}
\end{align*}
$$
Next, repeat [[#Step 3]] and [[#Step 4]], dividing and adding multiples of rows to get leading ones in each row. Now we have a matrix in row echelon form. There is an extra step to get it into rref.

---
### Gauss-Jordan Elimination
$$
\begin{align*}
\begin{bmatrix}
1 & 2 & -5 & 3 & 6 & 14 \\ 
0 & 0 & 1 & 0 & -\frac{7}{2} + 1\left(\frac{7}{2}\right) & -6 + 2 \left(\frac{7}{2}\right) \\ 
0 & 0 & 0 & 0 & 1 & 2
\end{bmatrix}&=
\begin{bmatrix}
1 & 2 & -5 & 3 & 6 & 14 \\ 
0 & 0 & 1 & 0 & 0 & 1 \\ 
0 & 0 & 0 & 0 & 1 & 2
\end{bmatrix}\\
\\
\begin{bmatrix}
1 & 2 & -5 & 3 & 6 + (-6)(1) & 14 + (-6)(2) \\ 
0 & 0 & 1 & 0 & 0 & 1 \\ 
0 & 0 & 0 & 0 & 1 & 2
\end{bmatrix}&=
\begin{bmatrix}
1 & 2 & -5 & 3 & 0 & 2 \\ 
0 & 0 & 1 & 0 & 0 & 1 \\ 
0 & 0 & 0 & 0 & 1 & 2
\end{bmatrix}\\
\\
\begin{bmatrix}
1 & 2 & -5 + (5)(1) & 3 & 0 & 2 + (5)(1) \\ 
0 & 0 & 1 & 0 & 0 & 1 \\ 
0 & 0 & 0 & 0 & 1 & 2
\end{bmatrix} &= 
\begin{bmatrix}
1 & 2 & 0 & 3 & 0 & 7 \\ 
0 & 0 & 1 & 0 & 0 & 1 \\ 
0 & 0 & 0 & 0 & 1 & 2
\end{bmatrix}
\end{align*}
$$
Starting at the bottom non-zero row, add multiples of the rows to create 0s above the leading ones. The matrix is now in the reduced row echelon form.

---
### Finding Matrix Inverses with Gaussian Elimination

To find the inverse of of the matrix
$$
A=\begin{bmatrix}
1 & 2 \\ 3 & 4
\end{bmatrix}
$$
We can augment it with the identity matrix
$$
\begin{bmatrix}
1 & 2 & 1 & 0\\
3 & 4 & 0 & 1
\end{bmatrix}
$$
And then we can do [[#Gaussian Elimination]] on this augmented matrix.
$$
\begin{align*}
&\begin{bmatrix}
1 & 2 & 1 & 0 \\ 
0 & -2 & -3 & 1
\end{bmatrix}\\
\\
&\begin{bmatrix}
1 & 2 & 1 & 0 \\ 
0 & 1 & \frac{3}{2} & -\frac{1}{2}
\end{bmatrix}\\
\\
&\begin{bmatrix}
1 & 0 & -2 & 1 \\ 
0 & 1 & \frac{3}{2} & -\frac{1}{2}
\end{bmatrix}
\end{align*}
$$
So, the inverse of $A$ is
$$
A^{-1} = \begin{bmatrix}
-2 & 1 \\ \frac{3}{2} & - \frac{1}{2}
\end{bmatrix}
$$

---
### Additional Information

- [Gaussian Elimination on Wikipedia](https://en.wikipedia.org/wiki/Gaussian_elimination#:~:text=In%20mathematics%2C%20Gaussian%20elimination%2C%20also,the%20corresponding%20matrix%20of%20coefficients.)
- [[Maths for CS Linear Algebra Topic 5 Linear Equations and Gaussian Elimination.pdf|Steven Bradley's Notes on Gaussian Elimination]]
