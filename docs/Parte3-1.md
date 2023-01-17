<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


# 3.1. Flujo de ejecución


En la mayoría de los motores modernos, el flujo de ejecución es muy
similar. Esto se debe a que la estructura de ejecución de cualquier
juego es esencialmente idéntica a la del resto. Un videojuego es,
generalmente, una aplicación altamente interactiva, con muchos elementos
que deben actuar de manera independiente en modo concurrente.
Básicamente, un juego se compone de un tiempo de inicialización (la
carga inicial del mismo) seguido por un bucle principal en el que, por
cada iteración del mismo, se genera una imagen o ***frame*** que
describe el estado del juego en ese momento. Durante cada *frame*, cada
objeto puede ejecutar código que actualice su estado.

> Cada iteración del bucle principal de juego se corresponde con una
> imagen estática (***frame***) generada como resultado.

Dependiendo del tipo de juego, el bucle principal puede requerir de una
respuesta más o menos inmediata. Por ejemplo, no es lo mismo un FPS que
un juego de cartas.

> Si deseamos 60 FPS en nuestro juego, hemos de garantizar que toda la
> lógica del mismo se ejecute en no más de 16 milisegundos por *frame*.

Es importante tener en cuenta que los *scripts* en sí mismos, como
*assets* dentro de nuestro proyecto, no se ejecutarán a menos que se
asignen como componente a algún GameObject en la escena del juego.
Unity solo ejecuta los métodos de scripts asociados a un GameObject de
la escena en curso. Esto lo debemos hacer desde el editor, seleccionando
un GameObject en la pestaña Scene. Entonces, desde el Inspector debemos
pulsar el botón Add Component y seleccionar un script de C\#.

--> <a href="Parte3-2.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)

# 3.1. Flux d'execució


En la majoria dels motors moderns, el flux d\'execució és molt similar.
Això es deu al fet que l\'estructura d\'execució de qualsevol joc és
essencialment idèntica a la de la resta. Un videojoc és, generalment,
una aplicació altament interactiva, amb molts elements que han d\'actuar
de manera independent en mode concurrent. Bàsicament, un joc es compon
d\'un temps d\'inicialització (la càrrega inicial del joc) seguit per un
bucle principal en el qual, per cada iteració, es genera una imatge o
***frame*** que descriu l\'estat del joc en aquest moment. Durant cada
*frame*, cada objecte pot executar codi que n'actualitzi l'estat.

> Cada iteració del bucle principal de joc es correspon amb una imatge
> estàtica (***frame***) generada com a resultat.

Depenent del tipus de joc, el bucle principal pot demanar resposta més o
menys immediata. Per exemple, no és el mateix un FPS que un joc de
cartes.

> Si desitgem 60 FPS en el nostre joc, hem de garantir que tota la
> lògica del joc s\'executi en no més de 16 mil·lisegons per *frame*.

És important tenir en compte que els *scripts* en si mateixos, com a
*assets* dins del nostre projecte, no s\'executaran tret que s\'assignin
com a component a algun GameObject a l\'escena del joc. Unity només
executa els mètodes de *scripts* associats a un GameObject de l\'escena
en curs. Això ho hem de fer des de l\'editor, seleccionant un GameObject
a la pestanya Scene. Llavors, des de l\'Inspector hem de prémer el botó
Add Component i seleccionar un script de C\#.

--> <a href="Parte3-2.md">Pàgina següent</a>
