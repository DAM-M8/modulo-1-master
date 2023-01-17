<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


# 3. *Scripting* en Unity


Si bien Unity permite gestionar el comportamiento de los GameObjects
hasta cierto punto por medio del editor, el caso más habitual será el de
programar la lógica de nuestro juego con fragmentos de código fuente,
llamados *scripts*.

> Un ***script*** en Unity es un componente más que podemos definir
> nosotros, siempre asociado a un GameObject concreto.

El lenguaje de programación que utiliza Unity es C\#. Los *scripts* de
Unity son clases que heredan de la superclase MonoBehaviour, definida
por el propio motor, y que sirve como interfaz para poder implementar
varias funciones a las que se llama internamente desde Unity, mediante
su redefinición (*override*). Los métodos más importantes y que usaremos
más a menudo son los siguientes:

-   **Awake** y **Start:** se invocan al iniciarse por primera vez el
    *script*, una sola vez.

-   **OnEnable:** se invoca cuando se habilita el objeto.

-   **OnDisable:** se invoca cuando se deshabilita el objeto.

-   **OnDestroy:** se invoca cuando se destruye el objeto.

-   **Update:** se invoca una vez por cada *frame* de ejecución.

Si exploramos la documentación oficial de Unity, veremos que la lista es
en realidad mucho más amplia. Aunque podemos encontrar toda la
información en dicha documentación, en esta sección vamos a describir
brevemente cuándo se ejecuta cada método y su caso de uso más común,
además de las convenciones que vamos a utilizar a la hora de programar
en Unity.

> Podéis encontrar la documentación oficial de la clase MonoBehaviour
> [aquí](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html).

Históricamente, Unity no ha seguido fielmente las convenciones estándar
de C\# establecidas originalmente por Microsoft. Sí lo está haciendo más
recientemente, así que en el curso también lo haremos. Los puntos
básicos de esta convención son los siguientes:

-   Los nombres de clases y métodos son CamelCase.

-   Los nombres de propiedades y variables públicas son CamelCase.

-   Los nombres de variables privadas comienzan por minúscula.

-   No se utilizan nunca prefijos del tipo CMiTipo o
    m\_miVariablePrivada.

Un punto que hay que destacar es que Unity nos obliga a que los ficheros
de *script* se llamen igual que la clase que contienen.

## Consideraciones sobre el *scripting* en Unity


A los programadores más experimentados les puede sorprender el hecho de
que no haya que usar *keywords* como *override* o que las llamadas a
métodos como Start o Update puedan tener firmas distintas (pueden
ser públicos, privados, pueden retornar datos o no, etc.). El motivo de
que esto se pueda hacer es que el motor no hace llamadas directas a
estos métodos, sino que usa *reflection*. Esta flexibilidad tiene un
coste asociado en términos de rendimiento, ya que llamar a un método
mediante *reflection* es más caro que hacer una llamada directa.


--> <a href="Parte3-1.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)

## 3. *Scripting* a Unity


Si bé Unity permet gestionar el comportament dels GameObjects fins a
cert punt per mitjà de l\'editor, el cas més habitual serà el de
programar la lògica del nostre joc amb fragments de codi font, anomenats
*scripts*.

> Un ***script*** a Unity és un component més que podem definir
> nosaltres, sempre associat a un GameObject concret.

El llenguatge de programació que utilitza Unity és C\#. Els *scripts* de
Unity són classes que hereten de la superclasse MonoBehaviour, definida
pel propi motor, i que serveix com a interfície per poder implementar
diverses funcions a les quals es crida internament des de Unity,
mitjançant la seva redefinició (*override*). Els mètodes més importants
i que usarem més sovint són els següents:

-   **Awake** i **Start:** s\'invoquen en iniciar-se per primera vegada
    l'*script*, una sola vegada.

-   **OnEnable:** s\'invoca quan s\'habilita l\'objecte.

-   **OnDisable:** s\'invoca quan es deshabilita l\'objecte.

-   **OnDestroy:** s\'invoca quan es destrueix l\'objecte.

-   **Update:** s\'invoca una vegada per cada *frame* d\'execució.

Si explorem la documentació oficial de Unity, veurem que la llista és en
realitat molt més àmplia. Encara que podem trobar tota la informació en
aquesta documentació, en aquesta secció descriurem breument quan
s\'executa cada mètode i el seu cas d\'ús més comú, a més de les
convencions que utilitzarem a l\'hora de programar amb Unity.

> Podeu trobar la documentació oficial de la classe MonoBehaviour
> [aquí](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html).

Històricament, Unity no ha seguit fidelment les convencions estàndard de
C\# establertes originalment per Microsoft. Sí que ho està fent més
recentment, així que en el curs també ho farem. Els punts bàsics
d\'aquesta convenció són els següents:

-   Els noms de classes i mètodes són CamelCase.

-   Els noms de propietats i variables públiques són CamelCase.

-   Els noms de variables privades comencen per minúscula.

-   No s\'utilitzen mai prefixos del tipus CElmeuTipus o
    m\_lamevaVariablePrivada.

Un punt que cal destacar és que a Unity és obligatori que els fitxers de
*script* s'anomenin igual que la classe que contenen.

## Consideracions sobre l'*scripting* a Unity

Als programadors més experimentats els pot sorprendre el fet que no
calgui usar *keywords* com *override* o que les crides a mètodes com
Start o Update puguin tenir signatures diferents (poden ser públics,
privats, poden retornar dades o no, etc.). El motiu que això es pugui
fer és que el motor no fa crides directes a aquests mètodes, sinó que
utilitza *reflection*. Aquesta flexibilitat té un cost associat en
termes de rendiment, ja que cridar a un mètode mitjançant *reflection*
és més car que fer una crida directa.


--> <a href="Parte3-1.md">Pàgina següent</a>
