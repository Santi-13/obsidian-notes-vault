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
\tau=\Omega^{-1}[g^{-1}(q_{a})( - K_{P}q_{a} - K_{D}q_{b} - f(q_{a},q_{b}) )] - \langle \lambda(t),f(q_{a}) \rangle 
$$
When substituting into the dynamics we get:
$$
\dot{q}_{b} = f(q_{a},q_{b}) + g(q_{a})(\cancel{ \Omega(\Omega^{-1} }[g^{-1}(q_{a})( - K_{P}q_{a} - K_{D}q_{b} - f(q_{a},q_{b}) )] \cancel{ - \langle \lambda(t),f(q_{a}) \rangle ) +\langle \lambda(t), f(q_{a}) \rangle })
$$
$$
\dot{q}_{b} = f(q_{a},q_{b}) + \cancel{ g(q_{a})[g^{-1}(q_{a}) }( - K_{P}q_{a} - K_{D}q_{b} - f(q_{a},q_{b}) )]
$$
$$
\dot{q}_{b} = \cancel{ f(q_{a},q_{b}) - f(q_{a},q_{b}) } - K_{P}q_{a} - K_{D}q_{b} 
$$
$$
\dot{q}_{b} = -K_{P}q_{a} - K_{D}q_{b}
$$
We basically made a ***controller*** for the **system's acceleration** by proposing one for the **torque**. Resulting in our new dynamics:
$$
\begin{cases}
\dot{q}_{a}=q_{b} \\
\dot{q}_{b}=-K_{P}q_{a} - K_{D}q_{b} 
\end{cases}
$$
In **vector form**:
$$
\frac{d}{dt} \mathrm{q}=\frac{d}{dt} \begin{bmatrix} q_{a}  \\ q_{b} \end{bmatrix} =
\begin{bmatrix}
q_{b} \\
-K_{P}q_{a} - K_{D}q_{b}
\end{bmatrix}
$$
$$
= \begin{bmatrix}
0_{n\times n} & I_{n\times n} \\
-K_{P} & -K_{D}
\end{bmatrix} \begin{bmatrix}
q_{a} \\
q_{b}
\end{bmatrix}
$$
$$
\frac{d}{dt} \mathrm{q} = A\mathrm{q} 
$$
From this, is obvious to note that $\mathrm{q}$ is a $12\times1$ vector, and both $K_P$ and $K_D$ are $6\times6$ matrices. 
#### Proposal 2. Perturbed System
Consider the case where:
$$
\begin{cases}
\dot{q}_{a}=q_{b} \\
\dot{q}_{b}= f(q_{a},q_{b}) + g(q_{a})(\Omega\tau +\langle \lambda(t), f(q_{a}) \rangle) + \psi(q_{a},q_{b},t)
\end{cases}
$$
$\text{Where:}$
$\psi(q_{a},q_{b},.):\text{Non-modelled sections of the robot.}$
$\psi(.,.,t): \text{Effect of all external perturbations.}$

Where the perturbations $\psi$ are constrained to a set $\Psi$ defined by:
$$
\Psi=\{ \psi:Q_{a} \times TQ_{a} \times \mathrm{R}^+ \to \mathrm{R}^n | \text{ } \lvert\lvert \psi \rvert\rvert^2 \leq \psi_{0} + \psi_{1}\lvert\lvert q_{a} \rvert\rvert^2 + \psi_{2} \lvert\lvert q_{b} \rvert\rvert^2\}
$$
$\text{Where:}$
$Q_{a}\subset \mathrm{R}^n: \text{Configuration space (positions of } q_{a} \text{)}$
$TQ_{a}: \text{Tangent bundle of }Q_{a} \text{, representing positions and velocities  } (q_{a}, q_{b})$
$\psi_{0},\psi_{1},\psi_{2} \geq 0: \text{Bounds on perturbation magnitude where:}$
$\psi_{0}: \text{Constant Disturbances (e.g. sensor noise)}$
$\psi_{1}: \text{Uncnertainties that scale with position.}$
$\psi_{2}: \text{Velocity-dependent disturbances}$

Here, $TQ_{a}$ represents all posible states $(q_{a}, q_{b})$ where $q_{b}=\dot{q}_{a}$ are velocities. It essentially **formalizes** the **state-space** of the *system* as pairs of *positions* and *velocities*.

We follow the same procedure to propose a **control input** $\tau$ to cancel *nonlinear* terms and enforce *linear dynamics*:
$$
\tau=\Omega^{-1}[g^{-1}(q_{a})( - K_{P}q_{a} - K_{D}q_{b} - f(q_{a},q_{b}) )] - \langle \lambda(t),f(q_{a}) \rangle 
$$
So we end up with:
$$
\dot{q}_{b} = -K_{P}q_{a} - K_{D}q_{b}+\psi(q_{a},q_{b},t)
$$
$$
\frac{d}{dt} q = \underbrace{ \begin{bmatrix}
0_{n\times n} & I_{n\times n} \\
-K_{P} & -K_{D}
\end{bmatrix} }_{ A } \begin{bmatrix}
q_{a} \\
q_{b}
\end{bmatrix} + \underbrace{ \begin{bmatrix} 0 \\ I \end{bmatrix} }_{ B } \psi
$$
Where we said our perturbations $\psi$ are bounded by:
$$
\lvert\lvert \psi \rvert\rvert^2 \leq \psi_{0} + \psi_{1}\lvert\lvert q_{a} \rvert\rvert^2 + \psi_{2} \lvert\lvert q_{b} \rvert\rvert^2
$$
