##Ejercicio 5
Instalar una jaula chroot para ejecutar el servidor web de altas prestaciones nginx.

Instalo una máquina debian "sudo debootstrap wheezy /home/jaulas/debian/ http://ftp.us.debian.org/debian"

* Una vez dentro instalamos apt 

* Entramos con sudo chroot /home/jaulas/debian
  
* Instalamos nginx "apt-get install nginx"

* Iniciamos el servidor "service nginx start"


