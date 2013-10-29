##Ejercicio 3

1. Usar debootstrap (o herramienta similar en otra distro) para crear un sistema mínimo que se pueda ejecutar más adelante.

  Instalamos debootstrap y una vez terminada la instalación, ejecutamos:
  
    "sudo debootstrap --arch=i386 quantal /home/jaulas/quantal/	http://archive.ubuntu.com/ubuntu"
    
    [Captura Instalación debootstrap](https://github.com/rafacruiz/IV/blob/master/t2-e3.png)


2. Experimentar con la creación de un sistema Fedora dentro de Debian usando Rinse.

  Instalamos rinse y ejecutamos la siguiente orden: "sudo rinse --arch=amd64 --distribution fedora-core-6 --directory /home/jaulas/fedora"
  
  Cuando ejecuto la orden rinse me muestra este tipo de error. No he conseguido instalarlo.
  
    [Captura Instalación rinse](https://github.com/rafacruiz/IV/blob/master/t2-e3-2.png)
    
  Con la distribución 8 de fedora no ocurre este error. Me decido por fedora-core-8 para su instalación.
  
    "sudo rinse --arch=i386 --distribution fedora-core-9 --directory /home/jaulas/fedora"
    
    [Captura Instalación Fedora](https://github.com/rafacruiz/IV/blob/master/rinse.png)

##Ejercicio 4

Instalar alguna sistema debianita y configurarlo para su uso. Trabajando desde terminal, probar a ejecutar alguna aplicación o instalar las herramientas necesarias para compilar una y ejecutarla.
  
  Uso la máquina instalada en el ejercicio anterior. Montamos /proc como nos indica en los apuntes de clase.
  
    [Captura Montaje Top](https://github.com/rafacruiz/IV/blob/master/top.png) 
  
