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

#Ejercicio4
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
  
#Ejercicio6
Crear un dispositivo ceph usando BTRFS o XFS.

Creamos el directorio donde vamos almacenar la información de Ceph.

  ![capdirec](https://dl.dropbox.com/s/q1no9rbqmfjibs3/eje6.png)

A continuación creamos el fichero de configuración y creamos la imagen de Ceph.

  ![capimg](https://dl.dropbox.com/s/a7ngc1f3w5wh9b9/ejer6-1.png)
  
Formateamos el sistema de ficheros.

  ![capform](https://dl.dropbox.com/s/sb83im45gibzve9/ejer6-2.png)
  
Creamos el siguiente directorio.

  ![capdic](https://dl.dropbox.com/s/tu9kce4sfs7z32i/ejer6-4.png)
  
Una vez realizados los pasos anteriores, iniciamos el demonio.

  `sudo /etc/init.d/ceph -a start`
  
Y por ultimo lo montamos.

  `sudo mount -t ceph rafa:/ /mnt/ceph`

#Ejercicio7
Almacenar objetos y ver la forma de almacenar directorios completos usando ceph y rados.

Creamos el objeto como se indica en los apuntes, podemos ver con rados lspools el estado de los objetos.

  `sudo rados mkpool esa-piscina`
  
Y la almacenamos con put.

  `sudo rados put -p esa-piscina objeto imgpiscina.img`

#Ejercicio8
Tras crear la cuenta de Azure, instalar las herramientas de línea de órdenes (Command line interface, cli) del mismo y configurarlas con la cuenta Azure correspondiente.

Accedemos a www.windowsazurepass.com y creamos una cuenta en Windows Azure. Una vez hecho esto instalamos node.js para ello debemos añadir un repositorio:

```
  sudo add-apt-repository ppa:chris-lea/node.js
  sudo apt-get update
  sudo apt-get install nodejs
```

  ![caprepo](https://dl.dropbox.com/s/bc0wle7cavzbtkk/ej8.png)

Despues instalamos el modulo de azure-cli:

  `sudo npm install -g azure-cli`
  
  ![cap](https://dl.dropbox.com/s/9pc5ompcvvhtoj8/eje8-1.png)
  
Una vez descargada la herramienta de linea de comando, nos bajamos el fichero .publishsettings que contiene información sobre la cuenta de usuario de la siguiente manera:

  `azure account download`
  
  ![capcuenta](https://dl.dropbox.com/s/643g390gaeeciaa/ejer8-2.png)

Cuando ya tenemos descargado el fichero tenemos que importarlo:

 `azure account import...`


  
Ahora ya podemos crear la cuenta de almacenamiento:



  







  










  




