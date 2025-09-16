### **Tu Guía de Estudio para la Semana 1, Sesión 3: Cadenas, Registros y Objetos 🧱**

---

### **1. Cadenas de Caracteres: Los Dos Mundos del Texto en C++ 📜**

El texto es esencial en casi cualquier programa. C++ te ofrece dos formas de manejarlo: la "vieja escuela" heredada de C y la forma moderna y segura de C++. Es crucial que entiendas ambas.

#### **A) Cadenas Estilo C (`char*` o arreglos de `char`)**

Piensa en esto como la forma manual y de bajo nivel de manejar texto.

*   **¿Qué son?** Son simplemente un **arreglo de caracteres**. La gran regla es que **siempre deben terminar con un carácter especial nulo `\0`**. Este carácter le dice al programa dónde termina la cadena.
*   **¡Consideración Clave para el Examen!** Si una palabra tiene `N` letras (ej: "HOLA" tiene 4), necesitas un arreglo de tamaño `N+1` para guardarla, porque el espacio extra es para el `\0`. Así, "HOLA" se guarda en memoria como `['H', 'o', 'l', 'a', '\0']`.
*   **Riesgos y Responsabilidades:**
    1.  **Manejo Manual de Memoria:** Si usas `char*` con `new`, tú eres el responsable de liberar la memoria con `delete[]`. Olvidarte de hacerlo causa "fugas de memoria".
    2.  **Peligro de Desbordamiento (Buffer Overflow):** Si tienes un `char buffer[10]` e intentas copiar en él la palabra "parangaricutirimicuaro", vas a sobrescribir memoria que no te pertenece, lo que puede hacer que tu programa falle de formas misteriosas o incluso crear un agujero de seguridad.

*   **Código - El Estilo C en Acción:**
    Para usar estas funciones, necesitas `#include <cstring>`.

    ```cpp
    #include <iostream>
    #include <cstring> // Librería para funciones como strlen, strcpy

    using namespace std;

    int main() {
        // Arreglo estático. Tiene espacio para 9 caracteres + el '\0'
        char saludo_c[10];

        // Copiamos texto de forma segura con strncpy (copia hasta 9 caracteres)
        strncpy(saludo_c, "Hola", 9);
        saludo_c[9] = '\0'; // Aseguramos el terminador nulo

        cout << "Cadena estilo C: " << saludo_c << endl;

        // Obtenemos su longitud (sin contar el '\0')
        cout << "Longitud (strlen): " << strlen(saludo_c) << endl;

        // Concatenamos (añadimos texto al final)
        strncat(saludo_c, "!", 9 - strlen(saludo_c));
        cout << "Concatenado: " << saludo_c << endl;

        return 0;
    }
    ```

#### **B) Cadenas Estilo C++ (`std::string`)**

Esta es la forma **moderna, segura y recomendada** de trabajar con texto en C++.

*   **¿Qué son?** Son un **objeto** que maneja el texto por ti. ¡Olvida el `\0` y el manejo manual de memoria!
*   **Ventajas:**
    1.  **Automático y Seguro:** Crece y se encoge según lo necesites. No hay riesgo de desbordamiento si usas sus operaciones.
    2.  **Intuitivo:** Usas operadores lógicos como `+` para concatenar y `==` para comparar. Es mucho más legible.
    3.  **Potente:** Viene con un montón de funciones útiles integradas (métodos) como `.size()`, `.find()`, `.substr()`, etc.

*   **Código - El Estilo C++ en Acción:**
    Para usarlo, necesitas `#include <string>`.

    ```cpp
    #include <iostream>
    #include <string>

    using namespace std;

    int main() {
        // Crear un string es tan fácil como declarar una variable
        string saludo_cpp = "Hola";

        // Concatenar es súper simple con el operador '+'
        saludo_cpp += ", mundo moderno!";

        cout << "Cadena estilo C++: " << saludo_cpp << endl;

        // Obtenemos su longitud con el método .size()
        cout << "Longitud (.size()): " << saludo_cpp.size() << endl;

        // Buscar una subcadena
        if (saludo_cpp.find("moderno") != string::npos) {
            cout << "La palabra 'moderno' fue encontrada." << endl;
        }

        return 0;
    }
    ```**Veredicto:** Siempre que puedas, **usa `std::string`**. Es más seguro, más fácil y más potente. Solo necesitarás `char*` cuando interactúes con librerías antiguas de C.

---

### **2. Registros o Estructuras (`struct`): Crea Tus Propios Tipos de Datos 📦**

¿Qué pasa si quieres representar un "Alumno" que tiene una edad (`int`), un tipo (`char`) y un promedio (`double`)? Tener tres variables separadas es desordenado. Un `struct` te permite **agrupar estas variables en una sola unidad lógica**.

*   **La Idea:** Es como crear tu propio tipo de dato personalizado.
*   **La Diferencia Clave con `class` (¡Pregunta de Examen!):**
    *   En un `struct`, los miembros son **públicos** por defecto (puedes acceder a ellos desde fuera).
    *   En una `class`, los miembros son **privados** por defecto (están ocultos y solo se puede acceder a través de métodos públicos).
    *   Por convención, se usan `structs` para agrupar datos simples y `classes` para crear objetos más complejos con datos y comportamientos.

*   **Código - Creando y Usando un `struct`:**

    ```cpp
    #include <iostream>
    #include <string>

    using namespace std;

    // 1. Definimos la plantilla de nuestro nuevo tipo de dato
    struct Alumno {
        int edad;
        string nombre; // Usamos string, es más práctico
        double promedio;
    };

    int main() {
        // 2. Creamos una variable (una instancia) de tipo Alumno
        Alumno a1;

        // 3. Accedemos a sus campos (miembros) usando el operador punto '.'
        a1.edad = 20;
        a1.nombre = "Sofia Rodriguez";
        a1.promedio = 17.5;

        // Podemos imprimir la información
        cout << "Nombre: " << a1.nombre << ", Promedio: " << a1.promedio << endl;

        return 0;
    }
    ```

---

### **3. Objetos, Referencias e Instancias: El Salto a la Programación Orientada a Objetos 🚀**

Esta parte te introduce a conceptos clave de la Programación Orientada a Objetos (POO).

*   **Clase vs. Objeto:**
    *   **Clase:** Es el **plano** o la plantilla (ej: `class Coche`). Define qué datos (atributos) y qué funciones (métodos) tendrá.
    *   **Objeto (o Instancia):** Es la **construcción real** a partir del plano (ej: `miCocheRojo`, `elCocheDeJuan`). Es una porción de memoria que existe mientras el programa corre.

*   **Memoria Estática vs. Dinámica (¡Muy Importante!):**
    *   **Creación Estática (en la Pila):** `Alumno a1;`
        *   Rápida y automática. La variable `a1` se crea cuando el programa entra en su ámbito (ej: una función) y se destruye automáticamente al salir.
        *   Úsala para objetos de la librería estándar (`string`, `vector`) y para objetos simples que no necesites que sobrevivan fuera de una función.
    *   **Creación Dinámica (en el Heap):** `Alumno* ptrAlumno = new Alumno();`
        *   Tú tienes el control total. El objeto se crea cuando dices `new` y **solo se destruye cuando tú dices `delete`**.
        *   Es la forma recomendada para tus objetos complejos, porque te da flexibilidad para decidir su tiempo de vida.
        *   **Regla de Oro:** Por cada `new`, debe haber un `delete` correspondiente para evitar fugas de memoria.

*   **Código - Objeto Dinámico con `new` y `delete`:**

    ```cpp
    #include <iostream>
    #include <string>

    using namespace std;

    class Mascota {
    public:
        string nombre;

        // Constructor: se ejecuta al crear el objeto con 'new'
        Mascota(string n) {
            nombre = n;
            cout << nombre << " ha nacido (objeto creado)!" << endl;
        }

        // Destructor: se ejecuta al destruir el objeto con 'delete'
        ~Mascota() {
            cout << nombre << " se ha ido (objeto destruido)." << endl;
        }

        void ladrar() {
            cout << nombre << " dice: Guau!" << endl;
        }
    };

    int main() {
        // Creamos un puntero para guardar la dirección del objeto
        Mascota* ptrMiPerro;

        // Creamos el objeto en memoria dinámica con 'new'
        ptrMiPerro = new Mascota("Fido");

        // Para acceder a miembros a través de un puntero, usamos el operador flecha '->'
        ptrMiPerro->ladrar();

        // Cuando ya no necesitamos el objeto, liberamos la memoria
        delete ptrMiPerro;
        ptrMiPerro = nullptr; // Buena práctica para evitar usar un puntero inválido

        return 0;
    }
    ```

Esta sesión te ha dado las herramientas para crear y manejar tipos de datos complejos y estructurados. ¡Dominar esto es un gran paso para convertirte en un programador experto