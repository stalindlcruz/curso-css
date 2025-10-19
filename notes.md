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
