# UNIX WORKBENCH
Notas de curso en Coursera basado en el [libro](https://seankross.com/the-unix-workbench/) _The Unix Workbench_ de Sean Kross.  
Además de otras fuentes varias.

Jon Duque

## Creation and inspection
- `ls` listar ficheros,archivos
 - `ls -al` lista archivos ocultos
 - `ls -al | wc -l` contabiliza numero total de archivos en carpeta 	
- `tail/head` visualiza las 10 líneas de la cabecera/cola de un archivo. `tail archivo.txt -n 20` 20 líneas  
- `less` explora todo el archivo. Con `/` hace busqueda. Con `q` termina
- `wc` word count. Cuenta filas, oalabras y # caracteres en un archivo
 `wc leanme.txt`
- `help/man cmd` Ayuda o manual de un comando
- `nautilus` En linux abre el explorador de carpetas. Se le puede pasar argumento de wd
- `du -sh *` lista las carpetas actuales con el peso total en el sistema
- `du -sh * | sort -hr` Lista en orden y con tamaño las carpetas y archivos 
- `sudo du -hsc *` muestra consumo en disco de los directorios actuales 


## Redireccionamiento  
Cualquier programa tiene un flujo de entrada de datos *STANDAR INPUT: <*, un flujo de salida “STANDAR OUTPUT” = “>” o “1>” y un modo de capturar errores “STANDAR ERROR” = “2>”. En la terminal, podemos tener este mismo flujo de datos gracias a: “<” , “>” y “2>”.
  - `cmd > output.txt` redirecciona la salida del comando (standar output) al archivo output.txt   
  - `cmd > output.txt > 2>&1` redirecciona standar output o stanndar error al archivo output.txt  

### Pipe 
The pipe (|) takes the output of the program on its left side and directs the output to be the input for the program on its right side.  
 - `ls -lh > out2.txt | less` guara la salida de ls en out2 y lo visualiza 

### Encadenando comandos
 - `cmd1; cmd2; cmd3` ejecuta comandos de manera sincrona, es decir, primero cmd1, luego cmd2, ...  
 - `cmd1 & cmd2 & cmd3` ejecuta comandos de manera asincrona. Crea un hilo de procesamiento por cada cmd. 
 - `cmd1 && cmd2` ejecucion condicional. Se ejecuta cmd2 solo si se ejecuta cmd1. && haces las veces de AND logico. Se puede utilizar el OR como ||

## Manejo de usuarios y grupos

### Usuarios
El comando _id_ nos muestra el identificador único (uid) de cada usuario en nuestro sistema operativo. El ID 0 está reservado para el usuario root.

`whoami` retorna el usuario  actual.  
 Podemos ver todos los usuarios del sistema leyendo el archivo */etc/passwd* `cat /etc/passwd`.  
 En el archivo */etc/group* esta la info de los grupos

- `sudo adduser nombre-usuario` crea un nuevo usuario con contraseña y más información. También creará una nueva carpeta en  */home/*.
- `userdel nombre-usuario` eliminar cuentas de usuarios.
- `usermod` modificar la información de alguna cuenta.
- `passwd` cambia el password del ususario actual. 
- `sudo passwd user` cambia el password del ususario _user_


Nunca modificar directamente archivo _/etc/passwd_. Para administrar los usuarios se debe hacer mediante los comandos.

### Grupos
`cat etc/group` lista los grupos existentes

- `groups` lista los grupos en los que esta el usuario actual
- `groups user` lista los grupos en los que esta el usuario _user_
- `sudo groupadd <new_grupo>` crear un nuevo grupo en el sistema
- `sudo groupdel <ngrupo>` elimina _ngrupo_
- `sudo usermod -aG <grupo> <nuser>` asocia _nuser_ al grupo _grupo_
- `sudo gpasswd -a/-d user group` asocia (-a) o elimina (-d) el ususario _user_ al grupo _group_

## Permisos de un archivo (chmod)

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
  - `$ find . -type d -empty -print` Busca e imprime las carpetas vacias, recursivo
  - `$ find . -type d -empty -delete` Elimina las carpetas vacias de manera recursiva para el dir actual
  - `find . -type d -empty | wc -l` Cuenta carpetas vacías


## Manejo de procesos/recursos

- `ps` lista los procesos y sus ID en curso
- `ps aux` 
- `pgrep -f "python"` obtiene los PID de los procesos que coincidan con _python_
- `sudo ps auxf | sort -nr -k 3 | head -5` muestras los 5 procesos que más consumen CPU
- `sudo ps auxf | sort -nr -k 4 | head -5` muestras los 5 procesos que más consumen RAM
- `kill PID` termina un proceso
- `top` lista los procesos organizados por demanda de recursos
- `sudo du -hsc *` muestra consumo en disco de los directorios actuales 

**Conocer los recursos de la máquina**   
- `free -g` Muestra en Gb la memoria RAM total/disponibe  
- `sudo lscpu` CPU total en la máquina  
- `sudo lshw` muestra información detallada sobre el hardware del sistema  
- `nvidia-smi` muestra resumen de GPU Nvidia de tenerla instalada 

### Limitar recursos de hardware a un usuario con _cgroup_
Se puede limitar el uso de recursos para ciertos procesoso o para un usuario especifico.
[Ver tutorial1](https://towardsdatascience.com/the-power-of-linux-cgroups-how-containers-take-control-of-their-resources-ba564fef13b0)
[Tuto 2](https://linuxaria.com/article/introduction-to-cgroups-the-linux-conrol-group)
  
`sudo apt install cgroup-tools` instala _cgroups_

1. Crear un nuevo grupo de control de recursos (cgroup) _user-limite_. limites para CPU (40%) y RAM (16Gb)  
`sudo cgcreate -g cpu,memory:/grupo_limites`
`sudo cgset -r cpu.cfs_quota_us=40000 -r memory.limit_in_bytes=16G grupo_limites`
2. Asignar todos los procesos de ese usuario al cgroup creado. 
`ps -u <user> -o pid= | awk '{print $1}' | xargs sudo cgclassify -g cpu,memory:grupo_limites`  

El comando `ps -u <nombre de usuario> -o pid=` devuelve una lista de los PIDs de los procesos del usuario, y el comando `awk '{print $1}'` filtra sólo los PIDs y los pasa a `xargs`, que a su vez pasa cada PID a `cgclassify` para agregarlo al cgroup.

Para comprobar qué procesos están siendo controlados dentro de un cgroup específico, puede utilizar el comando `cgps -g cpu,memory:/x_cgroup`, que muestra una lista de los procesos en el cgroup junto con su uso actual de recursos.

* Listar los cgroups existentes.  
`sudo cgget -g cpu,memory`   
* Listar los procesos controlados en un cgroup.  
`sudo cgexec -g cpu,memory:/monai_lims -- lsof -p 1`
* Eliminar un cgroup o detener los procesos controlados en un cgroup.  
`sudo cgdelete -g cpu,memory:/monai_lims`

_Nota:_ Estos códigos están sujetos a verificación ya que fueron creados con chatGPT


### Trabajar en background
- `nohub script &` ejecuta el comando en background y genera un archo nohub.out con la salida

## Manejo de variables de entorno  

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