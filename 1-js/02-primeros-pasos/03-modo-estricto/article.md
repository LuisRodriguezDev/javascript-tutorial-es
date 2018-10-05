# El modo moderno, "usa estricto"

Durante mucho tiempo, JavaScript evolucionó sin problemas de compatibilidad. Se agregaban nuevas características al lenguaje, pero la funcionalidad anterior no cambiaba.

Esto tuvo el beneficio de nunca romper código ya existente. Pero el inconveniente fue que cualquier error o decisión imperfecta por parte de los creadores de JavaScript se quedo atascada en el lenguaje para siempre.

Fue asi hasta el 2009, cuando apareció ECMAScript 5 (ES5). Esta nueva versión agregó nuevas características al lenguaje y modificó algunas de las existentes. Para mantener al código antiguo funcionando, la mayoría de las modificaciones están desactivadas por defecto. Uno necesita habilitarlas explícitamente con una directiva especial `"use strict"` ("usa estricto" en español).

## "use strict"

La directiva se ve como un string: `"use strict"` o `'use strict'`. Cuando esta se encuentra en la parte superior del script, todo el script funciona a la manera "moderna".

Por ejemplo:

```js
"use strict";

// este código funciona a la manera moderna
...
```

Aprenderemos funciones (una forma de agrupar comandos) pronto.

De cara al futuro, tengamos en cuenta que `"use strict"` se puede poner al inicio de una función (en la mayoría de los tipos de funciones) en lugar de en todo el script. Entonces el modo estricto se habilita solo en esa función. Pero generalmente la gente lo usa para todo el script.


````warn header="Asegurate de que \"use strict\" esté en la parte superior"
Por favor asegurate de que \"use strict\" esté en la parte superior del script, de lo contrario, es posible que el modo estricto no esté habilitado.

En este ejemplo no hay modo estricto :

```js no-strict
alert("algo de código");
// El "use strict" a continuación es ignorado, debe estar en la parte superior

"use strict";

// el modo estricto no está activado
```

Solamente los comentarios pueden aparecer arriba de `"use strict"`.
````

```warn header="No hay forma de cancelar `use strict`"
No existe una directiva `"no use strict"` o similar, que retorne al comportamiento viejo.

Una vez que ingresamos al modo estricto, no hay retorno.
```

## Siempre "usa estricto"

Las diferencias entre el modo `"use strict"` frente al modo "predeterminado" aún no se han cubierto.

En los próximos capítulos, a medida que aprendamos las características del lenguaje, observaremos las diferencias con respecto al modo estricto. Afortunadamente, no hay tantas. Y realmente hacen nuestra vida mejor.

En este momento, basta con saber en general que:

1. La directiva `"use strict"` cambia el motor al modo "moderno", cambiando el comportamiento de algunas características integradas. Veremos los detalles de esto a medida que estudiemos las características.
2. El modo estricto es habilitado por `"use strict"` en la parte superior. También hay varias características del lenguaje como "clases" y "módulos" que habilitan el modo estricto de manera automática.
3. El modo estricto es compatible con todos los navegadores modernos.
4. Siempre se recomienda iniciar los scripts con `"use strict"`. Todos los ejemplos en este tutorial asumen esto, a menos que (muy raramente) se especifique lo contrario.
