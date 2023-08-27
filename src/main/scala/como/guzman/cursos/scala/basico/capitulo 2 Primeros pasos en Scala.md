## Capítulo 2: Primeros Pasos en Scala

Este capítulo introduce los conceptos básicos de Scala a través de ejemplos prácticos y ejercicios interactivos.

1. **Uso del intérprete de Scala**:
    - Se introduce el intérprete interactivo de Scala, que permite escribir y evaluar expresiones de Scala en tiempo
      real.
    - Se muestra cómo ingresar expresiones y cómo el intérprete devuelve resultados con un formato específico,
      como `res0: Int = 3`.

2. **Definición de variables**:
    - Scala tiene dos tipos de variables: `val` (inmutable) y `var` (mutable).
    - Se muestra cómo definir variables y cómo la inferencia de tipos en Scala puede determinar automáticamente el tipo
      de una variable basándose en su valor inicial.

3. **Definición de funciones**:
    - Se introduce la sintaxis para definir funciones en Scala, destacando que las funciones son ciudadanos de primera
      clase en el lenguaje.
    - Se muestra cómo definir funciones con y sin especificación explícita de tipo.

4. **Escribir scripts en Scala**:
    - Se introduce la idea de escribir scripts de Scala, que son secuencias de declaraciones en un archivo que se
      ejecutan secuencialmente.
    - Se muestra cómo acceder a los argumentos de la línea de comandos en un script.

5. **Uso de bucles y condicionales**:
    - Se introduce el bucle `while` y la estructura condicional `if` en Scala, mostrando cómo se utilizan en un estilo
      imperativo.

6. **Iterar con "foreach" y "for"**:
    - Se introduce la programación funcional en Scala, mostrando cómo usar `foreach` y las expresiones `for` para iterar
      sobre colecciones.
    - Se destaca la diferencia entre el estilo funcional y el estilo imperativo y se alienta al lector a familiarizarse
      con el enfoque funcional.

---

## 2.1 Paso 1: Aprender a usar el intérprete de Scala**

- **Intérprete de Scala**: La forma más sencilla de comenzar con Scala es utilizando el intérprete de Scala, una "
  consola" interactiva para escribir expresiones y programas en Scala. Al escribir una expresión en el intérprete, este
  evalúa la expresión y muestra el resultado.

- **Uso del intérprete**: Al escribir `scala` en la línea de comandos, se inicia el intérprete. Por ejemplo, al escribir
  una expresión como `1 + 2`, el intérprete muestra `res0: Int = 3`, donde:
    - `res0` es un nombre generado automáticamente para referirse al valor computado.
    - `Int` es el tipo de la expresión, que corresponde a la clase `Int` en el paquete `scala`.
    - `3` es el valor resultante de la evaluación.

- **Paquetes en Scala**: Son similares a los paquetes en Java. Ayudan a particionar el espacio de nombres global y
  proporcionan un mecanismo para ocultar información. Todos los tipos primitivos de Java tienen clases correspondientes
  en el paquete `scala`.

- **Uso de identificadores resX**: Los identificadores generados automáticamente, como `res0`, pueden ser utilizados en
  líneas posteriores. Por ejemplo, si `res0` fue previamente establecido a 3, `res0 * 3` resultará en 9.

- **Impresión en consola**: La función `println` se utiliza para imprimir cadenas en la salida estándar, similar
  a `System.out.println` en Java.

---
¡Por supuesto! Aquí tienes un resumen del capítulo 2.2 con ejemplos prácticos:

---

## 2.2 Paso 2: Definir algunas variables

- **Tipos de variables en Scala**: Scala tiene dos tipos de variables: `val` y `var`.
    - **val**: Es similar a una variable `final` en Java. Una vez inicializada, no puede ser reasignada.
      Ejemplo:
      ```scala
      scala> val msg = "Hello, world!"
      msg: java.lang.String = Hello, world!
      ```

    - **var**: Es similar a una variable no final en Java. Puede ser reasignada durante su vida útil.
      Ejemplo:
      ```scala
      scala> var greeting = "Hello, world!"
      greeting: java.lang.String = Hello, world!
      ```

- **Inferencia de tipo**: Scala puede inferir tipos automáticamente. Por ejemplo, al inicializar `msg` con una cadena
  literal, Scala infiere que el tipo de `msg` es `String`. Sin embargo, si se desea, se puede especificar el tipo
  explícitamente.
  Ejemplo:
  ```scala
  scala> val msg2: java.lang.String = "Hello again, world!"
  msg2: java.lang.String = Hello again, world!
  ```

- **Uso de variables**: Una vez definida una variable, se puede usar normalmente. Pero si es un `val`, no se puede
  reasignar.
  Ejemplo de reasignación fallida:
  ```scala
  scala> msg = "Goodbye cruel world!"
  <console>:5: error: reassignment to val
  ```

  Ejemplo de reasignación exitosa con `var`:
  ```scala
  scala> greeting = "Leave me alone, world!"
  greeting: java.lang.String = Leave me alone, world!
  ```

- **Entrada de múltiples líneas**: Si se desea ingresar una expresión que abarque varias líneas en el intérprete,
  simplemente se sigue escribiendo después de la primera línea. Si lo que se ha escrito no está completo, el intérprete
  mostrará una barra vertical en la siguiente línea.

---

## 2.3 Paso 3: Definir algunas funciones

- **Definición de funciones**: Las funciones en Scala comienzan con `def`, seguido del nombre de la función, una lista
  de parámetros y el tipo de resultado.
  Ejemplo:
  ```scala
  scala> def max(x: Int, y: Int): Int = {
      if (x > y) x
      else y
  }
  max: (Int,Int)Int
  ```

- **Inferencia de tipo en funciones**: Aunque es necesario especificar el tipo de los parámetros de la función, Scala
  puede inferir el tipo de resultado de la función en muchos casos. Sin embargo, para funciones recursivas, es necesario
  especificar el tipo de resultado.
  Ejemplo simplificado sin llaves:
  ```scala
  scala> def max2(x: Int, y: Int) = if (x > y) x else y
  max2: (Int,Int)Int
  ```

- **Llamada a funciones**: Una vez definida, puedes llamar a una función por su nombre.
  Ejemplo:
  ```scala
  scala> max(3, 5)
  res6: Int = 5
  ```

- **Funciones sin parámetros y sin retorno**: Scala tiene un tipo especial llamado `Unit` que es similar al `void` de
  Java. Las funciones que retornan `Unit` generalmente se ejecutan solo por sus efectos secundarios.
  Ejemplo:
  ```scala
  scala> def greet() = println("Hello, world!")
  greet: ()Unit
  ```

- **Salir del intérprete**: Puedes salir del intérprete de Scala usando `:quit` o `:q`.

---

## 2.4 Paso 4: Escribe algunos scripts en Scala

- **Ejecución de scripts**: Scala no solo es adecuado para grandes sistemas, sino que también es ideal para scripting.
  Un script de Scala es simplemente una secuencia de declaraciones en un archivo que se ejecutarán secuencialmente.

  Ejemplo:
    1. Crea un archivo llamado `hello.scala` con el siguiente contenido:
       ```scala
       println("Hello, world, from a script!")
       ```
    2. Ejecuta el script con:
       ```
       $ scala hello.scala
       ```
    3. Verás la salida:
       ```
       Hello, world, from a script!
       ```

- **Argumentos de línea de comando**: Los argumentos pasados a un script de Scala están disponibles a través de un array
  llamado `args`. En Scala, los arrays comienzan desde el índice 0, y se accede a un elemento usando paréntesis.

  Ejemplo:
    1. Crea un archivo llamado `helloarg.scala` con el siguiente contenido:
       ```scala
       // Say hello to the first argument
       println("Hello, " + args(0) + "!")
       ```
    2. Ejecuta el script con:
       ```
       $ scala helloarg.scala planet
       ```
    3. Verás la salida:
       ```
       Hello, planet!
       ```

- **Comentarios en Scala**: Puedes agregar comentarios a tus scripts de Scala usando `//` para comentarios de una sola
  línea y `/* */` para comentarios de varias líneas.

- **Concatenación de cadenas**: En Scala, puedes concatenar cadenas usando el operador `+`, similar a otros lenguajes
  como Java.

---

## 2.5 Paso 5: Bucle con "while"; decide con "if"

- **Bucle "while"**: Scala tiene un bucle `while` que funciona de manera similar a otros lenguajes de programación. Se
  ejecuta mientras la condición proporcionada sea verdadera.

  Ejemplo:
  ```scala
  var i = 0
  while (i < args.length) {
      println(args(i))
      i += 1
  }
  ```
  Si ejecutas este script con `$ scala printargs.scala Scala is fun`, verás:
  ```
  Scala
  is
  fun
  ```

- **Uso de "if"**: En Scala, puedes usar la declaración `if` para tomar decisiones basadas en condiciones.

  Ejemplo:
  ```scala
  var i = 0
  while (i < args.length) {
      if (i != 0)
          print(" ")
      print(args(i))
      i += 1
  }
  println()
  ```
  Si ejecutas este script con `$ scala echoargs.scala Scala is even more fun`, obtendrás:
  ```
  Scala is even more fun
  ```

- **Notas adicionales**:
    - En Scala, las expresiones booleanas para `while` o `if` deben estar entre paréntesis.
    - Si un bloque tiene solo una declaración, puedes omitir las llaves.
    - Aunque no se mostró en los ejemplos, Scala utiliza punto y coma (`;`) para separar las declaraciones, pero a
      menudo son opcionales.

## 2.6 Paso 6: Iterar con "foreach" y "for"

En este capítulo, se introduce la programación funcional en Scala, que es una alternativa al estilo imperativo
comúnmente utilizado en lenguajes como Java o C++.

1. **Uso de "foreach" con función literal**:
   En Scala, puedes usar el método `foreach` para iterar sobre cada elemento de una colección y aplicar una función a
   cada elemento.

   Ejemplo:
   ```scala
   args.foreach(arg => println(arg))
   ```

   Si ejecutas este script con `$ scala pa.scala Concise is nice`, verás:
   ```
   Concise
   is
   nice
   ```

   También puedes ser más explícito sobre el tipo del argumento o usar una forma más concisa:
   ```scala
   args.foreach((arg: String) => println(arg))
   args.foreach(println)
   ```

2. **Expresiones "for"**:
   Scala ofrece una versión funcional del bucle `for` tradicional llamada "expresión for".

   Ejemplo:
   ```scala
   for (arg <- args)
       println(arg)
   ```

   Aquí, `arg` es un `val` (una constante) que toma el valor de cada elemento en `args` en cada iteración. Aunque puede
   parecer que `arg` se reasigna en cada iteración, en realidad se crea un nuevo `val` para cada elemento.

   Si ejecutas este script con `$ scala forargs.scala for arg in args`, verás:
   ```
   for
   arg
   in
   args
   ```

   Las expresiones `for` en Scala son muy poderosas y versátiles, y verás más sobre ellas en secciones posteriores del
   libro.


