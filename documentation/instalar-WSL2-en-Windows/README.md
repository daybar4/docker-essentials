## _// Tutorial //_ ##

# MAINTAINER
- Name: David Aybar
- Email: daybar4@gmail.com

## Cómo instalar y usar WSL2 (Windows Subsystem for Linux) compatible con docker
Instalar docker desktop, al hacerlo instalará automáticamente el docker backend para WSL
Link de descarga:
https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?utm_source=docker&utm_medium=webreferral&utm_campaign=dd-smartbutton&utm_location=header

Es importante usar WSL2 ya que WSL 1 no es compatible con docker

Links: 
- https://docs.docker.com/desktop/windows/wsl/
- https://learn.microsoft.com/en-us/windows/wsl/install
- https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
- https://learn.microsoft.com/es-es/windows/terminal/install

### Prerequisitos
- Instalar Windows 10 version 1903 o superior o Instalar Windows 11
- Instalar Docker Desktop
- Habilitar WSL 2 en Windows
- Descargar e instalar el paquete de Linux kernet update (apartado de links wsl_update_x64.msi)

Después de instalar Docker Desktop ir a configuración > Resources > WSL Integration y habilitar integración y distros adicionales.

### Encender siempre Docker Desktop antes que WSL2 para que WSL2 pueda acceder a docker desktop backend, si encendemos antes WSL2 los comandos docker no funcionarán.

### Habilitar WSL 2 en Windows
Abrir características de Windows.
Seleccionar e instalar "Subsistema de Windows para Linux" y "Plataforma de máquina virtual"
Abrir powershell
```
wsl -l -v ### check version running
wsl --set-default-version 2 ## Definir WSL2 como versión predeterminada
wsl --list --online
wsl --install -d Ubuntu
wsl --setdefault Ubuntu
wsl --set-version Ubuntu 2 ### Definir Ubuntu WSL2
```
Comprobar la ejecución de los comandos docker y docker-compose.

### Instalación de Terminal Windows (opcional, recomendable)
(apartado de links /windows/terminal/install)
Una vez instalado, en la configuración recomiendo cambiar inicio automático de Ubuntu.
- Configuración > Inicio > Perfil predeterminado > Ubuntu

También iniciar ubuntu con permisos de administrador.
- Configuración > Ubuntu > Ejecutar este perfil como Administrador
