Golang interview questions and answers

## 🧠 Cuestionario de Programación en Go (Golang) – Nivel Intermedio y Avanzado

Este cuestionario está diseñado para evaluar conocimientos sólidos en Golang, desde fundamentos hasta concurrencia, interfaces, testing y buenas prácticas.

---

## 🔹 Sección 1: Fundamentos del Lenguaje

1. ¿Qué diferencia hay entre un *array* y un *slice* en Go?  
    - a.  un array es un conjunto de elementos del mismo tipo. Y un slice es una referencia a un array.
    - b. un array es un apuntador a un conjunto de elementos del mismo tipo. Y un slice es una referencia a un apuntador.
    - c. un array es un hashmap. Y un slice es una lista.
    - d. no existen estas estructuras de datos en GOLANG.

    Answer: a
    Explanation: Un array en Go es una colección de elementos del mismo tipo con tamaño fijo, almacenados de forma contigua en memoria. Un slice es una estructura que referencia una porción de un array, permitiendo trabajar con secuencias dinámicas de elementos. Los slices incluyen un puntero al array subyacente, longitud y capacidad, y permiten redimensionar y compartir datos eficientemente.
2. ¿Qué sucede si intentas acceder a un índice fuera del rango en un *array*?  
    - a. El programa retorna un valor por defecto del tipo de dato.
    - b. El programa entra en un bucle infinito.
    - c. El programa compila pero ignora el acceso fuera de rango.
    - d. El programa entra en pánico (*panic*) y se detiene la ejecución.

    Answer: d
    Explanation: En Go, si intentas acceder a un índice fuera del rango válido de un array o slice, el programa entra en pánico (*panic*) en tiempo de ejecución y se detiene la ejecución. Esto ayuda a prevenir errores de memoria y comportamientos inesperados.
3. ¿Cómo se declara una constante tipada y una no tipada?
    a. `const name = value`
    b. `const name type = value`
    c. Ambas son correctas
    d. Ninguna es correcta
    Answer: c
    Explanation: En Go, puedes declarar una constante no tipada usando `const name = value`, donde el tipo se infiere automáticamente. Para declarar una constante tipada, usas `const name type = value`, especificando explícitamente el tipo de la constante. Con esto, Go garantiza que el valor de la constante sea del tipo especificado.
4. Explica qué es una variable *zero-value* en Go.
    - a. Una variable que no ha sido inicializada y tiene un valor predeterminado según su tipo.
    - b. Una variable que siempre tiene el valor cero.
    - c. Una variable que no puede ser modificada.
    - d. Una variable que se usa para contar iteraciones.

    Answer: a
    Explanation: En Go, una variable *zero-value* es aquella que no ha sido explícitamente inicializada y, por lo tanto, toma un valor predeterminado basado en su tipo. Por ejemplo, el *zero-value* de un `int` es `0`, el de un `string` es una cadena vacía `""`, y el de un `bool` es `false`. Esto asegura que todas las variables tengan un valor definido incluso si no se les asigna uno explícitamente.
5. ¿Qué diferencia hay entre `new()` y `make()`?
    - a. `new()` se usa para crear slices, maps y channels, mientras que `make()` se usa para tipos básicos.
    - b. `new()` asigna memoria y devuelve un puntero al tipo, mientras que `make()` inicializa y devuelve el valor del tipo (no un puntero) para slices, maps y channels.
    - c. No hay diferencia, ambos hacen lo mismo.
    - d. `new()` es una función obsoleta y no se debe usar.

    Answer: b
    Explanation: En Go, `new()` es una función incorporada que asigna memoria para un tipo específico y devuelve un puntero a esa memoria. Se puede usar con cualquier tipo de dato, pero no inicializa el valor; simplemente lo establece en su *zero-value*. Por otro lado, `make()` es una función específica para inicializar y devolver valores de tipos como slices, maps y channels. `make()` no devuelve un puntero, sino el valor inicializado del tipo correspondiente, listo para su uso.
6. ¿Qué significa que Go es un lenguaje con *tipado estático* pero *inferido*?
    - a. Los tipos de las variables se verifican en tiempo de compilación, pero no es necesario declararlos explícitamente.
    - b. Los tipos de las variables se verifican en tiempo de ejecución.
    - c. Go no tiene tipos de datos.
    - d. Los tipos de las variables cambian dinámicamente durante la ejecución.

    Answer: a
    Explanation: Go es un lenguaje con *tipado estático* porque los tipos de las variables se verifican en tiempo de compilación, lo que ayuda a detectar errores antes de ejecutar el programa. Sin embargo, también es un lenguaje con *tipado inferido* porque el compilador puede deducir automáticamente el tipo de una variable basada en el valor que se le asigna, permitiendo declarar variables sin especificar explícitamente su tipo.
7. ¿Qué es una función variádica? Da un ejemplo.
    - a. Una función que puede aceptar un número variable de argumentos del mismo tipo.
    - b. Una función que siempre retorna múltiples valores.
    - c. Una función que no acepta argumentos.
    - d. Una función que solo acepta argumentos de tipo `interface{}`.

    Answer: a
    Explanation: Una función variádica en Go es una función que puede aceptar un número variable de argumentos del mismo tipo. Se define usando `...` antes del tipo del último parámetro. Por ejemplo:

    ```go
    func sum(numbers ...int) int {
        total := 0
        for _, number := range numbers {
            total += number
        }
        return total
    }
    ```
    En este ejemplo, la función `sum` puede recibir cualquier cantidad de enteros y los suma.
8. ¿Qué sucede si no usas una variable en una función?
    - a. El programa compila pero muestra una advertencia.
    - b. El programa entra en pánico (*panic*).
    - c. El programa no compila y muestra un error.
    - d. La variable se ignora automáticamente.

    Answer: c
    Explanation: En Go, si declaras una variable dentro de una función y no la usas, el programa no compilará y mostrará un error indicando que la variable está declarada pero no utilizada. Esto es parte del diseño del lenguaje para fomentar buenas prácticas de programación y evitar código innecesario.
9. ¿Qué diferencia hay entre `:=` y `var`? 
    - a. `:=` se usa para declarar y asignar variables en una sola línea, mientras que `var` se usa para declarar variables con un tipo explícito o sin asignación inicial.
    - b. No hay diferencia, ambos hacen lo mismo.
    - c. `var` solo se usa para variables globales.
    - d. `:=` solo se usa dentro de funciones.

    Answer: a
    Explanation: En Go, `:=` es una forma corta de declarar y asignar una variable en una sola línea, y solo puede usarse dentro de funciones. El tipo de la variable se infiere automáticamente del valor asignado. Por otro lado, `var` se utiliza para declarar variables con un tipo explícito o sin asignación inicial, y puede usarse tanto dentro como fuera de funciones (para variables globales). Por ejemplo:

    ```go
    var x int = 10 // Declaración con tipo explícito
    y := 20        // Declaración corta con inferencia de tipo
    ```
10. ¿Qué es el *shadowing* de variables?
    - a. Cuando una variable local tiene el mismo nombre que una variable en un ámbito superior, ocultando la variable superior.
    - b. Cuando una variable se declara pero nunca se usa.
    - c. Cuando una variable cambia de tipo durante la ejecución.
    - d. Cuando una variable es global y accesible desde cualquier parte del código.

    Answer: a
    Explanation: El *shadowing* de variables en Go ocurre cuando una variable local dentro de un bloque (como una función o un bucle) tiene el mismo nombre que una variable en un ámbito superior (como una variable global o de nivel de paquete). En este caso, la variable local "oculta" o "sombra" la variable superior dentro de su propio ámbito, lo que significa que cualquier referencia a esa variable dentro del bloque se refiere a la variable local y no a la superior.
---

## 🔹 Sección 2: Estructuras de Datos y Tipos

11. ¿Cómo defines un *struct* y cómo accedes a sus campos?
    - a. Usando la palabra clave `struct` y accediendo a los campos con el operador punto (`.`).
    - b. Usando la palabra clave `class` y accediendo a los campos con el operador flecha (`->`).
    - c. Usando la palabra clave `type` y accediendo a los campos con corchetes (`[]`).
    - d. Usando la palabra clave `record` y accediendo a los campos con el operador doble punto (`::`).

    Answer: a
    Explanation: En Go, defines un *struct* usando la palabra clave `struct`, seguida del nombre del struct y una lista de campos entre llaves. Accedes a los campos de un struct utilizando el operador punto (`.`). Por ejemplo:

    ```go
    type Person struct {
        Name string
        Age  int
    }

    p := Person{Name: "Alice", Age: 30}
    fmt.Println(p.Name) // Acceso al campo Name
    ```
12. ¿Cómo creas un puntero a un *struct* y cómo accedes a sus campos?
    - a. Usando el operador `&` para crear el puntero y el operador `.` para acceder a los campos.
    - b. Usando el operador `*` para crear el puntero y el operador `->` para acceder a los campos.
    - c. Usando la función `new()` para crear el puntero y el operador `.` para acceder a los campos.
    - d. Usando la función `make()` para crear el puntero y el operador `->` para acceder a los campos.

    Answer: c
    Explanation: En Go, puedes crear un puntero a un *struct* usando la función `new()`, que asigna memoria para el struct y devuelve un puntero a él. También puedes usar el operador `&` para obtener la dirección de una variable struct existente. Para acceder a los campos de un struct a través de un puntero, puedes usar el operador punto (`.`) directamente, ya que Go automáticamente desreferencia el puntero cuando accedes a sus campos. Por ejemplo:

    ```go
    type Person struct {
        Name string
        Age  int
    }

    p := new(Person) // Crear un puntero a Person
    p.Name = "Bob"   // Acceso al campo Name a través del puntero
    fmt.Println(p.Name)
    
    p2 := Person{Name: "Alice", Age: 30}
    p2Ptr := &p2 // Crear un puntero usando &
    fmt.Println(p2Ptr.Name) // Acceso al campo Name a través del puntero
    ```
13. ¿Qué es una *etiqueta de campo (tag)* en un *struct* y para qué se usa?
    - a. Una cadena de texto asociada a un campo de un struct que proporciona metadatos, comúnmente usada para serialización/deserialización.
    - b. Un comentario que describe el campo del struct.
    - c. Un identificador único para cada campo del struct.
    - d. Una función que se ejecuta cuando se accede al campo del struct.

    Answer: a
    Explanation: En Go, una *etiqueta de campo (tag)* es una cadena de texto opcional que se asocia a un campo de un struct y proporciona metadatos adicionales sobre ese campo. Las etiquetas se colocan entre comillas después de la declaración del campo y suelen usarse para propósitos como la serialización/deserialización (por ejemplo, con JSON o XML), validación, o mapeo a bases de datos. Por ejemplo:

    ```go
    type Person struct {
        Name string `json:"name"`
        Age  int    `json:"age"`
    }
    ```
    En este ejemplo, las etiquetas indican cómo se deben nombrar los campos cuando se convierten a JSON.
14. ¿Qué pasa al copiar un *struct* por valor?
    - a. Se crea una copia independiente del struct, y los cambios en la copia no afectan al original.
    - b. Se crea una referencia al struct original, y los cambios en la copia afectan al original.
    - c. No se permite copiar structs por valor en Go.
    - d. Se crea una copia superficial que comparte referencias a campos internos.

    Answer: a
    Explanation: En Go, cuando copias un *struct* por valor, se crea una copia independiente del struct original. Esto significa que cualquier cambio realizado en la copia no afectará al struct original, ya que ambos son instancias separadas en memoria. Por ejemplo:

    ```go
    type Point struct {
        X, Y int
    }

    p1 := Point{X: 1, Y: 2}
    p2 := p1 // Copia por valor

    p2.X = 10 // Modificar la copia
    fmt.Println(p1.X) // Imprime 1, el original no se ve afectado
    fmt.Println(p2.X) // Imprime 10, la copia se modificó
    ```
15. Explica la diferencia entre *value types* y *reference types* en Go.
    - a. Los *value types* almacenan datos directamente, mientras que los *reference types* almacenan una referencia a los datos.
    - b. No hay diferencia, ambos son lo mismo en Go.
    - c. Los *value types* son inmutables, mientras que los *reference types* son mutables.
    - d. Los *value types* solo pueden ser tipos primitivos, mientras que los *reference types* son structs y slices.

    Answer: a
    Explanation: En Go, los *value types* son tipos de datos que almacenan sus valores directamente en la memoria. Ejemplos de *value types* incluyen tipos primitivos como `int`, `float`, `bool`, y también structs y arrays. Cuando se asigna o pasa un *value type*, se crea una copia independiente del valor.

    Por otro lado, los *reference types* son tipos de datos que almacenan una referencia (o puntero) a la ubicación de los datos en memoria. Ejemplos de *reference types* incluyen slices, maps, channels y punteros. Cuando se asigna o pasa un *reference type*, se copia la referencia, lo que significa que múltiples variables pueden apuntar al mismo conjunto de datos en memoria. Cambios realizados a través de una referencia afectarán a todas las referencias que apuntan a esos datos.
16. ¿Qué sucede al comparar dos *structs*?  
17. ¿Cómo conviertes un tipo a otro en Go (*type conversion*)?  
18. ¿Qué son los tipos definidos por el usuario (*custom types*) y cuándo se usan?  
19. ¿Cómo implementas métodos en tipos definidos por el usuario?  
20. ¿Cuál es la diferencia entre un *receiver value* y un *receiver pointer*?

---

## 🔹 Sección 3: Interfaces y Polimorfismo

21. ¿Cómo defines una interfaz en Go?  
22. ¿Cómo sabes si un tipo implementa una interfaz?  
23. ¿Qué es el *duck typing* en Go?  
24. ¿Qué diferencia hay entre una interfaz vacía `interface{}` y una interfaz específica?  
25. ¿Qué pasa al comparar dos valores de tipo `interface{}`?  
26. ¿Cómo realizas una aserción de tipo (*type assertion*)?  
27. ¿Qué es un *type switch* y para qué sirve?  
28. ¿Qué significa que las interfaces son satisfechas de forma implícita?  
29. ¿Qué sucede si una interfaz contiene un método que un tipo no implementa?  
30. ¿Qué pasa si una interfaz contiene otra interfaz?

---

## 🔹 Sección 4: Concurrencia y Sincronización

31. ¿Qué es una *goroutine* y cómo se lanza una?  
32. ¿Qué es un *channel* y cómo se usa para comunicar goroutines?  
33. ¿Cuál es la diferencia entre canales con buffer y sin buffer?  
34. ¿Qué sucede si envías datos a un canal cerrado?  
35. ¿Qué pasa si cierras un canal más de una vez?  
36. ¿Cómo utilizas la palabra clave `select` en Go?  
37. ¿Qué es el patrón *fan-in* y *fan-out* en concurrencia?  
38. ¿Cómo se evita una *race condition* en Go?  
39. ¿Qué herramientas provee Go para detectar *race conditions*?  
40. Explica cómo funciona `sync.WaitGroup` y su propósito.

---

## 🔹 Sección 5: Errores y Manejo de Excepciones

41. ¿Cómo se maneja el error en Go?  
42. ¿Qué diferencia hay entre `panic`, `recover` y `defer`?  
43. ¿Qué pasa si no manejas un error en Go?  
44. ¿Cómo se implementa un tipo de error personalizado?  
45. ¿Qué función se usa para envolver errores (`fmt.Errorf`) y por qué?  
46. ¿Qué diferencia hay entre `log.Fatal` y `panic`?  
47. ¿Por qué Go no utiliza excepciones como otros lenguajes?  
48. ¿Qué patrón se recomienda para propagar errores en funciones anidadas?  
49. ¿Cómo se usa `errors.Is` y `errors.As` para manejar errores?  
50. ¿Qué ventaja tiene usar *sentinel errors*?

---

## 🔹 Sección 6: Testing, Rendimiento y Buenas Prácticas

51. ¿Cómo se estructuran las pruebas unitarias en Go?  
52. ¿Cómo ejecutas todas las pruebas del módulo desde la línea de comandos?  
53. ¿Qué paquete se usa para *benchmarking*?  
54. ¿Cómo defines una *table-driven test*?  
55. ¿Qué hace el flag `-race` durante la ejecución de pruebas?  
56. ¿Cómo se organiza un proyecto grande en Go (paquetes, módulos)?  
57. ¿Qué es un *Go module* y cómo se inicializa?  
58. ¿Qué herramientas ofrece Go para formatear y analizar código (`go fmt`, `go vet`)?  
59. ¿Qué es la *garbage collection* y cómo impacta el rendimiento?  
60. Menciona tres buenas prácticas para escribir código idiomático en Go.

---

🧩 **Sugerencia de uso:**
- Usa este cuestionario como guía de repaso antes de una entrevista técnica.  
- Puedes responder en formato ensayo o crear opciones múltiples.  
- Complementa con ejercicios prácticos para reforzar cada sección.

