<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


# 4.1. Flujo del juego

Antes de empezar a desarrollar el proyecto propiamente dicho, vamos a
analizar cuál será el flujo del juego para así tener claro qué
herramientas necesitaremos.

La idea es crear un nivel de nuestro juego, pero diseñando nuestro
proyecto de manera que se pueda expandir fácilmente en un futuro. Muchos
juegos que tienen distintos niveles suelen tener una pantalla principal
en la que le preguntan al jugador si quiere ir a un nivel u otro, o si
quiere cargar una partida anterior. Como vamos a tener un solo nivel,
una pantalla de este tipo no es estrictamente necesaria, pero puede ser
muy útil incluirla para luego poder expandir el juego a más niveles.

> Al crear un juego, se recomienda empezar por la generación del
> recorrido básico entre escenas (pantalla de inicio, de juego, de final
> de partida, de configuración, etc.).

Esta pantalla de inicio de momento solo necesita contener un par de
botones, uno para llevarnos a la partida y otro para salir del juego. La
pantalla de la partida contendrá básicamente elementos de UI, ya que es
una aventura de texto. Cuando el jugador acabe esta pantalla, debemos
enseñarle algún mensaje para que quede claro que ha progresado en el
juego o, en este caso, que lo ha terminado. Si tuviésemos más niveles,
podríamos añadir opciones de guardar la partida o de saltar a otro
nivel. En cambio, con solo un nivel de juego, este mensaje puede parecer
irrelevante. Sin embargo, por el mismo motivo que hemos mencionado
anteriormente, es mejor añadir este elemento para poder ampliar el juego
más adelante.

De esta manera, vemos que necesitaremos tres partes, la pantalla
inicial, la pantalla del juego y la pantalla de final. Vamos a explicar
las herramientas fundamentales para desarrollar todas ellas, empezando
por el UI.

--> <a href="Parte4-2.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)

# 4.1. Flux del joc


Abans de començar a desenvolupar el projecte pròpiament dit, analitzarem
quin serà el flux del joc per així tenir clar quines eines necessitarem.

La idea és crear un nivell del nostre joc, però dissenyant el nostre
projecte de manera que es pugui expandir fàcilment en un futur. Molts
jocs que tenen diferents nivells solen tenir una pantalla principal a la
qual li pregunten al jugador si vol anar a un nivell o un altre, o si
vol carregar una partida anterior. Com que tindrem un sol nivell, una
pantalla d\'aquest tipus no és estrictament necessària, però pot ser
molt útil incloure-la per després poder expandir el joc a més nivells.

> Quan es crea un joc, es recomana començar per la generació del
> recorregut bàsic entre escenes (pantalla d\'inici, de joc, de final de
> partida, de configuració, etc.).

Aquesta pantalla d\'inici de moment només necessita contenir un parell
de botons, un per portar-nos a la partida i un altre per sortir del joc.
La pantalla de la partida contindrà bàsicament elements d\'UI, ja que és
una aventura de text. Quan el jugador acabi aquesta pantalla, hem
d\'ensenyar-li algun missatge perquè quedi clar que ha progressat en el
joc o, en aquest cas, que l'ha acabat. Si tinguéssim més nivells,
podríem afegir opcions de guardar la partida o de saltar a un altre
nivell. En canvi, amb només un nivell de joc, aquest missatge pot
semblar irrellevant. No obstant això, pel mateix motiu que hem esmentat
anteriorment, és millor afegir aquest element per poder ampliar el joc
més endavant.

D\'aquesta manera, veiem que necessitarem tres parts: la pantalla
inicial, la pantalla del joc i la pantalla de final. Explicarem les
eines fonamentals per a desenvolupar-les totes, començant per la UI.


--> <a href="Parte4-2.md">Pàgina següent</a>
