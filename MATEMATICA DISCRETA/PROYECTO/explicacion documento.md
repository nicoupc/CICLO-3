### **1AMA0265 – 202520 PROYECTOS (Página 1 del primer documento)**

Aquí se describe tu Proyecto 1: **Transformaciones Lineales**.

*   **Objetivo:** Aplicar transformaciones lineales a figuras geométricas.
    *   Esto significa que el programa que van a hacer debe tomar una figura (como un triángulo) y cambiarla de alguna manera (girarla, voltearla, cambiarle el tamaño) usando matemáticas.
*   **Descripción:**
    *   **Representar figuras simples:** Tu programa debe poder "dibujar" triángulos y cuadriláteros. ¿Cómo se hace esto? En el código, estas figuras son solo un conjunto de **puntos** (coordenadas como (x,y)) que se unen para formar la figura. Por ejemplo, un triángulo es `(x1, y1), (x2, y2), (x3, y3)`.
    *   **El programa debe:**
        *   **Graficar "cualquier" triángulo o cuadrilátero:** Esto significa que el usuario (o el programa) debe poder poner los puntos que quiera, no siempre la misma figura fija.
        *   **Aplicar transformaciones:** Aquí vienen las acciones principales:
            *   **Rotación:** Girar la figura. Puede ser alrededor de un punto cualquiera (el "centro de rotación") y en sentido horario o antihorario.
            *   **Reflexión:** Voltear la figura como un espejo. Puede ser sobre una línea (el "eje x", el "eje y", el "origen" (el punto (0,0)), o "cualquier" línea recta que el usuario elija).
            *   **Homotecia:** Cambiar el tamaño de la figura. Se hace desde un punto central (el "centro de homotecia"). La figura se hace más grande o más pequeña.
        *   **Mostrar figura original y transformada:** El programa debe dibujar las dos figuras juntas para ver el cambio.
        *   **Permitir al usuario ingresar su propia matriz de transformación:** Esto es más avanzado. Además de las rotaciones, reflexiones y homotecias predefinidas, el usuario debería poder escribir sus propios números en una "tabla" (una matriz) y ver qué transformación ocurre.
        *   **Verificar si la transformación conserva longitudes o áreas (isometría):** Una "isometría" es cuando la figura, después de la transformación, sigue teniendo el mismo tamaño y forma, solo que está en otra posición o girada. Rotaciones y reflexiones son isometrías; la homotecia (si cambia el tamaño) no lo es. Tu programa debe decir si la transformación mantuvo el tamaño original.

---

### **Informe del Trabajo Grupal - "Transformaciones Lineales" (Segundo documento adjunto)**

Este es el documento clave que explica las matemáticas detrás de todo.

#### **Página 2: Índice**
Aquí está la estructura del informe. Te ayuda a ver dónde se explica cada cosa.

#### **Página 3: 1. Introducción y 2. Objetivos**
*   **1. Introducción:** Básicamente, dice que el proyecto une matemáticas discretas y programación para entender las transformaciones lineales aplicadas a figuras en un plano. Se va a usar C++ y Visual Studio 2019. Se busca no solo entender la teoría sino también ver cómo se aplica en un programa [2, p. 3].
*   **2. Objetivos:**
    *   **2.1. Objetivo General:** Crear un programa en C++ que dibuje figuras y les aplique transformaciones lineales, para que sea más fácil entenderlas viendo los cambios [2, p. 3].
    *   **2.2. Objetivo Específicos:** Estos son como una lista de lo que el programa debe poder hacer, y es casi una repetición de los puntos de la descripción del proyecto que vimos antes [2, p. 4].
        *   Dibujar triángulos y cuadriláteros.
        *   Hacer rotaciones, reflexiones, homotecias (considerando diferentes puntos o ejes de transformación).
        *   Permitir al usuario poner sus propias matrices (tablas de números) de transformación.
        *   Mostrar la figura original y la transformada.
        *   Verificar si conserva el tamaño y la forma (isometrías).

#### **Página 4: 3. Marco Teórico y 3.1. ¿Qué es una transformación lineal?**
Aquí empieza lo importante de las matemáticas.

*   **3.1. ¿Qué es una transformación lineal?**
    *   Una transformación lineal es como una **función** matemática que toma un punto (o "vector") en un "espacio" (tu plano cartesiano) y lo mueve a otro punto en el mismo espacio o en otro. Pero no lo mueve de cualquier forma; sigue reglas muy específicas.
    *   **Reglas clave (Aditividad y Homogeneidad):**
        *   **Aditividad:** `T(u + v) = T(u) + T(v)`
            *   Imagina que `u` y `v` son dos puntos. Si primero sumas `u` y `v` (obtienes un nuevo punto) y luego le aplicas la transformación `T` a ese resultado, es lo mismo que si aplicas `T` a `u`, luego aplicas `T` a `v`, y al final sumas los dos resultados. Es una propiedad de "orden".
        *   **Homogeneidad:** `T(α·ν) = α· Τ(ν)`
            *   Imagina que `v` es un punto y `α` es un número (como 2 o 3). Si primero multiplicas el punto `v` por `α` (lo estiras o encoges) y luego le aplicas la transformación `T`, es lo mismo que si primero aplicas `T` a `v` y luego multiplicas el resultado por `α`.
    *   **Ejemplo fundamental: T(x,y) = (2x, 3y)**
        *   Esta es una transformación muy simple. Si tienes un punto `(x, y)`, esta transformación lo convierte en un nuevo punto `(2x, 3y)`.
        *   **Explicación de la "Demostración":** Tus compañeros muestran que esta transformación `T(x,y) = (2x, 3y)` sí cumple las dos reglas (Aditividad y Homogeneidad).
            *   **Aditividad:** Toman dos puntos `(x1, y1)` y `(x2, y2)`.
                *   Primero los suman: `(x1+x2, y1+y2)`.
                *   Luego aplican `T`: `(2*(x1+x2), 3*(y1+y2))`. Esto da `(2x1+2x2, 3y1+3y2)`.
                *   Ahora lo separan: `(2x1, 3y1) + (2x2, 3y2)`.
                *   ¡Y esto es `T(x1, y1) + T(x2, y2)`! Como ves, el resultado es el mismo, así que cumple la aditividad.
            *   **Homogeneidad:** Toman un punto `(x,y)` y un número `α`.
                *   Multiplican el punto por el número: `(αx, αy)`.
                *   Luego aplican `T`: `(2*αx, 3*αy)`.
                *   Ahora sacan el `α`: `α * (2x, 3y)`.
                *   ¡Y esto es `α * T(x, y)`! También cumple la homogeneidad.
        *   Por eso concluyen: `∴T Es una transformación lineal.`

#### **Página 5: Propiedades importantes y Representación Matricial**

*   **Propiedades importantes:**
    *   `T(0) = 0w`: Si transformas el punto origen (0,0), el resultado sigue siendo el origen.
    *   `T(−v) = −T(ν)`: Si transformas un punto negativo, es lo mismo que transformar el punto positivo y luego hacerlo negativo.
    *   **Toda transformación lineal puede representarse mediante una matriz:** ¡Esta es la idea central para el código! ✨
*   **Representación Matricial: T(x) = Ax**
    *   Esto significa que cualquier transformación lineal `T` se puede hacer multiplicando una "matriz" `A` por el punto `x` (que es también una matriz, pero de una sola columna).
    *   La matriz `A` es como una **tabla de números** que contiene la "receta" de la transformación.
    *   **Ejemplo de representación: T(x, y) = (3x + y, − x + 2y)**
        *   Si tu transformación convierte `(x, y)` en `(3x + y, − x + 2y)`, ¿cuál es su matriz `A`?
        *   Mira los números que acompañan a `x` y `y` en cada parte del resultado:
            *   Para la primera parte `(3x + 1y)`: los números son `3` y `1`.
            *   Para la segunda parte `(-1x + 2y)`: los números son `-1` y `2`.
        *   Así se forma la matriz `A`:
            ```
            A = [ 3  1 ]  <-- (3x + 1y)
                [ -1 2 ]  <-- (-1x + 2y)
            ```
        *   Cuando multiplicas esta matriz `A` por el punto `[x, y]` (escrito como columna), obtienes el nuevo punto `[3x+y, -x+2y]`. Esto es lo que significa la fórmula `[3x+y / -x+2y]`.

#### **Página 5 (continuación): 3.2. Rotación**

*   **¿Qué es?** Girar una figura.
*   **Representación Matemática:**
    *   **Rotación alrededor del origen (0,0) por un ángulo θ (theta):**
        *   Si tienes un punto `(x, y)` y quieres girarlo `θ` grados (en sentido antihorario, que es el estándar), usas esta matriz:
            ```
            [ x' ] = [ cos θ  -sin θ ] [ x ]
            [ y' ]   [ sin θ   cos θ ] [ y ]
            ```
        *   `x'` y `y'` son las nuevas coordenadas del punto después de girarlo.
        *   `cos θ` y `sin θ` son el coseno y el seno del ángulo. Los calculas con calculadora (o tu programa lo hará) para el ángulo que quieres girar.
        *   **Cómo funciona:** Tu programa tomará cada punto `(x,y)` de tu figura, lo multiplicará por esta "matriz de rotación" y obtendrá un nuevo `(x', y')`. Al unir todos los `(x', y')` formará la figura girada.
    *   **Rotación alrededor de un punto arbitrario (h, k):**
        *   Si quieres girar la figura no sobre el (0,0), sino sobre otro punto `(h, k)`, el proceso es:
            1.  **Mover el punto `(h,k)` al origen:** Le restas `(h,k)` a todos tus puntos `(x,y)`. Esto convierte `(x,y)` en `(x-h, y-k)`.
            2.  **Rotar sobre el origen:** Aplicas la matriz de rotación de arriba a `(x-h, y-k)`.
            3.  **Mover de vuelta:** Le sumas `(h,k)` a los puntos ya rotados para regresarlos a su posición correcta.
        *   La fórmula grande que ves `[ x' / y' ] = [ cos θ -sin θ / sin θ cos θ ] [ x-h / y-k ] + [ h / k ]` resume esos tres pasos.

#### **Página 6: 3.3. Reflexión**

*   **¿Qué es?** Voltear una figura como si fuera un espejo.
*   **Representación Matemática:**
    *   Aquí tienes matrices específicas para reflejar sobre líneas comunes:
        *   **Reflexión sobre el eje X:** `[ x' / y' ] = [ 1 0 / 0 -1 ] [ x / y ]`
            *   Si `y` era 5, ahora es -5. `x` se queda igual. Ejemplo: `(2, 5)` se vuelve `(2, -5)`.
        *   **Reflexión sobre el eje Y:** `[ x' / y' ] = [ -1 0 / 0 1 ] [ x / y ]`
            *   Si `x` era 2, ahora es -2. `y` se queda igual. Ejemplo: `(2, 5)` se vuelve `(-2, 5)`.
        *   **Reflexión sobre la recta y = x:** `[ x' / y' ] = [ 0 1 / 1 0 ] [ x / y ]`
            *   Intercambia `x` por `y`. Ejemplo: `(2, 5)` se vuelve `(5, 2)`.
    *   **Reflexión sobre una recta arbitraria ax + by + c = 0:**
        *   Esta es la fórmula general para cualquier línea recta. Es más compleja y tu documento te da la fórmula final `[ x' / y' ] = [x / y] - (2a(ax + by + c) / a²+b²) [ a / b ]`. No te preocupes por entender el porqué de cada parte de esta fórmula ahora mismo, solo que existe para casos generales. En tu proyecto, se pide que implementen al menos las reflexiones en los ejes y `y=x` con multiplicación matricial, lo que es mucho más sencillo.

#### **Página 6 (continuación): 3.4. Homotecia**

*   **¿Qué es?** Cambiar el tamaño de una figura (agrandar o encoger).
*   **Representación Matemática:**
    *   **Homotecia con centro en el origen (0,0):**
        *   Si quieres cambiar el tamaño de una figura por un factor `k` (por ejemplo, `k=2` para hacerla el doble de grande, o `k=0.5` para hacerla la mitad), y el centro de la ampliación es el (0,0), usas esta matriz:
            ```
            [ x' ] = [ k 0 ] [ x ]
            [ y' ]   [ 0 k ] [ y ]
            ```
        *   Cada coordenada `x` se multiplica por `k` y cada `y` se multiplica por `k`. Ejemplo: si `k=2`, `(x,y)` se vuelve `(2x, 2y)`.
    *   **Homotecia con centro en (h, k):**
        *   Similar a la rotación con centro arbitrario, si el centro de ampliación es `(h, k)` y no el (0,0), el proceso es:
            1.  **Mover el punto `(h,k)` al origen:** Restas `(h,k)` a todos tus puntos `(x,y)`.
            2.  **Aplicar la homotecia sobre el origen:** Multiplicas `(x-h, y-k)` por la matriz de homotecia con factor `k`.
            3.  **Mover de vuelta:** Sumas `(h,k)` a los puntos ya transformados.
        *   La fórmula `[ x' / y' ] = [ k 0 / 0 k ] [ x-h / y-k ] + [ h / k ]` resume estos pasos.

#### **Página 7: 4. Ejercicios resueltos**

Estos ejercicios son ejemplos prácticos de cómo encontrar la "receta mágica" (la transformación lineal) cuando sabes dónde estaban algunos puntos y a dónde fueron a parar.

*   **4.1. Ejercicio 1: Transformación lineal a partir de puntos de una figura.**
    *   **El problema:** Tienes los puntos `A(2,6)` y `B(2,4)` de una figura original. Sabes que después de la transformación, `A` se vuelve `A'(4,4)` y `B` se vuelve `B'(3,2)`. ¡Quieren que encuentres la fórmula de la transformación!
    *   **La solución:** Sabes que una transformación lineal general es `T(x, y) = (ax + by; cx + dy)`. Lo que tienes que hacer es encontrar los números `a, b, c, d`.
        1.  Usas el punto `A`: `T(2,6) = (a*2 + b*6; c*2 + d*6)`. Y sabes que esto debe ser igual a `(4,4)`.
            *   Esto te da dos ecuaciones: `2a + 6b = 4` y `2c + 6d = 4`.
        2.  Usas el punto `B`: `T(2,4) = (a*2 + b*4; c*2 + d*4)`. Y sabes que esto debe ser igual a `(3,2)`.
            *   Esto te da otras dos ecuaciones: `2a + 4b = 3` y `2c + 4d = 2`.
        3.  Ahora tienes dos sistemas de ecuaciones (uno para `a` y `b`, otro para `c` y `d`):
            *   Sistema 1: `2a + 6b = 4` y `2a + 4b = 3`
            *   Sistema 2: `2c + 6d = 4` y `2c + 4d = 2`
        4.  ¡Resuelves estos sistemas! El documento dice que al resolverlos, obtienes `a = 0.5, b = 0.5, c = -1, d = 1`.
        5.  Finalmente, sustituyes esos números en la fórmula general: `T(x,y) = (0.5x + 0.5y; − x + y)`. ¡Esa es tu transformación!
*   **4.2. Ejercicio 2: Transformación de un paralelogramo en otro.**
    *   **El problema:** Tienes un paralelogramo (Figura 1) y sabes a qué se transforma (Figura 2). Quieren que encuentres dos posibles transformaciones lineales que hagan eso.
    *   **La solución:** Aquí usan una propiedad importante de las transformaciones lineales: si sabes cómo transforma los puntos base `(1,0)` y `(0,1)` (lo que se llama la base canónica), entonces puedes saber cómo transforma *cualquier* punto `(x,y)` con la fórmula `T(x; y) = xT(1; 0) + yT(0; 1)`.
        *   El ejercicio te da los puntos del paralelogramo y sus transformaciones. A partir de esos puntos, tus compañeros calculan a qué se transforma `T(1,0)` y `T(0,1)`.
        *   **Caso 1 y Caso 2:** Son dos formas diferentes de obtener los `T(1,0)` y `T(0,1)` que resultan en la misma transformación final. El método es similar a resolver sistemas de ecuaciones, pero aplicando la propiedad de que los puntos de una figura se pueden expresar como combinaciones de otros puntos.

#### **Página 8: 5. Referencias Bibliográficas**

*   Esta sección es simplemente una lista de los libros y artículos que tus compañeros usaron como fuentes de información para hacer el informe. Es importante para mostrar que la información es creíble y de dónde la sacaron [2, p. 8].

---

### **PROYECTOS - AVANCE AL 30% (Página 1 del último documento adjunto)**

Este documento es una guía corta sobre qué se espera exactamente para este primer avance del 30%. ¡Es muy útil para saber qué mostrar en tu video!

*   **Proyecto 1: Transformaciones Lineales (¡Tu proyecto!)**
    *   **Representar figuras simples:** El programa ya debe poder dibujar triángulos y cuadriláteros como conjuntos de puntos. ¡Importante: no siempre el mismo triángulo o cuadrilátero! El usuario debe poder definirlo.
    *   **Al menos una de las transformaciones:** Tu programa, para este avance, debe tener implementada **al menos una** de las transformaciones (rotación, reflexión o homotecia). No tiene que ser perfecta o con todas las opciones (como centros arbitrarios), pero debe funcionar.
    *   Aunque no completa como se pide (para la entrega final).

---

### **Fechas y Rúbricas (Los otros documentos adjuntos)**

Estos son súper importantes para la entrega de hoy.

*   **Fechas para la presentación del proyecto Grupal (TB1) (página 1):**
    *   **Semana 03 (HOY):** Es la revisión del avance del trabajo con un informe y un vídeo.
    *   **Fecha de entrega:** 14 de septiembre hasta las 23:55 horas. ¡Esto es vital! ⏰
    *   **Puntaje:** 4 puntos (20% de la nota final).

*   **Rúbrica para el primer avance del Proyecto (Informe) – Semana 3 (4 puntos) (página 1):**
    *   Esta es la lista de verificación que el profesor usará para calificarlos.
    *   **Avance del Informe y del Código (3 puntos):**
        *   **LOGRADO (3.0 puntos) si:** Tiene introducción, objetivos, marco teórico (con referencias), citas y bibliografía (min. 2 libros, APA), 2 ejercicios resueltos y tipeados, y el **30% del programa** incluido.
        *   **EN PROGRESO (1.5-2.5 puntos) si:** Cumple 3 o 4 de los ítems.
        *   **INSUFICIENTE (0-1 puntos) si:** Cumple 2 o menos ítems.
    *   **Avance del programa en vídeo (1 punto):**
        *   **LOGRADO (1.0 puntos) si:** Video de 4-10 minutos, muestra y explica la interfaz, explica brevemente la teoría.
        *   **EN PROGRESO (0.5 puntos) si:** Cumple a lo más 2 ítems.
        *   **INSUFICIENTE (0.0 puntos) si:** No presenta video o cumple a lo más un ítem.

*   **Rúbrica para el segundo avance... y Rúbrica para la entrega final... (páginas 2 y 3):**
    *   Estas son para futuras entregas, pero puedes ver cómo el proyecto va creciendo en complejidad.

---

### **Anuncio del profesor (¡Lo más urgente para HOY!)**

Esto lo leíste antes, pero quiero resaltarlo porque es crucial para la entrega de hoy:

*   **Informe y Video:** Ambos deben estar en "contenido adicional".
*   **SafeAssign:** ¡El informe debe tener **menos del 30% de similitud**! Si es más, la nota es cero. ¡Esto es muy serio!
*   **Penalización por retraso:** Si entregan 1 minuto tarde, ya empiezan a perder puntos. ¡Si se pasan de 30 minutos, es nota cero! Asegúrense de enviar *antes* de las 23:55.
*   **Vídeo:**
    *   Fecha máxima: Domingo (hoy) hasta las 23:59.
    *   Un solo integrante sube el informe y el link del video.
    *   El video en Drive con permiso para ver.
    *   **Contenido del informe:** Introducción, objetivos, marco teórico, citas/bibliografía, 2 ejercicios resueltos, 30% del programa (el flujograma es opcional para esta vez).
    *   **Contenido del video:** 4-10 minutos, mostrar interfaz, explicar teoría brevemente, **participación de todos**.

---

Sé que es mucha información, pero espero que ahora al menos tengas una idea clara de cada sección del documento y el porqué de esas fórmulas. Las fórmulas son las "instrucciones" que tu programa usará para mover los puntos de las figuras.

**Lo más importante ahora es:**
1.  **Habla con tu grupo:** Diles que ahora entiendes mejor el documento y que quieres ayudar a revisar los últimos puntos. Pregunta qué parte del informe o del video podrías revisar o preparar.
2.  **Concéntrate en el 30% del código:** Asegúrate de entender la lógica de la única transformación que ya tienen implementada.
3.  **Participa en el video:** Practica lo que vas a decir sobre la introducción, los objetivos o la breve explicación teórica.

¡No te sientas mal! Estás aprendiendo y esto es parte del proceso. Ahora tienes la información, ¡y eso es un gran paso! ¡Mucho éxito con la entrega de hoy! ¡Tú puedes! 👍