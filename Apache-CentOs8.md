
# Webserver Apache Linux Centos 8


Instalar un servidor web (web server) en Linux Centos 8. Te explico detalladamente los pasos de instalación y configuración.


###   1. Configuraciones del server y del cliente
![](https://i.postimg.cc/kg0YTpy1/1.png)

###  2.	Ponemos el adaptador del server en puente
![](https://i.postimg.cc/rmJhFF23/2.png)

###  3.	Vamos a configurar la ip del server con (nmtui) que es un entorno más gráfico para editar la red.
    nmtui
![](https://i.postimg.cc/Gpv7Vx7c/3.png)

###  4.	Editar la conexión
![](https://i.postimg.cc/sxgTBdVX/4.png)

###  5.	Seleccionamos interfaz
![](https://i.postimg.cc/G2r7CTVv/5.png)

###   6.	Configuramos la ipv4 manual y deshabilitamos la ipv6
![](https://i.postimg.cc/1zScnhBQ/6.png)

###   7.	Antes de salir , pulsar activar conexión
![](https://i.postimg.cc/d3N4rH19/7.png)

###   8.	Pulsamos ok
![](https://i.postimg.cc/L4xycXTZ/8.png)

###   9.	Vemos la ip nueva
    ip address show
![](https://i.postimg.cc/bNd6phCV/9.png)

###   10.	Vemos que tenemos ping
![](https://i.postimg.cc/C1FNtTnN/10.png)

###   11.	Actualizamos paquetes
    yum update
![](https://i.postimg.cc/pdMkfn23/11.png)

###   12.	Intalamos apache con la opción -y no tenemos que ir confirmando
yum install httpd -y
![](https://i.postimg.cc/0ywcKCqp/12.png)

###   13.	Vemos la ruta del binario
![](https://i.postimg.cc/wTPwBGnq/13.png)

###   14.	Arrancamos servicio http
    systemctl start httpd
![](https://i.postimg.cc/TPj0CY11/14.png)

###   15.	Vemos que haya levantado y escucha por el puerto 80, y observamos que el inicio automatico del servicio cuando inicia sistema esta deshabilitado.
    systemctl status httpd
![](https://i.postimg.cc/Hs7Q6sPm/15.png)

###   16.	Para activar el inicio automático por si reinicia.
    systemctl enable httpd
![](https://i.postimg.cc/76mVrsgy/16.png)

###   17.	Vemos que ya esta activado el inicio automático
    systemctl status httpd
![](https://i.postimg.cc/XJHwzZbj/17.png)

###   18.	Entramos en /etc/ y luego hacemos un listado que nos filtre por carpeta httpd
    cd /etc/
    ll | grep httpd

![](https://i.postimg.cc/VvvFfqR0/18.png)

###   19.	Entramos en directorio
    cd httpd
![](https://i.postimg.cc/qqFxzNbb/19.png)

###   20.	Listamos contenido, en la carpeta conf  esta el fichero de configuración httpd.conf
![](https://i.postimg.cc/4dN6P6j2/20.png)

###   21.	La carpeta donde alojaremos la web
    cd /var/www/html
![](https://i.postimg.cc/CMrNv2hG/21.png)

###   22.	Intalamos nano
![](https://i.postimg.cc/xTWPQbbq/22.png)

###   23.	Dentro creamos una web de prueba
    nano index.php
![](https://i.postimg.cc/657hFhqD/23.png)

###   24.	Escribimos contenido
    <html>
    	<body> Página de prueba </body>
    </html>

![](https://i.postimg.cc/rwxNwFSj/24.png)

###   25.	Vemos la web desde el terminal con el comando curl
    curl localhost
![](https://i.postimg.cc/DzcQ1jpb/25.png)

###   26.	Vemos que el firewall este activo
    systemctl status firewalld
![](https://i.postimg.cc/7Z3SytkQ/26.png)

###   27.	Ahora vemos que no tiene ninguna regla configurada
    firewalld -cmd –list-all
![](https://i.postimg.cc/dVPGpPzy/27.png)

###   28.	Agregamos el puerto 80 para nuestro servidor web de forma permanente para cuando reinicie el server siga estando
    firewall-cmd –add-port=80/tcp –permanent
![](https://i.postimg.cc/HnrQDpYQ/28.png)

###   29.	Reiniciamos el firewall
    firewall-cmd --reload
![](https://i.postimg.cc/Gt6vbZt6/29.png)

###   30.	Ahora vemos que la regla este activada
    firewalld -cmd –list-all
![](https://i.postimg.cc/sg7bCz1d/30.png)

###   31.	Desde el cliente ya podemos ver el server
![](https://i.postimg.cc/c1zR78hT/31.png)
