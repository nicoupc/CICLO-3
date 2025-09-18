### **1. ¿Qué Son las Funciones Lambda? Funciones "Al Instante" ⚡**

Imagina que necesitas una pequeña función de ayuda para una tarea muy específica, por ejemplo, para decirle al algoritmo `sort` que ordene números de mayor a menor.

**La forma tradicional:**
1.  Sales de tu función `main`.
2.  Defines una función completa: `bool compararDesc(int a, int b) { return a > b; }`.
3.  Vuelves a `main` y la usas: `sort(miVector.begin(), miVector.end(), compararDesc);`.

Esto funciona, pero es un poco engorroso. Tienes que ir a otra parte del código para definir una función que solo vas a usar una vez en un lugar muy concreto.

**La forma con Lambdas:**
Creas la función **justo ahí**, en el mismo lugar donde la necesitas.

`sort(miVector.begin(), miVector.end(), [](int a, int b) { return a > b; });`

**En resumen, una función Lambda es:**
*   **Una función anónima:** No tiene nombre. Su "identidad" es el código que contiene.
*   **Una función "in-situ":** La defines y (generalmente) la usas en el mismo lugar.
*   **Concisa y Local:** Mantiene la lógica junta, haciendo el código más fácil de leer y entender, porque no tienes que saltar por todo el archivo para ver qué hace una pequeña función de ayuda.

---

### **2. La Anatomía de una Lambda: Desglosando la Sintaxis 🧩**

La sintaxis `[captura](parametros) mutable -> tipo_retorno { cuerpo }` parece un jeroglífico, pero cada pieza tiene un propósito claro. Vamos a desglosarla.

`[ ] ( ) -> { }`

1.  **`[ ]` La Cláusula de Captura (El Cerebro de la Lambda 🧠):**
    *   **¿Qué es?** Es lo que le da a la lambda acceso a las variables que existen **fuera** de ella, en el ámbito donde fue creada. ¡Esto es su superpoder!
    *   **Modos de Captura (¡Clave para el Examen!):**
        *   `[]`: No captura nada. La lambda no puede ver ninguna variable de fuera.
        *   `[=]`: Captura **todo por valor (copia)**. La lambda recibe una *copia* de todas las variables externas que usa. Si modifica una, solo modifica su copia local, la original no se ve afectada.
        *   `[&]`: Captura **todo por referencia (acceso directo)**. La lambda obtiene un *acceso directo* a las variables externas. Si modifica una, la variable original **sí cambia**.
        *   `[variable]`: Captura solo `variable` por valor.
        *   `[&variable]`: Captura solo `variable` por referencia.
        *   `[=, &var]`: Captura `var` por referencia y todo lo demás por valor.
        *   `[&, var]`: Captura `var` por valor y todo lo demás por referencia.

2.  **`( )` La Lista de Parámetros:**
    *   Funciona exactamente igual que en una función normal. Son los "ingredientes" que le pasas a la lambda cuando la llamas. Es opcional si no recibe parámetros.

3.  **`-> tipo_retorno` El Tipo de Retorno (Opcional):**
    *   Especifica qué tipo de dato devuelve la lambda (ej: `-> bool`, `-> int`).
    *   En la mayoría de los casos, el compilador es lo suficientemente inteligente como para deducirlo por sí mismo, así que puedes omitirlo.

4.  **`{ }` El Cuerpo:**
    *   El código que se ejecuta. Aquí va la lógica de tu función, igual que en cualquier otra.

---

### **3. Lambdas en Acción: De la Teoría al Código Real**

Vamos a analizar los ejemplos de tus diapositivas para que veas cómo se aplica todo esto.

#### **Ejemplo 1: Ordenar un vector de mayor a menor**
Este es el caso de uso más famoso. El algoritmo `std::sort` necesita que le digas *cómo* comparar dos elementos.

```cpp
#include <iostream>
#include <vector>
#include <algorithm> // Aquí vive std::sort

using namespace std;

void imprimir(const vector<int>& v) {
    for (int num : v) {
        cout << num << " ";
    }
    cout << endl;
}

int main() {
    vector<int> v = {44, 11, 77, 55, 66, 33, 22, 88};
    cout << "Original: ";
    imprimir(v);

    // Usamos una lambda para definir el criterio de ordenamiento "descendente"
    // Parámetros: const int left, const int right
    // Retorno (inferido): bool
    // Cuerpo: return left > right;
    sort(v.begin(), v.end(), [](const int left, const int right) {
        return left > right;
    });

    cout << "Ordenado (mayor a menor): ";
    imprimir(v); // Salida: 88 77 66 55 44 33 22 11
    
    return 0;
}
```

#### **Ejemplo 2: Usando la Cláusula de Captura para contar múltiplos**
Aquí queremos contar cuántos números en un vector son múltiplos de una variable `multi`. La lambda necesita "ver" esa variable.

```cpp
#include <iostream>
#include <vector>
#include <algorithm> // Aquí vive std::count_if

using namespace std;

int main() {
    vector<int> vec = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 15, 20};
    int multi = 5;

    // `count_if` cuenta elementos que cumplen una condición.
    // La condición se la damos con una lambda.
    // [=] captura 'multi' por valor (una copia).
    // La lambda recibe un 'num' del vector y comprueba si es divisible por 'multi'.
    size_t count = count_if(vec.begin(), vec.end(), [=](int num) {
        return num % multi == 0;
    });

    cout << "Hay " << count << " multiplos de " << multi << "." << endl; // Salida: Hay 4 multiplos de 5.

    return 0;
}
```

#### **Ejemplo 3: Demostración de Captura por Valor y Referencia**
Este ejemplo de tus diapositivas es perfecto para entender la diferencia.

```cpp
#include <iostream>

using namespace std;

int main() {
    int m = 0;
    int n = 0;

    cout << "Antes: m = " << m << ", n = " << n << endl;

    // Capturamos 'm' por referencia (&m) y 'n' por valor (n).
    // La lambda recibe un parámetro 'a' que será 4.
    // 'mutable' es necesario si quisiéramos modificar la *copia* de 'n'.
    // En este caso, con la captura por referencia de 'm', no es estrictamente necesario,
    // pero no da error.
    [&m, n](int a) mutable {
        m = ++n + a; // n se incrementa a 1, luego se suma con a (4), m = 5
                     // OJO: 'n' aquí es la COPIA. El 'n' original no cambia.
                     // Pero 'm' SÍ es el original.
    }(4); // La llamamos inmediatamente con el valor 4.

    cout << "Despues: m = " << m << ", n = " << n << endl; // Salida: Despues: m = 5, n = 0

    return 0;
}
```
**Análisis del resultado:** `m` cambió a `5` porque lo capturamos por referencia (`&m`), dándole a la lambda acceso directo. `n` se quedó en `0` porque fue capturado por valor (`n`), y la lambda solo trabajó con una copia.

---

### **4. Un Caso Avanzado: Lambdas como Parámetros**

Tus diapositivas muestran cómo puedes hacer que tus **propias funciones** acepten lambdas, lo que las hace increíblemente flexibles.

```cpp
#include <iostream>
#include <vector>
#include <functional> // Necesario para std::function

using namespace std;

// Esta función aplica una operación (una lambda) a cada elemento de un vector.
// 'const function<void(int)>& operacion' significa:
// "Acepto cualquier función (o lambda) que no devuelva nada (void) y reciba un int".
void aplicar_operacion(const vector<int>& v, const function<void(int)>& operacion) {
    for (int elemento : v) {
        operacion(elemento);
    }
}

int main() {
    vector<int> numeros = {10, 20, 30};
    int multiplicador = 3;

    cout << "Multiplicando por " << multiplicador << ":" << endl;

    // Le pasamos una lambda que captura 'multiplicador' e imprime el resultado.
    aplicar_operacion(numeros, [=](int num) {
        cout << num << " * " << multiplicador << " = " << num * multiplicador << endl;
    });

    return 0;
}
```

Las lambdas son un concepto que transforma tu código. Te permiten pensar de una manera más funcional, pasando comportamientos como si fueran datos. ¡Practica con los algoritmos de `<algorithm>` como `sort`, `for_each`, `count_if`, `find_if`, etc., y verás lo naturales que se vuelven