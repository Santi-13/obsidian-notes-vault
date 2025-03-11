#Chairing #Definition 
#### Basic Matrix Calculus Rule for Quadratic Forms

For a scalar function $f(\mathrm{x}) = \mathrm{x}^TA\mathrm{x}$, its *derivative* with respect to $\mathrm{x}$ is:
$$
\frac{ \partial f }{ \partial \mathrm{x} } = (A+A^T)\mathrm{x} 
$$
To prove this, we may expand $f(\mathrm{x})$ in component form as defined in the ***[[Quadratic Norm Representation]]***:
$$
f(\mathrm{x}) = \sum^n_{i=1} \sum^n_{j=1} A_{ij} \mathrm{x}_{i} \mathrm{x}_{j}
$$
We make the partial derivative $\frac{ \partial f }{ \partial \mathrm{x}_{k} }$, where $\mathrm{x}_{k}$ represents the $k\text{-th}$ element of $\mathrm{x}$:
$$
\frac{\partial f(\mathrm{x})}{\partial \mathrm{x}_{k}} = \sum^n_{i=1} \sum^n_{j=1} A_{ij} \frac{\partial}{\partial \mathrm{x}_{k}} ( \mathrm{x}_{i} \mathrm{x}_{j} ) 
$$
Using the *product rule*:
$$
\frac{\partial f(\mathrm{x})}{\partial \mathrm{x}_{k}} = \sum^n_{i=1} \sum^n_{j=1} A_{ij} \left( \frac{\partial \mathrm{x}_{i}}{\partial \mathrm{x}_{k}} \mathrm{x}_{j} + \mathrm{x}_{i} \frac{\partial \mathrm{x}_{j}}{\partial \mathrm{x}_{k}} \right)
$$
We notice that each partial derivative equals $1$ and is non-zero when the $k\text{-th}$ element of $\mathrm{x}$ matches $i$ or $j$ (**Kronecked Delta**), so we eliminate the rest of the sum as it only matters when it matches $k$:
$$
\frac{\partial f(\mathrm{x})}{\partial \mathrm{x}_{k}} =  \sum_{j=1}^n A_{kj} \mathrm{x}_{j} + \sum_{i=1}^n A_{ik} \mathrm{x}_{i}  
$$
As the sum of both $j$ and $i$ go from $1$ to $n$, they are essentially the same, thus getting the form:
$$
\frac{\partial f(\mathrm{x})}{\partial \mathrm{x}_{k}} = (A + A_{T}) \mathrm{x}
$$

