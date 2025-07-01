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
2 & -3  \\
-1 & 2
\end{bmatrix} 
$$
Podemos comprobar que si es la inversa multiplicandola para ver si da la identidad.
$$
A^{-1}A = \begin{bmatrix}
2 & -3  \\
-1 & 2
\end{bmatrix} \begin{bmatrix}
2 & 3 \\
1 & 2
\end{bmatrix} = 
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

4. ![[Pasted image 20250701103156.png]]
	1. Podemos ver que $A$ es invertible por la diagonal de ceros que tiene, ya que esto hace que ninguna fila sea una combinación lineal de las otras.
	2. Para calcularlo, primero hay que calcular $\text{adj}(A)$:
$$
\text{For } A = \begin{bmatrix}
2 & -1 & 0 \\
1 & 0 & 3 \\
0 & 2 & -1
\end{bmatrix}
$$
$$
\text{adj}(A) = \begin{bmatrix}
A_{11} & A_{12} & A_{13} \\
A_{21} & A_{22} & A_{23} \\
A_{31} & A_{32} & A_{33}
\end{bmatrix}^T, \text{where } A_{ij} = (-1)^{i+j}|M_{ij}|
$$
$$
\text{adj}(A)=\begin{bmatrix}
-6 & 1 & 2 \\
-1 & -2 & -4 \\
-3 & -6 & 1
\end{bmatrix}^T = \begin{bmatrix}
-6 & -1 & -3 \\
1 & -2 & -6 \\
2 & -4 & 1
\end{bmatrix}
$$
	   Después, se usa la formula de $A^{-1}=\frac{1}{\det A} \text{adj}(A)$:
$$
\begin{matrix}
\det A=2 A_{11} + (-1) A_{12} + 0 \\
\det A= 2(-6) -1 (1) = -12-1=-13
\end{matrix}
$$
$$
A^{-1} = \frac{1}{-13} \begin{bmatrix}
-6 & -1 & -3 \\
1 & -2 & -6 \\
2 & -4 & 1
\end{bmatrix} = \begin{bmatrix}
\frac{6}{13} & \frac{1}{13} & \frac{3}{13} \\
-\frac{1}{13} & \frac{2}{13} & \frac{6}{13} \\
-\frac{2}{13} & \frac{4}{13} & -\frac{1}{13}
\end{bmatrix}
$$
	3. Para encontrar las velocidades angulares:
$$
A^{-1} \begin{bmatrix}
\dot{x} \\
\dot{y} \\
\dot{z}
\end{bmatrix} = \begin{bmatrix}
\frac{6}{13} & \frac{1}{13} & \frac{3}{13} \\
-\frac{1}{13} & \frac{2}{13} & \frac{6}{13} \\
-\frac{2}{13} & \frac{4}{13} & -\frac{1}{13}
\end{bmatrix} \begin{bmatrix}
1 \\
-2 \\
3
\end{bmatrix}
$$
$$
= \begin{bmatrix}
\frac{6}{13}-\frac{2}{13}+\frac{9}{13} \\
-\frac{1}{13}-\frac{4}{13}+\frac{18}{13} \\
-\frac{2}{13}-\frac{8}{13}-\frac{3}{13}
\end{bmatrix} = \begin{bmatrix}
1 \\
1 \\
-1
\end{bmatrix} = \begin{bmatrix}
\dot{\theta_{1}} \\
\dot{\theta_{2}} \\
\dot{\theta_{3}}
\end{bmatrix}
$$

5. ![[Pasted image 20250701105731.png]]


6. ![[Pasted image 20250701105815.png]]
Para las primeras dos demostraciones, así como para la cuarta simplemente podemos obtener el determinante de estas:
$$
R = R_{x}(\theta)R_{y}(\phi) = \begin{bmatrix}
1 & 0 & 0 \\
0 & \cos \theta & -\sin \theta \\
0 & \sin \theta & \cos \theta
\end{bmatrix} \begin{bmatrix}
\cos \phi & 0 & \sin \phi \\
0 & 1 & 0 \\
-\sin \phi & 0 & \cos \phi
\end{bmatrix}
$$
$$
R = \begin{bmatrix}
\cos \phi & 0 & \sin \phi \\
\sin \phi \sin \theta & \cos \theta & -\sin \theta \cos \phi \\
-\cos \theta \sin \phi & \sin \theta & \cos \theta \cos \phi
\end{bmatrix}
$$
$$
\begin{matrix}
\det R_{x}(\theta) = 1 A_{11} = \cos^2 \theta + \sin^2 \theta \neq 0, \forall \theta \in \mathrm{Re} \\
\det R_{y}(\phi) = 1 A_{22} = \cos^2 \phi + \sin^2 \phi \neq 0, \forall \theta \in \mathrm{Re} \\
\det R=\cos \phi A_{11} + \sin \phi A_{13}  \\
= \cos \phi (\cos^2\theta \cos \phi+\sin^2\theta \cos \phi) + \sin \phi(\sin^2\theta \sin \phi+\cos^2\theta \sin \phi) \neq 0
\end{matrix}
$$
Como $\phi$ o $\theta$ no tienen un valor que la suma de los cuadrados de sus cosenos y senos sean igual a 0, se puede decir que estas matrices de rotación son ortogonales y no singulares.

Para la inversa, necesitamos los $\text{adj}$.
$$
\text{adj}(R_{x}(\theta)) = \begin{bmatrix}
\cos ^2\theta+\sin^2\theta & 0 & 0 \\
0 & \cos \theta & \sin \theta \\
0 & -\sin \theta & \cos \theta
\end{bmatrix}^T = \begin{bmatrix}
\cos ^2\theta+\sin^2\theta & 0 & 0 \\
0 & \cos \theta & -\sin \theta \\
0 & \sin \theta & \cos \theta
\end{bmatrix}
$$
$$
R_{x}^{-1} = \frac{1}{\cos^2 \theta + \sin^2 \theta} \begin{bmatrix}
\cos ^2\theta+\sin^2\theta & 0 & 0 \\
0 & \cos \theta & -\sin \theta \\
0 & \sin \theta & \cos \theta
\end{bmatrix}
$$

$$
\text{adj}(R_{y}(\phi)) = \begin{bmatrix}
\cos \phi & 0 & \sin \phi \\ 
 0 & \cos^2\phi+\sin^2\phi & 0 \\
-\sin \phi & 0 & 
\end{bmatrix}
$$