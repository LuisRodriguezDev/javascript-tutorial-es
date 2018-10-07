
```js no-beautify
"" + 1 + 0 = "10" // (1)
"" - 1 + 0 = -1 // (2)
true + false = 1
6 / "3" = 2
"2" * "3" = 6
4 + 5 + "px" = "9px"
"$" + 4 + 5 = "$45"
"4" - 2 = 2
"4px" - 2 = NaN
7 / 0 = Infinity
" -9\n" + 5 = " -9\n5"
" -9\n" - 5 = -14
null + 1 = 1 // (3)
undefined + 1 = NaN // (4)
```

1. La adición con un string `"" + 1` convierte `1` en un string: `"" + 1 = "1"`, y luego tenemos `"1" + 0`, donde se aplica la misma regla.
2. La resta `-` (como la mayoría de las operaciones matemáticas) solo funciona con números, esta convierte el string vacío `""` a `0`.
3. `null` se convierte en `0` después de la conversión numérica.
4. `undefined` se convierte en `NaN` después de la conversión numérica.
