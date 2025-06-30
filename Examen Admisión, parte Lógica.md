*Nombre: Santiago Peñúñuri Félix*
*Carrera (Institución): Ingeniería Mecatrónica*

---
1. (25 pts) Demostrar la validez del siguiente argumento: $[(p \to q) \wedge (q \to r)] \to (p \to r)$
*Para demostrar la validez, hacemos la tabla de verdad del argumento.*

| $p$ | $q$ | $r$ | $p\to q$ | $q\to r$ | $p\to r$ | $(p\to q) \wedge (q\to r)$ | $\text{Todo}$ |
| --- | --- | --- | -------- | -------- | -------- | -------------------------- | ------------- |
| V   | F   | V   | F        | V        | V        | F                          | V             |
| V   | V   | V   | V        | V        | V        | V                          | V             |
| V   | F   | F   | F        | V        | F        | F                          | V             |
| V   | V   | F   | V        | F        | F        | F                          | V             |
| F   | F   | V   | V        | V        | V        | V                          | V             |
| F   | V   | V   | V        | V        | V        | V                          | V             |
| F   | F   | F   | V        | V        | V        | V                          | V             |
| F   | V   | F   | V        | F        | V        | F                          | V             |
*Se ve entonces que el argumento se cumple para todas las condiciones, por lo que es una **tautología**.*

2. (25 pts) Demostrar la validez del siguiente argumento:
	Si me gustan las matemáticas, entonces estudio.
	Yo estudio o repruebo.
	Si repruebo, entonces no me gustan las matemáticas.

*Asignamos variables a los argumentos.*
$$
\begin{matrix}
p \equiv \text{Me gustan las matemáticas} \\
q \equiv \text{Estudio} \\
r \equiv \text{Repruebo}
\end{matrix}
$$
*En base a esto, creamos las proposiciones adecuadas.*
	Si me gustan las matemáticas, entonces estudio.
$$p\to q$$
	Yo estudio o repruebo.
$$q \vee r$$
	Si repruebo, entonces no me gustan las matemáticas.
$$r\to \neg q$$

*Para demostrar la validez del argumento, hacemos la tabla de verdad. Revisando el caso en el que todas las premisas sean verdaderas al mismo tiempo.* 

| $p$ | $q$ | $r$ | $p\to q$ | $q\vee r$ | $\neg q$ | $r\to \neg q$ | $\text{Todo}$ |
| --- | --- | --- | -------- | --------- | -------- | ------------- | ------------- |
| V   | V   | V   | V        | V         | F        | F             | F             |
| V   | V   | F   | V        | V         | F        | V             | V             |
| V   | F   | V   | F        | V         | V        | V             | F             |
| V   | F   | F   | F        | F         | V        | V             | F             |
| F   | V   | V   | V        | V         | F        | F             | F             |
| F   | V   | F   | V        | V         | F        | V             | V             |
| F   | F   | V   | V        | V         | V        | V             | V             |
| F   | F   | F   | V        | F         | V        | V             | F             |
*La contradicción podría venir de la 3ra proposición $r\to \neg q$, pero observamos que para el caso que todas las proposiciones son verdaderas, no se contradice a esta proposición.*


3. (25 pts) Demuestre por contradicción.
$$
\begin{matrix}
\neg(p \vee s) \\
p \vee (q \wedge r) \\
--- \\
\therefore \neg q
\end{matrix}
$$


4. (25 pts) La secuencia de Fibonnaci $\{ f_{n} \}$ se define como:
$$ \begin{matrix}
f_{1} = 1 \\
f_{2} = 1 \\
f_{n} = f_{n-1} + f_{n-2}, \forall n \geq 3, n ∈ \text{natural positivo}\
\end{matrix}
$$
Demostrar por inducción matemática que:
$$
\sum_{i=1}^n f_{i} = f_{n+2} - 1, \text{para todo } n ∈ \text{natural positivo mayor o igual a 1}
$$
Describa rigurosamente la demostración utilizando todos los pasos planteados en clase.

*Para esto, primero planteamos el caso más pequeño posible; Es decir, cuando $n=3$.*
$$
\begin{matrix}
f_{3} = f_{1} + f_{2} = 1 + 1 = 2  \\
\sum_{i=1}^3f_{i} = f_{5} - 1 \\
f_{1}+f_{2}+f_{3} = f_{5}-1 \\
1 +1 +2 = 5 - 1 \\
4 = 4
\end{matrix}
$$
	*Ahora planteamos un caso para hacer la deducción en base a nuesta hipotesis original. En este caso, podemos decir que si para un número cualquiera $k \geq n$ es válido el argumento, entonces existe un número $k+1$ para el que también es válido. Entonces:*
$$\sum_{i=1}^{k+1} f_{i} = f_{k+3} - 1$$
*Del lado izquierdo de la ecuacion:*
$$
\sum_{i=1}^{k+1} f_i=  \sum_{i=1}^{k} f_{i} + f_{k+1}
$$
*Por nuestra hipotesis original:*
$$
\sum_{i=1}^{k} f_{i} + f_{k+1} = f_{k+2} - 1 + f_{k+1}
$$
*De aquí, podemos obtener $f_{k+3}$ basado en la definición de la secuencia de Fibonacci:*
$$
\begin{matrix}
f_{k+3} = f_{k+2} + f_{k+1} \Rightarrow f_{k+3} - 1 = f_{k+2} + f_{k+1} - 1 \\
\sum_{i=1}^{k+1} f_i = f_{k+3} - 1
\end{matrix}
$$
*Por lo que comprobamos y damos validez a la demostración ya que nos queda lo mismo de ambos lados de la ecuación para todo $n \geq 3, n \in \text{Naturales Positivos}$.*

