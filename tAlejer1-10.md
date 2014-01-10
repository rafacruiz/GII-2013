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
  
  ![CapIp](https://dl.dropbox.com/s/bwo03uhtrdfklug/almejer2.png)
  
Ahora creamos una carpeta en nuestr maquina local, a la cual queremos acceder:

  `mkdir remoto`

Ya podemos acceder a la carpeta local:

  `sshfs ubuntu@10.10.10.2:/home/ubuntu /home/rafa/remoto`
  
#Ejercicio3
Crear imágenes con estos formatos (y otros que se encuentren tales como VMDK) y manipularlas a base de montarlas o con cualquier otra utilidad que se encuentre.

Creamos una imagen con extensión .qcow2 utilizando quemu-img:

  `qemu-img create -f qcow2 imagen.qcow2 30M`

Para una imagen .img:

  `qemu-img create -f raw imagen.img 30M`
  
Y para VMDK he utilizado la siguiente linea de ordenes:

  `qemu-img create -f vmdk imagen.vmdk 30M`

#Ejericio4
Crear uno o varios sistema de ficheros en bucle usando un formato que no sea habitual (xfs o btrfs) y comparar las prestaciones de entrada/salida entre sí y entre ellos y el sistema de ficheros en el que se encuentra, para comprobar el overhead que se añade mediante este sistema.

Primero creamos dos imagenes utilizando quemu-img, visto en el ejercicio anterior:

  `quemu-img create -f raw xfs.img 80M`
  `quemu-img create -f raw btrfs.img 80M`
  
Ahora poder utilizar estas imagenes dentro de nuestro sistema, necesitamos convertirlas en dispositivos loop con losetup:

  `sudo losetup -v -f xfs.img`
  `sudo losetup -v -f btrfs.img`

Cuando ya estan creados los dos dispositivos tenemos quedar formato, ya que no tienen formato alguno. Para ello utilizamos mkfs:

  `sudo mkfs.xfs /dev/loop1`
  `sudo mkfs.btrfs /dev/loop2`

Y una vez que ambos dispositvos tienen formato, pueden ser montados en máquinas virtuales o cualquier otra cosa.

#Ejercicio5
Instalar ceph en tu sistema operativo.

  Instalamos ceph con apt-get:
    
      `sudo apt-get install ceph-mds`








  




