# golang-interview-questions-and-answers

## 🧠 Cuestionario de Programación en Go (Golang) – Nivel Intermedio y Avanzado

Este cuestionario está diseñado para evaluar conocimientos sólidos en Golang, desde fundamentos hasta concurrencia, interfaces, testing y buenas prácticas.

---

## 🔹 Sección 1: Fundamentos del Lenguaje

1. ¿Qué diferencia hay entre un *array* y un *slice* en Go?  
    - a.  
    - b.
    - c.
    - d.

    Answer: a
    Explanation: 
2. ¿Qué sucede si intentas acceder a un índice fuera del rango en un *array*?  
3. ¿Cómo se declara una constante tipada y una no tipada?  
4. Explica qué es una variable *zero-value* en Go.  
5. ¿Qué diferencia hay entre `new()` y `make()`?  
6. ¿Qué significa que Go es un lenguaje con *tipado estático* pero *inferido*?  
7. ¿Qué es una función variádica? Da un ejemplo.  
8. ¿Qué sucede si no usas una variable en una función?  
9. ¿Qué diferencia hay entre `:=` y `var`?  
10. ¿Qué es el *shadowing* de variables?

---

## 🔹 Sección 2: Estructuras de Datos y Tipos

11. ¿Cómo defines un *struct* y cómo accedes a sus campos?  
12. ¿Cómo creas un puntero a un *struct* y cómo accedes a sus campos?  
13. ¿Qué es una *etiqueta de campo (tag)* en un *struct* y para qué se usa?  
14. ¿Qué pasa al copiar un *struct* por valor?  
15. Explica la diferencia entre *value types* y *reference types* en Go.  
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

