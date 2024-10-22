### Comandos básicos de Git

Git recuerda los cambios efectuados en los archivos como si tomara instantáneas del sistema de archivos.

Vamos a hablar de algunos comandos básicos para iniciar el seguimiento de los archivos del repositorio. Luego va a guardar la primera "instantánea" con la que Git va a comparar.

git status
El primer comando de Git, y el que se usa con más frecuencia, es git status. Ya lo ha usado una vez en el ejercicio anterior para ver que había inicializado correctamente el repositorio de Git.

git status muestra el estado del árbol de trabajo (y del área de almacenamiento provisional, de la que pronto hablaremos más). Permite ver los cambios que Git está siguiendo en ese momento para poder decidir si quiere pedir a Git que tome otra instantánea.

git add
git add es el comando que se usa para indicar a Git que empiece a realizar un seguimiento de los cambios en determinados archivos.

El término técnico es almacenamiento provisional de estos cambios. Va a usar git add para almacenar provisionalmente los cambios a fin de prepararse para una confirmación. Todos los cambios en los archivos que se han agregado pero que aún no se han confirmado se almacenan en el área de almacenamiento provisional.

git commit
Después de haber almacenado provisionalmente algunos cambios para su confirmación, puede guardar el trabajo en una instantánea si invoca al comando git commit.

Confirmar (o "commit") es un verbo y un sustantivo. Básicamente tiene el mismo significado que cuando se confirma en un plan o se confirma un cambio en una base de datos. Como verbo, la confirmación de cambios significa que se coloca una copia (del archivo, el directorio u otra "cosa") en el repositorio como una nueva versión. Como sustantivo, una confirmación es el pequeño fragmento de datos que asigna una identidad única a los cambios que se confirman. Los datos que se guardan en una confirmación incluyen el nombre del autor y la dirección de correo electrónico, la fecha, los comentarios sobre lo que se ha hecho (y por qué), una firma digital opcional y el identificador único de la confirmación anterior.

git log
El comando git log permite ver información sobre las confirmaciones anteriores. Cada confirmación tiene un mensaje adjunto (un mensaje de confirmación), y el comando git log permite imprimir información sobre las confirmaciones más recientes, como su marca de tiempo, el autor y un mensaje de confirmación. Este comando ayuda a realizar un seguimiento de lo que ha estado haciendo y de los cambios que se han guardado.

git help
Ya ha probado el comando git help, pero vale la pena recordar ciertas cosas. Use este comando para obtener información fácilmente sobre todos los comandos que conoce hasta ahora y más.

Recuerde que cada comando incluye también su propia página de ayuda. Para encontrar estas páginas de ayuda, escriba git <command> --help. Por ejemplo, git commit --help muestra una página que proporciona más información sobre el comando git commit y cómo usarlo.

### Ejercicio: Prueba de Git
Configuración de Git
En Cloud Shell, para comprobar que Git está instalado, escriba git --version:

Bash

git --version
 Sugerencia

Puede usar el botón para los comandos en el Portapapeles. Para pegarlos, haga clic con el botón derecho en una nueva línea en el terminal de Cloud Shell y seleccione Pegar, o bien use el método abreviado de teclado Mayús+Insert (⌘+V en macOS).

Debería ver una salida similar a la de este ejemplo:

Resultados

git version 2.7.4
Para configurar Git, debe definir algunas variables globales: user.name y user.email. Ambas son necesarias para realizar confirmaciones.

Establezca su nombre en Cloud Shell con el siguiente comando. Reemplace <USER_NAME> por el nombre de usuario que quiere usar.

Bash

git config --global user.name "<USER_NAME>"
Ahora, use este comando para crear una variable de configuración user.email; para ello, reemplace <USER_EMAIL> por su dirección de correo electrónico:

Bash

git config --global user.email "<USER_EMAIL>"
Ejecute el siguiente comando para comprobar que los cambios han funcionado:

Bash

git config --list
Confirme que la salida incluye dos líneas similares al siguiente ejemplo. El nombre y la dirección de correo electrónico serán distintos a los que se muestran en el ejemplo.

Resultados

user.name=User Name
user.email=user-name@contoso.com
Configuración del repositorio de Git
Git funciona buscando cambios en los archivos dentro de una determinada carpeta. Vamos a crear una carpeta que actúe como árbol de trabajo (directorio del proyecto) y a permitir que Git sepa sobre ella para que pueda comenzar a seguir los cambios. Se indica a Git que empiece a realizar el seguimiento de los cambios mediante la inicialización de un repositorio de Git en esa carpeta.

Empiece por crear una carpeta vacía para el proyecto y luego inicialice un repositorio de Git dentro de ella.

Cree una carpeta con el nombre Cats. Esta carpeta va a ser el directorio del proyecto, también denominado árbol de trabajo. El directorio del proyecto es donde se almacenan todos los archivos relacionados con el proyecto. En este ejercicio, es donde se almacenan el sitio web y los archivos que crean el sitio web y su contenido.

Bash

mkdir Cats
Vaya al directorio del proyecto mediante el comando cd:

Bash

cd Cats
Ahora, inicialice el nuevo repositorio y establezca el nombre de la rama predeterminada en main:

Si está ejecutando la versión 2.28.0 o una posterior de Git, use el comando siguiente:

Bash

git init --initial-branch=main
O bien, use el siguiente comando:

Bash

git init -b main

En versiones anteriores de Git, use estos comandos:

Bash

git init
git checkout -b main

Después de ejecutar el comando de inicialización, debería ver una salida similar a la de este ejemplo:

Resultados

Initialized empty Git repository in /home/<user>/Cats/.git/

Switched to a new branch 'main'
Ahora, use un comando git status para mostrar el estado del árbol de trabajo:

Bash

git status
Git responde con esta salida, que indica que master es la rama actual. (De hecho, también es la única rama). Por ahora todo está claro.

Resultados

 On branch master

 No commits yet

 nothing to commit (create/copy files and use "git add" to track)        
Use un comando ls para mostrar el estado del árbol de trabajo:

Bash

ls -a
Confirme que el directorio contiene un subdirectorio denominado .git. (El uso de la opción -a con ls es importante, ya que Linux normalmente oculta los nombres de archivos y directorios que comienzan con un punto). Esta carpeta es el repositorio de Git: el directorio en el que Git almacena los metadatos y el historial del árbol de trabajo.

Normalmente no se hace nada directamente con el directorio .git. Git actualiza los metadatos a medida que el estado del árbol de trabajo cambia para mantener un seguimiento de lo que ha cambiado en sus archivos. Este directorio es práctico para usted, pero es increíblemente importante para Git.

Ayuda desde Git
Git, al igual que la mayoría de las herramientas de línea de comandos, tiene una función de ayuda integrada que se puede usar para buscar comandos y palabras clave.

Escriba el comando siguiente para obtener ayuda sobre lo que puede hacer con Git:

Bash

git --help
El comando muestra la salida siguiente:

Resultados

usage: git [--version] [--help] [-C <path>] [-c name=value]
       [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
       [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
       [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
       <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Forward-port local commits to the updated upstream head
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
Lea las distintas opciones disponibles con Git y observe que cada comando incluye su propia página de ayuda, para cuando empiece a profundizar más. No todos estos comandos tendrán sentido todavía, pero es posible que algunos le resulten familiares si tiene experiencia con un VCS.

### Ejercicio: Inicio de un proyecto
Ahora que ha dedicado tiempo a descubrir los comandos de Git fundamentales, pasemos a crear un proyecto en Git.

En los ejercicios que siguen, va a agregar un sencillo archivo HTML al árbol de trabajo para empezar a usar Git. Luego va a realizar algunos cambios en el directorio y a aprender a confirmar los cambios.

Creación y adición (almacenamiento provisional) de un archivo
Git no hace mucho con los directorios vacíos, así que vamos a agregar un archivo al árbol de trabajo para que actúe como página principal del sitio web de fotos de gatos.

Asegúrese de que la sesión de Cloud Shell sigue activa y de que se encuentra en la carpeta del repositorio de nombre Cats.

Use un comando touch para crear un archivo denominado index.html:

Bash

touch index.html
touch actualiza la hora de la última modificación de un archivo, si este existe. Si el archivo no existe, Git crea un archivo vacío con ese nombre de archivo.

Ahora, use git status para obtener el estado del árbol de trabajo:

Bash

git status
Git responde informándole de que no se ha confirmado nada, pero el directorio contiene un nuevo archivo:

Resultados

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    index.html

nothing added to commit but untracked files present (use "git add" to track)
Observe que git status ofrece sugerencias sobre lo que puede hacer a continuación. Git puede configurarse para que sea menos detallado, pero en esta fase, cuanto más, mejor.

Use git add para agregar el nuevo archivo al índice de Git, seguido de git status para comprobar el estado. No olvide el punto al final del comando. Este indica a Git que indexe todos los archivos del directorio actual que se han agregado o modificado.

Bash

git add .
Ahora se ha almacenado provisionalmente una confirmación. El índice de Git es un área de almacenamiento provisional para las confirmaciones. Se trata de una lista de todas las versiones de archivo que van a formar parte de la siguiente confirmación que se haga.

En lugar de git add ., podría haber usado git add index.html, porque index.html era el único archivo nuevo del directorio. Pero si se hubieran agregado varios archivos, git add . los habría incluido todos.

Por último, vuelva a usar git status para asegurarse de que los cambios se han almacenado provisionalmente de forma correcta:

Bash

git status
Debería ver una salida como la de este ejemplo:

Resultados

On branch main

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

    new file:   index.html
Realización de la primera confirmación
Ahora que index.html se ha agregado al índice, el paso siguiente consiste en confirmarlo.

Utilice el comando siguiente para crear otra confirmación:

Bash

git commit index.html -m "Create an empty index.html file"
La marca-m en este comando indica a Git que está proporcionando un mensaje de confirmación.

Hay muchas maneras de formular mensajes de confirmación, pero una buena pauta consiste en escribir la primera línea de modo que indique lo que la confirmación hace en el árbol. También es habitual poner en mayúsculas la primera letra y dejar fuera el punto final para ahorrar espacio. Imagine que la primera línea del mensaje completa la oración que empieza por "Cuando se inserte, esta confirmación...".

Un mensaje de confirmación puede tener varias líneas. La primera línea no debe tener más de 50 caracteres y debe ir seguida de una línea en blanco. Las líneas siguientes no deben tener más de 72 caracteres. No se trata de requisitos estrictos, y se remontan a los días de las tarjetas perforadas y los terminales "tontos", pero mejoran el aspecto de la salida de git log.

Git responde con una confirmación de lo que ha hecho:

Resultados

[main (root-commit) 87e874c] Create an empty index.html file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 index.html
Realice un seguimiento con un comando git status y confirme que el árbol de trabajo está limpio, es decir, que no contiene cambios sin confirmar.

Ahora, use un comando git log para mostrar información sobre la confirmación:

Bash

git log
La respuesta de Git debería ser similar a este ejemplo:

Resultados

commit 87e874c4aeeb3f9692ae5d9875235353708d7dd5
Author: User Name <user-name@contoso.com>
Date:   Fri Nov 15 20:47:05 2019 +0000

Create an empty index.html file
Modifique index.html y confirme el cambio.
index.html se ha creado para servir como página principal del sitio web, pero actualmente está vacío. El siguiente paso es agregarle algún código HTML. Para hacerlo sencillo, vamos a usar el editor integrado de Cloud Shell para agregar una sola línea de HTML.

Abra index.html en el editor en línea escribiendo code index.html en el símbolo del sistema de Terminal:

Bash

code index.html
Escriba o pegue las instrucciones siguientes en el editor:

HTML

<h1>Our Feline Friends</h1>
Guarde el archivo y cierre el editor en línea. Puede seleccionar los puntos suspensivos "..." de la esquina derecha del editor de Cloud Shell o usar la tecla de aceleración (Ctrl+S en Windows y Linux, Cmd+S en macOS).

Use un comando git status para comprobar el estado del árbol de trabajo:

Bash

git status
Puede ver que Git es consciente de los cambios realizados:

Resultados

On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
Ahora, confirme los cambios:

Bash

git commit -a -m "Add a heading to index.html"
Observe que esta vez no se ha ejecutado el comando git add para almacenar provisionalmente los cambios. En su lugar, usamos la marca -a en el comando git commit. La opción -a agrega todos los archivos que se han modificado desde la última confirmación. No agregará archivos nuevos. Para agregar nuevos archivos, se sigue necesitando git add.

Compruebe los resultados. Deberían parecerse a los de este ejemplo:

Resultados

[main 8c9143a] Add a heading to index.html
 1 file changed, 1 insertion(+)
Se ha confirmado el cambio en index.html. Ahora hay dos versiones del archivo en el repositorio, aunque solo se ve una de ellas (la actual). Una de las ventajas de usar Git es que se pueden revertir los cambios realizados o retroceder en el tiempo y ver las versiones anteriores. Veremos más cosas sobre este tema tan importante más adelante.

### Ejercicio: Realización de cambios y seguimiento de estos con Git
La mayoría de los proyectos de desarrollo son iterativos. Se escribe algún código y luego se prueba para asegurarse de que funciona. Luego se escribe más código y se invita a otras personas a contribuir. La iteración significa que hay muchos cambios: adiciones de código, correcciones de errores, eliminaciones y sustituciones.

A medida que trabaje en el proyecto, Git le ayudará a realizar un seguimiento de los cambios que realice. También permite deshacer errores. En los ejercicios siguientes va a continuar compilando el sitio web en el que está trabajando y a aprender algunos nuevos comandos importantes, como git diff.

Modificación de index.html
La página principal del sitio web, index.html, de momento contiene una sola línea de HTML. Vamos a actualizarla para hacer más cosas y luego a confirmar el cambio en Git.

Vuelva a abrir el archivo index.html en el editor en línea de Cloud Shell (code index.html) y reemplace el contenido del archivo por el siguiente código HTML:

HTML

<!DOCTYPE html>
<html>
  <head>
    <meta charset='UTF-8'>
    <title>Our Feline Friends</title>
  </head>
  <body>
    <h1>Our Feline Friends</h1>
    <p>Eventually we will put cat pictures here.</p>
    <hr>
  </body>
</html>
Guarde el archivo y cierre el editor en línea.

Use un comando git diff para ver lo que ha cambiado:

Bash

git diff
El formato de salida es el mismo que el del comando diff de Unix, y el comando de Git tiene muchas de las mismas opciones. Aparece un signo "más" delante de las líneas que se han agregado, y un signo "menos" indica las líneas que se han eliminado.

El valor predeterminado para comparar el árbol de trabajo con el índice es git diff. Es decir, muestra todos los cambios que aún no se han almacenado provisionalmente (agregado al índice de Git). Para comparar el árbol de trabajo con la última confirmación, puede usar git diff HEAD.

Si el comando no vuelve al símbolo del sistema después de ejecutarse, escriba q para salir de la vista de diferencias.

Ahora confirme el cambio. En lugar de usar la marca -a, puede asignar explícitamente un nombre a un archivo para que se almacene provisionalmente y se confirme si Git ya lo tiene en el índice (el comando commit solo comprueba la existencia de un archivo).

Bash

git commit -m "Add HTML boilerplate to index.html" index.html
Use git diff de nuevo para comparar el árbol de trabajo con el índice:

Bash

git diff
Esta vez git diff no genera ninguna salida porque el árbol de trabajo, el índice y HEAD concuerdan.

Digamos que decide que "peludo" suena más amigable que "felino". Sustituya las dos apariciones de "Felino" en index.html por "Peludo". A continuación, guarde el archivo.

Si ha usado el editor de código integrado con el comando code, no verá nada inusual. Pero si ha usado otro editor, como uno llamado sed, es probable que haya creado un archivo index.html.bak que no quiere confirmar. Editores como Vim y Emacs crean archivos de copia de seguridad con nombres como index.html~ y index.html.~1~, en función de cómo estén configurados.

Use el comando siguiente para crear y abrir un archivo denominado .gitgnore en el editor de código integrado:

Bash

code .gitignore
Agregue las líneas siguientes al archivo:

Bash

*.bak
*~
Esta línea indica a Git que omita los archivos cuyos nombres de archivo terminan en .bak o ~.

.gitignore es un archivo muy importante en el mundo de Git porque impide que los archivos extraños se envíen al control de versiones. Hay archivos .gitignore reutilizables disponibles para lenguajes y entornos de programación populares.

Guarde y cierre el editor y luego use estos comandos para confirmar los cambios:

Bash

git add -A
git commit -m "Make small wording change; ignore editor backups"
En este ejemplo se usa la opción -A con git add para agregar todos los archivos sin seguimiento (y no omitidos), así como los que han cambiado, a los archivos que ya están bajo control de Git.

Si en este momento usa git diff, la salida estará vacía porque los cambios se han confirmado. Sin embargo, siempre puede usar un comando git diff HEAD^ para comparar las diferencias entre la confirmación más reciente y la anterior. Pruébelo y vea. No olvide incluir el carácter ^ de cursor de inserción al final del comando.

Adición de un subdirectorio
La mayoría de los sitios web usan hojas de estilo CSS y HTML, y el sitio que está compilando no es una excepción. Normalmente, las hojas de estilo se almacenan en un subdirectorio, así que vamos a crear uno llamado CSS y a agregarlo al repositorio.

Empiece por crear un subdirectorio llamado CSS en el directorio del proyecto:

Bash

mkdir CSS
Luego ejecute git status:

Bash

git status
¿Por qué indica Git que no hay nada que confirmar?

Los usuarios a menudo se sorprenden al saber que Git no considera que agregar un directorio vacío sea un cambio. Esto se debe a que Git solo realiza el seguimiento de los cambios en los archivos, no en los directorios.

En ocasiones, especialmente en las fases iniciales de desarrollo, quiere tener directorios vacíos como marcadores de posición. Una convención común es crear un archivo vacío, a menudo llamado .git-keep, en un directorio de marcador de posición.

Use los comandos siguientes para crear un archivo vacío con ese nombre en el subdirectorio CSS y agregue el contenido del subdirectorio al índice:

Bash

touch CSS/.git-keep
git add CSS
Vuelva a realizar un seguimiento mediante git status para comprobar el estado del repositorio. Confirme que informa de un nuevo archivo.

Reemplazo de un archivo
Ahora vamos a reemplazar .git-keep por un archivo CSS y a actualizar index.html para hacer referencia a él.

Elimine .git-keep del subdirectorio CSS:

Bash

rm CSS/.git-keep
Use el editor integrado para crear un archivo denominado site.css en el subdirectorio CSS:

Bash

cd CSS
code site.css
Agregue el siguiente CSS al archivo. Después, guarda y cierra el archivo.

css

h1, h2, h3, h4, h5, h6 { font-family: sans-serif; }
body { font-family: serif; }
Ahora agregue la siguiente línea a index.html (no olvide volver al directorio Cats) después de la línea <title> y guarde el archivo modificado:

HTML

<link rel="stylesheet" href="CSS/site.css">
Use git status para ver un resumen de los archivos que han cambiado. Luego, use los siguientes comandos para almacenar provisionalmente los archivos sin seguimiento en el control de versiones y confirmar los cambios en site.css e index.html:

Bash

git add .
git commit -m "Add a simple stylesheet"
A diferencia de la mayoría de los VCS, Git registra el contenido de los archivos en lugar de las diferencias (cambios) entre ellos. Esto es en gran medida lo que hace que la confirmación, la bifurcación y el cambio entre ramas sean tan rápidos en Git. Otros VCS tienen que aplicar una lista de cambios que se quieren obtener entre una versión de un archivo y otra. Git solo descomprime la otra versión.

Enumeración de las confirmaciones
Ahora que tiene un número razonable de cambios registrados, puede usar git log para verlos. Al igual que con la mayoría de los comandos de Git, hay muchas opciones entre las que elegir. Uno de los ejemplos más útiles es --oneline.

Use el comando siguiente para revisar todas las confirmaciones:

Bash

git log
Compruebe los resultados. Deben tener un aspecto similar a este ejemplo:

Resultados

commit ae3f99c45db2547e59d8fcd8a6723e81bbc03b70
Author: User Name <user-name@contoso.com>
Date:   Fri Nov 15 22:04:05 2019 +0000

    Add a simple stylesheet

commit 4d07803d7c706bb48c52fcf006ad50946a2a9503
Author: User Name <user-name@contoso.com>
Date:   Fri Nov 15 21:59:10 2019 +0000

    Make small wording change; ignore editor backups

...
Ahora, use este comando para obtener una lista más concisa:

Bash

git log --oneline
Vuelva a comprobar la salida. Esta vez debe parecerse a este ejemplo:

Resultados

ae3f99c Add a simple stylesheet
4d07803 Make small wording change; ignore editor backups
f827c71 Add HTML boilerplate to index.html
45535f0 Add a heading to index.html
a69fe78 Create an empty index.html file
Puede ver por qué cuando hay cientos (o miles) de confirmaciones en un proyecto la opción --oneline puede ser su mejor aliada. Otra opción útil es -nX, donde X es un número de confirmación: 1 para la última confirmación, 2 para la anterior, y así sucesivamente. Para verlo, pruebe un comando git log -n2.

### Ejercicio: Corrección de errores simples
En ocasiones, algo no sale según lo previsto. Es posible que se olvide de agregar un archivo nuevo o que agregue uno por error. Quizás haya cometido un error ortográfico en la confirmación más reciente o haya confirmado algo que no quería confirmar. Quizás haya eliminado accidentalmente un archivo.

Git le permite realizar cambios sin miedo, porque siempre ofrece una manera de volver atrás. Puede incluso cambiar el historial de confirmaciones de Git siempre y cuando cambie solo las confirmaciones que no se hayan compartido.

Rectificación de una confirmación: marca --amend
En el ejercicio anterior ha actualizado el archivo index.html para modificar la ruta de acceso a la hoja de estilos. Debería haber agregado la siguiente instrucción:

HTML

<link rel="stylesheet" href="CSS/site.css">
Imagine que descubre que ha cometido un error al escribir la instrucción. En lugar de especificar la ruta de acceso de la carpeta como CSS, ha escrito CS:

HTML

<link rel="stylesheet" href="CS/site.css">
Al actualizar la página en el explorador, observará que no se aplica la hoja de estilos CSS. Después de investigar, se da cuenta de que ha especificado los valores de la ruta de acceso de forma incorrecta.

Por lo tanto, actualice index.html con la ruta de acceso correcta a la hoja de estilos. En este punto bastaría con confirmar la versión corregida de index.html, pero, en lugar de ello, prefiere colocarla en la misma confirmación que la original. La opción --amend para git commit permite cambiar el historial (¿y con qué frecuencia se tiene la oportunidad de cambiar el historial?).

Bash

git commit --amend --no-edit
La opción --no-edit indica a Git que realice el cambio sin cambiar el mensaje de confirmación. También puede usar --amend para editar un mensaje de confirmación, para agregar archivos dejados accidentalmente fuera de la confirmación o para quitar archivos agregados por equivocación.

 Nota

La capacidad de cambiar el historial es una de las características más útiles de Git. Al igual que la mayoría de las herramientas avanzadas, debe usarse con cuidado. En concreto, es mala idea cambiar las confirmaciones que se han compartido con otro desarrollador, o que se han publicado en un repositorio compartido, como GitHub.

Recuperación de un archivo eliminado: git checkout
Imagine que ha realizado un cambio en un archivo de código fuente que ha interrumpido todo el proyecto, por lo que quiere revertir a la versión anterior de ese archivo. Quizás haya eliminado un archivo por completo accidentalmente. Git facilita la recuperación de una versión anterior, incluso aunque la versión actual ya no exista. El mejor aliado en esta situación es el comando git checkout.

git checkout tiene varias utilidades, pero en el siguiente ejercicio se va a usar para recuperar un archivo eliminado. git checkout actualiza los archivos del árbol de trabajo para que coincidan con la versión del índice o la del árbol especificado.

Si ha eliminado un archivo por accidente, puede recuperarlo si devuelve la versión del índice al árbol de trabajo con este comando:

Bash

git checkout -- <file_name>
También puede extraer del repositorio un archivo de una confirmación anterior (normalmente, el nivel superior de otra rama), pero el valor predeterminado es obtener el archivo del índice. El objeto -- de la lista de argumentos sirve para diferenciar la confirmación de la lista de rutas de archivo. No es estrictamente necesario en este caso, pero si tuviera una rama llamada <nombre_archivo> (quizás porque ese es el nombre del archivo en el que se está trabajando en esa rama), -- evitaría que Git se confundiera.

Más adelante va a aprenderá que checkout también se usa para cambiar de rama.

Recuperación de archivos: git reset
También puede eliminar un archivo con git rm. Este comando elimina el archivo en el disco, pero también hace que Git registre su eliminación en el índice.

Por lo tanto, si ha ejecutado este comando:

Bash

git rm index.html
git checkout -- index.html
Git no restauraría index.html fácilmente. Por el contrario, se obtendría un error como este ejemplo:

Resultados

error: pathspec 'index.html' did not match any file(s) known to git.
Para recuperar index.html, habría que usar otra técnica: git reset. Puede usar git reset para anular el almacenamiento provisional de los cambios.

index.html se puede recuperar con estos dos comandos:

Bash

git reset HEAD index.html
git checkout -- index.html
Aquí, git reset revierte la eliminación del archivo del almacenamiento provisional de Git. Este comando devuelve el archivo al índice, aunque sigue eliminado del disco. Luego se puede restaurar en el disco desde el índice con git checkout.

He aquí otro momento "¡Ahá!" para los nuevos usuarios de Git. Muchos VCS hacen que los archivos sean de solo lectura para asegurarse de que solo una persona pueda efectuar cambios cada vez; los usuarios usan un comando checkout no relacionado para obtener una versión grabable del archivo. También usan checkin para una operación similar a la que realiza Git con una combinación de add, commit y push. A veces este hecho origina confusión cuando los usuarios empiezan a usar Git.

Reversión de una confirmación: git revert
El último comando importante que se debe conocer para corregir errores con Git es git revert. git checkout solo funciona en situaciones en las que los cambios que se van a deshacer están en el índice. Después de confirmar los cambios, debe emplear otra estrategia para deshacerlos. En este caso se puede usar git revert para revertir la confirmación anterior. Crea otra confirmación que cancela la primera.

Se puede usar git revert HEAD para realizar una confirmación exactamente opuesta a la última, con lo que esta se deshace y deja todo el historial intacto. La parte HEAD del comando simplemente indica a Git que se quiere "deshacer" solo la última confirmación.

Por otro lado, también se puede quitar la confirmación más reciente con el comando git reset:

Bash

git reset --hard HEAD^
Git ofrece varios tipos de restablecimientos. El valor predeterminado es --mixed, que restablece el índice, pero no el árbol de trabajo; también mueve HEAD si se especifica otra confirmación. La opción --soft solo mueve HEAD y deja el índice y el árbol de trabajo sin cambios. Esta opción deja todos los cambios como "pendientes de confirmar", como indicaría git status. Un restablecimiento --hard cambia el índice y el árbol de trabajo para que coincidan con la confirmación especificada; los cambios realizados en los archivos seguidos se descartan.

### Ejercicio: Uso de Git para corregir errores
Práctica de recuperación de un archivo eliminado
En primer lugar, intente eliminar index.html:

Bash

rm index.html
Puede parecer una mala idea, pero recuerde: Git le cubre las espaldas.

Use un comando ls para comprobar que index.html se haya eliminado:

Bash

ls
Debería ver la siguiente salida. Observe que ahora no hay ningún archivo index.html.

Resultados

CSS
Vamos a recuperar index.html. Use git checkout para recuperar index.html:

Bash

git checkout -- index.html
Vuelva a utilizar ls para comprobar el contenido del directorio actual. ¿Se ha restaurado index.html?

Sí. Ahora la salida debe tener un archivo index.html y un directorio CSS:

Resultados

CSS  index.html
Práctica de la recuperación de un archivo eliminado: git rm
Si quiere recuperar archivos eliminados, las cosas son un poco más complicadas si los elimina mediante git rm en lugar de rm.

Para ver lo que sucede, pruebe este comando:

Bash

git rm index.html
De nuevo, busque index.html al ejecutar ls. No debería ver index.html.

Intente recuperar index.html lo mismo que la última vez:

Bash

git checkout -- index.html
Esta vez, Git indica que no sabe nada de index.html. Esto se debe a que Git no solo ha eliminado el archivo, sino que ha registrado la eliminación en el índice:

Resultados

error: pathspec 'index.html' did not match any file(s) known to git.
Revierta la eliminación de index.html del almacenamiento provisional con el comando git reset:

Bash

git reset HEAD index.html
Busque esta salida, que lo confirma:

Resultados

Unstaged changes after reset:
D       index.html
Ahora puede recuperar el archivo del índice con el comando que ha usado antes:

Bash

git checkout -- index.html
git reset deshizo el cambio, pero el archivo seguía borrado, así que tuvo que usar checkout para recuperarlo.

Vuelva a comprobar que ha funcionado al ejecutar ls.

Reversión de una confirmación
Ahora vamos a complicar las cosas un poco más. Imagine que por accidente sobrescribe un archivo con otro, o que hace un cambio en un archivo que resulta ser un gran error. Quiere revertir el archivo a la versión anterior, pero ya ha confirmado los cambios. En este caso, un sencillo git checkout no va a funcionar.

Una solución a este problema consiste en revertir la confirmación anterior.

Abra index.html con code:

Bash

code index.html
Reemplace el contenido de index.html por este código:

HTML

<h1>That was a mistake!</h1>
Guarde y cierre el archivo.

Use estos comandos para confirmar los cambios y mostrar la confirmación más reciente:

Bash

git commit -m "Purposely overwrite the contents of index.html" index.html
git log -n1
La marca -n1 aquí indica a Git que solo se quiere la entrada de confirmación más reciente.

Use los comandos siguientes para intentar restaurar index.html:

Bash

git checkout -- index.html
Abra index.html en el editor:

Bash

code index.html
¿Qué versión de index.html verá? ¿La versión anterior o la nueva?

En esta situación, la mejor opción es revertir el cambio realizando otra confirmación que cancele la primera. Este es un trabajo para git revert.

Cierre el archivo y use git revert para deshacer los cambios confirmados:

Bash

git revert --no-edit HEAD
La marca --no-edit aquí indica a Git que no se quiere agregar un mensaje de confirmación para esta acción.

Compruebe los resultados. Deben tener un aspecto similar a este ejemplo:

Resultados

[main 6a27310] Revert "Purposely overwrite the contents of index.html"
1 file changed, 13 insertions(+), 1 deletion(-)
Realice un seguimiento con un comando git log para mostrar la confirmación más reciente:

Bash

git log -n1
Vuelva a comprobar la salida. Deberían parecerse a los de este ejemplo:

Resultados

Author: User Name <user-name@contoso.com>
Date:   Tue Nov 19 23:42:26 2019 +0000

Revert "Purposely overwrite the contents of index.html"

This reverts commit 15d3bded388470c98881a632025bc15190fe9d17.
Por último, abra el archivo index.html para asegurarse de que el contenido es la versión correcta.

La reversión no es la única manera de solucionar esta situación; bastaría con editar index.html y confirmar el archivo corregido. Esa opción es más difícil si los cambios confirmados fueran muchos. En cualquier caso, git revert es una clara señal de intenciones.

### Ejercicio: Colaboración mediante un comando de incorporación de cambios
En su tiempo de ocio ha estado trabajando en un sitio web que hospeda fotos de gatos. Ha estado usando Git para el control de versiones, y es hora de invitar a colaboradores al proyecto. Durante una cena en su casa, su amiga y también amante de los gatos, Alice, se ofrece a ayudarle a materializar su proyecto, y usted acepta encantado.

Alice primero debe hacer una copia del proyecto de Git. Luego es recomendable que Alice le envíe sus cambios a medida que los realiza. En esta situación es donde destaca la naturaleza distribuida de Git. Con Git, dos o más usuarios pueden trabajar juntos en un proyecto sin miedo a sobrescribir el trabajo de los otros. Además, puede comprobar el trabajo de Alice antes de combinarlo con el suyo. (Alice tiene talento, pero ningún desarrollador es perfecto. Confíe, pero compruebe)

En esta lección va a aprender a clonar un repositorio (también denominado repo) para ponerlo a disposición de otros usuarios. También aprenderá a usar una de las características más importantes de Git: las solicitudes de incorporación de cambios.

Clonación de un repositorio (git clone)
En Git, un repositorio se copia al clonarlo mediante el comando git clone. Puede clonar un repositorio independientemente de dónde esté almacenado, siempre que tenga una dirección URL o una ruta de acceso a la que apuntar.

git clone acepta rutas de acceso del sistema de archivos, rutas de acceso SSH (por ejemplo, git@example.com:alice/Cats; estará familiarizado con este formato si ha usado Rsync o SCP) o direcciones URL, normalmente una que empiece por file:, git: o ssh. Los distintos formatos se describen en la documentación de git clone. En Unix y Linux, la operación de clonación usa vínculos físicos, así que es rápida y usa un espacio mínimo, ya que solo hay que las entradas de directorio, no los archivos.

Repositorios remotos (git pull)
Cuando Git clona un repositorio, crea una referencia al repositorio original, al que se llama remoto, mediante el nombre origin. Configura el repositorio clonado de modo que incorpore o recupere datos del repositorio remoto. (Git también puede enviar cambios. Va a obtener información sobre el envío de cambios en Git más adelante en este módulo). origin es la ubicación predeterminada desde la que Git incorpora los cambios y a la que los envía. git pull copia los cambios del repositorio remoto en el local. El comando git pull es muy eficaz, porque solo copia las confirmaciones y los objetos nuevos y luego los inserta en el árbol de trabajo.

Puede incorporar cambios de origin mediante el comando git pull. Resulta útil comparar git pull con otros métodos de copia de archivos. El comando scp copia todo. (scp es similar al comando cp de Unix, salvo que los archivos que se copian no tienen que estar en el mismo equipo). Si hay 10 000 archivos en el directorio remoto, scp los copia todos. Un programa más eficaz llamado Rsync examina todos los archivos de los directorios local y remoto y solo copia los que son diferentes. Rsync se suele usar para realizar copias de seguridad, pero tiene que aplicar hash a todos los archivos, a menos que tengan diferentes tamaños o fechas de creación.

Git solo examina las confirmaciones. Ya sabe cuál es la última confirmación que ha obtenido del repositorio remoto porque ha guardado la lista de confirmaciones. Luego, Git indica al equipo desde el que está copiando que envíe todo lo que ha cambiado, incluidas las nuevas confirmaciones y los objetos a los que apuntan. Esos objetos y confirmaciones se agrupan en un archivo denominado paquete que se envía en un lote. Por último, Git actualiza el árbol de trabajo al desempaquetar todos los objetos que han cambiado y combinarlos (si fuera necesario) con las confirmaciones y los objetos del árbol de trabajo.

Git solo incorpora o envía cambios si el usuario se lo indica. En eso difiere de, por ejemplo, Dropbox, que tiene que pedir al sistema operativo que le notifique los cambios realizados en su carpeta y, a veces, preguntar al servidor si alguna otra persona ha realizado cambios.

Creación de solicitudes de incorporación de cambios (git request-pull)
Una vez que otro desarrollador, como Alice, ha clonado el repositorio y realizado algunos cambios en local, es recomendable que incorpore esos cambios al repositorio original. Podría parecer que lo adecuado sería enviar los cambios al repositorio original, pero se produciría un error al hacerlo, ya que otros usuarios no tienen permiso para realizar cambios en él. Y así debe ser. Por ahora, quiere revisar los cambios entrantes antes de combinarlos con la base de código principal.

Por ahora, Alice tendrá que enviar una solicitud de incorporación de cambios para pedirle que incorpore sus cambios a la base de código principal. Alice puede hacerlo mediante git request-pull, que podría tener el aspecto de este ejemplo:

Bash

git request-pull -p origin/main .
Alice hace referencia a la rama main del remoto origin como origin/main.

Esta solicitud de incorporación de cambios es básicamente lo mismo que una de GitHub, que es un lugar para almacenar código del que no se habla en este módulo. Una solicitud de incorporación de cambios le ofrece la posibilidad de revisar los cambios de otros colaboradores antes de incorporar su trabajo al que está realizando en el sitio web. Las revisiones de código son una parte importante (algunos dirían que la más importante) de la programación colaborativa.

Creación de un remoto (git remote) y finalización de la solicitud de incorporación de cambios (git pull)
Como propietario del proyecto, debe saber cómo combinar las solicitudes de incorporación de cambios. En primer lugar, use el comando git remote para configurar el repositorio de otro desarrollador como remoto. Luego use ese remoto para las incorporaciones y las solicitudes de incorporación de cambios mediante el comando git pull.

En segundo plano, git pull es una combinación de dos operaciones más sencillas: git fetch, que obtiene los cambios, y git merge, que combina esos cambios en el repositorio. En este caso, la combinación era de avance rápido, lo que significa que Alice tenía la confirmación más reciente en su repositorio, por lo que esta confirmación podría agregarse al principio del historial sin ninguna modificación.

### Ejercicio: Clonación de un repositorio
Para que Alice practique cómo clonar un repositorio y realizar una solicitud de incorporación de cambios, primero se debe configurar un repositorio para que Alice lo clone.

Configuración
Git ya se ha instalado automáticamente en Azure Cloud Shell, por lo que podemos usar Git en Cloud Shell, a la derecha.

Use el comando mkdir para crear una carpeta denominada Cats:

Bash

mkdir Cats

Use el comando cd para ir a la carpeta del proyecto:

Bash

cd Cats

Ahora, inicialice el nuevo repositorio y establezca el nombre de la rama predeterminada en main.

Si está ejecutando la versión 2.28.0 o una posterior de Git, use los comandos siguientes:

Bash

git init --initial-branch=main
git init -b main

En versiones anteriores de Git, use estos comandos:

Bash

git init
git checkout -b main

Configure Git mediante la incorporación de sus credenciales. Reemplace <USER_NAME> y <USER_EMAIL> por su propia información (por ejemplo, "Nombre de usuario" y "user-name@contoso.com").

Bash

git config user.name "<USER_NAME>"
git config user.email "<USER_EMAIL>"

Cree algunos archivos con el comando touch y almacénelos provisionalmente y confírmelos mediante Git:

Bash

touch index.html
mkdir CSS
touch CSS/site.css
git add .
git commit -m "Create empty index.html, site.css files"

Agregue algún código HTML al archivo index.html mediante el editor de código de Cloud Shell, que puede abrir con el comando code en el símbolo del sistema del terminal:

Bash

code index.html

Pegue este código HTML:

HTML

<!DOCTYPE html>
<html>
  <head>
    <meta charset='UTF-8'>
    <title>Our Feline Friends</title>
    <link rel="stylesheet" href="CSS/site.css">
  </head>
  <body>
    <h1>Our Feline Friends</h1>
    <p>Eventually we will put cat pictures here.</p>
    <hr>
  </body>
</html>
Guarde el archivo y cierre el editor. Puede seleccionar los puntos suspensivos "..." de la esquina derecha del editor o usar el método abreviado de teclado (Ctrl+S en Windows y Linux, Cmd+S en macOS).

Vaya al directorio CSS y abra site.css en el editor:

Bash

cd CSS
code site.css

Agregue el siguiente CSS a site.css:

css

h1, h2, h3, h4, h5, h6 { font-family: sans-serif; }
body { font-family: serif; }
Luego guarde el archivo y cierre el editor.

Vuelva al directorio Cats.

Bash

cd ..

Por último, confirme los cambios de nuevo:

Bash

git add .
git commit -m "Add simple HTML and stylesheet"

Compruebe rápidamente el registro de Git para asegurarse de que todo parezca correcto:

Bash

git log --oneline

Compruebe los resultados. Debería ver una salida como la de este ejemplo:

Resultados

2bf69ab Add simple HTML and stylesheet
bb371c8 Create empty index.html, site.css files
Clonación de un repositorio
Ahora vamos a asumir el papel de Alice y a practicar la clonación de un repositorio para colaborar en él.

Para simular la clonación del repositorio por parte de Alice en el equipo de ella, cree un directorio denominado Alice en su equipo y clone en él el directorio del proyecto. En la vida real, esta colaboración se lograría mediante la configuración de un recurso compartido de red o un remoto accesible por medio de una dirección URL.

Cree un directorio denominado Alice en el que clonar el repositorio. No debe ser un subdirectorio del directorio del proyecto (Cats), así que use cd de nuevo para ir al directorio principal desde el directorio del proyecto a fin de convertir Alice en un elemento del mismo nivel que el directorio del proyecto. Luego, use cd para ir al directorio Alice.

Bash

cd ..
mkdir Alice
cd Alice

Ahora use git clone para clonar el repositorio que se encuentra en el directorio del proyecto en el directorio Alice. Asegúrese de incluir el punto al final del comando:

Bash

git clone ../Cats .

../Cats indica a Git desde dónde debe realizar la clonación, mientras que . le indica la ubicación de destino de esta. En Unix, . hace referencia al directorio actual.

Compruebe los resultados. Git debe mostrar este texto para indicarle que ha funcionado:

Resultados

Cloning into '.'...
done.
Ahora hay un clon del repositorio del directorio del proyecto en el directorio Alice.

### Ejercicio: Creación de una solicitud de incorporación de cambios
En el espacio aislado, asegúrese de que sigue en el directorio Alice, que es la carpeta superior del clon de Alice del repositorio Cats. Puede usar el comando pwd para comprobar la ubicación de la carpeta.

Bash

pwd

En este momento no hay nada que Alice pueda incorporar, porque no se ha realizado ningún cambio desde que ella clonó el repositorio. Puede probarlo con el siguiente comando, que muestra la salida Already up-to-date:

Bash

git pull

Realización de un cambio y envío de una solicitud de incorporación de cambios
Alice comienza a trabajar en el sitio web. Su primera decisión es cambiar el color de fondo del sitio. Alice experimenta en local y, finalmente, elige su tono favorito de azul claro.

Configure una identidad para Alice mediante la ejecución de los siguientes comandos:

Bash

git config user.name "Alice"
git config user.email "alice@contoso.com"

Estos valores de configuración config se almacenan en el repositorio en el archivo .git/config, así que no tendrá que volver a escribirlos. Cada vez que vaya al directorio Alice, asumirá la identidad de Alice.

Abra el archivo site.css del directorio Alice/CSS:

Bash

code CSS/site.css

Para cambiar el color de fondo de la página a azul claro, reemplace la segunda línea del archivo por la siguiente instrucción:

css

body { font-family: serif; background-color: #F0FFF8; }
Luego guarde el archivo y cierre el editor.

Ahora confirme el cambio:

Bash

git commit -a -m "Change background color to light blue"

Luego realice una solicitud de incorporación de cambios al repositorio original:

Bash

git request-pull -p origin/main .

Compruebe los resultados. Debería ver una salida similar al ejemplo siguiente:

Resultados

The following changes since commit 2bf69ab0226d8d35efd1e92c83cd92c5cc09a7ae:

  Add simple HTML and stylesheet (2019-11-21 01:57:24 +0000)

are available in the git repository at:

  .

for you to fetch changes up to 95bbc3b6929953e9b04353920e97230b463022f0:

  Change background color to light blue (2019-11-21 02:33:48 +0000)

----------------------------------------------------------------
Alice (1):
      Change background color to light blue

 CSS/site.css | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

diff --git a/CSS/site.css b/CSS/site.css
index caefc86..86d41e8 100644
--- a/CSS/site.css
+++ b/CSS/site.css
@@ -1,2 +1,2 @@
 h1, h2, h3, h4, h5, h6 { font-family: sans-serif; }
-body { font-family: serif; }
\ No newline at end of file
+body { font-family: serif; background-color: #F0FFF8; }
\ No newline at end of file
Creación de un remoto y finalización de la solicitud de incorporación de cambios
Dado que el directorio del proyecto y el directorio Alice están en el mismo equipo, puede incorporar los cambios directamente desde el directorio Alice. En la vida real, el directorio Alice estaría en el equipo de ella. Esta circunstancia se soluciona mediante la configuración de un remoto con el comando git remote. Luego se usa ese remoto para las solicitudes de incorporación y envío de cambios. En este ejercicio no resulta práctico configurar dos máquinas para realizar estos pasos, así que se va a configurar un remoto que use un nombre de ruta de acceso local. En realidad, se usaría una ruta de acceso de red o una URL.

Vuelva al directorio del proyecto y use el comando git remote para crear un remoto de nombre remote-alice que tenga como destino el directorio del proyecto de Alice:

Bash

cd ../Cats
git remote add remote-alice ../Alice

Ahora ejecute una incorporación de cambios:

Bash

git pull remote-alice main

Observe que tiene que especificar una rama, main, en el comando de incorporación de cambios. En la siguiente lección va a aprender a configurar una dirección URL ascendente para la rama.

Compruebe los resultados. Debería ver una salida como la de este ejemplo, que muestra que la solicitud de incorporación de cambios se ha realizado correctamente:

Resultados

remote: Counting objects: 4, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 1), reused 0 (delta 0)
Unpacking objects: 100% (4/4), done.
From ../Alice
 * branch            main     -> FETCH_HEAD
 * [new branch]      main     -> remote-alice/main
Updating 2bf69ab..95bbc3b
Fast-forward
 CSS/site.css | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
La diversión acaba de empezar. En la siguiente lección, aprenderá a configurar y utilizar un repositorio compartido, lo que hace que la colaboración resulte más sencilla y cómoda.

### Ejercicio: Colaboración mediante un repositorio compartido
La incorporación de cambios directa desde el repositorio de otro usuario funciona, siempre que ambos estén en la misma red. Pero es un proceso burdo, y la mayoría de los colaboradores no están en la misma red. Es mejor configurar un repositorio central en el que todos los colaboradores pueden insertar y enviar.

Cuando le habla a su amigo desarrollador Bob sobre su proyecto y este le pide participar, eso es exactamente lo que decide hacer: configurar un repositorio central, que también se conoce como repositorio vacío.

Creación de un repositorio vacío
Lo que necesita es un repositorio que no tenga árbol de trabajo. Un repositorio vacío tiene varias ventajas con respecto a un árbol de trabajo:

Sin un árbol de trabajo, todo el mundo puede enviar cambios sin tener que preocuparse de qué rama se extrae del repositorio.
Para Git es fácil detectar si otro usuario ha enviado cambios que podrían entrar en conflicto con los suyos.
Un repositorio compartido se escala a cualquier número de desarrolladores. Con un repositorio vacío solo tiene que saber sobre el repositorio compartido y no sobre los demás colaboradores de los que puede que tenga que incorporar.
Al colocar el repositorio compartido en un servidor al que todos pueden acceder, no tiene que preocuparse por los firewalls ni los permisos.
No necesita cuentas independientes en el servidor, ya que Git realiza un seguimiento de quién ha realizado cada confirmación. (GitHub tiene millones de usuarios que comparten la cuenta git. Todos usan el protocolo de red criptográfico de Secure Shell (SSH) y los usuarios se distinguen por sus claves públicas).
Crear un repositorio vacío para compartir es sencillo:

Cree un nuevo directorio denominado Shared.git en el mismo nivel que los directorios Alice y Cats para que contenga el repositorio vacío:

Bash

cd ..
mkdir Shared.git
cd Shared.git

El nombre del directorio no tiene importancia, pero en estos ejercicios nos referiremos a él como el directorio Shared.git o simplemente como el directorio compartido.

Al asignar al directorio el nombre Shared.git se sigue la larga tradición de asignar a los repositorios vacíos un nombre que finaliza en .git para distinguirlos de los árboles de trabajo. Se trata de una convención, no de un requisito.

Ahora use el siguiente comando para crear un repositorio vacío en el directorio compartido:

Bash

git init --bare

Cuando un repositorio todavía está vacío, no se puede usar el comando git checkout para establecer el nombre de la rama predeterminada. Para realizar esta tarea, puede cambiar la rama HEAD para que apunte a otra rama; en este caso es la rama main:

Bash

git symbolic-ref HEAD refs/heads/main

El siguiente paso consiste en obtener el contenido de su repositorio en el repositorio compartido. Use estos comandos para volver al directorio del proyecto donde está almacenado el repositorio, configure un remoto origin y realice un envío de cambios inicial:

Bash

cd ../Cats
git remote add origin ../Shared.git
git push origin main

Compruebe los resultados. La salida debería indicar que la operación se ha realizado correctamente:

Resultados

Counting objects: 12, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (8/8), done.
Writing objects: 100% (12/12), 1.07 KiB | 0 bytes/s, done.
Total 12 (delta 1), reused 0 (delta 0)
To ../Shared.git
 * [new branch]      main -> main
Quiere que push y pull usen de manera predeterminada la rama main de origin, como si se hubiera creado el repositorio clonándolo. Pero primero debe indicar a Git la rama cuyo seguimiento se va a efectuar.

Bash

git branch --set-upstream-to origin/main

Busque esta salida:

Resultados

Branch main set up to track remote branch main from origin.
Git se quejaría si se intentara ejecutar este comando antes del envío de cambios inicial, ya que el nuevo repositorio no tendría ramas. Git no puede realizar el seguimiento de una rama que no existe. Lo único que Git hace por debajo es buscar en .git/refs/remotes/origin un archivo denominado trunk.

Configuración para colaboradores
El siguiente paso es que Bob clone el repositorio vacío y que Alice defina el origen en su repositorio para establecer como destino de las incorporaciones y los envíos de cambios el repositorio compartido.

Cree un directorio denominado Bob que sea un elemento del mismo nivel que el directorio del proyecto y luego vaya al directorio Bob:

Bash

cd ..
mkdir Bob
cd Bob

Ahora, clone el repositorio compartido (asegúrese de incluir el punto al final del comando):

Bash

git clone ../Shared.git .

Actualmente, el repositorio de Alice está configurado para enviar e incorporar cambios desde su propio repositorio. Use los siguientes comandos para ir al directorio Alice y cambie origin para que apunte al repositorio compartido:

Bash

cd ../Alice
git remote set-url origin ../Shared.git

Inicio de la colaboración
Ahora que Bob lo tiene todo a punto para trabajar en el sitio web, decide agregar un pie de página en la parte inferior. Vamos a asumir el rol de Bob y Alice durante unos minutos para aprender los aspectos básicos de la colaboración.

Comience por ir al directorio Bob y trabaje como Bob:

Bash

cd ../Bob
git config user.name Bob
git config user.email bob@contoso.com

Abra index.html y reemplace el elemento <hr> por esta línea (se encuentra al final del elemento <body>):

HTML

<footer><hr>Copyright (c) 2021 Contoso Cats</footer>
Luego guarde el archivo y cierre el editor.

Confirme los cambios e insértelos en el origen remoto:

Bash

git commit -a -m "Put a footer at the bottom of the page"
git push

Compruebe los resultados. Si ve una advertencia similar a la del ejemplo siguiente, no se preocupe. Simplemente comunica a los usuarios un cambio en los comportamientos predeterminados de Git. Si quiere asegurarse de no volver a ver esta advertencia, puede ejecutar git config --global push.default simple.

Resultados

warning: push.default is unset; its implicit value has changed in
Git 2.0 from 'matching' to 'simple'. To squelch this message
and maintain the traditional behavior, use:

  git config --global push.default matching

To squelch this message and adopt the new behavior now, use:

  git config --global push.default simple

When push.default is set to 'matching', git will push local branches
to the remote branches that already exist with the same name.

Since Git 2.0, Git defaults to the more conservative 'simple'
behavior, which only pushes the current branch to the corresponding
remote branch that 'git pull' uses to update the current branch.

See 'git help config' and search for 'push.default' for further information.
(the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
'current' instead of 'simple' if you sometimes use older versions of Git)
Mientras Bob edita el sitio, Alicia también lo hace. Ella decide agregar una barra de navegación a la página. Esta incorporación obliga a Alice a modificar dos archivos: index.html y site.css. Empiece por volver al directorio Alice:

Bash

cd ../Alice

Ahora, abra index.html e inserte la línea siguiente inmediatamente después de la etiqueta <body>, en la línea 8:

HTML

<nav><a href="./index.html">home</a></nav>
Luego guarde el archivo y cierre el editor.

Abra site.css en la carpeta CSS y agregue la línea siguiente en la parte inferior:

css

nav { background-color: #C0D8DF; }
Guarde el archivo y cierre el editor.

Ahora imagine que Alice recibe un correo electrónico de Bob en el que le dice que ha hecho cambios en el sitio. Alice decide extraer los cambios de Bob antes de confirmarlos. (Si Alice ya hubiera confirmado los cambios, tendrían otro problema que trataremos en otro módulo). Alice ejecuta este comando:

Bash

git pull

Compruebe los resultados. Por la salida, parece que Git ha evitado un problema:

Resultados

remote: Counting objects: 3, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 2), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
From ../Shared
   843d142..2cf6cbf  main     -> origin/main
Updating 843d142..2cf6cbf
error: Your local changes to the following files would be overwritten by merge:
        index.html
Please commit your changes or stash them before you can merge.
Aborting
Git advierte que la incorporación de cambios sobrescribiría la versión de Alice de index.html y se perderían sus cambios. Esto se debe a que Bob también ha modificado index.html. Si Alice no hubiera cambiado index.html, Git habría confirmado la combinación.

Use un comando git diff para ver qué cambios ha realizado Bob en index.html:

Bash

git diff origin -- index.html

Compruebe los resultados. Por la salida, es evidente que los cambios de Alice y los de Bob no se superponen. Ahora Alice puede guardar provisionalmente sus cambios.

git stash guarda el estado del árbol de trabajo y el índice mediante un par de confirmaciones temporales. Piense en el almacenamiento provisional como una manera de guardar el trabajo actual mientras hace otra cosa, sin tener que realizar una confirmación "real" ni afectar al historial del repositorio.

En realidad, Alice debería haber confirmado o guardado provisionalmente sus cambios antes de intentar incorporar cambios. La incorporación de cambios a un árbol de trabajo "sucio" es algo arriesgado, ya que puede provocar incidencias más complejas de subsanar.

Use el siguiente comando para guardar provisionalmente los cambios de Alice:

Bash

git stash

Compruebe los resultados. Deberían parecerse a los de este ejemplo:

Resultados

Saved working directory and index state WIP on main: 95bbc3b Change background color to light blue
HEAD is now at 95bbc3b Change background color to light blue
Ahora Alice puede incorporar los cambios con seguridad, después de lo cual puede "sacar" los cambios guardados provisionalmente, que están organizados como una pila. (De hecho, git stash es una forma abreviada de git stash push. Es muy similar a la pila donde se colocan las facturas que aún no se han podido pagar). Ejecute estos comandos:

Bash

git pull
git stash pop

Los cambios guardados provisionalmente se combinan al extraerlos. Si los cambios se superponen, podría haber un conflicto. Puede obtener información sobre cómo resolver esas situaciones en un módulo de Git más avanzado de Microsoft Learn.

Compruebe los resultados. Alice debería ver esta salida, que le permite saber que la combinación se ha realizado correctamente y que los cambios están de vuelta, aunque aún no se hayan almacenado provisionalmente para su confirmación:

Resultados

Auto-merging index.html
On branch main
Your branch is up-to-date with 'origin/main'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   CSS/site.css
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (0cfb7b75d56611d9fc6a6ab660a51f5582b8d9c5)
En este punto Alice puede seguir trabajando o simplemente confirmar y enviar los cambios. Vamos a hacer otro cambio como Alice: asignar a los pies de página el mismo estilo que a las barras de navegación.

Abra site.css en la carpeta CSS y reemplace la tercera línea (la que aplica estilo a los elementos <nav>) por esta regla CSS compartida. Luego, como de costumbre, guarde los cambios y cierre el editor.

HTML

nav, footer { background-color: #C0D8DF; }
Ahora confirme los cambios y envíelos al repositorio compartido:

Bash

git commit -a -m "Stylize the nav bar"
git push

El sitio actualizado está ahora en el repositorio compartido.

Para finalizar, vuelva al directorio del proyecto y realice una incorporación de cambios:

Bash

cd ../Cats
git pull

Abra index.html (el que se encuentra en el directorio del proyecto) para confirmar que los cambios realizados por Bob y Alice están presentes en el repositorio local. Compruebe que index.html tiene el código más actualizado:

HTML

<!DOCTYPE html>
<html>
  <head>
    <meta charset='UTF-8'>
    <title>Our Feline Friends</title>
    <link rel="stylesheet" href="CSS/site.css">
  </head>
  <body>
    <nav><a href="./index.html">home</a></nav>
    <h1>Our Feline Friends</h1>
    <p>Eventually we will put cat pictures here.</p>
    <footer><hr>Copyright (c) 2021 Contoso Cats</footer>
  </body>
</html>
En este momento, su repositorio y el de Alice están sincronizados, pero el de Bob no lo está. Para finalizar, actualice también el de Bob:

Bash

cd ../Bob
git pull

Los tres repositorios ya están alineados. El repositorio compartido es el único origen de confianza para todos los usuarios, y todos los envíos de cambios e incorporaciones se dirigen a él.

### Ejercicio: Creación de una rama como Alice
Ejercicio: Creación de una rama como Alice
Configurar
Para que podamos asumir el rol de Alice, debe hacer algo de trabajo para configurar un repositorio vacío que todos compartan y, después, agregar algunos archivos.

Git ya se ha instalado automáticamente en Azure Cloud Shell, por lo que podemos usar Git en Cloud Shell, a la derecha.

Creación de un repositorio vacío compartido
Cree un directorio denominado Shared.git para que contenga el repositorio vacío:

Bash

mkdir Shared.git
cd Shared.git

Ahora, ejecute el comando siguiente para crear un repositorio vacío en el directorio compartido:

Bash

git init --bare

Establezca el nombre de la rama predeterminada del nuevo repositorio. Para realizar este paso, puede cambiar la rama HEAD para que apunte a otra rama; en este caso, la rama main:

Bash

git symbolic-ref HEAD refs/heads/main

Clonación del repositorio compartido para Bob
Suba un nivel a partir de este directorio y cree un directorio para que Bob almacene su repositorio:

Bash

cd ..
mkdir Bob

Clone y configure el repositorio de Bob:

Bash

cd Bob
git clone ../Shared.git .
git config user.name Bob
git config user.email bob@contoso.com
git symbolic-ref HEAD refs/heads/main

 Nota

Como quiere empezar con la rama predeterminada de main, debe cambiar HEAD para que apunte a refs/heads/main en lugar de refs/heads/master, que es el nombre de la rama predeterminada.

Incorporación de archivos base
Como paso final de configuración, se agregarán los archivos de sitio web base y se insertarán en el repositorio compartido. En el caso de estos comandos, todavía estamos trabajando en el directorio Bob.

Cree algunos archivos mediante el comando touch de Linux, agréguelos al "stage" y confírmelos mediante Git:

Bash

touch index.html
mkdir Assets
touch Assets/site.css
git add .
git commit -m "Create empty index.html and site.css files"

Ahora agregue HTML al archivo con el editor de código de Cloud Shell. Puede abrir el editor mediante la ejecución del comando code. Abra index.html en el editor en línea; para ello, introduzca code index.html en el símbolo del sistema del terminal:

Bash

code index.html

Pegue este código HTML:

HTML

<!DOCTYPE html>
<html>
  <head>
    <meta charset='UTF-8'>
    <title>Our Feline Friends</title>
    <link rel="stylesheet" href="CSS/site.css">
  </head>
  <body>
    <nav><a href="./index.html">home</a></nav>
    <h1>Our Feline Friends</h1>
    <p>Eventually we will put cat pictures here.</p>
    <footer><hr>Copyright (c) 2021 Contoso Cats</footer>
  </body>
</html>
Guarde el archivo y cierre el editor. Puede seleccionar los puntos suspensivos "…" de la esquina derecha del editor o usar el método abreviado de teclado (CTRL+S en Windows y Linux, o bien Cmd+S en macOS).

Cambie al directorio Assets (Recursos) y abra site.css en el editor:

Bash

cd Assets
code site.css

Agregue el siguiente CSS al archivo:

css

h1, h2, h3, h4, h5, h6 { font-family: sans-serif; }
body { font-family: serif; background-color: #F0FFF8; }
nav, footer { background-color: #C0D8DF; }
Guarde el archivo y cierre el editor.

Vuelva al directorio Bob y confirme de nuevo:

Bash

cd ..
git add .
git commit -m "Add simple HTML and stylesheet"
git push --set-upstream origin main

 Nota

Como se va a usar otro nombre de rama predeterminado, debe indicarle a Git que asocie la rama principal a la rama principal del repositorio de origen.

Compruebe los resultados. Si ve una advertencia similar a la de este ejemplo, no se preocupe. Esta advertencia simplemente informa a los usuarios de un cambio en los comportamientos predeterminados de Git.

Resultados

warning: push.default is unset; its implicit value has changed in
Git 2.0 from 'matching' to 'simple'. To squelch this message
and maintain the traditional behavior, use:

  git config --global push.default matching

To squelch this message and adopt the new behavior now, run:

  git config --global push.default simple

When push.default is set to 'matching', git will push local branches
to the remote branches that already exist with the same name.

Since Git 2.0, Git defaults to the more conservative 'simple'
behavior, which only pushes the current branch to the corresponding
remote branch that 'git pull' uses to update the current branch.

See 'git help config' and search for 'push.default' for further information.
(the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
'current' instead of 'simple' if you sometimes use older versions of Git)
Si quiere asegurarse de que no vuelve a ver esta advertencia, puede ejecutar este comando:

Bash

git config --global push.default simple

Compruebe la salida de este indicador de éxito:

Resultados

Counting objects: 9, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (9/9), 953 bytes | 953.00 KiB/s, done.
Total 9 (delta 0), reused 0 (delta 0)
To ../Shared.git
 * [new branch]      main -> main
Creación de una rama para Alice
Alice quiere crear una rama puntual denominada add-style para realizar su trabajo. Vamos a asumir el rol de Alice y, después, crearemos la rama y agregaremos código a esta rama.

Suba un nivel a partir de este directorio y cree un directorio para la copia del repositorio de Alice:

Bash

cd ..
mkdir Alice

Clone el repositorio de Alice y, a continuación, configúrelo:

Bash

cd Alice
git clone ../Shared.git .
git config user.name Alice
git config user.email alice@contoso.com

Ahora tiene una copia actual del repositorio. Puede enumerar el contenido del archivo y ejecutar git status para confirmar el estado del repositorio.

Bash

ls
git status

Ejecute el comando git branch para crear una rama denominada add-style. Luego, ejecute el comando git checkout para cambiar a esa rama (de este modo, la convierte en la rama actual).

Bash

git branch add-style
git checkout add-style

En el directorio Alice/Assets (Alice/Recursos), abra site.css. Agregue la siguiente definición de clase CSS al final del archivo:

css

.cat { max-width: 40%; padding: 5 }
Guarde los cambios en el archivo y cierre el editor.

Confirme el cambio:

Bash

git commit -a -m "Add style for cat pictures"

En este momento, Alice quiere poner su estilo a disposición de todos los demás, para que cambien a main de nuevo y realicen una incorporación de cambios por si alguna otra persona ha realizado cambios:

Bash

git checkout main
git pull

La salida indica que la rama main está actualizada (es decir, main del equipo de Alice coincide con main en el repositorio compartido). Por tanto, Alice combina la rama add-style con la rama main mediante la ejecución del comando git merge --ff-only para realizar una combinación de avance rápido. Luego, Alice inserta la main de su repositorio en el compartido.

Bash

git merge --ff-only add-style
git push

En este caso, la combinación de avance rápido no era estrictamente necesaria porque la rama main no tenía ningún cambio y Git habría combinado los cambios de todos modos. Sin embargo, usar la marca --ff only es una buena práctica porque se produce un error en una combinación de --ff-onlysi main ha cambiado.

### Ejercicio: Combinación de la rama de Bob
Ejercicio: Combinación de la rama de Bob

Aunque Alice está trabajando en CSS para el sitio web, Bob está trabajando en casa, completamente ajeno al trabajo que está realizando Alice. No hay problema con esta disposición porque ambos usan ramas. Bob decide realizar algunos cambios por su cuenta.

Creación de una rama para Bob
Vuelva al directorio Bob y ejecute el comando siguiente para crear una rama denominada add-cat. Use la popular opción checkout -b para crear la rama y cambiar a ella con un solo comando.

Bash

cd ../Bob
git checkout -b add-cat

Descargue el archivo ZIP que contiene algunos recursos del sitio web. A continuación, descomprima los archivos de recursos:

Bash

wget https://github.com/MicrosoftDocs/mslearn-branch-merge-git/raw/main/git-resources.zip
unzip git-resources.zip

Ahora, mueva el archivo bobcat2-317x240.jpg al directorio Assets (Recursos) de Bob. Elimine los demás archivos. Descargará los archivos y los volverá a usar más adelante.

Bash

mv bobcat2-317x240.jpg Assets/bobcat2-317x240.jpg
rm git-resources.zip
rm bombay-cat-180x240.jpg

A continuación, abra el archivo index.html y reemplace la línea que dice "Eventually we will put cat pictures here" (al final se incluirán aquí las imágenes de gatos) por la siguiente línea:

HTML

<img src="Assets/bobcat2-317x240.jpg" />
Guarde el archivo y cierre el editor.

Ha realizado dos cambios en la rama add-cat de Bob: se ha agregado un archivo y se ha modificado otro. Ejecute git status para volver a comprobar los cambios:

Bash

git status

Después, ejecute los comandos siguientes para agregar el nuevo archivo del directorio Assets (Recursos) al índice y confirmar todos los cambios:

Bash

git add .
git commit -a -m "Add picture of Bob's cat"

Bob ahora realiza la misma acción que antes hizo Alice. Bob vuelve a cambiar a la rama main y ejecuta una incorporación de cambios para ver si ha cambiado algo:

Bash

git checkout main
git pull

Compruebe los resultados. Esta vez, el resultado indica que los cambios se han realizado en la rama main en el repositorio compartido (el resultado de las inserciones de Alice). También indica que el cambio extraído de main en el repositorio compartido se ha combinado con main en el repositorio de Bob:

Resultados

remote: Counting objects: 4, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 1), reused 0 (delta 0)
Unpacking objects: 100% (4/4), done.
From D:/Labs/Git/Bob/../Shared
   e81ae09..1d2bfea  main     -> origin/main
Updating e81ae09..1d2bfea
Fast-forward
 Assets/site.css | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)
A continuación, Bob combina su rama en la rama para que de su repositorio tenga sus cambios mainymain los de Alice. A continuación, Bob envía los cambios de main del equipo de la rama main del repositorio compartido:

Bash

git merge add-cat --no-edit
git push

Bob no usó la marca --ff-only porque sabían que main había cambiado. Una combinación de solo avance rápido habría producido un error.

Sincronización de los repositorios
En este momento, Bob tiene un repositorio actualizado, pero Alice no. Alice tiene que ejecutar git pull en el repositorio compartido para asegurarse de que tiene la versión óptima y más reciente del sitio.

Ejecute los comandos siguientes para sincronizar el repositorio de Alice con el repositorio compartido:

Bash

cd ../Alice
git pull

Tómese unos minutos para comprobar que el repositorio de Alice y el repositorio de Bob están sincronizados. Cada repositorio debe tener un archivo JPG en el directorio Assets (Recursos) y un elemento <img> declarado en el archivo index.html. El archivo site.css de la carpeta Assets (Recursos) de cada repositorio debe contener una línea que defina una hoja de estilo CSS llamada cat. Alice agregó este estilo cuando realizó los cambios.

Si abre index.html en un explorador, verá la imagen siguiente:

Screenshot that shows cats on the website.

### Ejercicio: Resolución de conflictos de combinación

Ejercicio: Resolución de conflictos de combinación

A veces, independientemente de lo bien que lo planee todo, las cosas salen mal. Imagine que dos desarrolladores están trabajando en el mismo archivo del proyecto al mismo tiempo. El primer desarrollador envía sus cambios a la rama main del repositorio del proyecto sin ningún problema. Cuando el segundo desarrollador intenta enviar los cambios, Git indica que hay un conflicto de combinación. El archivo que el segundo desarrollador está intentando modificar ya no está actualizado con los cambios o la versión de archivo más recientes. La versión de archivo debe estar actualizada antes de que se puedan combinar los cambios del segundo desarrollador. Una de las principales preocupaciones de los desarrolladores que usan el control de versiones es un conflicto de combinación.

Pueden producirse conflictos como este, por lo que debe saber cómo tratarlos. La buena noticia es que Git ofrece soluciones para tratar los conflictos de combinación.

Creación de ramas para Alice y Bob
Comencemos por crear una rama para Alice y otra para Bob. Ambos amigos desarrolladores están actualizando los archivos del repositorio del proyecto al mismo tiempo. No son conscientes de los cambios que realiza el otro porque están realizando las actualizaciones en sus ramas locales.

Asegúrese de que se encuentra en el directorio Alice y, a continuación, cree una rama denominada add-cat para que Alice trabaje en:

Bash

git checkout -b add-cat

Cambie al directorio Bob y, después, cree una rama denominada style-cat para que Bob trabaje en:

Bash

cd ../Bob
git checkout -b style-cat

Ahora vamos a realizar algunos cambios en las ramas.

Realización de un cambio como Alice
Para empezar, suponga que tiene el rol de Alice y realice un cambio en la página principal del sitio web. Reemplace la imagen del gato de Bob por una fotografía del de Alice.

Vuelva a cambiar al directorio Alice:

Bash

cd ../Alice

Si no ha descargado anteriormente los recursos, descargue el archivo ZIP que contiene los recursos que complementan esta lección. Descomprima los archivos de recursos:

Bash

wget https://github.com/MicrosoftDocs/mslearn-branch-merge-git/raw/main/git-resources.zip
unzip git-resources.zip

Mueva el archivo bombay-cat-180x240.jpg al directorio Assets (Recursos) de Alice y elimine los demás archivos:

Bash

mv bombay-cat-180x240.jpg Assets/bombay-cat-180x240.jpg
rm git-resources.zip
rm bobcat2-317x240.jpg

Abra el archivo index.html y, a continuación, reemplace esta instrucción (que usa una de las imágenes del gato de Bob):

HTML

<img src="Assets/bobcat2-317x240.jpg" />
Con esta instrucción (que usa una de las imágenes del gato de Alice):

HTML

<img class="cat" src="Assets/bombay-cat-180x240.jpg" />
Guarde el archivo y cierre el editor.

Ahora, ejecute los siguientes comandos de Git para enviar los cambios al repositorio del proyecto. En primer lugar, vamos a agregar las confirmaciones realizadas en la carpeta Assets (Recursos). Después, volveremos a la rama main y ejecutaremos git pull para asegurarnos de que no haya cambiado nada. Por último, vamos a combinar la rama local add-cat con la rama main y, después, enviaremos los cambios al repositorio.

Bash

git add Assets
git commit -a -m "Add picture of Alice's cat"
git checkout main
git pull
git merge --ff-only add-cat
git push

Por último, es necesario confirmar que el envío de cambios se ha realizado correctamente.

Realización de un cambio como Bob
Sin saber lo que está haciendo Alice, Bob observa que el último envío de cambios de Alice ha agregado un estilo CSS denominado cats al archivo site.css para el repositorio. Por tanto, Bob decide aplicar esa clase a la imagen de su gato.

Vuelva al directorio Bob:

Bash

cd ../Bob

Abra el archivo index.html . Reemplace la instrucción que usa la imagen del gato de Bob por la siguiente instrucción que agrega un atributo class="cat" al elemento <img>:

HTML

<img class="cat" src="Assets/bobcat2-317x240.jpg" />
Guarde el archivo y cierre el editor.

Ahora, ejecute los siguientes comandos de Git para sincronizar los cambios en el repositorio del proyecto, como hizo para las actualizaciones en el repositorio de Alice. Confirme el cambio, cambie a la rama main, ejecute git pull y, a continuación, combine el cambio de estilo:

Bash

git commit -a -m "Style Bob's cat"
git checkout main
git pull
git merge style-cat

Y ahí está: el temido conflicto de combinación. Dos personas han cambiado la misma línea en el mismo archivo. Git detecta el conflicto y notifica un error de combinación automática. Git no tiene forma de saber si el atributo src del elemento <img> debe hacer referencia a los archivos bobcat2-317x240.jpg o bombay-cat-180x240.jpg.

Resultados

Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
La salida de Git identifica el archivo index.html como origen del conflicto.

La pregunta ahora es: ¿Qué puede hacer Bob?

Resolución del conflicto de combinación
Bob tiene pocas opciones en este momento. Bob puede realizar una de estas acciones:

Ejecute el comando git merge --abort para restaurar la rama main a su estado anterior a la combinación intentada. Ejecute el comando git pull para obtener los cambios de Alice. A continuación, cree una rama, realice los cambios y combine su rama con la rama main. Por último, envían los cambios.
Ejecute el comando git reset --hard para volver a la ubicación en la que estaban antes de que iniciaran la combinación.
Resuelva el conflicto manualmente mediante la información que Git inserta en los archivos afectados.
Los desarrolladores parecen preferir la última opción. Cuando Git detecta un conflicto en las versiones del contenido, inserta ambas versiones del contenido en el archivo. Git usa un formato especial para ayudarle a identificar y resolver el conflicto: corchetes angulares de apertura <<<<<<<, guiones dobles (signos igual) ======= y corchetes angulares de cierre >>>>>>>. El contenido situado encima de la línea de guiones ======= muestra los cambios en la rama. El contenido que se encuentra debajo de la línea de separación muestra la versión del contenido de la rama en la que intenta realizar la combinación.

Este es el aspecto ahora del archivo index.html del repositorio de Bob. Tenga en cuenta el formato especial que rodea el contenido con conflictos:

HTML

<!DOCTYPE html>
<html>
  <head>
    <meta charset='UTF-8'>
    <title>Our Feline Friends</title>
    <link rel="stylesheet" href="CSS/site.css">
  </head>
  <body>
    <nav><a href="./index.html">home</a></nav>
    <h1>Our Feline Friends</h1>
    <<<<<<< HEAD
    <img class="cat" src="Assets/bombay-cat-180x240.jpg">
    =======
    <img class="cat" src="assets/bobcat2-317x240.jpg">
    >>>>>>> style-cat
    <footer><hr>Copyright (c) 2021 Contoso Cats</footer>
  </body>
</html>
Vamos a resolver el conflicto de combinación mediante la edición del archivo index.html. Dado que este conflicto de combinación se corrige rápidamente, realizará el cambio directamente en la rama main, aunque todavía esté en el directorio Bob.

Abra el archivo index.html y, a continuación, elimine las líneas de formato especiales. No quite ninguna otra instrucción.

HTML

<<<<<<< HEAD
=======
>>>>>>> style-cat
Guarde el archivo y cierre el editor.

El archivo index.html ahora tiene dos elementos <img>: uno para la imagen del gato de Bob y otro para la del gato de Alice.

Algunos editores de texto incluyen la integración de Git y ofrecen ayuda cuando ven texto que indica un conflicto de combinación. Si abre el archivo index.html en Visual Studio Code, verá el código siguiente:

Screenshot that shows how to resolve merge conflicts in Visual Studio Code.

Si selecciona Aceptar ambos cambios, el editor quita las líneas alrededor de los elementos <img> y los dos elementos permanecen intactos.

Ejecute los comandos siguientes para confirmar el cambio:

Bash

git add index.html
git commit -a -m "Style Bob's cat"

El comando git add indica a Git que se ha resuelto el conflicto en el archivo index.html.

Envíe los cambios a la rama main en el repositorio remoto:

Bash

git push

Ahora, sincronice los cambios con el repositorio de Alice:

Bash

cd ../Alice
git pull

Por último, abra el archivo index.html de Alice y confirme que su versión también tiene dos etiquetas <img> con imágenes de gatos.

### crear una rama apartir de otra y cambiar a ella
git checkout -b <nombre de la rama> <nombre de la rama base>

### cambiar de rama
git checkout <nombre de la rama>

### fusionar una rama con otra
git merge <nombre de la rama>

### eliminar una rama en local y en remoto
git branch -d <nombre de la rama>
git push origin --delete <nombre de la rama>

### ver las ramas
git branch

### ver las ramas en local y en remoto
git branch -a

### ver las ramas en remoto
git branch -r

### ver las ramas que se han fusionado
git branch --merged

### agregar un archivo al stage y agregar todos los archivos al stage
git add <nombre del archivo>
git add .

### confirmar los cambios
git commit -m "mensaje"

### enviar los cambios al repositorio remoto o a una rama en concreto
git push
git push origin <nombre de la rama>

### traer los cambios del repositorio remoto o de una rama en concreto
git pull
git pull origin <nombre de la rama>

