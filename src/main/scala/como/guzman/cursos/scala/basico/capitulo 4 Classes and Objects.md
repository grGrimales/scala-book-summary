# Capítulo 4.1: Clases, Campos y Métodos en Scala

#### Conceptos Clave:

- Una clase en Scala sirve como un plano para crear objetos.
- Los campos (variables) y métodos (funciones) dentro de una clase se llaman miembros.
- Los campos pueden ser `val` (inmutables) o `var` (mutables).
- Los métodos se definen usando la palabra clave `def`.

#### Ejemplo Práctico:

Supongamos que queremos crear una clase para calcular el acumulador de suma de verificación (checksum). Podemos definir
una clase `ChecksumAccumulator` con un campo `sum` y dos métodos `add` y `checksum`.

```scala
class ChecksumAccumulator {
  private var sum = 0 // Campo privado

  def add(b: Byte): Unit = { // Método para agregar un byte al acumulador
    sum += b
  }

  def checksum(): Int = { // Método para calcular el checksum
    return ~(sum & 0xFF) + 1
  }
}
```

Para crear una instancia de esta clase:

```scala
val acc = new ChecksumAccumulator()
```

Podemos usar los métodos `add` y `checksum` para modificar y obtener el estado del objeto.

```scala
acc.add(5)
println(acc.checksum()) // Imprimirá el checksum calculado
```

#### Notas Importantes:

1. Los campos privados (`private var sum`) no pueden ser accedidos directamente desde fuera de la clase.
2. Los parámetros de los métodos son `val` por defecto, lo que significa que no pueden ser reasignados dentro del
   método.
3. Es posible omitir las llaves `{}` y la palabra `return` si el método consta de una única expresión.
4. Si se omite el signo `=` en la definición del método, el tipo de retorno será `Unit`, independientemente del
   contenido del método.

Este capítulo ofrece una introducción sólida a cómo se definen y se utilizan clases en Scala, proporcionando las bases
para la programación orientada a objetos en este lenguaje.

---

# Capítulo 4.2: Inferencia de punto y coma en Scala

#### Conceptos clave:

1. **Opcionalidad del punto y coma**: En Scala, el punto y coma (`;`) al final de una declaración es generalmente
   opcional si la declaración aparece sola en una línea.

2. **Declaraciones múltiples en una línea**: Si tienes más de una declaración en una sola línea, entonces el punto y
   coma es obligatorio.
    ```scala
    val s = "hello"; println(s)
    ```

3. **Declaraciones en múltiples líneas**: Si una declaración se extiende por varias líneas, Scala generalmente la
   tratará como una sola declaración.
    ```scala
    if (x < 2)
      println("too small")
    else
      println("ok")
    ```

4. **Excepciones en la inferencia**: A veces, Scala puede dividir una declaración en dos partes, especialmente cuando se
   usan operadores infijos. Para evitar esto, puedes usar paréntesis o colocar el operador al final de la línea.
    ```scala
    // Usando paréntesis
    (x
    + y)
    
    // Colocando el operador al final de la línea
    x +
    y +
    z
    ```

#### Reglas para la inferencia de punto y coma:

1. La línea termina en una palabra que no sería legal al final de una declaración, como un punto o un operador infijo.
2. La siguiente línea comienza con una palabra que no puede iniciar una declaración.
3. La línea termina dentro de paréntesis `(...)` o corchetes `[...]`, ya que estos no pueden contener múltiples
   declaraciones.

#### Ejemplos prácticos:

1. **Declaración simple sin punto y coma**
    ```scala
    val x = 10
    ```

2. **Múltiples declaraciones en una línea con punto y coma**
    ```scala
    val x = 10; val y = 20
    ```

3. **Declaración en múltiples líneas sin punto y coma**
    ```scala
    if (x < 2)
      println("too small")
    else
      println("ok")
    ```

4. **Uso de paréntesis para evitar la división de declaraciones**
    ```scala
    val result = (x
    + y)
    ```

5. **Colocar operadores al final para evitar la división de declaraciones**
    ```scala
    val result = x +
                y +
                z
    ```

Espero que este resumen te sea útil para entender mejor la inferencia de punto y coma en Scala.