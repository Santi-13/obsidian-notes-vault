#Chairing #Explanation 
Given our ***[[Euler-Lagrange Formulation#Defining Lagrange Equation|Euler-Lagrange Formulation]]***:
$$
B(q)\ddot{q} + C(\dot{q},q)\dot{q} + G(q) = \Omega\tau+ \phi_{diss}(\dot{q},q,t) + \langle \lambda(t), f(q) \rangle
$$
We can propose our **state variables**:
$$ \begin{cases}
q_{a} = q \\
 q_{b} = \dot{q} 
\end{cases} $$
Then, the *dynamics* of the proposed **state variables** are:
$$ \dot{q}_{a}=\dot{q}=q_{b} $$
$$ 
\dot{q}_{b} = \ddot{q} = B^{-1}(q_{a}) [ \Omega\tau +\phi_{diss}(q_{b},q_{a},t) + \langle \lambda(t),f(q_{a}) \rangle- C(q_{b},q_{a})q_{b} - G(q_{a}) ] $$ $$ =f(q_{a},q_{b}) + g(q_{a})(\Omega\tau +\langle \lambda(t), f(q_{a}) \rangle) $$
$\text{Where:}$
$g(q_{a})=B^{-1}(q_{a})$ 
$f(q_{a},q_{b})=-B^{-1}(q_{a})(C(q_{b},q_{a})q_{b} + G(q_{a}))$

Now, in order to control the system using this representation, we need to propose a ***linear controller*** that *mimics* this **system dynamics**. Here we analyze two cases.
#### Proposal 1. Unperturbed System
Similar to the previously proposed system, our dynamics are expressed as:
$$
\begin{cases}
\dot{q}_{a}=q_{b} \\
\dot{q}_{b}= f(q_{a},q_{b}) + g(q_{a})(\Omega\tau +\langle \lambda(t), f(q_{a}) \rangle)
\end{cases}
$$
Now, we need to propose a controller so we can control our dynamics disregarding the **system**, in other words, for a ***PD controller*** we need:
$$
\dot{q}_{b} = f(q_{a},q_{b}) + g(q_{a})(\Omega\tau +\langle \lambda(t), f(q_{a}) \rangle) = -K_{P}q_{a} - K_{D}q_{b}
$$
To do this, we may simply propose a ***PD controller*** for the **torque** $\tau$ that takes into account the dynamics.
$$
\tau=\Omega^{-1}
$$
#### Proposal 2. Perturbed System