El **Movimiento Circular** es la historia de todo lo que gira: una rueda de la fortuna, las aspas de un ventilador, un CD en un reproductor. Y aquí viene el gran secreto, la idea más importante de todas:

> **Este tema es un "remix" de lo que ya vimos (MRU y MRUV). Las reglas y las fórmulas son las MISMAS, pero con letras griegas para que se vea más cool.**

---

# 🎡 Guía Rápida de Movimiento Circular: ¡Lo Mismo, pero Girando!

Imagina que el movimiento en línea recta (MRU/MRUV) es como conducir por una autopista. El movimiento circular es como estar en una rueda de la fortuna. Las ideas son las mismas, solo cambia el escenario.

### **Módulo 1: Traduciendo el Idioma (La Piedra Rosetta de la Física)**

Para no confundirnos, los físicos usan letras diferentes para el movimiento circular. ¡Pero significan lo mismo!

| Mundo Recto (MRU/MRUV) | Símbolo | Mundo Circular (MCU/MCUV) | Traducción Sencilla |
| :--- | :---: | :--- | :--- |
| **Posición** (cuántos metros avanzaste) | **x** | **Posición Angular (θ)** | **Cuántos grados o "rebanadas de pizza" has girado.** Se mide en **radianes (rad)**. |
| **Velocidad** (metros por segundo) | **v** | **Velocidad Angular (ω)** | **Qué tan rápido estás girando.** Se mide en **rad/s**. (¡Las "rpm" son velocidad angular!). |
| **Aceleración** (cambio de velocidad) | **a** | **Aceleración Angular (α)** | **Qué tan rápido cambia tu velocidad de giro.** (Si aprietas el acelerador de la rueda de la fortuna). Se mide en **rad/s²**. |

¡Eso es todo! `x` se convierte en `θ`, `v` se convierte en `ω`, y `a` se convierte en `α`.

---

### **Módulo 2: Los Dos Tipos de Giro (¡Ya los conoces!)**

#### **1. MCU (Movimiento Circular Uniforme) 🎠**
*   **Traducción:** Es el primo hermano del **MRU**.
*   **¿Qué es?** El objeto gira a una **velocidad angular (ω) constante**. ¡No acelera ni frena!
*   **La Clave:** La aceleración angular es **CERO** (`α = 0`).
*   **La Fórmula (¡es la misma!):**
    *   MRU: `Δx = v * t`
    *   MCU: `Δθ = ω * t`

#### **2. MCUV (Movimiento Circular Uniformemente Variado) 🏎️**
*   **Traducción:** Es el primo hermano del **MRUV**.
*   **¿Qué es?** El objeto gira, pero su **velocidad angular (ω) cambia a un ritmo constante**.
*   **La Clave:** La aceleración angular (`α`) es **CONSTANTE** (un número que no cambia).
*   **Las Fórmulas (¡Son las mismas, pero traducidas!):**

| Fórmula del MRUV | Fórmula "Traducida" del MCUV |
| :--- | :--- |
| `v = v₀ + a*t` | `ω = ω₀ + α*t` |
| `Δx = v₀*t + (1/2)*a*t²` | `Δθ = ω₀*t + (1/2)*α*t²` |
| `v² = v₀² + 2*a*Δx` | `ω² = ω₀² + 2*α*Δθ` |
| `Δx = ((v₀ + v)/2) * t` | `Δθ = ((ω₀ + ω)/2) * t` |

Si sabes usar las de la izquierda, ¡ya sabes usar las de la derecha!

---

### **Módulo 3: El Puente entre Mundos (El Radio 'R')**

A veces queremos saber la velocidad "normal" (`v` en m/s) de un punto en el borde de algo que gira (como la punta de un aspa).

*   **La idea:** Un punto en el borde de un CD viaja más rápido que un punto cerca del centro, aunque ambos giran a la misma velocidad angular (`ω`).
*   **El Puente:** El radio (`R`) conecta el mundo angular con el mundo lineal.
    *   `v = ω * R` (Velocidad en el borde = Velocidad de giro × Radio)

---

### **🛠️ Módulo 4: Resolviendo el Ejercicio 1 (El Ventilador)**

Vamos a usar nuestra receta para resolver el problema del ventilador que se apaga.

**El Problema:** Un ventilador baja su velocidad de 500 rpm a 200 rpm en 4,00 s.

**Paso 1: ¡El paso más importante! Traducir las unidades.**
Las fórmulas de física no entienden "rpm" (revoluciones por minuto). Necesitamos traducirlas a `rad/s` (radianes por segundo).
*   **Factor de Traducción Mágico:** `1 rpm = (2π / 60) rad/s`
*   **Velocidad Inicial (`ω₀`):**
    `500 rpm * (2π / 60) = 52,36 rad/s`
*   **Velocidad Final (`ω`):**
    `200 rpm * (2π / 60) = 20,94 rad/s`

**Paso 2: Haz una lista de tus datos (ya traducidos).**
*   Velocidad angular inicial `ω₀ = 52,36 rad/s`
*   Velocidad angular final `ω = 20,94 rad/s`
*   Tiempo `t = 4,00 s`
*   **Pregunta (a):** ¿Cuál es la aceleración angular (`α`)?
*   **Pregunta (b):** ¿Cuál es el desplazamiento angular (`Δθ`)?

**Paso 3: Elige tu herramienta (la fórmula correcta).**
*   **Para (a), la aceleración angular (`α`):** Tenemos `ω`, `ω₀` y `t`. La fórmula perfecta es la primera de nuestra lista:
    > `ω = ω₀ + α*t`

*   **Para (b), el desplazamiento angular (`Δθ`):** Tenemos todo. La fórmula más fácil y directa (un atajo) es la cuarta:
    > `Δθ = ((ω₀ + ω)/2) * t`

**Paso 4: Resuelve.**
*   **Cálculo de (a):**
    `20,94 = 52,36 + α * 4,00`
    `20,94 - 52,36 = 4α`
    `-31,42 = 4α`
    `α = -31,42 / 4 = -7,85 rad/s²`
    *(Tiene sentido que sea negativa, ¡el ventilador está frenando!)*

*   **Cálculo de (b):**
    `Δθ = ((52,36 + 20,94) / 2) * 4,00`
    `Δθ = (73,3 / 2) * 4,00`
    `Δθ = 36,65 * 4,00`
    `Δθ = 146,6 rad` (Que se redondea a **147 rad**).

**Paso 5: ¡Celebra!**
Has resuelto un problema de movimiento circular. Simplemente tradujiste las unidades, elegiste la misma fórmula que usarías para un coche frenando, ¡y listo!