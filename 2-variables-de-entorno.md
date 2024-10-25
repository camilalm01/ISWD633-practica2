# Variables de Entorno
### ¿Qué son las variables de entorno
Una variable de entorno es un valor dinámico que influye en el comportamiento de los procesos en ejecución en un sistema informático. Estas variables pueden contener información como rutas de archivos, configuraciones de idioma, y otros parámetros que afectan cómo se ejecutan las aplicaciones.

### Para crear un contenedor con variables de entorno?

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.
![image](https://github.com/user-attachments/assets/8758398c-2f85-4d26-b555-53c7f54b8caf)

### Crear un contenedor con mysql:8 , mapear todos los puertos

### ¿El contenedor se está ejecutando?
No
![image](https://github.com/user-attachments/assets/9ce51fe6-462c-4772-a38e-d98e0d578f72)

### Identificar el problema
![image](https://github.com/user-attachments/assets/29fbd028-7883-4b3d-9f5b-4536b7366dc4)
MySQL detectó que no hay una base de datos inicializada, y como medida de seguridad, no se puede ejecutar sin configurar una contraseña de root o sin una política de contraseña explícita. (variable de entorno)

### Eliminar el contenedor creado con mysql:8 

```
docker rm mysql
```
![image](https://github.com/user-attachments/assets/1f060fc3-bf57-44dc-9ea4-9d56e4c524ca)


### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo
![image](https://github.com/user-attachments/assets/beeb9761-097e-4515-988c-646520191ba8)
 

### ¿Qué bases de datos existen en el contenedor creado?
![image](https://github.com/user-attachments/assets/36fad02b-5491-4fe4-9d94-355ec55b1992)
