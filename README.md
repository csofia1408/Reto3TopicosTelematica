# Reto3TopicosTelematica

## Descripción Reto 3

En este desafío se implementa una arquitectura que incluye dos sitios WordPress, un balanceador de carga, una base de datos y un servidor NFS. Se emplean dos instancias de WordPress para garantizar la disponibilidad del sitio web, además de asegurar una conexión segura mediante HTTPS con un dominio con certificado SSL.

### Aspectos Desarrollados

Todos los requisitos funcionales  se han cumplido. Se han creado cinco instancias: una para el servidor Nginx, que actúa como balanceador de carga y gestiona el certificado SSL para el dominio, dos instancias para los sitios WordPress, conectados a una base de datos remota, una instancia para la base de datos, y una instancia para el servidor NFS.

### Información General de Diseño

La arquitectura implementada sigue un enfoque cliente-servidor utilizando contenedores Docker para las instancias del balanceador de carga, WordPress y base de datos. Se destina una máquina al balanceador de carga, que distribuye las peticiones entre las instancias de WordPress. Estas instancias comparten una base de datos y un servidor NFS para el almacenamiento de archivos.

### Ambiente de Desarrollo y Técnico

#### Base de Datos:

- Actualización de la instancia y instalación de Docker.
  
![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/00e3e199-ef00-4334-a1f9-ab9e1419565e)

  
- Creación de un archivo .yml para Docker Compose con la configuración requerida.
nano wordpressbd.yml

- Ejecución del comando "docker-compose -f wordpress-db.yml up".

#### WordPress:

- Actualización de la instancia y instalación de Docker.
- Creación de un archivo .yml para Docker Compose con la configuración de WordPress, base de datos remota y NFS.
- Configuración del cliente NFS.
- Ejecución del comando "docker-compose -f wordpress.yml up".

#### NFS Server:

- Instalación del NFS-server.
- Configuración del NFS server.
- Especificación de la IP privada de las instancias WordPress.
- Reinicio del NFS server.

#### Balanceador de Carga:

- Verificación de puertos requeridos.
- Actualización de la máquina e instalación de letsencrypt, certbot y nginx.
- Modificación del archivo de configuración de nginx.
- Creación de la carpeta para letsencrypt y recarga de nginx.
- Reserva de nombre de dominio y asignación de IP elástica.
- Obtención del certificado SSL para el dominio.
- Movimiento de archivos generados por letsencrypt.
- Instalación de Docker.
- Creación y configuración de archivos Docker Compose.
- Modificación del archivo de configuración de nginx.
- Verificación de la no ejecución predeterminada de nginx.
- Ejecución del docker-compose.
