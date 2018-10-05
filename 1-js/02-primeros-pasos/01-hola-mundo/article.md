# Hola, Mundo!

El tutorial que estás leyendo trata acerca del núcleo de JavaScript, el cual es
independiente de plataformas. Más adelante, aprenderas Node.JS y otras plataformas que usan este
núcleo.

Pero, necesitamos un entorno de trabajo para ejecutar nuestros scripts, y, solo porque este libro está en línea, el navegador es una buena opción. Mantendremos la cantidad de comandos específicos al navegador (como `alert`) al mínimo, para que no pierdas tiempo en ellos si luego planeas concentrarte en otro entorno como Node.JS. Por el otro lado, los detalles del navegador son explicados en detalle en la [siguiente parte](/ui) del tutorial.

Entonces, primero, veamos cómo adjuntar un script a una página web. Para entornos del lado del servidor, puedes simplemente ejecutarlo con un comando como `"node mi.js"` para Node.JS.

## La etiqueta "script"

Los programas de JavaScript se pueden insertar en cualquier parte de un documento HTML con la ayuda de la etiqueta `<script>`.

Por ejemplo:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>Antes del script...</p>

*!*
  <script>
    alert( 'Hola, mundo!' );
  </script>
*/!*

  <p>...Después del script.</p>

</body>

</html>
```

```online
Puedes ejecutar el ejemplo haciendo clic en el botón "Reproducir" en la esquina superior derecha.
```

La etiqueta `<script>` contiene código JavaScript que se ejecuta automáticamente cuando el navegador se encuentra con la etiqueta.

## El marcado moderno

La etiqueta `<script>` tiene algunos atributos que rara vez se usan hoy en día, pero podemos encontrarlos en código antiguo:

 El atributo `type`: <code>&lt;script <u>type</u>=...&gt;</code>

 : El antiguo HTML4 estándar requería que un script tuviera un tipo. Usualmente era `type="text/javascript"`. Ya esto no es requerido. Además, el estándar moderno cambió totalmente el significado de este atributo. Ahora puede ser usado para módulos de Javascript. Pero ese es un tema avanzado, hablaremos de módulos más adelante en otra parte del tutorial.

 El atributo `language`: <code>&lt;script <u>language</u>=...&gt;</code>
  : Este atributo estaba destinado a mostrar el lenguaje del script. A dia de hoy, este atributo no tiene sentido, JavaScript es el lenguaje por defecto. Ya no es necesario usarlo.

Comentarios antes y después de los scripts.
: En libros y guías realmente antiguas, uno puede encontrar comentarios dentro de `<script>`, como este:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

    Este truco no es usado en el JavaScript moderno. Estos comentarios se usaban para ocultar el código JavaScript en navegadores antiguos que no conocían la etiqueta `<script>`. Debido a que los navegadores que nacieron en los últimos 15 años no tienen este problema, este tipo de comentarios pueden ayudarte a identificar código realmente antiguo.

## Scripts externos

Si tenemos un montón de código JavaScript, podemos ponerlo en un archivo separado.

El archivo del script se adjunta al HTML con el atributo `src`:

```html
<script src="/ruta/al/script.js"></script>
```

Aquí `/ruta/al/script.js` es una ruta absoluta hacia al archivo con el script (desde la raíz del sitio).

También es posible proporcionar una ruta relativa a la página actual. Por ejemplo, `src="script.js"` significaría un archivo `"script.js"` en la carpeta actual.

También podemos proporcionar una URL completa, por ejemplo:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js"></script>
```

Para adjuntar varios scripts, usa múltiples etiquetas:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
Como regla, solo los scripts más simples se ponen en el HTML. Los más complejos residen en archivos separados.

El beneficio de tener un archivo separado es que el navegador lo descargará y luego lo almacenará en su [caché](https://es.wikipedia.org/wiki/Cach%C3%A9_web).

Después de esto, otras páginas que quieran el mismo script, lo sacarán del caché en lugar de descargarlo. Entonces, el archivo solo sera descargado una vez.

Eso ahorra tráfico y hace que las páginas sean más rápidas.
```

````warn header="Si `src` tiene un valor, el contenido dentro del script es ignorado."
Una sola etiqueta `<script>` no puede tener el atributo `src` y código adentro de ella.

Esto no funcionará:

```html
<script *!*src*/!*="archivo.js">
  alert(1); // el contenido es ignorado, porque el atributo src esta en la etiqueta
</script>
```

Debemos elegir: o bien es un `<script src="…">` externo o un `<script>` regular con código.

El ejemplo anterior se puede dividir en dos scripts para que funcione:

```html
<script src="archivo.js"></script>
<script>
  alert(1);
</script>
```
````

## Resumen

- Podemos usar una etiqueta `<script>` para agregar código JavaScript a la página.
- Los atributos `type` y `language` no son necesarios.
- Un script en un archivo externo se puede insertar con `<script src="ruta/al/script.js"></script>`.


Hay mucho más que aprender acerca de los scripts de navegador y su interacciones con las páginas web. Pero tengamos en cuenta que esta parte del tutorial está dedicada al lenguaje JavaScript, por lo que no deberíamos distraernos de eso. Estaremos usando un navegador como una manera de ejecutar JavaScript, la cual es muy conveniente para la lectura en línea, pero es solo una de muchas maneras
de ejecutar JavaScript.
