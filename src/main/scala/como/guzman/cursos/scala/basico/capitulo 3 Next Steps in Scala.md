# Capítulo 3 Siguientes pasos en Scala

## Capítulo 3.1: Parámetro de arrays con tipos**

En Scala, puedes instanciar objetos usando `new`. Al instanciar un objeto, puedes parametrizarlo con valores y tipos.
Parametrizar significa "configurar" una instancia cuando la creas.

**Ejemplo 1: Parametrización con valores**

```scala
val big = new java.math.BigInteger("12345")
```

Aquí, estás parametrizando el objeto `BigInteger` con el valor "12345".

**Ejemplo 2: Parametrización con tipos**

```scala
val greetStrings = new Array[String](3)
```

En este caso, `greetStrings` es un array de tipo `String` que tiene una longitud de 3. La parametrización con tipos se
realiza con corchetes, mientras que la parametrización con valores se realiza con paréntesis.

**Acceso y modificación de arrays**
En Scala, los arrays se acceden y modifican usando paréntesis:

```scala
greetStrings(0) = "Hello"
greetStrings(1) = ", "
greetStrings(2) = "world!\n"
```

Esto es diferente de otros lenguajes como Java, donde se usan corchetes.

**Iteración sobre arrays**
Puedes iterar sobre un array usando un bucle `for`:

```scala
for (i <- 0 to 2)
  print(greetStrings(i))
```

**Conceptos clave:**

- En Scala, cuando defines una variable con `val`, la variable no puede ser reasignada, pero el objeto al que se refiere
  puede ser modificado.
- En Scala, todas las operaciones son llamadas a métodos. Por ejemplo, `1 + 2` es en realidad una llamada al método `+`
  en el objeto `Int` 1, pasando 2 como parámetro.
- Scala proporciona una forma más concisa de crear e inicializar arrays:

```scala
val numNames = Array("zero", "one", "two")
```

Este código crea un nuevo array de longitud tres, inicializado con las cadenas "zero", "one" y "two".

En resumen, Scala ofrece una forma uniforme y orientada a objetos de trabajar con arrays y otros tipos, eliminando la
necesidad de recordar casos especiales y proporcionando una sintaxis más concisa y expresiva.

---

## Capítulo 3.2: Uso de listas

En el estilo funcional de programación, se prefiere que los métodos no tengan efectos secundarios. En lugar de cambiar
objetos existentes, se crean nuevos objetos con los valores deseados. En este contexto, Scala ofrece listas inmutables,
que son secuencias de objetos que comparten el mismo tipo.

**Ejemplo 1: Creación de una lista**

```scala
val oneTwoThree = List(1, 2, 3)
```

Este código crea una lista inmutable con tres enteros.

**Ejemplo 2: Concatenación de listas**

```scala
val oneTwo = List(1, 2)
val threeFour = List(3, 4)
val oneTwoThreeFour = oneTwo ::: threeFour
```

Aunque las listas `oneTwo` y `threeFour` permanecen inmutables, puedes concatenarlas para crear una nueva
lista, `oneTwoThreeFour`.

**Ejemplo 3: Prependiendo elementos a una lista**

```scala
val twoThree = List(2, 3)
val oneTwoThree = 1 :: twoThree
```

El operador `::` (cons) agrega un nuevo elemento al principio de una lista existente.

**Ejemplo 4: Creación de listas con Nil**

```scala
val oneTwoThree = 1 :: 2 :: 3 :: Nil
```

`Nil` es una forma de representar una lista vacía en Scala. Puedes usar `::` para construir una lista, terminando
con `Nil`.

**Métodos útiles de la lista:**
Las listas en Scala vienen con una variedad de métodos útiles. Algunos de ellos incluyen:

- `:::`: Concatena dos listas.
- `head`: Devuelve el primer elemento de la lista.
- `tail`: Devuelve todos los elementos de la lista excepto el primero.
- `isEmpty`: Verifica si la lista está vacía.
- `reverse`: Devuelve una lista con el orden de los elementos invertido.
- `map`: Aplica una función a todos los elementos de la lista.
- `filter`: Devuelve una lista con elementos que cumplen una condición específica.
- `mkString`: Convierte la lista en una cadena, utilizando un separador específico.
- `length`: Devuelve el número de elementos en la lista.

**Nota importante:** Las listas en Scala son inmutables. Esto significa que, en lugar de modificar una lista existente,
las operaciones en listas crean nuevas listas. Por ejemplo, al concatenar dos listas, se crea una nueva lista sin
modificar las listas originales.

En resumen, las listas en Scala son secuencias inmutables que ofrecen una amplia variedad de métodos útiles. Están
diseñadas para facilitar un estilo de programación funcional, donde los métodos no tienen efectos secundarios y se crean
nuevos objetos en lugar de modificar los existentes.

---

## Capítulo 3.3: Uso de tuplas

Las tuplas son contenedores inmutables que pueden contener elementos de diferentes tipos. A diferencia de las listas,
que tienen elementos del mismo tipo, las tuplas permiten combinar múltiples tipos en una sola estructura.

**Ejemplo 1: Creación y uso de una tupla**

```scala
val pair = (99, "Luftballons")
println(pair._1)
println(pair._2)
```

En este ejemplo, se crea una tupla que contiene un entero y una cadena de texto. Luego, se accede a sus elementos
utilizando `._1` y `._2`. La salida de este código será:

```
99
Luftballons
```

**Características clave de las tuplas:**

1. **Diferentes tipos de elementos:** A diferencia de las listas, las tuplas pueden contener elementos de diferentes
   tipos. Por ejemplo, `(99, "Luftballons")` es una tupla que contiene un `Int` y un `String`.

2. **Acceso a elementos:** Los elementos de una tupla se acceden utilizando `._N`, donde N es el índice del elemento
   basado en 1. Es decir, `._1` accede al primer elemento, `._2` al segundo, y así sucesivamente.

3. **Tipos de tuplas:** El tipo de una tupla depende del número y tipo de sus elementos. Por ejemplo, el tipo
   de `(99, "Luftballons")` es `Tuple2[Int, String]`, mientras que el tipo de `('u', 'r', "the", 1, 4, "me")`
   es `Tuple6[Char, Char, String, Int, Int, String]`.

4. **Inmutabilidad:** Al igual que las listas en Scala, las tuplas son inmutables. Una vez que se crea una tupla, no se
   puede modificar.

5. **Uso común:** Las tuplas son especialmente útiles cuando se necesita devolver múltiples valores desde un método sin
   crear una clase específica para ello.

**Nota:** Las tuplas en Scala están definidas hasta `Tuple22`, lo que significa que puedes tener tuplas con hasta 22
elementos. La razón por la que las tuplas no permiten el acceso basado en índice como las listas (por
ejemplo, `pair(0)`) es porque cada elemento de una tupla puede tener un tipo diferente, y el método `apply` de una lista
siempre devuelve el mismo tipo.

---

## Capítulo 3.4: Uso de conjuntos (sets) y mapas (maps)

Scala ofrece tanto colecciones mutables como inmutables. Las colecciones mutables permiten cambios después de su
creación, mientras que las inmutables no.

**1. Conjuntos (Sets):**

- **Conjuntos Inmutables:** Por defecto, cuando creas un conjunto en Scala, es inmutable.
   ```scala
   var jetSet = Set("Boeing", "Airbus")
   jetSet += "Lear"
   println(jetSet.contains("Cessna"))  // Imprime: false
   ```
  Aquí, `jetSet` es un conjunto inmutable. Al usar `+=`, en realidad estás creando un nuevo conjunto con el elemento
  añadido y reasignando `jetSet` a este nuevo conjunto.

- **Conjuntos Mutables:** Si necesitas un conjunto que pueda cambiar, Scala ofrece conjuntos mutables.
   ```scala
   import scala.collection.mutable.Set
   val movieSet = Set("Hitch", "Poltergeist")
   movieSet += "Shrek"
   println(movieSet)  // Imprime: Set(Hitch, Poltergeist, Shrek)
   ```
  Aquí, `movieSet` es un conjunto mutable. Al usar `+=`, estás añadiendo "Shrek" directamente al conjunto existente.

**2. Mapas (Maps):**

- **Mapas Inmutables:** Por defecto, cuando creas un mapa en Scala, es inmutable.
   ```scala
   val romanNumeral = Map(
     1 -> "I", 2 -> "II", 3 -> "III", 4 -> "IV", 5 -> "V"
   )
   println(romanNumeral(4))  // Imprime: IV
   ```
  Aquí, `romanNumeral` es un mapa inmutable que mapea números a sus representaciones romanas.

- **Mapas Mutables:** Si necesitas un mapa que pueda cambiar, Scala ofrece mapas mutables.
   ```scala
   import scala.collection.mutable.Map
   val treasureMap = Map[Int, String]()
   treasureMap += (1 -> "Go to island.")
   treasureMap += (2 -> "Find big X on ground.")
   treasureMap += (3 -> "Dig.")
   println(treasureMap(2))  // Imprime: Find big X on ground.
   ```
  Aquí, `treasureMap` es un mapa mutable. Estás añadiendo pares clave-valor directamente al mapa existente.

**Puntos clave:**

- Las colecciones mutables e inmutables tienen sus propios usos y ventajas. Las colecciones inmutables son seguras para
  el acceso concurrente, mientras que las mutables son útiles cuando necesitas cambiar el contenido después de la
  creación.
- Los conjuntos y mapas en Scala son muy versátiles y ofrecen una amplia gama de operaciones para manipular y consultar
  datos.
- Para usar conjuntos y mapas mutables, es necesario importar `scala.collection.mutable.Set`
  o `scala.collection.mutable.Map` respectivamente.

---

## Capítulo 3.5: Aprende a reconocer el estilo funcional**

Scala permite programar en un estilo imperativo, pero te anima a adoptar un estilo más funcional. La diferencia entre
ambos estilos puede ser evidente en el código. Si el código contiene `vars`, probablemente esté en un estilo imperativo.
Si solo contiene `vals`, probablemente esté en un estilo funcional. Una forma de moverse hacia un estilo funcional es
intentar programar sin `vars`.

**Diferencia entre `val` y `var`:**

- Si vienes de un fondo imperativo (como Java o C++), puedes pensar en `var` como una variable regular y `val` como una
  variable especial.
- Si vienes de un fondo funcional (como Haskell o Erlang), podrías pensar en `val` como una variable regular y `var`
  como algo no deseado.

**Ejemplo de transformación de estilo imperativo a funcional:**

1. Estilo Imperativo:
   ```scala
   def printArgs(args: Array[String]): Unit = {
       var i = 0
       while (i < args.length) {
           println(args(i))
           i += 1
       }
   }
   ```
2. Estilo Funcional:
   ```scala
   def printArgs(args: Array[String]): Unit = {
       for (arg <- args)
           println(arg)
   }
   ```
   o
   ```scala
   def printArgs(args: Array[String]): Unit = {
       args.foreach(println)
   }
   ```

El estilo funcional es más claro, conciso y menos propenso a errores que el estilo imperativo.

**Funciones sin efectos secundarios:**

Una función sin efectos secundarios simplemente devuelve un valor sin cambiar nada en el mundo exterior. Un signo
revelador de una función con efectos secundarios es que su tipo de resultado es `Unit`.

Ejemplo:

```scala
def formatArgs(args: Array[String]) = args.mkString("\n")
```

Esta función simplemente formatea los argumentos para imprimir, pero no imprime nada. Puedes probar
fácilmente `formatArgs` simplemente comprobando su resultado.

**Consejo para programadores de Scala:**
Prefiere `vals`, objetos inmutables y métodos sin efectos secundarios. Úsalos primero. Utiliza `vars`, objetos mutables
y métodos con efectos secundarios solo cuando tengas una necesidad específica y justificación para ellos.

---

## Capítulo 3.6: Leer líneas de un archivo

Este capítulo te muestra cómo leer líneas de un archivo y procesarlas. El objetivo es leer un archivo, y para cada línea, imprimir el número de caracteres en esa línea seguido de la línea misma.

**Ejemplo inicial:**
```scala
import scala.io.Source
if (args.length > 0) {
    for (line <- Source.fromFile(args(0)).getLines)
        print(line.length +" "+ line)
}
else
    Console.err.println("Please enter filename")
```
Este script importa la clase `Source` de `scala.io` y verifica si se proporcionó un argumento (nombre del archivo). Luego, lee cada línea del archivo y la imprime junto con su longitud.

**Mejorando la presentación:**
Para mejorar la presentación, se puede alinear los números a la derecha y agregar un carácter de tubería (`|`). Para lograr esto, se necesita calcular el ancho máximo requerido por el recuento de caracteres de cualquier línea.

**Ejemplo mejorado:**
```scala
import scala.io.Source

def widthOfLength(s: String) = s.length.toString.length

if (args.length > 0) {
    val lines = Source.fromFile(args(0)).getLines.toList
    val longestLine = lines.reduceLeft(
        (a, b) => if (a.length > b.length) a else b
    )
    val maxWidth = widthOfLength(longestLine)
    for (line <- lines) {
        val numSpaces = maxWidth - widthOfLength(line)
        val padding = " " * numSpaces
        print(padding + line.length +" | "+ line)
    }
}
else
    Console.err.println("Please enter filename")
```
En este script:
- Se define una función `widthOfLength` que devuelve la longitud de una cadena.
- Se lee el archivo y se almacena en una lista llamada `lines`.
- Se encuentra la línea más larga usando `reduceLeft`.
- Se calcula el ancho máximo necesario para alinear los números.
- Finalmente, se itera sobre cada línea, se calcula el espacio necesario para alinear los números y se imprime la línea con el formato deseado.

Este enfoque te permite leer y procesar archivos de manera efectiva y presentar la información de manera ordenada y legible.

---