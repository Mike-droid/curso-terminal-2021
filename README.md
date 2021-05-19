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
