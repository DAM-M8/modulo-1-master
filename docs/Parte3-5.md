<a name="es">**CAST**</a> (<a href="#ca">versión en catalán aquí</a>)

# 3.5. Ciclo de vida y orden de ejecución de los MonoBehaviour


En los ejemplos que hemos ido viendo, hemos añadido los *scripts* a un
único objeto, pero ¿qué pasaría si los añadiésemos a más objetos? La
respuesta es que cada objeto que tuviese el *script* añadido se
comportaría de la misma manera y, por lo tanto, el mismo código se
ejecutaría varias veces, una por objeto. Pero ¿qué instancia se ejecuta
primero? ¿Y si tuviéramos varios *scripts* distintos y quisiéramos que
un *script* se ejecutase antes que otro? ¿Cómo podemos saber cuándo se
va a ejecutar un *script*?

Unity está diseñado con la simplicidad en mente. La filosofía de
programación es bastante diferente a la de programar otro tipo de
aplicaciones. Generalmente, no tenemos manera de saber el orden exacto
en que se ejecutarán nuestros *scripts*. Tampoco instanciamos clases con
nuestro código, sino que añadimos *scripts* a GameObjects y es el
motor el que se encarga de instanciar dichos *scripts*. Si bien esto en
la práctica resulta muy conveniente, puede resultar extraño si tenemos
experiencia programando otro tipo de aplicaciones.

A la hora de establecer el orden de ejecución, el motor se encarga de
tomar todas las decisiones a nivel interno. Una manera de acostumbrarse
a esta mentalidad es imaginarnos que todos nuestros *scripts* se
ejecutan realmente en paralelo, una vez por *frame*. En el diseño de
nuestra aplicación debemos plantearnos que la mayoría de *scripts* deben
ser lo más simples posibles y realizar una única tarea concreta y
completamente autocontenida. Por ejemplo, un *script* puede controlar
cómo se mueve un enemigo, y otro controlar el desplazamiento para
evaluar si está cansado. Aunque se podría hacer todo en un mismo
*script*, por el modo de trabajar de Unity es mejor tener los dos por
separado.

Sin embargo, hay casos en los que realmente necesitamos tener el control
de qué se ejecuta antes, o enviar información o llamadas de un *script*
a otro. En este caso podríamos echar mano de otros métodos:

-   **Awake:** se ejecuta una sola vez, inmediatamente tras cargarse la
    instancia del *script* y antes del Start.

-   **LateUpdate:** se ejecuta una vez por *frame*, igual que el
    Update, pero solo una vez ya se han ejecutado todos los métodos
    Update de todos los objetos.

> *Awake* se ejecuta incluso antes de que se haya creado completamente
> el propio GameObject asociado.

La secuencia completa de ejecución de los métodos de un *script* en
Unity se puede encontrar en la documentación oficial, pero, a título
ilustrativo y para ver su complejidad real, la reproducimos a
continuación:

![](images/part3/monobehaviour_flowchart.svg)



> Este esquema y su explicación asociada se pueden encontrar
> [aquí](https://docs.unity3d.com/Manual/ExecutionOrder.html).

En este módulo nos limitaremos a gestionar ciclos de ejecución basados
en los métodos Awake, Start y Update.


--> <a href="Parte4.md">Página siguiente</a>

<br /><hr />

<a name="ca">**CAT**</a> (<a href="#es">versión en español aquí</a>)

# 3.5. Cicle de vida i ordre d\'execució dels MonoBehaviour


En els exemples que hem anat veient, hem afegit els *scripts* a un únic
objecte, però què passaria si els afegíssim a més objectes? La resposta
és que cada objecte que tingués l'*script* afegit es comportaria de la
mateixa manera i, per tant, el mateix codi s\'executaria diverses
vegades, una per objecte. Però quina instància s\'executa primer? I si
tinguéssim diversos *scripts* diferents i volguéssim que un *script*
s\'executés abans que un altre? Com podem saber quan s'executarà un
*script*?

Unity està dissenyat pensant amb la simplicitat. La filosofia de
programació és bastant diferent a la de programar un altre tipus
d\'aplicacions. Generalment, no tenim manera de saber l\'ordre exacte en
què s\'executaran els nostres *scripts*. Tampoc instanciem classes amb
el nostre codi, sinó que afegim *scripts* a GameObjects i és el motor el
que s\'encarrega d\'instanciar aquests *scripts*. Si bé això a la
pràctica resulta molt convenient, pot resultar estrany si tenim
experiència programant un altre tipus d\'aplicacions.

A l\'hora d\'establir l\'ordre d\'execució, el motor s\'encarrega de
prendre totes les decisions en l'àmbit intern. Una manera
d\'acostumar-se a aquesta mentalitat és imaginar-nos que tots els
nostres *scripts* s\'executen realment en paral·lel, una vegada per
*frame*. En el disseny de la nostra aplicació hem de plantejar-nos que
la majoria de *scripts* han de ser al més simples possible i realitzar
una única tasca concreta i completament autocontinguda. Per exemple, un
*script* pot controlar com es mou un enemic, i un altre controlar el
desplaçament per avaluar si està cansat. Encara que es podria fer tot en
un mateix *script*, per la manera de treballar de Unity és millor
tenir-los tots dos per separat.

No obstant això, hi ha casos en els quals realment necessitem tenir el
control de què s\'executa abans, o enviar informació o crides d\'un
*script* a un altre. En aquest cas emprar altres mètodes:

-   **Awake:** s\'executa una sola vegada, immediatament després de
    carregar-se la instància de l'*script* i abans del Start.

-   **LateUpdate:** s\'executa una vegada per *frame*, igual que
    l\'Update, però només una vegada ja s\'han executat tots els mètodes
    Update de tots els objectes.

> *Awake* s\'executa fins i tot abans que s\'hagi creat completament el
> propi GameObject associat.

La seqüència completa d\'execució dels mètodes d\'un *script* a Unity es
pot trobar a la documentació oficial, però, a títol il·lustratiu i per
veure'n la complexitat real, la reproduïm a continuació:

![](images/part3/monobehaviour_flowchart.svg)

En aquest mòdul ens limitarem a gestionar cicles d\'execució basats en
els mètodes Awake, Start i Update.


--> <a href="Parte4.md">Pàgina següent</a>
