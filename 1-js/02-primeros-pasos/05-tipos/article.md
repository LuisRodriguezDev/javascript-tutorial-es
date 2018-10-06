# Tipos de datos

Una variable en JavaScript puede contener cualquier dato. Una variable puede ser un string en un momento y luego recibir un valor numérico:

```js
// no hay error
let mensaje = "hola";
mensaje = 123456;
```

Los lenguajes de programación que permiten tales cosas se dice que usan un ["tipado dinámico"](https://es.wikipedia.org/wiki/Tipado_din%C3%A1mico), lo que significa que hay tipos de datos, pero que las variables no están vinculadas a ninguno de ellos.

Hay siete tipos de datos básicos en JavaScript. Aquí estudiaremos lo básico, y en los próximos capítulos hablaremos de cada uno de ellos en más detalle.

## Un número

```js
let n = 123;
n = 12.345;
```

El tipo *número* sirve tanto para números enteros como para números decimales.

Hay muchas operaciones para los números, por ejemplo: multiplicación `*`, división `/`, adición `+`, substracción `-` y así sucesivamente.

Además de los números regulares, existen los llamados "valores numéricos especiales" que también pertenecen a ese tipo: `Infinity`, `-Infinity` y `NaN`.

- `Infinity` representa el [Infinito](https://es.wikipedia.org/wiki/Infinito) matemático ∞. Es un valor especial que es mayor que cualquier número.



    Podemos obtenerlo como el resultado de una división por cero:

    ```js run
    alert( 1 / 0 ); // Infinity
    ```

    O simplemente mencionarlo directamente en el código:

    ```js run
    alert( Infinity ); // Infinity
    ```
- `NaN` representa un error computacional. Es el resultado de una operación matemática incorrecta o indefinida, por ejemplo:

    ```js run
    alert( "no es un número" / 2 ); // NaN, tal división es errónea
    ```

    `NaN` es pegajoso. Cualquier operación adicional con `NaN` daría `NaN` como resultado:

    ```js run
    alert( "no es un número" / 2 + 5 ); // NaN
    ```

    Entonces, si hay un `NaN` en algún lugar de una expresión matemática, este se propaga a todo el resultado.

```smart header="Las operaciones matemáticas son seguras"
Realizar matemáticas en JavaScript es seguro. Podemos hacer cualquier cosa: dividir por cero, tratar strings no numéricos como números, etc.

El script nunca se detendrá con un error fatal. En el peor de los casos obtendremos `NaN` como el resultado.
```

Los valores numéricos especiales formalmente pertenecen al tipo "número". Por supuesto que no son números en el sentido común de esta palabra.

Veremos más acerca de cómo trabajar con números en el capítulo <info:numero>.

## Un string ("cadena de cáracteres")

Un string en JavaScript debe estar entre comillas.

```js
let str = "Hola";
let str2 = 'Las comillas simples también funcionan';
let frase = `puedes incrustar ${str}`;
```

En JavaScript, hay 3 tipos de comillas.

1. Comillas dobles: `"Hola"`.
2. Comillas simples: `'Hola'`.
3. Comillas invertidas: <code>&#96;Hola&#96;</code>.

Las comillas dobles y simples son comillas "sencillas". No hay diferencia entre ellas en JavaScript.

Las comillas invertidas son comillas con "funcionalidad extendida". Estas nos permiten incrustar variables y expresiones en un string al envoverlas en `${…}`, por ejemplo:

```js run
let nombre = "John";

// incrustar una variable
alert( `Hola, *!*${nombre}*/!*!` ); // Hola, John!

// incrustar una expresión
alert( `el resultado es *!*${1 + 2}*/!*` ); // el resultado es 3
```

La expresión dentro de `${…}` es evaluada y el resultado se convierte en una parte del string. Podemos poner cualquier cosa allí: una variable como `nombre` o una expresión aritmética como `1 + 2` o algo más complejo.

Por favor ten en cuenta que esto solo se puede hacer con comillas invertidas. Otros tipos de comillas no permiten tal incrustación!
```js run
alert( "el resultado es ${1 + 2}" ); // el resultado es ${1 + 2} (las comillas dobles no hacen nada)
```

Cubriremos los strings más a fondo en el capítulo <info:string>.

```smart header="No hay un tipo de *carácter*."
En algunos lenguajes, hay un tipo especial de "carácter" para un solo carácter. Por ejemplo, en el lenguaje C y en Java es `char`.

En JavaScript, no existe tal tipo. Solo hay un tipo: `string`. Un string puede constar de un solo carácter o de muchos de ellos.
```

## Un booleano (tipo lógico)

El tipo booleano tiene solo dos valores: `true` ("verdadero") y `false` ("falso").

Este tipo se usa comúnmente para almacenar valores de sí/no: `true` significa "sí, correcto", y `false` significa "no, incorrecto".

Por ejemplo:

```js
let campoNombreMarcado = true; // si, el campo de nombre esta marcado
let campoEdadMarcado = false; // no, el campo de nombre no esta marcado
```

Los valores booleanos también son el resultado de comparaciones:

```js run
let esMayor = 4 > 1;

alert( esMayor ); // true (el resultado de la comparación es "sí")
```

Cubriremos los booleanos con mayor profundidad más adelante en el capítulo <info:operadores-logicos>.

## El valor "null" ("nulo")

El valor especial `null` no pertenece a ningún tipo de los descritos anteriormente.

Este forma un tipo separado, independiente de los otros, el cual solo contiene el valor `null`:

```js
let edad = null;
```

En JavaScript `null` no es una "referencia a un objeto no existente" o un "puntero nulo" como en otros lenguajes.

Este solamente es un valor especial que tiene el significado de "vacío", "nada", o "valor desconocido".

El código anterior indica que la `edad` es desconocida o está vacía por alguna razón.

## El valor "undefined" ("indefinido")

El valor especial `undefined` se distingue por separado. Este representa un tipo propio, igual que `null`.

El significado de `undefined` es "valor no está asignado".

Si se declara una variable, pero no se le asigna nada, entonces su valor es exactamente `undefined`:

```js run
let x;

alert(x); // muestra "undefined"
```

Técnicamente, es posible asignar `undefined` a cualquier variable:

```js run
let x = 123;

x = undefined;

alert(x); // "undefined"
```

...Pero no se recomienda que hagamos eso. Normalmente, usamos `null` para describir un valor "vacío" o "desconocido" en la variable, y `undefined` solo se usa para verificaciones, para ver si la variable tiene un valor asignado o similar.

## Objetos y Símbolos

El tipo `object` ("objeto") es especial.

Todos los otros tipos son llamados "primitivos", ya que sus valores solo pueden contener una sola cosa (ya sea un string o un número o lo que sea). En contraste, los objetos se utilizan para almacenar colecciones de datos y entidades más complejas. Trataremos con ellos más adelante en el capítulo <info:objeto> después de que sepamos lo suficiente acerca de los primitivos.

El tipo `symbol` ("símbolo") se utiliza para crear identificadores únicos para objetos. Tenemos que mencionarlo aquí para completar nuestro recorrido, pero es mejor estudiarlos después de los objetos.

## El operador typeof [#type-typeof]

El operador `typeof` ("tipo de") retorna el tipo del argumento. Este es útil cuando queremos procesar valores de diferentes tipos de manera diferente, o si simplemente queremos hacer una comprobación rápida.

Este soporta dos formas de sintaxis:

1. Como un operador: `typeof x`.
2. Como una función: `typeof(x)`.

En otras palabras, este funciona con paréntesis o sin ellos. El resultado es el mismo.

La llamada a `typeof x` retorna un string con el nombre del tipo:

```js
typeof undefined // "undefined"

typeof 0 // "number"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

*!*
typeof Math // "object"  (1)
*/!*

*!*
typeof null // "object"  (2)
*/!*

*!*
typeof alert // "function"  (3)
*/!*
```

Las últimas tres líneas pueden necesitar explicaciones adicionales:

1. `Math` es un objeto incorporado que proporciona operaciones matemáticas. Lo aprenderemos a usar en el capítulo <info:numero>. Aquí solo sirve como un ejemplo de un objeto.
2. El resultado de `typeof null` es `"object"`. Eso está mal. Es un error oficialmente reconocido en `typeof`, mantenido por compatibilidad. Por supuesto, `null` no es un objeto. Este es un valor especial con un tipo propio separado. Así que, de nuevo, esto es un error en el lenguaje.
3. El resultado de `typeof alert` es `"function"`, porque `alert` es una función del lenguaje. Estudiaremos las funciones en los próximos capítulos y veremos que no hay un tipo especial de "función" en el lenguaje. Las funciones pertenecen al tipo de objeto. Pero `typeof` las trata de manera diferente. Formalmente, es incorrecto, pero muy conveniente en la práctica.

## Resumen

Hay 7 tipos básicos en JavaScript.

- `number` para números de cualquier tipo: enteros o decimales.
- `string` para cadenas de caracteres. Un string puede tener uno o más caracteres, no hay un tipo separado para un solo carácter.
- `boolean` para `true`/`false`.
- `null` para valores desconocidos -- un tipo independiente que solo tiene el valor `null`.
- `undefined` para valores no asignados -- un tipo independiente que solo tiene el valor `undefined`.
- `object` para estructuras de datos más complejas.
- `symbol` para identificadores únicos.

El operador `typeof` nos permite ver qué tipo está almacenado en la variable.

- Dos formas: `typeof x` o `typeof(x)`.
- Retorna un string con el nombre del tipo, de esta manera: `"string"`.
- Para `null` retorna `"object"` -- esto es un error en el lenguaje, de hecho no es un objeto.

En los siguientes capítulos nos concentraremos en los valores primitivos y, una vez que estemos familiarizados con ellos, pasaremos a los objetos.
