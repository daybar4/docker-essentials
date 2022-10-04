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

## Subir un cambio
Se detecta un cambio en el repositorio local.
```
git add .
```
Hacemos un comit, captura una instantánea de los cambios preparados en ese momento del proyecto.
```
git commit -m 'mensaje'
```
Cargar contenido del repositorio local a un repositorio remoto.
```
git push
```