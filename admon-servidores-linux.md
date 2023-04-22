# Administración de servidores linux

Notas del curso de Platzi

## Habilidades y Roles de un Administrador
###Habilidades clave:

* Control de accesos.
* Monitoreo del sistema.
* Administración de recursos.
* Troubleshooting.
* Instalación y mantenimiento de software.
* Creación de respaldos.
* Documentación.

* ### Roles que puedes desempeñar:

* _DevOps Engineer:_ Se enfocan en los procesos y metodologías para la correcta liberación en el proceso de desarrollo de software.
* _Site Reliability Engineer:_ Se enfocan en que los sistemas de software operen de manera correcta y con el mayor grado de confiabilidad posible.
* _Security Operations Engineer:_ Encargados de mantener la seguridad de los sistemas a nivel de red y aplicaciones.
* Algunos otros roles:
	* Network Engineer.
	* Database Administrator.
	* Network Operation Center Engineer.
	* MLOps Engineer.
	* Cloud Engineer.

## Arquitectura de un sistema Unix/Linux
Se divide típicamente en cuatro capas:
 ((((Hardware) Kernel) SO) Aplicacioens)

1. Nivel de hardware: este nivel se refiere al hardware físico del sistema, que incluye la CPU, la memoria, los dispositivos de almacenamiento, la tarjeta de red, etc.

2. Nivel de kernel: esta capa es la que está más cerca del hardware y es responsable de administrar los recursos del sistema, como la memoria y los dispositivos de entrada/salida. El kernel también proporciona una interfaz entre el software del sistema y el hardware subyacente.
 
3. Nivel de sistema operativo: esta capa incluye los componentes del sistema operativo que se ejecutan en el nivel del usuario, como los controladores de dispositivos, el administrador de archivos, el shell de línea de comandos, la interfaz gráfica de usuario, etc.

4. Nivel de aplicación: esta capa es la que está más cerca del usuario final y se compone de las aplicaciones y servicios que se ejecutan en el sistema operativo, como navegadores web, editores de texto, reproductores multimedia, servidores web, etc.

## Sistemas operativos y distribuciones

Una distribución de Linux es una variante de Linux creada por una organización o comunidad específica que toma el kernel de Linux y lo combina con otras aplicaciones y herramientas de software para crear un sistema operativo completo. Las distribuciones de Linux pueden variar en características, propósitos y enfoques.

Hay muchas distribuciones de Linux disponibles, y algunas de las más populares son:

Rolling Release:  
* Arch Linux
* Gentoo
* Solus
* Manjaro
* openSUSE Tumbleweed

Fixed Release:
* Debian
* Ubuntu
* CentOS
* Fedora
* Red Hat Enterprise Linux (RHEL)

Las distribuciones de Rolling Release reciben actualizaciones continuas y no tienen versiones específicas. Las actualizaciones se entregan a medida que se lanzan y se prueban. Las distribuciones de Fixed Release, por otro lado, tienen una versión específica que se lanza en un momento determinado y reciben actualizaciones de seguridad y mantenimiento regulares, pero no se actualizan con nuevas características de forma regular.

Cada distribución de Linux tiene su propia comunidad de usuarios y su propia filosofía y enfoque. La elección de una distribución de Linux depende de las necesidades y preferencias individuales del usuario, como el propósito de la distribución, el nivel de experiencia técnica del usuario y las características específicas que se buscan.


## SFTP to Securely Transfer Files with a Remote Server

[Ref](https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server#how-to-connect-with-sftp)

SFTP, which stands for Secure File Transfer Protocol, is a separate protocol packaged built into SSH that can implement FTP commands over a secure connection. Typically, it can act as a drop-in replacement in any contexts where an FTP server is still needed.

###How to Connect with SFTP

By default, SFTP uses the SSH protocol to authenticate and establish a secure connection. Because of this, the same authentication methods are available that are present in SSH.

`sftp user@your_server_ip_or_remote_hostname`

* `sftp> help` menú ayuda. 
* `sftp> ls cd pwd` navegación en server
* `sftp> lls lcd lpwd` navegación en maquina local
* `sftp> get [-r] remoteFile [dir]` dowload remote file or dir (-r)
* `sftp> put [-r] localFile [dir]` upload remote file or dir (-r)
* `sftp> !/exit` !: pasar a local terminal, exit: volver a sftp