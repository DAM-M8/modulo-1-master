<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)

# 3.4. Clases auxiliares


Unity proporciona una extensa colección de librerías para facilitarnos
la programación de nuestros proyectos. En este apartado vamos a enumerar
brevemente las más relevantes, con el simple propósito de dar a conocer
su existencia; la explicación más detallada se encuentra en la
documentación oficial. En este sentido, los ejemplos incluidos solo
sirven para dar una visión más clara del propósito de cada clase.

## 3.4.1. La clase Input


Esta clase nos permite reconocer la entrada del jugador en varios
dispositivos (teclado, ratón, *gamepad*, pantalla táctil, etc.). Veamos
algunos ejemplos de cómo usar esta clase:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
            Debug.Log("Space key was pressed.");
    }
}
```

> **KeyCode** contiene toda una serie de constantes que definen las
> distintas teclas del teclado (Space, F1, Asterisk, A, etc.).

En este *script*, comprobamos en cada *frame* si el jugador ha pulsado
la tecla espaciadora en su teclado. De ser así, escribimos el mensaje
"Space key was pressed" en la consola. Nótese el uso del método
Update para poder reconocer la entrada del jugador en cada *frame*.

Veamos otro ejemplo:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        if (Input.touchCount > 0 && Input.GetTouch(0).phase == TouchPhase.Moved)
            Debug.Log("Screen was touched.");
    }
}
```

En este *script*, comprobamos en cada *frame* si el jugador ha movido el
dedo sobre la pantalla táctil de su dispositivo. De ser así, escribimos
el mensaje "Screen was touched" en la consola. Por supuesto, si el
dispositivo en cuestión no dispone de pantalla táctil, esto no ocurrirá
nunca. Para simular un dispositivo táctil, podemos descargar desde el 
package manager el paquete con el nombre "Device Simulator".

> [Device Simulator](https://docs.unity3d.com/Packages/com.unity.device-simulator@2.2/manual/index.html).

Para poder descargar el package del device simulator en la versión 2020.1.4f1 hay que acceder a Project Settings / Package Manager y activar el check “Enable Preview Packages”. 

![Seleccionar Advanced Project Setting](images/part2/device_simulator_1.png)

![Activar Preview Packages](images/part2/device_simulator_2.png)


*Input* es una clase muy extensa con multitud de funcionalidades.
Siempre que necesitemos obtener algún tipo de dato de interacción del
jugador no cubierta en este capítulo (giroscopio, brújula, localización,
etc.), podemos acudir a la documentación oficial de Unity.

> Podemos encontrar la documentación oficial de la clase *Input*
> [aquí](https://docs.unity3d.com/ScriptReference/Input.html).

### Consejos sobre Input en juegos dirigidos a múltiples plataformas

Unity es un motor multiplataforma, como lo son muchos juegos en la
actualidad. Si nuestro juego está dirigido a varias plataformas con
mecanismos de entrada diferentes, será necesario crear nuestra propia
capa de abstracción para detectar la entrada del usuario de la manera
adecuada según la plataforma (por ejemplo, con *gamepad* en consolas y
con los dedos sobre la pantalla táctil en móviles).

## 3.4.2. La clase Application

Esta clase nos permite acceder a una gran cantidad de información sobre
el dispositivo en el que se está ejecutando nuestro juego.

Veamos un ejemplo:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        Debug.Log($"The current platform is {Application.platform}");
        if (Application.platform == RuntimePlatform.WindowsPlayer)
            Debug.Log("The current platform is Windows.");
    }
}
```

> **RuntimePlatform** contiene toda una serie de constantes que definen
> las distintas plataformas disponibles en Unity (PC, PS4, iOS, etc.).

En este ejemplo, primero mostramos por consola la plataforma en la que
se está ejecutando el juego. Después, si se da el caso de que estamos en
Windows, enseñamos por pantalla un mensaje específico. Hay que tener en
cuenta que dentro del editor no estamos en RuntimePlatform.WindowsPlayer
sino en RuntimePlatform.WindowsEditor.

> Podemos encontrar la documentación oficial de la clase Application
> [aquí](https://docs.unity3d.com/ScriptReference/Application.html).

## 3.4.3. La clase Time


Programando la lógica de un juego, en muchas ocasiones queremos hacer
operaciones que no dependan del número de *frames* que el dispositivo es
capaz de obtener. Por ejemplo, una animación debería empezar y acabar en
el mismo momento, o un juego de carreras debería desplazar los coches
según la velocidad del vehículo y no según los FPS. Hay que tener en
cuenta que es bastante frecuente tener grandes variaciones en los FPS
que conseguimos, sobre todo cuando cambiamos de perspectiva en la escena
y hay partes con mucho detalle y otras muy simples. Para todo este tipo
de operaciones, tenemos a nuestra disposición la clase *Time*, que nos
permite controlar el tiempo que ha transcurrido entre diferentes
eventos, como puede ser entre dos *frames* consecutivos.

Veamos un ejemplo de uso:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        transform.Translate(0, 0, Time.deltaTime * 1);
    }
}
```


> El método **Transform.Translate** permite mover el GameObject
> asociado.
>
> **Time.deltaTime** indica el tiempo que ha transcurrido entre la
> ejecución del último *frame* y el actual.

Este *script* hace que el GameObject asociado se traslade una unidad
por segundo en el eje Z. En cada *frame* (de ahí que utilicemos el
método Update), el objeto se desplaza la cantidad de tiempo que ha
pasado entre dos *frames*. Si tenemos FPS muy altos, Time.deltaTime
será una cantidad muy pequeña a cada ejecución, por lo que el objeto se
moverá muy poco, y viceversa. Independientemente de los FPS, solo se
desplazará una unidad cuando haya pasado un segundo completo.

> La variable Time.deltaTime es de gran utilidad, ya que, usada como
> factor de corrección, permite ejecutar cualquier funcionalidad
> independientemente de los FPS reales del juego.
>
> Podemos encontrar la documentación oficial de la clase Time
> [aquí](https://docs.unity3d.com/ScriptReference/Time.html).





--> <a href="Parte3-5.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)

# 3.4. Classes auxiliars


Unity proporciona una extensa col·lecció de llibreries per facilitar-nos
la programació dels nostres projectes. En aquest apartat enumerarem
breument les més rellevants, amb el simple propòsit de donar-ne a
conèixer l'existència; l\'explicació més detallada està a la
documentació oficial. En aquest sentit, els exemples inclosos solament
serveixen per donar una visió més clara del propòsit de cada classe.

## 3.4.1. La classe Input


Aquesta classe ens permet reconèixer l\'entrada del jugador en diversos
dispositius (teclat, ratolí, *gamepad*, pantalla tàctil, etc.). Vegem
alguns exemples de com usar aquesta classe:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
            Debug.Log("Space key was pressed.");
    }
}
```

> **KeyCode** conté tot un seguit de constants que defineixen les
> diferents tecles del teclat (Space, F1, Asterisk, A, etc.).

En aquest *script*, comprovem a cada *frame* si el jugador ha premut la
tecla d'espai en el seu teclat. En aquest cas, escrivim el missatge
«Space key was pressed» a la consola. Noteu l\'ús del mètode Update per
a poder reconèixer l\'entrada del jugador a cada *frame*.

Vegem-ne un altre exemple:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        if (Input.touchCount > 0 && Input.GetTouch(0).phase == TouchPhase.Moved)
            Debug.Log("Screen was touched.");
    }
}
```

En aquest *script*, comprovem a cada *frame* si el jugador ha mogut el
dit sobre la pantalla tàctil del seu dispositiu. En aquest cas, escrivim
el missatge «Screen was touched» a la consola. Per descomptat, si el
dispositiu en qüestió no disposa de pantalla tàctil, això no passarà
mai.Per a simular un dispositiu tàctil, podem descarregar des del
package manager el paquet amb el nom "Device Simulator".

> [Device Simulator](https://docs.unity3d.com/Packages/com.unity.device-simulator@2.2/manual/index.html).


Per a poder descarregar el package del device simulator en la versió 2020.1.4f1 cal accedir a Project Settings / Package Manager i activar el check "Enable Preview Packages".

![Seleccionar Advanced Project Setting](images/part2/device_simulator_1.png)

![Activar Preview Packages](images/part2/device_simulator_2.png)

*Input* és una classe molt extensa amb multitud de funcionalitats.
Sempre que necessitem obtenir algun tipus de dada d\'interacció del
jugador no coberta en aquest capítol (giroscopi, brúixola, localització,
etc.), podem anar a la documentació oficial de Unity.

> Podem trobar la documentació oficial de la classe *Input*
> [aquí](https://docs.unity3d.com/ScriptReference/Input.html).

### Consells sobre Input en jocs dirigits a múltiples plataformes

Unity és un motor multiplataforma, com ho són molts jocs actualment. Si
el nostre joc es dirigeix a diverses plataformes amb mecanismes
d\'entrada diferents, serà necessari crear la nostra pròpia capa
d\'abstracció per detectar l\'entrada de l\'usuari de la manera adequada
segons la plataforma (per exemple, amb *gamepad* en consoles i amb els
dits sobre la pantalla tàctil en mòbils).

## 3.4.2. La classe Application

Aquesta classe ens permet accedir a una gran quantitat d\'informació
sobre el dispositiu en el qual s\'està executant el nostre joc.

Vegem-ne un exemple:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        Debug.Log($"The current platform is {Application.platform}");
        if (Application.platform == RuntimePlatform.WindowsPlayer)
            Debug.Log("The current platform is Windows.");
    }
}
```


> **RuntimePlatform** conté tot un seguit de constants que defineixen
> les diferents plataformes disponibles a Unity (PC, PS4, iOS, etc.).

En aquest exemple, primer mostrem per consola la plataforma en la qual
s\'està executant el joc. Després, si és el cas que estem a Windows,
ensenyem per pantalla un missatge específic. Cal tenir en compte que
dins de l\'editor no estem a RuntimePlatform.WindowsPlayer sinó a
RuntimePlatform.WindowsEditor.

> Podem trobar la documentació oficial de la classe Application
> [aquí](https://docs.unity3d.com/ScriptReference/Application.html).

## 3.4.3. La classe Time


Programant la lògica d\'un joc, en moltes ocasions volem fer operacions
que no depenguin del nombre de *frames* que el dispositiu és capaç
d\'obtenir. Per exemple, una animació hauria de començar i acabar al
mateix moment, o un joc de carreres hauria de desplaçar els cotxes
segons la velocitat del vehicle i no segons els FPS. Cal tenir en compte
que és bastant freqüent tenir grans variacions en els FPS que
aconseguim, sobretot quan canviem de perspectiva a l\'escena i hi ha
parts amb molt detall i altres molt simples. Per a tot aquest tipus
d\'operacions, tenim a la nostra disposició la classe *Time*, que ens
permet controlar el temps que ha transcorregut entre diferents
esdeveniments, com pot ser entre dos *frames* consecutius.

Vegem un exemple d\'ús:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    private void Update()
    {
        transform.Translate(0, 0, Time.deltaTime * 1);
    }
}
```


> El mètode **Transform.Translate** permet moure el GameObject associat.
>
> **Time.deltaTime** indica el temps que ha transcorregut entre
> l\'execució de l\'últim *frame* i l\'actual.

Aquest *script* fa que el GameObject associat es traslladi una unitat
per segon en l\'eix Z. En cada *frame* (per aquest motiu utilitzem el
mètode Update), l\'objecte es desplaça la quantitat de temps que ha
passat entre dos *frames*. Si tenim FPS molt alts, Time.deltaTime serà
una quantitat molt petita a cada execució, per la qual cosa l\'objecte
es mourà molt poc, i viceversa. Independentment dels FPS, només es
desplaçarà una unitat quan hagi passat un segon complet.

> La variable Time.deltaTime és molt útil, ja que, emprada com a factor
> de correcció, permet executar qualsevol funcionalitat independentment
> dels FPS reals del joc.
>
> Podem trobar la documentació oficial de la classe Time
> [aquí](https://docs.unity3d.com/ScriptReference/Time.html).

--> <a href="Parte3-5.md">Pàgina següent</a>
