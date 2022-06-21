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