
# WampServer - Instalación y configuración básica


WampServer es un entorno de desarrollo web de Windows. Te permite crear aplicaciones web con Apache2, PHP y una base de datos MySQL. Además, PhpMyAdmin le permite administrar fácilmente sus bases de datos.



Aqui tenemos web para acceder: [WAMP](https://www.wampserver.com/en/)


###  1.  Bajamos el instalador de la web principal.
![](https://i.postimg.cc/wB0KNnfZ/1.png)

###  2. Ejecutamos el exe
![](https://i.postimg.cc/mDpGvK7C/2.png)

###  3. Lo instalamos en el directorio por defecto o donde queramos
![](https://i.postimg.cc/tJ1HpDzf/3.png)

###  4. Seleccionamos el chrome como directorio por defecto
![](https://i.postimg.cc/rwG2VDS8/4.png)

###  5. El chrome.exe
![](https://i.postimg.cc/J7gLPVrW/5.png)

###  6. Ejecutamos el icono  de escritorio
![](https://i.postimg.cc/7hpr67sL/6.png)

###  7. Pulsamos la siguiente opcion para que nos aparezca el estado del servidor ENCENDER o  APAGAR 
![](https://i.postimg.cc/1z9hfyHD/7.png)

###  8. Con click derecho nos aparecen unas opciones, como ponerlo en español
![](https://i.postimg.cc/rFrLHnsR/8.png)


###  9. Con click izquierdo aparecen otras opciones como el estado de los servicios
![](https://i.postimg.cc/VkPcPq0G/9.png)


###  10. Ahora vemos el boton ENCENDER, gracias a la opcion que pulsamos antes en paso 7
![](https://i.postimg.cc/DZMtjLKc/10.png)


###  11. Por defecto phpmyadmin. User: root clave: vacía
![](https://i.postimg.cc/PxxgQK0x/11.png)


###  12. Por defecto viene con tamaño máximo de base de datos 128 mb
![](https://i.postimg.cc/HktWSZv4/12.png)


###  13. Para ampliarlo modificar este archivo
![](https://i.postimg.cc/Vv023vfP/13.png)


###  14. Cambiar las siguientes  lineas
![](https://i.postimg.cc/65npZ5dP/14.png)


###  15. Así quedarían según nuestras necesidades, aumentamos  los tiempos de ejecucion ya que al ser más grande tardará más.
![](https://i.postimg.cc/Jh4rSN9w/15.png)


###  16. Reiniciamos los servicios
![](https://i.postimg.cc/zGNXFZ7G/16.png)


###  17. En www creo mis proyectos web
![](https://i.postimg.cc/9z3sV20R/17.png)


###  18. Creamos un index.php con hola mundo
![](https://i.postimg.cc/Y249pxjM/18.png)


###  19. Abrir web:   localhost/nombrecarpetaproyecto
![](https://i.postimg.cc/9XvfzqqT/19.png)


###  20. Cambiar directorio de los proyectos, editamos este archivo y reiniciamos servicios
![](https://i.postimg.cc/k4L7VkD9/20.png)


###  21. Ponemos el nuevo directorio
![](https://i.postimg.cc/pr8RKqnj/21.png)


###  22. Esta opcion debe estar vacia para que no coja los puertos del wamp
![](https://i.postimg.cc/59F4cNkt/22.png)


###  23. Vamos al fichero configuracion apache
![](https://i.postimg.cc/gkFYGFfH/23.png)


###  24. Podemos cambiar los puertos al 85 por ejemplo, reiniciar procesos
![](https://i.postimg.cc/mgTBF3Zc/24.png)


###  25. Pondremos ahora   localhost:85/proyecto
![](https://i.postimg.cc/mDPbgbL8/25.png)


###  26. Podemos cambiar el puerto mysql entre el 3601 y 3609
![](https://i.postimg.cc/3JX3Rfh5/26.png)

###  27. Extensiones php si necesitamos alguna podemos habilitarla
![](https://i.postimg.cc/Y9CHytLt/27.png)
