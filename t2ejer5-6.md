##Ejercicio 5
Instalar una jaula chroot para ejecutar el servidor web de altas prestaciones nginx.

Instalo una máquina debian "sudo debootstrap wheezy /home/jaulas/debian/ http://ftp.us.debian.org/debian"

* Una vez dentro instalamos apt 

* Entramos con sudo chroot /home/jaulas/debian
  
* Instalamos nginx "apt-get install nginx"

* Iniciamos el servidor "service nginx start"

##Ejercicio 6
Crear una jaula y enjaular un usuario usando `jailkit`, que previamente se habrá tenido que instalar.

* Descargamos jailkit de la página http://olivier.sessink.nl/jailkit/

* Ejecutamos la siguiente orden: ./configure && make && sudo make install

* Creamos sistema de ficheros:
        
        * sudo mkdir -p /seguro/jaulas/dorada
        * sudo chown -R root:root /seguro

* Iniciamos jailkit ejecutando "sudo jk_init -v -j /seguro/jaulas/dorada jk_lsh basicshell netutils editors"

* Añadimos un usuario nuevo: sudo adduser rafilla

* Se asigna la jaula al nuevo usuario: sudo "jk_jailuser -m -j /seguro/jaulas/dorada" 

![Foto jailkit](https://dl.dropboxusercontent.com/s/o4nnrz42tt6urxn/Captura%20de%20pantalla%20de%202013-11-08%2011%3A10%3A44.png)




