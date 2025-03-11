#Chairing #Explanation 
Given our ***[[Euler-Lagrange Formulation#Defining Lagrange Equation|Euler-Lagrange Formulation]]***:
$$
B(q)\ddot{q} + C(\dot{q},q)\dot{q} + G(q) = \Omega\tau+ \phi_{diss}(\dot{q},q,t) + \langle \lambda(t), f(q) \rangle
$$
We can propose our **state variables**:
$$ q_{a} = q \newline 
\\

$$
$$ q_{b} = \dot{q} $$
Then, the *dynamics* of the proposed **state variables** are:
$$ \dot{q}_{a}=\dot{q}=q_{b} $$
$$ 
\dot{q}_{b} = \ddot{q} = B^{-1}(q_{a}) [ \Omega\tau +\phi_{diss}(q_{b},q_{a},t) + \langle \lambda(t),f(q_{a}) \rangle- C(q_{b},q_{a})q_{b} - G(q_{a}) ] $$ $$ =f(q_{a},q_{b}) + g(q_{a})(\Omega\tau +\langle \lambda(t), f(q_{a}) \rangle) $$
$\text{Where:}$
$g(q_{a})=B^{-1}(q_{a})$ 
$f(q_{a},q_{b})=-B^{-1}(q_{a})(C(q_{b},q_{a})q_{b} + G(q_{a}))$

