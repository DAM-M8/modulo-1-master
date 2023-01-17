<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


# 4.4. La pantalla de fin de juego

Hay varias opciones para comunicarle al jugador que el juego ha
terminado. Diferentes juegos nos han demostrado que puede haber una gran
diversidad en este aspecto, desde dejarnos rebobinar en el tiempo hasta
pantallas específicas relacionadas con la muerte. Sin embargo, la
mayoría de los juegos optan por una solución más sencilla y menos
creativa, aunque conocida por cualquier jugador con un mínimo de
experiencia. Esta solución consiste en mostrar un mensaje que le indica
al jugador que la partida se ha acabado y le muestra varias opciones,
que pueden abarcar desde repetir el nivel hasta volver al menú
principal.

En nuestro caso, ya que tenemos una pantalla inicial, podemos mostrar un
simple mensaje y dar la opción de reiniciar la partida o de volver a la
pantalla principal. Vamos a crear una UI sencilla, con dos botones, como
podéis ver en la figura siguiente. El botón de la izquierda queremos que
nos lleve a la pantalla inicial, mientras que el botón de la derecha
reinicia directamente la partida.


![](images/part4/pause.png)

| **Reto 9** |
| ---    |
| Cread esta pantalla, de manera similar a cuando elaborasteis la pantalla de inicio, y haced que GameplayManager la muestre al acabar el juego. |

Aprovechando que tenemos una pantalla que permite volver al menú de
inicio o reiniciar una partida, podemos incluir una funcionalidad de
pausa en el juego, de manera que cuando se pulsa la tecla *Esc*,
aparezca esta pantalla. Así, en cualquier momento podemos salir de la
partida de manera limpia.

| **Reto 10** |
| ---    |
| Añadid la opción de cancelar la partida con la tecla Esc. |

Ahora, tan solo tenemos que asociar los eventos OnClick, el del botón
MainMenuButton al método LoadMainMenu, y el del botón RestartGameButton
a RestartGame. También tenemos que añadir una variable pública de tipo
GameObject en el *script* GameplayManager, que asociaremos en el editor
a la UI que acabamos de crear. Finalmente, esta UI la debemos posicionar
en el centro de la pantalla y desactivarla, para que el jugador la vea
cuando se activa, pero que esté invisible por defecto.

Como detalle, podemos observar que esta UI es perfectamente válida para
cuando pausamos el juego. De esta manera, hemos escogido la tecla Esc
para enseñarla, como se puede ver en el método Update.


--> <a href="Parte4-5.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)

# 4.4. La pantalla de final del joc

Hi ha diverses opcions per comunicar-li al jugador que el joc ha acabat.
Diferents jocs ens han demostrat que pot haver-hi una gran diversitat en
aquest aspecte, des de deixar-nos rebobinar en el temps fins a pantalles
específiques relacionades amb la mort. No obstant això, la majoria dels
jocs opten per una solució més senzilla i menys creativa, encara que
coneguda per qualsevol jugador amb un mínim d\'experiència. Aquesta
solució consisteix a mostrar un missatge que indica al jugador que la
partida s\'ha acabat i li mostra diverses opcions, que poden anar des de
repetir el nivell fins a tornar al menú principal.

En el nostre cas, ja que tenim una pantalla inicial, podem mostrar un
simple missatge i donar l\'opció de reiniciar la partida o de tornar a
la pantalla principal. Crearem una UI senzilla, amb dos botons, com
podeu veure a la figura següent. El botó de l\'esquerra volem que ens
porti a la pantalla inicial, mentre que el botó de la dreta reinicia
directament la partida.

![](images/part4/pause.png)

| **Repte 9** |
| ---    |
| Creeu aquesta pantalla, de manera similar a quan vau elaborar la pantalla d\'inici, i feu que GameplayManager la mostri en acabar el joc. |


Aprofitant que tenim una pantalla que permet tornar al menú d\'inici o
reiniciar una partida, podem incloure una funcionalitat de pausa al joc,
de manera que quan es premi la tecla *Esc*, aparegui aquesta pantalla.
Així, en qualsevol moment podem sortir de la partida de manera neta.

| **Repte 10** |
| ---    |
| Afegiu l\'opció de cancel·lar la partida amb la tecla Esc. |

Ara, només hem d\'associar els esdeveniments OnClick, el del botó
MainMenuButton al mètode LoadMainMenu, i el del botó RestartGameButton a
RestartGame. També hem d\'afegir una variable pública de tipus
GameObject a l'*script* GameplayManager, que associarem a l\'editor a la
UI que acabem de crear. Finalment, aquesta UI l\'hem de posicionar al
centre de la pantalla i desactivar-la, perquè el jugador la vegi quan
s\'activa, però que estigui invisible per defecte.

Com a detall, podem observar que aquesta UI és perfectament vàlida quan
pausem el joc. D\'aquesta manera, hem escollit la tecla Esc per
ensenyar-la, com es pot veure en el mètode Update.


--> <a href="Parte4-5.md">Pàgina següent</a>
