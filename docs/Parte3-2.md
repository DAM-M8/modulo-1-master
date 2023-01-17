
<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)


# 3.2. Métodos importantes en Unity


Los motores de juegos nos proporcionan maneras de programar lo que
queremos hacer durante la inicialización del juego y durante cada
*frame* del mismo. En el caso de Unity, el motor se encarga de llamar en
los momentos adecuados a los métodos Start y Update, entre otros, de los
*scripts* asociados a cada GameObject de la escena actual. De este modo,
podemos controlar lo que ocurre en cada instante de nuestro juego. A
continuación, veremos en detalle cómo se usan estos métodos con algunos
ejemplos prácticos.

## 3.2.1. Awake y Start

Estos métodos se ejecutan una sola vez por componente del objeto.
Específicamente, justo después de crear dicho componente. En estos
métodos vamos a encontrar, habitualmente, código relacionado con la
inicialización del componente. Incluyendo también el almacenamiento de
datos por motivos de rendimiento (normalmente, para no tener que
ejecutar llamadas o cálculos costosos cada *frame* sino hacerlo una sola
vez al principio). La diferencia entre Awake y Start es que utilizaremos
el primero para la inicialización local del componente y el segundo para
la inicialización externa del mismo (esto es, cálculos o llamadas
relacionados con otros objetos). El Awake siempre se ejecuta antes del
Start.

Veamos un pequeño ejemplo de *script*:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Awake()
    {
        Debug.Log("Hello world, from Awake!");
    }
    
    private void Start()
    {
        Debug.Log("Hello world, from Start!");
    }
}
```

> El método Debug.Log permite escribir texto por la consola durante la
> ejecución de un *script* de Unity.

Como ya habíamos comentado anteriormente, nuestro *script* de ejemplo es
una clase que hereda de MonoBehaviour, que es una clase definida
internamente por Unity. Esta clase la hemos llamado ExampleClass y
contiene dos métodos. El objeto que contenga este *script* escribirá una
sola vez por consola, al inicio de la ejecución, los mensajes de texto
"Hello world, from Awake!" y "Hello world, from Start!", en ese
orden.

Como comentamos anteriormente, es importante que el *script* que
contenga esta clase se llame igual que esta (es decir, ExampleClass.cs).

## 3.2.2. Update


Este método es uno de los más importantes porque se ejecuta una vez por
*frame*, justo antes de mostrar la imagen final resultante en pantalla.

Es muy importante que esta función sea lo más óptima posible. Es muy
fácil incurrir en costes excesivos que afecten a la experiencia final
del juego; por ejemplo, realizando operaciones complejas cada *frame*
que podrían realizarse una única vez en tiempo de inicialización, a lo
largo de varios *frames* o cada cierto número de *frames*.

Veamos un ejemplo sencillo de *script* con la función Update:


```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        Debug.Log("Updating...");
    }
}
```

Este *script* escribe el mensaje "Updating..." en cada *frame* y por
cada GameObject al cual esté añadido. Así pues, si nuestro juego se
ejecuta a 30 FPS, el mensaje se escribirá treinta veces por segundo.

## 3.2.3. OnEnable y OnDisable

Estas funciones se ejecutan cada vez que un *script* se activa
(incluyendo el momento en que el *script* se añade a un objeto) o se
desactiva. Puede tener sentido desactivar temporalmente un *script* si
queremos que deje de ejecutar su código momentáneamente. En caso de
querer que el *script* deje de ejecutarse definitivamente, lo más
adecuado es eliminarlo mediante el editor o vía programación con el
método
[Destroy](https://docs.unity3d.com/ScriptReference/Object.Destroy.html).

> Un *script* se activa o desactiva mediante el *checkbox* de la lista
> de componentes del Inspector.

Veamos un ejemplo:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void OnEnable()
    {
        Debug.Log("Script was enabled.");
    }
    
    private void OnDisable()
    {
        Debug.Log("Script was disabled.");
    }
}
```
En este caso, al entrar en modo ejecución veremos el mensaje "Script
was enabled" en la consola de Unity. Si vamos al Inspector y hacemos
clic en el *checkbox* que activa/desactiva el *script*, veremos por
consola que cada vez que activamos el *script* se nos muestra el mensaje
"Script was enabled" y que cuando desactivamos el *script* se nos
muestra "Script was disabled".

Al salir del modo ejecución también veremos el mensaje "Script was
disabled", ya que, justo antes de salir de este modo, todos los
componentes llaman a su OnDisable.

--> <a href="Parte3-3.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)



# 3.2. Mètodes importants a Unity


Els motors de jocs ens proporcionen maneres de programar el que volem
fer durant la inicialització del joc i durant cada *frame*. En el cas de
Unity, el motor s\'encarrega de cridar en els moments adequats els
mètodes Start i Update, entre d'altres, dels *scripts* associats a cada
GameObject de l\'escena actual. D\'aquesta manera, podem controlar el
que passa a cada instant del nostre joc. A continuació, veurem
detalladament com s\'usen aquests mètodes amb alguns exemples pràctics.

## 3.2.1. Awake i Start

Aquests mètodes s\'executen una sola vegada per component de l\'objecte.
Específicament, just després de crear aquest component. En aquests
mètodes habitualment hi ha codi relacionat amb la inicialització del
component. S'hi inclou també l\'emmagatzematge de dades per motius de
rendiment (normalment per no haver d\'executar crides o càlculs costosos
cada *frame* i fer-ho una sola vegada al principi). La diferència entre
Awake i Start és que utilitzarem el primer per a la inicialització local
del component i el segon per a la inicialització externa d'aquest
component (és a dir, càlculs o crides relacionats amb altres objectes).
L\'Awake sempre s\'executa abans del Start.

Vegem un petit exemple de *script*:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Awake()
    {
        Debug.Log("Hello world, from Awake!");
    }
    
    private void Start()
    {
        Debug.Log("Hello world, from Start!");
    }
}
```

> El mètode Debug.Log permet escriure text per la consola durant
> l\'execució d\'un *script* de Unity.

Com ja havíem comentat anteriorment, el nostre *script* d\'exemple és
una classe que hereta de MonoBehaviour, que és una classe definida
internament per Unity. Aquesta classe l\'hem anomenat ExampleClass i
conté dos mètodes. L\'objecte que contingui aquest *script* escriurà una
sola vegada per consola, a l\'inici de l\'execució, els missatges de
text «Hello world, from Awake!» i «Hello world, from Start!», en aquest
ordre.

Com hem comentar anteriorment, és important que l'*script* que contingui
aquesta classe es digui igual que aquesta (és a dir, Exampleclass.cs).

## 3.2.2. Update



Aquest mètode és un dels més importants perquè s\'executa una vegada per
*frame*, just abans de mostrar la imatge final resultant a pantalla.

És molt important que aquesta funció sigui al més òptima possible. És
molt fàcil incórrer en costos excessius que afectin l\'experiència final
del joc; per exemple, realitzant operacions complexes cada *frame* que
podrien realitzar-se una única vegada en temps d\'inicialització, al
llarg de diversos *frames* o cada cert nombre de *frames*.

Vegem un exemple senzill de *script* amb la funció Update:


```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        Debug.Log("Updating...");
    }
}
```

Aquest *script* escriu el missatge «Updating...» a *cada frame* i per
cada GameObject al qual estigui afegit. Així doncs, si el nostre joc
s\'executa a 30 FPS, el missatge s\'escriurà trenta vegades per segon.

## 3.2.3. OnEnable i OnDisable

Aquestes funcions s\'executen cada vegada que un *script* s\'activa
(incloent-hi el moment en què l'*script* s\'afegeix a un objecte) o es
desactiva. Pot tenir sentit desactivar temporalment un *script* si volem
que deixi d\'executar el seu codi momentàniament. En cas de voler que
l'*script* deixi d\'executar-se definitivament, el més adequat és
eliminar-lo mitjançant l\'editor o via programació amb el mètode
[Destroy](https://docs.unity3d.com/ScriptReference/Object.Destroy.html).

> Un *script* s\'activa o desactiva mitjançant el *checkbox* de la
> llista de components de l\'Inspector.

Vegem-ne un exemple:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void OnEnable()
    {
        Debug.Log("Script was enabled.");
    }
    
    private void OnDisable()
    {
        Debug.Log("Script was disabled.");
    }
}
```
En aquest cas, quan entrem en mode execució veurem el missatge «Script
was enabled» a la consola de Unity. Si anem a l\'Inspector i fem clic al
*checkbox* que activa/desactiva l'*script*, veurem per consola que cada
vegada que activem l'*script* se\'ns mostra el missatge «Script was
enabled» i que quan desactivem l'*script* se\'ns mostra «Script was
disabled».

Quan sortim del mode execució també veurem el missatge "Script was
disabled», ja que, just abans de sortir d'aquest mode, tots els
components criden el seu OnDisable.

--> <a href="Parte3-3.md">Pàgina següent</a>
