# Conversiones de Tipos

La mayoría de las veces, los operadores y las funciones automáticamente convierten un valor al tipo deseado. Esto se llama "conversión de tipo".

Por ejemplo, `alert` convierte automáticamente cualquier valor a un string para asi mostrarlo. Las operaciones matemáticas convierten los valores a números.

También hay casos en los que necesitamos convertir un valor explícitamente para realizar las cosas correctamente.

```smart header="Aún no hablaremos de los objetos"
En este capítulo todavía no cubriremos a los objetos. Aquí primero estudiaremos a los primitivos. Más adelante, después de que aprendamos mas de los objetos, veremos cómo funciona la conversión de objetos en el capítulo <info:objeto-a-primitivo>.
```

## A String

La conversión a string ocurre cuando necesitamos la forma en string de un valor.

Por ejemplo, `alert(valor)` lo hace para mostrar el valor.

También podemos usar una llamada a la función `String(valor)` para eso:

```js run
let valor = true;
alert(typeof valor); // boolean

*!*
valor = String(valor); // ahora valor es el string "true"
alert(typeof valor); // string
*/!*
```

Las conversiones a strings son mayormente obvias. Un `false` se convierte en `"false"`, `null` se convierte en `"null"`, etc.

## A Número

La conversión numérica ocurre en expresiones y funciones matemáticas de manera automática.

Por ejemplo, cuando la división `/` es aplicada a no-números:

```js run
alert( "6" / "2" ); // 3, los strings son convertidos en números
```

Podemos usar la función `Number(valor)` para explícitamente convertir un `valor`:

```js run
let str = "123";
alert(typeof str); // string

let num = Number(str); // se convierte en el número 123

alert(typeof num); // number
```

La conversión explícita generalmente es requerida cuando leemos un valor de una fuente basada en strings como un formulario de texto, en la que esperamos que se ingrese un número.

Si el string no es un número válido, el resultado de dicha conversión es `NaN`, por ejemplo:

```js run
let edad = Number("Un string arbitrario en lugar de un número");

alert(edad); // NaN, la conversión fallo
```

Reglas de la conversión numérica:

| Valor |  Se convierte en... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;y&nbsp;false</code> | `1` y `0` |
| `string` | Los espacios en blanco del principio y el final son eliminados. Luego, si el string restante está vacío, el resultado es `0`. De lo contrario, el número se "lee" del string. Un error da `NaN`. |

Ejemplos:

```js run
alert( Number("   123   ") ); // 123
alert( Number("123z") );      // NaN (error leyendo un número en la "z")
alert( Number(true) );        // 1
alert( Number(false) );       // 0
```

Por favor ten en cuenta que `null` y `undefined` se comportan de manera diferente aquí: `null` se convierte en cero, mientras que `undefined` se convierte en `NaN`.

````smart header="La adición '+' concatena cadenas"
Casi todas las operaciones matemáticas convierten valores a números. Con la notable excepción de la adición `+`. Si uno de los valores agregados es un string, entonces el otro tambien es convertido a string.

Luego los concatena (une):

```js run
alert( 1 + '2' ); // '12' (string a la derecha)
alert( '1' + 2 ); // '12' (string a la izquierda)
```

Eso solo sucede cuando uno de los argumentos es un string. De lo contrario, los valores son convertidos en números.
````

## A Booleano

La conversión booleana es la más sencilla.

Esta ocurre en operaciones lógicas (más adelante aprenderemos de las pruebas de condición y otros tipos de ellas), pero también se puede realizar manualmente con la llamada a `Boolean(valor)`.

La regla de conversión:

- Los valores que están intuitivamente "vacíos", como `0`, un string vacío, `null`, `undefined` y `NaN` se convierten en `false`.
- Todos los otros valores se convierten en `true`.

Por ejemplo:

```js run
alert( Boolean(1) ); // true
alert( Boolean(0) ); // false

alert( Boolean("hola") ); // true
alert( Boolean("") ); // false
```

````warn header="Ten en cuenta: el string con cero `\"0\"` es `true`"
Algunos lenguajes (a saber, PHP) tratan `"0"` como `false`. Pero en JavaScript, un string no-vacío siempre es `true`.

```js run
alert( Boolean("0") ); // true
alert( Boolean(" ") ); // espacios, tambien es `true` (cualquier string no-vacío siempre es verdadero)
```
````

## Resumen

Hay tres conversiones de tipo que son ampliamente utilizadas: a string, a número y a booleano.

**`A String`** -- Ocurre cuando mostramos algo, se puede realizar con `String(valor)`. La conversión a strings usualmente es obvia para valores primitivos.

**`A Número`** -- Ocurre en operaciones matemáticas, se puede realizar con `Number(valor)`.

Esta conversión sigue las reglas:

| Valor |  Se convierte en... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;/&nbsp;false</code> | `1 / 0` |
| `string` | Los espacios en blanco del principio y el final son eliminados. Luego, si el string restante está vacío, el resultado es `0`. De lo contrario, el número se "lee" del string. Un error da `NaN`. |

**`A Booleano`** -- Ocurre en operaciones lógicas, o puede realizarse con `Boolean(valor)`.

Sigue las reglas:

| Valor |  Se convierte en... |
|-------|-------------|
|`0`, `null`, `undefined`, `NaN`, `""` |`false`|
|cualquier otro valor| `true` |

La mayoría de estas reglas son fáciles de entender y memorizar. Las excepciones notables en donde las personas suelen cometer errores son:

- `undefined` es `NaN` cuando es convertido en número, no `0`.
- `"0"` y los strings que solo continen espacios como `"   "` son `true` como un valor booleano.

Los objetos no son cubiertos aquí, regresaremos a ellos más adelante en el capítulo <info:objeto-a-primitivo> que se dedica exclusivamente a los objetos, después de que aprendemos más cosas básicas acerca de JavaScript.
