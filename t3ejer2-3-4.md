##Ejercicio2
Comprobar qué interfaces puente ha creado y explicarlos.

Ejecutamos el comando ifconfig y podemos comprobar que nos crea una nueva interfaz llamada lxcbr0 y otra con el termino veth.

 ![Inter.Puente](https://dl.dropbox.com/s/p6bjpezsr51nn8c/puente.png)

 ![Puerta veth](https://dl.dropbox.com/s/u2978kwqbj7zgt4/puente2.png)

##Ejercicio3
1. Crear y ejecutar un contenedor basado en Debian.

En primer lugar creamos un contendor basando en nuestra distribución. Para ello ejecutamos la siguiente orden:

    "sudo lxc-create -t ubuntu -n una-caja"
  
Una vez terminan todos los pasos de la instalación, tenemos nuestro contendor basado en ubuntu creado. Para acceder utilizamos la siguiente orden:

    "sudo lxc-start -n una-caja"
  
  Como podemos comprobar en la imagen, para acceder nuestro login y password son: ubuntu/ubuntu
  
 ![Caja2](https://dl.dropbox.com/s/ggew3a99ajb11ge/caja2.png)
  
 ![caja](https://dl.dropbox.com/s/cw488s6ltcx8pfi/caja.png)
  

2. Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. Nota En general, crear un contenedor basado en tu distribución y otro basado en otra que no sea la tuya.

En este paso creamos un contenedor basado en la distribución debian. Aunque ubuntu esta basado en debian, no son la mismo distrubición.

    "sudo lxs-create -t debian -n midebian"

 ![cajadebian](https://dl.dropbox.com/s/xoelx5c44trps9w/debiaconter.png?m)

##Ejercicio4
1. Instalar lxc-webpanel y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.

 Para instalar lxc-webpanel, seguimos los pasos de la página web: http://lxc-webpanel.github.io/install.html

 ![webpanel](https://dl.dropbox.com/s/9f0ia8xkyjwrio5/webpanel.png)
 
 ![webpafun](https://dl.dropbox.com/s/cotogcvu4d4sdgs/webpfu.png)

2. Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria.

 Una vez que estamos dentro de web panel, en el panel de la izquierda podemos elegir el contendor que queremos configurar y restringir los recursos.
 Accedemos al contenedor miDebian.
 
 ![miDebian](https://dl.dropbox.com/s/zz1o1n11iq2jsug/webdebian.png)
    

#Ejercicio5

1. Comparar las prestaciones de un servidor web en una jaula y el mismo servidor en un contenedor. Usar nginx.

 Primero entramos en la jaula lxc-start -n una-caja, una vez dentro instalamos nginx. Con 'ab' realizamos una petición repetida al servidor. Asginamos mediante la inferfaz grafica de lxc-web-panel una dirección IP.
 
 Realizamos la petición:
 
   "ab -n 10000 -c 50  http://10.0.0.2/"
 
 ![jaula](https://dl.dropbox.com/s/d53oz6t7khxuca1/jaulanginx.png)
 
 Y para nuestra máquina lazamos el siguiente comando:
 
   "ab -n 10000 -c 50  http://localhost/"
 
 ![local](https://dl.dropbox.com/s/iif2qke8y9dg3j3/localeje5.png)
 
 
 Se puede observar es mas rapido usar una jaula chroot que un contenedor que usa un puente a la interfaz de red.
