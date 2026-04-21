## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
<img width="500" height="68" alt="image" src="https://github.com/user-attachments/assets/a7e652ca-d7b3-483b-9331-c5352228945f" />

# COMPLETAR CON EL COMANDO COMANDO
```
docker network create net-wp -d brigde
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
Según la documentación, mysql almacena la información en */var/lib/mysql*
<img width="1281" height="358" alt="image" src="https://github.com/user-attachments/assets/f9d5490d-0aae-4c7d-b9a0-0f412aa7a862" />

En el esquema del ejercicio carpeta del contenedor (a) es */var/lib/mysql*

Ruta carpeta host: .../ejercicio3/db

<img width="1273" height="727" alt="image" src="https://github.com/user-attachments/assets/701a0ad7-fc4a-45c4-89be-3f51132d7aee" />

### ¿Qué contiene la carpeta db del host?
Inicialmente antes de la creación del contenedor, dicha carpeta no contiene nada, pero su función es guardar los registros es guardar los archivos físicos del motor de base de datos.
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
```
docker run -d -P --name mysqlp3 --network net-wp --mount type=bind,source=C:\Users\User\ejercicio3\db,target=/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=db-p3 -e MYSQL_USER=santi -e MYSQL_PASSWORD=admin mysql:8
```
<img width="1718" height="74" alt="image" src="https://github.com/user-attachments/assets/5ef012cf-8c67-499c-b242-0e367e057577" />

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Lo que la carpeta contiene ahora son los archivos del motor de base de datos que representan la persistencia de datos en esta carpeta, lo que confirma que bind mount se realizó con éxito.
<img width="1300" height="954" alt="image" src="https://github.com/user-attachments/assets/9ad172ec-256c-4c07-bef9-bd0c9cd41f8c" />

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es */var/www/html*

<img width="722" height="388" alt="image" src="https://github.com/user-attachments/assets/5691527a-9b7e-4d75-96ed-4760d74ccfb1" />

Ruta carpeta host: .../ejercicio3/www

Carpeta creada.

<img width="1273" height="727" alt="image" src="https://github.com/user-attachments/assets/17dc1e32-98db-42f6-9540-a26f379be125" />

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO

```
docker run -d --name wordpressp3 --network net-wp -p 9500:80 --mount type=bind,source=C:\Users\User\ejercicio3\www,target=/var/www/html -e WORDPRESS_DB_HOST=mysqlp3 -e WORDPRESS_DB_USER=santi -e WORDPRESS_DB_PASSWORD=admin -e WORDPRESS_DB_NAME=db-p3 wordpress

docker run -d --name wordpressp3 --network net-wp -p 9500:80 --mount type=bind,source=C:\Users\User\ejercicio3\www,target=/var/www/html -e WORDPRESS_DB_HOST=mysqlp3 -e WORDPRESS_DB_USER=santi -e WORDPRESS_DB_PASSWORD=admin -e WORDPRESS_DB_NAME=db-p3 wordpress
```
<img width="1890" height="80" alt="image" src="https://github.com/user-attachments/assets/5e6eeef4-9032-406f-8dc9-4de66584b0c7" />

### Personalizar la apariencia de wordpress y agregar una entrada
<img width="1909" height="940" alt="image" src="https://github.com/user-attachments/assets/dc9926ac-fdf4-4d23-8fbb-93fde5c7901f" />

<img width="1875" height="928" alt="image" src="https://github.com/user-attachments/assets/1b319502-ce70-4f0f-95aa-22352dca253c" />

<img width="1919" height="942" alt="image" src="https://github.com/user-attachments/assets/2c4ba3ff-d980-4dce-9d09-189995d2261e" />

<img width="1911" height="956" alt="image" src="https://github.com/user-attachments/assets/1ad42357-2e93-4986-af2c-b974edaab128" />

<img width="1919" height="940" alt="image" src="https://github.com/user-attachments/assets/431da646-e41b-4f1a-9e43-b71dc7230444" />


### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
## Eliminado
```
docker rm -f wordpressp3
```
<img width="1906" height="132" alt="image" src="https://github.com/user-attachments/assets/74f9c66b-bf76-48c1-a90e-0c030c08fbb0" />

<img width="1919" height="949" alt="image" src="https://github.com/user-attachments/assets/3c9d9f2b-3c06-4067-b3f6-9df3311f9297" />

## Creado
```
docker run -d --name wordpressp3 --network net-wp -p 9500:80 --mount type=bind,source=C:\Users\User\ejercicio3\www,target=/var/www/html -e WORDPRESS_DB_HOST=mysqlp3 -e WORDPRESS_DB_USER=santi -e WORDPRESS_DB_PASSWORD=admin -e WORDPRESS_DB_NAME=db-p3 wordpress
```
<img width="1918" height="939" alt="image" src="https://github.com/user-attachments/assets/e189eed1-d8b4-4537-912d-4e31cad006d4" />
<img width="1919" height="939" alt="image" src="https://github.com/user-attachments/assets/abb88903-c5a4-4401-b9c1-030f0fab457e" />
<img width="1538" height="816" alt="image" src="https://github.com/user-attachments/assets/955f5cb9-d278-4901-a59e-0ea57a1edc2c" />

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 
Tras seguir las instrucciones dadas, es decir, al eliminar lo que sucede es que si recargamos la página esta ya no aparece disponible. Sin embargo, al volver a crearla y recargarla,esta página aparece nuevamente e incluso incia desde nos quedamos como si solo se hubiera ido la conexión. Esto se debe a que los datos de registro y existencia se guardó en las rutas configuradas y las imagenes están creadas de modo que estas persistan en dichos lugares, por ello es que la información no se ha perdido.
