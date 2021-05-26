# Curso de Introducción a la Terminal y Línea de Comandos

## Primeros pasos

### ¿Qué es la terminal?

4 razones para aprender a usar la terminal:

1. Flexibilidad -> Podemos hacer grandes procesos en la computadora de una manera eficaz.
2. Velocidad -> Hacer cosas en la terminal es mucho más rápida que en una GUI.
3. No siempre cuentas con una interfaz gráfica
4. Puedes invocar demonios 😈 -> Si no sabes usar bien la terminal puedes provocar grandes daños.

- Terminal: Ventanita que nos muestra el prompt. Este aloja a la shell.
- Línea de comandos (shell): Un programa que toma comandos y los pasa al sistema operativo para hacer algo.
- Comando: Un programa que se puede ejecuta desde la terminal. Este puede recibir parámetros y opciones.

### Aprendiendo a caminar en la terminal

Todo inicia desde '/'. Es la raíz del sistema de archivos.

- /
  - etc
  - dev
  - home -> Aquí se almacena la información del usuario del S.O.
    - jono
      - work
      - photos
    - mako
    - cory
  - usr
    - lib
  - var

Comandos:

- `ls` lista los archivos
- `ls -lh` lista los archivos de forma más humana
- `cd` change directory, cambia de directorio
- `clear` limpia la pantalla, también podemos usar `ctrl + l`
- Podemos escribir opciones con `-`
- Con las arrow de arriba y abajo podemos ver los comandos que hemos usado
- `cd` sin parámetros nos lleva a home
- `pwd` nos muestra la ruta del directorio en donde estamos
- Podemos copiar texto con el click derecho o `ctrl + shift + c`
- Para pegar hacemos `ctrl + v`
- Con `.` nos referimos al directorio actual
- Con `..` nos referimos al directorio de atrás

### Manipular archivos y directorios

- `ls -la` muestra TODOS los archivos
- `ls -lS` ordena los documentos del por tamaño de peso, el más pesado va arriba de todos
- `ls -lr` ordena de menos pesado a más pesado
- `mkdir nombreCarpeta` crea una carpeta con su nombre
- `touch nombreArchivo` crea un archivo
- `cp nombreArchivo nombreNuevo` copia un archivo y crea otro
- `mv archivo directorio` mueve un archivo hacía el directorio indicado
- `mv nombreArchivo nombreArchivoNuevo` reemplaza el nombre de un archivo por otro ``nombre
- `rm archivo` **COMANDO PELIGROSO** borra totalmente de la existencia a un archivo
- `rm -i archivo` Aquí nos hará una pregunta para confirmar si en verdad queremos eliminar un archivo
- `rm -ri` Elimina directorio con sus archivos internos
- `rm -rf` ***COMANDO SUPER PELIGROSO*** va a borrar TODO sin importar nada, ***NO SE RECOMIENDA USARLO***

### Explorando el contenido de nuestros archivos

- `head nombreArchivo -n numero` te muestra las primeras 10 líneas (o las que indiques) de un archivo de texto
- `tail nombreArchivo -n numero` te muestra las últimas 10 líneas (o las que indiques) de un archivo de texto
- `less nombreArchivo` es una interfaz para leer y editar archivos de texto, con `/` podemos buscar texto específico. Con 'q' salimos de less.
- `cat nombreArchivo` muestra todo el contenido del archivo.
- Matamos procesos con `ctrl + c`

### ¿Qué es un comando?

Puede ser 4 cosas:

1. Un programa ejecutable.
2. Un comando de utilidad de la shell.
3. Una función de shell.
4. Un alias.

- `type nombreComando` te muestra la definición del comando.
- Para crear alias usamos -> `alias nombreDelAlias="comando de linux"`
- `help nombreComando` (no funciona en zsh) te da ayuda de un comando
- `man nombreComando (no funciona en zsh)` es un manual para el comando
- `info nombreComando (no funciona en zsh)` casi lo mismo que man
- `whatis nombreComando (no funciona en zsh)` te da información en 1 línea
- `echo $0` te permite saber qué shell estás usando

### Wildcards

Son caracteres especiales que nos permiten encontrar patrones o realizar búsquedas mucho más avanzadas.

- `ls *.txt` -> Nos mostrará todos los archivos que **terminen** con la '.txt'
- `ls inicioNombreArchivo*` -> Nos mostrará todos los archivos que sus nombres empiecen con cierto texto y después tengan cualquier caracter
- `ls inicioNombreArchivo?` -> Nos mostrará todos los archivos que sus nombres empiecen con cierto texto y después tengan solamente 1 caracter (el número de '?' corresponde al número de caracteres)
- `ls [[:upper:]]*` -> Nos mostrará todos los archivos que empiecen con una letra mayúscula
- `ls -d [[:upper:]]*` -> Nos mostrará todos los directorios que empiecen con una letra mayúscula
- `ls  [[:lower:]]*` -> Nos mostrará todos los archivos que empiecen con una letra minúscula
- `ls -d [[:lower:]]*` -> Nos mostrará todos los directorios que empiecen con una letra minúscula
- `ls [letraletra]*` -> Nos mostrará todos los archivos que empiecen con la primera letra y todos los que empiecen con la segunda letra
- `ls *[:digit:]` -> Nos mostrará archivos que tengan números en sus nombres

[Cheatsheet de comandos útiles de linux](https://static.platzi.com/media/public/uploads/command-line-cheat-sheet_f2552bde-3bb0-4b1c-a1a7-dbd40095fa4f.pdf)

## Empezando a correr

### Redirecciones: cómo funciona la shell

Podemos hacer un "stdin" (standar input) a través de un comando o archivo y esté nos puede regresar ya sea un standar output o un error. Para redirigir algo usamos el símbolo ">" y luego ponemos el nombre del archivo al que lo queremos mandar. Sin embargo esto va a sobreescribir los cambios, si queremos que se concatenen tenemos que usar ">>".

- standar input tiene el valor de 0
- standar output tiene el valor de 1
- standar error tiene el valor de 2

Para redigir un error, podemos hacer por ejemplo: `ls asfgsah 2>error.txt`

Para redigir tanto un error como un ouput, debemos hacer, por ejemplo: `ls -l> output.txt 2>&1`

### Redirecciones: pipe operator

El pipe operator nos permite ejecutar un comando, que su standar output pase como standar input a otro comando.

- echo "mensaje" simplemente produce un output en la terminal.
- cat archivo1 archivo2 contatenará ambos outputs en la terminal.

- Podemos hacer por ejemplo `ls -lh | less`, aquí redirigimos el output a la terminal.
- `ls -lh | tee archivo.txt | less`, aquí creamos un archivo y luego redigirimos el output a la terminal.
- `ls -ls Pictures | sort | tee pictures.txt | less`, aquí creamos un archivo que ordena los resultados que obtuvo y al final muestra el output en la terminal.

### Encadenando comandos: operadores de control

Los operadores de control son símbolos en la terminal que nos permiten ejecutar más de 1 comando a la vez o encadenarlos. Podemos correr síncrona y asíncronamente e incluso con condicionales.

- `cal` nos muestra un calendario
- `date` nos muestra la fecha del día de hoy

Para ejecutar comandos síncronamente (uno detrás de otro) usamos ";" al final de cada comando. Para ejecutarlos asíncronamente usamos "&" al final de cada comando.

Para ejecutar comandos con condicionales usamos "&&" que es el operador lógico AND. Por ejemplo `mkdir test && cd test` -> Crea el directorio y entrará en él sólo si el primero se ejecutó de manera correcta.

También podemos usar "||", es el operador lógico OR.

### Cómo se manejan los permisos

#### Tipos de archivo

|Atributo|Tipo de archivo|
|--------|---------------|
|-|Un archivo normal.|
|d|Un directorio.|
|l|Un link simbólico.|
|b|Un archivo de bloque especial. Son archivos que manejan la información de los bloques de datos como una USB.|

#### Tipos de modo

|Dueño|Grupo|World|
|-----|-----|-----|
|rwx|r-x|r-x|
|111|101|101|

Aquí muestra los permisos que tienen distintas entidades sobre un archivo.

- r -> read
- w -> write
- x -> execute

[Diferencia de permisos entre archivos y directorios](https://static.platzi.com/media/public/uploads/diferencia-de-permisos-entre-archivos-y-directorios_677909ae-1b00-4a21-9a6a-8ecd389dc9db.docx)

Ya que los permisos usan 3 bits, podemos representarlos con el sistema numérico octal.

|Octal|Binario|Permisos|
|-----|-------|--------|
|0|000|---|
|1|001|--x|
|2|010|-w-|
|3|011|-wx|
|4|100|r--|
|5|101|r-x|
|6|110|rw-|
|7|111|rwx|

#### Modo simbólico

|Símbolo|Significado|
|-------|-----------|
|u|Sólo para el usuario|
|g|Sólo para el grupo|
|o|Sólo para otros(Es el world)|
|a|Aplica para todos|

### Modificando permisos en la terminal

Podemos otorgar y quitar permisos de la terminal con los valores octales y los valores simbólicos. Por ejemplo:

- `chmod u-r` -> Le quitamos al usuario el permiso de leer el archivo.
- `chmod u+r` -> Le otorgamos al usuario el permiso de leer el archivo.

Un comando un poco más avanzado:

- `chmod u-x,go=w mitexto.txt` -> Al usuario le quitamos el permiso de ejecución, al grupo y others le dimos el permiso de write.

- El comando `whoami` nos ayudará para saber quién somos, por si tenemos dudas existenciales en la terminal.
- Podemos cambiar de usuario con `su nombreDeUsuario`, por ejemplo `su root`
- El famoso comando `sudo` nos dará los permisos de root a nuestro usuario normal y la contraseña que pedirá para ejecutar los comandos es de nuestro usuario normal.

### Variables de entorno

Los links simbólicos son como darle un alias a una direccion en la computadora para acceder a ella más rápido. Por ejemplo: `ln -s Documents/Dev Desarrollo`. -> ln -s para decir que es un link simbólico, luego la ruta a donde iremos y finalmente el nombre que tendrá este link simbólico. Los links simbólicos no tienen permisos.

- `printenv` nos mostrará las variables de entorno de nuestra computadora.
- `echo $NombreDeVariable` nos mostrará una variable de entorno específica.

La variable de entorno PATH tiene las rutas de todos los binarios que se ejecutan en nuestro sistema. Esta variables es **MUY IMPORTANTE**.

En el archivo ".bashrc" tenemos guardadas las configuraciones de la terminal. Si es una terminal de ZSH, estarán en el archivo ".zsgrc"

Un alias muy útil para evitar escribir `git push origin main` es simplemente `alias gpom='git push origin main'`.

### Comandos de búsqueda

Podemos buscar el nombre, la extensión y la ubicación del archivo.

- El comando `which` busca en todas las rutas del PATH para encontrar un archivo binario.
- Para buscar usamos el comando `find`. Por ejemplo `find ./ -name *.txt` -> Buscará en el directorio actual todos los archivos, que su nombre termine con .txt
- Para buscar por tipos, podemos hacer `find ./ -type df nombreABuscar` -> "f" es para file y "d" es para directory
- Para buscar por tamaño de archivos, podemos usar `find ./ -size 20M` -> buscará archivos con tamaño de 20 Megabytes

### Su majestad grep

Grep nos permite encontrar coindidencias de una búsqueda dentro de un archivo de texto.

Por ejemplo: `grep Towers movies.csv` -> Buscará en el archivo de las películas, todas las coincidencias con la palabra "The". Hay que tomar en cuenta que grep es case-sensitive, es decir, no es lo mismo "The" que "the". Podemos hacer que ignore esto con `grep the -i movies.csv`.

También podemos contar cuántas veces aparece una cadena de texto usando `grep -c tower movies.csv`.

Incluso podemos traer resultados que NO cumplan con lo que buscamos. Lo hacemos con `grep -vi towers movies.csv`.

Finalmente, tenemos el comando `wc` (No, no es para el baño 🚽), significa Word Count y contará las palabras que haya en un archivo con texto. Como arroja 3 números, el primero es para las *líneas*, el segundo es para los  *caracteres* y el tercero es para el número de bits.

## Utilidades de la terminal

### Utilidades de red

- Para analizar la información de nuestra red usamos el comando `ifconfig`.
- Podemos hacer ping con el comando de `ping www.url.com`
- `curl www.url.com` nos trae un archivo de texto a través de la red.
- `wget www.url.com` nos trae mejor formateada la información de la página web.
- `netstat -i` trae la misma información que `ifconfig` pero resumida.

### Comprimiendo archivos

- Podemos comprimir archivos con `tar -cvf nombreQueTendraElArchivoComprimido.tar carpetaOArchivoAComprimir`
- Otra opción y que es más recomendad es lo mismo pero escribir .tar.gz 
- Para descomprimir el archivo tenemos que hacer `tar -xzvf nombreDelArchivoADescomprimir.tar.gz`
- También podemos comprir con zip, `zip -r nombreQueTendraElArchivo.zip carpetaAComprimir`
- Para descomprimir zip, simplemente hacemos `unzip nombreDelArcvhioADescomprimir.zip`

### Manejo de procesos


- `ps` nos muestra los procesos que se están ejecutando
- Cada proceso tiene un ID, algunos pueden detenerse con el comando `kill ID-del-proceso`
- `top` nos mostrará los procesos que más recursos usen, de forma descentente

### Procesos en foreground y background

Como viste en la clase de procesos podemos correr de manera asíncrona comandos, y si estos no se completan quedarán activos dentro de los procesos de la terminal.

Cuando un proceso está en ejecución sin que sea mostrado en la terminal se dice que se está ejecutando en el background. Si se muestra la ejecución del comando dentro de la terminal se dice que está en el foreground. En esta clase aprenderás a cómo mover los procesos del background al foreground a tu voluntad, incluso a cómo suspenderlos.

¿Te acuerdas del truco que aprendimos para tener un editor de texto supersencillo en la terminal? Lo usaremos en esta ocasión. Imagina que queremos una nota desde la terminal y para eso usamos:

`cat > mi_nota.txt`

Nuestra terminal tendrá el prompt esperando a que ingresemos texto.

Podemos escribir algo y después terminar el input del texto con CTRL+D, pero en esta ocasión no haremos eso. Lo que queremos hacer será suspender el proceso, esto lo podemos hacer con CTRL+Z. El resultado que nos mostrará la terminal deberá ser uno donde nos indique la suspensión del comando cat.

Ahora hemos movido nuestro comando exitosamente al background de la terminal. Para consultar todos los procesos que tenemos en background podemos hacerlo con el comando jobs.

A la izquierda aparece el número del trabajo ( ⚠ ️ cuidado que no es lo mismo que el process ID). Si queremos traer la ejecución de nuevo a la terminal, es decir, al foreground; debemos usar el comando fg y especificar qué número de trabajo queremos continuar. Para nuestro caso será el 1.

`fg 1`

En caso de que estés usando ZSH como shell el formato para llamar el trabajo sería con un porcentaje. ZSH tiende a interpretar algunas cosas incluyendo las wildcards de manera diferente.

`fg %1`

Una vez enviado al foreground veremos como se activa la ejecución del comando en la terminal y podremos seguir escribiendo nuestra nota. Recuerda que una vez terminemos de escribir presionamos CTRL+D para terminar el input y guardar.

Cuando se guarda nuestra nota nos daremos cuenta de que el proceso por fin termina y si usamos jobs no nos mostrará ningún trabajo en background.

#### Otras formas de enviar al background

Existen otras formas de enviar comandos al background. La primera es usando el operador de control & al final de un comando. Este operador nos permite enviar de manera directa un proceso al background una vez ejecutado. Por ejemplo:

`cat > mi_nota.txt &`

La segunda forma es con el comando bg. Este sirve de manera similar que fg solo que en vez de traerlo al foreground este lleva un trabajo al background. Por ejemplo:

`bg 1`

Bien, la pregunta ahora es ¿Cómo usamos bg? Imagina que abrimos algún programa de interfaz gráfica desde la terminal. En mi caso abriré el navegador Google Chrome. Para hacerlo desde la terminal solo ejecuta:

`google-chrome-stable`

Y verás como se ejecuta pero no nos deja hacer ninguna otra tarea ya que la ventana del navegador está abierta.

Para suspender el proceso como ya sabes lo hacemos con CTRL+Z y si revisamos con jobs veremos como el proceso se encuentra en pausa. En este caso la ventana del navegador que se abrió no nos dejará interactuar ni escribir en ella.

La diferencia entre `ctrl + C` y `ctrl Z` es que:

- `ctrl + C` mata a un proceso
- `ctrl + Z` suspende a un proceso

### Editores de texto en la terminal

vim es el más chido.

## examen

- Es un comando que nos ayuda a buscar la ruta de binarios o ejecutables en nuestro sistema: find
- ¿Con cuál comando copiamos un directorio y su contenido? (Esto hace parte de uno de los retos que te dejé): copy -r mi_directorio ruta_destino
- ¿Qué operador nos ayuda a concatenar la salida de un comando a un archivo de texto?: >>
- Es una mala práctica de seguridad asignar la siguiente configuración de permisos en modo octal a cualquier archivo o directorio: 777
- ¿Qué comando nos ayuda consultar la disponibilidad de un equipo en una red?: ifconfig
- El file descriptor correspondiente al stderr es: 2
- ¿Qué hace el comando pwd?: imprime la ruta actual de trabajo
- Si queremos listar todos los archivos que sean extensión txt podemos usar el comando: ls .*txt
- Si queremos explorar las primeras 100 líneas de un documento de texto lo podemos hacer con: head -n 100 mi_Texto | less
- ¿Qué comando muestra las últimas 5 líneas de texto de un documento?: tail -n 5 mi_texto
- Si queremos correr una serie de comandos de manera asíncrona lo hacemos con el operador: &
- ¿Qué comando muestra los procesos que consumen más recursos en nuestro sistema?: top
- La shell o línea de comandos es: un programa que nos ayuda a comunicarnos
- El pipe operator redirecciona la salida de un comando a la entrada de otro comando, esto es: verdadero
- Con el siguiente comando podemos ver la ruta del directorio Home de nuestro usuario: echo $HOME
- Si deseamos condicionar la ejecución de un comando solo si uno anterior se ejecuto de manera exitosa podemos usar: &&
- El comando chmod u=rwx,go=r mi_archivo ¿qué permisos otorga?: lectura, escritura, ejecución a 1 usuario, lectura y lectura solo a grupos
- Para leer el manual de usuario de un comando usamos: man
- find / -name *.png
- Para usar grep sin distinción de mayúsculas o minúsculas usamos: -i

