#Explanation #Chairing 

***Barrier Lyapunov Functions*** (**BLF**) enforce **state constraints** by designing the ***Lyapunov Function*** $V_{B}$ to grow unbounded as $x$ approaches the constraint boundary. For our system, we define our **constraint** as:
$$
\mathrm{x} = \begin{bmatrix}
q \\
\dot{q}
\end{bmatrix}
$$
$$
\lvert\lvert \mathrm{x} \rvert\rvert^2_{P} < x^+ 
$$
The constant $x^+$ is defined as the boundary of the state, in the case of two **cobots** working on the same **workspace**, this constant is constantly updated by the state of the other robot.