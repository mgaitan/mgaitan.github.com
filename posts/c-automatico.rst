Más por costumbre que utilidad solemos poner la antigüedad de un sitio
web al pie de página, asociado al símbolo ©, o (cc) si usamos `Creative
Commons <http://es.wikipedia.org/wiki/Creative_Commons>`_.

En el 2007 hicimos el sitio, y en este 2009 todavía muestra.

    © 2007

¡Muy feo! Aunque no hayamos actualizado el sitio desde entonces, nuestro
deber, como buenos mentirosos, es lograr que el visitante no se entere.

Así que podemos hacer que el año, o el período **Año inicio - Año
actual** se actualice automáticamente.

Muy simple:

::

    © <BOUCLE_yearbegin(ARTICLES){par date}{0,1}>
        #SET{year, #DATE|annee} #GET{year}
      </BOUCLE_yearbegin>
    [(#GET{year}|=={#DATE|annee}|?{'' , - #DATE|annee} )]   


Explicación
~~~~~~~~~~~

- Por convención, asumimos que el año de inicio del sitio es el año del 
  primer artículo publicado, lo cual a mi me suena bastante lógico. 
- Un bucle recupera esta información, la muestra y a la vez la 
  guarda en una variable spip ``#SET{year, #DATE|annee}``. 
- Fuera del bucle comparamos el año ya mostrado con el actual, 
  obtenida de la baliza ``#DATE`` sin contexto. Si son iguales, 
  no se muestra nada más (para que no quede algo como 
  **© 2009 - 2009**, que quedaría bien feo). 
  Pero si son distintos, se muestra el año actual 

El resultado, será:

    © 2007 - 2009

Y si la lógica o el reloj del servidor no fallan, en cada año nuevo se 
incrementará el año final del período sin que toquemos una línea de código. 
