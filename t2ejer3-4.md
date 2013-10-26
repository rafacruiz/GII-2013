##Ejercicio 3

1. Usar debootstrap (o herramienta similar en otra distro) para crear un sistema mínimo que se pueda ejecutar más adelante.

  Instalamos debootstrap y una vez terminada la instalación, ejecutamos:
  
    "sudo debootstrap --arch=amd64 quantal /home/jaulas/quantal/	http://archive.ubuntu.com/ubuntu"
    
    [Captura Instalación debootstrap](https://github.com/rafacruiz/IV/blob/master/t2-e3.png)


2. Experimentar con la creación de un sistema Fedora dentro de Debian usando Rinse.

  Instalamos rinse y ejecutamos la siguiente orden: "sudo rinse --arch=amd64 --directory /home/jaulas/fedora --distribution fedora-core-6"
  
  Cuando ejecuto la orden rinse me muestra este tipo de error. No he conseguido instalarlo.
  
    [Captura Instalación rinse](https://github.com/rafacruiz/IV/blob/master/t2-e3-2.png)

##Ejercicio 4

Instalar alguna sistema debianita y configurarlo para su uso. Trabajando desde terminal, probar a ejecutar alguna aplicación o instalar las herramientas necesarias para compilar una y ejecutarla.
  
  
