### **Tu Guía de Estudio (Versión con Código 💻) para la Semana 1**

---

### **1. Introducción: De Datos Crudos a Programas Inteligentes**

La idea central es que tomamos datos sin procesar y usamos **algoritmos** para manipularlos dentro de **estructuras de datos** y así generar información útil.

*   **Algoritmo en Acción:** Un algoritmo es una receta. Aquí tienes el código de un algoritmo simple que calcula el promedio de los números en un arreglo, tal como se muestra en tus diapositivas.

    ```cpp
    #include <iostream>
    #include <vector> // Usaremos un vector, que es como un arreglo dinámico.

    // ALGORITMO para calcular el promedio
    // Input: un vector de números enteros (datos)
    // Output: el promedio (información)
    double calcularPromedio(const std::vector<int>& arreglo) {
        int sum = 0;
        int n = arreglo.size(); // Obtenemos la cantidad de elementos

        if (n == 0) {
            return 0; // Para evitar división por cero
        }

        // Este bucle es el corazón del algoritmo
        for (int i = 0; i < n; i++) {
            sum = sum + arreglo[i];
        }

        // El 'double' asegura que la división sea con decimales
        double promedio = static_cast<double>(sum) / n;

        return promedio;
    }

    int main() {
        std::vector<int> mis_numeros = {10, 20, 30, 40, 50}; // Estructura de Datos
        double resultado = calcularPromedio(mis_numeros);
        std::cout << "El promedio es: " << resultado << std::endl; // Muestra 30
        return 0;
    }
    ```    Aquí, `mis_numeros` es la **estructura de datos** (un vector) que organiza nuestros **datos**. La función `calcularPromedio` es el **algoritmo** que los procesa.

---

### **2. Tipos de Datos Abstractos (TDA): El Muro entre el Piloto y el Motor**

Un TDA define **qué** puedes hacer, pero oculta **cómo** lo hace. Esto se llama **abstracción**. En C++, esto se logra perfectamente con archivos de cabecera (`.h`) y de implementación (`.cpp`).

*   **Ejemplo de un TDA "BolsaSimple":** Imagina que quieres una "bolsa" donde solo puedes `agregar` elementos y ver `cuantosHay`.

    **Paso 1: La Interfaz (El "Qué") - `BolsaSimple.h`**
    Este es el "manual del piloto". Cualquiera que incluya este archivo sabe qué operaciones están disponibles.

    ```cpp
    // BolsaSimple.h - La interfaz pública de nuestro TDA
    #ifndef BOLSASIMPLE_H
    #define BOLSASIMPLE_H

    #include <vector>
    #include <string>

    class BolsaSimple {
    public:
        // Constructor: se llama al crear un objeto BolsaSimple
        BolsaSimple();

        // Operaciones públicas (lo que el usuario puede hacer)
        void agregar(const std::string& item);
        int cuantosHay() const; // 'const' significa que este método no modifica la bolsa

    private:
        // Detalles de implementación (ocultos al usuario)
        std::vector<std::string> items; // ¡El usuario no necesita saber que usamos un vector!
    };

    #endif
    ```

    **Paso 2: La Implementación (El "Cómo") - `BolsaSimple.cpp`**
    Este es el "motor". Aquí está la lógica interna que el usuario no ve.

    ```cpp
    // BolsaSimple.cpp - La implementación de las operaciones
    #include "BolsaSimple.h"

    BolsaSimple::BolsaSimple() {
        // El constructor puede estar vacío o inicializar algo
    }

    void BolsaSimple::agregar(const std::string& item) {
        items.push_back(item); // Usamos el método push_back del vector
    }

    int BolsaSimple::cuantosHay() const {
        return items.size(); // Usamos el método size del vector
    }
    ```

    **Paso 3: El Uso - `main.cpp`**
    El programa principal solo interactúa con la interfaz pública. No tiene idea de que dentro hay un `std::vector`.

    ```cpp
    #include <iostream>
    #include "BolsaSimple.h" // Solo incluimos la interfaz

    int main() {
        BolsaSimple mi_bolsa; // Creamos un objeto de nuestro TDA

        mi_bolsa.agregar("Manzana");
        mi_bolsa.agregar("Platano");

        std::cout << "En la bolsa hay " << mi_bolsa.cuantosHay() << " items." << std::endl;
        // Salida: En la bolsa hay 2 items.

        return 0;
    }
    ```

---

### **3. Análisis de Algoritmos y Big O: El Código bajo el Microscopio 🔬**

Vamos a analizar el costo (tiempo de ejecución) de fragmentos de código, aplicando las reglas de tus diapositivas.

#### **Regla 1: Sentencias Secuenciales → O(1) - Constante**
Cada operación simple (asignación, operación aritmética, acceso a un arreglo) tiene un costo constante.

```cpp
// Tiempo Detallado: 1 (i=x) + 3 (a=b+2*3) + 3 (v[i]=v[0]) = 7 operaciones
// Tiempo Asintótico (Big O): O(1) -> El tiempo no depende del tamaño de ninguna entrada 'n'.
void sentencias_secuenciales() {
    int i, x, a, b;
    int v[10];
    // ... asumimos que las variables tienen valores ...

    i = x;                  // Costo: 1 (una asignación)
    a = b + 2 * 3;          // Costo: 3 (una multiplicación, una suma, una asignación)
    v[i] = v[0];            // Costo: 3 (un acceso, otro acceso, una asignación)
}
```

#### **Regla 2: Bucles Simples → O(n) - Lineal**
El tiempo de ejecución crece linealmente con el tamaño de la entrada `n`.

```cpp
// Tiempo Detallado: 1 (i=0) + n+1 (i<n) + n (i++) + n * (3 + 1)
// ==> 1 + n + 1 + n + 4n = 6n + 2
// Tiempo Asintótico (Big O): O(n) -> Nos quedamos con el término dominante (n).
void bucle_simple(int n) {
    long long sum = 0;
    // El bucle se ejecuta 'n' veces
    for (int i = 0; i < n; ++i) {
        sum = sum + i;      // Costo interno: ~2 (suma, asignación)
        std::cout << sum;   // Costo interno: ~1 (operación de salida)
    }
}
```

#### **Regla 3: Bucles Anidados → O(n²) - Cuadrático**
Un bucle dentro de otro. El costo se multiplica.

```cpp
// Tiempo Asintótico (Big O): O(n * n) = O(n²)
// El bucle externo corre 'n' veces.
// Por CADA una de esas veces, el bucle interno corre 'n' veces.
void bucles_anidados(int n) {
    int contador = 0;
    for (int i = 0; i < n; ++i) {       // Se ejecuta n veces
        for (int k = 0; k < n; ++k) {   // Se ejecuta n veces por cada 'i'
            contador++;                 // Esta línea se ejecuta n * n veces
        }
    }
}
```

#### **Regla 4: Bucles Consecutivos → O(n)**
Se suman los costos, pero en Big O nos quedamos con el más grande.

```cpp
// Costo total: O(n) + O(m)
// Si n es mucho más grande que m, la complejidad es O(n).
// Si m es mucho más grande que n, la complejidad es O(m).
void bucles_consecutivos(int n, int m) {
    // Primer bloque: O(n)
    for (int i = 0; i < n; ++i) {
        // ... operaciones de costo O(1) ...
    }

    // Segundo bloque: O(m)
    for (int j = 0; j < m; ++j) {
        // ... operaciones de costo O(1) ...
    }
}
```

#### **Regla 5: Condicionales `if-else` → O(max(bloque_if, bloque_else))**
Se toma el costo del peor caso, es decir, el bloque que sea más lento.

```cpp
// En el peor caso, la condición 'condicion' es verdadera y se ejecuta el bucle.
// Por lo tanto, el tiempo asintótico es O(n).
void condicional(bool condicion, int n) {
    if (condicion) {
        // Bloque IF: Tiene una complejidad de O(n)
        for (int i = 0; i < n; ++i) {
            std::cout << i;
        }
    } else {
        // Bloque ELSE: Tiene una complejidad de O(1)
        std::cout << "Hola";
    }
}
```

---

### **4. Programación Genérica (Templates): Código Reutilizable ♻️**

Escribir una función para cada tipo de dato es ineficiente. Los `templates` nos permiten escribir una única función "genérica".

**El Problema: Código Repetitivo**

```cpp
// Tres funciones que hacen exactamente lo mismo con tipos diferentes. ¡Mala práctica!
int sumaInt(int a, int b) { return a + b; }
float sumaFloat(float a, float b) { return a + b; }
double sumaDouble(double a, double b) { return a + b; }
```

**La Solución: Templates**

```cpp
#include <iostream>

// Con 'template<typename T>', creamos una plantilla.
// 'T' puede ser cualquier tipo: int, float, double, etc.
template<typename T>
T suma(T a, T b) {
    return a + b;
}

int main() {
    // El compilador crea las versiones necesarias automáticamente.
    // Versión para enteros (int)
    std::cout << "Suma de enteros: " << suma<int>(5, 10) << std::endl;

    // Versión para flotantes (float)
    std::cout << "Suma de floats: " << suma<float>(3.5f, 2.2f) << std::endl;

    // Versión para dobles (double)
    std::cout << "Suma de doubles: " << suma<double>(10.5, 20.75) << std::endl;

    // A veces, el compilador puede incluso inferir el tipo
    std::cout << "Suma inferida: " << suma(100, 200) << std::endl; // Infiere <int>

    return 0;
}
```
