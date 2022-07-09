# Programación
En este archivo iré dejando notas respecto a la programación, por cursos que vaya tomando.

## Platzi
### Curso profesional de Git y GitHub

#### Pasos de git:
1. Crear una carpeta.
2. Tipear comando `git init` para crear el repositorio.
3. Crear un archivo con un editor de texto, podría ser Visual Studio Code. Para abrir VSC, se puede tipear `code` en el bash.
4. Con `git status` puedo ver el estado de mi proyecto.
5. Al hacer lo anterior me daré cuenta que git en realidad no está haciedo el track de ningún archivo. Para que haga esto debo utilizar el comando `git add nombre_archivo.extension`. También sirve el comando `git add .`
6. Si quisiera sacarle el ***add*** a mi archivo y dejarlo tal cual antes del ***add***, debo hacer: `git rm --cached archivo.extension`
7. Hasta ahora nuestro archivo se encuentra en el llamado ***limbo***, que denominaremos ***stage***.
8. Para añadir nuestro archivo al repositorio hacemos: `git commit -m "mensaje"`
9. Con `cat archivo.extension` puedo ver el contenido del archivo, pero no lo puedo modificar.
10. Con `code archivo.extension` puedo ver el archvio en VSC y modificarlo.
11. Luego de modificarlo es importante volver a agregarlo con el comando `git add .`. Con este comando agrego todos los archivos de la carpeta. Con el punto indico "esta carpeta", asi que se agrega todo. Importante agregarlo al repositorio también.
12. Con `git log archivo.extension` puedo ver la historia de modificaciones del archivo. El número laguísimo es el tag, corresponde al nombre de la modificacion, es su codigo interno.
13. `git show archivo.extension` se van a mostar los cambios que han existido sobre un archivo.
14. Si intento hacer un commit sin comentarios, el bash me va a tirar a un entorno VIM. Salgo de aca agregando un comentario y luego apretando `ESC + SHIFT + Z + Z`. Con esto fuerzo el envio del commit porque guardo el archivo. Esta es la forma de guardar en VIM.
**Aprender mas de terminal linea de comandos para saber más de VIM.**

> Un guion indica que ocuparé un comando, doble guión indica que ocuparé una palabra: Ejemplos:
```
ls -la
git config --global
```
HEAD -> master : estoy en la version mas reciente.
diff: agarra la version anterior con la nueva y me muestra la diferencia.
El index es un indicador dentro de la base de datos de git de donde estan los cambios.
--- a/felipe.txt
+++ b/felipe.txt : esto indica que hay una version a y b.
@@ -1,5 +1,6 @@ : esto indica cuantos bytes cambiaron los archivos

#### Apuntes de clases

##### 23. Git Rebase: reorganizando el trabajo realizado

- Rebase: agarrar una rama entera y pegarla de regreso a la rama main. Es una muy mala practica si se envia a repositorios remotos, esto debe hacerse para repositorios locales. Rebase reescibe la hisotria del repositorio, es como si nunca hubiese existido. Cuidado al hacer rebase. 

- Recordar que primero se hace rebase a la rama que cambia y luego rebase a la rama final.

- Problemas: no queda historia, no se sabe quien hizo qué.

- Rebase es el proceso de mover o combinar una secuencia de confirmaciones en una nueva confirmación base. La reorganización es muy útil y se visualiza fácilmente en el contexto de un flujo de trabajo de ramas de funciones. El proceso general se puede visualizar de la siguiente manera.


<p><a href="https://imgur.com/tiUn7Kh"><img src = "https://i.imgur.com/tiUn7Kh.jpg" width="50%" title="descripcion de la imagen"/></a></p>


- Para hacer un rebase en la rama feature de la rama master, correrías los siguientes comandos:

```
git checkout feature
git rebase master
```

Esto trasplanta la rama feature desde su locación actual hacia la punta de la rama master:

<p><a href="https://imgur.com/F7xTWpC"><img src = "https://i.imgur.com/F7xTWpC.jpg" width="50%" title="descripcion de la imagen"/></a></p>

Ahora, falta fusionar la rama feature con la rama master

```
git checkout master
git rebase feature
# No reorganices el historial público
```

- Nunca debes reorganizar las confirmaciones una vez que se hayan enviado a un repositorio público. La reorganización sustituiría las confirmaciones antiguas por las nuevas y parecería que esa parte del historial de tu proyecto se hubiera desvanecido de repente.

- El comando **rebase** es **una mala práctica, sobre todo en repositorios remotos.** Se debe evitar su uso, pero para efectos de práctica te lo vamos a mostrar, para que hagas tus propios experimentos. Con rebase puedes recoger todos los cambios confirmados en una rama y ponerlos sobre otra.

```
# Cambiamos a la rama que queremos traer los cambios
git checkout experiment
# Aplicamos rebase para traer los cambios de la rama que queremos 
git rebase master
```

##### 24. Git Stash: Guardar cambios en memoria y recuperarlos después




## OpenBootcamp

### Curso de Introducción a la Programación

#### 1. Programación, Variables y Constantes.

##### Tipos de lenguajes de programación

> Es posible hablar de 2 grandes tipos de lenguajes de programación, más un tercero mas secundario:

- 1er tipo: Lenguaje compilado. Son aquellos que a partir de nuestro codigo, se genera un programa que el procesador es capaz de ejecutar directamente desde el Sistema Operativo. El procesador es capaz de ejecutarlo sin ayuda intermedia. Ejemplos: C, Go. Desventajas: Para cada programa que tengo, se debe adaptar a la estructura del procesador que tengo.

- 2do tipo: Lenguaje interpretado. Parte de un codigo fuente pero no se compila a algo que entiende el procesador, sino que algo intermedio. Es un bite-code que no entiende el procesador. Para ejecutarlo necesito un interprete, que es un programa que lee el codigo y ejecuta el programa paso a paso, pero no sobre mi procesador sino que sobre el mismo. Estos son mas lentos que el otro tipo. Ejemplos: Java (se ejecuta en JVM), Python, Pearl, PHP. Ventajas: funcionan en cualquier parte.

- 3er tipo: Híbrido. Tiene lo bueno de los dos: interpreta en cualquier plataforma y es capaz de compilar en ese procesador.

> Los lenguajes pueden ser de otro dos tipos (entre compilado e interpretado), pueden ser tipados y no tipados.

- Tipados: en donde puedo almacenar datos, pero le debo decir al programa que dato es: si es un numero, un texto, mensaje, valor numérico.

- No tipados: aquellos en que mi compilador interprete es capaz de deducir que tipo de dato es.

- Esto de tipado o no tipado lo deciden los programadores del lenguaje. Si un lenguaje es tipado, no hay forma de que yo lo haga no tipado.

> Tipos de aplicaciones:

- Web, de escritorio, aplicaciones móviles.

- Web: capa de chapa y pintura: front-end, es lo que se ve. Cuenta con un codigo HTML (codigo fuente). Tienen codigo JavaScript, da funcionalidad. Tiene tambien CSS, que son los estilos. Los 3 trabajan altamente cohesionados. HTML define la estructura, CSS la pone bonita y JS nos permite interactuar de forma dinámica.

- El back-end de una aplicación Web es el sistema remoto que contiene la información.

- Las app Web se dividen en front-end y back-end. El primero es lo que se ve en la pagina, el segundo es el que contiene la información remota que luego vemos.

- La app de escritorio es mas de lo mismo que la app Web, hay una parte que vemos y otra que no vemos. Cambia como está programada, cambian las tecnologías subyacentes, pero es básicamente lo mismo. En Windows estas app están desarrolladas en .NET, en Mac y otros sistemas cambia.

- La app móvil difiera de las otras por la lógica. Tenemos una unica ventana a la vez, las otras estan diseñadas para mostrar la maxima cantidad de informacion posible (debido a la pantalla). Estas igual estan diseñadas considerando un front-end y back-end.

##### Aplicaciones cliente-servidor

- Las aplicaciones cliente-servidor son todas aquellas aplicaciones que te muestran información que descargan u obtienen a través de un servidor que tiene toda esa información. Por ejemplo, Twitter al mostrar su universo de tweets.

- Cuando hacemos una aplicación cliente-servidor se ocupa el protocolo HTTP para acceder a las APIs.

##### Memoria y variables

- La memoria es donde nuestro ordenador contiene cierta información que, si no lo colocamos, no podemos trabajar con él.

- Cuando compilamos, el procesador debe ser capaz de leer la información desde la memoria.

- Variable: es un nombre humano para una posición de memoria. Fue creado para que no tenga que recordar en que espacio de memoria se ha quedado alguna variable definida. Basta con que me acuerde del nombre de la variable.

```
numero = 1234
decimal = 2.2
saluda = "benvingut"
otro = adios
```

- Podemos identificar dos tipos de variables:
    - Cambiantes: que pueden cambiar su valor en cualquier momento. Se les llama **variables**.
    - No cambiantes: no pueden cambiar su valor una vez que se les ha asignado uno. Se les llama **constantes**.

- Una constante es una asignación de variable que no voy a poder cambiar durante la ejecución del programa.

- Una variable es uan asignación de valor que va a poder cambiar mientras se ejecuta el programa.

##### Instalación Java e Intellij

- En PATH debemos agregar `%JAVA_HOME%\bin`, que lo que hace es apuntar a la variable JAVA_HOME. `\bin` es para que sea capaz de encontrar Java desde la Terminal.

- Intellij es el entorno de desarrollo integrado de Java. Nos proporciona una herramienta con la cual programar aplicaciones Java.

#### 2. Tipos de datos: primitivos y complejos.

##### Introducción a los tipos de datos primitivos

- Un tipo de dato primitivo es un tipo de dato básico en casi cualquier lenguaje de programación.

- Un caracter es un tipo de dato primitivo y este puede ser una letra ('a'), un número ('9') y/o un símbolo ('~'). En las tablas ASCII se puede ver que numero se almacena en la memoria para poder representar cierto caracter.

- Un texto es un conjunto de caracteres. Se le conoce como ***string***. Es importante tener en cuenta que en la memoria se almacena cada caracter por separado pero consecutivo.

> 1 caracter ocupa 8 bits de memoria = 1 bytes.
> 4 caracteres ocupan 8*4 = 32 bits = 4 bytes.

- Otro tipo de dato primitivo son los numeros enteros.

##### Tipos de datos primitivos - Datos Numéricos

- Pueden ser enteros o de coma flotante. Esto ultimo significa que es decimal.

- Los numeros enteros son de 32 bits o de 64 bits.

##### Tipos de datos primitivos - Boolean

- Representan valores Verdadero o Falso. True o False.

##### Tipos de datos complejos - Arrays

- Los tipos de datos complejos se forman a partir de tipos de datos básicos.

- Un array es un conjunto de **un mismo tipo** de datos primitivos.

- A un array de array se le llama "array bidimensional".

```
arraysChar = ['a','b','c','d']
arrayString = ["hola","adios"]
arrayNumeros = [0,1,2,3,4,5,6]
arrayNumeroF = [1.1,4.4,3.14]

arrayInvalido = ['a', 'texto', 9, 3.1]

arrayArrays = [
    [1,2,3]
    [4,5,6]
]
```

##### Tipos de datos complejos - Tuplas

- Suele ser similar a un array, pero con una diferencia. Los elementos del array son variables (mutables), mientras que los de la tupla con invariables (inmutables). La tupla es una especia de **array invariable** (aunque esta definición puede cambiar dependiendo del lenguajes de programación).

- Definición adicional: mapa asociativo = array asociativo = mapa. Esto corresponde a lo siguiente:

```
arrayCapitalesPais[
    "Ucrania" => "Kiev",
    "España" => "Madrid"
]
```

- Los mapas vendrían a ser casi lo mismo que un diccionario (como se le conoce en Python). Son elementos que cuentan con una clave y un valor.

##### Tipos de datos complejos - Objetos

- Un objeto es algo que la lógica de nuestro programa intenta representar el mundo real. Ejemplo: Caja.

- Los objetos pueden tener propiedades. Ejemplo: Caja cuadrada, caja rectangular.

```
Caja:
    Propiedades:
        - Color: blanco.
        - Forma: rectangular

En Java sería así:
class Caja {
    String Color = "blanco";
    String Forma = "rectangular";
    int Largo = 20;
}
```

- Los objetos tienen propiedades y métodos.

- Los métodos son algo que pueden alterar las propiedades del objeto.


>El señor cara de papa, por ejemplo, sería un objeto, ya que intenta representar una papa (que sería la realidad). Las propiedades del señor cara de papa serían color marrón, sombrero, nariz, ojos, etc. El método sería "quitar sombrero", "quitar oreja","poner brazo", etc.


```
Juguete:
    Propiedades:
        - Color: marrón
        - Forma: patata
    Métodos:
        - Poner sombrero.
        - Quitar brazo.

class Juguete{
    String Color = "marron";
    String Forma = "patata";

    ponerSombrero(){}
    quitarBrazo(){}
}
```

##### Consejos y curiosidades sobre los tipos de datos

- Una cadena de texto es una secuencia de caracteres. Los computadores saben donde empieza la secuencia de caracteres pero no donde terminan. Implicitamente los lenguajes de programacion añaden un 0 al final de la cadena de texto creada.

- Por ejemplo, si escribo "Victor", el lenguaje en realidad guardará "Victor"+0. El valor 0 indica fin de cadena, no hace falta crearlo. En definitiva, en la memoria se almacenará: Victor0, con cada caracter en cada espacio. El 0 es algo que va a poner el computador.

- Las cadenas de texto son una conveniencia. Por debajo son escritos así: `arrayCaracteres = ['V','i','c','t','o','r',0]`, pero es mucho mas conveniente no hacer esto, tanto para el PC como para los humanos.

#### 3. Funciones.

##### Definicion y conceptos

- Una función nos permite no tener que repetir codigo.

- En JAVA, la variable `void` en una función indica que esta función no devolverá algún valor. Devolverá nada!

#### 4. Sentencias de control

- Forma en la que hacemos que un programa actúe como nosotros queramos. Son una serie de reglas. Si el codigo hace algo mal, es porque nosotros nos hemos equivocado.

- Condicionales: son condiciones, comparan unas cosas con otras.

- Condiciones lógicas: "Y", "O".

- Comparativas: "MAYOR QUE", "MENOR QUE", "MAYOR O IGUAL QUE", "MENOR O IGUAL QUE", "IGUAL A".

- En esta lección se ha explicado:
    - El `IF` en los lenguajes de programación.
    - Los bucles, que consiste en que un fragmento de mi codigo se va a ejecutar mientras se cumpla una condición. Esto corresponde a los ciclos `WHILE` y `DO WHILE`.
    - El `FOR`, que es otro bucle.
    - Los interruptores (`SWITCH CASE`) que es otra forma de hacer los ciclos `IF ELSE`. Estos `SWITCH CASE` evalúa distintos casos. En Java es importante poner `break` al final de cada `case`, ya que Jjava va ejecutando cada `case` hasta que se encuentra con un `break`.

> IMPORTANTE:

```
contador -=5 es equivalente a contador = contador -5.
contador-- es equivalente a contador = contador - 1.
```

- `DO WHILE` primero ejecuta las acciones y luego evalúa la condición. Lo que hay dentro del cuerpo se va a ejectuar por lo menos una vez, luego veremos si se sigue ejecutando.

-`WHILE` primero evalúa la expresión y luego ejecuta las acciones. Puede que lo que hay dentro de su cuerpo no se ejecute.


> DATO CURIOSO: el lenguaje `Go` no tiene `while`, porque no le hace falta. 

#### 5. Errores

##### Gestión de errores

- **Primer error**: No nombrar bien las variables. Por ejemplo, si una variable es un contador, nombrarla como tal. Esto es para facilitar la vida a un colega que vea el código. El código sin comentarios debe ser entendible fácilmente por alguien que no lleva mucho tiempo programando. Excepeción a esta regla: en los ciclos for es una buena practica identificar las variables como i, j, k, etc. Está permitido igualmente utilizar `temp` o `tmp` para una variable temporal.

```
Un error típico de un programador es asignar un mal nombre a una variable.
```

- **Segundo error**: Hacer un chorro de código sin explicar lo que se quiere hacer. Es importante comentar los códigos. De todas formas, es importante recalcar que es mala práctica comentar lo obvio. No es necesario comentar absolutamente cada línea. Es igualmente malo no comentar que comentar de más.

```
Al hacer comentarios, más que pensar en otro programador, piensa en que esa explicación puede ser útil para tí mismo. Ya sea en el presente o en el futuro.
```

- **Tercer error**: Nno mantener la coherencia en el formato del código. En las empresas hay que seguir la guía de estilo, puede ser que ya tengan un estándar.

- **Cuarto error**: No hacer respaldos de mis códigos, o no ocupar un sistema de control de versiones.

- **Quinto error**: Utilizar formas complejas de codificar que me permite un lenguaje cuando conozco formas mas sencillas de hacerlo.

- **Sexto error**: Encontrar un error en el código utilizando el comando `print`. Lo ideal es utilizar un depurador para esto. Un depurador nos permite hacer cosas que los `print` no.

- **Septimo error**: Crear funciones grandes. Las funciones no pueden ser hechas porque sí, deben tener un cometido en nuestro codigo. Sirven también para simplificar nuestro código.

- **Octavo error**: Abusar de la capacidad de memoria. En un código hay que tener en cuenta que lo ejecutado ocupará memoria en un servidor, por lo que es un parámetro que debe ser tomado en cuenta al momento de programar.

```
La optimización prematura es la causa de todos los males. La micro optimización, más aún.
```

#### 6. Depuración de código

- La **depuración de código** se trata de buscar anomalías durante la ejecución de nuestro código. Un buen programador va a depurar utilizando un depurador y no utilizando `print`.

- Los depuradores funcionan mediante **puntos de ruptura o break point**. Un **punto de ruptura** es una parte en la que decimos al programa que debe detenerse y en ese momento aparece el depurador.

- Un **watcher o watch point** es un **break point** que se dispara solamente si se cumple una condición.

- La **pila de llamadas** es también una herramienta del depurador y sirve para ver por donde ha pasado mi programa.

#### 7. Introducción a la Programación Orientada a Objetos

- La programación orientada a bjetos nos permite tener un código limpio y segmentado. No siempre hay que usarlo, pero es una buena práctica en proyectos grandes.

- **Objeto**: entidad que represente a algo del mundo real.

- Los **objetos** tienen **propiedades**, como lo son el tamaño, color, material, etc. Los objetos también tienen métodos, si hablamos de un auto podemos hablar de abrir/cerrar la puerta, prender/apagar el motor, etc.

- Los **objetos**, según el lenguaje de programación, se declaran mediante **clases** (Java, PHP, Python, etc) o **funciones entre estructuras** (Go).

- Las **clases** tienen que tener una serie de propiedades. Estas propiedades puedes ser **variables** o **constantes**.

- ¿Cómo puedo tener un **objeto** de una **clase**?: **Instanciándolo**.

- **Instanciar** un **objeto** significa crear una zona en la memoria, a través de una **variable**, y que esa zona en la memoria (a la que voy a acceder por medio de esta variable) va a tener lo que tenga la **clase**.

- La convención dice que para crear una instancia de una clase, y por lo tanto crear un objeto, se debe hacer lo siguiente:

    - Primero, poner el nombre de la clase.
    - Seguir con el nombre de la variable que quieres que tenga.
    - Para instanciarlo se debe hacer igual a una nueva referencia en memoria.

- Ejemplo de como crear una instancia de una clase (en Java):

```
Coche coche = new Coche()
```

- **Coche** es una clase definida (ya creada) que cuenta con algunas propiedades.
- **coche** es el nombre de nuestra variable.
- **Coche()** es la nueva referencia en memoria que hemos creado, sería la instancia.


- Al crear el **objeto** ya puedo invocar sus funciones, como se muestra en el siguiente ejemplo:

```
coche.acelerar();
coche.decelerar();
```

- Un ejemplo de **clase** sería el siguiente:

```
class Coche {
    int numeroDePuertas;
    int velocidadMaxima;
    float velocidadActual;

    public void acelerar() {
        velocidadActual +=15;
    }
    public void decelerar() { }
}
```

- Cuando hablamos de funciones dentro de una clase, las llamamos **métodos**.

- **new Coche()** equivale a **instanciar** un objeto. Con **new** nos reserva memoria para un nuevo coche. Nosotros podríamos hacer lo siguiente:

```
Coche coche = new Coche();
Coche coche2 = new Coche();
Coche coche3 = new Coche();
```

- En el ejemplo anterior, cada uno de los coches (coche, coche2 y coche3) tienen variables numeroDdePuertas, velocidadMaxima y velocidadActual independientes entre sí. Esto es porque **new Coche()** asigna memoria en una zona independiente en donde estuvieran las otras variables. Comparten las mismas propiedades y los mismos métodos, pero no son los mismos.

- Un **constructor** es una forma de inicializar las **propiedades** de una **clase** cuando la **instanciamos**.

- Un **constructor** se ejecuta siempre que invoquemos la **clase** y sirve para inicializar las variables (como el número de puertas o la velocidad máxima).

- Un **constructor** es lo primero que se ejecuta cuando se **instancia** una **clase**. El **constructor** es el mejor sitio que se tiene para **inicializar** las **propiedades** de una **clase**.

- Cuando yo no creo un **constructor**, Java automáticamente lo crea por mí. Cuando yo creo un **constructor**, Java ya no va a crear ningún otro **constructor** por mí.

- La gracia del constructor, aplicado a nuestro ejemplo del coche, es que no todos los coches son iguales: algunos pueden tener mas o menos puertas, así como también distintas velocidades máximas para el motor. De esta forma puedo crear el constructor de forma que pueda ingresar las propiedades de la clase. Por ejemplo:

```
public Coche(int puertas, int velocidad) {
        numeroDePuertas = puertas;
        velocidadMaxima = velocidad;
        System.out.println("Estoy en el constructor");
    }
```

- De esta forma, con una misma **clase** puedo crear muchos **objetos** con las mismas **propiedades** pero con valores distintos entre sí. Por ejemplo:

```
Coche coche = new Coche(2, 90);
```
-En Java existe el concepto de **sobrecarga**. Esto consiste en tener dos funciones con el mismo tipado (*"public"*, por ejemplo), pero distintos parámetros. Un ejemplo de esto es crear dos funciones que se llaman igual y que tienen el mismo tipado, pero a una no le defino parámetros de entrada pero a la otra sí. Al llamar a la función, si no le agrego parámetros de entrada entonces será llamada la primera función. En caso contrario, es decir si le he asignado parámetros de entrada, se llama a la otra función.

- No es extraño sobrecargar las funciones para que puedan ser invocadas de distintas formas.

- Hay funciones que se sobrecargan en el tipo de dato. Ejemplo:

```
public int Suma(int a, int b) {return a + b};
public float Suma(float a, float b) {return a + b};
```
- En el ejemplo anterior, ambas funciones se llaman **"Suma"**. Una devuelve un tipo **integer** y acepta valores **integer**, mientras que la otra devuelve valores **float** y acepta valores **float**. Este es otro ejemplo de sobrecarga típica.

- Recordar que lo primero que se ejecuta cuando se **instancia** una **clase** es el **contructor**. El **constructor** es el mejor sitio que tenemos para inicializar las **propiedades** de una **clase**. En el **constructor** podremos sobrecargar las **propiedades** las veces que sean necesarias.

- Como ya se dijo, Java permite realizar la **sobrecarga de funciones**. En concreto, lo que se ha hecho con el ejemplo de **"Coche"** (durante el video) es una **sobrecarga de constructor** o **constructor overloading**.

- Buena práctica: cuando se tiene un constructor con parámetros y se quiere incializar variables internas, habitualmente se dará como nombre de los parámetros los mismos nombres de parámetros que tenga la clase. Para hacer esto correctamente, a la propiedad de la clase se debe anteponer **"this."**:

```
class Coche {

    int numeroDePuertas;
    int velocidadMaxima;
    float velocidadActual;

    public Coche(int numeroDePuertas, int velocidadMaxima) {
        this.numeroDePuertas = numeroDePuertas;
        this.velocidadMaxima = velocidadMaxima;
        System.out.println("Estoy en el constructor CON parametros");
    }

}
```
- Lo que hace el **"this."** en las líneas anteriores es "al parametro numeroDePuertas de esta clase asígnale el valor de la variable de este parametro numeroDePuertas". Esto se hace cuando quiero inicializar una propiedad de la clase cuyo nombre es igual a un parámetro de la función. Para hacer referencia a la propiedad de la clase, debo anteponer el **"this."**, y con esto lo inicializaría.

#### 8. Privacidad, abstracción y encapsulación.

- La **privacidad**, **abstracción** y **encapsulación** son conceptos muy ligados a la **programación orientada a objetos**.

- Las **propiedades** de una **clase** pueden ser públicas, privadas o protegidas.

- Una propiedad privada únicamente la podré utilizar en la implementación de la clase, dentro de la clase. Cuando es pública la podré utilizar tanto dentro de la clase como en el programa principal. Las definiciones de ambas dependen del lenguaje.

- Un ejemplo en Java a continuación:

```
public class Main {

    public static void main(String[] args) {
        Vehiculo vehiculo = new Vehiculo();
        vehiculo.tipo = "Coche";
        System.out.println(vehiculo.tipo);
    }
}

class Vehiculo{
    String tipo;
}
``` 

- Respecto al código anterior, ojo con `Vehiculo vehiculo = new Vehiculo();`. Esto es: la clase `Vehiculo` declara una variable de nombre `vehiculo` que a su vez es una instancia de `Vehiculo` (new Vehiculo()).

- El código anterior muestra un ejemplo de una propiedad pública: puedo acceder (y en este caso definir) a la propiedad de un objeto desde el cuerpo principal del código. En pantalla se imprime 'Coche'. Cambia si el código fuese así:

```
public class Main {

    public static void main(String[] args) {
        Vehiculo vehiculo = new Vehiculo();
        vehiculo.tipo = "Coche";
        System.out.println(vehiculo.tipo);
    }
}

class Vehiculo{
    private String tipo;
}
``` 

- La diferencia del anterior, este código no compilará porque ahora la propiedad "tipo" es privada.

##### ENCAPSULACIÓN:

- La **Encapsulación** consiste en jugar con los tipos públicos y privados de forma que desde la clase los manipule y desde fuera de la clase los pueda utilizar. Para realizar una **encapsulación** se hace lo siguiente (ojo a los comentarios):

```
CLASE MICLASE
    //primero, las propiedades se declaran como privadas:

    PRIVADA PROPIEDAD1;
    PRIVADA PROPIEDAD2;

    // luego, tenemos que definir dos tipos de funciones por cada una de las propiedades: GETTER y SETTER. Tienen como tarea modificar la propiedad o darnos el valor de la propiedad.

    //este es un SETTER:
    //es una funcion que acepta parametros para asignar valores, pero no devuelve un valor.
    FUNCION SETTERPROPIEDAD1(TEXTO valor)
        ESTA_CLASE.PROPIEDAD1 = valor

    //este es un GETTER:
    //esta funcion no acepta parametros pero devuelve algo, en este caso un texto.    
    FUNCION GETTERPROPIEDAD1() TEXTO
        DEVUELVE EL VALOR DE ESTA_CLASE.PROPIEDAD1
``` 

- Se llama **encapsulación** porque estamos encapsulando las propiedades para acceder a ellas únicamente mediante funciones.

- No es necesario crear GETTERS y SETTERS para propiedades que están dentro de la clase.

- La **encapsulación** consiste en que vamos a permitir que se modifiquen ciertas variables privadas de una clase mediante los métodos GET y SET.

- **Encapsular** puede ser muy útil en la programación multi-hilo o si necesitamos que la clase tenga información de su estado.

##### ABSTRACCIÓN:

- La **Abstracción** consiste en que voy a implementar parte de mi **clase** y voy a dejar la otra parte de mi **clase** a su libre albedrío.
