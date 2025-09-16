# 🚀 Guía Rápida de Proyectiles: El Secreto de los Dos Movimientos

Imagina que lanzas una pelota de béisbol. Su movimiento curvo y elegante es lo que llamamos "movimiento de proyectiles".

El truco para entender esto es darse cuenta de que la pelota está haciendo **dos cosas a la vez**:
1.  **Se mueve hacia adelante** (en horizontal).
2.  **Sube y luego baja** (en vertical).

La idea más importante de todo este tema es que **estos dos movimientos son totalmente independientes**. Lo que pasa en horizontal no afecta a lo vertical, y viceversa. ¡Son como dos juegos separados que ocurren al mismo tiempo!

---

## 🎯 Módulo 1: Las Reglas del Juego

### **Juego Horizontal (Eje X) → El Mundo del MRU 🚶‍♂️**
En el eje horizontal, ¡no hay gravedad que empuje o frene la pelota! Una vez que la lanzas, su velocidad hacia adelante no cambia (ignorando la resistencia del aire, claro).

*   **Tipo de Movimiento:** **MRU** (velocidad constante).
*   **Aceleración Horizontal (`a_x`):** Siempre es **CERO**.
*   **Velocidad Horizontal (`v_x`):** **NUNCA CAMBIA**. Es la misma al principio, en medio y al final.
*   **La ÚNICA Fórmula que usarás:** `x = v₀x * t` (distancia = velocidad horizontal × tiempo).

### **Juego Vertical (Eje Y) → El Mundo del MRUV 🎢**
En el eje vertical, la gravedad es la jefa. Siempre está tirando del objeto hacia abajo.

*   **Tipo de Movimiento:** **MRUV** (aceleración constante).
*   **Aceleración Vertical (`a_y`):** Es siempre la **gravedad (`g = -9,81 m/s²`)**. Es negativa porque apunta hacia abajo.
*   **Velocidad Vertical (`v_y`):** **SIEMPRE CAMBIA**. Empieza siendo grande hacia arriba, se hace cero en el punto más alto, y luego se vuelve grande hacia abajo.
*   **Las Fórmulas que usarás:** Son las mismas del MRUV que ya conoces, pero con la letra `y` en lugar de `x` y con `a = -9,81`.
    *   `v_y = v₀y + a_y*t`
    *   `y = y₀ + v₀y*t + (1/2)*a_y*t²`
    *   `v_y² = v₀y² + 2*a_y*Δy`

### **La Pieza Clave: El Tiempo (`t`) ⏳**
El **tiempo** es el **único valor que conecta los dos juegos**. El tiempo que la pelota pasa en el aire es el mismo para el movimiento horizontal y para el vertical. ¡El tiempo es el puente entre los dos mundos!

---

## 🔧 Módulo 2: Descomponiendo la Velocidad Inicial (El Primer Paso SIEMPRE)

Cuando lanzas algo con un ángulo (como en los ejercicios), la velocidad inicial (`v₀`) está "repartida" entre el movimiento horizontal y el vertical. Necesitamos saber cuánta velocidad le toca a cada uno.

Imagina la velocidad inicial como la diagonal de un rectángulo. Los lados de ese rectángulo son las velocidades horizontal (`v₀x`) y vertical (`v₀y`).

Para encontrarlas, SIEMPRE usarás estas dos fórmulas:

*   **Velocidad Horizontal Inicial (`v₀x`):** `v₀x = v₀ * cos(α₀)`
    *   (El `coseno` se usa para el lado que está "pegado" al ángulo).
*   **Velocidad Vertical Inicial (`v₀y`):** `v₀y = v₀ * sen(α₀)`
    *   (El `seno` se usa para el lado que está "opuesto" al ángulo).

*(Asegúrate de que tu calculadora esté en modo "DEG" para los grados)*

---

## 🛠️ Módulo 3: La Receta para Resolver CUALQUIER Problema de Proyectiles

Ahora sí, vamos a resolver el **Ejercicio 2 de la atleta** usando un método infalible.

**El Problema:** Una atleta lanza una bala con `v₀ = 12,0 m/s` y un ángulo `α₀ = 51,0°`. La bala golpea el suelo `2,08 s` después.

### **Paso 1: ¡No entres en pánico! Haz una lista de TODOS tus datos.**
Separa tus datos en dos columnas, una para cada "juego".

| Datos Generales | Juego Horizontal (MRU) | Juego Vertical (MRUV) |
| :--- | :--- | :--- |
| `v₀ = 12,0 m/s` | `v₀x = ?` | `v₀y = ?` |
| `α₀ = 51,0°` | `a_x = 0` | `a_y = -9,81 m/s²` |
| `t = 2,08 s` | `Δx = ?` (la distancia horizontal) | `Δy = ?` (la altura desde la que se lanzó) |
| | `v_x = ?` (velocidad horizontal final) | `v_y = ?` (velocidad vertical final) |

### **Paso 2: Calcula las velocidades iniciales (`v₀x` y `v₀y`).**
Este es siempre el primer cálculo que debes hacer.
*   `v₀x = v₀ * cos(α₀) = 12,0 * cos(51,0°) = 7,55 m/s`
*   `v₀y = v₀ * sen(α₀) = 12,0 * sen(51,0°) = 9,33 m/s`

¡Genial! Ya tenemos las piezas que nos faltaban.

### **Paso 3: Responde las preguntas una por una.**

**a) ¿Cuáles son las componentes de la velocidad al inicio y al final?**
*   **Al inicio:** ¡Ya las calculamos!
    *   `v₀x = 7,55 m/s`
    *   `v₀y = 9,33 m/s`
*   **Al final (justo antes de tocar el suelo):**
    *   La velocidad horizontal **NUNCA CAMBIA**, así que `v_x = v₀x = 7,55 m/s`.
    *   La velocidad vertical sí cambia. Usamos la fórmula del MRUV: `v_y = v₀y + a_y*t`.
        `v_y = 9,33 + (-9,81) * 2,08`
        `v_y = 9,33 - 20,40`
        `v_y = -11,1 m/s` (Tiene sentido que sea negativa, ¡está cayendo!)

**b) ¿Qué distancia horizontal (`Δx`) recorre la bala?**
*   Nos pasamos al "Juego Horizontal". La fórmula es `Δx = v₀x * t`.
*   `Δx = 7,55 * 2,08`
*   `Δx = 15,7 m`

**c) ¿Desde qué altura sobre el suelo se lanzó la bala?**
*   Esto es una pregunta del "Juego Vertical". Nos preguntan por la altura inicial (`y₀`). Podemos usar la fórmula de posición vertical, asumiendo que la posición final es el suelo (`y = 0`).
*   La fórmula es: `y = y₀ + v₀y*t + (1/2)*a_y*t²`.
*   `0 = y₀ + (9,33 * 2,08) + (1/2) * (-9,81) * (2,08)²`
*   `0 = y₀ + 19,4 - 21,2`
*   `0 = y₀ - 1,8`
*   `y₀ = 1,8 m` (Se redondea a `1,82 m` si usamos más decimales en los cálculos intermedios).

¡Y listo! Hemos resuelto todo el problema simplemente tratando los movimientos horizontal y vertical como dos problemas separados y más sencillos.
