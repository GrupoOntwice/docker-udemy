# Docker 

Para agregar docker a sudo

Creamos un grupo
```
    $ sudo groupadd docker
```

Añadimos nuestro usuario al grupo
```
    $ sudo usermod -aG docker $USR
```

Cerramos la terminal y volvemos a activar los cambios del grupo
```
    $ newgrp docker
```

Verificar que todo funciona
```
    $ docker run hello-world
```





```
    $ docker inspect id/name
    $ docker inspect -f {{ json .Config.Env  }} container_name
    $ docker rename actual_name new_name
    $ docker logs container_name
    $ docker rm container_name(id
```

Para saber todos los nombres de los id de los dockers es con:
```
    $ docker ps -aq
    $ docker rm $(docker ps -aq) // con esto se borran todos los dockers 
```

Volumenes
```
    $ docker volume ls
    $ docker volume prune
    $ docker volume create dbdata

    $ docker run -d --name db --mount src=dbdata, dst=/data/db
```


docker volume ls —> Listar todos los volumenes
docker volume prune —> Borrar todos los volúmenes que no están en uso por ningún contenedor
docker volume create <nombre volume> —> Crear un nuevo volume
docker run -d --name db --mount src=dbdata,dst=/data/db mongo —> Para poder asociar el directorio de un contenedor a un volumen se utiliza el parámetro --mount, luego src para indicar el volumen donde se guardará la información, y luego dst para indicar el destino o directorio del contenedor que se montará en el volumen indicado en src.
Una vez ejecutado nuevamente mongo con el nombre de db sobre el volumen dbdata, volver a ejecutar un bash dentro del contenedor y probar nuevamente la creación de datos en mongo.


docker run -d --name dbmongo --mount src=dbdata,dst=/data/db mongo


Imágenes
```
    $ docker images ls
```

Dockerfile
```
    $ docker build -t ubuntu:platzi .
```

Para subir una imagen que tenga directamente a dockerhub
```
    $ docker tag ubuntu:platzi gvilarino/ubuntu:platzi
    $git push gvilarino/ubuntu:platzi
    $ docker history ubuntu:platzi
```

Ahora para no ver history y que no etendamos mucho existe dive 
```
    https://github.com/wagoodman/dive
    $ dive ubuntu:platzi

    $ docker network ls
    $ docker build -t adsad .
    $ docker network create --attachable platzinet
    $ docker network add platzinet app
    $ docker inspect network platzinet
```

Docker compose
```
    $ docker-compose up -d --build
    $ docker-compose logs -f app
    $ docker-compose exec app bash
    $ docker-compose down
    $ docker-compose build 
    $ docker-compose scale  app=4
```


Docker Multi Stage Build
```
    $ docker build -t platziapp -f build/development.Dockerfile .
```

Hola, cuando ejecutas docker run puedes usar el flat -m este te permite definir el máximo de memoria que puede usar ese contenedor por ejemplo si quieres asignar máximo 128 Megabites de memoria sería docker run -m 128m ... los puntos los reemplazas por el resto del comando.



## UDEMY

```
    $ docker build -t name .
    $ docker build -t name:tag .
    $ docker images | grep apache
    $ docker history -H apache-centos:latest
```

Creando contenedor con base  a la imagen recién creada
```
    $ docker run -d centos-apache
    $ docker rm -fv docker-name
    $ docker run -d --name apache centos-apache
```

Dentro de Dockerfile
```
    LABEL author=”Mario Guadalupe Sanchez”
    LABEL version=1.0
```

Instruccion para encontrar las imagenes que se quedaron huerfanas
```
    $ docker images -f dangling=true
```

-- revisar el tema de multi-stage-build


Para eliminar esas imagenes huerfanas
```
    $ docker rmi $(docker images -f dangling=true -aq)
```

para renombrar un contenedor
```
    $ doker rename romantic_poasd to_new_name
```

Detener un contenedor
```
    docker stop container_id/container_name
```

Iniciar un seervicio

```
    docker start container_id/container_name
```

Para reiniciar
```
    docker restart container_id/container_name
```

Entrar a un contenedor
```
    docker exec -it container_name bash
```

Entrar a un contenedor como un usuario
```
    docker exec -u root -it container_name bash
```

Para agregar variables de entorno al crear un contenedor
```
    docker run -dti -e "prueba1=1234" --name test image_name
```

Para ver los  procesos que esta ocupando un contenedor
```
    $ docker stats container_name
```

Para instalar un contenedor de jenkins
```
    $ docker pull jenkins
    $ docker run -d -p 8080:8080 --name jenkins jenkins
```

Limitar el limite de memoria utilizado por un contenedor
```
    $ docker run -d -m "500mb" --name mongo2 mongo
    $ docker stats mongo2
```

Para limitar el numero de procesadores a utilizar
```
    $ docker run --help | grep cpu
    $ docker run -d -m "500mb" --cpus 1 --name mongo2 mongo 
```

Para copiar archivos dentro de un contenedor
```
    docker cp file container_name:/directory/to/copy/file
```

Para poder revisar los logs de un contenedor
```
    $ docker logs -f container_name
```

Pasos para poder crear volumenes de host
```
    docker 
```





