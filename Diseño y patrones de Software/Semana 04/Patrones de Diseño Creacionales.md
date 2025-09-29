¡Absolutamente! Hemos recorrido un largo camino en la Unidad 1, desde los principios de diseño hasta las herramientas de modelado como UML. Ahora, este documento nos lleva al siguiente nivel práctico: **los Patrones de Diseño Creacionales de la "Gang of Four" (GoF)**.

Este es uno de los temas más emocionantes porque aquí es donde dejas de pensar en "reglas" (como SOLID) y empiezas a usar "recetas" probadas y comprobadas para construir tu software. ¡Vamos a desglosar estas recetas para que puedas empezar a "cocinar" tu proyecto CliniScan de manera profesional! 🧑‍🍳

---

# 🏭 Tu Guía Completa de "Diseño y Patrones de Software" (1ASI720) - **Unidad 1: Los Cimientos (Parte 7: Patrones de Diseño Creacionales)**

El objetivo final de esta unidad es que sepas **elaborar y comunicar artefactos de diseño** aplicando principios y patrones. Este documento se enfoca en la primera categoría de patrones GoF: los **Creacionales**.

## 🤔 1. ¿Qué Son los Patrones de Diseño Creacionales?

Como su nombre indica, estos patrones se centran en un problema fundamental en la programación orientada a objetos: **la creación de objetos**.

*   **El Problema:** A veces, crear un objeto directamente con `new MiClase()` es demasiado rígido. ¿Qué pasa si la clase que necesitas crear depende de la configuración del sistema? ¿O si el objeto es muy complejo y requiere muchos pasos para inicializarse? Hacerlo directamente puede generar un código muy acoplado y difícil de mantener.
*   **La Solución (Patrones Creacionales):** Proporcionan un **mecanismo uniforme, simple y controlado para crear objetos**.
    *   **Encapsulan la lógica de creación:** Esconden los detalles de qué clases se instancian y cómo se crean.
    *   **Fomentan el uso de interfaces:** Reducen el acoplamiento porque tu código no depende de clases concretas, sino de abstracciones.

**Analogía:** Imagina que vas a un restaurante de lujo. Tú no vas a la cocina a mezclar los ingredientes para tu plato. Tú le das tu pedido al mesero (la "interfaz"), y la cocina (el "patrón creacional") se encarga de crear el plato perfecto para ti, con todos sus detalles. Los patrones creacionales son como la "cocina" de tu software.

El documento se enfoca en tres patrones creacionales clave: **Builder, Factory Method y Singleton**.

---

## 🏗️ 2. El Patrón Builder (El Constructor de Objetos Complejos)

*   **Intención (¿Qué hace?):** "Separa la construcción de un objeto complejo de su representación."
*   **Problema que Resuelve:** Cuando tienes un objeto que necesita muchos pasos o configuraciones para ser creado (por ejemplo, tiene muchos atributos que deben ser establecidos). Si lo creas con un constructor con muchos parámetros, se vuelve confuso y propenso a errores.
*   **La Idea Principal:** El patrón Builder te permite construir un objeto complejo **paso a paso**. Separa el "qué" se construye (el producto final) del "cómo" se construye (los pasos para ensamblarlo).
*   **Analogía Tecnológica (para CliniScan):**
    Imagina que en CliniScan necesitas crear un objeto `PreInformeMedico`. Este objeto podría ser muy complejo:
    *   `setDatosPaciente(paciente)`
    *   `setDatosEstudio(estudio)`
    *   `setResultadosIA(resultados)`
    *   `setSugerenciaDerivacion(sugerencia)`
    *   `setObservacionesMedico(observaciones)`
    *   `setFechaGeneracion(fecha)`
    Crear esto con un solo constructor sería un caos. Un Builder te permitiría crearlo paso a paso de forma clara: `new PreInformeBuilder().conDatosPaciente(p).conResultadosIA(r).construir()`.

### Los Actores del Patrón Builder:

1.  **Builder (Interfaz):** Es la interfaz que define los pasos de construcción (ej. `buildBody()`, `insertWheels()`).
2.  **ConcreteBuilder (Constructor Concreto):** Es la clase que implementa la interfaz `Builder` y sabe cómo construir una parte específica del producto. (ej. `Car` y `MotorCycle` en el ejemplo de las diapositivas).
3.  **Product (Producto):** Es el objeto complejo que se está construyendo.
4.  **Director (Director):** Es una clase opcional que conoce la secuencia de pasos de construcción para crear un producto. Le dice al `Builder` qué hacer y en qué orden.

### ¿Cómo funciona el ejemplo de las diapositivas?
1.  **`IBuilder`** es la interfaz que dice que cualquier "constructor" debe saber cómo `buildBody`, `insertWheels`, `addHeadlights` y `getVehicle`.
2.  **`Car` y `MotorCycle`** son los `ConcreteBuilder`. Cada uno sabe cómo implementar esos pasos para su tipo de vehículo (un coche tiene 4 ruedas, una moto tiene 2).
3.  **`Product`** es el vehículo final, una lista de las partes que se han añadido.
4.  **`Director`** tiene un método `construct` que toma un `IBuilder` y sigue la secuencia de pasos para construir el vehículo, sin importar si es un coche o una moto.

### Consecuencias (¿Qué ganas?):
*   **Diferentes representaciones:** Puedes usar el mismo proceso de construcción para crear diferentes versiones del producto.
*   **Código más limpio:** Aísla el código de construcción del código de representación.
*   **Control fino:** Tienes un control total sobre cada paso del proceso de construcción.

---

## 🏭 3. El Patrón Factory Method (El Delegador de Creación)

*   **Intención (¿Qué hace?):** "Define una interfaz para crear un objeto, pero deja que las subclases decidan qué clase instanciar."
*   **Problema que Resuelve:** Cuando una clase necesita crear un objeto, pero no puede saber *qué tipo específico* de objeto crear de antemano. La decisión de qué objeto crear se delega a las subclases.
*   **La Idea Principal:** La clase "padre" (Creator) define un "método de fábrica" (`factoryMethod()`) que sus clases "hijas" (ConcreteCreator) deben implementar. La clase padre usa este método para crear el objeto, sin saber qué tipo de objeto están creando sus hijas.
*   **Analogía Tecnológica (para CliniScan):**
    Imagina que CliniScan necesita generar diferentes tipos de **notificaciones**: una por `Email`, otra por `SMS`, otra por `Push Notification` en la app.
    *   Podrías tener una clase abstracta `NotificationCreator` con un método abstracto `createNotification()`.
    *   Luego, tendrías subclases como `EmailNotificationCreator`, `SMSNotificationCreator`, etc.
    *   Cada una implementaría `createNotification()` para crear el tipo correcto de objeto (`EmailNotification`, `SMSNotification`).
    *   El código principal usaría un `NotificationCreator` sin saber si es de email o SMS, y simplemente llamaría a su método de envío, que internamente usaría `createNotification()`.

### Los Actores del Patrón Factory Method:

1.  **Product (Interfaz):** La interfaz para los objetos que el método de fábrica crea.
2.  **ConcreteProduct (Producto Concreto):** Las clases que implementan la interfaz `Product`.
3.  **Creator (Creador):** La clase que declara el `factoryMethod()` que devuelve un objeto de tipo `Product`.
4.  **ConcreteCreator (Creador Concreto):** La clase que sobrescribe el `factoryMethod()` para devolver una instancia de un `ConcreteProduct`.

### ¿Cómo funciona el ejemplo de las diapositivas (Botones)?
1.  **`Button`** es la interfaz `Product`. Dice que todos los botones deben tener `render()` y `onClick()`.
2.  **`HtmlButton`** y **`WindowsButton`** son los `ConcreteProduct`. Cada uno sabe cómo renderizarse a sí mismo.
3.  **`Dialog`** es la clase abstracta `Creator`. Tiene un método `renderWindow()` que usa un `Button`, y un método abstracto `createButton()`.
4.  **`HtmlDialog`** y **`WindowsDialog`** son los `ConcreteCreator`. Cada uno implementa `createButton()` para devolver el tipo de botón que le corresponde.
5.  El código cliente decide qué `Dialog` usar (dependiendo del sistema operativo) y luego simplemente llama a `dialog.renderWindow()`, sin saber ni preocuparse por qué tipo de botón se está usando.

### Consecuencias (¿Qué ganas?):
*   **Desacoplamiento:** Elimina la necesidad de que tu código principal esté "atado" a clases específicas de productos. Tu código solo trabaja con la interfaz del producto. ¡Esto es el Principio de Inversión de Dependencias (D de SOLID) en acción!

---

## 👤 4. El Patrón Singleton (El Objeto Único y Especial)

*   **Intención (¿Qué hace?):** "Asegura que una clase solo tenga una única instancia, y proporciona un punto de acceso global a ella."
*   **Problema que Resuelve:** Cuando necesitas que haya exactamente **un solo objeto de una clase** en todo tu sistema. Por ejemplo, un gestor de configuración, un servicio de logging, o un pool de conexiones a la base de datos.
*   **La Idea Principal:**
    1.  Haces el **constructor privado** para que nadie más pueda crear instancias de la clase.
    2.  Creas un **método estático público** (generalmente llamado `getInstance()`) que se encarga de crear la única instancia la primera vez que se llama, y de devolver esa misma instancia en todas las llamadas posteriores.
*   **Analogía Tecnológica (para CliniScan):**
    Imagina que en CliniScan necesitas un **servicio de logging** que escriba todos los eventos importantes del sistema en un solo archivo. No querrías tener múltiples "loggers" escribiendo en el mismo archivo al mismo tiempo, ¡sería un caos!
    *   Usarías el patrón Singleton para crear una clase `GlobalLogger` que asegure que solo hay una instancia de logger en toda la aplicación. Cualquier parte del sistema que necesite registrar un evento llamaría a `GlobalLogger.getInstance().log("Evento importante")`.

### Los Actores del Patrón Singleton:

1.  **Singleton:** La propia clase que se implementa a sí misma. Tiene una instancia estática de sí misma, un constructor privado y un método estático `getInstance()`.

### ¿Cómo funciona el ejemplo de las diapositivas (Java)?
*   Las diapositivas muestran varias formas de implementarlo en Java, pero la idea central es la misma:
    *   `private static MySingleton instance;` (La única instancia)
    *   `private MySingleton() {}` (El constructor privado)
    *   `public static MySingleton getInstance() { ... }` (El método de acceso global)
*   **Nota sobre Concurrencia (thread safety):** Algunas de las implementaciones que se muestran (con `synchronized` o `volatile`) son para asegurar que el patrón funcione correctamente en entornos con múltiples hilos de ejecución, donde dos hilos podrían intentar crear la instancia al mismo tiempo. ¡Es una consideración importante en sistemas reales!

### Consecuencias (¿Qué ganas?):
*   **Acceso controlado:** Tienes un control total sobre cómo y cuándo se accede a la única instancia.
*   **Evita variables globales:** Es más elegante que tener una variable global para el objeto.
*   **Cuidado:** A veces, el patrón Singleton puede ser mal utilizado y actuar como una "variable global glorificada", lo que puede dificultar las pruebas unitarias y crear dependencias ocultas. ¡Úsalo con sabiduría!

---

## 🚨 Errores Comunes y Consejos con los Patrones Creacionales:

*   **Builder vs. Factory:** A veces se confunden.
    *   Usa **Builder** cuando necesitas crear un objeto **complejo paso a paso**, y el proceso de construcción es el mismo para diferentes representaciones.
    *   Usa **Factory Method** cuando una clase no puede anticipar el tipo de objeto que debe crear, y **delega esta responsabilidad a sus subclases**.
*   **Singleton en exceso:** No todo lo que necesitas una vez es un Singleton. **Consejo:** Úsalo para recursos que son *verdaderamente globales y únicos por naturaleza*, como un gestor de configuración, un logger o un pool de conexiones.
*   **No usar interfaces con Factories:** El poder del Factory Method viene de que tu código trabaja con la interfaz del producto, no con la clase concreta. ¡No te saltes esa parte!

---

¡Felicidades! Has completado el recorrido por los Patrones Creacionales. Ahora tienes en tu arsenal las "recetas" para crear objetos de forma flexible y controlada. Estos patrones son fundamentales para construir software que sea fácil de mantener y de extender.

¡Intenta pensar cómo podrías aplicar estos patrones en tu proyecto CliniScan! Esto no solo te ayudará a entenderlos mejor, sino que también mejorará enormemente la calidad de tu diseño. ¡Gran trabajo! ✨