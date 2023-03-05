# MAINTAINER
- Name: David Aybar
- Email: daybar4@gmail.com
- Web: https://www.davidaybar.com/

## Trabajar con docker-compose.yml
> El archivo docker-compose.yml normalmente comienza con la definición de la versión. Esto indicará a Docker Compose qué versión de la configuración estamos usando.

> Luego tenemos el bloque services, donde configuramos los servicios que son parte de este entorno. En nuestro caso, tenemos un único servicio llamado web. Este servicio utiliza la imagen httpd:2.4 y establece una redirección de puerto con la directiva ports. Todas las solicitudes en el puerto 8000 del equipo host (el sistema desde el cual está ejecutando Docker Compose) serán redirigidas al contenedor web en el puerto 80, donde se ejecutará apache.

> La directiva volumes creará un volumen compartido entre el equipo host y el contenedor. Esto compartirá la carpeta app local con el contenedor, y el volumen se ubicará en /usr/local/apache2/htdocs dentro del contenedor, que luego sobreescribirá la raíz predeterminada del documento para apache.

> Hemos creado una página demo y un archivo docker-compose.yml para crear un entorno de servidor web en contenedor que lo presentará. En el siguiente paso, abriremos este entorno con Docker Compose.

## Proceso de instalación

Se expondrán los siguientes puertos:
- 8000: Apache TCP HTTP

### Clonemos el proyecto git al directorio actual
```
git clone <url-to-git-project>
```

### Cambiamos directorio a la ruta del proyecto
```
cd <to-project-directory>
```

### Generamos archivos docker-compose.yml, .env
```
cp docker-compose.yml.dist docker-compose.yml
```

Con el archivo docker-compose.yml implementado, ahora podemos ejecutar Docker Compose para mostrar nuestro entorno. El siguiente comando descargará las imágenes Docker necesarias, creará un contenedor para el servicio web y ejecutará el entorno en contenedor en modo segundo plano:
```
docker-compose up -d --build
```
El entorno ahora está funcionando en segundo plano. Para verificar que el contenedor está activo, puede ejecutar:
```
docker-compose ps
```
Ahora podemos acceder a la aplicación demo apuntando a localhost:8000
```
curl http://localhost:8000/
```
El volumen compartido que se ha configurado en el archivo docker-compose.yml mantiene los archivos de la carpeta app sincronizados con la raíz del documento del contenedor. Si se realiza algún cambio al archivo index.html, serán recogidos automáicamente por el contenedor y se reflejarán en el navegador cuando vuelva a cargar la página.

### Familiarizarse con los comandos de Docker Compose
Comando de docker-compose que se utiliza para verificar los registros producidos por el contenedor httpd, usar el comando logs:
```
docker-compose logs 
```
o
```
docker logs -f nombre_del_contenedor
```
Comando de docker-compose que se utiliza para ver la configuración local
```
docker-compose config
```
Comando de docker-compose que se utiliza para parar el contenedor, usamos el nombre del servicio declarado en docker-compose.yml, no el nombre del contenedor.
```
docker-compose stop web
```
Comando de docker-compose que se utiliza para eliminar los contenedores:
```
docker-compose down (la data persistida se guarda)
```
Comando de docker-compose que se utiliza para recrear un contenedor:
```
docker-compose up -d --force-recreate
```
En ocasiones añadiremos por ejemplo un nuevo volumen, para construirlo en el contenedor:
```
docker-compose up -d --build
```
Comando de Docker que se utiliza para ver contenedores parados:
```
docker ps -a
```
Comando de Docker que se utiliza para eliminar un contenedor:
```
docker rm nombre_del_contenedor
```
Comando de Docker que se utiliza para eliminar o borrar objetos o datos no utilizados:
```
docker system prune -af
```
Comando de Docker que se utiliza para entrar dentro del contenedor:
```
docker exec -it nombre_del_servicio bash o sh
```
Comando de Docker que se utiliza para ver las redes de docker:
```
docker network ls
```
Comando para ejecutar dentro de un contenedor de Docker que se utiliza para ver las variables declaradas:
```
printenv
```
mismo comando desde fuera del contenedor:
```
docker exec mysql bash -c 'printenv'
```

## Links
`https://hub.docker.com/_/httpd/tags`
