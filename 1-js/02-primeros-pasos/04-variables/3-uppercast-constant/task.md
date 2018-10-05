importance: 4

---

# Constante en mayúsculas?

Examina el siguiente código:

```js
const cumpleaños = '18.04.1982';

const edad = algoDeCodigo(cumpleaños);
```

Aquí tenemos una fecha de `cumpleaños` constante y una `edad` que se calcula a partir de `cumpleaños` con la ayuda de algún código (no se proporciona para mantener al código conciso, y porque los detalles no importan aquí).

¿Sería correcto usar mayúsculas para `cumpleaños`? Para `edad`? O incluso para las dos?

```js
const CUMPLEAÑOS = '18.04.1982'; // poner en mayúsculas?

const EDAD = algoDeCodigo(CUMPLEAÑOS); // poner en mayúsculas?
```
