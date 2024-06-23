## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
# docker network create net-wp   
# Por defecto se crea una de tipo bridge.
### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es /var/lib/mysql
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# Contiene solo un archivo .gitignore para estas rutas: db/ www/

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# docker run -d --name srv-mysql --network net-wp -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=wordpress -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# Sigue vacía porque no se inicializó el contenedor con un volumen en específico.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (b) es /var/www/html
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# docker run -d -p 9500:80 --name srv-wordpress --network net-wp -e WORDPRESS_DB_HOST=srv-mysql:3306 -e WORDPRESS_DB_NAME=wordpress -e WORDPRESS_DB_USER=admin -e WORDPRESS_DB_PASSWORD=admin wordpress 

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# Los cambios persisten.



