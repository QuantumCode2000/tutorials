install postgresql official image

```bash
docker pull postgres
```

correr la base de datos

se tienenque poner las siguientes variales
docker run --name <nombre-de-tu-cont> -e POSTGRES_USER=<usuario> -e POSTGRES_PASSWORD=<contraseña> -e POSTGRES_DB=<nombre-de-la-base-de-datos> -p <puerto-externo>:<puerto-interno> -d postgres
-d = detach (correr en segundo plano)
-e = environment (variables de entorno)
--name = nombre del contenedor
-p = puerto
postgres = imagen de postgres

```bash
docker run --name some-postgres -e POSTGRES_USER=quantum -e POSTGRES_PASSWORD=quantum -e POSTGRES_DB=quantumdb -p 5432:5432 -d postgres
```

conectar a la base de datos

```bash
docker exec -it <container_id> bash
```

```bash
docker exec -it some-postgres bash
```

bash se utiliza para ejecutar comandos en el contenedor , utilizare el programa
bash del contenedor para conectarme a la base de datos

```bash
psql -U quantum --password --db quantumdb
```

DOCKER COMPOSE

1. Crear un archivo docker-compose.yml
2. Escribir la configuración de los servicios
   3.Puedes crear
   services , volumes , networks
   en "services" se pone la configuración de la base de datos
   en "volumes" se pone la configuración de los volumenes
   en "networks" se pone la configuración de la red

CREANDO EL SERVICIO

1. services: nombre del servicio :
   image :
   nombre de la imagen
   services :
   nginx:
   image: nginx

2. uso docker compose up para correr el servicio
   up = correr el servicio
3. puedes agregarle el flag -d para correr en segundo plano
   d = detach

agregando el flag para sacar el puerto afuera
ports:

- "80:80"
  <puerto-externo>:<puerto-interno>


```bash
docker compose up -d
```

CREACION DE dockerfile
el docjerfile es un archivo que contiene las instrucciones para crear una imagen de docker
1. Crear un archivo llamado Dockerfile
2. Escribir las instrucciones para crear la imagen
3. Construir la imagen con el comando docker build

