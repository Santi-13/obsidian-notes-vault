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
The constant $x^+$ is defined 