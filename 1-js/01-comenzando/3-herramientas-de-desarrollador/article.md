# Consola del Desarrollador

El código es propenso a errores. Es muy probable que cometas errores... Oh, ¿qué estoy diciendo? *Absolutamente* vas a cometer errores, al menos si eres un humano y no un [robot](https://es.wikipedia.org/wiki/Bender_(Futurama)).

Pero en el navegador, un usuario no ve los errores por defecto. Entonces, si algo sale mal en el script, no veremos qué está roto y no podremos arreglarlo.

Para ver los errores y obtener mucha otra información útil acerca de los scripts, los navegadores incorporan una serie de "herramientas de desarrollador".

La mayoría de los programadores tienden a elegir Chrome o Firefox para el desarrollo, ya que estos navegadores tienen las mejores herramientas de desarrollo. Otros navegadores también proporcionan herramientas de desarrollo, a veces con características especiales, pero generalmente están jugando a "ponerse al día" con Chrome o Firefox. Entonces la mayoría de las personas tiene un navegador "favorito" y solo cambia a otros si el problema es algo específico del navegador.

Las herramientas de desarrollo son realmente poderosas, estas incluyen muchas funciones. Para comenzar, aprenderemos cómo abrirlas, ver errores y ejecutar comandos de JavaScript.

## Google Chrome

Abre la página [bug.html](bug.html).

Hay un error en el código JavaScript en ella. Está oculto ante los ojos de un visitante normal, así que necesitaremos a abrir las herramientas de desarrollador para poder verlo.

Presiona `key:F12` o, si estás en Mac, `key:Cmd+Opt+J`.

Las herramientas de desarrollador se abrirán con la pestaña Consola seleccionada de manera predeterminada.

Se ve algo como esto:

![chrome](chrome.png)

El aspecto exacto de las herramientas de desarrollo depende de tu versión de Chrome. Cambia de tiempo en tiempo, pero debería de verse similar.

- Aquí podemos ver el mensaje de error en un color rojo. En este caso, el script contiene un comando desconocido "lalala".
- A la derecha, hay un enlace `bug.html:12` el cual dirige hacia al número de línea en donde se produjo el error.

Debajo del mensaje de error hay un símbolo `>` azul. Este marca una "línea de comando" donde podemos escribir comandos de JavaScript y presionar `key:Enter` para ejecutarlos (`key:Shift+Enter` para ingresar comandos de varias líneas).

Ahora podemos ver errores y eso es suficiente para comenzar. Volveremos a las herramientas de desarrollador más adelante y cubriremos la depuración con más profundidad en el capítulo <info:depurando-chrome>.

## Firefox, Edge y otros

La mayoría de los otros navegadores usan `key:F12` para abrir las herramientas del desarrollador.

La apariencia de las herramientas entre navegadores es bastante similar. Una vez que sepas cómo usar las herramientas en alguno de ellos (puedes comenzar con Chrome), puedes fácilmente cambiar a las de otro.

## Safari

Safari (navegador de Mac, no compatible con Windows/Linux) es un poco especial aquí. Necesitamos primero habilitar el "menú de Desarrollador".

Abre Preferencias y ve al panel "Avanzado". Hay una casilla de verificación en la parte inferior:

![safari](safari.png)

Ahora `key:Cmd+Opt+C` puede abrir la consola. También ten en cuenta que ha aparecido un nuevo elemento en el menú superior llamado "Desarrollo". Tiene muchos comandos y opciones.

## Resumen

- Las herramientas de desarrollador nos permiten ver errores, ejecutar comandos, examinar variables y mucho más.
- Estas se pueden abrir con `key:F12` para la mayoría de navegadores en Windows. Chrome para Mac necesita `key:Cmd+Opt+J`, Safari: `key:Cmd+Opt+C` (necesitan ser habilitadas primero).

Ahora tenemos el entorno listo. En la siguiente sección, nos adentraremos a JavaScript.
