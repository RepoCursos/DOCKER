1)Copiar los archivos docker

2)Acceder al directorio

3)Mapear carpeta donde quieres que se cree el proyecto en el docker-compose

4)Levantar los contenedores

sudo docker compose up -d

5)Acceder al contenedor laravel

sudo docker exec -it laravel bash

6)Crear proyecto

composer create-project laravel/laravel .

7)Asignar al usuario apache a la carpeta storage (dentro del contenedor)

chown -R apache:apache storage