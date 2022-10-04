## _// DEMO //_ ##
## Trabajar con docker-compose.yml
El archivo docker-compose.yml normalmente comienza con la definición de la versión. Esto indicará a Docker Compose qué versión de la configuración estamos usando.

Luego tenemos el bloque services, donde configuramos los servicios que son parte de este entorno. En nuestro caso, tenemos un único servicio llamado web. Este servicio utiliza la imagen nginx:alpine y establece una redirección de puerto con la directiva ports. Todas las solicitudes en el puerto 8000 del equipo host (el sistema desde el cual está ejecutando Docker Compose) serán redirigidas al contenedor web en el puerto 80, donde se ejecutará Nginx.

La directiva volumes creará un volumen compartido entre el equipo host y el contenedor. Esto compartirá la carpeta app local con el contenedor, y el volumen se ubicará en /usr/share/nginx/html dentro del contenedor, que luego sobreescribirá la raíz predeterminada del documento para Nginx.

Hemos creado una página demo y un archivo docker-compose.yml para crear un entorno de servidor web en contenedor que lo presentará. En el siguiente paso, abriremos este entorno con Docker Compose.