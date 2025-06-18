*Nombre: Santiago Peñúñuri Félix*
*Carrera (Institución): Ingeniería Mecatrónica*

1. (25 pts) Determinar la validez del siguiente argumento: 𝑝 → 𝑞, 𝑟 → 𝑞, 𝑟 ⊨ ¬$p$ 

| p   | r   | q   | $\neg p$ | $p \to q$ | $r \to q$ | $r ⊨ \neg p$ |
| --- | --- | --- | -------- | --------- | --------- | ------------ |
| V   | V   | V   | F        | V         | V         | F            |
| V   | V   | F   | F        | F         | F         | F            |
| F   | V   | V   | V        | V         | V         | V            |
| F   | V   | F   | V        | V         | F         | V            |
| V   | F   | V   | F        | V         | V         | V            |
| V   | F   | F   | F        | F         | V         | V            |
| F   | F   | V   | V        | V         | V         | F            |
| F   | F   | F   | V        | V         | V         | F            |

El argumento no es válido, ya que no sigue las premisas del argumento y hay casos en los que, aunque $p$ implique $q$ y $r$ implique $q$, $r$ no satisface $\neg p$.

2. (25 pts) Mostrar i) por tablas de verdad y ii) por algebra de proposiciones, si la expresión 𝑝 ↔ 𝑞 ≡ (𝑝 ∨ 𝑞) → (𝑞 ∧ 𝑝) es efectivamente una equivalencia.
i)

| $p$ | $q$ | $p \leftrightarrow q$ | $p ∨ q$ | $𝑞 ∧ 𝑝$ | $(𝑝 ∨ 𝑞) → (𝑞 ∧ 𝑝)$ | \*  |
| --- | --- | --------------------- | ------- | --------- | ----------------------- | --- |
| V   | V   | V                     | V       | V         | V                       | V   |
| V   | F   | F                     | V       | F         | F                       | V   |
| F   | V   | F                     | V       | F         | F                       | V   |
| F   | F   | V                     | F       | F         | V                       | V   |
\* la expresión entera

ii) 
$p∨q$
$𝑞 ∧ 𝑝$
---
$\therefore $

3. (25 pts) Resolver por resolución.
![[Pasted image 20250618113416.png]]

$\neg p ∨ s$
$\neg r ∨ (s ∧ t)$
$p ∨ r ∨ m$
---
$\therefore s ∨ t ∨ m$



4. (20 pts) Considere la siguiente red.
![[Pasted image 20250618113424.png]]
Que puede representarse como (𝑝 ∨ 𝑞 ∨ 𝑟) ∧ (𝑝 ∨ 𝑡 ∨ ¬𝑞) ∧ (𝑝 ∨ ¬𝑡 ∨ 𝑟) Se propone la siguiente red como una solución equivalente mas sencilla como un mínimo de componentes.
![[Pasted image 20250618113435.png]]
¿Son las redes equivalentes? Justifique detalladamente su respuesta utilizando argumentos de lógica proposicional.

5. (20 pts) Demostrar por inducción matemática que

