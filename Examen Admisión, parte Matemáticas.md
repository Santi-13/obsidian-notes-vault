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
F_{1} = 6.74
\end{matrix}
$$

Podemos comprobar con las ecuaciones originales:
$$
\begin{matrix}
F_{1} + F_{2} + F_{3} = 19.62 = mg\\
\end{matrix}
$$
$$
\begin{matrix}
(F_{1}-F_{3})L = \tau _{x} \\
(6.74 - 5.94) \times 0.25 = 0.2 \\
(0.8) \times 0.25 = 0.2 \\
0.2 = 0.2
\end{matrix}
$$
$$
\begin{matrix}
\left( F_{2} - \frac{F_{1} + F_{3}}{2} \right)L = \tau_{y} \\
\left( 6.94 - \frac{6.74 + 5.94}{2} \right) \times 0.25 = 0.15 \\
( 6.94 - 6.34 ) \times 0.25 = 0.15 \\
0.6 \times 0.25 = 0.15 \\
0.15 = 0.15
\end{matrix}
$$
2. Un brazo robótico con 5 articulaciones debe posicionar su efector final en *(x,y,z)* sujeto a las siguientes restricciones:
![[Pasted image 20250701102609.png]]
$$
\begin{bmatrix}
2 & -1 & 0 & 3  & 0\\
0 & 1 & 1 & 0 & -1 \\
1 & 0 & 1 & 2 & 0 \\
1 & 0 & -2 & 0 & 1
\end{bmatrix} \begin{bmatrix}
10 \\
5 \\
8 \\
3
\end{bmatrix}
$$


3. Encuentre una matriz A tal que:
![[Pasted image 20250701102741.png]]
$$
A^{-1} = \frac{1}{\det A} \begin{bmatrix}
d & -b \\
-c & a
\end{bmatrix}
$$
$$
A = \begin{bmatrix}
2 & 3 \\
1 & 2
\end{bmatrix}
$$
$$
\det A = (2\times2) - (3 \times 1) = 4-3 = 1
$$
$$
A^{-1} = \begin{bmatrix}

\end{bmatrix} 
$$

4. 