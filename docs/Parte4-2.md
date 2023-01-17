<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


## 4.2. Creación de la interfaz de usuario básica

Una interfaz de usuario intuitiva e informativa es esencial para que el
usuario sepa cómo manejarse dentro del juego. Una gran mayoría de juegos
empiezan con un menú principal desde donde se pueden comenzar partidas
nuevas o continuar partidas existentes. Si bien hay juegos que han
explorado maneras más originales de cumplir esta función, esta es una
fórmula clásica y probada que sabemos que no va a fallar. Empezaremos,
pues, por esta pantalla.

En primer lugar, crearemos un nuevo proyecto de Unity, recordando
seleccionar el *template* 2D. Una vez creado el proyecto,
seleccionaremos la pestaña Game y la ubicaremos, arrastrándola, a la
derecha de la pestaña Scene, para trabajar más cómodamente. A
continuación, añadiremos un botón mediante la opción de menú GameObject
\> UI \> Button.

> En el menú GameObject se agrupan distintos tipos de objetos. Entre
> ellos, UI para los de interfaz de usuario.

El resultado debería ser muy parecido a la siguiente figura, que será
nuestro punto de partida:

![](images/part4/button.png)

### 4.2.1. Elementos de UI en Unity

Al añadir el botón, se han creado varios GameObjects en el apartado de
Hierarchy. Uno de ellos lleva por nombre EventSystem. Si lo
seleccionamos, veremos en el Inspector que contiene dos componentes: un
Event System y un Standalone Input Module.

Por una parte, el componente Event System permite recibir la interacción
del usuario, y simplemente necesitamos que exista uno en la escena para
poder llevar a cabo esta función. Por otra parte, el componente
Standalone Input Module se encarga de hacer la traducción de las
acciones a eventos. Por ejemplo, en este componente podemos seleccionar
cuál es el botón de cancelar una acción o cómo se llaman los ejes
verticales y horizontales. En general, si no estamos experimentando con
controles específicos para nuestra aplicación, los valores por defecto
serán adecuados para la mayoría de las situaciones habituales.

Otro GameObject que se ha creado en la Hierarchy es el llamado Canvas.
Si lo seleccionamos y observamos en el Inspector, lo primero que nos
llamará la atención es que no tiene un componente Transform, sino uno
llamado Rect Transform. En realidad, se trata de un caso específico de
Transform que usan los elementos de UI en Unity. Internamente funciona
igual que un Transform, pero nos proporciona una manera más cómoda de
interacción para el diseño de nuestra UI. Los siguientes tres
*components* en este GameObject son Canvas, Canvas Scaler y Graphic
Raycaster. El funcionamiento exacto de estos tres *components* es
complejo, pero se puede resumir diciendo que nos permiten definir un
área donde podemos añadir elementos de UI, y que se encargan de calcular
a qué elementos afecta la interacción del usuario. Por ahora, esto es
suficiente.

> Todos los elementos de UI han de ser nodos hijo del *Canvas*.

Finalmente, está el propio botón, el objeto Button, que ha aparecido
como elemento hijo de Canvas. A su vez, ha aparecido un objeto Text como
hijo de Button. Los nombres son bastante autoexplicativos.

> Este GameObject representa un texto en una UI. Como hijo de un botón,
> representa el texto que contiene.

Si observamos Button en el Inspector, vemos que tiene tres componentes:
Canvas Renderer, Image y Button. Canvas Renderer es el componente que le
indica a Unity que hay elementos visuales de una UI (por ejemplo, texto,
una imagen, etc.) y, por lo tanto, hay que añadirlo para que se vean por
pantalla. Image permite especificar la imagen que se mostrará en nuestra
UI, mientras que Button es únicamente una manera de indicarle a Unity
que este GameObject tiene una interacción de botón, pero no se encarga
de mostrar nada por pantalla.

> Cualquier GameObject con un componente Button se comporta como un
> botón, respondiendo a la entrada del usuario.

Así pues, como vemos, para programar UI en Unity reutilizamos y
combinamos muchos componentes sencillos por medio del editor, cada uno
con una funcionalidad muy concreta, de modo que se van creando
estructuras más complejas, siguiendo la filosofía de la simplicidad.

### 4.2.2. La pantalla inicial


Es el momento de empezar a trabajar en la pantalla de inicio del juego.
En primer lugar, duplicamos el botón y renombramos ambos botones con los
nombres NewGame y Exit. A continuación, cambiamos el texto de cada
botón por los textos correspondientes, "Nueva partida" y "Salir". Para
ello, editamos su componente Text.

> Para duplicar un GameObject, se puede hacer cortar y pegar como en la
> mayoría de los editores.
>
> El nombre de un GameObject se cambia desde el Inspector.

Finalmente, situamos los botones centrados y separados de manera que no
se tapen el uno al otro. Podemos arrastrarlos visualmente mediante el
editor o asignar unas coordenadas concretas en el componente Transform
de cada uno de ellos:

-   **NewGame:** Pos X = 0, Pos Y = 30, Pos Z = 0

-   **Exit:** Pos X = 0, Pos Y = -30, Pos Z = 0

El resultado de estas operaciones es el siguiente:

![](images/part4/main_menu.png)

En estos momentos, si entramos en modo ejecución (pulsando el botón
Play), veremos que los botones se muestran correctamente y que se
pueden pulsar, aunque hacerlo no tiene ningún efecto asociado todavía.

### 4.2.3. *Scripting* asociado a la UI

Para que nuestra UI lleve a cabo acciones concretas, será necesario
asociar a nuestros objetos de UI *scripts* que implementen esas
acciones. Empezaremos creando el *script* que responderá a la pulsación
del botón *Exit* y que simplemente debe cerrar la aplicación.

> Para crear un *script*, debemos pulsar el botón derecho del ratón
> sobre el apartado de *Assets* (pestaña *Project*) en el editor y
> seleccionar Create \> C\# Script.

| **Reto 1** |
| ---    |
| Cread un *script* llamado ExitGame con un único método llamado Exit que cuando sea llamado provoque que se muestre por consola el mensaje "Saliendo del juego...".

Una vez creado el *script*, lo añadiremos como componente al botón
Exit, simplemente arrastrándolo sobre el Inspector (o,
alternativamente, haciendo clic sobre el botón Add Component y
eligiendo el componente manualmente). Con esto, el *script* pasa a
formar parte de este objeto.

> Los *scripts* se asocian, generalmente, como componentes de los
> objetos del juego.

Ahora es necesario asociarlo a la acción propiamente de pulsar el botón
Exit. Para asociar código a la acción de pulsar un botón se debe asignar
vía un *listener*. Esto se lleva a cabo con el componente Button del
botón. En la parte inferior del Inspector aparece un recuadro donde se
listan los *listeners* del evento OnClick.

> Un ***listener*** es el encargado de escuchar y controlar eventos.

Para añadir un *listener* se debe pulsar el símbolo *+; entonces*,
aparece un apartado donde se puede indicar el *listener*, inicializado a None (Object) (ninguno). Sobre este cuadro se debe arrastrar desde la
Hierarchy el objeto que posee el código a ejecutar. En nuestro caso,
el objeto que contiene el *script*, que es el propio botón Exit. Una
vez arrastrado, es posible seleccionar en la caja desplegable contigua
el método que se ha de ejecutar. Para ello, primero se debe buscar el
componente adecuado (en este caso, nuestro *script* GameExit), y luego
el método, tal y como muestra la siguiente imagen:

![](images/part4/exit_game.png)

Como podemos comprobar, Unity reconoce los métodos que contienen los
*scripts*, siempre que sean públicos y tengan una firma compatible con
el evento (que tengan los mismos parámetros y que devuelvan *void*). En
concreto, lo que hace Unity es enumerar los componentes del objeto que
se seleccione y listar todas las funciones compatibles. Gracias a esta
funcionalidad, podemos definir comportamientos de manera visual con el
editor.

Para comprobar que el proceso funciona correctamente, podemos entrar en
modo ejecución y pulsar el botón Exit. Una vez hecho esto, podemos
actualizar el código para que realmente provoque la salida del juego en
lugar de mostrar únicamente un mensaje en la consola.

| **Reto 2** |
| ---    |
|  Modificad el *script* que realmente detendría el juego al pulsar el botón Exit. Para esta tarea, estudiad la documentación de la clase Application.

El motivo por el que hemos llevado a cabo esta tarea en dos pasos es que
la llamada al método que sale de la aplicación no tiene efecto dentro
del editor de Unity. Por lo tanto, no es posible probar realmente su
funcionamiento en modo ejecución.

Llega el momento a hacer la funcionalidad del otro botón, el de
*NewGame*. Antes, sin embargo, será necesario preparar el proyecto para
que exista una pantalla de juego (escena), que cargaremos al pulsar
dicho botón.

Para definirla, debemos guardar primero la escena actual mediante la
opción de menú File \> Save Scene, con el nombre MainMenu. Una buena
práctica es guardar las escenas juntas, en una carpeta Scenes, para
mantener un orden dentro del proyecto.

Seguidamente, crearemos una escena nueva con el menú File \> New Scene.
Al hacerlo, aparece una nueva pantalla vacía. La guardamos con el nombre
Game. De esta manera, Unity ya puede discriminar y cargar distintas
pantallas según su nombre. Sin embargo, aún no hemos terminado, porque
antes debemos indicar cuál es la primera escena que debe cargar Unity al
arrancar el juego.

La gestión de escenas en un proyecto se lleva a cabo mediante el menú
File \> Build Settings. En este menú podemos especificar diferentes
opciones sobre la generación del juego, como puede ser la plataforma
objetivo. En la parte superior (Scenes In Build) se encuentra la lista
de escenas que forman parte del juego. A esta lista podemos arrastrar
cualquier escena desde el apartado de *Assets* del editor. La primera
escena de la lista será la primera que se cargará al iniciarse el juego.
El resto, se cargarán únicamente mediante código. Pero solo será posible
cargar escenas que se encuentren en esta lista explícitamente.

![](images/part4/build_settings.png)
 

¿Qué sentido tiene esta lista, más allá de la primera escena? Es
bastante frecuente en proyectos hacer escenas de prueba que no queremos
que acaben en la versión final. También hay muchos *assets* en la Asset
Store que incluyen escenas para demostrar cómo se configuran o cómo
pueden mostrarse, que tampoco nos interesa que acaben en nuestro
ejecutable final, porque podrían inflar innecesariamente nuestra
aplicación. Así pues, de este modo podemos indicar qué escenas acaban
incluyéndose realmente en el juego final.

Una vez completado este paso, Unity ya podrá cargar nuestras escenas
correctamente.

> Cada vez que se carga una nueva escena, se destruyen todos los objetos
> de la anterior.

| **Reto 3** |
| ---    |
| Haced que al pulsar el botón de nueva partida se cargue la escena Game. Para ello, cread un *script* llamado NewGame con un único método llamado StartNewGame que lleve a cabo esta acción. Para esta tarea, estudiad la documentación de Unity sobre clase SceneManager.

Recordad que deberéis asociar el método al evento de pulsación del botón
mediante el *listener* correspondiente.

| **Reto 4** |
| ---    |
| Pensad qué deberíais hacer si, en vez de usar botones, quisierais usar texto (un GameObject tipo Text, en vez de Button) y que el usuario pudiera iniciar partida o salir del juego pulsando sobre él.

Ahora que ya sabemos cómo interactuar con una UI simple y cambiar de
escena, vamos a desarrollar la pantalla de juego de nuestro proyecto.


--> <a href="Parte4-3.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)


## 4.2. Creació de la interfície d\'usuari bàsica

Una interfície d\'usuari intuïtiva i informativa és essencial perquè
l\'usuari sàpiga com moure's dins del joc. La gran majoria dels jocs
comencen amb un menú principal des d\'on es poden començar partides
noves o continuar partides existents. Si bé hi ha jocs que han explorat
maneres més originals de complir aquesta funció, aquesta és una fórmula
clàssica i provada que sabem que no fallarà. Començarem, doncs, per
aquesta pantalla.

En primer lloc, crearem un nou projecte de Unity, recordant seleccionar
el *template* 2D. Una vegada creat el projecte, seleccionarem la
pestanya Game i la situarem, arrossegant-la, a la dreta de la pestanya
Scene, per treballar més còmodament. A continuació, afegirem un botó
mitjançant l\'opció de menú GameObject \> UI \> Button.

> En el menú GameObject s\'agrupen diferents tipus d\'objectes. Entre
> ells, la UI per als d\'interfície d\'usuari.

El resultat hauria de ser molt semblat a la següent figura, que serà el
nostre punt de partida:

![](images/part4/button.png)

### 4.2.1. Elements d'UI a Unity


Quan s'ha afegit el botó, s\'han creat diversos GameObjects a l\'apartat
de Hierarchy. Un d\'ells porta el nom d'EventSystem. Si el seleccionem,
veurem a l\'Inspector que conté dos components: un Event System i un
Standalone Input Module.

D\'una banda, el component Event System permet rebre la interacció de
l\'usuari, i simplement necessitem que n'hi hagi un a l\'escena per
poder dur a terme aquesta funció. D\'altra banda, el component
Standalone Input Module s\'encarrega de fer la traducció de les accions
a esdeveniments. Per exemple, en aquest component podem seleccionar quin
és el botó de cancel·lar una acció o com es diuen els eixos verticals i
horitzontals. En general, si no estem experimentant amb controls
específics per a la nostra aplicació, els valors per defecte seran
adequats per a la majoria de les situacions habituals.

Un altre GameObject que s\'ha creat a la Hierarchy és l\'anomenat
Canvas. Si el seleccionem i l'observem a l\'Inspector, el primer que ens
cridarà l\'atenció és que no té un component Transform, sinó un
d\'anomenat Rect Transform. En realitat, es tracta d\'un cas específic
de Transform que empren els elements d\'UI a Unity. Internament funciona
igual que un Transform, però ens proporciona una manera més còmoda
d\'interacció per al disseny de la nostra UI. Els següents tres
*components* en aquest GameObject són Canvas, Canvas Scaler i Graphic
Raycaster. El funcionament exacte d\'aquests tres *components* és
complex, però es pot resumir dient que ens permeten definir una àrea on
podem afegir elements d\'UI, i que s\'encarreguen de calcular a quins
elements afecta la interacció de l\'usuari. Ara com ara, això és
suficient.


> Tots els elements d\'UI han de ser nodes fill del *Canvas*.

Finalment, hi ha el mateix botó, l\'objecte Button, que ha aparegut com
a element fill de Canvas. Al seu torn, ha aparegut un objecte Text com a
fill de Button. Els noms són bastant autoexplicatius.

> Aquest GameObject representa un text en una UI. Com a fill d\'un botó
> representa el text que conté.

Si observem Button a l\'Inspector, veiem que té tres components: Canvas
Renderer, Image i Button. Canvas Renderer és el component que indica a
Unity que hi ha elements visuals d\'una UI (per exemple, text, una
imatge, etc.) i, per tant, cal afegir-lo perquè es vegin per pantalla.
Image permet especificar la imatge que es mostrarà a la nostra UI,
mentre que Button és únicament una manera d\'indicar-li a Unity que
aquest GameObject té una interacció de botó, però no s\'encarrega de
mostrar res per pantalla.

> Qualsevol GameObject amb un component Button es comporta com un botó,
> responent a l\'entrada de l\'usuari.

Així doncs, com veiem, per programar UI a Unity reutilitzem i combinem
molts components senzills per mitjà de l\'editor, cadascun amb una
funcionalitat molt concreta, de manera que es van creant estructures més
complexes, seguint la filosofia de la simplicitat.

### 4.2.2. La pantalla inicial


És el moment de començar a treballar en la pantalla d\'inici del joc. En
primer lloc, dupliquem el botó i renombrem tots dos botons amb els noms
NewGame i Exit. A continuació, canviem el text de cada botó pels textos
corresponents, «Nova partida» i «Sortir». Per a fer-ho, editem el seu
component Text.

> Per duplicar un GameObject, es pot fer retallant i enganxant com en la
> majoria dels editors.
>
> El nom d\'un GameObject es canvia des de l\'Inspector.

Finalment, situem els botons centrats i separats de manera que no es
tapin l\'un a l\'altre. Podem arrossegar-los visualment mitjançant
l\'editor o assignar unes coordenades concretes al component Transform
de cadascun d\'ells:

-   **NewGame:** Pos X = 0, Pos Y = 30, Pos Z = 0

-   **Exit:** Pos X = 0, Pos Y = -30, Pos Z = 0


El resultat d\'aquestes operacions és el següent:

![](images/part4/main_menu.png)

En aquests moments, si entrem en mode execució (prement el botó Play),
veurem que els botons es mostren correctament i que es poden prémer, tot
i que fer-ho encara no té cap efecte associat.

### 4.2.3. *Scripting* associat a la UI

Perquè la nostra UI dugui a terme accions concretes, serà necessari
associar *scripts* que implementin aquestes accions als nostres objectes
d\'UI. Començarem creant l'*script* que respondrà quan es premi el botó
*Exit* i que simplement ha de tancar l\'aplicació.

> Per crear un *script*, hem de prémer el botó dret del ratolí sobre
> l\'apartat d\'*Assets* (pestanya *Project*) a l\'editor i seleccionar
> Create \> C\# Script.


| **Repte 1** |
| ---    |
| Creeu un *script* anomenat ExitGame amb un únic mètode anomenat Exit que quan sigui anomenat provoqui que es mostri per consola el missatge «Sortint del joc...».|


Quan s'hagi creat l'*script*, l'afegirem com a component al botó Exit,
simplement arrossegant-lo sobre l\'Inspector (o, alternativament, fent
clic sobre el botó Add Component i triant el component manualment). Amb
això, l'*script* passa a formar part d\'aquest objecte.

> Els *scripts* s\'associen, generalment, com a components dels objectes
> del joc.

Ara és necessari associar-lo a l\'acció pròpiament de prémer el botó
Exit. Per associar codi a l\'acció de prémer un botó s\'ha d\'assignar
mitjançant un *listener*. Això es duu a terme amb el component Button
del botó. A la part inferior de l\'Inspector apareix un requadre on es
llisten els *listeners* de l\'esdeveniment OnClick.

> Un ***listener*** és l\'encarregat d\'escoltar i controlar
> esdeveniments.

Per afegir un *listener* s\'ha de prémer el símbol +; aleshores, apareix
un apartat on es pot indicar el *listener*, inicialitzat a None (Object)
(cap). Sobre aquest quadre s\'ha d\'arrossegar des de la Hierarchy
l\'objecte que posseeix el codi per executar. En el nostre cas,
l\'objecte que conté l'*script*, que és el mateix botó Exit. Una vegada
arrossegat, és possible seleccionar a la caixa desplegable contigua el
mètode que s\'ha d\'executar. Per a fer-ho, primer s\'ha de buscar el
component adequat (en aquest cas, el nostre *script* GameExit), i
després el mètode, tal com mostra la següent imatge:

![](images/part4/exit_game.png)

Com podem comprovar, Unity reconeix els mètodes que contenen els
*scripts*, sempre que siguin públics i tinguin una signatura compatible
amb l\'esdeveniment (que tinguin els mateixos paràmetres i que retornin
*void*). En concret el que fa Unity és enumerar els components de
l\'objecte que se seleccioni i llistar totes les funcions compatibles.
Gràcies a aquesta funcionalitat, podem definir comportaments de manera
visual amb l\'editor.

Per comprovar que el procés funciona correctament, podem entrar en mode
execució i prémer el botó Exit. Una vegada fet això, podem actualitzar
el codi perquè realment provoqui la sortida del joc en lloc de mostrar
únicament un missatge a la consola.

| **Repte 2** |
| ---    |
|   Modifiqueu l'*script* que realment detindria el joc en prémer el botó Exit. Per a aquesta tasca, estudieu la documentació de la classe Application.|
El motiu pel qual hem dut a terme aquesta tasca en dos passos és que la
crida al mètode que surt de l\'aplicació no té efecte dins de l\'editor
de Unity. Per tant, no és possible provar realment el funcionament que
té en mode execució.

Arriba el moment de fer la funcionalitat de l\'altre botó, el de
*NewGame*. Abans, però, serà necessari preparar el projecte perquè hi
hagi una pantalla de joc (escena), que carregarem en prémer aquest botó.

Per definir-la, primerament hem de guardar l\'escena actual mitjançant
l\'opció de menú File \> Save Scene, amb el nom MainMenu. Una bona
pràctica és guardar les escenes juntes, en una carpeta Scenes, per
mantenir un ordre dins del projecte.

Seguidament, crearem una escena nova amb el menú File \> New Scene. En
fer-ho, apareix una nova pantalla buida. La guardem amb el nom Game.
D\'aquesta manera, Unity ja pot discriminar i carregar diferents
pantalles segons el seu nom. De totes maneres, encara no hem acabat,
perquè abans hem d\'indicar quina és la primera escena que ha de
carregar Unity en començar el joc.

La gestió d\'escenes en un projecte es duu a terme mitjançant el menú
File \> Build Settings. En aquest menú podem especificar diferents
opcions sobre la generació del joc, com pot ser la plataforma objectiu.
A la part superior (Scenes In Build) hi ha la llista d\'escenes que
formen part del joc. Podem arrossegar a aquesta llista qualsevol escena
des de l\'apartat d\'*Assets* de l\'editor. La primera escena de la
llista serà la primera que es carregarà en iniciar-se el joc. La resta,
es carregaran únicament mitjançant codi. Però només serà possible
carregar escenes que siguin explícitament en aquesta llista.

![](images/part4/build_settings.png)
 

Quin sentit té aquesta llista més enllà de la primera escena? En els
projectes, és bastant freqüent fer escenes de prova que no volem que
acabin a la versió final. També hi ha molts *assets* a l\'Asset Store,
que inclouen escenes per demostrar com es configuren o com poden
mostrar-se, que tampoc ens interessa que acabin al nostre executable
final, perquè podrien inflar innecessàriament la nostra aplicació. Així
doncs, d\'aquesta manera podem indicar quines escenes acaben incloent-se
realment al joc final.

Quan haguem completat aquest pas, Unity ja podrà carregar les nostres
escenes correctament.

> Cada vegada que es carrega una nova escena, es destrueixen tots els
> objectes de l\'anterior.

| **Repte 3** |
| ---    |
| Feu que en prémer el botó de nova partida es carregui l\'escena Game. Per a fer-ho, creeu un *script* anomenat NewGame amb un únic mètode anomenat StartNewGame que dugui a terme aquesta acció. Per a fer aquesta tasca, estudieu la documentació de Unity sobre classe SceneManager.

Recordeu que haureu d\'associar el mètode a l\'esdeveniment de pulsació
del botó mitjançant el *listener* corresponent.

| **Repte 4** |
| ---    |
| Penseu què hauríeu de fer si, en comptes d\'usar botons, volguéssiu usar text (un GameObject tipus Text, en comptes de Button) i que l\'usuari pogués iniciar partida o sortir del joc prement-hi.

Ara que ja sabem com interactuar amb una UI simple i canviar d\'escena,
desenvoluparem la pantalla de joc del nostre projecte.

--> <a href="Parte4-3.md">Pàgina següent</a>
