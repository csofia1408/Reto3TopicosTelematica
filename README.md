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
  
![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/3b385137-1979-4f01-bd72-fc0f569028af)


  
- Creación de un archivo .yml para Docker Compose con la configuración requerida.
nano wordpressbd.yml

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/153ab8d1-f18a-458f-a48f-59b2c107e6c1)


- Ejecución del comando "docker-compose -f wordpressdb.yml up".

#### WordPress:

- Actualización de la instancia y instalación de Docker.
  
![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/d9d9c19f-f380-474b-94f7-8c3c99625c13)

- Creación de un archivo .yml para Docker Compose con la configuración de WordPress, base de datos remota y NFS.
  
  ![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/a95757d4-d3e6-4d3a-9f87-99313d1a2c0d)

- Configuración del cliente NFS.

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/967b1b94-8e2e-4db6-83a7-178a5b274216)


- Ejecución del comando "docker-compose -f wordpress.yml up".

#### NFS Server:

- Instalación del NFS-server y Configuración del NFS server
  
![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/8ce64f7a-f736-4407-9f00-4ae0928ae4df)

  
- Especificación de las instancias WordPress.
  
![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/937c720b-be54-41e1-9928-68b4ec4e46aa)

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/f85baae6-95d8-4606-a009-64c7dd60d76f)


- Reinicio del NFS server.

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/9cbfe934-c124-4fc0-8b26-58335a805076)


#### Balanceador de Carga:

- Verificación de puertos requeridos.

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/97181ef0-1d93-4895-b66b-c6789bb8372c)

  
- Actualización de la máquina e instalación de letsencrypt, certbot y nginx.
  
  
- Modificación del archivo de configuración de nginx.

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/ebde2f3a-c90a-455a-be06-8039b6901c3a)

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/49278889-f0e7-4d47-8741-60a366969912)


- Creación de la carpeta para letsencrypt y recarga de nginx.

  ![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/4fa23424-9369-4058-aa1b-c2e5ceaefbc7)

  
- Reserva de nombre de dominio y asignación de IP elástica y Obtención del certificado SSL para el dominio.

- Instalación de Docker.
  
![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/a635e932-df38-418e-a15f-f36374bdb490)

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/dd74a332-db5d-4682-b2a1-e56ba28fbcf0)


- Creación y configuración de archivos Docker Compose.

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/956d5078-ce8f-4d4e-8f31-5f90345234f9)



- Modificación del archivo de configuración de nginx y ssl.conf

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/611faf84-fba4-4b3d-abe8-8f8e3fa7c8c8)

![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/52e5d4e7-bd13-401e-ae1e-876d08a81990)


  
- Verificación de la no ejecución predeterminada de nginx.
  
  ![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/d8cc7083-828d-45b5-a18f-fffd17d40795)

- Ejecución del docker-compose.
  
![imagen](https://github.com/csofia1408/Reto3TopicosTelematica/assets/72955238/1562d3e5-0f4f-48d9-a2f3-833e2949857a)

## Referencias

- https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04
- https://www.digitalocean.com/community/tutorials/how-to-run-nginx-in-a-docker-container-on-ubuntu-22-04
- https://github.com/st0263eafit/st0263-231/tree/main/docker-nginx-wordpress-ssl-letsencrypt
- https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-setup-an-Nginx-load-balancer-example

