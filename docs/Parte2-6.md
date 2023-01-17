
<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)

## 2.6. *Prefabs*


Es muy habitual durante el desarrollo de un proyecto tener estructuras
que se repiten a menudo. Por ejemplo, los enemigos se suelen controlar
por medio de uno o varios *scripts* y, si tenemos cientos de ellos en
una pantalla, hay que añadírselos a todos uno a uno. Huelga decir que
añadir todos los *scripts* con todas las configuraciones para cada uno
puede ser terriblemente tedioso; además, es muy probable que nos
equivoquemos en algún momento. Incluso podría ser peor si en un momento
más avanzado del desarrollo decidimos hacer algún cambio y tenemos que
repetir el proceso de nuevo: deberíamos asegurarnos de que modificamos
absolutamente todos los enemigos. Para evitar este tipo de problemas,
Unity tiene un sistema llamado ***prefab***.

> Podemos imaginarnos un ***prefab*** como una plantilla donde guardamos
> el estado actual de un objeto y sus componentes. Esta plantilla se
> puede usar para instanciar objetos sin límite en cualquier escena del
> proyecto. Cualquier cambio hecho al *prefab* original afecta a todas
> sus instancias.

No estamos obligados a que todos los objetos sean copias exactas. Una
vez se ha creado un objeto a partir del *prefab*, podemos personalizar
cada instancia individualmente si lo deseamos. Por ejemplo, para el caso
anterior, podríamos hacer que la mayoría de enemigos tengan la misma
velocidad, pero que uno en concreto sea más rápido, aun cuando comparta
el resto de propiedades exactamente.

Existen diversas maneras de crear un *prefab*, pero una relativamente
simple es la siguiente:

-   Crear el GameObject que deseamos convertir en *prefab* en el
    editor. Asignar todas las propiedades deseadas hasta tenerlo a
    punto.

-   Arrastrar dicho objeto desde el apartado de Hierarchy al de
    Project.

-   Al hacerlo, veremos que aparece un nuevo *asset* con el nombre
    remarcado en color azul (en vez de negro, que es el habitual). Esto
    indica que se trata de un *prefab*.

-   Para crear una instancia, basta con arrastrar el *prefab* desde
    Project hasta Hierarchy, o bien directamente sobre la escena
    actual.

Para modificar las propiedades de todas las instancias a la vez, basta
con seleccionar el *prefab* y editar los valores apropiados en la
pestaña Inspector.

> Es recomendable guardar todos los *prefabs* de nuestro proyecto en la
> carpeta Prefabs.


--> <a href="Parte3.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)

## 2.6. *Prefabs*

És molt habitual durant el desenvolupament d\'un projecte tenir
estructures que es repeteixen sovint. Per exemple, els enemics se solen
controlar per mitjà d\'un o diversos *scripts* i, si tenim en centenars
en una pantalla, cal afegir-los tots un a un. Cal dir que afegir tots
els *scripts* amb totes les configuracions per a cadascun pot ser
terriblement tediós; a més, és molt probable que ens equivoquem en algun
moment. Fins i tot podria ser pitjor si en un moment més avançat del
desenvolupament decidim fer algun canvi i hem de repetir el procés de
nou: hauríem d\'assegurar-nos que modifiquem absolutament tots els
enemics. Per evitar aquest tipus de problemes, Unity té un sistema
anomenat ***prefab***.

> Podem imaginar-nos un ***prefab*** com una plantilla on guardem
> l\'estat actual d\'un objecte i els seus components. Aquesta plantilla
> es pot emprar per instanciar objectes sense límit en qualsevol escena
> del projecte. Qualsevol canvi fet *al prefab* original afecta totes
> les seves instàncies.

No és obligatori que tots els objectes siguin còpies exactes. Una vegada
s\'ha creat un objecte a partir del *prefab*, podem personalitzar cada
instància individualment si ho desitgem. Per exemple, per al cas
anterior, podríem fer que la majoria d\'enemics tinguin la mateixa
velocitat, però que un en concret sigui més ràpid, tot i que comparteixi
la resta de propietats exactament.

Hi ha diverses maneres de crear un *prefab*, però una de relativament
simple és la següent:

-   Crear el GameObject que desitgem convertir en *prefab* a l\'editor.
    Assignar totes les propietats desitjades fins a tenir-lo a punt.

-   Arrossegar aquest objecte des de l\'apartat de Hierarchy al de
    Project.

-   Quan ho fem, veurem que apareix un nou *asset* amb el nom remarcat
    en color blau (en comptes de negre, que és l\'habitual). Això indica
    que es tracta d\'un *prefab*.

-   Per crear una instància, n\'hi ha prou amb arrossegar el *prefab*
    des de Project fins a Hierarchy, o bé directament sobre l\'escena
    actual.

Per modificar les propietats de totes les instàncies alhora, n\'hi ha
prou a seleccionar el *prefab* i editar els valors apropiats a la
pestanya Inspector.

> És recomanable guardar tots els *prefabs* del nostre projecte a la
> carpeta Prefabs.


--> <a href="Parte3.md">Pàgina següent</a>
