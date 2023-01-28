# DOCKER
Curos de Platzi, Guido Vilariño

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

