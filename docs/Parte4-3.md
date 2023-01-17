<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


# 4.3. La pantalla de juego


La pantalla de juego estará compuesta por dos secciones con elementos de
UI: una en la que tendremos el texto que describe nuestra situación y
otra en la que tendremos todas las opciones posibles de interacción del
jugador. Vamos a construir estas dos secciones en la escena Game, que
corresponderá a la pantalla de juego.

## 4.3.1. Configuración de la pantalla de juego


En primer lugar, vamos a Hierarchy y desplegamos el menú contextual con
el botón derecho del ratón sobre el Canvas. Mediante la opción UI \>
Text, creamos un elemento UI de texto. Para hacer que ocupe el espacio
que nos interesa, podemos usar las herramientas señaladas en la figura.
La señalada en la parte superior sirve para poder definir el tamaño de
los distintos elementos de UI en el editor de escena, a partir de los
puntos azules remarcados. La herramienta señalada con forma de triángulo
nos sirve para definir el anclaje del campo de texto. Especialmente en
los dispositivos móviles, hay una gran diversidad de tamaños de
pantallas y de proporciones; por ello, debemos situar los anclajes
correctamente para que nuestro UI se muestre correctamente en diferentes
dispositivos.

![](images/part4/ui_text.png)

> El **anclaje** (*anchoring*) de un elemento indica su comportamiento
> cuando se redimensiona la pantalla.

Vamos a añadirle también un fondo. Esta vez seleccionamos la opción UI
\> Image. Ajustamos el tamaño para que sea ligeramente más grande que el
texto y ajustamos los anclajes para que sean los mismos que los del
texto. Ahora podemos emparentar el texto a la imagen por comodidad.
Podemos también añadirle un fondo para que tenga los bordes un poco
suavizados. Para hacerlo, se debe asignar a la propiedad Source Image de
su componente Image. Podemos pulsar sobre el campo para abrir un
selector, o bien arrastrarla directamente desde al apartado de Assets
sobre el campo.

> Para poder añadir una imagen al objeto Image, esta antes ha de estar
> incluida dentro de los *assets* del proyecto. En nuestro ejemplo,
> ponemos simplemente un fondo gris.

| **Reto 5** |
| ---    |
|Buscad un fichero con una imagen de fondo que os guste y ponedla como fondo de la pantalla usando el objeto Image.

Además, vamos a añadir un pequeño título para que el jugador sepa
visualmente qué significa esta sección. Podemos duplicar los GameObjects
que hemos creado y ajustar el tamaño, para que se vean como un simple
detalle, y la posición, para que queden centrados y en la parte
superior. Si renombramos los GameObjects con nombres que reflejen el
significado de lo que representan, debería quedarnos una estructura como
la de la siguiente figura:

![](images/part4/story_section.png)


Ahora vamos a crear la sección de respuestas. El proceso será muy
similar al anterior, pero situaremos todo en la parte inferior de la
pantalla. También crearemos un botón, que hará de modelo de posible
respuesta. Existirá un botón por respuesta posible en cada escena. El
anclaje de este primer botón lo pondremos en la esquina superior
izquierda de la zona de respuestas.

![](images/part4/answers_section.png)

De este modo, tenemos los siguientes objetos de UI en la escena:

- **StoryText:** el texto que describe la situación actual al jugador.
- **StoryTitleText:** el título de la sección de historia.
- **AnswersTitleText:** el título de la sección de respuestas.
- **Button:** los botones de las posibles respuestas (de momento, solo uno).


A cada uno de estos objetos se le asocia una imagen de modo que, por su
relación en la *Hierarchy*, si se desplaza la imagen, también se
desplaza con ella el elemento de UI correspondiente.

Finalmente, vamos a generar un *prefab* a partir del botón. La idea es
que el texto de la historia puede darnos varias opciones de respuesta, y
queremos poder instanciar un botón por cada una. Para hacerlo, la opción
más cómoda es usando *prefabs*. El tamaño del botón lo hemos dejado en
*Width = 150 y Height = 45, que* parece un poco grande, pero así
permitimos respuestas un poco largas.

> Para crear un *prefab* fácilmente, basta con arrastrar el objeto de la
> *Hierarchy* al apartado de *Assets*. Su nombre quedará en azul.

Ya tenemos una primera configuración de la escena, pero aún quedan
algunos problemas que resolver. El primero es que el texto o los bordes
de las imágenes puede que se vean un poco borrosos. Esto se puede
solucionar marcando la opción Pixel Perfect, en el componente de Canvas,
dentro del GameObject con el mismo nombre.

Otro problema surge cuando el texto es demasiado largo y no cabe en el
espacio que hemos dejado para el texto de la historia. Necesitamos
entonces configurar una función de *scroll*. Para ello, primero
agrandamos el GameObject StoryText hacia abajo, de manera que sobresalga
claramente de la imagen que delimita el texto de la historia. Esto, como
es de esperar, causa que el texto se vea en zonas donde no debería
verse, pero es un paso previo a la solución final.

![](images/part4/answers_overflow.png)

Para solucionar el problema, vamos a crear un GameObject hijo de
StoryImage y hermano de StoryText. A este nuevo GameObject, al que vamos
a llamar MaskImage, le vamos a añadir una imagen mediante el componente
Image. Lo importante es que se defina el tamaño de manera que delimite
dónde se tendría que ver texto únicamente, es decir, debe ser un tamaño
ligeramente menor que el del GameObject StoryImage. Al GameObject
MaskImage le añadimos un componente Scroll Rect y otro Mask. El primero
le indica a Unity que todo el contenido que se asigne al campo Content
se puede desplazar en modo *scroll*. El segundo limita la visualización
de un objeto hijo en la Hierarchy, de modo que nunca ocupe más tamaño
que el objeto padre. Por lo tanto, tendremos que emparentar el contenido
que queramos delimitar con MaskImage.

En estos dos componentes, Scroll Rect y Mask, hay que configurar algunas
propiedades. De entrada, el componente Image está pintando una imagen
que realmente no nos interesa mostrar y que está tapando el contenido
que hay debajo. Para corregir esto, en el componente Mask desmarcamos la
opción Show Mask Graphic. Ahora que ya le hemos indicado a Unity cómo
funciona el *scroll* y qué zonas se deben ver, debemos emparentar
correctamente el contenido. Como hemos dicho, los elementos hijos de
MaskImage son los que se verán correctamente. Por lo tanto, debemos
emparentar el GameObject StoryText al MaskImage, y entonces el texto ya
sí que solo se debería ver en las zonas que nos interesan.

Por otra parte, la propiedad Content del Scroll Rect se debe asignar al
GameObject StoryText (por ejemplo, arrastrando desde la Hierarchy) para
indicarle a Unity que este es el elemento que funciona en modo *scroll*.
En este mismo componente también deseleccionamos el campo Horizontal,
para que el *scroll* solo sea vertical. Con todo esto, si al ejecutar el
juego ponemos un texto muy largo, podremos desplazarlo arrastrando el
contenido con el ratón. Por otro lado, es habitual definir barras de
*scroll* para poder operar de una manera más intuitiva.

![](images/part4/scrollrect.png)

Por comodidad, se suelen poner las barras a los lados, para poder hacer
desplazamiento fácilmente. Esto se puede hacer añadiendo un objeto UI \>
Scrollbar en el Canvas, que representa una barra de desplazamiento.
Inicialmente, se nos mostrará una barra horizontal, que no es adecuada
para nuestro diseño. En el campo Direction, en su componente Scrollbar,
podemos seleccionar el sentido de la barra. En nuestro caso nos interesa
Bottom To Top.

Ahora debemos asignar este GameObject al campo Vertical Scrollbar del
componente Scroll Rect que hemos creado. Finalmente, ajustamos el tamaño
y la posición de la barra de *scroll* para que quede situada cómodamente
en la parte derecha. Con todas estas operaciones deberíamos tener un
texto con desplazamiento, y probar el correcto funcionamiento apretando
Play.

![](images/part4/scrollbar.png)

En general, es una buena idea tener los GameObjects bien organizados y
por categorías. En ese sentido, a veces conviene tener GameObjects
vacíos (*empty*), que no tienen ninguna función en el juego pero que
hacen posible agrupar otros objetos de manera que formen una estructura
que permita tener ordenados los elementos de juego por grupos. Esto
mejora la legibilidad del proyecto.

| **Reto 6** |
| ---    |
| Reorganizad la jerarquía usando objetos vacíos, de modo que al final quede todo ordenado según la figura de debajo. Dividiremos los elementos de la pantalla de juego según dos apartados: StorySection y AnswersSection. |

![](images/part4/organization.png)

## 4.3.2. Control del juego

Ahora que ya tenemos todos los elementos de la UI, ya podemos empezar a
crear la lógica del juego. Cuando tratamos lógica que no está claramente
asociada a un objeto concreto en la interfaz (por ejemplo, los botones
de la pantalla de inicio), lo normal es crear un GameObject vacío que
sirve como controlador o gestor del juego; este GameObject vacío no
tiene visualización en pantalla, solo sirve para agrupar ciertos scripts
generales. En este caso, llamaremos a dicho objeto *GameplayManager* y
contendrá el *script* con el código.

La estrategia que hay que seguir para controlar el juego será la
siguiente. Si bien podríamos generar tantas pantallas como
localizaciones tiene nuestro juego (si nuestro juego tiene diez
localizaciones, crear diez escenas en el proyecto), dado que todas las
pantallas van a tener un aspecto idéntico salvo en el texto explicativo
y las opciones disponibles, lo que haremos es trabajar sobre una sola
pantalla de juego y cambiar el contenido de los cuadros de texto según
corresponda. No tiene sentido ir replicando exactamente la misma escena,
ya que sería un trabajo sumamente tedioso e ineficiente.

> Las localizaciones del juego se corresponderían, de hecho, a las
> páginas de un libro de *Elige tu propia aventura*.

De cara a generar el código que controle las distintas localizaciones
del juego, el punto de partida será una estructura de datos en forma de
grafo dirigido que represente el mapa de localizaciones. Cada vértice es
una localización y sus aristas salientes son las distintas opciones,
cada una apuntando a su vértice destino.

El código del *script* que define esta estructura de datos será el
siguiente:

```csharp
using System;

public class StoryNode
{
    public string History;
    public string[] Answers;
    public bool IsFinal;
    public StoryNode[] NextNode;
    public Action OnNodeVisited;
}

```

Este *script* define una estructura de datos llamada *StoryNode*. A
partir de esta, generaremos el grafo y todo el contenido de las
localizaciones. Sus atributos son:

-   **History:** el texto que describe la localización.

-   **Answers\[\]:** la lista de textos con las respuestas posibles.

-   **IsFinal:** indica que este nodo corresponde a un final, donde
    acaba la aventura.

-   **NextNode\[\]:** la lista de nodos destino, en el mismo orden que
    en la lista de respuestas. Es decir, si se elige la respuesta en el
    índice 1 de *answers*, el jugador se desplazará al nodo indicado por
    *nextNode\[1\].*

-   **OnNodeVisited:** permite asignar una referencia a un método
    delegado que se ejecutará siempre que se visite esa localización.
    Esta estrategia permite ejecutar código que manipule el mapa al
    llegar a ciertas localizaciones.

**Modificando el mapa en tiempo de ejecución**

En algunos momentos del juego será necesario modificar el mapa en tiempo
de ejecución. Por ejemplo, una ubicación puede tener una puerta cerrada,
que solo se podrá abrir si se ha cogido la llave correspondiente.

En un libro de *Elige tu propia aventura*, esto se resuelve normalmente
con un texto al estilo "Si tienes la llave, ves a la página ...; en
caso contrario, ves a la página ...". En nuestro juego, la estrategia
es la siguiente. Se van a crear dos nodos, uno que indica que la puerta
no se puede abrir (N1) y otro que representa que se abre con éxito (N2).
Inicialmente, el nodo asignado en *nextNode* a la opción de abrir la
puerta es N1. Será en la localización que representa que se coge la
llave donde asignaremos el método delgado que reemplace N2 por N2, de
modo que, a partir de entonces, al llegar a la puerta, la acción de
abrir tendrá éxito automáticamente.

Además, en la clase GameplayManager existe el atributo CurrentNode,
que indicará en todo momento en qué nodo se encuentra actualmente el
jugador. El valor que se le asigne al iniciar el juego será la primera
localización.

Nuestra primera tarea será inicializar el mapa de localizaciones. En
este ejemplo, para simplificar, lo haremos de manera estática
directamente mediante código. Evidentemente, esta solución no es
escalable ni la mejor en un proyecto real. Sería mejor cargarlo desde un
fichero de datos estructurado, por ejemplo. Sin embargo, nuestra opción
a veces es una buena manera de generar prototipos rápidamente para
comprobar que todo funciona; más tarde se puede reformular si se
considera necesario.

La inicialización la llevará a cabo otro *script* que llamaremos
*StoryFiller* y que definirá una clase auxiliar que no se asignará a
ningún objeto. De este modo se separa la gestión del juego de la carga
de datos, manteniendo así el principio de encapsulación de código.

> Nótese que StoryFiller no hereda de MonoBehaviour, puesto que no
> es necesario.

```csharp
public static class StoryFiller
{
    public static StoryNode FillStory()
    {
        // Código de inicialización.
    }
}

```

Su valor de retorno es el nodo inicial, la que será la primera
localización del juego.

| **Reto 7** |
| ---    |
| Rellenad el código del método FillStory de modo que generéis un mapa de localizaciones para el juego. Será necesario ir creando los nodos dinámicamente e inicializar sus atributos de algún modo.

Una vez tenemos el código que carga el mapa del juego, podemos
implementar el *script* GameplayManager, que es el que realmente
gestionará la pantalla de juego. Su función principal será la de
actualizar la interfaz de usuario con los datos asociados a la ubicación
actual del jugador. Principalmente, actualizar los textos en pantalla,
eliminar los botones actuales y crear los nuevos que correspondan, según
el número de acciones disponibles en dicha localización.

Para destruir y crear objetos dinámicamente, Unity ofrece dos métodos.
Por una parte, Destroy elimina el objeto pasado como parámetro. Por
otra parte Instantiate crea objetos a partir de uno ya existente, que
es replicado. En este caso, sus parámetros son una referencia al objeto
a copiar, su posición y su rotación. Vale la pena destacar que dicho
método genera copias de objetos, no los crea realmente desde cero.
Normalmente lo que se hace no es copiar realmente un objeto ya
preexistente en la Hierarchy (lo que podría ser un problema si no hay
ningún otro objeto del mismo tipo aún creado), sino usar un *prefab*.

> Podéis ver todos los detalles de ambos métodos en la documentación
> oficial.

**Accediendo a *prefabs* desde el código de un *script***

Los *prefabs* se crean desde la pantalla del editor y se guardan en
forma de *asset* en el apartado Project. Una manera muy sencilla para
que vuestro código pueda acceder a dicho *prefab* es la siguiente.
Primero, crear un atributo público de tipo GameObject en vuestro
*script*. Esto hace que en el Inspector, dentro del componente
Script, aparezca un campo asignable. Entonces, arrastrar el *prefab*
de Project a dicho apartado. A partir de ese momento, siempre que se
ejecute el *script*, en dicho atributo estará disponible el *prefab*.

En general, recordad que todo atributo declarado público en el código de
un *script* aparece como un apartado asignable en su componente en el
editor, que puede ser inicializado arrastrando el elemento
correspondiente. Por ejemplo, si queremos tener un modo de acceso fácil
a un elemento de la UI (1) o a alguno de sus componentes, podemos hacer
exactamente lo mismo. Solo habrá que definir el atributo del tipo que
corresponda (por ejemplo, Text para un campo de texto, Transform para
una componente Transform, etc.). Unity dispone de tipos de datos para
prácticamente todos los elementos asociados a objetos en el editor.

(1) Las clases que representan los elementos de una UI en Unity están en
    > la biblioteca UnityEngine.UI.

Una vez creado un objeto a partir de un *prefab*, seguramente querremos
personalizar algunas de sus propiedades. Para ello, deberemos modificar
sus componentes, también dinámicamente. Para acceder a una componente de
un GameObject es necesario invocar su método GetComponent(). Por
ejemplo, para acceder al componente RectTransform de un elemento de UI,
se ejecutaría GetComponent\< RectTransform\>(). Una vez se dispone del
componente, es posible acceder y manipular todas sus propiedades
mediante los métodos y atributos públicos que ofrece.

Otro aspecto que deberemos gestionar dinámicamente es añadir *listeners*
a elementos de UI (en este caso, los nuevos botones), de modo que cada
nuevo botón nos desplace a la ubicación que corresponda. En este
sentido, los componentes de UI que esperan *listeners* disponen de
atributos que permiten asignar referencias a métodos. Por ejemplo, el
componente Button dispone de la variable onClick, que a su vez dispone
del método AddListener.

> Recordad que el *listener* se añade a un componente Button de un
> GameObject, no al objeto en sí.

Un ejemplo de código asociado a esta operación sería:

```csharp
var button = obj.GetComponent<Button>();
button.onClick.AddListener(() =>
{
    // Código del listener.
});

```

> Básicamente, es la misma sintaxis que en los métodos delegados.

Finalmente, otro mecanismo muy útil a la hora de gestionar objetos por
medio de un *script* es poder recorrer los elementos de su jerarquía de
acuerdo con la estructura mostrada en la Hierarchy del editor. Esta
tarea se puede llevar a cabo mediante el componente Transform de un
objeto:

```csharp
var parent = obj.GetComponent<Transform>();
foreach (Transform child in parent)
{
    // Código que manipula sus hijos vía la variable child.
}

```

> Recordad que toda manipulación del componente Transform de un objeto
> se hereda a todos los hijos en la jerarquía.

Relacionado con este mecanismo de recorrido, el componente Transform
posee también el atributo *parent*, que contiene su padre en la
jerarquía. Asignando el valor correspondiente es posible crear
relaciones padre-hijo.

> El atributo gameObject contiene el objeto asociado al Transform en
> cuestión.

| **Reto 8** |
| ---    |
| Completad la clase GameplayManager. Primero, debe encargarse de generar el mapa al inicio de la partida. Pensad qué método debe incorporar dicho código. Inmediatamente después, debe inicializar la UI con los datos de la primera ubicación. A partir de aquí, debe encargarse de actualizar la ubicación del personaje y mostrar los nuevos datos en la UI cada vez que se pulsa alguno de los botones que enumeran las acciones disponibles. |



--> <a href="Parte4-4.md">Página siguiente</a>

<br /><hr />


<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)


# 4.3. La pantalla de joc

La pantalla de joc estarà composta per dues seccions amb elements d\'UI:
una en la qual tindrem el text que descriu la nostra situació i una
altra on tindrem totes les opcions possibles d\'interacció del jugador.
Construirem aquestes dues seccions en l\'escena Game, que correspondrà a
la pantalla de joc.


## 4.3.1. Configuració de la pantalla de joc



En primer lloc, anem a Hierarchy i despleguem el menú contextual amb el
botó dret del ratolí sobre el Canvas. Mitjançant l\'opció UI \> Text,
crearem un element UI de text. Per fer que ocupi l\'espai que ens
interessa, podem utilitzar les eines assenyalades a la figura.
L\'assenyalada a la part superior serveix per poder definir la grandària
dels diferents elements d\'UI a l\'editor d\'escena, a partir dels punts
blaus remarcats. L\'eina assenyalada amb forma de triangle ens serveix
per definir l\'ancoratge del camp de text. Especialment en els
dispositius mòbils, hi ha una gran diversitat de grandàries de pantalles
i de proporcions; per això, hem de situar els ancoratges correctament
perquè el nostre UI es mostri correctament en diferents dispositius.

![](images/part4/ui_text.png)

> L\'**ancoratge** (*anchoring*) d\'un element indica el comportament
> que té quan es redimensiona la pantalla.

Anem a afegir-li també un fons. Aquesta vegada seleccionem l\'opció UI
\> Image. Ajustem la grandària perquè sigui lleugerament més gran que el
text i ajustem els ancoratges perquè siguin els mateixos que els del
text. Ara podem emparentar el text a la imatge per comoditat. Podem
també afegir-li un fons perquè tingui les vores una mica suavitzades.
Per a fer-ho, s\'ha d\'assignar a la propietat Source Image del seu
component Image. Podem prémer sobre el camp per obrir un selector, o bé
arrossegar-la directament des de l\'apartat d\'Assets sobre el camp.

> Per poder afegir una imatge a l\'objecte Image, aquesta abans ha
> d\'estar inclosa dins dels *assets* del projecte. En el nostre
> exemple, posem simplement un fons gris.

| **Repte 5** |
| ---    |
|Busqueu un fitxer amb una imatge de fons que us agradi i poseu-la com a fons de la pantalla usant l\'objecte Image.

A més, afegirem un petit títol perquè el jugador sàpiga visualment què
significa aquesta secció. Podem duplicar els GameObjects que hem creat i
ajustar-los la grandària, perquè es vegin com un simple detall, i la
posició, perquè quedin centrats i a la part superior. Si renombrem els
GameObjects amb noms que reflecteixin el significat del que representen,
hauria de quedar-nos una estructura com la de la següent figura:

![](images/part4/story_section.png)


Ara crearem la secció de respostes. El procés serà molt similar a
l\'anterior, però ho situarem tot a la part inferior de la pantalla.
També crearem un botó, que farà de model de resposta possible. Hi haurà
un botó per resposta possible a cada escena. L\'ancoratge d\'aquest
primer botó el posarem a la cantonada superior esquerra de la zona de
respostes.

![](images/part4/answers_section.png)


D\'aquesta manera, tenim els següents objectes d\'UI a l\'escena:

-   **StoryText:** el text que descriu la situació actual al jugador.

-   **StoryTitleText:** el títol de la secció d\'història.

-   **AnswersTitleText:** el títol de la secció de respostes.

-   **Button:** els botons de les respostes possibles (de moment, només
    un).

D\'aquesta manera, tenim els següents objectes d\'UI a l\'escena:

-   **StoryText:** el text que descriu la situació actual al jugador.

-   **StoryTitleText:** el títol de la secció d\'història.

-   **AnswersTitleText:** el títol de la secció de respostes.

-   **Button:** els botons de les respostes possibles (de moment, només
    un).

A cadascun d\'aquests objectes se li associa una imatge de manera que,
per la seva relació a la *Hierarchy*, si es desplaça la imatge, també es
desplaça, amb ella, l\'element d\'UI corresponent.

Finalment, generarem un *prefab* a partir del botó. La idea és que el
text de la història pot donar-nos diverses opcions de resposta, i volem
poder instanciar un botó per a cadascuna d'elles. Per a fer-ho, l\'opció
més còmoda és utilitzar *prefabs*. La grandària del botó l'hem deixat en
*Width = 150* i *Height = 45*, que sembla una mica gran, però així
permetem respostes una mica llargues.

> Per crear un *prefab* fàcilment, n\'hi ha prou d'arrossegar l\'objecte
> de la *Hierarchy* a l\'apartat d\'*Assets*. El nom quedarà en blau.


Ja tenim una primera configuració de l\'escena, però encara queden
alguns problemes per resoldre. El primer és que el text o les vores de
les imatges pot ser que es vegin una mica borrosos. Això es pot
solucionar marcant l\'opció Píxel Perfect, al component de Canvas, dins
del GameObject amb el mateix nom.

Un altre problema sorgeix quan el text és massa llarg i no cap a
l\'espai que hem deixat per al text de la història. Aleshores necessitem
configurar una funció de *scroll*. Per a fer-ho, primerament engrandim
el GameObject StoryText cap avall, de manera que sobresurti clarament de
la imatge que delimita el text de la història. Això, com és normal, fa
que el text es vegi en zones on no hauria de veure\'s, però és un pas
previ a la solució final.


![](images/part4/answers_overflow.png)


Per solucionar el problema, crearem un GameObject fill de StoryImage i
germà de StoryText. A aquest nou GameObject, al qual anomenarem
MaskImage, li afegirem una imatge mitjançant el component Image.
L\'important és que es defineixi la grandària de manera que delimiti on
s'hauria de veure únicament text, és a dir, ha de ser una grandària
lleugerament menor que el del GameObject StoryImage. Al GameObject
MaskImage li afegim un component Scroll Rect i un altre Mask. El primer
indica a Unity que tot el contingut que s\'assigni al camp Content es
pot desplaçar en mode *scroll*. El segon limita la visualització d\'un
objecte fill a la Hierarchy, de manera que mai no ocupi més grandària
que l\'objecte pare. Per tant, haurem d\'emparentar el contingut que
vulguem delimitar amb MaskImage.

En aquests dos components, Scroll Rect i Mask, cal configurar algunes
propietats. D\'entrada, el component Image està pintant una imatge que
realment no ens interessa mostrar i que està tapant el contingut que hi
ha sota. Per corregir això, en el component Mask desmarquem l\'opció
Show Mask Graphic. Ara que ja li hem indicat a Unity com funciona
l'*scroll* i quines zones s\'han de veure, hem d\'emparentar
correctament el contingut. Com hem dit, els elements fills de MaskImage
són els que es veuran correctament. Per tant, hem d\'emparentar el
GameObject StoryText al MaskImage, i llavors el text ja sí que només
s\'hauria de veure a les zones que ens interessen.

D\'altra banda, la propietat Content del Scroll Rect s\'ha d\'assignar
al GameObject StoryText (per exemple, arrossegant des de la Hierarchy)
per indicar-li a Unity que aquest és l\'element que funciona en mode
*scroll*. En aquest mateix component també desseleccionem el camp
Horitzontal, perquè l'*scroll* només sigui vertical. Amb tot això, si
quan executem el joc posem un text molt llarg, podrem desplaçar-lo
arrossegant el contingut amb el ratolí. D\'altra banda, és habitual
definir barres de *scroll* per poder operar d\'una manera més intuïtiva.

![](images/part4/scrollrect.png)

Per comoditat, se solen posar les barres als costats, per poder fer el
desplaçament de manera fàcil. Això es pot fer afegint un objecte UI \>
Scrollbar al Canvas, que representa una barra de desplaçament.
Inicialment, se\'ns mostrarà una barra horitzontal, que no és adequada
per al nostre disseny. En el camp Direction, al component Scrollbar,
podem seleccionar el sentit de la barra. En el nostre cas ens interessa
Bottom To Top.

Ara hem d\'assignar aquest GameObject al camp Vertical Scrollbar del
component Scroll Rect que hem creat. Finalment, ajustem la grandària i
la posició de la barra de *scroll* perquè quedi situada còmodament a la
part dreta. Amb totes aquestes operacions hauríem de tenir un text amb
desplaçament, i provar-ne el funcionament correcte prement Play.

![](images/part4/scrollbar.png)


En general, és una bona idea tenir els GameObjects ben organitzats i per
categories. En aquest sentit, de vegades convé tenir GameObjects buits
(*empty*), que no tenen cap funció en el joc però que fan possible
agrupar altres objectes de manera que formin una estructura que permeti
tenir ordenats els elements de joc per grups. Això millora la
llegibilitat del projecte.

| **Repte 6** |
| ---    |
| Reorganitzeu la jerarquia utilitzant objectes buits, de manera que al final quedi tot ordenat segons la figura de sota. Dividirem els elements de la pantalla de joc segons dos apartats: StorySection i AnswersSection. |

![](images/part4/organization.png)

## 4.3.2. Control del joc

Ara que ja tenim tots els elements de la UI, ja podem començar a crear
la lògica del joc. Quan tractem lògica que no està clarament associada a
un objecte concret en la interfície (per exemple, els botons de la
pantalla d\'inici), el normal és crear un GameObject buit que serveixi
com a controlador o gestor del joc; aquest GameObject buit no té
visualització a pantalla, només serveix per a agrupar certs *scripts*
generals. En aquest cas, anomenarem a aquest objecte *GameplayManager* i
contindrà l'*script* amb el codi.

L\'estratègia que cal seguir per controlar el joc serà la següent. Si bé
podríem generar tantes pantalles com localitzacions té el nostre joc (si
el nostre joc té deu localitzacions, crearem deu escenes en el
projecte), atès que totes les pantalles tindran un aspecte idèntic
excepte pel que fa al text explicatiu i a les opcions disponibles, el
que farem és treballar sobre una sola pantalla de joc i canviar el
contingut dels quadres de text segons correspongui. No té sentit anar
replicant exactament la mateixa escena, ja que seria una feina summament
tediosa i ineficient.

> Les localitzacions del joc es correspondrien, de fet, a les pàgines
> d\'un llibre de *Tria la teva aventura*.

Per a generar el codi que controli les diferents localitzacions del joc,
el punt de partida serà una estructura de dades en forma de graf dirigit
que representi el mapa de localitzacions. Cada vèrtex és una
localització i les seves arestes sortints són les diferents opcions,
cadascuna apuntant al seu vèrtex destí.

El codi de l'*script* que defineix aquesta estructura de dades serà el
següent:

```csharp
using System;

public class StoryNode
{
    public string History;
    public string[] Answers;
    public bool IsFinal;
    public StoryNode[] NextNode;
    public Action OnNodeVisited;
}

```

Aquest *script* defineix una estructura de dades anomenada *StoryNode*.
A partir d\'aquesta, generarem el graf i tot el contingut de les
localitzacions. Els seus atributs són:

-   **History:** el text que descriu la localització.

-   **Answers\[\]:** la llista de textos amb les respostes possibles.

-   **IsFinal:** indica que aquest node correspon a un final, on acaba
    l\'aventura.

-   **NextNode\[\]:** la llista de nodes destí, en el mateix ordre que
    en la llista de respostes. És a dir, si es tria la resposta en
    l\'índex 1 d\'*answers*, el jugador es desplaçarà al node indicat
    per *nextNode\[1\].*

-   **OnNodeVisited:** permet assignar una referència a un mètode
    delegat que s\'executarà sempre que es visiti aquesta localització.
    Aquesta estratègia permet executar codi que manipuli el mapa en
    arribar a certes localitzacions.

**Modificant el mapa en temps d\'execució**


En alguns moments del joc serà necessari modificar el mapa en temps
d\'execució. Per exemple, una ubicació pot tenir una porta tancada, que
només es podrà obrir si s\'ha agafat la clau corresponent.

En un llibre de *Tria la teva aventura*, això es resol normalment amb un
text de l\'estil «Si tens la clau, ves a la pàgina...; en cas contrari,
ves a la pàgina...». En el nostre joc, l\'estratègia és la següent. Es
crearan dos nodes: un que indica que la porta no es pot obrir (N1) i un
altre que representa que s\'obre amb èxit (N2). Inicialment, el node
assignat a *nextNode* a l\'opció d\'obrir la porta és N1. Serà en la
localització que representa que s\'agafa la clau on assignarem el mètode
prim que reemplaci N2 per N2, de manera que, a partir de llavors, en
arribar a la porta, l\'acció d\'obrir tindrà èxit automàticament.

A més, a la classe GameplayManager hi ha l\'atribut CurrentNode, que
indicarà en tot moment en quin node està actualment el jugador. El valor
que se li assigni en iniciar el joc serà la primera localització.

La nostra primera tasca serà inicialitzar el mapa de localitzacions. En
aquest exemple, per simplificar, ho farem de manera estàtica directament
mitjançant codi. Evidentment, aquesta solució no és escalable ni la
millor en un projecte real. Seria millor carregar-lo des d\'un fitxer de
dades estructurat, per exemple. No obstant això, la nostra opció de
vegades és una bona manera de generar prototips ràpidament per comprovar
que tot funciona; més tard es pot reformular si es considera necessari.

La inicialització la durà a terme un altre *script* que anomenarem
*StoryFiller* i que definirà una classe auxiliar que no s\'assignarà a
cap objecte. D\'aquesta manera se separa la gestió del joc de la càrrega
de dades, i es manté així el principi d\'encapsulació de codi.

> Noteu que StoryFiller no hereta de MonoBehaviour, ja que no és
> necessari.

```csharp
public static class StoryFiller
{
    public static StoryNode FillStory()
    {
        // Código de inicialización.
    }
}

```

El seu valor de tornada és el node inicial, que serà la primera
localització del joc.


| **Repte 7** |
| ---    |
| Empleneu el codi del mètode FillStory de manera que genereu un mapa de localitzacions per al joc. Serà necessari anar creant els nodes dinàmicament i inicialitzar els seus atributs d\'alguna manera.


Quan tenim el codi que carrega el mapa del joc, podem implementar
l'*script* GameplayManager, que és el que realment gestionarà la
pantalla de joc. La seva funció principal serà actualitzar la interfície
d\'usuari amb les dades associades a la ubicació actual del jugador.
Principalment, actualitzar els textos en pantalla, eliminar els botons
actuals i crear els nous que corresponguin, segons el nombre d\'accions
disponibles en aquesta localització.

Per destruir i crear objectes dinàmicament, Unity ofereix dos mètodes.
D\'una banda, Destroy elimina l\'objecte passat com a paràmetre.
D\'altra banda, Instantiate crea objectes a partir d\'un de ja existent,
que és replicat. En aquest cas, els seus paràmetres són una referència a
l\'objecte que cal copiar, la seva posició i la seva rotació. Val la
pena destacar que aquest mètode genera còpies d\'objectes, no els crea
realment des de zero. Normalment el que es fa no és copiar realment un
objecte ja preexistent a la Hierarchy (fet que podria ser un problema si
no hi ha cap altre objecte del mateix tipus encara creat), sinó usar un
*prefab*.

> Podeu veure tots els detalls de tots dos mètodes a la documentació
> oficial.

**Accedint a *prefabs* des del codi d\'un *script***

Els *prefabs* es creen des de la pantalla de l\'editor i es guarden en
forma d\'*asset* a l\'apartat Project. Una manera molt senzilla perquè
el vostre codi pugui accedir a aquesta *prefab* és la següent.
Primerament, crear un atribut públic de tipus GameObject en el vostre
*script*. Això fa que a l\'Inspector, dins del component Script,
aparegui un camp assignable. Llavors, arrossegar el *prefab* de Project
a aquest apartat. A partir d\'aquest moment, sempre que s\'executi
l'*script*, en aquest atribut estarà disponible el *prefab*.

En general, recordeu que tot atribut declarat públic en el codi d'un
*script* apareix com un apartat assignable en el seu component a
l\'editor, que pot ser inicialitzat arrossegant l\'element corresponent.
Per exemple, si volem tenir una manera d\'accés fàcil a un element de la
UI (1) o a algun dels seus components, podem fer exactament el mateix.
Només caldrà definir l\'atribut del tipus que correspongui (per exemple,
Text per a un camp de text, Transform per a una component Transform,
etc.). Unity disposa de tipus de dades per pràcticament tots els
elements associats a objectes a l\'editor.

(1) Les classes que representen els elements d\'una UI a Unity són a
    > la biblioteca UNITYENGINE.UI.

Quan hem creat un objecte a partir d\'un *prefab*, segurament voldrem
personalitzar-ne algunes de les propietats. Per a fer-ho, haurem de
modificar els seus components, també dinàmicament. Per accedir a un
component d\'un GameObject és necessari invocar el seu mètode
GetComponent(). Per exemple, per accedir al component RectTransform
d\'un element d\'UI, s\'executaria GetComponent\< RectTransform\>().
Quan es disposa del component, és possible accedir i manipular totes les
seves propietats mitjançant els mètodes i atributs públics que ofereix.

Un altre aspecte que haurem de gestionar dinàmicament és afegir
*listeners* a elements d\'UI (en aquest cas, els nous botons), de manera
que cada nou botó ens desplaci a la ubicació que correspongui. En aquest
sentit, els components d\'UI que esperen *listeners* disposen
d\'atributs que permeten assignar referències a mètodes. Per exemple, el
component Button disposa de la variable onClick, que al seu torn disposa
del mètode AddListener.

> Recordeu que el *listener* s\'afegeix a un component Button d\'un
> GameObject, no a l\'objecte en si.

Un exemple de codi associat a aquesta operació seria:

```csharp
var button = obj.GetComponent<Button>();
button.onClick.AddListener(() =>
{
    // Código del listener.
});

```

> Bàsicament, és la mateixa sintaxi que en els mètodes delegats.

Finalment, un altre mecanisme molt útil a l\'hora de gestionar objectes
per mitjà d\'un *script* és poder recórrer els elements de la seva
jerarquia d\'acord amb l\'estructura mostrada a la Hierarchy de
l\'editor. Aquesta tasca es pot dur a terme mitjançant el component
Transform d\'un objecte:

```csharp
var parent = obj.GetComponent<Transform>();
foreach (Transform child in parent)
{
    // Codi que manipula els seus fills via la variable child.
}

```


> Recordeu que tota manipulació del component Transform d\'un objecte
> s\'hereta a tots els fills en la jerarquia.

Relacionat amb aquest mecanisme de recorregut, el component Transform
posseeix també l\'atribut *parent*, que conté el seu pare en la
jerarquia. Assignant el valor corresponent és possible crear relacions
pare-fill.

> L\'atribut gameObject conté l\'objecte associat al Transform en
> qüestió.

| **Repte 8** |
| ---    |
|Completeu la classe GameplayManager. Primer, ha d\'encarregar-se de generar el mapa a l\'inici de la partida. Penseu quin mètode ha d\'incorporar aquest codi. Immediatament després, ha d\'inicialitzar la UI amb les dades de la primera ubicació. A partir d\'aquí, ha d\'encarregar-se d\'actualitzar la ubicació del personatge i mostrar les noves dades a la UI cada vegada que es prem algun dels botons que enumeren les accions disponibles. |


--> <a href="Parte4-4.md">Pàgina següent</a>
