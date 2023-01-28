# UNIX WORKBENCH
Notas de curso en Coursera

## Creation and inspection
 - `tail/head` visualiza las 10 líneas de la cabecera/cola de un archivo. `tail archivo.txt -n 20` 20 líneas  
 - `less` explora todo el archivo. Con `/` hace busqueda. Con `q` termina
 - `wc` word count. Cuenta filas, oalabras y # caracteres en un archivo
 `wc leanme.txt`
 - `help/man cmd` Ayuda o manual de un comando
 - `nautilus` En linux abre el explorador de carpetas. Se le puede pasar argumento de wd
 - `du -sh * | sort -hr Lista en orden y con tamaño las carpetas y archivos 

## Redireccionamiento  
Cualquier programa tiene un flujo de entrada de datos “STANDAR INPUT” = “<”, un flujo de salida “STANDAR OUTPUT” = “>” o “1>” y un modo de capturar errores “STANDAR ERROR” = “2>”. En la terminal, podemos tener este mismo flujo de datos gracias a: “<” , “>” y “2>”.
  - `cmd > output.txt` redirecciona la salida del comando (standar output) al archivo output.txt   
  - `cmd > output.txt > 2>&1` redirecciona standar output o stanndar error al archivo output.txt  

### Pipe 
The pipe (|) takes the output of the program on its left side and directs the output to be the input for the program on its right side.  
 - `ls -lh > out2.txt | less` guara la salida de ls en out2 y lo visualiza 

### Encadenando comandos
 - `cmd1; cmd2; cmd3` ejecuta comandos de manera sincrona, es decir, primero cmd1, luego cmd2, ...  
 - `cmd1 & cmd2 & cmd3` ejecuta comandos de manera asincrona. Crea un hilo de procesamiento por cada cmd. 
 - `cmd1 && cmd2` ejecucion condicional. Se ejecuta cmd2 solo si se ejecuta cmd1. && haces las veces de AND logico. Se puede utilizar el OR como ||

### Permisos de un archivo (chmod)

`chmod [simboloDelUsuario][operador][permiso] [archivoParaCambiarSusPermisos]`  
* Simbolo de usuario: u (user, owner), g (group), o (others), a (todos)
* operador. + añade permiso, - quita, = asigna (sobreescribe)  
* permiso. r lectura, w escritura, x ejecucion
* Ejemplo ls -l: -rw-rw-r-- 1 user group file - archivo (d dir), rw- permiso user, rw- permiso group, r-- permisos otros

 - `chmod g+w archivo` le asigna permisos de escritura al grupo  
 - `chmod go+wx [archivo]` permiso de escritura y ejecucion al grupo y a otros  
 - `sudo chown user2: file` cambia de propietario file a user2

### Search

- `grep 'key' file.txt` busca key in file. También puedo buscar en multiples archivos con grep 'key' FILE_PATTERN`
- `grep -rnw . -e 'pattern'` busca de manera reiterativa un patron en todos los archivos de la carpeta
- `egrep 'key' file.txt` extención de grep con soporte de multicaracteres 
  - `-n` display de line number 
  - `egrep "^[AEIOU]{1}.+[aeiou]{1}$" states.txt` state names that both begin and end with a vowel
- `find` busca archivos
  - `find . -name "*.jpg"` Busca en directorio local todos los archivo jpg

### Manejo de procesos
- `ps` lista los procesos y sus ID en curso
- `ps aux` 
- `sudo ps auxf | sort -nr -k 3 | head -5` muestras los 5 procesos que más consumen CPU
- `sudo ps auxf | sort -nr -k 4 | head -5` muestras los 5 procesos que más consumen RAM
- `kill PID` termina un proceso
- `top` lista los procesos organizados por demanda de recursos
- `sudo du -hsc *` muestra consumo en disco de los directorios actuales 


Trabajar en background
- `nohub script &` ejecuta el comando en background y genera un archo nohub.out con la salida

### Variables de entorno  

- `printenv`  Imprime las variables de entorno
- `echo $PATH` imprime las rutas de los binarios del sistema

En la carpeta /usr/local/bin se encuentran todos los link simbolicos del sistema. Esta carpeta se encuentra en el $PATH.  

- `ln -s Documents/Dev Dev`  Crea link simbolico. Cuando ejecute `Dev` se va a la carpeta que apunta
- `rm Dev` elimina el link sumbolico

En Mac se puede editar las variables de entorno modificando el archivo .zshrc. 

``` bash
.zshrc

MY_VAR="hola mundo" #crea una nueva variable de entorno
alias <nombre>="comando" #crea un alias para un comando
PATH=$PATH:/home/program/bin #agrega una ruta para la variable path
```




## Script

### Arguments 
The first argument to your script is stored in $1, the second argument is stored in $2, etc. An array of all of the arguments passed to your script is stored in $@

### Conditional, If and Else
- All Bash programs have an exit status. true has an exit status of 0 and false has an exit status of 1.

- Conditional execution uses two operators: AND (&&) and OR (||) which you can use to control what command get executed based on their exit status.

- Conditional expressions are always in double brackets ([[ ]]). They have exit an exit status of 0 if they contain a true assertion or 1 if they contain a false assertion.

- IF statements evaluate conditional expressions. If an expression is true then the code within an IF statement is executed, otherwise it is skipped.

- ELIF and ELSE statements also help control the flow of a Bash program, and IF statements can be nested within other IF statements.

### Functions
- Functions start with the function keyword followed by the name of the function and curly brackets ({}).

- Functions are small, reusable pieces of code that behave just like commands.

- You can use variables like $1, $2, and $@ in order to provide arguments to functions, just like a Bash script.

- Use the source command in order to read in a Bash script with function definitions so that you can use your functions in your shell.

- Use the local keyword to prevent your function from creating or modifying global variables.

- Be sure to echo the results of your function (if there are any) so that they can be captured with command substitution.