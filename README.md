## _// Tutorial //_ ##
## Cómo vincular clave SSH a GitHub
> Crear una llave SSH no solo es la forma más rápida de trabajar con tus repositorios en GitHub, es también la forma más segura y recomendada en los entornos de desarrollo profesionales.

##### ¿Que es una llave SSH?
Una llave SSH es una clave que te permitirá autenticarte ante un servicio, en este caso, GitHub. Por lo general vienen 2 llaves: una pública y una privada. Con la pública puedes enviar y recibir información cifrada de la web, mientras que con la privada puedes descifrar esa información para poder su contenido.
_Nunca compartir una clave privada_

##### ¿Cómo crear un llave SSH?
Para crear una llave SSH, simplemente ejecuta este comando:
``` 
ssh-keygen
```
o
```
ssh-keygen -t rsa -b 4069
```
No incluir passphrase

##### Vincular llave SSH con GitHub

Para poder vincular la llave SSH con tu cuenta de GitHub debes ir a:
Tu perfil (click en tu avatar) -> Opción settings -> En la barra izquierda seleccionas la opción SHH Keys and GPG Keys
Una vez allí, seleccionas la opción New SSH Key

En la opción title te recomiendo poner un título descriptivo, por ejemplo: PC de John, PC de trabajo (nombre de empresa), etc... Y en la opción Key deberás pegar tu llave pública. Para eso, vamos a la consola y ejecutamos este comando:
```
cat ~/.ssh/nombre_key.pub
```
Le das en la opción Add SSH Key y ya está creada la clave SSH en GitHUb.
Y eso es todo. Ya puedes clonar repositorios mediante llaves SSH sin ningún tipo de problema con la opción de clonar mediante SSH.
```
git clone -b branch git@github.com:daybar4/docker-essentials-1.git ./destino
```

__________________________________________________________________

## Cómo instalar y usar Docker en Ubuntu
Introducción
> Docker es una aplicación que simplifica el proceso de administración de procesos de aplicación en contenedores. Los contenedores le permiten ejecutar sus aplicaciones en procesos con aislamiento de recursos. Son similares a las máquinas virtuales, pero los contenedores son más portátiles, más flexibles con los recursos y más dependientes del sistema operativo host.

> En este tutorial, instalará y usará Docker Community Edition (CE) en Ubuntu. Instalará Docker, trabajará con contenedores e imágenes e introducirá una imagen en un repositorio de Docker.

[DockerHUb] - https://hub.docker.com/

### Instalación
Primero, actualice su lista de paquetes existente:
```
sudo apt update
```

A continuación, instale algunos paquetes de requisitos previos que permitan a apt usar paquetes a través de HTTPS:
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
Luego, añada la clave de GPG para el repositorio oficial de Docker en su sistema:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
Agregue el repositorio de Docker a las fuentes de APT:
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
A continuación, actualice el paquete de base de datos con los paquetes de Docker del repositorio recién agregado:
```
sudo apt update
```
Por último, instale Docker:
```
sudo apt install docker-ce
```
Con esto, Docker quedará instalado, el demonio se iniciará y el proceso se habilitará para ejecutarse en el inicio. Compruebe que funcione:
```
sudo systemctl status docker
```