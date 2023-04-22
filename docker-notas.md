# DOCKER
Curos de Platzi, Guido Vilariño

**Docker** es una plataforma que permite _construir, ejecutar y compartir_ aplicaciones mediante **contenedores**. Docker corre de forma nativa en Linux.  

**Estructura de Docker**
![Image sample](./images/DockerEngine.png)

## Concepto de contenedor
Es la base fundamental de Docher, hace las veces de una máquina virtual liviana.

* Es una agrupación de procesos.

* Es una entidad lógica, no tiene el limite estricto de las máquinas virtuales, emulación del sistema operativo simulado por otra más abajo.

* Ejecuta sus procesos de forma nativa y aislados del resto del sistema, Docker no le permite ver más allá.

* Los procesos que se ejecutan adentro de los contenedores ven su universo como el contenedor lo define, no pueden ver mas allá del contenedor, a pesar de estar corriendo en una maquina más grande. No tienen forma de consumir más recursos que los que se les permite. Si esta restringido en memoria ram por ejemplo, es la única que pueden usar.

* Sector del disco: Cuando un contenedor es ejecutado, el daemon de docker le dice, a partir de acá para arriba este disco es tuyo, pero no puedes subir mas arriba.

* Cada contenedor tiene un ID único y un nombre.


- ´docker exec -it db bash´ abro el docker db en modo bash. Puedo ingresar al docker

## Manejo de datos
### Bind mounts  
Compartir una carpeta entre la maquina anfitriona y el docker. Tiene la limitacion de que el docker puede acceder a los datos locales

### Volumes  
Es una evolución de bind mounts. Son volumenes que corrigen los problemas de seguridad. Es gestionado enteramente por docker y sólo tenemos acceso con permisos especiales
- ´docker volume ls´ lista los volumes actuales
- ´docker volume create mydata´  crea un volume mydata
- ´docker run -d --name db --mount src=dbdata,dst=/data/db mongo´ se crea un docker de mongo con un volumen dbdata en /data/db. Si el volume src=sbdata no existe, se crea
- `docker inspect db´ inspecciona el docher db. Se ve los volume montados

