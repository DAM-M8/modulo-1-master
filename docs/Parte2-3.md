<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


## 2.3. El editor de Unity


La gran mayoría de los motores de los juegos modernos proporcionan un
editor con el que podemos trabajar visualmente. Unity no es una
excepción, y su potente editor es posiblemente una de las claves detrás
de su éxito.

Por defecto, el editor de Unity se visualiza de la siguiente manera
cuando creamos un nuevo proyecto:

![](images/part2/editor.png)


El editor está compuesto por ***tabs*** (**pestañas**), cada una de las
cuales tiene una función específica. Las pestañas se pueden reordenar
--pulsando el botón izquierdo del ratón sobre las mismas y
arrastrándolas--, ajustar de tamaño o agrupar según nuestras
preferencias. Por defecto, las pestañas que aparecen son las de
Hierarchy, Scene, Game, Inspector, Project y Console, aunque existen
más, que cubriremos a medida que necesitemos opciones más avanzadas.

> La distribución de pestañas de Unity en un momento dado se conoce como
> el ***layout***.

### 2.3.1. La pestaña Hierarchy


La pestaña Hierarchy contiene la lista de GameObjects de una escena.
Una escena se organiza en forma de jerarquía, de ahí el nombre de la
pestaña, de modo que los distintos GameObjects se pueden anidar unos
dentro de otros. Por ejemplo, en la imagen que se muestra a continuación
hemos añadido un cubo a la escena y luego hemos arrastrado con el ratón
el objeto llamado Main Camera al objeto llamado Cube:

![](images/part2/tab_hierarchy.png)

> Para añadir el cubo se ha usado la opción GameObject \> 3D Object \>
> Cube del menú principal de Unity. Esta opción también se puede
> acceder pulsando el botón derecho del ratón sobre la pestaña
> Hierarchy.

El resultado de emparentar dos objetos resulta en que los objetos hijo
se verán afectados siempre de la misma manera que su objeto padre. Así
pues, en el ejemplo, Main Camera (el GameObject hijo) se moverá,
rotará, se eliminará o se escalará siempre que Cube (el GameObject
padre) lo haga. Además de ser útil para sincronizar movimientos entre
objetos, este tipo de jerarquía también nos servirá para organizar
nuestra escena y encontrar nuestros objetos de una manera mucho más
rápida y cómoda.

> Una jerarquía no está limitada en número de hijos por padre ni en
> cuantos niveles de jerarquía hay por escena.

### 2.3.2. La pestaña Scene


La pestaña Scene es el editor visual de la escena con la que estamos
trabajando en Unity. Por ejemplo, después de añadir el cubo, el
resultado es el siguiente:

![](images/part2/tab_scene.png)

Cada uno de los objetos que hayamos añadido en la pestaña Hierarchy nos
aparecerá en la pestaña Scene representado por un símbolo. Además, el
objeto que tengamos seleccionado mostrará más detalles.

> El símbolo con el que se visualiza un objeto en la pestaña Scene se
> denomina **gizmo**. El símbolo utilizado varía según los componentes
> añadidos al GameObject correspondiente.

En la imagen que acabamos de ver, el objeto seleccionado es el Main
Camera, representado con una cámara porque tiene un componente Camera.
En la escena también hay una luz, que podemos ver por el gizmo de un
sol. Finalmente, en este ejemplo, al tener una cámara seleccionada en la
Hierarchy, podemos ver una previsualización (*preview*) de cómo se vería
la escena desde el punto de vista de la cámara en la parte inferior
derecha de la escena.

Existen varios modos de interactuar con los objetos y de navegar dentro
de esta pestaña. Estos modos se pueden cambiar con los botones que
tenemos justo debajo de la barra de menú o con las teclas.

![](images/part2/barra_interaccion.png)

> Podemos cambiar rápidamente de modo con las teclas QWERT del teclado.

> Podemos cambiar rápidamente de modo con las teclas QWERT del teclado.

Cada uno de los modos presenta una funcionalidad única:

-   **Mano:** permite moverse alrededor de la escena.

-   **Traslación:** permite trasladar (mover) el objeto seleccionado.

-   **Rotación:** permite rotar el objeto seleccionado.

-   **Escalado:** permite escalar (cambiar el tamaño) el objeto
    seleccionado.

-   **Rectángulo:** permite cambiar el tamaño del objeto de UI
    seleccionado.

-   **Traslación + Rotación + Escalado:** permite trasladar, rotar y
    escalar el objeto seleccionado.

-   **Herramientas *custom* del editor:** permite acceder a las
    herramientas *custom* del editor (si las hay).


### 2.3.3. La pestaña Game

La pestaña Game se encuentra por defecto detrás de la de Scene. Para
seleccionarla, debemos pulsar sobre la pestaña, de modo que la pantalla
del editor queda reemplazada por otra que nos muestra el resultado que
obtendríamos si ejecutásemos el proyecto. Es decir, es donde realmente
nos tenemos que fijar para comprobar que todo funciona como esperábamos.

![](images/part2/tab_game.png)


Hay una opción en su barra de menú, llamada Stats, que es especialmente
interesante. Cuando está activada, nos muestra información sobre el
rendimiento (*performance*) de nuestra aplicación. En particular, hay
que destacar el número de milisegundos que consume nuestro juego en la
CPU y en el hilo de renderizado. Cuanto menor sea este número, mayor
será el rendimiento del mismo.

![](images/part2/stats.png)

Es importante remarcar que utilizar esta opción solo nos va a dar una
aproximación general del rendimiento real de nuestro juego, puesto que
el propio editor de Unity supone una carga adicional. Si queremos la
mayor fidelidad posible en los resultados, será necesario analizar una
*build* final.

### 2.3.4. La pestaña Inspector

Esta es probablemente la pestaña más importante del editor. Aquí podemos
ver qué contienen los GameObjects seleccionados en la Hierarchy. Veamos
un ejemplo para el objeto llamado Main Camera.

![](images/part2/inspector_camera.png)

En este caso, podemos ver que Main Camera contiene componentes de tipo
Camera y Audio Listener. Además, tiene un componente de tipo Transform,
que contienen absolutamente todos los GameObjects.

> Dentro del componente Transform de un objeto se indica su posición,
> rotación y escala.

Recordemos que, en Unity, un GameObject es cualquier elemento del juego,
sin definir por sí mismo de qué se trata. Puede ser cualquier cosa: una
cámara, un elemento gráfico, un *script*, etc. Para que un objeto se
comporte de la manera deseada, debemos añadirle el componente adecuado.

> En Unity, los componentes de un objeto son los que realmente definen
> cuál es su comportamiento o cómo se va a representar en el juego.

Por ejemplo, si añadimos un componente vacío a nuestra escena, podemos
transformarlo en una luz pulsando en el botón Add Component que
encontramos en la pestaña Inspector y buscando el tipo Light entre la
lista de componentes.

![](images/part2/add_component.png)

> Para crear un objeto vacío se puede usar la opción Create \> Create
> Empty en la pestaña Hierarchy.
>
> Para encontrar rápidamente un componente en la lista, es recomendable
> usar el cuadro de búsqueda asociado.

Será solo de esta manera como el GameObject se comportará como una luz.
Añadiendo componentes adicionales, se pueden asociar diferentes
comportamientos a los GameObjects. Por ejemplo, el objeto de nuestro
ejemplo puede ser también una cámara si le añadimos el componente
adecuado.

Naturalmente, también podemos quitarle componentes a un objeto, pulsando
en la parte superior derecha (el icono con el engranaje) para activar el
siguiente menú:

![](images/part2/inspector_light1.png)

Una vez se ha añadido un componente, es posible configurar su
comportamiento en la misma pestaña Inspector:

![](images/part2/inspector_light2.png)

### 2.3.5. La pestaña Project

Esta pestaña muestra todos los ficheros que tenemos dentro de nuestro
proyecto.

> Se denomina ***asset*** a cualquier fichero importado que sea
> necesario para la ejecución del proyecto. Por ejemplo: imágenes,
> *scripts* (fragmentos de código fuente), texturas, vídeos, modelos 3D,
> animaciones, etc.
>
> Podemos encontrar una gran cantidad de contenido libre y gratuito en
> webs como la siguiente: http://opengameart.org.

El aspecto inicial de la pestaña es el siguiente. En este caso, aún no
tenemos ningún archivo importado. Lo único que contiene el proyecto es
una escena de ejemplo que incluye automáticamente Unity.

![](images/part2/tab_project.png)

Supongamos que nos descargamos una imagen de Internet que deseamos
incorporar a nuestro proyecto. Para ello, podemos importarla de dos
maneras:

-   Copiando el fichero en la carpeta Assets del proyecto de Unity en
    el sistema de ficheros de nuestro ordenador.

-   Arrastrando el fichero directamente desde el explorador de archivos
    del ordenador al interior de la pestaña Project.

Una manera rápida de encontrar la carpeta Assets del ordenador es
haciendo clic derecho en la pestaña Project y seleccionando Show in
Explorer (o Reveal in Finder en Mac OS).

### 2.3.6. La pestaña Console

Esta pestaña nos mostrará todos los avisos y errores que ocurran en
nuestro proyecto. También permite mostrar mensajes de depuración
generados directamente desde el código de nuestro juego.

> Podemos encontrar más información sobre el uso de la pestaña Console [aquí](https://docs.unity3d.com/Manual/Console.html).

### 2.3.7. Modos de ejecución en Unity

Los dos modos de funcionamiento de Unity son:

-   El **modo edición** (***editor mode***). Cuando estamos en este
    modo, el motor de juego está parado y tanto su código como muchas de
    sus herramientas integradas (como la física, sistemas de partículas,
    etc.) están detenidas. El modo edición sirve para que vayamos
    construyendo la escena sin tener distracciones, como objetos
    moviéndose o desapareciendo. En esencia, en este modo trabajamos con
    un editor de niveles.

-   El **modo ejecución** (***play mode***). En este modo, en cambio,
    Unity está simulando que un usuario inicia la aplicación que hemos
    desarrollado. Todas las herramientas del motor se activarán y la
    experiencia que tengamos viendo la pestaña Game será muy similar a
    la que tendríamos al iniciar la aplicación real.

> En modo ejecución es posible modificar una escena del juego y sus
> elementos mediante el editor. Sin embargo, todo lo que se modifique en
> este modo se perderá una vez salgamos de él. Por ejemplo, si añadimos
> un objeto *A a la escena y borramos un objeto B existente, al volver
> al modo edición, el objeto A desaparecerá y el objeto B volverá a
> existir. En caso de querer mantener esas operaciones, hay que
> llevarlas a cabo siempre en el modo* edición.

Para entrar en modo ejecución, simplemente hay que pulsar el botón Play
en el grupo de botones situado en la parte superior central del editor,
justo debajo del menú. Para salir, volvemos a pulsar Play, con lo que
volveremos a estar en modo edición. El botón de pausa congela la
aplicación momentáneamente; lo podemos usar para examinar con calma una
escena. El tercer botón sirve para ir *frame* a *frame*, de modo que
podemos ver los cambios con mucho más detalle.

![](images/part2/botones_control.png)






--> <a href="Parte2-4.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)


## 2.3. L'editor de Unity


La gran majoria dels motors dels jocs moderns proporcionen un editor amb
el qual podem treballar visualment. Unity no n'és l'excepció, i el seu
editor potent és possiblement una de les claus del seu èxit.

Per defecte, l\'editor de Unity es visualitza de la següent manera quan
creem un projecte nou:

![](images/part2/editor.png)

L\'editor està compost per ***tabs*** (**pestanyes**), cadascuna de les
quals té una funció específica. Les pestanyes es poden reordenar
--prement-hi el botó esquerre del ratolí i arrossegant-les--, ajustar de
grandària o agrupar segons les nostres preferències. Per defecte, les
pestanyes que apareixen són les de Hierarchy, Scene, Game, Inspector,
Project i Console, encara que n'hi ha més, que cobrirem a mesura que
necessitem opcions més avançades.

> La distribució de pestanyes de Unity en un moment donat es coneix com
> el ***layout***.

### 2.3.1. La pestanya Hierarchy

La pestanya Hierarchy conté la llista de GameObjects d\'una escena. Una
escena s\'organitza en forma de jerarquia, d\'aquí el nom de la
pestanya, de manera que els diferents GameObjects es poden niar uns dins
dels altres. Per exemple, a la imatge que es mostra a continuació hem
afegit un cub a l\'escena i després hem arrossegat amb el ratolí
l\'objecte anomenat Main Camera a l\'objecte anomenat Cube:

![](images/part2/tab_hierarchy.png)

> Per afegir el cub s\'ha usat l\'opció GameObject \> 3D Object \> Cube
> del menú principal de Unity. A aquesta opció també s'hi pot accedir
> prement el botó dret del ratolí sobre la pestanya Hierarchy.

El resultat d\'emparentar dos objectes és que els objectes fill es
veuran afectats sempre de la mateixa manera que l'objecte pare. Així
doncs, en l\'exemple, Main Camera (el GameObject fill) es mourà, girarà,
s\'eliminarà o s\'escalarà sempre que Cube (el GameObject pare) ho faci.
A més de ser útil per sincronitzar moviments entre objectes, aquest
tipus de jerarquia també ens servirà per organitzar la nostra escena i
trobar els nostres objectes d\'una manera molt més ràpida i còmoda.

> Una jerarquia no està limitada en nombre de fills per pare ni en
> quants nivells de jerarquia hi ha per escena.


### 2.3.2. La pestanya Scene

La pestanya Scene és l\'editor visual de l\'escena que estem treballant
a Unity. Per exemple, després d\'afegir el cub, el resultat és el
següent:

![](images/part2/tab_scene.png)


Cadascun dels objectes que hàgim afegit en la pestanya Hierarchy ens
apareixerà a la pestanya Scene representat amb un símbol. A més,
l\'objecte que tinguem seleccionat mostrarà més detalls.

> El símbol amb el qual es visualitza un objecte a la pestanya Scene
> s'anomena **gizmo**. El símbol utilitzat varia segons els components
> afegits al GameObject corresponent.

A la imatge que acabem de veure, l\'objecte seleccionat és el Main
Camera, representat amb una càmera perquè té un component Camera. A
l\'escena també hi ha una llum, que podem veure pel gizmo d\'un sol.
Finalment, en aquest exemple, si tenim una càmera seleccionada a la
Hierarchy, podem veure una previsualització (*preview*) de com es veuria
l\'escena des del punt de vista de la càmera a la part inferior dreta de
l\'escena.

Hi ha diverses maneres d\'interactuar amb els objectes i de navegar dins
d\'aquesta pestanya. Aquestes maneres es poden canviar amb els botons
que tenim just a sota la barra de menú o amb les tecles.

![](images/part2/barra_interaccion.png)


> Podem canviar ràpidament de mode amb les tecles QWERT del teclat.
>
> Podem canviar ràpidament de mode amb les tecles QWERT del teclat.

Cadascun dels modes presenta una funcionalitat única:

-   **Mà:** permet moure\'s per l\'escena.

-   **Translació:** permet traslladar (moure) l\'objecte seleccionat.

-   **Rotació:** permet girar l\'objecte seleccionat.

-   **Escalat:** permet escalar l\'objecte seleccionat (canviar-li la
    grandària).

-   **Rectangle:** permet canviar la grandària de l\'objecte d\'UI
    seleccionat.

-   **Translació + Rotació + Escalat:** permet traslladar, girar i
    escalar l\'objecte seleccionat.

-   **Eines *custom* de l\'editor:** permet accedir a les eines *custom*
    de l\'editor (si n\'hi ha).

### 2.3.3. La pestanya Game

La pestanya Game és, per defecte, darrere de la de Scene. Per
seleccionar-la, hem de prémer sobre la pestanya, de manera que la
pantalla de l\'editor quedi reemplaçada per una altra que ens mostra el
resultat que obtindríem si executéssim el projecte. És a dir, és on
realment ens hem de fixar per comprovar que tot funciona com esperàvem.

![](images/part2/tab_game.png)


Hi ha una opció a la barra de menú, anomenada Stats, que és especialment
interessant. Quan està activada, ens mostra informació sobre el
rendiment (*performance*) de la nostra aplicació. En particular, cal
destacar el nombre de mil·lisegons que consumeix el nostre joc a la CPU
i al fil de renderitzat. Com més petit sigui aquest nombre, més gran
serà el rendiment.

![](images/part2/stats.png)


És important remarcar que utilitzar aquesta opció només ens donarà una
aproximació general del rendiment real del nostre joc, ja que el propi
editor de Unity suposa una càrrega addicional. Si volem la major
fidelitat possible en els resultats, serà necessari analitzar una
*build* final.

### 2.3.4. La pestanya Inspector

Aquesta és probablement la pestanya més important de l\'editor. Aquí
podem veure què contenen els GameObjects seleccionats a la Hierarchy.
Vegem un exemple per a l\'objecte anomenat Main Camera.

![](images/part2/inspector_camera.png)

En aquest cas, podem veure que Main Camera conté components de tipus
Camera i Àudio Listener. A més, té un component de tipus Transform, que
contenen absolutament tots els GameObjects.

> Dins del component Transform d\'un objecte s\'indica la posició, la
> rotació i l'escala que té.

Recordem que, a Unity, un GameObject és qualsevol element del joc, sense
definir per si mateix de què es tracta. Pot ser qualsevol cosa: una
càmera, un element gràfic, un *script*, etc. Perquè un objecte es
comporti de la manera desitjada, hem d\'afegir-li el component adequat.

> A Unity, els components d\'un objecte són els que realment defineixen
> quin n'és el comportament o com es representarà en el joc.

Per exemple, si afegim un component buit a la nostra escena, podem
transformar-lo en una llum prement el botó Add Component que hi ha a la
pestanya Inspector i buscant el tipus Light entre la llista de
components.

![](images/part2/add_component.png)


> Per crear un objecte buit es pot usar l\'opció Create \> Create Empty
> a la pestanya Hierarchy.
>
> Per trobar ràpidament un component a la llista, és recomanable usar el
> quadre de cerca associat.

Només així el GameObject es comportarà com una llum. Si afegim
components addicionals, podrem associar diferents comportaments als
GameObjects. Per exemple, l\'objecte del nostre exemple pot ser també
una càmera si li afegim el component adequat.

Naturalment, també podem treure-li components a un objecte, prement a la
part superior dreta (la icona amb l\'engranatge) per activar el següent
menú:

![](images/part2/inspector_light1.png)


Una vegada s\'ha afegit un component, és possible configurar-ne el
comportament a la mateixa pestanya Inspector:

![](images/part2/inspector_light2.png)


### 2.3.5. La pestanya Project

Aquesta pestanya mostra tots els fitxers que tenim dins del nostre
projecte.

> S'anomena ***asset*** qualsevol fitxer importat que sigui necessari
> per a l\'execució del projecte. Per exemple: imatges, *scripts*
> (fragments de codi font), textures, vídeos, models 3D, animacions,
> etc.
>
> Podem trobar una gran quantitat de contingut lliure i gratuït en webs
> com la següent: http://opengameart.org.

L\'aspecte inicial de la pestanya és el següent. En aquest cas, encara
no tenim cap arxiu importat. L\'única cosa que conté el projecte és una
escena d\'exemple que inclou automàticament Unity.

![](images/part2/tab_project.png)


Suposem que ens descarreguem una imatge d\'Internet que desitgem
incorporar al nostre projecte. Per a fer-ho, podem importar-la de dues
maneres:

-   Copiant el fitxer a la carpeta Assets del projecte de Unity en el
    sistema de fitxers del nostre ordinador.

-   Arrossegant el fitxer directament des de l\'explorador d\'arxius de
    l\'ordinador a l\'interior de la pestanya Project.

Una manera ràpida de trobar la carpeta Assets de l\'ordinador és fent
clic al botó dret a la pestanya Project i seleccionant Show in Explorer
(o Reveal in Finder a Mac US).

### 2.3.6. La pestanya Console

Aquesta pestanya ens mostrarà tots els avisos i errors que ocorrin en el
nostre projecte. També permet mostrar missatges de depuració generats
directament des del codi del nostre joc.

> Podem trobar més informació sobre l\'ús de la pestanya Console [aquí](https://docs.unity3d.com/Manual/Console.html).

### 2.3.7. Modes d\'execució a Unity

Els dos modes de funcionament de Unity són:

-   El **mode edició** (***editor mode***). Quan estem en aquest mode,
    el motor de joc està parat i tant el seu codi com moltes de les
    seves eines integrades (com la física, sistemes de partícules, etc.)
    estan detingudes. El mode edició serveix perquè anem construint
    l\'escena sense tenir distraccions, com per exemple objectes
    movent-se o desapareixent. En essència, en aquest mode treballem amb
    un editor de nivells.

-   El **mode execució** (***play mode***). En aquest mode, en canvi,
    Unity està simulant que un usuari inicia l\'aplicació que hem
    desenvolupat. Totes les eines del motor s\'activaran i
    l\'experiència que tinguem veient la pestanya Game serà molt similar
    a la qual tindríem en iniciar l\'aplicació real.

> En mode execució és possible modificar una escena del joc i els seus
> elements mitjançant l\'editor. No obstant això, tot el que es
> modifiqui en aquest mode es perdrà quan en sortim. Per exemple, si
> afegim un objecte *A a l\'escena i esborrem un objecte B existent,
> quan tornem al mode edició, l\'objecte A desapareixerà i l\'objecte B
> tornarà a existir. En cas de voler mantenir aquestes operacions, cal
> dur-les a terme sempre en el mode* edició.

Per entrar en mode execució, simplement cal prémer el botó Play en el
grup de botons situat en la part superior central de l\'editor, just a
sota del menú. Per sortir, tornem a prémer Play, i tornarem a estar en
mode edició. El botó de pausa congela l\'aplicació momentàniament; el
podem usar per examinar amb calma una escena. El tercer botó serveix per
anar *frame* a *frame*, de manera que podem veure els canvis amb molt
més detall.

![](images/part2/botones_control.png)

--> <a href="Parte2-4.md">Pàgina següent</a>
