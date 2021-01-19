
# SSH - Avanzado
introduccion
El protocolo telnet era inseguro, podian ver nuestros comandos
crearon nuevo protocolo SSH más seguro que usa clave para enviar y recibir datos entre dos equipos.

***Cada comando repite los anteriores tengo que probar si son necesarios o solo se pone el nuevo***


###  1.  Con este comando creamos una clave publica y hacemos que el servidor copie nuestra clave del cliente al fichero authorized_keys directamente, pedirá la clave después de apretar comando.

    ssh-keygen
    ssh-copy-id root@209.76.63.14
    
pondremos la clave

ahora ya podemos entrar sin clave

![](https://i.postimg.cc/QMQyS5dR/1.png)


###  2.  Usar como un cliente de chat, para algunos sitios que nos bloquean los puertos y no podemos con otras apps, le abrirá una terminal al servidor y podrá ver lo que escribimos

    ssh-copy-id
    ssh -t root@209.76.63.14 irssi

![](https://i.postimg.cc/ryQ7vSNT/2.png)


### 3  Usar ssh como un proxy para nuestro navegador.
Esto va a crear un proxy en el servidor ssh para usarlo como un proxy, entonces saldremos a internet con la configuración y accesos de la ip del servidor

    ssh-copy-id
    ssh -t root@209.76.63.14 irssi
    ssh -D puerto root@209.76.63.14

![](https://i.postimg.cc/tCJ8yYBx/44.png)

### Configuraremos nuestro navegador proxy.
![](https://i.postimg.cc/W3sfy3Dt/4.png)

###  4.  Ejecutar app que están en el server desde mi maquina
En Linux no hay que hacer nada, en Windows o Mac hay que instalar un servidor X como XQuartz.app

Por ejemplo con esto abre un Firefox del servidor pero lo abre en la máquina del cliente.

    ssh-copy-id
    ssh -t root@209.76.63.14 irssi
    ssh -D puerto root@209.76.63.14
    ssh -X root@209.76.63.14
    firefox


###  5.  Esta es la mejor opcion de SSH
Por ejemplo si hay un firewall y quiero acceder al server 2 pero solo tengo acceso al 1. El 1 si ve al 2. El 2 tiene abierto el puerto 22 ssh para ver solo los equipos de área local como el server 1 por tcp.

![](https://i.postimg.cc/QtSnZ35m/6.png)

Configuración firewall server 2:

![](https://i.postimg.cc/FHJqdw5F/8.png)

    ssh-copy-id
    ssh -t root@209.76.63.14 irssi
    ssh -D puerto root@209.76.63.14
    ssh -X root@209.76.63.14
    ssh -L 2020:10.8.5.126:22 root@209.76.63.14
 
 ahora para conectar al server 2:
 
    ssh -p 2020 root@localhost

![](https://i.postimg.cc/SNP3KkPt/7.png)

ssh -l ,ip de mi maquina, puerto 2020 que se va a crear en mi maquina, ip privada del servidor 2,puerto 22, usuario:ip servidor 1

Esto lo que hace crear el puerto 2020 en mi maquina que apunta al puerto 22 del servidor 2 a través del servidor 1

Esto es lo que hemos echo
-L 2020 : server2:22

Otra opción podría ser apuntar el puerto 8080 de mi maquina apuntado al puerto 80 del server 1, de esta forma puedo entrar al puerto 80 que tal vez no este permitido desde fuera del server 1.

-L 8080 : localhost:80


###  7.  TUNEL SSH REVERSO

Aveces tenemos un servidor que esta detrás de un firewall pero no hay otro servidor conectado como en el anterior caso, pero si hay una persona en ese servidor.

Este caso se da cuando se quiere acceder a un servidor que esta detrás de muchos firewalls por ejemplo.

![](https://i.postimg.cc/hvywTBtv/9.png)

    ssh-copy-id
    ssh -t root@209.76.63.14 irssi
    ssh -D puerto root@209.76.63.14
    ssh -X root@209.76.63.14
    ssh -L 2020:10.8.5.126:22 root@209.76.63.14
    ssh -R 2020:localhost:22 root@209.76.63.14

Haremos que la persona desde el servidor 2 se conecte mi servidor externo  ssh que tendra que acceder con un usuario y clave. Y desde este ya me puedo meter al servidor 2.

    ssh -R 2020:localhost:22 root@209.76.63.14

Ósea voy a crear el puerto 2020 en mi equipo que apunte al puerto 22 del server 2 con usuario e ip de mi servidor

 Ahora desde mi servidor externo pongo:

    ssh root@localhost -p2020

###  7.  COMENTARIO DE USUARIO YOUTUBE CON MUCHOS VOTOS:

#### Pendiente a probar
Lo maximo muchas gracias!, un "tip" mas, por si te sirve: ssh -l root ip-servidor -w 10:10 esto levanta una interfase "tun10" en el cliente y en el servidor (ejecutalo como root en el cliente tambien) luego: en el cliente: ip addr add 10.10.10.10/24; ip link set up dev tun10; en el servidor: ip addr add 10.10.10.11/24; ip link set up dev tun10 y podras hacer ping entre ambos equipos a travez de un tunnel VPN! asi no tienes que "tunelizar" un puerto, con esto tienes acceso en todos los puertos ya que es un tunnel encriptado (como openvpn pero sin instalar openvpn). 

Notas: 10:10 podria ser 120:98 y en el otigen se crearia el "tun120" y en el destino el "tun98", usa el numero que quieras 10.10.10.... la res no importa, usa cualquiera que no se traslape con las redes a las que el servidor o cliente YA tengan acceso si se cierra la sesion SSH el tunel muere, (yo uso "screen" y dejo un "ping" constante) al estar usando SSH para encriptar el trafico y levantar el tunnel puede que consuma un poco mas de CPU que OPENVPN como servicio, pero vamos! es para salir de apuros! (aun que yo dejo el tunnel abierto por dias y la verdad no hay mayor impacto.. con los CPU que tenemos hoy en dia...)


