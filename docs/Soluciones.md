<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)

# Soluciones

## Reto 1

```csharp
using UnityEngine;

public class ExitGame : MonoBehaviour
{
    public void Exit()
    {
        Debug.Log("Saliendo del juego...");
    }
}
```

## Reto 2

```csharp
using UnityEngine;

public class ExitGame : MonoBehaviour
{
    public void Exit()
    {
        Application.Quit();
    }
}
```

## Reto 3

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class NewGame : MonoBehaviour
{
    public void StartNewGame()
    {
        SceneManager.LoadScene("Game");
    }
}
```

## Reto 4

El aspecto que hace que un objeto se comporte como un botón (y, por
ejemplo, pueda ser pulsado) es el hecho de que contenga un componente de
tipo Button. Por lo tanto, si queremos que un bloque de texto, un
objeto de tipo Text, se comporte de este modo, basta con añadirle
dicho componente mediante el botón Add Component del Inspector.

## Reto 5

Primero, es necesario añadir el fichero de imagen al proyecto como
*asset*. En caso contrario, Unity no podría encontrarlo. No busca en el
sistema de ficheros, sino únicamente entre los ficheros del proyecto.
Para hacerlo, basta con arrastrar el fichero desde el explorador del
sistema al apartado *Assets* de Unity, que lo importará automáticamente.
Entonces, hay que arrastrar el nuevo *asset* sobre la propiedad Source
Image del componente Image.

## Reto 6

Para reorganizar los objetos, basta con crear dos nuevos GameObjects
vacíos dentro del Canvas (opción de menú Create Empty) con los nombres
indicados. Entonces, hay que arrastrar los elementos ya existentes,
manteniendo la relación jerárquica entre ellos, de modo que los dos
nuevos objetos sean los únicos nodos que cuelgan directamente del
Canvas.

## Reto 7

Un ejemplo de mapa de localizaciones podría ser el siguiente. En este
caso, usamos un método estático (CreateNode) para construir los nodos a
partir de dos parámetros: el texto de la localización y la lista de
opciones, como array de *string*. El resto de atributos se asignan
directamente, aprovechando que han sido declarados como públicos.

```csharp
public static class StoryFiller
{
    public static StoryNode FillStory()
    {
        var root = CreateNode(
            "Te encuentras en una habitación y no recuerdas nada. Quieres salir",
            new [] {
            "Explorar objetos",
            "Explorar habitación"});

        var node1 = CreateNode(
            "Hay una silla y una mesa con una planta a la izquierda. " +
            "A la derecha hay una estanteria con libros. " +
            "Detrás parece que hay cunas cajas.",
            new [] {
            "Ir a la derecha",
            "Ir a la izquierda",
            "Ir hacia atrás",
            "Explorar habitación"});

        var node2 = CreateNode(
            "Nada interesante... " +
            "Aunque hay un libro que llama la atención... " +
            "¿Botánica para astronautas?",
            new [] {
            "Explorar el resto de la habitación",
            "Averiguar más del libro raro."});

        var node3 = CreateNode(
           "Parece que habla de plantas, qué sorpresa. " +
           "Hay una señalada, se llama plantus corrientis.",
           new [] {
            "Dejar el libro en su sitio y explorar el resto de objetos de la habitación."});

        var node4 = CreateNode(
           "Nada interesante en las cajas, están llenas de libros... " +
           "Deberían estar en la estantería.",
           new [] {
            "Volver y explorar el resto de objetos de la habitación."});

        var node5 = CreateNode(
           "Humm, una silla. Te duele la cabeza, así que te sientas.",
           new [] {
            "Quiero ver lo de la mesa también."});

        var node6 = CreateNode(
            "La mesa en sí no tiene nada de especial, tiene un poco de tierra de la planta. " +
            "Los cajones de la mesa parecen entreabiertos.",
            new [] {
            "Explorar los cajones.",
            "Volver a explorar los otros objetos"});

        var node6Bis = CreateNode(
           "La mesa en sí no tiene nada de especial, tiene un poco de tierra de la planta. " +
           "La etiqueta de la planta pone plantus corrientis. " +
           "Los cajones de la mesa parecen entreabiertos.",
           new [] {
            "Explorar los cajones.",
            "Mirar la planta de cerca.",
            "Volver a explorar los otros objetos"});

        var node7 = CreateNode(
          "Los cajones están vacíos, mejor explorar otra cosa.",
          new [] {
            "Volver a explorar los otros objetos"});

        var node8 = CreateNode(
           "¡¡Al levantar la planta encuentras una llave!! ¿Qué abrirá?",
           new [] {
            "Explorar la habitación"});

        var node9 = CreateNode(
          "La habitación tiene un par de ventanas y una puerta.",
          new [] {
            "Ir a la ventana #1",
            "Ir a la ventana #2",
            "Ir a la puerta"});

        var node10 = CreateNode(
          "La ventana está tapiada, no se puede abrir.",
          new [] {
            "Ir a la otra ventana",
            "Ir a la puerta"});

        var node11 = CreateNode(
          "La puerta está cerrada con un candado.",
          new [] {
            "Explorar los objetos de la habitación"});

        var node11Bis = CreateNode(
          "La puerta está cerrada con un candado.",
          new [] {
            "Explorar los objetos de la habitación",
            "Usar la llave"});

        var node12 = CreateNode(
          "¡¡Has salido de la habitación!!",
          new [] {
            "Salir del juego"});

        root.NextNode[0] = node1;
        root.NextNode[1] = node9;

        node1.NextNode[0] = node2;
        node1.NextNode[1] = node5;
        node1.NextNode[2] = node4;
        node1.NextNode[3] = node9;

        node2.NextNode[0] = node1;
        node2.NextNode[1] = node3;

        node3.NextNode[0] = node1;
        node3.OnNodeVisited = () =>
        {
            node5.NextNode[0] = node6Bis;
        };

        node4.NextNode[0] = node1;

        node5.NextNode[0] = node6;

        node6.NextNode[0] = node7;
        node6.NextNode[1] = node1;

        node6Bis.NextNode[0] = node8;
        node6Bis.NextNode[1] = node1;

        node7.NextNode[0] = node1;

        node8.NextNode[0] = node9;
        node8.OnNodeVisited = () =>
        {
            node9.NextNode[2] = node10.NextNode[1] = node11Bis;
        };

        node9.NextNode[0] = node9.NextNode[1] = node10;
        node9.NextNode[2] = node11;

        node10.NextNode[0] = node10;
        node10.NextNode[1] = node11;

        node11.NextNode[0] = node1;

        node11Bis.NextNode[0] = node1;
        node11Bis.NextNode[1] = node12;

        node12.IsFinal = true;

        return root;
    }

    private static StoryNode CreateNode(string history, string[] options)
    {
        var node = new StoryNode
        {
            History = history,
            Answers = options,
            NextNode = new StoryNode[options.Length]
        };
        return node;
    }
}
```

## Reto 8

Un posible código para gestionar el juego es el siguiente. Nótese como
se añaden algunos atributos (HistoryText, AnswersParent, ButtonAnswer)
que, inicializados correctamente desde el editor, permiten acceder a
ciertos elementos del proyecto (*prefabs*, elementos de la UI) desde el
*script*.

De cara a destruir los botones existentes, la estrategia es la
siguiente. Se guarda en un atributo (ButtonAnswer) con el GameObject
padre en la jerarquía de botones. Entonces, por medio de su componente
Transform, es posible recorrer los componentes Transform de todos los
botones existentes y manipularlos.

Al crear botones nuevos, estos se añaden a la jerarquía de nuevo
asignando ButtonAnswer como padre a cada uno de sus componentes
Transform.

```csharp
using UnityEngine;
using UnityEngine.UI;

public class GameplayManager : MonoBehaviour
{
    public Text HistoryText;
    public Transform AnswersParent;
    public GameObject ButtonAnswerPrefab;

    private StoryNode currentNode;

    private void Start()
    {
        currentNode = StoryFiller.FillStory();
        HistoryText.text = string.Empty;
        FillUi();
    }

    void FillUi()
    {
        HistoryText.text += "\n\n" + currentNode.History;

        foreach (Transform child in AnswersParent.transform)
        {
            Destroy(child.gameObject);
        }

        var isLeft = true;
        var height = 50.0f;
        var index = 0;
        foreach (var answer in currentNode.Answers)
        {
            var buttonAnswerCopy = Instantiate(ButtonAnswerPrefab, AnswersParent, true);

            var x = buttonAnswerCopy.GetComponent<RectTransform>().rect.x * 1.3f;
            buttonAnswerCopy.GetComponent<RectTransform>().localPosition = new Vector3(isLeft ? x : -x, height, 0);

            if (!isLeft)
                height += buttonAnswerCopy.GetComponent<RectTransform>().rect.y * 3.0f;
            isLeft = !isLeft;

            FillListener(buttonAnswerCopy.GetComponent<Button>(), index);

            buttonAnswerCopy.GetComponentInChildren<Text>().text = answer;

            index++;
        }
    }

    private void FillListener(Button button, int index)
    {
        button.onClick.AddListener(() => { AnswerSelected(index); });
    }

    private void AnswerSelected(int index)
    {
        HistoryText.text += "\n" + currentNode.Answers[index];

        if (!currentNode.IsFinal)
        {
            currentNode = currentNode.NextNode[index];

            currentNode.OnNodeVisited?.Invoke();

            FillUi();
        }
        else
        {
            HistoryText.text += "\n" + "TOCA ESCAPE PARA CONTINUAR";
        }
    }
}
```

## Reto 9

Ver las soluciones a los retos 2 y 3. De hecho, podemos volver a usar el
*script* del caso de iniciar partida, no es necesario crear un nuevo. Sí
será necesario para volver a la pantalla de inicio.

## Reto 10

Para llevar a cabo esta tarea, hay que controlar constantemente la
entrada del jugador para ver si este pulsa la tecla *Esc*. Por lo tanto,
se debe usar el método Update para, en cada *frame* del juego, ver si
dicha tecla ha sido pulsada.

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class PauseScreenManager : MonoBehaviour
{
    public GameObject PauseScreen;

    public void LoadMainMenu()
    {
        SceneManager.LoadScene("MainMenu");
    }

    public void RestartGame()
    {
        SceneManager.LoadScene("Game");
    }

    private void Update()
    {
        if (Input.GetKeyUp(KeyCode.Escape))
            PauseScreen.SetActive(!PauseScreen.activeSelf);
    }
}
```

## Reto 11
Podéis elegir la música que más os guste. A continuación, cargamos la
*scene* MainMenu, seleccionamos el GameObject Main Camera y le añadimos
un componente AudioSource. Una vez añadido, arrastramos el *asset* desde
Project al campo AudioClip del componente. Finalmente, seleccionamos las
opciones Loop y Play On Awake. De esta manera, nada más empezar el juego
ya estará sonando la música de fondo, y esta se repetirá automáticamente
cuando se acabe.

Si hacemos la misma operación para cada escena cambiando solo la pista
de audio que asignamos a cada AudioSource, tendremos ya toda la música
de fondo en nuestro proyecto. Dado que cada vez que se carga una escena
se destruyen los objetos de la anterior y se crean los de la nueva, esto
garantiza que se reproduzca una única música en cada pantalla.

## Reto 12

La opción para llevar a cabo esta tarea es mediante la plataforma WebGL.

























<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)



# Solucions

## Repte 1

```csharp
using UnityEngine;

public class ExitGame : MonoBehaviour
{
    public void Exit()
    {
        Debug.Log("Saliendo del juego...");
    }
}
```

## Repte 2

```csharp
using UnityEngine;

public class ExitGame : MonoBehaviour
{
    public void Exit()
    {
        Application.Quit();
    }
}
```

## Repte 3

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class NewGame : MonoBehaviour
{
    public void StartNewGame()
    {
        SceneManager.LoadScene("Game");
    }
}
```

## Repte 4

L\'aspecte que fa que un objecte es comporti com un botó (i, per
exemple, pugui ser premut) és el fet que contingui un component de tipus
Button. Per tant, si volem que un bloc de text, un objecte de tipus
Text, es comporti d\'aquesta manera, n\'hi ha prou d'afegir-li aquest
component mitjançant el botó Add Component de l\'Inspector.

## Repte 5

Primerament, és necessari afegir el fitxer d\'imatge al projecte com a
*asset*. En cas contrari, Unity no podria trobar-lo. No busca en el
sistema de fitxers, sinó únicament entre els fitxers del projecte. Per a
fer-ho, n\'hi ha prou d'arrossegar el fitxer des de l\'explorador del
sistema a l\'apartat *Assets* de Unity, que l'importarà automàticament.
Llavors, cal arrossegar el nou *asset* sobre la propietat Source Image
del component Image.

## Repte 6

Per reorganitzar els objectes, n\'hi ha prou de crear dos nous
GameObjects buits dins del Canvas (opció de menú Create Empty) amb els
noms indicats. Llavors, cal arrossegar els elements ja existents,
mantenint la relació jeràrquica entre ells, de manera que els dos
objectes nous siguin els únics nodes que pengen directament del Canvas.

## Repte 7


Un exemple de mapa de localitzacions podria ser el següent. En aquest
cas, emprem un mètode estàtic (CreateNode) per construir els nodes a
partir de dos paràmetres: el text de la localització i la llista
d\'opcions, com *array* de *string*. La resta d\'atributs s\'assignen
directament, aprofitant que han estat declarats com a públics.

```csharp
    public static class StoryFiller
    {
        public static StoryNode FillStory()
        {
            var root = CreateNode(
                "Ets en una habitació i no recordes res. Vols sortir",
                new [] {
                "Explorar objectes",
                "Explorar habitació"});

            var node1 = CreateNode(
                "Hi ha una cadira i una taula amb una planta a l'esquerra. " +
                "A la dreta hi ha una estanteria amb llibres. " +
                "Darrere sembla que hi ha caixes.",
                new [] {
                "Anar a la dreta",
                "Anar a l'esquerra",
                "Anar cap a enrere",
                "Explorar habitació"});

            var node2 = CreateNode(
                "Res d'interessant... " +
                "Encara que hi ha un llibre que crida l'atenció... " +
                "Botànica per a astronautes?",
                new [] {
                "Explorar la resta de l'habitació",
                "Esbrinar més sobre el llibre rar."});

            var node3 = CreateNode(
               "Sembla que parla de plantes, quina sorpresa. " +
               "N'hi ha una d'assenyalada, es diu plantus corrientis.",
               new [] {
                "Deixar el llibre al seu lloc i explorar la resta d'objectes de l'habitació."});

            var node4 = CreateNode(
               "Res d'interessant a les caixes, estan plenes de llibres... " +
               "Haurien d'estar a la prestatgeria.",
               new [] {
                "Tornar i explorar la resta d'objectes de l'habitació."});

            var node5 = CreateNode(
               "Humm, una cadira. Et fa mal el cap, així que t'asseus.",
               new [] {
                "Vull veure allò de la taula també."});

            var node6 = CreateNode(
                "La taula en si no té res d'especial, té una mica de terra de la planta. " +
                "Els calaixos de la taula semblen entreoberts.",
                new [] {
                "Explorar els calaixos.",
                "Tornar a explorar els altres objectes"});

            var node6Bis = CreateNode(
               "La taula en si no té res d'especial, té una mica de terra de la planta. " +
               "A l'etiqueta de la planta hi diu plantus corrientis. " +
               "Els calaixos de la taula semblen entreoberts.",
               new [] {
                "Explorar els calaixos.",
                "Mirar la planta de prop.",
                "Tornar a explorar els altres objectes"});

            var node7 = CreateNode(
              "Els calaixos estan buits, millor explorar una altra cosa.",
              new [] {
                "Tornar a explorar els altres objectes"});

            var node8 = CreateNode(
               "En aixecar la planta trobes una clau!! Què deu obrir?",
               new [] {
                "Explorar l'habitació"});

            var node9 = CreateNode(
              "L'habitació té un parell de finestres i una porta.",
              new [] {
                "Anar a la finestra #1",
                "Anar a la finestra #2",
                "Anar a la porta"});

            var node10 = CreateNode(
              "La finestra està tapiada, no es pot obrir.",
              new [] {
                "Anar a l'altra finestra",
                "Anar a la porta"});

            var node11 = CreateNode(
              "La porta està tancada amb un cadenat.",
              new [] {
                "Explorar els objectes de l'habitació"});

            var node11Bis = CreateNode(
              "La porta està tancada amb un cadenat.",
              new [] {
                "Explorar els objectes de l'habitació",
                "Usar la clau"});

            var node12 = CreateNode(
              "Has sortit de l'habitació!!",
              new [] {
                "Sortir del joc"});

            root.NextNode[0] = node1;
            root.NextNode[1] = node9;

            node1.NextNode[0] = node2;
            node1.NextNode[1] = node5;
            node1.NextNode[2] = node4;
            node1.NextNode[3] = node9;

            node2.NextNode[0] = node1;
            node2.NextNode[1] = node3;

            node3.NextNode[0] = node1;
            node3.OnNodeVisited = () =>
            {
                node5.NextNode[0] = node6Bis;
            };

            node4.NextNode[0] = node1;

            node5.NextNode[0] = node6;

            node6.NextNode[0] = node7;
            node6.NextNode[1] = node1;

            node6Bis.NextNode[0] = node8;
            node6Bis.NextNode[1] = node1;

            node7.NextNode[0] = node1;

            node8.NextNode[0] = node9;
            node8.OnNodeVisited = () =>
            {
                node9.NextNode[2] = node10.NextNode[1] = node11Bis;
            };

            node9.NextNode[0] = node9.NextNode[1] = node10;
            node9.NextNode[2] = node11;

            node10.NextNode[0] = node10;
            node10.NextNode[1] = node11;

            node11.NextNode[0] = node1;

            node11Bis.NextNode[0] = node1;
            node11Bis.NextNode[1] = node12;

            node12.IsFinal = true;

            return root;
        }

        private static StoryNode CreateNode(string history, string[] options)
        {
            var node = new 
            StoryNode {
                History = history,
                Answers = options,
                NextNode = new StoryNode[options.Length]
            };
            return node;
        }
    }
```

## Repte 8

Un codi possible per gestionar el joc és el següent. Noteu com
s\'afegeixen alguns atributs (HistoryText, AnswersParent, ButtonAnswer)
que, inicialitzats correctament des de l\'editor, permeten accedir a
certs elements del projecte (*prefabs*, elements de la UI) des de
l'*script*.

Per a destruir els botons existents, l\'estratègia és la següent. Es
guarda en un atribut (ButtonAnswer) amb el GameObject pare a la
jerarquia de botons. Llavors, per mitjà del seu component Transform, és
possible recórrer els components Transform de tots els botons existents
i manipular-los.

En crear botons nous, aquests s\'afegeixen a la jerarquia de nou i
s'assigna ButtonAnswer com a pare a cadascun dels seus components
Transform.

```csharp
using UnityEngine;
using UnityEngine.UI;

public class GameplayManager : MonoBehaviour
{
    public Text HistoryText;
    public Transform AnswersParent;
    public GameObject ButtonAnswerPrefab;

    private StoryNode currentNode;

    private void Start()
    {
        currentNode = StoryFiller.FillStory();
        HistoryText.text = string.Empty;
        FillUi();
    }

    void FillUi()
    {
        HistoryText.text += "\n\n" + currentNode.History;

        foreach (Transform child in AnswersParent.transform)
        {
            Destroy(child.gameObject);
        }

        var isLeft = true;
        var height = 50.0f;
        var index = 0;
        foreach (var answer in currentNode.Answers)
        {
            var buttonAnswerCopy = Instantiate(ButtonAnswerPrefab, AnswersParent, true);

            var x = buttonAnswerCopy.GetComponent<RectTransform>().rect.x * 1.3f;
            buttonAnswerCopy.GetComponent<RectTransform>().localPosition = new Vector3(isLeft ? x : -x, height, 0);

            if (!isLeft)
                height += buttonAnswerCopy.GetComponent<RectTransform>().rect.y * 3.0f;
            isLeft = !isLeft;

            FillListener(buttonAnswerCopy.GetComponent<Button>(), index);

            buttonAnswerCopy.GetComponentInChildren<Text>().text = answer;

            index++;
        }
    }

    private void FillListener(Button button, int index)
    {
        button.onClick.AddListener(() => { AnswerSelected(index); });
    }

    private void AnswerSelected(int index)
    {
        HistoryText.text += "\n" + currentNode.Answers[index];

        if (!currentNode.IsFinal)
        {
            currentNode = currentNode.NextNode[index];

            currentNode.OnNodeVisited?.Invoke();

            FillUi();
        }
        else
        {
            HistoryText.text += "\n" + "CLICA ESCAPE PER CONTINUAR";
        }
    }
}
```

## Repte 9

Vegeu les solucions als reptes 2 i 3. De fet, podem tornar a usar
l'*script* del cas d\'iniciar partida, no és necessari crear-ne un de
nou. Sí que serà necessari per tornar a la pantalla d\'inici.

## Repte 10

Per dur a terme aquesta tasca, cal controlar constantment l\'entrada del
jugador per veure si aquest prem la tecla *Esc*. Per tant, s\'ha
d\'emprar el mètode Update per, en cada *frame* del joc, veure si
aquesta tecla ha estat premuda.

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class PauseScreenManager : MonoBehaviour
{
    public GameObject PauseScreen;

    public void LoadMainMenu()
    {
        SceneManager.LoadScene("MainMenu");
    }

    public void RestartGame()
    {
        SceneManager.LoadScene("Game");
    }

    private void Update()
    {
        if (Input.GetKeyUp(KeyCode.Escape))
            PauseScreen.SetActive(!PauseScreen.activeSelf);
    }
}
```

## Repte 11

Podeu triar la música que més us agradi. A continuació, carreguem la
*scene* MainMenu, seleccionem el GameObject Main Camera i li afegim un
component AudioSource. Una vegada afegit, arrosseguem l\'*asset* des de
Project al camp AudioClip del component. Finalment, seleccionem les
opcions Loop i Play On Awake. D\'aquesta manera, només de començar el
joc ja estarà sonant la música de fons, i aquesta es repetirà
automàticament quan s\'acabi.

Si fem la mateixa operació per a cada escena i canviem només la pista
d\'àudio que assignem a cada AudioSource, tindrem ja tota la música de
fons en el nostre projecte. Atès que cada vegada que es carrega una
escena es destrueixen els objectes de l\'anterior i es creen els de la
nova, això garanteix que es reprodueixi una única música a cada
pantalla.

## Repte 12

L\'opció per dur a terme aquesta tasca és mitjançant la plataforma
WebGL.