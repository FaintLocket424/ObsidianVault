---
tags:
  - degree/glossary
  - degree/compsys/databases
---
![[Pasted image 20240123160636.png]]
### Reflexivity
If $B\subseteq A$, then $A \rightarrow B$
(*id, prename, surname*) $\rightarrow$ (*prename, surname*)

### Augmentation
If $A \rightarrow B$ then $(A,C) \rightarrow (B,C)$
(*id, prename*) $\rightarrow$ (*college, prename*)

### Transitivity
If $A \rightarrow B$ and $B\rightarrow C$ then $A \rightarrow C$
*id* $\rightarrow$ *college* and *college* $\rightarrow$ *collegeAddress* $\therefore$ *id* $\rightarrow$ *collegeAddress*

### Decomposition
If $A\rightarrow (B,C)$ then $A\rightarrow B$ and $A\rightarrow C$

### Union
If $A\rightarrow B$ and $A\rightarrow C$ then $A\rightarrow (B,C)$

### Composition
If $A\rightarrow B$ and $C\rightarrow D$ then $(A,C)\rightarrow (B,D)$
