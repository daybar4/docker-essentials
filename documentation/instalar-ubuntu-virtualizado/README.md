## _// Tutorial //_ ##

# MAINTAINER
- Name: David Aybar
- Email: daybar4@gmail.com

## Usar Ubuntu 22 LTS virtualizado
### Requierimientos
- Habilitar virtualización en la BIOS del host
- 20GB de espacio local

- Descargar e instalar VirtualBox, programa de virtualización: https://www.virtualbox.org/wiki/Downloads
- Descargar OVA: https://drive.google.com/drive/folders/1c-VrDB5uI__LdvtQIvAOHo10MKVHyqbg?usp=sharing
```
Usuario: user
Contraseña: user
Host: ubuntu
```
Acciones/Programas preinstalados:
- Comandos docker sin necesidad de contraseña
- Comandos sudo sin necesidad de contraseña
- Inicio de sesión sin necesidad de contraseña
- VirtualBox Guest Additions, para adaptación de pantalla y copy-paste bidireccional con host
- Git client
- Docker-ce y docker-compose
- Visual Studio Code
- Terminal Tilix
- Navegador Google Chrome
- Carpeta Demo con los proyectos docker-essentials y docker-essentials-stack clonados

Ejecutar Oracle VM VirtualBox Administrador
- Archivo > Importar y seleccionar ubuntu-desktop-22lts.ova
- Opciones por default, excepto ubicación del disco lcoal y politica de dirección MAC: "Generar nuevas direcciones MAC para todos los adaptadores de red"

Una vez importada, podemos ampliar RAM o CPU.
