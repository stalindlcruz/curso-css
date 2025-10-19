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
