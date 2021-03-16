# AREP LABORATORIO 5 - TALLER DE DE MODULARIZACIÓN CON VIRTUALIZACIÓN E INTRODUCCIÓN A DOCKER Y A AWS

Este taller consiste en crear una arquitectura que contenga un balanceador de carga, 3 nodos que manejen peticiones REST y un nodo que contenga una base de datos mongo. Cada nodo representa un contenedor en Docker.


### PREREQUISITOS

Los prerrequisitos que manejaremos para lograr con exito el desarrollo del laboratorio son:
- Maven
- Git
- MongoDB
- Aws
- Docker
- Docker-Compose

### Ejecucion e instalacion
se debe clonar el proyecto con el siguiente comando:

```
git clone https://github.com/memo1019/LAB04-AREP
```
luego ingresaremos a la carpeta dede el cmd o la consola:
```
cd /Lab05-AREP
```
Finalmente coonstruiremos y compilaremos el proyecto para asi poder ejecutarlo.
```
 docker pull memo1019/arep5balancer:latest
 docker pull memo1019/arep5web:latest
```

Si desea ejecutar los contenedores directamente desde las imágenes de DockerHub, ejecute el siguiente comando:
```
docker-compose up -d --scale web=3
```
Si estás trabajando en una máquina Linux o Mac, [instala docker-compose](https://docs.docker.com/compose/install/).
En windows, docker-compose ya está en docker desktop.

entonces ve a localhost:8087 para acceder directamente al contenedor del Load Balancer.
Si quieres acceder a los contenedores web, puedes ir a localhost:8088,localhost:8089 y localhost:8090, pero en AWS EC2 el puerto 8087 era el único oppened para el tráfico.la aplicación seguirá esta arquitectura en AWS(Para más información sobre cómo funcionaba en AWS plese visitar el archivo de documentación):

## Pruebas
las podra ver corriendo con el comando 

```
 mvn test
```

## DOCKER IMAGES

Para correr el programa tenemos que ejecutar el siguiente comando :

```
java -cp target/classes;target/dependency/* edu.co.escuelaing.nanospring.demo.Application
```
Luego vaya a http://localhost:4567/escuelaing/operacion.html para ver el programa desplegado localmente


La aplicación se despliega con heroku y el enlace está en la parte inferior de este documento (botón Heroku)

## Diseño

![Diagrama de Clases](/src/site/Resources/prueba8.png)
### Diagrama de clases
#### Load Balancer
![Diagrama de Clases](/images/prueba7.png)

#### Rest Server
![Diagrama de Clases](/images/prueba6.png)
## Documentacion
para realizar la documentacion de javadoc use estos comandos y aqui podra llevar acabo el proceso de creacion de esta documentacion.
```
$ mvn javadoc:javadoc
$ mvn javadoc:jar
$ mvn javadoc:aggregate
$ mvn javadoc:aggregate-jar
$ mvn javadoc:test-javadoc
$ mvn javadoc:test-jar
$ mvn javadoc:test-aggregate
$ mvn javadoc:test-aggregate-jar
```
si desea ver el javadoc se encuentra en el directorio
```
/target/site
```

Podemos ver la descripcion del proyecto en este pdf [file](/lab4.pdf) mostrando el diseño y la estructura del proyecto

## Construido con

* [Maven](https://maven.apache.org/) - Dependency Management
* Git - Version Control    
* Apache Maven 3.6.3
* Docker
* Spark web
* Java 1.8.0_211
* Git 2.26.2
* AWS (EC2)
   
  ## Comandos a Usar
  
  ***Listar todos los contenedores***
  
   ```sh
    $ docker container ls 
    $ docker ps -a (List all containers not just running)
   ```
     
    ***Listar imagenes***

      ```sh
    $ docker images  
     ```

   ***Contruir una imagen de un Dockerfile***

    ```sh
    $ docker build -t <myimage> 
  ```
   ***Correr un contenedor***

    ```sh
    $ docker run -d -p <localport>:<containerport> --name firstdockercontainer <image> 
  ```
   ***Correr docker-compose con 3 instancias web***

  ```sh
    $ docker-compose up -d --scale web=3
  ```

   ***Obtener un shell del contenedor***

  ```sh
    $ docker exec -it <docker ID> /bin/bash
  ```

## Autor

* **Guillermo Alfonso Castro Camelo** - [Memo1019](https://github.com/memo1019)

## Licencia

This project is licensed under the GNU v3.0 License - see the [LICENSE](LICENSE.txt) file for details
