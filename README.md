1-creamos el documento docker-compose y le asignamos permisos

    sudo touch docker-compose.yml
    
    sudo chmod a+w docker-compose.yml

2-escribimos en el documento
    
    sudo cat > docker-compose.yml

    version: '3.1'
    
    services:
    
      mongo:
        image: mongo:latest
        restart: always
        container_name: monguito
    
        environment:
          MONGO_INITDB_ROOT_USERNAME: root
          MONGO_INITDB_ROOT_PASSWORD: secret
        volumes:
          - ./monguitodata:/data/db
          - ./monguitodata/log:/var/log/mongodb/
        ports:
          - "27017:27017"
3-crear archivo para correr comandos y dar los permisos

    touch mongo.sh
    sudo chmod a+wx mongo.sh

4-escribir los comandos que nos gusten

    sudo cat > mongo.sh
    echo "mensaje de prueba"

5-creamos carpeta para volumen de mongo

    mkdir monguitodata && cd monguitodata; cd monguitodata || mkdir log

6-volvemos al home

    cd

7-iniciamos el contenedor

    sudo docker-compose up -d

8-entrar en el contenedor
    
    sudo docker exec -it monguito bash

9-salir del contenedor
    
    Ctrl + d

10-ejecutar comandos ingresados

    ./mongo.sh
