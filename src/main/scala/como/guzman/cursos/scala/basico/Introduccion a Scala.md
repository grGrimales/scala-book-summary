# A Scalable Language

 ## Introducciń a Scala

- **Nombre y Propósito**: Scala significa "lenguaje escalable". Fue diseñado para crecer según las demandas de sus
  usuarios, adecuado tanto para escribir pequeños scripts como para construir grandes sistemas.

- **Interoperabilidad con Java**: Scala es fácil de adoptar ya que funciona en la plataforma Java estándar e interopera
  sin problemas con todas las bibliotecas de Java.

- **Combinación de Paradigmas**: Scala es una fusión de programación orientada a objetos y funcional en un lenguaje
  tipado estáticamente. Esta combinación permite expresar nuevos patrones de programación y abstracciones de
  componentes, resultando en un estilo de programación legible y conciso.

- **Mapas Asociativos**: Scala permite una notación de alto nivel para trabajar con mapas, pero a diferencia de otros
  lenguajes, los mapas en Scala son abstracciones de biblioteca que se pueden extender y adaptar según las necesidades.

- **Crecimiento de Nuevos Tipos**: Scala permite a los usuarios extender el lenguaje en las direcciones que necesiten,
  definiendo bibliotecas fáciles de usar que se sienten como soporte nativo del lenguaje. Un ejemplo es `BigInt`, que
  permite trabajar con enteros de tamaño arbitrario.

- **Crecimiento de Nuevas Estructuras de Control**: Scala permite agregar nuevas estructuras de control que pueden
  usarse tan convenientemente como las incorporadas. Un ejemplo es la API de Scala para programación concurrente basada
  en actores. Los actores son abstracciones de concurrencia que se comunican enviándose mensajes entre sí. Aunque
  parecen construcciones integradas en el lenguaje, en realidad son métodos definidos en la biblioteca de actores de
  Scala.

En resumen, Scala es un lenguaje que ofrece una gran flexibilidad y escalabilidad, permitiendo a los usuarios adaptar y
extender el lenguaje según sus necesidades, sin sentir que están trabajando fuera de las capacidades nativas del
lenguaje.

### Ejemplos prácticos que ilustran los puntos

discutidos:

1. **Interoperabilidad con Java**:
   Scala puede utilizar bibliotecas de Java sin problemas. Por ejemplo, si deseas utilizar la clase `ArrayList` de Java
   en Scala:

   ```scala
   import java.util.ArrayList

   val list = new ArrayList[String]()
   list.add("Hola")
   list.add("Mundo")
   println(list.get(0) + " " + list.get(1))
   ```

2. **Mapas Asociativos**:
   En Scala, puedes crear y manipular mapas con facilidad:

   ```scala
   var capitales = Map("US" -> "Washington", "Francia" -> "París")
   capitales += ("Japón" -> "Tokio")
   println(capitales("Francia"))
   ```

3. **Crecimiento de Nuevos Tipos**:
   Usando `BigInt` para cálculos con números grandes:

   ```scala
   def factorial(x: BigInt): BigInt = {
     if (x == 0) 1 else x * factorial(x - 1)
   }
   println(factorial(30))
   ```

4. **Actores para Programación Concurrente**:
   Aunque la programación basada en actores es un tema avanzado, aquí hay un ejemplo simplificado de cómo se vería un
   actor en Scala:

   ```scala
   import scala.actors.Actor
   import scala.actors.Actor._

   object SimpleActor extends Actor {
     def act() {
       loop {
         receive {
           case msg: String => println("Received: " + msg)
           case _ => println("Unknown message!")
         }
       }
     }
   }

   SimpleActor.start()
   SimpleActor ! "Hola"
   ```

   En este ejemplo, `SimpleActor` es un actor que recibe mensajes de tipo `String` y los imprime. El actor se inicia
   con `start()` y se le envía un mensaje con el operador `!`.

Estos ejemplos ilustran algunas de las características discutidas en el capítulo 1 de "Programming in Scala". Es
importante notar que Scala ha evolucionado con el tiempo, y algunas bibliotecas o características pueden haber cambiado
en versiones más recientes del lenguaje.
---
## Sección 1.2: "What makes Scala scalable?"*

- **Combinación de Paradigmas**: Una de las principales características que hace a Scala escalable es su combinación de
  programación orientada a objetos y programación funcional.

- **Scala es Orientado a Objetos**:
    - Scala sigue el principio de que todo es un objeto y toda operación es una llamada a un método. Por ejemplo, en la
      expresión `1 + 2`, el `+` es en realidad un método de la clase `Int`.
    - Scala permite componer objetos de maneras avanzadas, como con los "traits", que son similares a las interfaces en
      Java pero pueden tener implementaciones de métodos y campos.

- **Scala es Funcional**:
    - Las funciones son valores de primera clase en Scala, lo que significa que pueden ser pasadas como argumentos,
      retornadas como resultados o almacenadas en variables.
    - La programación funcional se centra en mapear valores de entrada a valores de salida en lugar de cambiar datos en
      el lugar. Esto lleva a estructuras de datos inmutables, que son esenciales en programación funcional. Por ejemplo,
      las cadenas en Java y Scala son inmutables.
    - Los métodos en programación funcional no deben tener efectos secundarios y deben ser referencialmente
      transparentes. Es decir, para cualquier entrada dada, la llamada al método podría ser reemplazada por su resultado
      sin afectar la semántica del programa.

En resumen, Scala es escalable debido a su capacidad para fusionar de manera efectiva la programación orientada a
objetos y la programación funcional en un diseño de lenguaje uniforme. Esta combinación permite a los desarrolladores
aprovechar lo mejor de ambos paradigmas, lo que resulta en código más modular, reutilizable y fácil de mantener.

### Ejemplos prácticos basados en la sección 1.2 para ilustrar los conceptos
discutidos:

1. **Scala es Orientado a Objetos**:

   a. **Todo es un objeto y toda operación es una llamada a un método**:

   ```scala
   val result = 1.+(2)
   println(result)  // Esto imprimirá 3
   ```

   b. **Traits**:

   ```scala
   trait Saludador {
     def saludo: String
     def saludar(): Unit = {
       println(saludo)
     }
   }

   class Persona(nombre: String) extends Saludador {
     override def saludo: String = s"Hola, soy $nombre"
   }

   val persona = new Persona("Juan")
   persona.saludar()  // Esto imprimirá "Hola, soy Juan"
   ```

2. **Scala es Funcional**:

   a. **Funciones como valores de primera clase**:

   ```scala
   def aplicarFuncion(f: Int => String, valor: Int): String = f(valor)

   val funcion = (x: Int) => s"El doble de $x es ${x * 2}"
   println(aplicarFuncion(funcion, 5))  // Esto imprimirá "El doble de 5 es 10"
   ```

   b. **Estructuras de datos inmutables**:

   ```scala
   val lista1 = List(1, 2, 3)
   val lista2 = lista1 :+ 4  // Crea una nueva lista, lista1 sigue siendo [1, 2, 3]

   println(lista1)  // [1, 2, 3]
   println(lista2)  // [1, 2, 3, 4]
   ```

   c. **Métodos referencialmente transparentes**:

   ```scala
   def sumar(a: Int, b: Int): Int = a + b

   // La función sumar siempre devolverá el mismo resultado para los mismos argumentos, sin efectos secundarios.
   println(sumar(3, 4))  // 7
   ```
---


## 1.3 ¿Por qué Scala?

**Scala es compatible**:
- Scala está diseñado para interoperar sin problemas con Java.
- Los programas de Scala se compilan a bytecode de JVM y su rendimiento suele ser comparable al de Java.
- Puedes llamar a métodos de Java, acceder a campos de Java, heredar de clases de Java e implementar interfaces de Java desde Scala.
- Scala reutiliza muchos tipos de Java, pero también "los mejora" para hacerlos más agradables. Por ejemplo, las cadenas de Scala tienen métodos como `toInt` que no existen en Java, pero se logran mediante conversiones implícitas.

**Scala es conciso**:
- Los programas de Scala suelen ser más cortos que sus equivalentes en Java.
- Scala elimina mucho del código repetitivo (boilerplate) que se encuentra en Java.
- La inferencia de tipos en Scala reduce la necesidad de especificar tipos explícitamente.
- Las bibliotecas de Scala permiten escribir código más compacto y expresivo.

**Scala es de alto nivel**:
- Scala permite abstracciones de alto nivel que simplifican el código.
- Por ejemplo, en lugar de usar un bucle para verificar si una cadena tiene un carácter en mayúsculas (como en Java), en Scala puedes escribir `name.exists(_.isUpperCase)`.
- Las abstracciones de control en Scala, como los literales de función, son livianas y se utilizan con frecuencia.

**Scala está tipificado estáticamente**:
- Aunque Scala tiene un sistema de tipos estáticos avanzado, no es verboso gracias a la inferencia de tipos.
- Los tipos estáticos ofrecen varias ventajas:
    - **Propiedades verificables**: Garantizan que ciertos errores no ocurrirán en tiempo de ejecución.
    - **Refactorizaciones seguras**: Cambiar el código es más seguro porque los errores de tipo se detectarán en tiempo de compilación.
    - **Documentación**: Los tipos sirven como documentación que siempre está actualizada y es verificada por el compilador.

---

**1.4 Raíces de Scala**

- **Influencias de otros lenguajes**: Scala ha sido influenciado por muchos lenguajes de programación y conceptos en la investigación de lenguajes de programación.

- **Sintaxis**: A nivel superficial, Scala adopta gran parte de la sintaxis de Java y C#, que a su vez tomaron sus convenciones sintácticas de C y C++. Además, Scala adopta otros elementos de Java, como sus tipos básicos, sus bibliotecas de clases y su modelo de ejecución.

- **Modelo de objeto**: El modelo de objeto uniforme de Scala fue pionero en Smalltalk y luego adoptado por Ruby.

- **Nidificación universal**: La idea de que casi todos los constructos en Scala pueden anidarse dentro de cualquier otro constructo también está presente en lenguajes como Algol, Simula, Beta y gbeta.

- **Programación funcional**: Su enfoque de programación funcional es similar al de la familia de lenguajes ML, que incluye SML, OCaml y F#.

- **Parámetros implícitos**: Fueron motivados por las clases de tipo de Haskell.

- **Concurrencia basada en actores**: Fue inspirada en gran medida por Erlang.

- **Historia de lenguajes extensibles**: Scala no es el primer lenguaje en enfatizar la escalabilidad y extensibilidad. Iswim y Smalltalk, por ejemplo, permitieron la creación de lenguajes de dominio específico internos.

- **Integración de funcional y OOP**: Aunque Scala integra la programación funcional y orientada a objetos, no es el primero en hacerlo. Otros lenguajes que han integrado elementos de programación funcional en OOP incluyen Ruby, Smalltalk y Python.

- **Innovaciones de Scala**: Scala también ha aportado algunas innovaciones al campo de los lenguajes de programación, como sus tipos abstractos, sus rasgos y sus extractores.

---

Espero que este resumen te ofrezca una visión clara de las raíces e influencias detrás del diseño de Scala.