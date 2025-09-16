# 🚀 Guía Rápida de Cinemática: La Historia de Cómo se Mueven las Cosas

La **cinemática** es simplemente la parte de la física que describe el movimiento. No nos preguntamos *por qué* se mueven las cosas (eso viene después), solo nos interesa describir *cómo* se mueven: ¿qué tan rápido van?, ¿qué distancia recorren?, ¿aceleran o frenan?

---

## 🧱 Módulo 1: El Vocabulario Básico (Las Piezas del LEGO)

Antes de construir, necesitamos conocer nuestras piezas. Estos son los conceptos clave.

*   **Partícula 🤔:** En física, para simplificar, imaginamos que los objetos (un carro, una pelota, una persona) son un simple **punto**. A este punto lo llamamos partícula. Así no nos preocupamos por su forma o tamaño.

*   **Posición (x) 📍:** Es simplemente la ubicación de un objeto, como un pin en Google Maps. Se mide desde un punto de referencia que llamamos **origen (cero)**.

*   **Distancia (d) 🛣️:** Es la **longitud total** del camino que recorriste. Si vas de tu casa a la tienda y vuelves, la distancia es el camino de ida MÁS el camino de vuelta. ¡El cuenta-kilómetros de un coche mide la distancia!

*   **Desplazamiento (Δx) ✈️:** Es el cambio de tu posición. Es una flecha que va **en línea recta** desde donde empezaste hasta donde terminaste. Si vas de tu casa a la tienda y vuelves, tu punto de inicio y final es el mismo, ¡así que tu desplazamiento es CERO!

*   **Rapidez 🚗:** Es el número que ves en el velocímetro de un coche (`80 km/h`). Solo nos dice qué tan rápido vas, no le importa la dirección.

*   **Velocidad (v) 🧭:** Es la rapidez **MÁS la dirección**. Decir "80 km/h hacia el Norte" es una velocidad. En nuestros problemas, la dirección será simplemente "hacia la derecha" (positivo `+`) o "hacia la izquierda" (negativo `-`).

*   **Aceleración (a) 🔥:** Es el "pedal del acelerador" o el "freno". Mide **cuánto cambia la velocidad**.
    *   Si la velocidad aumenta, la aceleración es positiva.
    *   Si la velocidad disminuye (frenas), la aceleración es negativa.

### **Reglas de Redondeo (Cifras Significativas)**
Esto es solo para ser "honestos" con la precisión de nuestras medidas.
*   **Para Sumas y Restas:** El resultado tiene la **menor cantidad de decimales**.
    *   Ej: `15 m` (0 decimales) `+ 5,1 m` (1 decimal) `= 20,1 m`. El resultado debe tener 0 decimales, así que se redondea a **`20 m`**.
*   **Para Multiplicación y División:** El resultado tiene la **menor cantidad de cifras significativas**.
    *   Ej: `0,24` (2 c.s.) `x 10,8` (3 c.s.) `/ 2,150` (4 c.s.). El que menos tiene es 2.
    *   El resultado `1,097...` se redondea a **`1,1`** (que tiene 2 c.s.).

---

## 🚦 Módulo 2: Los Tipos de Movimiento (Las Reglas del Tráfico)

En este curso, solo nos importan dos tipos de movimiento en línea recta.

### **1. Movimiento Rectilíneo Uniforme (MRU) - "Modo Crucero"**
Este es el movimiento más fácil de todos.

*   **¿Qué es?** Un objeto se mueve en línea recta a **velocidad constante**.
*   **La Clave:** La **aceleración es CERO** (`a = 0`). No hay acelerador ni freno.
*   **Ejemplo:** Un coche en una autopista recta con el control de crucero activado.
*   **La ÚNICA Fórmula que necesitas:**
    > **`Δx = v * t`** (Distancia = velocidad × tiempo)

*   **Sus Gráficos:**
    *   **Posición vs. Tiempo:** Una línea recta inclinada.
    *   **Velocidad vs. Tiempo:** Una línea recta horizontal (¡porque no cambia!).

### **2. Movimiento Rectilíneo Uniformemente Variado (MRUV) - "Modo Acelerador/Freno"**
Este es el movimiento cuando la velocidad cambia.

*   **¿Qué es?** Un objeto se mueve en línea recta, pero su velocidad cambia a un ritmo constante.
*   **La Clave:** La **aceleración es CONSTANTE** (por ejemplo, `a = 2 m/s²` o `a = -9,8 m/s²`).
*   **Ejemplo:** Dejar caer una pelota (la gravedad la acelera constantemente) o un coche que acelera para entrar en la autopista.
*   **Las Fórmulas (Tu "Caja de Herramientas"):** No te asustes, no tienes que usarlas todas a la vez. Cada una sirve para una situación diferente.

    | Fórmula | ¿Cuándo la uso? |
    | :--- | :--- |
    | **`v = v₀ + a*t`** | Cuando **NO sabes (o no te importa)** la distancia recorrida. |
    | **`Δx = v₀*t + (1/2)*a*t²`** | Cuando **NO sabes (o no te importa)** la velocidad final. |
    | **`v² = v₀² + 2*a*Δx`** | La "fórmula sin tiempo". Úsala cuando el problema **NO te da (ni te pide)** el tiempo. |

    *(`v₀` es la velocidad inicial, con la que empieza el movimiento)*

*   **Sus Gráficos:**
    *   **Posición vs. Tiempo:** Una curva (parábola).
    *   **Velocidad vs. Tiempo:** Una línea recta inclinada (¡porque cambia constantemente!).
    *   **Aceleración vs. Tiempo:** Una línea recta horizontal (¡porque es constante!).

---

## 🛠️ Módulo 3: Cómo Resolver CUALQUIER Problema (La Receta)

Sigue estos 5 pasos y podrás resolver casi cualquier ejercicio. Usemos el **Ejercicio 2 de la conductora** como ejemplo.

**Paso 1: ¡No entres en pánico! Lee y dibuja.** 📝
Dibuja un cochecito. Está frenando. La flecha de la aceleración va para atrás.

**Paso 2: Haz una lista de tus datos.** 📋
¿Qué me dice el problema?
*   Aceleración: `a = -2,5 m/s²` (negativa porque está frenando)
*   Tiempo: `t = 4,0 s`
*   Distancia: `Δx = 20 m`
*   Límite de velocidad de la zona: `8,3 m/s`
*   **¿Qué me pregunta?** ¿Cuál era la velocidad del coche cuando empezó a frenar (`v₀`)? ¿Iba demasiado rápido?

**Paso 3: Elige tu herramienta.** 🔧
Mira tu lista de datos: tienes `a`, `t` y `Δx`, y quieres `v₀`.
Ahora mira tus fórmulas del MRUV. ¿Hay alguna que no use la velocidad final (`v`)? ¡Sí!

> **`Δx = v₀*t + (1/2)*a*t²`**

**Paso 4: Resuelve la ecuación (con calma).** 🧮
*   Pon los números en la fórmula: `20 = v₀ * (4,0) + (1/2) * (-2,5) * (4,0)²`
*   Simplifica: `20 = 4v₀ + (1/2) * (-2,5) * 16`
*   Simplifica más: `20 = 4v₀ - 20`
*   Despeja `v₀`: `20 + 20 = 4v₀` → `40 = 4v₀`
*   **Resultado:** `v₀ = 10 m/s`

**Paso 5: Responde la pregunta.** 💡
*   La velocidad inicial de la conductora era de **10 m/s**.
*   El límite de velocidad era **8,3 m/s**.
*   **Conclusión:** Sí, la aseguradora tiene razón. La conductora superaba la velocidad máxima permitida cuando empezó a frenar.
