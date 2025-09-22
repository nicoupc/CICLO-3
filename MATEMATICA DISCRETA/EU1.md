### **Cheatsheet Definitivo para tu Examen EU1 🚀**

#### **Tema 1: Conjuntos 📦**

**1. Pertenencia (∈) vs. Inclusión (⊆) - ¡El truco de la caja!**
*   **Pertenencia (∈):** "Es un **elemento DENTRO** de la caja".
    *   `x ∈ A` significa que `x` es uno de los objetos sueltos dentro del conjunto A.
*   **Inclusión (⊆):** "Es una **caja más pequeña DENTRO** de la caja grande".
    *   `B ⊆ A` significa que **TODOS** los elementos de la caja B también están en la caja A.
    *   **¡El truco!** Para usar `⊆`, lo que está a la izquierda **DEBE SER UN CONJUNTO** (tener llaves `{}`).

**2. Operaciones Clave**
*   **Unión (∪):** Juntar **TODO** lo de ambos conjuntos, sin repetir.
*   **Intersección (∩):** Solo lo que tienen en **COMÚN**.
*   **Diferencia (A - B):** A los de A, **QUÍTALE** los que también están en B.
*   **Complemento (A'):** **TODO** lo que está fuera de A (pero dentro del universo).

**3. Conjunto Potencia P(A) - ¡El armario de ropa!**
*   **¿Qué es?** Es el conjunto de **TODOS los posibles subconjuntos** que puedes formar con los elementos de A. (¡Incluyendo el conjunto vacío `∅` y el mismo conjunto A!).
*   **¡El truco!** Si A tiene `n` elementos, su conjunto potencia $P(A)$ tendrá **$2^n$** elementos.
    *   Si $A = \{1, 2\}$, $|A|=2$. Entonces $|P(A)| = 2^2 = 4$.
    *   $P(A) = \{\emptyset, \{1\}, \{2\}, \{1,2\}\}$.

---

#### **Tema 2: Lógica y Cuantificadores 🧠**

**1. Conectores Lógicos - ¿Cuándo es VERDADERO?**

| Símbolo | Nombre           | Cuándo es VERDADERO (V)                             |
| :------ | :--------------- | :-------------------------------------------------- |
| **∧**   | **Y** (AND)      | Solo si **AMBOS** son V.                            |
| **∨**   | **O** (OR)       | Si **AL MENOS UNO** es V.                           |
| **→**   | **Entonces...**  | **SIEMPRE**, excepto si es `V → F` (esto es FALSO). |
| **↔**   | **Si y solo si** | Si **AMBOS** son iguales (V↔V o F↔F).               |
| **~**   | **NO**           | Cambia el valor (V a F, F a V).                     |

**2. Cuantificadores (∀ y ∃) - ¡El truco para ganar la discusión!**
*   **∀ (Para TODOS):** Para demostrar que es **FALSO**, solo necesitas encontrar **UN contraejemplo**.
*   **∃ (Existe AL MENOS UNO):** Para demostrar que es **VERDADERO**, solo necesitas encontrar **UN ejemplo** que funcione.

**3. Negación de Cuantificadores (Ley de De Morgan)**
*   **¡El truco!** Cambia el cuantificador y niega lo de adentro.
    *   La negación de `∀x, P(x)` ("Todos son...") es `∃x, ~P(x)` ("Existe uno que no es...").
    *   La negación de `∃x, P(x)` ("Existe uno que es...") es `∀x, ~P(x)` ("Todos no son...").

---

#### **Tema 3: Relaciones y Propiedades 🔗**

**¡La Tabla Mágica de Propiedades!** (Tu mejor amiga para el examen)

| Propiedad      | La Regla Súper Simple                                   | Truco en el Dígrafo (Dibujo)                         | Truco en la Matriz (Tabla)                 |
| :------------- | :------------------------------------------------------ | :--------------------------------------------------- | :----------------------------------------- |
| **Reflexiva**  | "Yo conmigo mismo" (Todos se relacionan consigo mismos) | **TODOS** los puntos tienen un bucle 🔄.             | La **diagonal principal es todo 1s**.      |
| **Simétrica**  | "Si tú conmigo, yo contigo" (Si hay ida, hay vuelta)    | Las flechas son de **ida y vuelta** ↔️.              | La matriz es un **espejo** en la diagonal. |
| **Transitiva** | "El atajo" (Si A→B y B→C, debe haber A→C)               | Si hay un camino de 2 pasos, hay una flecha directa. | $M_{R^2}$ está "incluida" en $M_R$.        |

**Relación de Equivalencia (El Club VIP 👑)**
*   **¿Qué es?** Una relación que es **Reflexiva, Simétrica Y Transitiva**.
*   **¿Qué hace?** Agrupa los elementos en "cajas" de equivalentes.
*   **Clase de Equivalencia []:** La "caja" de un elemento `a`. Son todos los que se relacionan con `a`.
    *   **¡El truco de la matriz!** Para hallar la clase de `a`, ¡simplemente **lee la fila de `a`** en la matriz! Los 1s te dicen quiénes están en su caja.
*   **Conjunto Cociente (A/R):** La colección de todas las "cajas" que formaste.

---

#### **Tema 4: Operaciones con Relaciones (¡Puro poder con Matrices!) ⚙️**

Dadas dos relaciones R y S con sus matrices $M_R$ y $M_S$:

*   **Relación Inversa (R⁻¹):** "Voltear las flechas".
    *   **¡El truco de la matriz!** Transponer la matriz. $M_{R^{-1}} = (M_R)^T$. (Cambias filas por columnas).

*   **Unión (R ∪ S):** "Juntar todas las flechas".
    *   **¡El truco de la matriz!** Hacer un **OR** celda por celda. $M_{R \cup S} = M_R \lor M_S$.

*   **Intersección (R ∩ S):** "Solo las flechas que se repiten".
    *   **¡El truco de la matriz!** Hacer un **AND** celda por celda. $M_{R \cap S} = M_R \land M_S$.

*   **Composición (R o S):** "Caminos de S a R".
    *   **¡El truco de la matriz!** Multiplicación booleana, **¡OJO CON EL ORDEN!**
        $M_{R \circ S} = M_S \odot M_R$. (¡Sí, el orden se invierte!)

*   **Relación al Cuadrado (R²):** "Caminos de longitud 2".
    *   **¡El truco de la matriz!** Multiplicar la matriz por sí misma.
        $M_{R^2} = M_R \odot M_R$.

*   **Clausura Transitiva (R∞):** "Todos los caminos posibles".
    *   **¡El truco de la matriz!** Se calcula con el **Algoritmo de Warshall**, o uniendo las potencias:
        $M_{R^\infty} = M_R \lor M_{R^2} \lor M_{R^3} \lor \dots$ (hasta que ya no cambie).

---

¡Y listo! Con esta hoja de trucos tienes todo lo que necesitas. Repasa cada sección, entiende los "trucos" y verás que puedes resolver cualquier problema que te pongan.

**¡Mucha suerte en tu examen EU1, sé que lo harás genial!** 👍