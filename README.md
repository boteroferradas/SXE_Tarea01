# SXE_Tarea01

<h2>Tabla de especificaciones/analisis</h2>

|   Elemento  | Lo que dice la documentación | Lo que necesita la VM | Otros (comentarios relevantes) | Fuente de info | 
| ------------- | ------------- | ------------- | ------------- | ------------- |
| **S.O** | No específica ningún S.O  | | No se especifica ningun S.O, pero he considerado instalar Ubuntu Server porque es una distro ligera y está preparada para este tipo de tarea | https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview |
| **Servidor Web**  | Apache, Nginx | | | https://wordpress.org/about/requirements/ |
| **Version PHP** | PHP 7.4+  | | La documentacion dice 7.4 o mas, pero instalare una superior | https://wordpress.org/about/requirements/ \|\| https://nexonhost.com/wordpress-hosting-requirements |
| **Gestor de BBDD** | MySQL 5.5.5+  | | Igual que la version de PHP, se dice que la 5.5.5 es la minima, pero instalare una superior  | https://nexonhost.com/wordpress-hosting-requirements |
| **Memoria y Disco** | 1.5 GB de RAM 5GB de espacio en disco | 3GB de RAM como minimo 25GB de espacio en disco | | https://ubuntu.com/server/docs/reference/installation/system-requirements/ |

<h2>Configuacion de la VM</h2>
<ul>
  <li> <strong>S.O</strong>:   Ubuntu Server 26.04.1</li>
  <li><strong>Nº de Cores:</strong> 2</li>
  <li><strong>Memoria Total:</strong> 4GB</li>
  <li><strong>Espacio en Disco:</strong> 25GB</li>
</ul>
<br>

<h2>Instalación</h2>

<h3>1. S.O. - Instalacion de Ubuntu Server</h3>

![Ubuntu Server](capturas/ubuntuServer.png)
<p>Avanzar con las opciones por defecto e instalar el SSH para poder operar con comandos el sistema</p>

<h3>2. Servidor Web - Instalacion de Apache</h3>

![Apache](capturas/apache.png)
Comando: 
```
sudo systemctl start apache2
sudo systemctl enable apache2
```

<h3>3 - Instalacion de PHP</h3>

![PHP](capturas/php.png)
Comando: 
```
sudo apt install php
```

<h3>4 - Instalacion de MySQL</h3>

![MySQL](capturas/mysql.png)
Comando: 
```
sudo apt install mysql-server`
```

<h3>5 - Instalacion de Wordpress</h3>

![WordPress](capturas/wordpress.png)
Comandos:
Descargar el archivo necesario
```
sudo apt install wget
cd /tmp
wget http://wordpress.org/latest.tar.gz
```
Desempaquetarlo:
`tar -xf latest.tar.gz`
Moverlo al directorio por defecto de los archivos web de Apache2
```
sudo mv wordpress /var/www/html
sudo chown www-data:www-data /var/www/html -R
```

<h3>6 - Configuracion de Wordpress </h3>

![Configuracion](capturas/usuariowp.png)

Creacion de base de datos en wordpress, usuario y contraseña mas comprobacion de que ha sido creada

Para crear la base de datos:
```
sudo mysql -e "CREATE DATABASE wordpress;"
```
Crear Usuario y Contraseña
```
sudo mysql -e "CREATE USER 'wordpress'@'%' IDENTIFIED BY ´contraseña_exemplo´;"
```
Dar permisos: 
```
sudo mysql -e "GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress'@'%';"
```
Comprobar a creacion: 
```
sudo mysql -e "SHOW databases;"
```
