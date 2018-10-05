# Variables

La mayoría de las veces, una aplicación hecha con JavaScript necesita trabajar con información. Aquí hay 2 ejemplos:
1. Una tienda en línea -- la información puede incluir productos que se venden y un carrito de compras.
2. Una aplicación de chat -- la información puede incluir usuarios, mensajes y mucho más.

Las variables se usan para almacenar esta información.

## Una variable

Una [variable](https://es.wikipedia.org/wiki/Variable_(programaci%C3%B3n)) es un "espacio de almacenamiento con un nombre" para guardar datos. Podemos usar variables para almacenar regalos, visitantes y otros datos.

Para crear una variable en JavaScript, necesitamos usar la palabra clave `let`.

La siguiente declaración crea (en otras palabras: *declara* o *define*) una variable con el nombre "mensaje":

```js
let mensaje;
```

Ahora podemos poner algunos datos en ella utilizando el operador de asignación `=`:

```js
let mensaje;

*!*
mensaje = 'Hola'; // almacena el string
*/!*
```

El string ahora esta guardado en el área de memoria asociada con la variable. Podemos acceder a este valor al usar el nombre de la variable:

```js run
let mensaje;
mensaje = 'Hola!';

*!*
alert(mensaje); // muestra el contenido de la variable
*/!*
```

Para ser concisos, podemos fusionar la declaración de variable y la asignación en una sola línea:

```js run
let mensaje = 'Hola!'; // define la variable y asigna el valor

alert(mensaje); // Hola!
```

También podemos declarar múltiples variables en una sola línea:

```js no-beautify
let usuario = 'John', edad = 25, mensaje = 'Hola';
```

Esto puede parecer más corto, pero no es recomendable. Por el bien de una mejor legibilidad,
por favor usa una sola línea por variable.

La variante con líneas múltiples es un poco más larga, pero es más fácil de leer:

```js
let usuario = 'John';
let edad = 25;
let mensaje = 'Hola';
```

Algunas personas también escriben muchas variables de esta manera:
```js no-beautify
let usuario = 'John',
  edad = 25,
  mensaje = 'Hola';
```

...O incluso con el estilo de "coma primero":

```js no-beautify
let usuario = 'John'
  , edad = 25
  , mensaje = 'Hola';
```

Técnicamente, todas estas variantes hacen lo mismo. Entonces, es una cuestión de preferencias personales y estética.


````smart header="`var` en lugar de `let`"
En scripts viejos puedes encontrar otra palabra clave: `var` en lugar de `let`:

```js
*!*var*/!* mensaje = 'Hola';
```

La palabra clave `var` es *casi* igual que `let`. Esta también declara una variable, pero en una manera ligeramente diferente, a la "vieja escuela".

Hay sutiles diferencias entre `let` y `var`, pero estas aún no nos importan. Las cubriremos en detalle más adelante, en el capítulo <info:var>.
````

## Una analogía de la vida real

Podemos comprender fácilmente el concepto de una "variable" si la imaginamos como una "caja" para datos, con una pegatina con un nombre único pegada en ella.

Por ejemplo, la variable `mensaje` puede ser imaginada como una caja con la etiqueta `"mensaje"` y con el valor `"Hola!"` dentro de ella:

![](variable.png)

Podemos poner cualquier valor dentro de la caja.

También podemos cambiarlo. El valor se puede cambiar tantas veces como sea necesario:

```js run
let mensaje;

mensaje = 'Hola!';

mensaje = 'Mundo!'; // el valor cambio

alert(mensaje);
```

Cuando se cambia el valor, los datos antiguos son eliminados de la variable:

![](variable-change.png)

También podemos declarar dos variables y copiar datos de una a la otra.

```js run
let hola = 'Hola mundo!';

let mensaje;

*!*
// copiar 'Hola mundo' de hola a mensaje
mensaje = hola;
*/!*

// ahora las dos variables contienen los mismos datos
alert(hola); // Hola mundo!
alert(mensaje); // Hola mundo!
```

```smart header="Lenguajes funcionales"
Puede ser interesante saber que también existen lenguajes de programación [funcional](https://es.wikipedia.org/wiki/Programaci%C3%B3n_funcional), los cuales prohíben cambiar el valor de una variable. Como por ejemplo, [Scala](http://www.scala-lang.org/) o [Erlang](http://www.erlang.org/).

En tales lenguajes, una vez que el valor se almacena "en la caja", se queda ahí para siempre. Si necesitamos almacenar algo más, el lenguaje nos obliga a crear una nueva caja (declarar una nueva variable). No podemos reutilizar la anterior.

Aunque puede parecer un poco extraño a primera vista, estos lenguajes son bastante capaces de desarrollar programas serios. Más que eso, existen áreas como las computaciones paralelas en donde esta limitación confiere ciertos beneficios. Se recomienda estudiar alguno de esos lenguajes (incluso si no planeas usarlo en un futuro cercano) para ampliar la mente.
```

## Nombrando variables [#variable-naming]

Hay dos limitaciones para el nombre de una variable en JavaScript:

1. El nombre puede contener solo letras, dígitos, y los símbolos `$` y `_`.
2. El primer cáracter no puedes ser un dígito.

Nombres válidos, por ejemplo:

```js
let nombreDeUsuario;
let prueba123;
```

Cuando el nombre contiene varias palabras, [camelCase](https://es.wikipedia.org/wiki/CamelCase) se utiliza comúnmente. Es decir: las palabras van una tras otra, y cada palabra empieza con una letra en mayúscula: `miMuyLargoNombre`.

Lo que es interesante -- el signo de dólar `'$'` y el guión bajo `'_'` también pueden ser usados en los nombres. Son símbolos regulares, como las letras, sin ningún significado especial.

Estos nombres son válidos:

```js run untrusted
let $ = 1; // se declaró una variable con el nombre "$"
let _ = 2; // y ahora una variable con el nombre "_"

alert($ + _); // 3
```

Ejemplos de nombres de variables incorrectos:

```js no-beautify
let 1a; // no puede comenzar con un dígito

let mi-nombre; // un guión '-' no está permitido en el nombre
```

```smart header="Mayúsculas y minúsculas importan"
Las variables llamadas `manzana` y` ManzaNA` -- son dos variables diferentes.
```

````smart header="Se permiten letras que no provengan del ingles, pero no se recomiendan"
Es posible usar cualquier lenguaje, incluidas letras cirílicas o incluso jeroglíficos, de esta manera:

```js
let имя = '...';
let 我 = '...';
```

Técnicamente, no hay ningún error aquí, tales nombres están permitidos, pero existe una tradición internacional de utilizar inglés para los nombres de las variables. Incluso si estamos escribiendo un script pequeño, puede que este tenga una larga vida por delante. Las personas de otros países podrían necesitar leerlo alguna vez.
````

````warn header="Nombres reservados"
Hay una lista de palabras reservadas, las cuales no pueden ser usadas como nombres de variables, ya que estas son usadas por el lenguaje en si mismo.

Por ejemplo, las palabras `let`, `class`, `return`, `function` están reservadas.

El código a continuación da un error de sintaxis:

```js run no-beautify
let let = 5; // no se le puede dar el nombre "let" a una variable , error!
let return = 5; // tampoco puedo nombrarse "return", error!
```
````

````warn header="Una asignación sin `use strict`"

Normalmente, necesitamos definir una variable antes de usarla. Pero en los viejos tiempos, era técnicamente posible crear una variable con una mera asignación de valor, sin `let`. Esto todavía funciona si no ponemos `use strict` al comienzo de nuestro código. Este comportamiento se ha mantenido para mantener la compatibilidad con viejos scripts.

```js run no-strict
// nota: no se usa el modo estricto en este ejemplo

numero = 5; // la variable "numero" es creada si esta no existia antes

alert(numero); // 5
```

Esa es una mala práctica, da un error en el modo estricto:

```js run untrusted
"use strict";

*!*
numero = 5; // error: numero is not defined
*/!*
```

````

## Constantes

Para declarar una variable constante (inmutable), uno puede usar `const` en lugar de `let`:

```js
const miCumpleaños = '18.04.1982';
```

Las variables declaradas usando `const` son llamadas "constantes". No pueden ser cambiadas. Un intento de hacerlo causaría un error:

```js run
const miCumpleaños = '18.04.1982';

miCumpleaños = '01.01.2001'; // error, no se puede reasignar la constante!
```

Cuando un programador está seguro de que la variable nunca deberia cambiar, puede usar `const` para garantizar esto, y también para mostrar claramente ese hecho ante cualquier persona que lea su código.

### Constantes en mayúsculas

Existe una práctica generalizada de usar constantes como alias para valores difíciles de recordar, los cuales son conocidos antes de la ejecución.

Tales constantes son nombradas usando letras mayúsculas y guiones bajos.

De esta manera:

```js run
const COLOR_ROJO = "#F00";
const COLOR_VERDE = "#0F0";
const COLOR_AZUL = "#00F";
const COLOR_NARANJA = "#FF7F00";

// ...cuando necesitamos elegir un color
let color = COLOR_NARANJA;
alert(color); // #FF7F00
```

Beneficios:

- `COLOR_NARANJA` es mucho más fácil de recordar que `"#FF7F00"`.
- Es mucho más fácil de cometer un error al escribir `"#FF7F00"` que `COLOR_NARANJA`.
- Al leer el código, `COLOR_NARANJA` es mucho más significativo que `#FF7F00`.

¿Cuándo deberíamos de usar mayúsculas para una constante, y cuándo deberíamos nombrarlas normalmente? Vamos a aclarar eso.

Ser una "constante" solo significa que el valor nunca cambia. Pero hay constantes que se conocen antes de la ejecución (como un valor hexadecimal para el color rojo), y luego están las que son *calculadas* durante el tiempo de ejecución, pero que no cambian después de la asignación.

Por ejemplo:
```js
const tiempoDeCargaPagina = /* tiempo que le toma cargar a una página web */;
```

El valor de `tiempoDeCargaPagina` no se conoce antes de que la página cargue, por lo que se nombra normalmente. Pero sigue siendo una constante, ya que no cambia después de la asignación.

En otras palabras, las constantes con nombre en mayúsculas solo se utilizan como alias para valores codificados de "forma fija".

## Nombra las cosas bien

Hablando de variables, hay una cosa extremadamente importante.

Por favor, nombra las variables con sensatez. Tomate el tiempo para pensar si es necesario.

Nombrar variables es una de las habilidades más importantes y complejas en la programación. Un vistazo rápido a los nombres de las variables puede revelar qué código está escrito por un principiante y cuál por un programador experimentado.

En un proyecto real, la mayor parte del tiempo se gasta en modificar y ampliar la base de códigos existente, en lugar de escribir algo completamente separado desde cero. Y cuando regresamos al código después de algún tiempo de estar haciendo otra cosa, es mucho más fácil encontrar información que esta bien etiquetada. O, en otras palabras, cuando las variables tienen buenos nombres.

Dedica un momento a pensar en el nombre correcto de una variable antes de declararla. Esto te ayudara mucho.

Algunas buenas reglas para seguir son:

- Usa nombres legibles por humanos como `nombreDeUsuario` o `carroDeCompras`.
- Mantente alejado de abreviaturas o nombres cortos como `a`, `b`, `c`, a menos que realmente sepas lo que estas haciendo.
- Haz que el nombre sea lo mas descriptivo y conciso posible. Ejemplos de malos nombres son `datos` y `valor`. Tales nombres no dicen nada. Solo está bien usarlos si el contexto hace que sea excepcionalmente obvio saber a que se refieren los datos o el valor.
- Acuerda los términos dentro de tu equipo y en tu propia mente. Si un visitante del sitio es llamado un "usuario", entonces deberíamos nombrar variables relacionadas como `usuarioActual` o `nuevoUsuario`, pero no `visitanteActual` o `nuevoHombreEnLaCiudad`.

Suena simple? De hecho lo es, pero, en la práctica, la creación de buenos nombres descriptivos y concisos no es tan sencillo. Esfuerzate por ello.

```smart header="Reutilizar o crear?"
Y la última nota. Hay algunos programadores perezosos que, en lugar de declarar una nueva variable, tienden a reutilizar las existentes.

Como resultado, la variable es como una caja en donde las personas arrojan cosas diferentes sin cambiar la etiqueta. ¿Qué hay dentro de ella ahora? Quién sabe... Tenemos que acercarnos y verificar.

Tal programador ahorra un poco en la declaración de variables, pero pierde diez veces más en la depuración del código.

Una variable extra es buena, no malvada.

Los navegadores y minificadores de JavaScript modernos optimizan el código lo suficientemente bien, por lo que esto no creará problemas de rendimiento. Usar diferentes variables para diferentes valores incluso puede ayudar al motor a realizar optimizaciones.
```

## Resumen

Podemos declarar variables para almacenar datos. Eso se puede hacer usando `var` o `let` o `const`.

- `let` -- es una declaración de variable moderna. El código debe estar en modo estricto para usar `let` en Chrome (V8).
- `var` -- es una declaración de variable a la vieja escuela. Normalmente no la usamos en absoluto, pero cubriremos sutiles diferencias con `let` en el capítulo <info:var>, en caso de que necesites saberlas.
- `const` -- es como `let`, pero el valor de la variable no puede ser cambiado.

Las variables deben nombrarse de una manera que nos permita comprender fácilmente qué hay dentro.
