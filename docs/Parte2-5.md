<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


## 2.5. Carpetas especiales


Unity no trata a todos los *assets* por igual, y la distinción la hace
según la carpeta en la que están ubicados. La razón es dar más
flexibilidad a los desarrolladores. Por ejemplo, podemos crear
funcionalidades que sirvan solo como herramientas para acelerar el
desarrollo dentro del editor, pero que no tengan sentido dentro del
juego. Este es un recurso muy típico al que se suele recurrir cuando los
juegos alcanzan un cierto nivel de complejidad. Pero no es el único. A
continuación, veremos algunas de las carpetas especiales de Unity más
relevantes y analizaremos su uso.

> Para obtener la información completa de todas las carpetas especiales,
> podemos acudir a la documentación oficial de Unity
> [aquí](https://docs.unity3d.com/Manual/SpecialFolders.html)

### 2.5.1. Carpeta Editor

Podemos generar fragmentos de código en forma de *scripts* que nos
ayuden a acelerar nuestro progreso a la hora de desarrollar nuestro
juego, pero que no se incluirán en el juego una vez exportado a alguna
plataforma concreta. De este modo, optimizamos espacio y evitamos
posibles problemas.

### 2.5.2. Carpeta Plug-ins

Algunas funcionalidades se crean de manera específica para alguna
plataforma. Otras veces, simplemente queremos reaprovechar módulos ya
existentes programados en otros entornos y otros lenguajes. En estos
casos, normalmente, se generan archivos binarios ejecutables que se
puedan llamar directamente desde un *script* de Unity. Para que Unity
los reconozca como *plug-ins*, hay que ponerlos en esta carpeta
especial.

> Algunos ejemplos de binarios ejecutables son los archivos .dll en
> Windows o .so en Android.

### 2.5.3. Carpeta Resources

Algunos *assets* pueden ser costosos en términos de memoria y puede que
solo los necesitemos en algunos momentos en concreto. Para evitar esta
carga innecesaria, podemos usar ciertas funciones de código para indicar
qué *asset* queremos instanciar. Eso sí, solo tendremos acceso vía
código a los *assets* que se encuentren en la carpeta Resources.

### 2.5.4. Carpeta de recursos en línea

Muchas veces nos encontraremos que necesitamos recursos para nuestro
juego. Especialmente si somos un equipo pequeño, es muy complicado tener
nociones suficientes de cómo generar animaciones, texturas, música y
modelos 3D con suficiente calidad. Sin embargo, en muchas ocasiones, lo
que necesitamos ya ha sido creado para otro proyecto, y podemos
obtenerlo por un precio ajustado o, incluso, gratuitamente.

> La Asset Store es la tienda oficial de Unity. Contiene todo tipo de
> recursos, desde texturas y *scripts* hasta animaciones o niveles
> completos de algún juego. Para descargar *assets* desde la tienda es
> necesario tener una cuenta de Unity.

En esta tienda podemos encontrar recursos gratis y de pago, así como en
modalidad de prueba. Podemos acceder a la *Asset Store* desde la web de
Unity o desde el propio editor, pero los *assets* que queramos utilizar
solo los podemos descargar desde el editor.

Más allá de la tienda oficial, hay multitud de recursos *online* que
podemos encontrar en diversas webs. Sin embargo, debemos ir siempre con
cuidado con los derechos de autor de todo aquello que nos planteemos
usar en nuestros proyectos.


--> <a href="Parte2-6.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)


## 2.5. Carpetes especials


Unity no tracta tots els *assets* de la mateixa manera, i la distinció
la fa segons la carpeta on estan situats. La raó és donar més
flexibilitat als desenvolupadors. Per exemple, podem crear
funcionalitats que serveixin només com a eines per accelerar el
desenvolupament dins de l\'editor, però que no tinguin sentit dins del
joc. Aquest és un recurs molt típic al qual se sol recórrer quan els
jocs aconsegueixen un cert nivell de complexitat. Però no és l\'únic. A
continuació, veurem algunes de les carpetes especials de Unity més
rellevants i n'analitzarem l'ús.

> Per obtenir la informació completa de totes les carpetes especials,
> podem acudir a la documentació oficial de Unity
> [aquí](https://docs.unity3d.com/Manual/SpecialFolders.html)

### 2.5.1. Carpeta Editor

Podem generar fragments de codi en forma de *scripts* que ens ajudin a
accelerar el nostre progrés a l\'hora de desenvolupar el nostre joc,
però que no s\'inclouran en el joc una vegada exportat a alguna
plataforma concreta. D\'aquesta manera, optimitzem espai i evitem
possibles problemes.

### 2.5.2. Carpeta Plug-ins

Algunes funcionalitats es creen de manera específica per a alguna
plataforma. Altres vegades, simplement volem reaprofitar mòduls ja
existents programats en altres entorns i altres llenguatges. En aquests
casos, normalment es generen arxius binaris executables que es puguin
cridar directament des d\'un *script* de Unity. Perquè Unity els
reconegui com a *plug-ins*, cal posar-los en aquesta carpeta especial.

> Alguns exemples de binaris executables són els arxius .dll a Windows
> o .so a Android.

### 2.5.3. Carpeta Resources

Alguns *assets* poden ser costosos en termes de memòria i pot ser que
només els necessitem en alguns moments concrets. Per evitar aquesta
càrrega innecessària, podem utilitzar certes funcions de codi per
indicar quin *asset* volem instanciar. Això sí, només tindrem accés via
codi als *assets* que estiguin a la carpeta Resources.

### 2.5.4. Carpeta de recursos en línia

Moltes vegades ens trobarem que necessitem recursos per al nostre joc.
Especialment, si som un equip petit és molt complicat tenir nocions
suficients de com generar animacions, textures, música i models 3D amb
qualitat suficient. Tanmateix, moltes vegades el que necessitem ja ha
estat creat per a un altre projecte, i podem obtenir-ho per un preu
ajustat o, fins i tot, gratuïtament.

> L\'Asset Store és la botiga oficial de Unity. Conté tot tipus de
> recursos, des de textures i *scripts* fins a animacions o nivells
> complets d\'algun joc. Per descarregar *assets* des de la botiga és
> necessari tenir un compte de Unity.

En aquesta botiga podem trobar-hi recursos gratuïts i de pagament, i
també en modalitat de prova. Podem accedir a l\'*Asset* *Store* des de
la web de Unity o des del propi editor, però els *assets* que vulguem
utilitzar només els podem descarregar des de l\'editor.

Més enllà de la botiga oficial, hi ha multitud de recursos *online* que
podem trobar en diverses webs. No obstant això, hem d\'anar sempre amb
cura amb els drets d\'autor de tot allò que ens plantegem emprar en els
nostres projectes.


--> <a href="Parte2-6.md">Pàgina següent</a>
