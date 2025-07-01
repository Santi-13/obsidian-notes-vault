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
$$
\begin{bmatrix}
1 & 1 & 1 \\
0 & 2 & -2 \\
-1 & 2 & -1
\end{bmatrix} \begin{bmatrix}
19.62 \\
2.0 \\
1.2
\end{bmatrix}
$$
$$
\begin{bmatrix}
1 & 1 & 1 \\
0 & 1 & -1 \\
0 & 3 & 0
\end{bmatrix} \begin{bmatrix}
19.62 \\
1.0 \\
20.82
\end{bmatrix}
$$
$$
\begin{bmatrix}
1 & 1 & 1 \\
0 & 1 & -1 \\
0 & 1 & 0
\end{bmatrix} \begin{bmatrix}
19.62 \\
1.0 \\
6.94
\end{bmatrix}
$$
$$
\begin{bmatrix}
1 & 1 & 1 \\
0 & 1 & -1 \\
0 & 0 & 1
\end{bmatrix} \begin{bmatrix}
19.62 \\
1.0 \\
5.94
\end{bmatrix}
$$
Entonces tenemos que:
$$ F_{3}= 5.94$$
$$ \begin{matrix}
F_{2} -F_{3} = 1 \\
F_{2} - 5.94 = 1 \\
F_{2} = 6.94
\end{matrix} $$
$$
\begin{matrix}
F_{1} + F_{2} + F_{3} = 19.62 \\
F_{1} + 6.94 + 5.94 = 19.62 \\
F_{1} = 19.62 - 12.88 \\
F_{1} = 
\end{matrix}
$$



3. Encuentre la función de transferencia del siguiente circuito.

4. 