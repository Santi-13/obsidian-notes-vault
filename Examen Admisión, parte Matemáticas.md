*Nombre: Santiago Peñúñuri Félix*
*Carrera (Institución): Ingeniería Mecatrónica*

---
1. Un dron tricóptero (3 rotores) debe ajustar las fuerzas de sus motores F1, F2 y F3 para cumplir tres objetivos simultáneos:
	1. **Mantener la altitud (equilibrio vertical).** 
	2. **Generar un torque de inclinación para moverse en el eje x.** 
	3. **Generar un torque de inclinación para moverse en el eje y**
...
$$
\begin{bmatrix}
1 & 1 & 1 \\
0.25 & 0 & -0.25 \\
-0.125 & 0.25 & -.125
\end{bmatrix} \begin{bmatrix}
19.62 \\
0.2 \\
0.15
\end{bmatrix}
$$
*Por eliminación gaussiana, multiplicamos por 4 la segunda fila y por 8 la tercera. Siguiendo este proceso hasta encontrar la solución.*
$$
\begin{bmatrix}
1 & 1 & 1 \\
1 & 0 & -1 \\
-1 & 2 & -1
\end{bmatrix} \begin{bmatrix}
19.62 \\
0.8 \\
1.2
\end{bmatrix}
$$



2. Encuentre la función de transferencia del siguiente circuito.

3. 