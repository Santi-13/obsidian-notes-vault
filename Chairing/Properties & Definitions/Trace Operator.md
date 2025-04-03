#Chairing #Definition 
The ***trace operator*** says that, for any matrix $A \in \mathrm{R}^{n \times n}$, its trace $\text{tr}(A)$ is the **sum** of its **diagonal elements**:
$$
\text{tr}\{ A \} = \sum_{i=1}^n A_{ii}
$$
It has the following ***properties***:

- **Linearity:** $\text{tr}\{ cA + B \} = c \text{ }\text{tr}\{ A \} + \text{tr}\{ B \}$.
- **Invariance under permutations:** $\text{tr}\{ ABC \} = \text{tr}(BCA) = \text{tr}(CAB)$.
- **Trace of transpose:** $\text{tr}(A) = \text{tr}(A^T)$.
- **Trace of a scalar:** If $a \in \mathrm{R}, \text{tr}(a)=a$

For example, for:
$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4 
\end{bmatrix}
$$
$$
\text{tr}(A) = 1 + 4 = 5
$$
