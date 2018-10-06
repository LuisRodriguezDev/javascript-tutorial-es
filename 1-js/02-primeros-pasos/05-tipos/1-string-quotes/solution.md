
Las comillas invertidas incrustan la expresión dentro de `${...}` dentro del string.

```js run
let nombre = "Ilya";

// la expresión es un número 1
alert( `hola ${1}` ); // hola 1

// la expresión es un string "nombre"
alert( `hola ${"nombre"}` ); // hola nombre

// la expresión es una variable, esta es incrustada
alert( `hola ${nombre}` ); // hola Ilya
```
