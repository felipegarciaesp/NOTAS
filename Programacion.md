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

- Básicamente, `git rebase` se utiliza cuando hago cambios en otras ramas, pero que luego no quiero dejar registro alguno que estas ramas existieron.

- Recordar que primero se hace `git rebase` a las ramas que quiero obviar y luego se hace `git rebase` a la rama principal, donde quiero que se muestren los commits hechos en estas otras ramas. No hacerlo en este orden va a terminar en un conflicto que solo podrá ser resuelto por `git reset`.

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

- WIP siginifica Work In Progress.

- El Stash es util cuando he modificado por error algo en mi archivo y quiero volver a una version anterior.

- El stash es, básicamente, una forma útil de tener en temporal los cambios, poder moverte entre ramas y luego poder recuperar los archivos.

- `git stash` es tipico cuando se hacen pequeños experimentos que no requieren de una nueva rama o un rebase. Sino que simplemente estoy probando algo y despues quiero volver a mi version correcta, la del último commit. 

- Otro ejemplo cuando es necesario el `git stash`es cuando llevo mucho trabajo adelantado y se me olvidó hacer commit y necesito datos de otra rama. Puedo hacer `git stash` y luego un `git checkout` para irme a la otra rama.

- Tambien es útil cuando estoy haciendo modificaciones en la rama main y quiero ir a otra rama, pero aun no quiero hacer commit a mi rama main. En este escenario, es útil hacer `git stash`. 

- Con `git stash` guardo los cambios del archivo en un lugar temporal mientras me muevo a otra rama. Con `git stash list` puedo ver este lugar temporal.

- Con `git stash pop` puedo volver al archivo que dejé guardado en **stash**. Es importante que este comando lo haga en la rama donde hice el **stash**. Lo interesante acá es que estando en el archivo puedo hacer `Ctrl + Z` y volver a lo que había escrito antes.

- Con `git stash branch [nombre rama]` puedo hacer una rama del stash. 

- Con `git stash drop` borro completamente un stash.

- El **stashed** nos sirve para guardar cambios para después, Es una lista de estados que nos guarda algunos cambios que hicimos en Staging para poder cambiar de rama sin perder el trabajo que todavía no guardamos en un commit

- Esto es especialmente útil porque hay veces que no se permite cambiar de rama, ésto porque tenemos cambios sin guardar, no siempre es un cambio lo suficientemente bueno como para hacer un commit, pero no queremos perder ese código en el que estuvimos trabajando.

- El stashed nos permite cambiar de ramas, hacer cambios, trabajar en otras cosas y, más adelante, retomar el trabajo con los archivos que teníamos en Staging, pero que podemos recuperar, ya que los guardamos en el Stash.

###### git stash

- El comando git stash guarda el trabajo actual del Staging en una lista diseñada para ser temporal llamada Stash, para que pueda ser recuperado en el futuro.

- Para agregar los cambios al stash se utiliza el comando:

```
git stash
```

- Podemos poner un mensaje en el stash, para asi diferenciarlos en git stash list por si tenemos varios elementos en el stash. Esto con:

```
git stash save "mensaje identificador del elemento del stashed"
```

###### Obtener elementos del stash

- El **stashed** se comporta como una Stack de datos comportándose de manera tipo **LIFO** (del inglés Last In, First Out, último en entrar, primero en salir), así podemos acceder al método **pop**.

- El método **pop** recuperará y sacará de la lista el último estado del stashed y lo insertará en el staging area, por lo que es importante saber en qué branch te encuentras para poder recuperarlo, ya que el stash será agnóstico a la rama o estado en el que te encuentres. Siempre recuperará los cambios que hiciste en el lugar que lo llamas.

- Para recuperar los últimos cambios desde el stash a tu staging area utiliza el comando:

```
git stash pop
```

- Para aplicar los cambios de un stash específico y eliminarlo del stash:

```
git stash pop stash@{<num_stash>}
```

- Para retomar los cambios de una posición específica del Stash puedes utilizar el comando:

```
git stash apply stash@{<num_stash>}
```

- Donde el <num_stash> lo obtienes desden el git stash list

###### Listado de elementos en el stash

- Para ver la lista de cambios guardados en Stash y así poder recuperarlos o hacer algo con ellos podemos utilizar el comando:

```
git stash list
```

- Retomar los cambios de una posición específica del Stash || Aplica los cambios de un stash específico

###### Crear una rama con el stash

- Para crear una rama y aplicar el stash más reciente podemos utilizar el comando:

```
git stash branch <nombre_de_la_rama>
```

- Si deseas crear una rama y aplicar un stash específico (obtenido desde git stash list) puedes utilizar el comando:

```
git stash branch nombre_de_rama stash@{<num_stash>}
```

- Al utilizar estos comandos **crearás una rama** con el nombre **<nombre_de_la_rama>**, te pasarás a ella y tendrás el **stash especificado** en tu **staging area**.

###### Eliminar elementos del stash

- Para eliminar los cambios más recientes dentro del stash (el elemento 0), podemos utilizar el comando:

```
git stash drop
```

- Pero si, en cambio, conoces el índice del stash que quieres borrar (mediante git stash list) puedes utilizar el comando:

```
git stash drop stash@{<num_stash>}
```

- Donde el <num_stash> es el índice del cambio guardado.

- Si, en cambio, deseas eliminar todos los elementos del stash, puedes utilizar:

```
git stash clear
```

- Consideraciones:
    1. El cambio más reciente (al crear un stash) SIEMPRE recibe el valor 0 y los que estaban antes aumentan su valor.
    2. Al crear un stash tomará los archivos que han sido modificados y eliminados. Para que tome un archivo creado es necesario agregarlo al Staging Area con git add [nombre_archivo] con la intención de que git tenga un seguimiento de ese archivo, o también utilizando el comando git stash -u (que guardará en el stash los archivos que no estén en el staging).
    3. Al aplicar un stash este no se elimina, es buena práctica eliminarlo.

##### 25. Git Clean: limpiar tu proyecto de archivos no deseados.

- Con `git clean` podemos borrar todos esos archivos genereados or error (o quizás no por error) que no queremos que estén en nuestro repositorio. Sin embargo, antes es necesario utilizar `git clean --dry-run` para simular lo que se va a borrar, sin borrarlo.

- Con `git clean -f` se borran todos los archivos indicados en `git clean --dry-run`.

- Ojo que si se tienen carpetas duplicadas, esas deben borrarse a mano, no se borrarán con el comando descrito. Tampoco va a borrar aquellos archivos que le hemos dicho a git que deben ser ignorados (en el archivo .gitignore). **`git clean` solo va a borrar las cosas que puede indexar.**

- Mientras estamos trabajando en un repositorio podemos añadir archivos a él, que realmente no forma parte de nuestro directorio de trabajo, archivos que no se deberían de agregar al repositorio remoto.

- El comando `clean` actúa en archivos sin seguimiento, este tipo de archivos son aquellos que se encuentran en el directorio de trabajo, pero que aún no se han añadido al índice de seguimiento de repositorio con el comando `add`.

- La ejecución del comando predeterminado puede producir un error. La configuración global de Git obliga a usar la opción `force` con el comando para que sea efectivo. Se trata de un importante mecanismo de seguridad ya que este comando no se puede deshacer.

- En resumen:

> `git clean --dry-run` comando que revisa los archivos que no tienen seguimiento.

>`git clean -f` comando que elimina los archivos listados de no seguimiento.

##### 26. Git cherry-pick: traer commits viejos al head de un branch

- Con `git cherry-pick` puedo traer a la versión mas reciente de main una versión en particular hecha en otra rama.

- Funcionaría así: `git cherry-pick [ID del commit]`. Nisiquera debo hacer un commit adicional luego de hacerlo.

- El commit queda registrado como si hubiese sido hecho en main, cuando en realidad fue hecho en otra rama.

- ***Importante: cherry-pick es una mala práctica. Usa cherry-pick con sabiduría. Si no sabes lo que estás haciendo, mejor evita emplear este comando.***

- `git Cherry-pick` es un comando que permite tomar uno o varios commits de otra rama sin tener que hacer un merge completo. Así, gracias a **cherry-pick**, podríamos aplicar los commits relacionados con nuestra funcionalidad en la rama master sin necesidad de hacer un merge.

- Para demostrar cómo utilizar git cherry-pick, supongamos que tenemos un repositorio con el siguiente estado de rama:

> a -b - c - d   Master
>         \
>           e - f - g Feature

- Estando en la rama Master y tipear `git cherry-pick f`, tendremos los siguiente:

>a -b - c - d - f   Master
>         \
>           e - f - g Feature

- Y listo, el commit "f" se agrega a nuestra rama Master.

##### 27. Git Reset y Reflog: úsese en caso de emergencia

- Hay un comando que no olvida nada: `git reflog`. Esto es útil cuando se cometen errores graves, como borrar archivos, borrar ramas y hacer commits que no corresponden. De todas formas, **es igualmente una mala práctica**.

- Con `git reflog` se ve todo. Este es un comando que siempre tiene la verdad. Acá se van a ver incluso aquellos commits que no se ven en `git log` debido a algún `git reset` realizado anteriormente.

- `git reflog` funciona así: 
    1. Tipear `git reflog` en la consola y ver el último HEAD en el que funcionaba todo.
    2. Tipear `git reset HEAD@{4}`. El reset escrito corresponde a uno "soft" y el "HEAD@{4}" es solo un ejemplo, puede tener fácilmente cualquier número en tu proyecto actual.

- Recordar que hay dos tipos de reset:
    -`git reset --soft` mantiene lo que tengas en staging, esto es, todo lo que le has hecho `git add` pero que todavía este pendiente un `git commit`.
    -`git reset --hard` resetea todo.
    -`git reset --hard [ID]` perderá todo lo que se encuentra en staging y en el Working directory y se moverá el head al commit [ID].
    -`git reset --soft [ID]` recuperará todos los cambios que tengas diferentes al commit [ID], los agregará al staging area y moverá el head al commit [ID].

- El [ID] que he puesto en los mensajes anteriores también es conocido como "el hash del Head".

##### 28. Reconstruir commits en Git con amend

- Para esas ocasiones en las que has hecho un commit, pero en realidad te faltó hacer algo. Ejemplo: he hecho un commit que dice: "Cambio al tagline y color del footer", cuando en realidad no cambié el footer.

- Al momento de hacer el cambio del footer, es importante hacer un `git add [archivo.extension]`. Luego, tipeo el comando `git commit --amend`. Esto lo que va a hacer es que va a pegar al commit anterior los cambios que acabo de hacer. Se va a abrir VIM y te va a dar la opción de cambiar/editar el commit.

- *Remendar* un commit con `amend` puede modificar el commit más reciente (enmendar) en la misma rama. Lo ejecutamos así:

```
git add -A #Para hacer uso de amend, los archivos deben estar en staging.
git commit --amend #Remendar último commit.
```

- Este comando sirve para agregar archivos nuevos o actualizar el commit anterior y no generar commits innecesarios. También es una forma sencilla de editar o agregar comentarios al commit anterior porque abrirá la consola para editar este commit anterior.

- Usar `amend` ***es una mala práctica***, sobre todo cuando ya se ha hecho `push` o `pull` al repositorio remoto. Al momento de hacer `amend` con algún commit que esté en remoto, va a generar un conflicto que se va a arreglar haciendo un `commit` adicional y se perderá el beneficio del `amend`.

##### 29. Buscar en archivos y commits de Git con Grep y log

- A continuación, un listado de comandos:

```
git grep color        --> nos buscará en todo el proyecto los archivos en donde está la palabra color.
git grep la           --> donde use la palabra la
git grep -n color     -–> en que lineas usé la palabra color
git grep -n platzi    --> en que lineas usé la palabra platzi
git grep -c la        --> cuantas veces usé la palabra la
git grep -c platzi    --> cuantas veces usé la palabra platzi
git grep -c “<p>”     -–> cuantas veces usé la etiqueta <p>
git log -S “cabecera” --> cuantas veces usé la palabra cabecera en todos los commits.
```

- En resumen, `grep` se usa para los **archivos** y `log` se usa para los **commits**.



## OpenBootcamp

### Curso de Introducción a la Programación

#### Tipos de lenguajes de programación

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

#### Aplicaciones cliente-servidor

- Las aplicaciones cliente-servidor son todas aquellas aplicaciones que te muestran información que descargan u obtienen a través de un servidor que tiene toda esa información. Por ejemplo, Twitter al mostrar su universo de tweets.

- Cuando hacemos una aplicación cliente-servidor se ocupa el protocolo HTTP para acceder a las APIs.

#### Memoria y variables

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

#### Instalación Java e Intellij

- En PATH debemos agregar `%JAVA_HOME%\bin`, que lo que hace es apuntar a la variable JAVA_HOME. `\bin` es para que sea capaz de encontrar Java desde la Terminal.

- Intellij es el entorno de desarrollo integrado de Java. Nos proporciona una herramienta con la cual programar aplicaciones Java.