#Explanation #Chairing 

***Barrier Lyapunov Functions*** (**BLF**) enforce **state constraints** by designing the ***Lyapunov Function*** $V_{B}$ to grow unbounded as $x$ approaches the constraint boundary. For our system, we define our **constraint** as:
$$
\mathrm{x} = \begin{bmatrix}
q \\
\dot{q}
\end{bmatrix}
$$

^6c6b52

$$
\lvert\lvert \mathrm{x} \rvert\rvert^2_{P} < x^+ 
$$
The constant $x^+$ is defined as the boundary of the state, in the case of two **cobots** working on the same **workspace**, this constant is constantly updated by the state of the other robot. This **dynamic constraint** is defined:
$$
\lvert\lvert \mathrm{x} \rvert\rvert^2_{P} < x^+ (\mathrm{x}_{j}), \text{ }\text{ }\text{ } i,j \in \{ 1,2 \}, \text{ }\text{ }\text{ } i \neq j
$$
Where $x^+(\mathrm{x}_{j})$ is updated based on the other robot's state to avoid collisions.
#### Barrier Lyapunov Function
From our ***[[Euler-Lagrange Formulation]]***, we can get our *joints' acceleration* as:
$$
\ddot{q}= B^{-1}(q) (\tau-C(\dot{q},q) \dot{q} - G(q)) + B^{-1}\tau + \eta
$$
We can propose a **PD controller** that compensates for the dynamics such as:
$$
u= BK_{p}q + BK_{D} \dot{q} + C(q,\dot{q})\dot{q} + G(q) 
$$
After substituting, we get:
$$
\ddot{q} = K_{p}q + K_{D}\dot{q} + \eta
$$
Where $\eta$ represents **unmodeled dynamics/external perturbations**. In ***[[#^6c6b52|state-space form]]***:
$$
\dot{\mathrm{x}} = \begin{bmatrix}
0 & I \\
K_{p}  & K_{D}
\end{bmatrix} \mathrm{x} + \begin{bmatrix}
0 \\
I
\end{bmatrix} \eta
$$
$$
= A\mathrm{x} + B\eta
$$
#### Structure of BLF
The proposed *Barrier Lyapunov Function* is:
$$
V_{B} = \ln\left( \frac{ x^+ }{ x^+ - \lvert\lvert x \rvert\rvert^2_{P} } \right) + \lambda_{1}(t)tr(\tilde{K}_{P} \tilde{K}_{P}^T) + \lambda_{2}(t) tr(\tilde{K}_{D} \tilde{K}_{D}^T)
$$
$\text{Where:}$
$\tilde{K}_{P} = K_{P} - K_{P}^0: \text{Proportional parameter estimation error.}$
$\tilde{K}_{D} = K_{D} + K_{D}^0: \text{Derivative parameter estimation error}$