**SSH - Configuración básica**

El protocolo telnet era inseguro, podian ver nuestros comandos
crearon nuevo protocolo SSH más seguro que usa clave para enviar y recibir datos.


###  1.  Generalmente ya viene instalado. Sino meter el comando:
`apt-get install openssh-server`

![](https://i.postimg.cc/Bnf3pvwr/1.png)

comprobamos si el servicio esta activo:

    systemctl enable ssh


###  2.   Para conectar: 
En windows usamos putty para conectar a un servidor.
![](https://i.postimg.cc/DwQTMK98/2.png)

    ssh usuario : ip servidor
    ssh root@94.231.92.33

