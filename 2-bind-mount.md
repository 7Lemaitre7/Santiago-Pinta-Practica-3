# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)             <img width="1151" height="233" alt="image" src="https://github.com/user-attachments/assets/67f86d74-242d-4e39-874c-1dcaedb911d4" />

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO
```
docker run -d -P --name nginxp3 --mount type=bind,source=C:\Users\User\nginx\html,target=/usr/share/nginx/html nginx:alpine
```
<img width="1707" height="462" alt="image" src="https://github.com/user-attachments/assets/1b379abb-9c27-4028-8ece-31180edc3d97" />
```

```
<img width="1756" height="95" alt="image" src="https://github.com/user-attachments/assets/063db926-69e3-4748-8614-b5814ef16eca" />

### ¿Qué sucede al ingresar al servidor de nginx?

Al ingresar a *http://localhost:32769/* lo que aparece es un error 403 que nos indica que no hay autorización, pero tras investigar, también indica que no hay nada que mostrar, es decir, en la carpeta creada previamente no hay ningun archivo.

<img width="1919" height="187" alt="image" src="https://github.com/user-attachments/assets/5b8af468-00c7-4fc8-8f91-468354e24b5f" />

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### ¿Qué pasa con el archivo index.html del contenedor?
Al mirar con la herramienta *Inspeccionar* se puede notar que el archivo index.html contiene la siguiente información que correctamente es mostrada al ingresar al URL.
<img width="1114" height="386" alt="image" src="https://github.com/user-attachments/assets/51b032f7-4100-44d3-ba5d-cd43101eb427" />

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html

<img width="1691" height="926" alt="image" src="https://github.com/user-attachments/assets/bd371729-d798-4de7-8a44-66ac65ab2137" />
```
```
<img width="1359" height="707" alt="image" src="https://github.com/user-attachments/assets/5c46e2a3-6042-4b50-86e9-c54d49c06c4a" />

### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar o recargar *http://localhost:32769/* lo que aparece es el template descargado y descomprimido en la carpeta html de nginx, y ahora sí ya tiene algo que leer.
<img width="1911" height="942" alt="image" src="https://github.com/user-attachments/assets/c2a64777-ef05-4b81-b742-8f1db42baea7" />

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
```
docker rm -f nginxp3
```
<img width="262" height="77" alt="image" src="https://github.com/user-attachments/assets/27a74ea4-619d-4c55-a01c-93f2ece11349" />
```
```
<img width="1911" height="938" alt="image" src="https://github.com/user-attachments/assets/866b5450-54fb-494d-8108-820612a7fbc4" />
Como se puede observar, al eliminar el contenedor ya no se puede acceder al sitio.
### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
```
docker run -d -P --name nginxp3 --mount type=bind,source=C:\Users\User\nginx\html,target=/usr/share/nginx/html nginx:alpine
```
<img width="979" height="67" alt="image" src="https://github.com/user-attachments/assets/aae107e3-a37e-41d3-af34-473045910269" />
```
```
<img width="1747" height="285" alt="image" src="https://github.com/user-attachments/assets/b731dca2-a826-488f-bfc8-5c4f4235c796" />
```
```
<img width="1919" height="936" alt="image" src="https://github.com/user-attachments/assets/156e6665-9968-47d2-971e-d905339168d0" />

Al volver a crear el contenedor, primeramente se debe buscar el puerto en el que se ejecuta ya que no es el mismo por usar el flag -P en el comando, esto se logra con el comando:
```
docker ps -a
```
De este modo sabremos que el URL a usar es el *http://localhost:32770/*, en donde encontraremos el mismo contenido que se ejecutó antes de ser eliminado. Esto se debe a la configuración de la ruta en el comando de creación.
