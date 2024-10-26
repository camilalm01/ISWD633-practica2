### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17
![image](https://github.com/user-attachments/assets/04a37b4e-522c-4ecf-a72c-4989ee0df651)

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4

```
docker run -d --name pgadmin-client -e PGADMIN_DEFAULT_EMAIL=admin@admin.com -e PGADMIN_DEFAULT_PASSWORD=admin -p 5050:80 dpage/pgadmin4
```
![image](https://github.com/user-attachments/assets/3c929bd0-776f-494f-a2e6-e4b65cf197b8)

La figura presenta el esquema creado en donde los puertos son:
- a: El puerto del contenedor pgAdmin expuesto en el host es 5050.
- b: El puerto 80 dentro del contenedor de pgAdmin.
- c: El puerto por defecto de PostgreSQL es 5432.

![Imagen](img/esquema-ejercicio3.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
![image](https://github.com/user-attachments/assets/1c94c38d-eb88-4e46-a8bf-b6006bd4fead)
![image](https://github.com/user-attachments/assets/eb58b443-8c7c-40c9-bdad-be389f84fe52)

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.
![image](https://github.com/user-attachments/assets/5f51b01d-7c26-4f0b-9b82-07f0974a59c2)

## Desde el servidor postgresl
### Acceder al servidor
```
docker exec -it mi-postgres /bin/bash
```
```
psql -U postgres
```
### Conectarse a la base de datos info
```
\c info
```
### Realizar un select *from personas
![image](https://github.com/user-attachments/assets/f510be46-50ce-4809-8b5b-892503b71570)

