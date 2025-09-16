**1. Entendiendo el Proyecto 1: Transformaciones Lineales**

Tu proyecto trata sobre la aplicación de **transformaciones lineales** a figuras geométricas simples en un plano. En esencia, vas a tomar una figura (como un triángulo o un cuadrilátero) y la vas a mover, girar, voltear o cambiar de tamaño en el plano cartesiano usando matemáticas.

Aquí te explico los conceptos clave que tu programa debe manejar, basándome en los documentos que adjuntaste:

*   **Representación de Figuras:** Tu programa debe poder "dibujar" (representar) triángulos y cuadriláteros. Esto se hace definiendo las figuras como un conjunto de puntos (vértices) en el plano. Por ejemplo, un triángulo podría ser `{(x1, y1), (x2, y2), (x3, y3)}`.
*   **Transformaciones a Implementar:** Debes aplicar los siguientes tipos de transformaciones lineales:
    *   **Rotación:** Girar una figura alrededor de un punto (un centro de rotación) en sentido horario o antihorario. El documento "Informe del Trabajo Grupal" explica la representación matemática para rotar alrededor del origen y de un punto arbitrario [2, p. 5].
    *   **Reflexión:** "Voltear" una figura como si se viera en un espejo, respecto a una línea (eje x, eje y, el origen, o una recta arbitraria). El informe también detalla las matrices de reflexión para el eje X, el eje Y y la recta y=x [2, p. 6].
    *   **Homotecia:** Cambiar el tamaño de una figura (agrandarla o reducirla) con respecto a un punto fijo (centro de homotecia) y un factor de escala. El informe explica cómo hacerlo con centro en el origen y en un punto arbitrario [2, p. 6].
*   **Transformación Personalizada:** El programa también debe permitir al usuario ingresar su propia matriz de transformación. Esto es para explorar efectos más allá de las transformaciones básicas.
*   **Visualización:** Debes mostrar tanto la figura original como la figura transformada al mismo tiempo, para que el usuario pueda ver el efecto de la transformación.
*   **Verificación de Isometría:** Una isometría es una transformación que conserva las longitudes y las áreas de las figuras (es decir, la figura se mueve o gira, pero no cambia de tamaño ni de forma). Tu programa debe verificar si la transformación aplicada es una isometría.

**En resumen, para la parte conceptual, el "Informe del Trabajo Grupal" (las páginas 3 a 6 principalmente) es tu mejor amigo. Ahí se explica qué es cada transformación y cómo se representa matemáticamente.**

---

**2. Desglosando el Primer Entregable (Semana 3): ¡Lo que hay que hacer AHORA!**

Para el avance de la Semana 3, necesitas preparar dos cosas principales: un **Informe en PDF** y un **Video**. Aquí te detallo cada requisito, combinando la rúbrica, el documento de avances y el anuncio del profesor:

**A. Informe en PDF (Máximo 4 puntos)**

*   **Contenido Mínimo Requerido (para lograr el puntaje completo):**
    *   **Introducción:** Presentar el proyecto, su importancia y lo que se busca lograr.
    *   **Objetivos Generales y Específicos:** Qué quieres lograr con el proyecto en general y en detalle. (Puedes encontrar ejemplos en el "Informe del Trabajo Grupal" adjunto [2, p. 3-4]).
    *   **Marco Teórico:** Explicar los conceptos matemáticos de las transformaciones lineales (rotación, reflexión, homotecia, matrices de transformación). Esto debe ser acorde a las referencias mencionadas. Usa las secciones 3.1, 3.2, 3.3, 3.4 del informe grupal para guiarte [2, p. 4-6].
    *   **Citas y Bibliografía:** Debes citar adecuadamente las fuentes en tu informe y tener una bibliografía con un mínimo de **2 referencias de libros**, en formato APA. Las referencias bibliográficas del "Informe del Trabajo Grupal" pueden ser un buen punto de partida [2, p. 8].
    *   **2 Ejercicios Resueltos y Tipeados:** Incluye dos ejemplos que ilustren el funcionamiento de tu proyecto. Deben estar bien explicados y con las ecuaciones tipeadas (no como imágenes). El documento "Informe del Trabajo Grupal" tiene ejemplos resueltos en las páginas 7 y 8 que puedes usar como modelo [2, p. 7-8].
    *   **30% del Programa:** Incluye el código del 30% del programa.
        *   **¿Qué significa "30% del programa" para Proyecto 1?** El documento "PROYECTOS - AVANCE AL 30%" especifica:
            *   Permitir representar figuras simples (triángulos, cuadriláteros) como conjuntos de puntos.
            *   NO siempre debe ser el mismo triángulo o cuadrilátero.
            *   Permitir realizar **al menos una de las transformaciones** (rotación, reflexión o homotecia), aunque no esté completa como se pide para el proyecto final.
            *   *La validación de este 30% se apreciará en el video.*
    *   **Flujograma (Opcional por ahora):** No es obligatorio para esta entrega, pero sí para la segunda.
*   **Importante sobre el Informe:**
    *   Pasará por SafeAssign: debe tener **menos del 30% de similitud** con otros trabajos. ¡Más del 30% significa nota cero! Esto es crucial, así que asegúrate de redactar con tus propias palabras y citar correctamente [Anuncio del profesor].

**B. Video (Máximo 1 punto)**

*   **Duración:** No menor de 4 minutos y no mayor de 10 minutos.
*   **Contenido:**
    *   **Interfaz del Programa:** Muestra y explica cómo funciona la interfaz de tu programa (incluso con el 30% de avance).
    *   **Teoría Breve:** Explica brevemente la parte teórica que están utilizando en el programa (los conceptos de transformaciones lineales, rotación, etc.).
    *   **Participación:** ¡Todos los integrantes deben participar! [Anuncio del profesor].
*   **Forma de Entrega del Video:**
    *   Súbelo a un Drive con permisos para que el profesor pueda visualizarlo [Anuncio del profesor].
    *   Comparte el enlace en el apartado de "contenido adicional" en la entrega del campus [Anuncio del profesor].

**C. Aspectos Clave de la Entrega (¡MUY IMPORTANTE!)** [Anuncio del profesor]

*   **Fecha Límite:** Domingo de la tercera semana hasta las **23:59 horas**. ¡Hoy mismo!
*   **Entrega:** Solo **UN integrante** por grupo sube el informe (PDF) y el link del video en "contenido adicional".
*   **Penalización por Retraso:**
    *   Hasta 30 minutos después de la fecha límite: **-1 punto por cada 10 minutos de retraso**.
    *   Más de 30 minutos de retraso: ¡**Nota cero**!
    *   Toma precauciones y envía a tiempo.

---

**3. ¿Qué hacer para no sentirte perdido y avanzar?**

1.  **Revisa el "Informe del Trabajo Grupal":** Empieza por leer las secciones de **Introducción, Objetivos** (páginas 3-4) y el **Marco Teórico** (páginas 4-6). Esto te dará una base sólida del tema y las fórmulas matemáticas que necesitas.
2.  **Enfócate en una transformación para el 30% del código:** Como el "avance al 30%" pide "al menos una de las transformaciones", puedes centrarte en la Rotación o la Reflexión, que son las primeras que se explican en el marco teórico y tienen ejemplos claros. Intenta entender cómo aplicar la matriz de rotación o reflexión a los puntos de tu figura.
3.  **Comunícate con tu grupo:** No tengas miedo de decirles a tus compañeros que te sientes perdido. Ellos ya han avanzado y pueden explicarte lo que han hecho, compartir el código del 30% que ya tienen, y asignarte tareas específicas para que puedas contribuir al informe o al video. ¡El trabajo en equipo es clave!
4.  **Crea una lista de verificación:** Usa los puntos que te he dado en la sección "Desglosando el Primer Entregable" como una lista. Marca cada ítem a medida que lo completes. Esto te dará una sensación de progreso y control.
5.  **Para el video, céntrate en lo que ya tienen:** Si ya tienen el 30% del código funcionando con al menos una transformación, concéntrense en mostrar esa funcionalidad y explicar brevemente cómo funciona matemáticamente. No tiene que ser perfecto, solo cumplir los requisitos de la rúbrica para el avance del 30%.
6.  **¡No te desesperes!** Es un curso nuevo y es normal no entender todo a la primera. Lo importante es que estás buscando ayuda y estás dispuesto a aprender. ¡Tus compañeros y tu esfuerzo te ayudarán a salir adelante!

Sé que el tiempo es muy limitado hoy. Mi mejor consejo es que te sientes con tus compañeros de inmediato, pídeles que te expliquen lo que ya tienen del código y el informe. Divide las tareas de última hora para el informe (como redactar tu parte de la introducción o los objetivos, revisar las referencias) y practica lo que dirás en el video.

¡Mucho ánimo! Vas a poder con esto.