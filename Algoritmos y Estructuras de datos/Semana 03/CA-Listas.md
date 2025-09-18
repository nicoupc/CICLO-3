### **Tu Guía de Estudio (Nivel Experto) para la Implementación de la Clase `Lista` 🚀**

---

### **Parte 1: El Plano Maestro (Análisis de `Lista.h`)**

Antes de construir una casa, necesitas los planos. El archivo de cabecera (`.h`) es exactamente eso para nuestra clase `Lista`. El código de la segunda página del documento define toda la **interfaz** de la lista. Vamos a analizarlo línea por línea.

```cpp
#pragma once // Directiva para que el compilador solo incluya este archivo una vez.
#include <functional> // La necesitamos para std::function, ¡ahorita vemos por qué!

using namespace std;
typedef unsigned int uint; // Un alias para no escribir "unsigned int" todo el tiempo.

template <typename T, T NADA = 0> // ¡Línea súper importante!
class Lista {
// ...
};
```

*   **`template <typename T, T NADA = 0>`:**
    *   `typename T`: Ya lo conoces. Hace que nuestra lista sea genérica. Puede ser una `Lista<int>`, `Lista<string>`, `Lista<Alumno>`, etc.
    *   `T NADA = 0`: ¡Esto es un truco muy ingenioso! Es un **parámetro de plantilla opcional**. `NADA` es un valor por defecto que usaremos para indicar "no se encontró nada" o "valor inválido". Si creas una `Lista<int>`, `NADA` será `0`. Si fuera una `Lista<Alumno*>`, podríamos definirla como `Lista<Alumno*, nullptr>` para que `NADA` sea `nullptr`. Es una forma flexible de manejar valores nulos.

Ahora, veamos los **miembros de la clase**:

```cpp
// ... dentro de class Lista
struct Nodo; // Declaración adelantada. Le decimos al compilador: "confía en mí, luego te defino qué es un Nodo".
typedef function<int(T, T)> Comp; // ¡Conexión con la clase anterior!

// --- MIEMBROS PRIVADOS (El motor interno de la lista) ---
Nodo* ini;       // Puntero al primer nodo. En lugar de "cabeza", el profe lo llamó "ini" (inicio).
uint  lon;       // La longitud (número de nodos). Un contador para no tener que recorrer toda la lista para saber su tamaño.
Comp  comparar;  // ¡Una variable que puede guardar una función lambda! Aquí guardaremos el criterio para buscar elementos.

public:
// --- MÉTODOS PÚBLICOS (El panel de control que el usuario puede usar) ---
    Lista();          // Constructor por defecto
    Lista(Comp cmp);  // Constructor que recibe una lambda de comparación
    ~Lista();         // Destructor (¡para liberar la memoria!)

    // Métodos para consultar estado
    uint longitud();
    bool esVacia();

    // Métodos para AÑADIR elementos
    void agregaInicial(T elem);
    void agregaPos(T elem, uint pos);
    void agregaFinal(T elem);

    // Métodos para ELIMINAR elementos
    void eliminaInicial();
    void eliminaPos(uint pos);
    void eliminaFinal();

    // Métodos para OBTENER y BUSCAR elementos
    T obtenerInicial();
    T obtenerPos(uint pos);
    T obtenerFinal();
    T buscar(T elem);
// ... y los métodos para modificar que están en el documento
```
¡Listo! Ya entendemos el plano. Sabemos qué "piezas" tiene nuestra lista por dentro y qué "botones" tiene por fuera para que la usemos.

---

### **Parte 2: El Ladrillo Fundamental (Implementación del `Nodo`)**

El documento lo define dentro de la clase, lo cual es una práctica común para mantenerlo encapsulado.

```cpp
template <typename T, T NADA>
struct Lista<T, NADA>::Nodo {
    T elem;      // El dato o elemento
    Nodo* sig;   // El puntero al siguiente nodo (siguiente)

    // Constructor para crear nodos fácilmente
    Nodo(T elem = NADA, Nodo* sig = nullptr) : elem(elem), sig(sig) {}
};
```
Esto es exactamente el nodo que ya habíamos discutido. `elem` es el tesoro, `sig` es la ubicación de la siguiente pista.

---

### **Parte 3: Las Operaciones en Acción (¡Con Código y Diagramas!)**

Ahora sí, vamos a implementar los métodos clave, siguiendo los diagramas de tu material.

#### **`agregaInicial(T elem)` - Añadir al Principio**

Esta es la operación más fundamental y eficiente de una lista enlazada.

*   **Lógica (ver diagrama de la pág. 4):**
    1.  **Crear un nuevo nodo:** Este nodo contendrá el nuevo elemento (`82` en el diagrama).
    2.  **Enlazar el nuevo nodo:** El puntero `siguiente` del nuevo nodo debe apuntar a lo que *antes* era el primer nodo (el nodo con `8`).
    3.  **Actualizar el inicio:** El puntero `ini` de la lista ahora debe apuntar al nuevo nodo, convirtiéndolo en el nuevo primer elemento.

*   **Código (pág. 5):**

    ```cpp
    template <typename T, T NADA>
    void Lista<T, NADA>::agregaInicial(T elem) {
        // Esta línea hace los pasos 1 y 2 de la lógica en un solo movimiento:
        // 1. new Nodo(elem, ini) -> Crea un nuevo nodo con el elemento 'elem'.
        // 2. El puntero 'siguiente' de este nuevo nodo se establece en 'ini' (el antiguo primer nodo).
        Nodo* nuevo = new Nodo(elem, ini);

        // Verificamos que se pudo crear el nodo (la memoria no está llena)
        if (nuevo != nullptr) {
            // Paso 3: Actualizamos el puntero 'ini' de la lista.
            ini = nuevo;
            // No olvides incrementar el contador de longitud.
            lon++;
        }
    }
    ```

#### **`buscar(T elem)` - Encontrar un Elemento**

Este algoritmo demuestra el acceso secuencial.

*   **Lógica (ver diagramas de págs. 5 y 6):**
    1.  Crear un puntero temporal `aux` que apunte al inicio de la lista (`ini`).
    2.  Iniciar un bucle que se repita mientras `aux` no sea `nullptr` (mientras no hayamos llegado al final de la lista).
    3.  En cada paso del bucle:
        *   Comparar el elemento del nodo actual (`aux->elem`) con el que buscamos. Para esto usamos nuestra función `comparar`.
        *   Si son iguales, ¡lo encontramos! Devolvemos el elemento.
        *   Si no son iguales, avanzamos `aux` al siguiente nodo: `aux = aux->sig`.
    4.  Si el bucle termina (porque `aux` se convirtió en `nullptr`), significa que recorrimos toda la lista y no lo encontramos. Devolvemos el valor `NADA`.

*   **Código (pág. 6):**

    ```cpp
    template <typename T, T NADA>
    T Lista<T, NADA>::buscar(T elem) {
        // Paso 1: Crear el puntero auxiliar
        Nodo* aux = ini;

        // Paso 2: Iniciar el bucle de recorrido
        while (aux != nullptr) {
            // Paso 3: Comparar y avanzar
            if (comparar(aux->elem, elem) == 0) { // == 0 es la convención para "iguales"
                return aux->elem; // ¡Encontrado!
            }
            aux = aux->sig; // Moverse al siguiente nodo
        }
        // Paso 4: No se encontró
        return NADA;
    }
    ```

#### **`eliminaInicial()` - Quitar el Primer Elemento**

La operación inversa a `agregaInicial`.

*   **Lógica (ver diagrama de la pág. 7):**
    1.  Asegurarse de que la lista no esté vacía. No se puede eliminar algo que no existe.
    2.  Crear un puntero temporal `aux` para "sujetar" el primer nodo que vamos a eliminar.
    3.  Actualizar `ini` para que apunte al **segundo** nodo de la lista (`ini->sig`). Este se convertirá en el nuevo primer nodo.
    4.  Ahora que la lista ya no apunta al nodo viejo, podemos eliminarlo de forma segura usando `delete aux`.
    5.  Decrementar la longitud `lon`.

*   **Código (pág. 8):**

    ```cpp
    template <typename T, T NADA>
    void Lista<T, NADA>::eliminaInicial() {
        // Paso 1: Verificar que la lista no esté vacía
        if (lon > 0) { // O !esVacia()
            // Paso 2: Guardar la dirección del primer nodo
            Nodo* aux = ini;
            // Paso 3: 'ini' ahora apunta al segundo nodo
            ini = ini->sig;
            // Paso 4: Liberar la memoria del nodo que era el primero
            delete aux;
            // Paso 5: Decrementar el contador
            lon--;
        }
    }
    ```

---

### **Parte 4: Tu Reto (¡Resuelto!) - Implementando `eliminaPos` y `eliminaFinal`**

El documento te lo deja como ejercicio, pero como te perdiste la clase, ¡lo resolvemos juntos! Esto es crucial para tu examen.

#### **`eliminaFinal()`**
Para eliminar el último, necesitamos llegar hasta el **penúltimo** nodo para poder desconectar el último.

```cpp
template <typename T, T NADA>
void Lista<T, NADA>::eliminaFinal() {
    if (lon == 1) {
        eliminaInicial(); // Si solo hay un nodo, es lo mismo que eliminar el primero
    } else if (lon > 1) {
        Nodo* aux = ini;
        // Avanzamos 'aux' hasta que su 'siguiente' sea el último nodo.
        // Es decir, nos paramos en el PENÚLTIMO nodo.
        for (uint i = 0; i < lon - 2; ++i) {
            aux = aux->sig;
        }
        Nodo* nodo_a_borrar = aux->sig; // Guardamos el último nodo
        aux->sig = nullptr;             // El penúltimo ahora es el último
        delete nodo_a_borrar;           // Borramos el que era el último
        lon--;
    }
}
```

#### **`eliminaPos(uint pos)`**
La lógica es similar: debemos llegar al nodo **anterior** a la posición que queremos eliminar.

```cpp
template <typename T, T NADA>
void Lista<T, NADA>::eliminaPos(uint pos) {
    if (pos >= lon) return; // Posición inválida
    if (pos == 0) {
        eliminaInicial();
    } else {
        Nodo* aux = ini;
        // Avanzamos 'aux' hasta el nodo ANTERIOR a la posición a eliminar
        for (uint i = 0; i < pos - 1; ++i) {
            aux = aux->sig;
        }
        Nodo* nodo_a_borrar = aux->sig;
        aux->sig = nodo_a_borrar->sig; // Re-enlazamos
        delete nodo_a_borrar;
        lon--;
    }
}
```

¡Y ahí lo tienes! Hemos desglosado y construido una clase de Lista Enlazada completa. Sé que es mucho, pero te recomiendo leer esto con calma, comparar cada función con su diagrama y, lo más importante, **intentar escribir el código tú mismo**. Copia la declaración de la clase y trata de implementar cada método. Esa es la mejor forma de prepararte.

¡Mucho ánimo! Has superado la parte más difícil. Cualquier otra duda, aquí estoy.