<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


# 4.5. Incorporación de efectos de sonido

El sonido es una parte fundamental en la gran mayoría de juegos. Muchos
jugadores recuerdan perfectamente tanto la música de fondo como los
efectos sonoros de sus juegos favoritos. Por lo tanto, es un aspecto que
no debemos olvidar durante el desarrollo. Unity nos ofrece una gran
cantidad de herramientas para poder dotar a nuestro proyecto de un
sonido de calidad. Vamos a dar un pequeño repaso de cuáles son estas
herramientas antes de añadir el sonido a nuestro proyecto.

> Todos los *assets* de sonido que importemos a nuestro proyecto
> (ficheros .mp3, .ogg, entre otros) se convierten en **Audio Clips**
> (clips de audio). De esta manera, abstraemos el tipo de fichero y su
> compresión, y trabajamos con el sonido de una manera unificada.

El elemento básico para generar sonidos es el componente AudioSource,
con el que podemos hacer sonar un *Audio Clip* asignado a la propiedad
correspondiente. El origen del sonido estará allí donde esté situado el
GameObject con dicho componente. En este tipo de componente, por
defecto, la opción Play On Awake de los AudioSource está activada.
Esto provoca que el sonido se ponga en marcha en el momento en que se
crea el objeto, lo que puede ser adecuado para música de fondo, pero no
para efectos de sonido en momento puntuales (conviene desactivarla). La
opción más importante es el Audio Clip que le asignamos para que se
escuche, y también si queremos que se repita automáticamente, lo que se
consigue mediante la opción Loop.

> Añadiremos un AudioSource como componente a los objetos que generan
> sonidos.

Otro aspecto que hay que tener en cuenta es el componente que indica a
Unity desde dónde queremos escuchar los sonidos: el AudioListener. En
este sentido, hay que tener en cuenta que Unity hace una simulación de
la propagación del sonido a través del espacio, de manera que lo que
esté más lejos sonará más flojo. De todos modos, este *component* se
añade normalmente en el mismo GameObject en el que está la cámara, de
la misma manera que nuestros ojos y nuestras orejas están cerca los unos
de los otros. Una escena suele tener como máximo uno activado a la vez.

> El resto de propiedades de AudioSource y AudioListener lo podéis
> consultar en la documentación de Unity
> ([aquí](https://docs.unity3d.com/ScriptReference/AudioSource.html) y
> [aquí](https://docs.unity3d.com/Manual/class-AudioListener.html),
> respectivamente).

De cara a aplicar estos componentes en nuestro proyecto, primero será
necesario explorar nuestros recursos para obtener sonidos. Un buen punto
de partida es el Asset Store, buscando sonidos de ambiente gratuitos.

| **Reto 11** |
| ---    |
| Añadid una música de fondo para cada una de las pantallas del juego. De cara a generar los sonidos, podéis ubicar su origen (AudioSource) en la propia cámara, junto con el AudioListener. |


--> <a href="Parte4-6.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)

# 4.5. Incorporació d'efectes de so

El so és una part fonamental en la gran majoria de jocs. Molts jugadors
recorden perfectament tant la música de fons com els efectes sonors dels
seus jocs favorits. Per tant, és un aspecte que no hem d\'oblidar durant
el desenvolupament. Unity ens ofereix una gran quantitat d\'eines per
poder dotar el nostre projecte d\'un so de qualitat. Farem un petit
repàs de quines són aquestes eines abans d\'afegir el so al nostre
projecte.

> Tots els *assets* de so que importem al nostre projecte (fitxers .mp3,
> .ogg, entre d'altres) es converteixen en **Àudio Clips** (clips
> d\'àudio). D\'aquesta manera, abstraiem el tipus de fitxer i la seva
> compressió, i treballem amb el so d\'una manera unificada.

L\'element bàsic per generar sons és el component AudioSource, amb el
qual podem fer sonar un *Àudio Clip* assignat a la propietat
corresponent. L\'origen del so estarà allí on estigui situat el
GameObject amb aquest component. En aquest tipus de component, per
defecte, l\'opció Play On Awake dels AudioSource està activada. Això
provoca que el so s\'engegui en el moment en què es crea l\'objecte, la
qual cosa pot ser adequada per a música de fons, però no per a efectes
de so en moment puntuals (convé desactivar-la). L\'opció més important
és l\'Àudio Clip que li assignem perquè s\'escolti, i també si volem que
es repeteixi automàticament, fet que s\'aconsegueix mitjançant l\'opció
Loop.

> Afegirem un AudioSource com a component als objectes que generen sons.

Un altre aspecte que cal tenir en compte és el component que indica a
Unity des d\'on volem escoltar els sons: l\'AudioListener. En aquest
sentit, cal tenir en compte que Unity fa una simulació de la propagació
del so a través de l\'espai, de manera que el que estigui més lluny
sonarà més fluix. De totes maneres, aquest *component* s\'afegeix
normalment en el mateix GameObject en el qual hi ha la càmera, de la
mateixa manera que els nostres ulls i les nostres orelles estan a prop
els uns dels altres. Una escena sol tenir com a màxim un activat alhora.

> La resta de propietats d\'AudioSource i AudioListener les podeu
> consultar a la documentació de Unity
> ([aquí](https://docs.unity3d.com/ScriptReference/AudioSource.html) i
> [aquí](https://docs.unity3d.com/Manual/class-AudioListener.html),
> respectivament).

Per a aplicar aquests components al nostre projecte, primer serà
necessari explorar els nostres recursos per obtenir sons. Un bon punt de
partida és l\'Asset Store, on podem buscar sons d\'ambient gratuïts.

| **Reto 11** |
| ---    |
| Afegiu una música de fons per a cadascuna de les pantalles del joc. Per a generar els sons, podeu situar-ne l'origen (AudioSource) en la pròpia càmera, juntament amb l\'AudioListener. |

--> <a href="Parte4-6.md">Pàgina següent</a>
