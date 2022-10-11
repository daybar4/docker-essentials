## _// Tutorial //_ ##

# MAINTAINER
- Name: David Aybar
- Email: daybar4@gmail.com

## Cómo instalar y usar Docker en Ubuntu
Introducción
> Docker es una aplicación que simplifica el proceso de administración de procesos de aplicación en contenedores. Los contenedores le permiten ejecutar sus aplicaciones en procesos con aislamiento de recursos. Son similares a las máquinas virtuales, pero los contenedores son más portátiles, más flexibles con los recursos y más dependientes del sistema operativo host.

> En este tutorial, instalarás y usarás Docker Community Edition (CE) en Ubuntu. Instalarás Docker, trabajarás con contenedores e imágenes e introducirás una imagen en un repositorio de Docker.

[DockerHUb] - https://hub.docker.com/

### Instalación
Primero, actualizar la lista de paquetes existente:
```
sudo apt update
```

A continuación, instalar algunos paquetes de requisitos previos que permitan a apt usar paquetes a través de HTTPS:
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
Luego, añadir la clave de GPG para el repositorio oficial de Docker en su sistema:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
Agregar el repositorio de Docker a las fuentes de APT:
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
Para Ubuntu LTS 22, añadir la siguiente clave y repositorio en vez de la anterior:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
A continuación, actualizar el paquete de base de datos con los paquetes de Docker del repositorio recién agregado:
```
sudo apt update
```
Por último, instalar Docker:
```
sudo apt install docker-ce
```
Con esto, Docker quedará instalado, el demonio(servicio) se iniciará y el proceso se habilitará para ejecutarse en el inicio. Comprobar que funciona:
```
sudo systemctl status docker
```

### Ejecutar el comando Docker sin sudo
Por defecto, el comando docker solo puede ser ejecutado por el usuario root o un usuario del grupo docker, que se crea automáticamente durante el proceso de instalación de Docker. Si intentas ejecutar el comando docker sin sudo como prefijo o sin formar parte del grupo docker, obtendrás un resultado como este:

```
Output
docker: Cannot connect to the Docker daemon. Is the docker daemon running on this host?.
See 'docker run --help'.
```

Si deseas evitar escribir sudo al ejecutar el comando docker, agregar el nombre de usuario al grupo docker:
```
sudo usermod -aG docker ${USER}
```
Para aplicar la nueva membresía de grupo, cerrar la sesión del servidor y volver a iniciarla o escribir lo siguiente:
```
su - ${USER}
```
Para continuar, añadir la contraseña del usuario.
Confirmar que ahora el usuario se agregó al grupo docker escribiendo lo siguiente:
```
id -nG
```
```
Output
sammy sudo docker
```

## Cómo instalar y usar Docker Compose en Ubuntu
Introducción
> Docker simplifica el proceso de administración de los procesos de las aplicaciones en contenedores. Aunque los contenedores son similares a las máquinas virtuales de cierta forma, son más ligeros y más sencillos en cuanto a recursos. Esto permite a los desarrolladores desglosar un entorno de aplicación en varios servicios aislados.

> Para las aplicaciones que dependen de varios servicios, organizar todos los contenedores para que se inicien, comuniquen y se apaguen juntos puede convertirse rápidamente en algo difícil de manejar. Docker Compose es una herramienta que le permite ejecutar entornos de aplicación multi contenedor según las definiciones establecidas en un archivo YAML. Se utilizan definiciones de servicio para crear entornos totalmente personalizables con varios contenedores que pueden compartir redes y volúmenes de datos.

> En esta guía, mostraremos cómo instalar Docker Compose en un servidor Ubuntu

### Instalar Docker Compose
Para asegurarnos de que obtenemos la versión estable más reciente de Docker Compose, descargaremos este software de su repositorio oficial de Github.

Primero, confirmamos la versión más reciente disponible en su página de versiones. En el momento de escribir este artículo, la versión estable más reciente es v2.11.2: https://github.com/docker/compose/releases

```
sudo apt install docker-compose
```

Para verificar que la instalación se realizó correctamente:
```
docker-compose --version
```
