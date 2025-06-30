*Nombre: Santiago Peñúñuri Félix*
*Carrera (Institución): Ingeniería Mecatrónica*

---
1. (25 pts) Demostrar la validez del siguiente argumento: $[(p \to q) \wedge (q \to r)] \to (p \to r)$
*Para demostrar la validez, hacemos la tabla de verdad del argumento.*

| $p$ | $q$ | $r$ | $p\to q$ | $q\to r$ | $p\to r$ | $(p\to q) \wedge (q\to r)$ | $\text{Todo}$ |
| --- | --- | --- | -------- | -------- | -------- | -------------------------- | ------------- |
| V   | F   | V   | F        | V        | V        |                            |               |
| V   | V   | V   | V        | V        | V        |                            |               |
| V   | F   | F   | F        | V        | F        |                            |               |
| V   | V   | F   | V        | F        | F        |                            |               |
| F   | F   | V   | V        | V        | V        |                            |               |
| F   | V   | V   | V        | V        | V        |                            |               |
| F   | F   | F   | V        | V        | V        |                            |               |
| F   | V   | F   | V        | F        | V        |                            |               |

1. (25 pts) Demostrar la validez del siguiente argumento:
	Si me gustan las matemáticas, entonces estudio.
	Yo estudio o repruebo.
	Si repruebo, entonces no me gustan las matemáticas.

2. (25 pts) Demuestre por contradicción.
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
