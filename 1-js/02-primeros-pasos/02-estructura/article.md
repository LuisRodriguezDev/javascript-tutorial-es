# Estructura del código

Lo primero que vamos a estudiar son los bloques de construcción del código.

## Declaraciones

Las declaraciones son constructos de sintaxis y comandos que realizan acciones.

Ya hemos visto una declaración `alert('Hola, mundo!')`, la cual muestra un mensaje.

Podemos tener tantas declaraciones en el código como queramos. Otra declaración puede
ser separarada con un punto y coma.

Por ejemplo, aquí dividimos el mensaje en dos:

```js run no-beautify
alert('Hola'); alert('Mundo');
```

Por lo general, cada declaración se escribe en una línea por separado -- por lo que el código se vuelve más legible:

```js run no-beautify
alert('Hola');
alert('Mundo');
```

## Puntos y comas [#semicolon]

Un punto y coma puede ser omitido en la mayoría de los casos en donde
existe un salto de línea.

Esto también funcionaría:

```js run no-beautify
alert('Hola')
alert('Mundo')
```

Aquí JavaScript interpreta el salto de línea como un punto y coma "implícito". Esto también se conoce como [inserción automática de punto y coma](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion).

**En la mayoría de los casos, una nueva línea implica un punto y coma. ¡Pero "en la mayoría de los casos" no significa "siempre"!**

Hay casos en los que una nueva línea no representa un punto y coma, por ejemplo:

```js run no-beautify
alert(3 +
1
+ 2);
```

El código muestra `6`, porque JavaScript no inserta puntos y comas aquí. Es intuitivamente obvio que si la línea termina con un más `"+"`, entonces esta es una "expresión incompleta", por lo que no se requiere un punto y coma. Y en este caso, esto funciona según lo previsto.

**Pero hay situaciones en las que JavaScript "falla" en asumir un punto y coma donde realmente se necesita.**

Los errores que ocurren en tales casos son bastante difíciles de encontrar y corregir.

````smart header="Un ejemplo de un error"
Si tienes curiosidad de ver un ejemplo concreto de tal error, chequeá este código:

```js run
[1, 2].forEach(alert)
```

No es necesario que pienses en el significado de los corchetes `[]` y `forEach` todavía. Los estudiaremos más adelante, por ahora no importan. Solo recordemos el resultado:
este muestra `1` y luego `2`.

Ahora agreguemos un `alert` antes del código y *no* lo terminaremos con un punto y coma:

```js run no-beautify
alert("Habrá un error")

[1, 2].forEach(alert)
```

Ahora si lo ejecutamos, solo se muestra el primer `alert`, ¡y entonces tenemos un error!

Pero todo está bien nuevamente si agregamos un punto y coma después del `alert`:
```js run
alert("Todo esta bien ahora");

[1, 2].forEach(alert)  
```

Ahora tenemos el mensaje "Todo esta bien ahora" y luego `1` y `2`.


El error en la variante sin punto y coma ocurre porque JavaScript implica un punto y coma antes de los corchetes `[...]`.

Por lo tanto, como el punto y coma no se inserta automáticamente, el código en el primer ejemplo es tratado como una sola declaración. Así es como lo ve el motor:

```js run no-beautify
alert("Habrá un error")[1, 2].forEach(alert)
```

Pero deberian ser dos declaraciones separadas, no una sola. Tal fusión en este caso es simplemente errónea, de ahí el error. Hay otras situaciones en las que sucede lo mismo.
````

Se recomienda poner puntos y comas entre declaraciones, incluso si estas están separadas por líneas nuevas. Esta regla es ampliamente adoptada por la comunidad. Tomemos nota una vez más -- *es posible* omitir los puntos y comas la mayor parte del tiempo. Pero es más seguro -- especialmente para un principiante -- usarlos.

## Comentarios

A medida que pasa el tiempo, el programa se vuelve más y más complejo. Ahora se vuelve una necesidad agregar *comentarios* que describan qué sucede y el por qué.

Los comentarios pueden colocarse en cualquier lugar del script. Estos no afectan a la ejecución, ya que el motor simplemente los ignora.

**Los comentarios de una línea comienzan con dos caracteres de barra diagonal `//`.**

El resto de la línea es un comentario. Este puede ocupar una línea completa o seguir una declaración.

Como aquí:
```js run
// Este comentario ocupa una línea completa
alert('Hola');

alert('Mundo'); // Este comentario sigue a la declaración
```

**Los comentarios de múltiples líneas comienzan con una barra inclinada y un asterisco <code>/&#42;</code> y finalizan con un asterisco y una barra inclinada <code>&#42;/</code>.**

Asi:

```js run
/* Un ejemplo con dos mensajes.
Este es un comentario de múltiples líneas.
*/
alert('Hola');
alert('Mundo');
```

El contenido de los comentarios es ignorado, por lo que si ponemos código dentro de <code>/&#42; ... &#42;/</code> este no se ejecutará.

Esto es útil algunas veces para desactivar temporalmente una parte del código:

```js run
/* Desactivando el código con comentarios
alert('Hola');
*/
alert('Mundo');
```

```smart header="Usa atajos!"
En la mayoría de los editores, una línea de código puede ser comentada con el atajo `key:Ctrl+/` para un comentario de una sola línea y algo como `key:Ctrl+Shift+/` -- para comentarios de líneas múltiples (selecciona un fragmento de código y utiliza el atajo). Para Mac prueba con `key:Cmd` en lugar de `key:Ctrl`.
```

````warn header="¡Los comentarios anidados no se permiten!"
No puede haber `/*...*/` dentro de otro `/*...*/`.

Tal código morirá con un error:

```js run no-beautify
/*
  /* comentario anidado? ?!? */
*/
alert( 'Mundo' );
```
````

Por favor, no dudes en comentar tu código.

Los comentarios aumentan el tamaño general del código, pero eso no es un problema en absoluto. Hay muchas herramientas que minimizan el código antes de subirlo al servidor de producción. Estas remueven los comentarios, por lo que estos no aparecen en los scripts de tus páginas. Por lo tanto, los comentarios no tienen ningún efecto negativo en producción.

Mas adelante en el tutorial, habrá un capítulo de <info:estilo-de-codigo> que también explica cómo escribir mejores comentarios.
