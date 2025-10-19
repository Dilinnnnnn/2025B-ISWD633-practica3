## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp

docker network create net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
esta vacio 

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

```
docker run -d --name mysql2 --network net-wp -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=wordpress_db -e MYSQL_USER=user -e MYSQL_PASSWORD=password -v "C:\6semestre\CYEDS\ejercicio3\db"/db:/var/lib/mysql mysql:8
```
### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?

se crearon muchos varios archivos que usa mysql para wordpress.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/

En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

```
docker run -d --name wordpress2 --network net-wp -p 9500:80 -e WORDPRESS_DB_HOST=mysql2 -e WORDPRESS_DB_USER=user -e WORDPRESS_DB_PASSWORD=password -e WORDPRESS_DB_NAME=wordpress_db -v "C:\6semestre\CYEDS\ejercicio3\www"/var/www/html wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

<img width="1861" height="1028" alt="image" src="https://github.com/user-attachments/assets/dae98f63-3fc5-4687-8271-357eae331853" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

La configuracion y todo lo que ya creamos previamente se mantiene y se almacena en el host de nuesta pc que creamos.


