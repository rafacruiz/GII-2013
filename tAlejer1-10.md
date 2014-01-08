#Ejercicio1

1. ¿Cómo tienes instalado tu disco duro? ¿Usas particiones? ¿Volúmenes lógicos?
Utilizando el comando fdisk -l, nos muestra de que manera tenemos instalado nuestro disco duro.

  ![CapDisco](https://dl.dropbox.com/s/4ydap49dq2qw71a/fdisk.png)
  
  La partición sda1 contiene el recovery de Windows
  La partición sda2 contiene la instalación de Windows
  La partición sda3 destinada para guardar datos
  La partición sda5 contiene la instalación de Linux
  La partición sda6 dedica para la memoria de intercambio en Linux

2. Si tienes acceso en tu escuela o facultad a un ordenador común para las prácticas, ¿qué almacenamiento físico utiliza?

Los equipos de la facultad utilizan un fichero remoto, cada vez que es cargado se vuelca la información al pc.

#Ejercicio2
Usar FUSE para acceder a recursos remotos como si fueran ficheros locales. Por ejemplo, sshfs para acceder a ficheros de una máquina virtual invitada o de la invitada al anfitrión.

Utilizamos un contenedor que anteriormente habiamos creado:
  `sudo lxc-start -n una-caja`

Una vez dentro instalamos sshfs:
  `sudo apt-get install sshfs fuse`
  
Despues de estos pasos, miramos que dirección ip utiliza el contenedor. Antes tenemos que agregar el usuario a Fuse de tal modo:
  `sudo usermod -a -G fuse rafa`
  


  




