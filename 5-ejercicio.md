## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio5.PNG)

### Crear la red
```
docker network create net-wp -d bridge 
````
### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
````
docker run -d --name mysql-db --network net-wp -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=wppass mysql:8
````

### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
````
docker run -d --name wordpress-site --network net-wp -p 9300:80 -e WORDPRESS_DB_HOST=mysql-db:3306 -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=wppass -e WORDPRESS_DB_NAME=wordpress wordpress
````

De acuerdo con el trabajo realizado, en la el esquema de ejercicio el puerto a es 9300

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
![image](https://github.com/user-attachments/assets/c8fd7cd8-93f7-4f05-8626-cd25b7e67644)
![image](https://github.com/user-attachments/assets/2f200e14-0112-40f2-804f-2f39fb58e8c0)


Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
![image](https://github.com/user-attachments/assets/991f336f-0e1b-40f0-b7cd-f41b42dccf3b)


### Eliminar el contenedor wordpress
````
docker rm -f wordpress-site
````

### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

### ¿Qué ha sucedido, qué puede observar?
En este caso la información y modificaciones realizadas han permanecido.
![image](https://github.com/user-attachments/assets/7d7a5651-d154-4315-80c7-fa78f3c0622e)






