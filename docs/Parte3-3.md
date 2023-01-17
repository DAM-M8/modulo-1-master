<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)

# 3.3. Edición de campos en el Inspector


Los campos (*fields*) de tipos básicos declarados como públicos de una
clase que derive de *MonoBehaviour* tienen una propiedad muy interesante
para los desarrolladores, y es que podemos ver y configurar su valor
visualmente mediante el editor de Unity, en la pestaña Inspector.

> ***bool**, **int**, **float*** y ***string*** se consideran tipos
> básicos, por ejemplo.

Veamos un ejemplo. Supongamos el siguiente *script*:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    public bool TestBool;
    public int TestInt;
    public float TestFloat;
    public string TestString;
    
    private void Start()
    {
        Debug.Log($"TestBool = {TestBool}");
        Debug.Log($"TestInt = {TestInt}");
        Debug.Log($"TestFloat = {TestFloat}");
        Debug.Log($"TestString = {TestString}");
    }
}
```
En este caso, los campos públicos son TestBool, TestInt, TestFloat y
TestString. Si asignamos este *script* a un objeto y echamos un vistazo
al componente que corresponde al *script* en la pestaña Inspector,
veremos que los cuatro campos aparecen reflejados y podemos modificarlos
directamente. Si pulsamos el botón *Play* para ejecutar el programa, se
nos mostrarán por consola los valores que hemos introducido
anteriormente.

Unity también muestra en el editor aquellos campos que se definan con el
atributo \[SerializeField\]. El ejemplo anterior lo podemos modificar
de la siguiente manera:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    [SerializeField]
    private bool testBool;
    [SerializeField]
    private int testInt;
    [SerializeField]
    private float testFloat;
    [SerializeField]
    private string testString;
    
    private void Start()
    {
        Debug.Log($"TestBool = {testBool}");
        Debug.Log($"TestInt = {testInt}");
        Debug.Log($"TestFloat = {testFloat}");
        Debug.Log($"TestString = {testString}");
    }
}
```

Esta estrategia es útil si, de acuerdo con el principio de encapsulación
y ocultación de la información, deseamos declarar un campo de una clase
como privado, pero queremos poder modificar su valor desde el editor del
mismo modo que si fuera público. La regla general es que si es un tipo
es serializable, se mostrará.

> También es posible mostrar datos vía el *Inspector* mediante
> funcionalidades más avanzadas como un *script* de editor.

## No persistencia de estado entre modo edición y ejecución

Es importante tener en cuenta que, al salir del modo ejecución, se
pierden todas las modificaciones que se hayan hecho durante ese tiempo.
Por ejemplo, si antes de pulsar el botón *Play, testInt* tenía como
valor 3, durante la ejecución lo modificamos para que tenga como valor 4
y salimos del modo ejecución, veremos que *testInt* volverá a tener
valor 3.

--> <a href="Parte3-4.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)



# 3.3. Edició de camps a l'Inspector


Els camps (*fields*) de tipus bàsics declarats com a públics d\'una
classe que derivi de *MonoBehaviour* tenen una propietat molt
interessant per als desenvolupadors, i és que podem veure i
configurar-ne el valor visualment mitjançant l\'editor de Unity, a la
pestanya Inspector.

> ***bool**, **int**, **float*** i ***string*** es consideren tipus
> bàsics, per exemple.

Vegem-ne un exemple. Suposem el següent *script*:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    public bool TestBool;
    public int TestInt;
    public float TestFloat;
    public string TestString;
    
    private void Start()
    {
        Debug.Log($"TestBool = {TestBool}");
        Debug.Log($"TestInt = {TestInt}");
        Debug.Log($"TestFloat = {TestFloat}");
        Debug.Log($"TestString = {TestString}");
    }
}
```
En aquest cas, els camps públics són TestBool, TestInt, TestFloat i
TestString. Si assignem aquest *script* a un objecte i fem un cop d\'ull
al component que correspon a l'*script* a la pestanya Inspector, veurem
que els quatre camps apareixen reflectits i podem modificar-los
directament. Si premem el botó *Play* per executar el programa, se\'ns
mostraran per consola els valors que hem introduït anteriorment.

Unity també mostra a l\'editor aquells camps que es defineixin amb
l\'atribut \[SerializeField\]. Podem modificar l\'exemple anterior de la
següent manera:

```csharp
using UnityEngine;

public class ExampleClass : MonoBehaviour
{
    [SerializeField]
    private bool testBool;
    [SerializeField]
    private int testInt;
    [SerializeField]
    private float testFloat;
    [SerializeField]
    private string testString;
    
    private void Start()
    {
        Debug.Log($"TestBool = {testBool}");
        Debug.Log($"TestInt = {testInt}");
        Debug.Log($"TestFloat = {testFloat}");
        Debug.Log($"TestString = {testString}");
    }
}
```

Aquesta estratègia és útil si, d\'acord amb el principi d\'encapsulació
i ocultació de la informació, desitgem declarar un camp d\'una classe
com a privat, però volem poder modificar-ne el valor des de l\'editor de
la mateixa manera com si fos públic. La regla general és que si és un
tipus és serialitzable, es mostrarà.

> També és possible mostrar dades via l\'*Inspector* mitjançant
> funcionalitats més avançades com un *script* d\'editor.

## No persistència d\'estat entre mode edició i execució


És important tenir en compte que, quan sortim del mode execució, es
perden totes les modificacions que s\'hagin fet durant aquest temps. Per
exemple, si abans de prémer el botó *Play, testInt* tenia com a valor 3,
durant l\'execució el modifiquem perquè tingui valor 4 i sortim del mode
execució, veurem que *testInt* tornarà a tenir valor 3.


--> <a href="Parte3-4.md">Pàgina següent</a>
