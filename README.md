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
    - a. Se comparan campo por campo, y los structs son iguales si todos los campos son iguales.
    - b. No se pueden comparar structs en Go.
    - c. Se comparan las direcciones de memoria de los structs.
    - d. Solo se comparan los campos exportados (con mayúscula inicial).

    Answer: a
    Explanation: En Go, al comparar dos *structs*, se realiza una comparación campo por campo. Dos structs son considerados iguales si todos sus campos correspondientes son iguales. Si alguno de los campos es diferente, los structs no serán iguales. Es importante destacar que para que la comparación sea válida, todos los campos del struct deben ser comparables (es decir, deben ser tipos que soporten la comparación directa). Si un struct contiene campos que no son comparables (como slices, maps o funciones), entonces no se podrá comparar directamente.
17. ¿Cómo conviertes un tipo a otro en Go (*type conversion*)?
    - a. Usando la sintaxis `Type(value)` para convertir `value` al tipo `Type`.
    - b. Usando la función `convert(Type, value)`.
    - c. Usando el operador `as` para realizar la conversión.
    - d. No se pueden convertir tipos en Go.

    Answer: a
    Explanation: En Go, puedes convertir un valor de un tipo a otro utilizando la sintaxis `Type(value)`, donde `Type` es el tipo al que deseas convertir y `value` es el valor que estás convirtiendo. La conversión solo es posible entre tipos compatibles, y puede implicar una pérdida de información si los tipos no son completamente compatibles. Por ejemplo:

    ```go
    var i int = 42
    var f float64 = float64(i) // Convertir int a float64
    var s string = string(i)    // Convertir int a string (no recomendado, mejor usar strconv)
    ```
18. ¿Qué son los tipos definidos por el usuario (*custom types*) y cuándo se usan?
    - a. Son tipos creados a partir de tipos existentes para agregar métodos o mejorar la legibilidad del código.
    - b. Son tipos que solo pueden ser usados en paquetes específicos.
    - c. Son tipos que no pueden tener métodos asociados.
    - d. No existen tipos definidos por el usuario en Go.

    Answer: a
    Explanation: En Go, los tipos definidos por el usuario (*custom types*) son tipos que se crean a partir de tipos existentes utilizando la palabra clave `type`. Estos tipos permiten agregar métodos específicos y mejorar la legibilidad del código al proporcionar nombres más significativos para ciertos conjuntos de datos. Los *custom types* son útiles cuando deseas encapsular comportamientos o restricciones adicionales sobre un tipo base. Por ejemplo:

    ```go
    type Age int

    func (a Age) IsAdult() bool {
        return a >= 18
    }
    ```
    En este ejemplo, `Age` es un tipo definido por el usuario basado en `int`, y tiene un método `IsAdult` asociado.
19. ¿Cómo implementas métodos en tipos definidos por el usuario?
    - a. Definiendo una función con un *receiver* del tipo definido por el usuario.
    - b. Usando la palabra clave `method` dentro del tipo.
    - c. No se pueden implementar métodos en tipos definidos por el usuario.
    - d. Usando la función `addMethod(Type, func)`.

    Answer: a
    Explanation: En Go, puedes implementar métodos en tipos definidos por el usuario definiendo una función que tiene un *receiver* del tipo definido por el usuario. El *receiver* se especifica entre paréntesis antes del nombre de la función y puede ser un valor o un puntero al tipo. Esto permite asociar comportamientos específicos con el tipo. Por ejemplo:

    ```go
    type Rectangle struct {
        Width, Height float64
    }

    // Método con receiver de valor
    func (r Rectangle) Area() float64 {
        return r.Width * r.Height
    }

    // Método con receiver de puntero
    func (r *Rectangle) Scale(factor float64) {
        r.Width *= factor
        r.Height *= factor
    }
    ```
20. ¿Cuál es la diferencia entre un *receiver value* y un *receiver pointer*?
    - a. Un *receiver value* recibe una copia del valor, mientras que un *receiver pointer* recibe una referencia al valor original, permitiendo modificarlo.
    - b. No hay diferencia, ambos son lo mismo.
    - c. Un *receiver value* solo puede usarse con tipos primitivos, mientras que un *receiver pointer* solo con structs.
    - d. Un *receiver value* es más eficiente en términos de memoria.

    Answer: a
    Explanation: En Go, un *receiver value* es un método que recibe una copia del valor del tipo al que está asociado. Esto significa que cualquier modificación realizada dentro del método no afectará al valor original fuera del método. Por otro lado, un *receiver pointer* es un método que recibe un puntero al valor del tipo, lo que permite modificar el valor original directamente desde el método. Usar un *receiver pointer* es útil cuando deseas cambiar el estado del objeto o cuando el tipo es grande y quieres evitar la sobrecarga de copiarlo. Por ejemplo:

    ```go
    type Counter struct {
        Count int
    }

    // Método con receiver de valor (no modifica el original)
    func (c Counter) Increment() {
        c.Count++
    }

    // Método con receiver de puntero (modifica el original)
    func (c *Counter) IncrementPointer() {
        c.Count++
    }
    ```

---

## 🔹 Sección 3: Interfaces y Polimorfismo

21. ¿Cómo defines una interfaz en Go?
    - a. Usando la palabra clave `interface` seguida de una lista de métodos.
    - b. Usando la palabra clave `type` seguida de una lista de métodos.
    - c. Usando la palabra clave `class` seguida de una lista de métodos.
    - d. No se pueden definir interfaces en Go.

    Answer: a
    Explanation: En Go, defines una interfaz usando la palabra clave `interface`, seguida del nombre de la interfaz y una lista de métodos entre llaves. Una interfaz especifica un conjunto de métodos que un tipo debe implementar para satisfacer esa interfaz. Por ejemplo:

    ```go
    type Shape interface {
        Area() float64
        Perimeter() float64
    }
    ```
22. ¿Cómo sabes si un tipo implementa una interfaz?
    - a. Si el tipo tiene todos los métodos definidos en la interfaz, entonces implementa la interfaz de forma implícita.
    - b. Si el tipo declara explícitamente que implementa la interfaz usando la palabra clave `implements`.
    - c. Si el tipo hereda de la interfaz.
    - d. No se pueden implementar interfaces en Go.

    Answer: a
    Explanation: En Go, un tipo implementa una interfaz de forma implícita si tiene todos los métodos definidos en esa interfaz. No es necesario declarar explícitamente que un tipo implementa una interfaz; simplemente debe cumplir con el contrato de métodos. Esto permite una mayor flexibilidad y facilita el uso de interfaces en el diseño del código. Por ejemplo, si tienes una interfaz `Shape` con métodos `Area()` y `Perimeter()`, cualquier tipo que defina estos métodos automáticamente satisface la interfaz `Shape`.
23. ¿Qué es el *duck typing* en Go?
    - a. Un concepto donde la compatibilidad de tipos se determina por la presencia de métodos, no por la herencia explícita.
    - b. Un patrón de diseño para crear objetos similares a patos.
    - c. Una técnica para optimizar el rendimiento de las interfaces.
    - d. No existe el *duck typing* en Go.

    Answer: a
    Explanation: El *duck typing* en Go es un concepto que se refiere a la idea de que la compatibilidad de tipos se determina por la presencia de métodos específicos, en lugar de por la herencia explícita o la declaración formal de implementación. La frase "si camina como un pato y suena como un pato, entonces es un pato" ilustra este concepto. En Go, si un tipo tiene los métodos necesarios para satisfacer una interfaz, se considera que implementa esa interfaz, independientemente de su estructura o nombre. Esto permite una mayor flexibilidad y facilita la creación de código modular y reutilizable.
24. ¿Qué diferencia hay entre una interfaz vacía `interface{}` y una interfaz específica?
    - a. `interface{}` puede contener cualquier tipo, mientras que una interfaz específica define un conjunto concreto de métodos que deben ser implementados.
    - b. No hay diferencia, ambos son lo mismo.
    - c. `interface{}` solo puede contener tipos primitivos, mientras que una interfaz específica puede contener structs.
    - d. `interface{}` es más eficiente en términos de rendimiento.

    Answer: a
    Explanation: En Go, una interfaz vacía `interface{}` es un tipo especial que puede contener valores de cualquier tipo, ya que no define ningún método. Esto la hace muy flexible para almacenar datos heterogéneos, pero también requiere aserciones de tipo para recuperar el valor original. Por otro lado, una interfaz específica define un conjunto concreto de métodos que un tipo debe implementar para satisfacer esa interfaz. Esto proporciona un contrato claro sobre el comportamiento esperado y permite un diseño más estructurado y seguro en el código.
25. ¿Qué pasa al comparar dos valores de tipo `interface{}`?
    - a. Se comparan los valores subyacentes y sus tipos; son iguales si ambos son del mismo tipo y tienen el mismo valor.
    - b. No se pueden comparar valores de tipo `interface{}`.
    - c. Se comparan las direcciones de memoria de los valores.
    - d. Siempre son considerados diferentes, independientemente de su contenido.

    Answer: a
    Explanation: En Go, al comparar dos valores de tipo `interface{}`, se comparan tanto los valores subyacentes como sus tipos. Dos valores de tipo `interface{}` son considerados iguales si ambos contienen valores del mismo tipo y esos valores son iguales según la comparación estándar para ese tipo. Si los tipos son diferentes, o si uno de los valores es `nil` mientras que el otro no lo es, entonces los valores no serán iguales. Si ambos valores son `nil`, entonces también se consideran iguales.
26. ¿Cómo realizas una aserción de tipo (*type assertion*)?
    - a. Usando la sintaxis `value.(Type)` para extraer el valor subyacente del tipo especificado.
    - b. Usando la función `assertType(value, Type)`.
    - c. Usando el operador `as` para realizar la aserción.
    - d. No se pueden realizar aserciones de tipo en Go.

    Answer: a
    Explanation: En Go, realizas una aserción de tipo (*type assertion*) utilizando la sintaxis `value.(Type)`, donde `value` es una variable de tipo `interface{}` y `Type` es el tipo al que deseas convertir el valor subyacente. Si la aserción es exitosa, obtienes el valor del tipo especificado; si no, se produce un pánico en tiempo de ejecución. Para evitar el pánico, puedes usar una forma segura de aserción que devuelve un segundo valor booleano indicando si la aserción fue exitosa:

    ```go
    var i interface{} = "hello"
    s, ok := i.(string) // s es "hello", ok es true
    n, ok := i.(int)    // n es 0, ok es false
    ```
27. ¿Qué es un *type switch* y para qué sirve?
    - a. Una estructura de control que permite ejecutar diferentes bloques de código según el tipo dinámico de una variable de interfaz.
    - b. Una función que convierte tipos automáticamente.
    - c. Un operador que compara tipos en tiempo de compilación.
    - d. No existe el *type switch* en Go.

    Answer: a
    Explanation: En Go, un *type switch* es una estructura de control que permite ejecutar diferentes bloques de código basados en el tipo dinámico de una variable de interfaz. Se utiliza para manejar múltiples tipos posibles que una variable puede contener, facilitando la ejecución de lógica específica para cada tipo. La sintaxis del *type switch* es similar a la de un switch normal, pero en lugar de comparar valores, compara tipos. Por ejemplo:

    ```go
    var i interface{} = 42

    switch v := i.(type) {
    case int:
        fmt.Println("Es un entero:", v)
    case string:
        fmt.Println("Es una cadena:", v)
    default:
        fmt.Println("Tipo desconocido")
    }
    ```
28. ¿Qué significa que las interfaces son satisfechas de forma implícita?
    - a. Un tipo satisface una interfaz si implementa todos los métodos de la interfaz, sin necesidad de una declaración explícita.
    - b. Un tipo debe declarar explícitamente que implementa una interfaz usando la palabra clave `implements`.
    - c. Las interfaces solo pueden ser satisfechas por tipos primitivos.
    - d. No se pueden satisfacer interfaces de forma implícita en Go.

    Answer: a
    Explanation: En Go, las interfaces son satisfechas de forma implícita, lo que significa que un tipo satisface una interfaz si implementa todos los métodos definidos en esa interfaz, sin necesidad de declarar explícitamente que implementa la interfaz. Esto permite una mayor flexibilidad y facilita el diseño del código, ya que cualquier tipo que cumpla con el contrato de métodos puede ser utilizado donde se espera esa interfaz. Por ejemplo, si tienes una interfaz `Shape` con un método `Area()`, cualquier tipo que defina ese método automáticamente satisface la interfaz `Shape`.
29. ¿Qué sucede si una interfaz contiene un método que un tipo no implementa?
    - a. El tipo no satisface la interfaz y no puede ser usado donde se espera esa interfaz.
    - b. El programa compila pero muestra una advertencia.
    - c. El programa entra en pánico (*panic*) en tiempo de ejecución.
    - d. El método faltante se ignora automáticamente.

    Answer: a
    Explanation: En Go, si una interfaz contiene un método que un tipo no implementa, entonces ese tipo no satisface la interfaz y no puede ser utilizado en contextos donde se espera esa interfaz. Esto es verificado en tiempo de compilación, lo que ayuda a garantizar que los tipos utilizados cumplen con los contratos definidos por las interfaces. Si intentas asignar un valor de un tipo que no satisface la interfaz a una variable de esa interfaz, el compilador generará un error.
30. ¿Qué pasa si una interfaz contiene otra interfaz?
    - a. La interfaz que contiene otra interfaz hereda todos los métodos de la interfaz contenida.
    - b. No se pueden anidar interfaces en Go.
    - c. La interfaz contenida se ignora automáticamente.
    - d. La interfaz que contiene otra interfaz solo puede usar los métodos de la interfaz contenida.

    Answer: a
    Explanation: En Go, una interfaz puede contener otra interfaz, lo que significa que la interfaz que contiene hereda todos los métodos de la interfaz contenida. Esto permite crear interfaces más complejas y reutilizables al combinar múltiples interfaces en una sola. Por ejemplo:

    ```go
    type Reader interface {
        Read(p []byte) (n int, err error)
    }

    type Writer interface {
        Write(p []byte) (n int, err error)
    }

    type ReadWriter interface {
        Reader
        Writer
    }
    ```
    En este ejemplo, `ReadWriter` hereda los métodos `Read` y `Write` de las interfaces `Reader` y `Writer`, respectivamente.

---

## 🔹 Sección 4: Concurrencia y Sincronización

31. ¿Qué es una *goroutine* y cómo se lanza una?
    - a. Una *goroutine* es una función que se ejecuta de forma concurrente y se lanza usando la palabra clave `go` antes de la llamada a la función.
    - b. Una *goroutine* es un hilo del sistema operativo y se lanza usando la función `startThread()`.
    - c. Una *goroutine* es un proceso independiente y se lanza usando la palabra clave `process`.
    - d. No existen las *goroutines* en Go.

    Answer: a
    Explanation: En Go, una *goroutine* es una función que se ejecuta de forma concurrente, permitiendo que múltiples tareas se realicen al mismo tiempo dentro del mismo programa. Las *goroutines* son ligeras y gestionadas por el runtime de Go, lo que las hace más eficientes que los hilos del sistema operativo. Para lanzar una *goroutine*, simplemente colocas la palabra clave `go` antes de la llamada a la función. Por ejemplo:

    ```go
    func sayHello() {
        fmt.Println("Hello, World!")
    }

    func main() {
        go sayHello() // Lanzar la goroutine
        time.Sleep(time.Second) // Esperar para que la goroutine termine
    }
    ```
32. ¿Qué es un *channel* y cómo se usa para comunicar goroutines?
    - a. Un *channel* es una estructura que permite la comunicación segura entre goroutines, y se usa con los operadores `<-` para enviar y recibir datos.
    - b. Un *channel* es una función que sincroniza el acceso a variables compartidas.
    - c. Un *channel* es un tipo de dato que almacena múltiples valores.
    - d. No existen los *channels* en Go.

    Answer: a
    Explanation: En Go, un *channel* es una estructura que permite la comunicación segura entre goroutines, facilitando el paso de datos de una goroutine a otra. Los *channels* son tipos de datos que se crean usando la función `make(chan Type)`, donde `Type` es el tipo de datos que el canal transportará. Para enviar datos a un canal, se utiliza el operador `<-` en la forma `channel <- value`, y para recibir datos de un canal, se usa en la forma `value := <-channel`. Los *channels* ayudan a sincronizar las goroutines y evitar condiciones de carrera al proporcionar un mecanismo seguro para compartir datos. Por ejemplo:

    ```go
    func worker(ch chan int) {
        ch <- 42 // Enviar dato al canal
    }

    func main() {
        ch := make(chan int)
        go worker(ch) // Lanzar goroutine
        result := <-ch // Recibir dato del canal
        fmt.Println(result) // Imprime 42
    }
    ```
33. ¿Cuál es la diferencia entre canales con buffer y sin buffer?
    - a. Un canal sin buffer bloquea al enviar si no hay un receptor listo, mientras que un canal con buffer permite enviar hasta su capacidad antes de bloquear.
    - b. No hay diferencia, ambos funcionan igual.
    - c. Un canal con buffer es más lento que uno sin buffer.
    - d. Un canal sin buffer solo puede usarse dentro de una goroutine.

    Answer: a
    Explanation: En Go, la diferencia entre canales con buffer y sin buffer radica en cómo manejan el envío y recepción de datos. Un canal sin buffer (creado con `make(chan Type)`) bloquea al enviar datos si no hay una goroutine receptora lista para recibir el dato. Esto significa que el envío y la recepción deben ocurrir simultáneamente para que la operación tenga éxito.

    Por otro lado, un canal con buffer (creado con `make(chan Type, capacity)`, donde `capacity` es un número entero que define el tamaño del buffer) permite enviar datos hasta su capacidad antes de bloquear. Esto significa que puedes enviar varios valores al canal sin necesidad de que haya una goroutine receptora lista, hasta que el buffer esté lleno. Una vez que el buffer está lleno, cualquier intento adicional de enviar datos bloqueará la goroutine hasta que se reciba algún dato del canal.

    Ejemplo de canal sin buffer:
    ```go
    ch := make(chan int) // Canal sin buffer
    go func() {
        ch <- 1 // Bloquea hasta que alguien reciba
    }()
    fmt.Println(<-ch) // Recibe el dato
    ```

    Ejemplo de canal con buffer:
    ```go
    ch := make(chan int, 2) // Canal con buffer de capacidad 2
    ch <- 1 // No bloquea
    ch <- 2 // No bloquea
    // ch <- 3 // Esto bloquearía porque el buffer está lleno
    fmt.Println(<-ch) // Recibe 1
    fmt.Println(<-ch) // Recibe 2
    ```
34. ¿Qué sucede si envías datos a un canal cerrado?
    - a. Se produce un pánico (*panic*) en tiempo de ejecución.
    - b. Los datos se ignoran automáticamente.
    - c. El canal se reabre automáticamente.
    - d. No se puede enviar datos a un canal cerrado.

    Answer: a
    Explanation: En Go, si intentas enviar datos a un canal que ha sido cerrado, se produce un pánico (*panic*) en tiempo de ejecución. Esto es porque un canal cerrado ya no puede aceptar nuevos datos, y cualquier intento de enviar a un canal cerrado es considerado un error grave. Para evitar este pánico, es común verificar si un canal está cerrado antes de enviar datos, o manejar la situación adecuadamente en el diseño del programa. Por ejemplo: 

    ```go
35. ¿Qué pasa si cierras un canal más de una vez?
    - a. Se produce un pánico (*panic*) en tiempo de ejecución.
    - b. El canal se reabre automáticamente.
    - c. El segundo cierre se ignora automáticamente.
    - d. No se puede cerrar un canal más de una vez.

    Answer: a
    Explanation: En Go, si intentas cerrar un canal que ya ha sido cerrado, se produce un pánico (*panic*) en tiempo de ejecución. Esto es porque cerrar un canal es una operación que solo debe realizarse una vez para indicar que no se enviarán más datos a través de ese canal. Intentar cerrar un canal más de una vez es considerado un error grave y resulta en un pánico. Para evitar este problema, es importante asegurarse de que el canal solo se cierre una vez, generalmente por la goroutine que lo creó o gestionó.
36. ¿Cómo utilizas la palabra clave `select` en Go?
    - a. `select` permite esperar en múltiples operaciones de canal, ejecutando la que esté lista primero.
    - b. `select` es una función que convierte tipos automáticamente.
    - c. `select` es un operador que compara tipos en tiempo de compilación.
    - d. No existe la palabra clave `select` en Go.

    Answer: a
    Explanation: En Go, la palabra clave `select` se utiliza para esperar en múltiples operaciones de canal, permitiendo que una goroutine maneje varias comunicaciones de canal simultáneamente. Cuando se usa `select`, se evalúan todas las operaciones de canal dentro del bloque `select`, y se ejecuta la primera operación que esté lista (ya sea enviar o recibir). Si ninguna operación está lista, la goroutine se bloquea hasta que una lo esté. Esto es útil para manejar múltiples canales de manera eficiente y reactiva. Por ejemplo:

    ```go
    ch1 := make(chan int)
    ch2 := make(chan int)

    go func() {
        ch1 <- 1
    }()
    go func() {
        ch2 <- 2
    }()

    select {
    case msg1 := <-ch1:
        fmt.Println("Received from ch1:", msg1)
    case msg2 := <-ch2:
        fmt.Println("Received from ch2:", msg2)
    }
    ```
37. ¿Qué es el patrón *fan-in* y *fan-out* en concurrencia?
    - a. *Fan-out* distribuye trabajo a múltiples goroutines, mientras que *fan-in* recoge resultados de múltiples goroutines en un solo canal.
    - b. *Fan-in* distribuye trabajo a múltiples goroutines, mientras que *fan-out* recoge resultados de múltiples goroutines en un solo canal.
    - c. Ambos patrones son lo mismo y se usan indistintamente.
    - d. No existen los patrones *fan-in* y *fan-out* en Go.

    Answer: a
    Explanation: En Go, el patrón *fan-out* se refiere a la distribución de trabajo a múltiples goroutines para realizar tareas concurrentes. Esto permite que varias goroutines trabajen en paralelo, aumentando la eficiencia y el rendimiento del programa. Por otro lado, el patrón *fan-in* se refiere a la recolección de resultados de múltiples goroutines en un solo canal. Esto permite consolidar los resultados de las tareas concurrentes en un solo lugar para su procesamiento posterior. Estos patrones son comunes en programas concurrentes para gestionar la distribución y recolección de trabajo de manera efectiva.
38. ¿Cómo se evita una *race condition* en Go?
    - a. Usando mecanismos de sincronización como *channels* y el paquete `sync` (por ejemplo, `sync.Mutex`).
    - b. No se pueden evitar las *race condition* en GO.
    - c. Usando variables globales para compartir datos entre goroutines.
    - d. Usando la palabra clave `safe` antes de las funciones.
    Answer: a
    Explanation: En Go, las *race condition* pueden evitarse utilizando mecanismos de sincronización como *channels* y el paquete `sync`. Los *channels* permiten la comunicación segura entre goroutines, evitando el acceso concurrente a datos compartidos. Además, el paquete `sync` proporciona herramientas como `sync.Mutex`, que permite bloquear secciones críticas del código para asegurar que solo una goroutine pueda acceder a ciertos datos a la vez. Otros mecanismos incluyen `sync.RWMutex` para lecturas concurrentes y escrituras exclusivas, y `sync.WaitGroup` para coordinar la finalización de múltiples goroutines. Estos enfoques ayudan a garantizar la integridad de los datos y prevenir condiciones de carrera en programas concurrentes.
39. ¿Qué herramientas provee Go para detectar *race conditions*?  
40. Explica cómo funciona `sync.WaitGroup` y su propósito.

---

## 🔹 Sección 5: Errores y Manejo de Excepciones

41. ¿Cómo se maneja el error en Go?
    - a. Go utiliza valores de error retornados por funciones para manejar errores, en lugar de excepciones.
    - b. Go utiliza bloques `try-catch` para manejar errores.
    - c. Go no tiene un mecanismo para manejar errores.
    - d. Go utiliza la palabra clave `throw` para lanzar errores.

    Answer: a
    Explanation: En Go, el manejo de errores se realiza mediante el uso de valores de error retornados por funciones, en lugar de utilizar excepciones como en otros lenguajes. Las funciones que pueden producir un error generalmente devuelven un valor adicional del tipo `error`, que puede ser `nil` si no hubo error o contener información sobre el error ocurrido. El patrón común es verificar si el valor de error es `nil` antes de proceder con la lógica normal del programa. Esto fomenta un manejo explícito y claro de los errores, mejorando la legibilidad y mantenibilidad del código. Por ejemplo:

    ```go
    func divide(a, b float64) (float64, error) {
        if b == 0 {
            return 0, fmt.Errorf("division by zero")
        }
        return a / b, nil
    }

    result, err := divide(10, 0)
    if err != nil {
        fmt.Println("Error:", err)
    } else {
        fmt.Println("Result:", result)
    }
    ```
42. ¿Qué diferencia hay entre `panic`, `recover` y `defer`?
    - a. `panic` detiene la ejecución del programa, `recover` captura un pánico y permite continuar, y `defer` pospone la ejecución de una función hasta que la función que la contiene termine.
    - b. No hay diferencia, todos son lo mismo.
    - c. `panic` maneja errores, `recover` lanza errores, y `defer` crea goroutines.
    - d. `panic` solo se usa en pruebas, `recover` solo en producción, y `defer` solo en funciones anónimas.

    Answer: a
    Explanation: En Go, `panic`, `recover` y `defer` son mecanismos relacionados con el manejo de errores y la gestión del flujo de control en situaciones excepcionales.

    - `panic`: Es una función que detiene la ejecución normal del programa cuando ocurre un error grave o una condición inesperada. Cuando se llama a `panic`, el programa comienza a deshacer la pila de llamadas (stack unwinding) y busca cualquier función diferida (`defer`) para ejecutarlas antes de terminar el programa.

    - `recover`: Es una función que se utiliza dentro de una función diferida para capturar un pánico y permitir que el programa continúe su ejecución normal. Si se llama a `recover` dentro de una función diferida durante un pánico, devuelve el valor pasado a `panic`, permitiendo manejar el error sin que el programa termine abruptamente.

    - `defer`: Es una palabra clave que pospone la ejecución de una función hasta que la función que la contiene termine. Las funciones diferidas se ejecutan en orden LIFO (Last In, First Out) cuando la función que las contiene retorna, ya sea normalmente o debido a un pánico.

    Estos tres mecanismos juntos permiten manejar situaciones excepcionales de manera controlada en Go.
43. ¿Qué pasa si no manejas un error en Go?
    - a. El error se propaga hacia arriba en la pila de llamadas, y si no se maneja en ningún nivel, puede llevar a un pánico.
    - b. El programa continúa ejecutándose sin problemas.
    - c. El compilador genera un error y no permite compilar el programa.
    - d. El error se ignora automáticamente.

    Answer: a
    Explanation: En Go, si no manejas un error retornado por una función, el error se propaga hacia arriba en la pila de llamadas. Si el error no se maneja en ningún nivel, puede llevar a un pánico si el código intenta continuar ejecutándose con un estado inválido o inesperado. Es una buena práctica siempre verificar y manejar los errores inmediatamente después de que una función los retorne para evitar comportamientos impredecibles en el programa.
44. ¿Cómo se implementa un tipo de error personalizado?
    - a. Definiendo un struct que implementa el método `Error() string` de la interfaz `error`.
    - b. Usando la función `newError(Type, message)`.
    - c. No se pueden crear tipos de error personalizados en Go.
    - d. Usando la palabra clave `customError` antes de la declaración del struct.

    Answer: a
    Explanation: En Go, puedes implementar un tipo de error personalizado definiendo un struct que implementa el método `Error() string` de la interfaz `error`. Al implementar este método, tu struct satisface la interfaz `error`, lo que te permite crear errores con información adicional o comportamientos específicos. Aquí tienes un ejemplo:

    ```go
    type MyError struct {
        Code    int
        Message string
    }

    func (e MyError) Error() string {
        return fmt.Sprintf("Error %d: %s", e.Code, e.Message)
    }

    func doSomething() error {
        return MyError{Code: 404, Message: "Not Found"}
    }

    func main() {
        err := doSomething()
        if err != nil {
            fmt.Println(err) // Imprime: Error 404: Not Found
        }
    }
    ```
45. ¿Qué función se usa para envolver errores (`fmt.Errorf`) y por qué?
    - a. `fmt.Errorf` se usa para crear un nuevo error con formato, permitiendo incluir contexto adicional al error original.
    - b. `fmt.Errorf` se usa para convertir errores en cadenas de texto.
    - c. `fmt.Errorf` se usa para lanzar errores automáticamente.
    - d. No existe la función `fmt.Errorf` en Go.

    Answer: a
    Explanation: En Go, la función `fmt.Errorf` se utiliza para crear un nuevo error con formato, lo que permite incluir contexto adicional al error original. Esta función es útil cuando deseas proporcionar más información sobre el error, como detalles específicos del contexto en el que ocurrió. Al usar `fmt.Errorf`, puedes combinar mensajes de error y valores dinámicos, lo que facilita la depuración y el manejo de errores en tu código. Por ejemplo:

    ```go
    func readFile(filename string) error {
        // Simulación de un error al leer el archivo
        return fmt.Errorf("failed to read file %s: %w", filename, os.ErrNotExist)
    }

    func main() {
        err := readFile("nonexistent.txt")
        if err != nil {
            fmt.Println(err) // Imprime: failed to read file nonexistent.txt: file does not exist
        }
    }
    ```
46. ¿Qué diferencia hay entre `log.Fatal` y `panic`?
    - a. `log.Fatal` registra el error y termina el programa, mientras que `panic` detiene la ejecución y puede ser recuperado con `recover`.
    - b. No hay diferencia, ambos hacen lo mismo.
    - c. `log.Fatal` solo se usa en pruebas, mientras que `panic` se usa en producción.
    - d. `log.Fatal` crea un nuevo hilo, mientras que `panic` no.

    Answer: a
    Explanation: En Go, `log.Fatal` y `panic` son dos mecanismos diferentes para manejar situaciones de error graves, pero tienen comportamientos distintos:

    - `log.Fatal`: Esta función del paquete `log` registra un mensaje de error y luego llama a `os.Exit(1)`, lo que termina inmediatamente el programa con un código de salida no cero. No permite la recuperación del estado del programa ni la ejecución de funciones diferidas (`defer`). Es útil para errores críticos donde no tiene sentido continuar la ejecución del programa.

    - `panic`: Esta función detiene la ejecución normal del programa y comienza a deshacer la pila de llamadas (stack unwinding). Durante este proceso, se ejecutan todas las funciones diferidas (`defer`) en orden LIFO (Last In, First Out). Si no se captura el pánico con `recover`, el programa terminará con un mensaje de error. Sin embargo, si se utiliza `recover` dentro de una función diferida, es posible capturar el pánico y permitir que el programa continúe su ejecución.

    En resumen, `log.Fatal` termina el programa inmediatamente sin posibilidad de recuperación, mientras que `panic` permite la recuperación mediante `recover` y ejecuta funciones diferidas antes de terminar.
47. ¿Por qué Go no utiliza excepciones como otros lenguajes?
    - a. Go prefiere un manejo explícito de errores mediante valores de error retornados para mejorar la claridad y mantenibilidad del código.
    - b. Go no tiene un mecanismo para manejar errores.
    - c. Las excepciones son demasiado lentas en Go.
    - d. Go utiliza excepciones, pero de manera diferente.

    Answer: a
    Explanation: Go no utiliza excepciones como otros lenguajes porque prefiere un manejo explícito de errores mediante valores de error retornados por funciones. Este enfoque mejora la claridad y mantenibilidad del código, ya que obliga a los desarrolladores a manejar los errores de manera consciente y directa. Al retornar errores como valores, el flujo del programa se vuelve más predecible y fácil de seguir, evitando la complejidad y ambigüedad que a menudo acompañan a las excepciones en otros lenguajes. Además, este patrón fomenta la escritura de código más robusto y facilita la depuración al hacer que los errores sean visibles en el lugar donde ocurren.
48. ¿Qué patrón se recomienda para propagar errores en funciones anidadas?
    - a. Retornar el error directamente y envolverlo con contexto adicional usando `fmt.Errorf` si es necesario.
    - b. Usar `panic` para propagar errores automáticamente.
    - c. Ignorar los errores en funciones anidadas.
    - d. Usar variables globales para almacenar errores.

    Answer: a
    Explanation: En Go, el patrón recomendado para propagar errores en funciones anidadas es retornar el error directamente y, si es necesario, envolverlo con contexto adicional utilizando `fmt.Errorf`. Esto permite que cada función maneje su propio contexto de error y proporcione información útil sobre dónde y por qué ocurrió el error. Al retornar el error hacia arriba en la pila de llamadas, se facilita la identificación y manejo del error en niveles superiores del código. Este enfoque promueve un manejo explícito y claro de los errores, mejorando la legibilidad y mantenibilidad del código. Por ejemplo:

    ```go
    func readFile(filename string) ([]byte, error) {
        data, err := os.ReadFile(filename)
        if err != nil {
            return nil, fmt.Errorf("readFile: failed to read %s: %w", filename, err)
        }
        return data, nil
    }

    func processFile(filename string) error {
        data, err := readFile(filename)
        if err != nil {
            return fmt.Errorf("processFile: %w", err)
        }
        // Procesar los datos...
        return nil
    }
    ```
49. ¿Cómo se usa `errors.Is` y `errors.As` para manejar errores?
    - a. `errors.Is` verifica si un error es igual a otro, mientras que `errors.As` permite extraer un error de un tipo específico.
    - b. No existen `errors.Is` y `errors.As` en Go.
    - c. `errors.Is` convierte errores en cadenas de texto, y `errors.As` lanza errores automáticamente.
    - d. Ambos son funciones para crear nuevos errores.

    Answer: a
    Explanation: En Go, `errors.Is` y `errors.As` son funciones del paquete `errors` que se utilizan para manejar errores de manera más efectiva.

    - `errors.Is`: Esta función se utiliza para verificar si un error es igual a otro error específico. Es útil cuando deseas comprobar si un error retornado coincide con un error conocido, incluso si el error original ha sido envuelto con contexto adicional usando `fmt.Errorf`. La función recorre la cadena de errores envueltos para encontrar una coincidencia.

    - `errors.As`: Esta función se utiliza para extraer un error de un tipo específico de una cadena de errores envueltos. Permite verificar si un error puede ser convertido a un tipo concreto y, si es así, asignarlo a una variable del tipo deseado. Esto es útil cuando necesitas acceder a campos o métodos específicos de un tipo de error personalizado.

    Ejemplo de uso:

    ```go
    var ErrNotFound = errors.New("not found")

    func findItem(id int) error {
        // Simulación de un error
        return fmt.Errorf("findItem: %w", ErrNotFound)
    }

    func main() {
        err := findItem(42)
        if errors.Is(err, ErrNotFound) {
            fmt.Println("Item not found")
        }

        var myErr *MyError
        if errors.As(err, &myErr) {
            fmt.Println("Custom error:", myErr.Code)
        }
    }
    ```
50. ¿Qué ventaja tiene usar *sentinel errors*?
    - a. Permiten identificar errores específicos de manera sencilla y consistente en todo el código.
    - b. No tienen ninguna ventaja, son obsoletos.
    - c. Son más rápidos que otros tipos de errores.
    - d. Permiten ignorar errores automáticamente.

    Answer: a
    Explanation: En Go, los *sentinel errors* son errores predefinidos que se utilizan para identificar errores específicos de manera sencilla y consistente en todo el código. La ventaja de usar *sentinel errors* es que proporcionan una forma clara y uniforme de manejar ciertos tipos de errores comunes, facilitando la comparación y verificación de errores en diferentes partes del programa. Al definir un error como una variable global (por ejemplo, `var ErrNotFound = errors.New("not found")`), puedes usarlo en múltiples funciones y compararlo fácilmente con otros errores utilizando `errors.Is`. Esto mejora la legibilidad del código y ayuda a mantener un manejo de errores coherente en toda la aplicación.

---

## 🔹 Sección 6: Testing, Rendimiento y Buenas Prácticas

51. ¿Cómo se estructuran las pruebas unitarias en Go?
    - a. Las pruebas unitarias se escriben en archivos con el sufijo `_test.go` y utilizan el paquete `testing`.
    - b. Las pruebas unitarias se escriben en archivos con el sufijo `.test` y utilizan el paquete `unittest`.
    - c. No se pueden escribir pruebas unitarias en Go.
    - d. Las pruebas unitarias se escriben en el mismo archivo que el código fuente.

    Answer: a
    Explanation: En Go, las pruebas unitarias se estructuran escribiendo funciones de prueba en archivos con el sufijo `_test.go`. Estas funciones deben tener un nombre que comience con `Test` y aceptar un parámetro de tipo `*testing.T`. El paquete `testing` proporciona herramientas y funciones para escribir y ejecutar pruebas, así como para reportar resultados. Al seguir esta convención, las herramientas de Go pueden identificar y ejecutar automáticamente las pruebas cuando se utiliza el comando `go test`. Por ejemplo:

    ```go
    // archivo: math.go
    package math

    func Add(a, b int) int {
        return a + b
    }

    // archivo: math_test.go
    package math

    import "testing"

    func TestAdd(t *testing.T) {
        result := Add(2, 3)
        if result != 5 {
            t.Errorf("Expected 5, got %d", result)
        }
    }
    ```
52. ¿Cómo ejecutas todas las pruebas del módulo desde la línea de comandos?
    - a. Usando el comando `go test ./...` en la terminal.
    - b. Usando el comando `go run tests`.
    - c. Usando el comando `go build`.
    - d. Usando el comando `go check`.

    Answer: a
    Explanation: Para ejecutar todas las pruebas del módulo en Go, se utiliza el comando `go test ./...` desde la línea de comandos. Este comando busca y ejecuta todas las funciones de prueba en los archivos con el sufijo `_test.go` en el módulo y sus subdirectorios. Es la forma estándar y recomendada para ejecutar pruebas unitarias y de integración en proyectos Go.

54. ¿Qué paquete se usa para *benchmarking*?
    - a. El paquete `testing` se utiliza para escribir benchmarks en Go.
    - b. El paquete `benchmark` se utiliza para escribir benchmarks en Go.
    - c. No se pueden escribir benchmarks en Go.
    - d. El paquete `performance` se utiliza para escribir benchmarks en Go.

    Answer: a
    Explanation: En Go, el paquete `testing` se utiliza para escribir benchmarks. Las funciones de benchmark deben tener un nombre que comience con `Benchmark` y aceptar un parámetro de tipo `*testing.B`. Estas funciones permiten medir el rendimiento de bloques de código específicos, ejecutándolos múltiples veces para obtener estadísticas sobre su tiempo de ejecución. Al igual que las pruebas unitarias, las funciones de benchmark se colocan en archivos con el sufijo `_test.go`. Por ejemplo:

    ```go
    func BenchmarkAdd(b *testing.B) {
        for i := 0; i < b.N; i++ {
            Add(2, 3)
        }
    }
    ```
54. ¿Cómo defines una *table-driven test*? 
    - a. Una *table-driven test* utiliza una tabla de casos de prueba para ejecutar la misma lógica de prueba con diferentes entradas y salidas esperadas.
    - b. Una *table-driven test* es una prueba que se ejecuta en una base de datos.
    - c. No existen las *table-driven tests* en Go.
    - d. Una *table-driven test* es una prueba que se ejecuta en paralelo.

    Answer: a
    Explanation: En Go, una *table-driven test* es un patrón de prueba que utiliza una tabla (generalmente un slice de structs) para definir múltiples casos de prueba, cada uno con diferentes entradas y salidas esperadas. Este enfoque permite ejecutar la misma lógica de prueba para cada caso definido en la tabla, lo que mejora la legibilidad y mantenibilidad del código de prueba. Al iterar sobre la tabla, puedes verificar que la función bajo prueba se comporte correctamente para todas las combinaciones de entrada y salida especificadas. Aquí tienes un ejemplo:

    ```go
    func TestAdd(t *testing.T) {
        tests := []struct {
            a, b     int
            expected int
        }{
            {2, 3, 5},
            {0, 0, 0},
            {-1, 1, 0},
            {10, 5, 15},
        }

        for _, tt := range tests {
            result := Add(tt.a, tt.b)
            if result != tt.expected {
                t.Errorf("Add(%d, %d) = %d; want %d", tt.a, tt.b, result, tt.expected)
            }
        }
    }
    ```
55. ¿Qué hace el flag \`-race\` durante la ejecución de pruebas?
    - a. Activa el detector de condiciones de carrera, analizando el acceso concurrente a variables compartidas y reportando posibles \`race conditions\` en tiempo de ejecución.
    - b. Optimiza la ejecución de pruebas para mayor velocidad.
    - c. Permite ejecutar pruebas en paralelo sin restricciones.
    - d. Ignora errores de concurrencia en el código.

    Answer: a
    Explanation: El flag \`-race\` en Go activa el detector de condiciones de carrera durante la ejecución de pruebas. Analiza el acceso concurrente a variables compartidas y reporta posibles \`race conditions\` en tiempo de ejecución, ayudando a identificar y corregir errores de concurrencia en el código.

56. ¿Cómo se organiza un proyecto grande en Go (paquetes, módulos)?
    - a. Un proyecto grande se organiza en múltiples paquetes, cada uno en su propio directorio, y se gestiona con *Go modules* para manejar dependencias.
    - b. Un proyecto grande debe estar en un solo archivo para facilitar la gestión.
    - c. No se pueden organizar proyectos grandes en Go.
    - d. Un proyecto grande se organiza usando clases y objetos.

    Answer: a
    Explanation: En Go, un proyecto grande se organiza en múltiples paquetes, cada uno ubicado en su propio directorio dentro del árbol de archivos del proyecto. Cada paquete contiene archivos fuente relacionados que definen tipos, funciones y métodos específicos a esa funcionalidad. Además, Go utiliza *Go modules* para gestionar las dependencias del proyecto, lo que permite especificar versiones de bibliotecas externas y facilita la construcción y distribución del código. Los módulos se inicializan con el comando `go mod init`, creando un archivo `go.mod` que define el módulo y sus dependencias. Esta estructura modular ayuda a mantener el código organizado, reutilizable y fácil de mantener a medida que el proyecto crece.
57. ¿Qué es un *Go module* y cómo se inicializa?
    - a. Un *Go module* es una colección de paquetes versionados, y se inicializa con el comando `go mod init <module-name>`.
    - b. Un *Go module* es un archivo ejecutable, y se inicializa con el comando `go build`.
    - c. No existen los *Go modules* en Go.
    - d. Un *Go module* es una función especial que gestiona dependencias automáticamente.

    Answer: a
    Explanation: Un *Go module* es una colección de paquetes versionados que permite gestionar las dependencias de un proyecto Go de manera eficiente. Los módulos facilitan la distribución y reutilización del código, ya que cada módulo puede especificar sus propias dependencias y versiones en un archivo `go.mod`. Para inicializar un *Go module*, se utiliza el comando `go mod init <module-name>`, donde `<module-name>` es el nombre del módulo, generalmente basado en la ruta del repositorio donde se alojará el código. Este comando crea el archivo `go.mod` en el directorio actual, estableciendo el módulo y permitiendo la gestión de dependencias a través de comandos como `go get` y `go mod tidy`.
58. ¿Qué herramientas ofrece Go para formatear y analizar código (`go fmt`, `go vet`)?
    - a. `go fmt` formatea el código según las convenciones de estilo de Go, y `go vet` analiza el código en busca de errores comunes y problemas potenciales.
    - b. No existen herramientas para formatear y analizar código en Go.
    - c. `go fmt` compila el código, y `go vet` ejecuta pruebas unitarias.
    - d. Ambas herramientas son obsoletas y no se usan en Go.

    Answer: a
    Explanation: En Go, `go fmt` es una herramienta que formatea el código fuente automáticamente según las convenciones de estilo establecidas por la comunidad de Go. Al ejecutar `go fmt`, el código se ajusta para mejorar la legibilidad y mantener un estilo consistente en todo el proyecto. Por otro lado, `go vet` es una herramienta que analiza el código en busca de errores comunes y problemas potenciales, como usos incorrectos de variables, llamadas a funciones con argumentos incorrectos, o problemas de concurrencia. Ambas herramientas son esenciales para mantener la calidad del código y se utilizan comúnmente durante el desarrollo para asegurar que el código sea limpio y libre de errores evidentes.
59. ¿Qué es la *garbage collection* y cómo impacta el rendimiento?
    - a. La *garbage collection* es un mecanismo automático de gestión de memoria que libera memoria no utilizada, pero puede introducir pausas que afectan el rendimiento.
    - b. La *garbage collection* es un proceso manual que los desarrolladores deben ejecutar para liberar memoria.
    - c. No existe la *garbage collection* en Go.
    - d. La *garbage collection* mejora el rendimiento eliminando todos los errores en el código.

    Answer: a
    Explanation: La *garbage collection* (recolección de basura) en Go es un mecanismo automático de gestión de memoria que se encarga de liberar memoria que ya no está siendo utilizada por el programa. Esto ayuda a prevenir fugas de memoria y facilita la gestión de recursos, ya que los desarrolladores no necesitan preocuparse por liberar memoria manualmente. Sin embargo, la *garbage collection* puede introducir pausas en la ejecución del programa mientras se realiza la recolección, lo que puede afectar el rendimiento, especialmente en aplicaciones con alta concurrencia o requisitos de baja latencia. Go ha optimizado su *garbage collector* para minimizar estas pausas, pero es importante considerar su impacto al diseñar sistemas de alto rendimiento.
60. Menciona tres buenas prácticas para escribir código idiomático en Go.
    - a. Usar nombres claros y concisos para variables y funciones, manejar errores explícitamente, y aprovechar las características del lenguaje como *interfaces* y *goroutines*.
    - b. Usar variables globales para compartir datos, ignorar errores, y evitar el uso de *interfaces*.
    - c. Escribir todo el código en un solo archivo, usar comentarios excesivos, y evitar la concurrencia.
    - d. No seguir ninguna convención y escribir código de cualquier manera.

    Answer: a
    Explanation: Tres buenas prácticas para escribir código idiomático en Go incluyen:

    1. Usar nombres claros y concisos para variables, funciones y paquetes: Esto mejora la legibilidad del código y facilita su comprensión por parte de otros desarrolladores.

    2. Manejar errores explícitamente: En Go, es fundamental verificar y manejar los errores retornados por las funciones de manera clara y directa, lo que ayuda a mantener la robustez del programa.

    3. Aprovechar las características del lenguaje: Utilizar *interfaces* para definir comportamientos comunes, emplear *goroutines* para la concurrencia, y utilizar *channels* para la comunicación entre goroutines son prácticas que aprovechan al máximo las capacidades de Go.

    Seguir estas prácticas contribuye a escribir código limpio, eficiente y mantenible en Go.

---

🧩 **Sugerencia de uso:**
- Usa este cuestionario como guía de repaso antes de una entrevista técnica.  
- Puedes responder en formato ensayo o crear opciones múltiples.  
- Complementa con ejercicios prácticos para reforzar cada sección.

