# Una Introducción a JavaScript

Vamos a ver que tiene JavaScript que lo hace tan especial,
qué podemos lograr con él y qué otras tecnologías se complementan bien con
este lenguaje.

## ¿Qué es JavaScript?

*JavaScript* se creó inicialmente para *"darle vida a las páginas web"*.

Los programas en este lenguaje son llamados *scripts*. Estos se pueden escribir directamente en el HTML y ejecutarse automáticamente a medida que la página carga.

Los scripts se proporcionan y son ejecutados como texto simple. Estos no necesitan
de una preparación especial o de una compilación para poder ejecutar.

En este aspecto, JavaScript es muy diferente a otro lenguaje llamado [Java](http://en.wikipedia.org/wiki/Java).

```smart header="¿Por qué <u>Java</u>Script?"
Cuando JavaScript fue creado, inicialmente tenía otro nombre: "LiveScript". Pero el lenguaje Java era muy popular en ese entonces, por lo que fue decidido que posicionar un nuevo lenguaje como un "hermano menor" de Java ayudaría con su popularidad.

Pero a medida que evolucionaba, JavaScript se convirtió en un lenguaje totalmente independiente, con su propia especificación llamada
[ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), y ahora no tiene ninguna relación con Java.

```

En la actualidad, JavaScript puede ser ejecutado no solo en el navegador, sino también en el servidor, o en cualquier dispositivo donde exista un programa especial llamado [el motor de JavaScript](https://es.wikipedia.org/wiki/Int%C3%A9rprete_de_JavaScript) .

El navegador tiene un motor incorporado, el cual es a veces llamado una "máquina virtual de JavaScript".

Diferentes motores tienen diferentes "nombres clave", por ejemplo:

- [V8](https://es.wikipedia.org/wiki/Chrome_V8) -- en Chrome y Opera.
- [SpiderMonkey](https://es.wikipedia.org/wiki/SpiderMonkey) -- en Firefox.
- ...Hay otros nombres clave como "Trident", "Chakra" para diferentes versiones de IE, "ChakraCore" para Microsoft Edge, "Nitro" y "SquirrelFish" para Safari, etc.

Es bueno recordar los términos anteriores, ya que estos se usan en artículos para desarrolladores en el Internet. Nosotros los usaremos también. Por ejemplo, si "una característica X es compatible con V8", entonces esta probablemente funcione en
Chrome y Opera.

```smart header="¿Cómo funcionan los motores?"

Los motores son complicados. Pero lo fundamental es fácil de explicar.

1. El motor (incorporado si esta en un navegador) lee ("analiza") el script.
2. Luego convierte ("compila") el script a [código máquina](https://es.wikipedia.org/wiki/Lenguaje_de_m%C3%A1quina).
3. Y luego el código máquina es ejecutado, bastante rápido.

El motor aplica optimizaciones en cada etapa del proceso. Incluso observa el script compilado a medida que este se ejecuta, analiza los datos que fluyen a través de él y aplica optimizaciones al código de máquina en función a ese conocimiento. Al final, los scripts son bastante rápidos.
```

## ¿Qué puede hacer JavaScript en el navegador?

El JavaScript moderno es un lenguaje de programación "seguro". Este no proporciona acceso de bajo nivel a la memoria o al CPU, ya que este se creó inicialmente para navegadores, los cuales no requieren de este tipo de acceso.

Las capacidades dependen en gran medida del entorno en el que se ejecuta JavaScript. Por ejemplo, [Node.JS](https://es.wikipedia.org/wiki/Node.js) soporta funciones que permiten a JavaScript leer/escribir archivos arbitrarios, realizar solicitudes de red, etc.

El JavaScript dentro del navegador puede realizar todo lo relacionado a la manipulación de la página web e interacciones con el usuario y con servidores web.

Por ejemplo, el JavaScript dentro del navegador puede:

- Agregar nuevo HTML a la página, cambiar el contenido existente, modificar estilos.
- Reaccionar a las acciones del usuario, ejecutar con clics del ratón, movimientos del puntero, pulsaciones de teclas.
- Enviar solicitudes a través de la red a servidores remotos, descargar y subir archivos (con las llamadas tecnologías [AJAX](https://es.wikipedia.org/wiki/AJAX) y
[COMET](https://es.wikipedia.org/wiki/Comet)).
- Obtener y configurar cookies, hacer preguntas al visitante, mostrar mensajes.
- Recordar datos en el lado del cliente ("almacenamiento local").

## ¿Qué NO PUEDE hacer JavaScript en el navegador?

Las capacidades de JavaScript en el navegador son limitadas por el bien de la seguridad del usuario. El objetivo es evitar que una página web maliciosa acceda a información privada o dañe datos del usuario.

Ejemplos de tales restricciones son:

- JavaScript en una página web no puede leer/escribir archivos arbitrarios en el disco duro, copiarlos o ejecutar programas. Este no tiene acceso directo a las funciones del sistema operativo.

    Los navegadores modernos le permiten a JavaScript trabajar con archivos, pero el acceso es limitado y solo es proporcionado si el usuario realiza determinadas acciones, como "soltar" un archivo en una ventana del navegador o seleccionarlo a traves de una etiqueta `<input>`.

    Hay formas de interactuar con la cámara/micrófono y otros dispositivos, pero requieren del permiso explícito de un usuario. Por lo tanto, una página habilitada por JavaScript no puede activar a escondidas una cámara web, observar los alrededores y enviar
    información a la [NSA](https://es.wikipedia.org/wiki/Agencia_de_Seguridad_Nacional).
- Diferentes pestañas/ventanas generalmente no saben una acerca de la otra. A veces lo hacen, por ejemplo, cuando una ventana usa JavaScript para abrir a la otra. Pero incluso en este caso, el JavaScript de una página no podria poder acceder a la otra si provienen de sitios diferentes (de dominios, protocolos o puertos diferentes).

    Esto se conoce como "Política del Mismo Origen". Para solucionar esto, *ambas páginas* deben contener un código JavaScript especial que maneje el intercambio de datos.

    La limitación es nuevamente por la seguridad del usuario. Una página `http://cualquiersitio.com` que un usuario haya abierto no debe poder acceder a otra pestaña del navegador con la URL`http://gmail.com` y robar información de allí.
- JavaScript puede comunicarse fácilmente a través de la red con el servidor de donde proviene la página actual. Pero su capacidad para recibir datos de otros sitios/dominios está lisiada. Aunque posible, esta requiere de un acuerdo explícito (expresado a traves de los encabezados HTTP) del lado remoto. Una vez más, esto es por limitaciones de seguridad.

![](limitations.png)

Tales límites no existen si JavaScript se utiliza fuera del navegador, por ejemplo, en un servidor. Los navegadores modernos también permiten instalar complementos/extensiones que pueden obtener permisos extendidos.

## ¿Qué hace que JavaScript sea único?

Hay al menos *tres* cosas especiales acerca de JavaScript:

```compare
+ Integración completa con HTML/CSS.
+ Cosas simples hechas simplemente.
+ Compatible con todos los navegadores principales y habilitado por defecto.
```

Combinadas, estas tres cosas existen solo en JavaScript y en ninguna otra tecnología de navegador.

Eso es lo que hace que JavaScript sea único. Es por eso que es la herramienta más utilizada para crear interfaces para navegadores.

Mientras se planifica aprender una nueva tecnología, es beneficioso chequear sus perspectivas. Asi que pasemos a las tendencias modernas que incluyen nuevos lenguajes y habilidades de navegador.

## Lenguajes "arriba" de JavaScript

La sintaxis de JavaScript no se adapta a las necesidades de todos. Diferentes personas quieren diferentes características.

Eso es lo esperado, ya que proyectos y requisitos son diferentes para todos.

Asi que recientemente han aparecido una gran cantidad de nuevos lenguajes, que son *transpilados* (convertidos) a JavaScript antes de que se ejecuten en el navegador.

Las herramientas modernas hacen que la transpilación sea muy rápida y transparente, lo que le permite a los desarrolladores programar en otro lenguaje y autoconvertirlo "bajo el capó".

Ejemplos de tales lenguajes:

- [CoffeeScript](http://coffeescript.org/) es "azúcar sintáctico" para JavaScript, este introduce una sintaxis más corta, lo que permite escribir código más preciso y claro. Normalmente a los desarrolladores de Ruby les gusta.
- [TypeScript](http://www.typescriptlang.org/) se concentra en agregar "tipos de datos estrictos" para simplificar el desarrollo y soportar sistemas complejos. Es desarrollado por Microsoft.
- [Dart](https://www.dartlang.org/) es un lenguaje independiente que tiene su propio motor que se ejecuta en entornos que no son de navegador (como aplicaciones móviles). Inicialmente fue ofrecido por Google como un reemplazo para JavaScript, pero al dia de hoy, los navegadores requieren que este sea transpilado a JavaScript al igual que los lenguajes de arriba.

Hay mas. Por supuesto, incluso si usamos alguno de esos lenguajes, también deberíamos conocer JavaScript, para entender realmente lo que estamos haciendo.

## Resumen

- JavaScript se creó inicialmente como un lenguaje solamente para navegadores, pero ahora también es usado en muchos otros entornos.
- En este momento, JavaScript tiene una posición única como el lenguaje de navegador más adoptado con integración completa con HTML/CSS.
- Hay muchos lenguajes que son "transpilados" a JavaScript y proporcionan ciertas características. Se recomienda echarles un vistazo, al menos brevemente, después de dominar JavaScript.
