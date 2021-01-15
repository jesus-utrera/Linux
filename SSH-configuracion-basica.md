# SSH - Configuración básica

introduccion
El protocolo telnet era inseguro, podian ver nuestros comandos
crearon nuevo protocolo SSH más seguro que usa clave para enviar y recibir datos entre dos equipos.


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

La 1º vez nos dice si queremos añadir el servidor a lista de servidor de confianza
por si alguna vez cambia la ip del servidor nos avisará que no es ese.

### 3  Generamos certificado

Certificado público de mi maquina al servidor nos permite conectarnos sin poner clave.

    ssh-keygen

![](https://i.postimg.cc/k4GPGRBb/3.png)


### 4  Ahora copiamos el certificado publico del cliente en el servidor. 

Cuidado! no copiar el privado sino público.

En el cliente:

    cat .ssh/id_rsa.pub

Copiamos la linea completa del resultado

![](https://i.postimg.cc/RhnrQr1C/4.png)


###  5.  En el server abrimos el siguiente fichero

     vim .ssh/autorized_keys

![](https://i.postimg.cc/VNY8yVw4/5.png)

###  6.  Pegamos dentro la clave del cliente.

![](https://i.postimg.cc/VNDczWLw/6.png)

###  7.  Ahora nos logueamos de nuevo y vemos que no nos pide clave . Porque se autentica con nuestro certificado privado que esta en mi maquina contra el certificado publico que esta en el servidor. El archivo autorized_keys permite guardar muchas claves para muchos usuarios.


![](https://i.postimg.cc/0Q4Rw5wH/7.png)
