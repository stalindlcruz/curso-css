<!--
Operador Descendiente en CSS
-----------------------------
<article>
  <p>Este es un párrafo dentro del artículo.</p>
  <footer>
    <p>Este es un párrafo dentro del footer.</p>
  </footer>
</article>

article > p {
  font-size: 24px;
  color: blue;
}

Operador Hermano Siguiente
--------------------------
El operador hermano siguiente (~) se utiliza para seleccionar todos los elementos hermanos que aparecen después de otro en el mismo nivel del DOM, sin importar si están inmediatamente después o más adelante.

<p>Este es un párrafo.</p>
<span>Este span será rojo.</span>
<span>Este span también será rojo.</span>

p ~ span {
  color: red;
}

En este caso, todos los <span> que estén después del <p> en el mismo nivel recibirán el color rojo. Los elementos que aparezcan antes del <p> o en otros niveles del HTML no serán afectados.

Operador hermano siguiente inmediato +
--------------------------------------
A diferencia del operador ~, el operador hermano siguiente inmediato (+) solo selecciona el primer elemento hermano que aparece inmediatamente después del elemento especificado.

<p>Este es un párrafo.</p>
<span>Este span será rojo.</span>
<span>Este span NO será rojo.</span>

p + span {
  color: red;
}

En este caso, el CSS solo aplicará el color rojo al primer <span> porque este se encuentra justo después del <p>. El siguiente elemento <span> no será afectado por esta regla.
 -->

<!--
Tabla mental rápida de especificidad (simplificada):

Inline style: 1 0 0 0
IDs: 0 1 0 0 por cada #id
Clases, atributos, pseudo-clases: 0 0 1 0 cada una
Elementos y pseudo-elementos: 0 0 0 1
 -->

<!--
📊 ¿Qué es la Especificidad?
----------------------------
La especificidad es un algoritmo que determina qué selector CSS tiene más prioridad sobre el resto. Por ejemplo, si tienes un párrafo con clase .text y otro estilo que dice que debería ser color rojo, pero aparece azul, es porque el algoritmo ha decidido aplicar un estilo más específico.

🧮 Cómo Funciona la Especificidad
La especificidad se calcula en tres niveles:

A: IDs
B: Clases, atributos y pseudo-clases
C: Elementos y pseudo-elementos
Imaginemos que tienes un selector sin IDs pero con una clase. La puntuación sería:

ID: 0
Clases: 1
Elementos: 0
Por lo tanto, 0, 1, 0. Compara esto con un simple elemento <p>, que tiene una puntuación de 0, 0, 1. ¡Sorpresa! La clase tiene más peso.

📐 Comparando Selectores
Si todos los selectores tienen una puntuación similar, el siguiente nivel de especificidad se evalúa. Por ejemplo:

.text (0, 1, 0)
#text (1, 0, 0)
<p> (0, 0, 1)

🔍 Herramientas Útiles
Utilizando herramientas de desarrollo en el navegador, puedes ver la especificidad de cada selector directamente y entender por qué ciertos estilos están siendo aplicados. Simplemente selecciona el elemento y observa la propiedad de especificidad que se muestra.

⚠️ Errores Comunes
Uno de los errores más comunes es utilizar !important en exceso. Aunque puede parecer una solución rápida, deberías evitarlo siempre que sea posible. ¡Recuerda! La simplicidad y claridad en tu CSS son clave.

🗒 Ejemplo de Uso Correcto
Cuando trabajas con JavaScript y modificaciones dinámicas, a veces necesitarás estilos inline, pero esto debe ser la excepción y no la regla.

<p style="color: orange;">
  Este párrafo es naranja debido a un estilo en línea.
</p>

La especificidad es una de las áreas más complejas y críticas de CSS. A medida que avances, encontrarás metodologías y herramientas que te ayudarán a evitar problemas comunes relacionados con estilos y su aplicación. Recuerda siempre verificar la especificidad cuando algo no funcione como esperabas.
 -->

<!--
El modelo de la caja en CSS es fundamental para comprender cómo se calculan las dimensiones de los elementos en tu página web. A lo largo de esta lección, exploraremos cómo el ancho y alto que specifies no siempre representan lo que realmente ocupan en el espacio.

📏 ¿Qué es el Modelo de la Caja?
El modelo de la caja describe cómo el ancho y la altura de un elemento son calculados. Cuando defines un elemento con 100 píxeles de ancho y alto, puede que este no se limite a esas dimensiones debido al padding y border.

🧩 Ejemplo de Cálculo
Si tienes un elemento con un alto y ancho de 100px, pero con un padding de 10px y un border de 10px, el espacio total será:

Total = ancho + 2 * padding + 2 * border
Total = 100px + 20px = 120px

📐 La Solución: box-sizing
El desafío se presenta cuando una interfaz de usuario pide que el tamaño exacto sea 150 píxeles. Para solucionar esto, utilizamos box-sizing: border-box;. Esta propiedad cambia la forma en que el ancho y la altura son calculados, permitiendo que se ajusten a las especificaciones que deseas sin complicaciones.

📊 Comparación de box-sizing
1. content-box (por defecto)
El ancho se calcula como: contenido + padding + border
2. border-box
El ancho se calcula como el tamaño total especificado, gracias a esta propiedad. Así, si defines que el elemento mide 150px, lo será realmente.

💡 Importancia de box-sizing
Muchos desarrolladores no comprenden completamente por qué box-sizing es crucial hasta que enfrentan problemas en su diseño. Usar box-sizing: border-box; es una práctica común y recomendada, adoptada por muchos frameworks de CSS.

🌐 ¿Por Qué No es el Predeterminado?
La razón principal por la cual los navegadores no aplican box-sizing: border-box; de forma predeterminada es retrocompatibilidad. Cambiar esta propiedad rompería millones de páginas web ya existentes.

Conclusión
Comprender el modelo de la caja y cómo manipular el box-sizing puede ahorrarte muchos problemas en el diseño de tu página.
 -->

<!--
Los elementos en CSS, por defecto, son estáticos. Esto significa que ocupan el lugar donde se definen en el HTML y se apilan uno tras otro. Por ejemplo, si agregas un nuevo div, se posicionará automáticamente justo debajo del anterior:

<section>
  <div class="container">Contenedor 1</div>
  <div class="container">Contenedor 2</div>
</section>

📌 Posicionamiento Estático
El position: static; es el comportamiento predeterminado. Los elementos están fijos en su lugar según el flujo del documento, a menos que especifiques lo contrario con otras propiedades de posición.

💎 Explora Más
Te invitamos a experimentar con las diferentes propiedades de position, como relative, absolute, fixed, y sticky. Cada una ofrece capacidades únicas para organizar y manipular tus elementos en la página.

🌐 Posicionamiento en CSS: Absolute vs Relative
En esta lección aprenderás sobre dos de las propiedades de posición más cruciales de CSS: Absolute y Relative. Conocerlas a fondo te permitirá tener un control total sobre el diseño y el flujo de tus elementos en una página web.

📌 ¿Qué es la posición Absolute?
La posición absoluta permite eliminar un elemento del flujo normal del documento y posicionarlo con coordenadas específicas. Al activar esta propiedad, podrás controlar con precisión dónde se coloca el elemento en la página.

Ejemplo de posición Absolute
Al aplicar position: absolute, el elemento se posiciona en relación con el primer elemento padre que tenga una posición distinta a static. Si no encuentra uno, se posiciona respecto al documento. Veamos un ejemplo.

.container {
  position: relative; /* Esto servirá como referencia para los elementos hijos */
}
.absolute-box {
  position: absolute;
  top: 0; /* 0 píxeles desde la parte superior */
  right: 0; /* 0 píxeles desde la derecha */
}


🚀 ¿Y la posición Relative?
Por otro lado, position: relative permite mover un elemento en relación con su posición original, creando un “punto de referencia” para cualquier hijo con posición absoluta. Esto es especialmente útil cuando deseas posicionar elementos dentro de otro.

Ejemplo de posición Relative
Al aplicar position: relative, te aseguras de que los elementos hijos con posición absoluta se alineen dentro de su contenedor.

🔑 Importancia de los dos tipos de posición
Es fundamental comprender cómo funcionan ambas propiedades:

Absolute: Posiciona elementos sin afectar a los demás. Utiliza coordenadas precisas, pero puede convertirse en un desafío si no tienes un contenedor de referencia adecuado.

Relative: Crea un contexto que permite que los hijos con posición absoluta se alineen correctamente respecto al contenedor.

🎯 Conclusión
Conocer la diferencia entre Absolute y Relative es crucial para un diseño CSS efectivo. Utiliza las propiedades adecuadamente para posicionar tus elementos de forma precisa y optimiza la experiencia del usuario.

El position sticky combina características del position relative y el position fixed. Permite que un elemento se “pegue” a su contenedor mientras se desplaza. Esto significa que se comporta como un elemento relativo, pero se fija a una posición específica cuando se desplaza hacia su límite superior.

🚀 Comparativa entre Position Fixed y Position Sticky

Fixed: El elemento se mantiene fijo en la ventana del navegador y no es afectado por su contenedor.

Sticky: El elemento se adhiere dentro de su contenedor, comportándose según el scroll.

Para que position sticky funcione correctamente, es fundamental que su contenedor tenga un position relative. Esto asegurará que el stickiness se aplique dentro del contexto de ese contenedor.
 -->

<!--
🎨 Entendiendo el Z Index en CSS
En esta lección, nos sumergiremos en el fascinante mundo del Z Index, una propiedad esencial en CSS que determina cómo se apilan los elementos en una página. Aunque las páginas web parecen ser bidimensionales, en realidad, tienen un eje de profundidad, conocido como el eje Z. Este eje es fundamental para comprender cómo los elementos pueden superponerse.

📚 ¿Qué Aprenderás?
Contexto de Apilamiento: Comprenderás el concepto de contexto de apilamiento y cómo se forma, lo que es clave para manipular el Z Index de manera efectiva.

Uso de la Propiedad Z Index: Aprenderás a usar la propiedad Z Index para controlar qué elementos deben estar al frente y cuáles deben estar detrás.

Ejemplos Prácticos: A través de ejemplos prácticos, verás cómo aplicar estos conceptos en situaciones reales y cómo resolver problemas comunes relacionados con la apilación de elementos.

🔍 ¿Qué es el Contexto de Apilamiento?
El contexto de apilamiento se refiere a la forma en que los elementos se apilan unos sobre otros en el eje Z. Este contexto es creado por propiedades como position, opacity, y transform.

Ejemplo de Creación de un Contexto

.element {
  position: relative; /* Crea un nuevo contexto de apilamiento */
  z-index: 1; /* Establece el índice Z */
}

Propiedad Z Index
La propiedad Z Index permite manejar la prioridad de los elementos apilados. Un valor mayor en el Z Index significa que el elemento se mostrará por delante de los que tienen un valor menor.

.box1 {
  position: relative;
  z-index: 1; /* Este estará detrás */
}

.box2 {
  position: relative;
  z-index: 2; /* Este estará delante */
}

🎭 Problemas Comunes con Z Index
A menudo, los desarrolladores se encuentran con problemas relacionados con el Z Index que no funcionan como se espera. Esto generalmente se debe a que no se han creado contextos de apilamiento. Aquí tienes un ejemplo típico de cómo no usar Z Index correctamente:

.box1 {
  z-index: 10; /* Sin posición establecida, no tiene efecto */
}

.box2 {
  z-index: 5; /* Sin relación de apilamiento, este valor no cuenta */
}
 -->

<!--
Flexbox
-------

📏 ¿Qué es Flexbox?
Flexbox es un sistema de diseño en CSS que permite distribuir espacio y alinear elementos de forma más eficiente en comparación con métodos anteriores. Usaremos las propiedades más importantes:

flex-grow: determina cómo crecerán los elementos.
flex-shrink: permite que los elementos se reduzcan.
flex-basis: establece el tamaño base del elemento.

📐 Configuración Inicial
Imaginemos que tenemos un contenedor con varios elementos. Al aplicarle un ancho de 200px, y elementos de 50px, el contenedor podría tener más espacio que el que ocupa el contenido.

.container {
  display: flex;
  width: 200px;
}

.item {
  width: 50px;
}

🔍 Entendiendo las Propiedades
Por defecto, el valor de flex-grow es 0, lo que significa que los elementos no crecerán. Si deseamos que ocupen todo el espacio disponible, debemos ajustar este valor.

Aquí tienes un ejemplo de cómo se vería:

.item {
  flex-grow: 1; /* Permite que los elementos crezcan */
}

🛠 Usando Flexbox para Distribuir Espacio
Podemos hacer que los elementos se ajusten a su contenido o todos tengan el mismo ancho.

Ajuste Automático a Contenido
Si deseamos que los elementos se ajusten automáticamente, podemos utilizar:

.item {
  flex-basis: auto; /* Ajusta según el contenido */
  flex-grow: 1; /* Permite que crezcan */
}

Elementos con Ancho Iguales
Para que todos los elementos tengan el mismo espacio independientemente de su contenido, usamos:

.item {
  flex-basis: 0; /* Base cero para iguales */
  flex-grow: 1; /* Todos pueden crecer */
}
 -->
