### **1. Introducción: Los Ladrillos del Software 🧱**

Antes de construir un rascacielos, necesitas entender qué son los ladrillos y el cemento. En programación, es igual.

*   **Dato vs. Información:**
    *   **Datos  raw:** Son valores sueltos, sin contexto. Por ejemplo: `25`, `8`, `CC68`. Por sí solos no significan mucho.
    *   **Información ℹ️:** Son datos organizados y con significado. `CC68` es el código del curso, `8` es el mes y `25` es la edad de una persona. ¡Ahora sí tienen sentido!

*   **Algoritmo 📜:** Es una **receta** o una serie de pasos secuenciales para resolver un problema. Toma una entrada (input), sigue los pasos y produce una salida (output). Piensa en la receta para hacer una torta.

*   **Estructura de Datos 📦:** Es una forma de **organizar y almacenar datos** para poder usarlos eficientemente. No es lo mismo guardar tus archivos en carpetas ordenadas que tenerlos todos sueltos en el escritorio. Las estructuras de datos son esas "carpetas ordenadas" para tu código. Ejemplos que verás: Listas, Pilas, Colas, Árboles.

> **Frase Clave de la Sesión:**
> > "Los malos programadores se preocupan por el código. Los buenos programadores se preocupan por las estructuras de datos y sus relaciones."

**¿Qué significa esto?** 🤔
Imagina que construyes una casa. El "código" son las paredes y el techo. La "estructura de datos" son los cimientos. Si tus cimientos son débiles o están mal diseñados, no importa qué tan bonitas sean tus paredes, la casa no será sólida ni eficiente. La forma en que organizas tus datos es la base de todo gran software.

---

### **2. Tipos de Datos Abstractos (TDA): El "Qué" y no el "Cómo" 🧠**

Este es uno de los conceptos más importantes. ¡Vamos a dominarlo!

*   **Abstracción:** Es el arte de **ocultar la complejidad**. Te enfocas solo en lo que necesitas saber y ocultas los detalles que no son relevantes.
    *   **Analogía del auto 🚗:** Para conducir, necesitas saber usar el volante, los pedales y la palanca de cambios (la **interfaz**). No necesitas ser un mecánico ni entender cómo funciona el motor por dentro (la **implementación**). La abstracción en programación funciona igual.

*   **Tipo de Dato Abstracto (TDA):** Es un modelo conceptual que define un conjunto de valores y las operaciones que puedes hacer con ellos, pero **sin decir cómo se hacen por dentro**.
    *   Un TDA te dice **QUÉ** puedes hacer. Por ejemplo, un TDA "Lista" te diría que puedes:
        *   `agregar_elemento()`
        *   `eliminar_elemento()`
        *   `buscar_elemento()`
    *   El TDA no te dice **CÓMO** se implementan esas funciones. Podría ser con arreglos dinámicos o con listas enlazadas por debajo, ¡pero a ti como usuario no te importa! Solo usas las funciones.
    *   Esto es genial porque separa la idea (la interfaz) de su construcción (la implementación), lo que hace el código más flexible y fácil de mantener.

---

### **3. Análisis de Algoritmos: ¿Tu Código es Rápido o Lento? ⏱️**

Un programa que funciona no es suficiente. ¡Necesita ser **eficiente**!

*   **Eficiencia:** Se mide principalmente en dos recursos:
    1.  **Complejidad Temporal (Tiempo ⏳):** ¿Cuánto tarda tu algoritmo en ejecutarse a medida que aumentan los datos?
    2.  **Complejidad Espacial (Espacio 💾):** ¿Cuánta memoria (RAM) consume tu algoritmo a medida que aumentan los datos?

*   **Los 3 Escenarios de Análisis:** Al analizar un algoritmo, siempre pensamos en:
    *   **Mejor Caso (Best Case) 😊:** El escenario ideal donde el algoritmo termina súper rápido. (Ej: el elemento que buscas está justo al inicio de una lista).
    *   **Caso Promedio (Average Case) 🤔:** El rendimiento esperado en una situación normal.
    *   **Peor Caso (Worst Case) 😫:** El escenario más lento posible. (Ej: el elemento que buscas está al final, o no está, y tuviste que recorrer toda la lista).

> **¿Por qué nos enfocamos en el PEOR CASO?**
> Porque nos da una **garantía**. Si sabemos que en el peor de los casos nuestro programa tardará 1 segundo, podemos estar seguros de que nunca tardará más que eso. Es una forma de estar preparados para lo peor y asegurar que el rendimiento sea aceptable siempre.

---

### **4. Notación Big O: El Lenguaje Universal de la Eficiencia 🅾️**

`Big O` es la forma estándar en la industria para hablar de la complejidad en el **peor caso**. Describe cómo "crece" el tiempo de ejecución a medida que la cantidad de datos (`n`) se hace muy, muy grande.

*   **La Idea Clave:** Cuando `n` es enorme (piensa en millones de datos), solo el término que crece más rápido importa.
    *   **Ejemplo de la diapositiva:** `h(n) = n³ - 12n² + 20n + 110`
    *   Cuando `n` es un millón, `n³` es un número tan gigantesco que los otros términos (`-12n²`, `+20n`, etc.) son como una gota de agua en el océano. No le hacen ni cosquillas.
    *   Por eso, simplificamos y decimos que la complejidad es **O(n³)**. Nos quedamos solo con el "pez gordo".

*   **Jerarquía de Complejidades (de más rápido a más lento):**
    *   **O(1) - Constante:** ¡El rey de la velocidad! 👑 No importa cuántos datos tengas, siempre tarda lo mismo.
    *   **O(log n) - Logarítmico:** Súper eficiente. Aunque añadas millones de datos, el tiempo aumenta muy poco. (Ej: Búsqueda Binaria).
    *   **O(n) - Lineal:** Bueno y muy común. El tiempo crece proporcionalmente a los datos. Si duplicas los datos, duplicas el tiempo. (Ej: Recorrer un arreglo una vez).
    *   **O(n log n) - Log-Lineal:** Muy buen rendimiento para algoritmos de ordenamiento.
    *   **O(n²) - Cuadrático:** Se empieza a poner lento. 🐢 Típico de bucles anidados. Si tienes 10 veces más datos, tarda 100 veces más.
    *   **O(2ⁿ) - Exponencial:** ¡Peligro! 🚨 Inservible para grandes cantidades de datos. El tiempo de ejecución se dispara muy rápido.

---

### **5. ¡A Programar! Programación Genérica y Templates ♻️**

¿Te imaginas tener que escribir la misma función de `suma` una vez para `int`, otra para `float` y otra para `double`? Sería repetitivo y un dolor de cabeza.

*   **Programación Genérica:** Es una técnica que te permite escribir código que funciona con **cualquier tipo de dato**.

*   **Templates en C++ (Plantillas):** Son la herramienta para lograr la programación genérica.
    *   Creas una "plantilla" de función o clase usando un marcador de posición como `typename T`.
    *   Cuando usas la función (ej: `suma<int>(a, b)`), el compilador ve que quieres usarla con `int` y automáticamente crea la versión correcta para ti.
    *   **Ventaja Principal:** **Reutilización de código**. Escribes una vez, usas muchas veces. ¡Menos código, menos errores, más eficiencia!

¡Y eso es todo por la primera semana! Con estos conceptos bien entendidos, tienes una base súper sólida para todo lo que viene.
