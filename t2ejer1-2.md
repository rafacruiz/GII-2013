##Ejercicio 1
Crear un espacio de nombres y montar en él una imagen ISO de un CD de forma que no se pueda leer más que desde él. 
Pista: en ServerFault nos explican como hacerlo, usando el dispositivo loopback

* En primer lugar tenemos que creamos un namespace, ejecutamos la siguiente linea:

    "sudo unshare -u /bin/bash"
  
* Cambiamos el nombre del equipo en este nuevo namespace:

    "hostname rafa"

[Captura namespace](https://github.com/rafacruiz/IV/blob/master/T2Ej1.png)

* Montamos una imagen este namespace, para ello creamos primero un punto de montaje:

  "mkdir /mnt/disk"
  
* Y realizamos el montaje de la iso:

    "mount -o loop /media/8E1AD7531AD73745/SO/debian-506-i386-kde-CD-1.iso /mnt/disk"
  
[Captura Montaje ISO](https://github.com/rafacruiz/IV/blob/master/T2Ej1%282%29.png)

##Ejercicio 2

1. Mostrar los puentes configurados en el sistema operativo.

Para realizar este ejercicio instalamos el paquete brctl. Ejecutamos el siguiente código y como podemos 
comprobar mi pc no contiene puentes configurados.
  
    "brctl show"
  
[Captura Show](https://github.com/rafacruiz/IV/blob/master/T2Ej2.png)

2. Crear un interfaz virtual y asignarlo al interfaz de la tarjeta wifi, si se tiene, o del fijo, si no se tiene.

* En primer lugar creamos el puente:

    "sudo brctl addr rafa"

* Una vez creado el puente, creamos una nueva interfaz:

    "ip addr show"
  
[Captura Interfaz](https://github.com/rafacruiz/IV/blob/master/T2Ej2-1.png)

* Para activar este puente lo añadimos a la interfaz eth0:

    "sudo brctl addif rafa eth0"

* Ya podemos comprobar que nuestro puente existe en nuestro pc:

    "brctl show"
  
[Captura Puente existente](https://github.com/rafacruiz/IV/blob/master/T2Ej2-3.png)



