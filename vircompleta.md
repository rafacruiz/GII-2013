##Ejercicio1
Instalar los paquetes necesarios para usar KVM. Se pueden seguir estas instrucciones. Ya lo hicimos en el primer tema, pero volver a comprobar si nuestro sistema está preparado para ejecutarlo o hay que conformarse con la paravirtualización.

Instalamos los paquetes qemu-kvm y libvirt-bin.

  `sudo apt-get install qemu-kvm`
  `sudo apt-get install libvirt`
  
  ![ImgInst](https://dl.dropbox.com/s/moungthne8f2lw4/ejeruno.png)
  
##Ejercicio2
a. Crear varias máquinas virtuales con algún sistema operativo libre, Linux o BSD. Si se quieren distribuciones que ocupen poco espacio con el objetivo principalmente de hacer pruebas se puede usar CoreOS (que sirve como soporte para Docker) GALPon Minino, hecha en Galicia para el mundo, Damn Small Linux, SliTaz (que cabe en 35 megas) y ttylinux (basado en línea de órdenes solo).

Descargamos la .iso de Damn Small Linux y SliTaz. Creamos las imagenes para los distintos Sistemas Operativos.

  `qemu-img create imagen.img 150M`

  ![ImgImagen](https://dl.dropbox.com/s/fzrbmf2hwimb0o4/ejerdos.png)
  
Instalamos Damn Small Linux en la imagen creada.

  `qemu-system-x86_64 -hda imagen.img -cdrom dsl-4.11.rc1.iso`
  
  ![ImgInst](https://dl.dropbox.com/s/i79mirtlc03rdit/ejerdos-1.png)
  
  ![ImgInst](https://dl.dropbox.com/s/evwjewfxkwha4d4/ejerdos-2.png)
  

Como podemos comprobar, ejecutamos la máquina virtual y no se instala correctamente.
  
  `quemu-system-x86_64 -hda imagen.img -m 256 -boot c`
  
  ![ImgPrue](https://dl.dropbox.com/s/aph0pm5ixbzk2v6/ejerdos-3.png)
  

Ahora probamos Slitaz. Creamos una imagen y realizamos la ejecución al ser un livecd.

  `qemu-img create -f qcow2 slitaz.img 200M`
  
  ![ImgImagen](https://dl.dropbox.com/s/0lqht0uorxkv951/ejerdos-4.png)
  
  `qemu-system-x86_64 -hda slitaz.img -cdrom slitaz-4.0.iso`

  ![ImgInst](https://dl.dropbox.com/s/3owryoug4yg6gay/ejerdos-6.png)
  
  
b. Hacer un ejercicio equivalente usando otro hipervisor como Xen, VirtualBox o Parallels.

 Para esta parte del ejercicio vamos a utilizar VirtualBox, aprovechamos que lo tengo instalado para la realización de la práctica anterior.
 
  ![Dedian1](https://dl.dropbox.com/s/1jst460fztg1vjn/Debian.png)
  
El siguiente paso que tenemos que realizamos es elegir la cantidad de memoria ram que vamos a reservar.


  ![Dedian2](https://dl.dropbox.com/s/qppm8mdpuqmfcqo/Debian1.png)
  
Ahora creamos un disco virtual donde realizaremos la instalación del S.O. Elegimos el tipo archivo (VDI) para el disco duro y el tamaño.

  ![Dedian3](https://dl.dropbox.com/s/gikpybf6vxtbpdf/Debian3.png)
  
  ![Dedian4](https://dl.dropbox.com/s/vko4h4hl4lxjn0s/Debian4.png)
  
Una vez tenemos creada la máquina virtual, antes de iniciar la vm elegimos el .iso donde tenemos S.O que queremos instalar en ella. Indicamos el iso de Debian.


  ![Dedian5](https://dl.dropbox.com/s/2r8xqh5bwexqs1a/Debian5.png)
  
Realizado este paso, iniciamos la vm y realizamos la instalación.

  ![Dedian6](https://dl.dropbox.com/s/grwqjvas4w4da5g/DeInst.png)
  
Es una instalación rápida y sencilla. En este primer paso elegimos el idioma, despues nos pedira el nombre que queremos asignar a la máquina.

  ![Dedian7](https://dl.dropbox.com/s/934iht8f698j6jk/DeInst1.png)
  
  ![Dedian8](https://dl.dropbox.com/s/kaob3r0a64kowjl/DeInst3.png)
  
Despues nos pide instroducir la contraseña que superusuario.

  ![Dedian9](https://dl.dropbox.com/s/xmrzlwcwy45qy5y/DeInst4.png)  

Una vez tenemos el paso anterior realizado, seleccionamos la forma de particionar el disco duro
  
  ![Dedian10](https://dl.dropbox.com/s/bzylbpe43ty8a3i/DeInst7.png)
  
Si estamos de acuerdo con la forma de particionar el disco, indicamos "si" a escribir los cambios en el disco

  ![Dedian11](https://dl.dropbox.com/s/xsszumij0co0u6r/DeInst9.png)
  
Y se realiza la instalación

  ![Dedian12](https://dl.dropbox.com/s/0hea32dv2tqel02/DeInst10.png)
  
Cuando termina la instalación, ya podemos acceder a nuestra distribución Debian en la vm

  ![Dedian13](https://dl.dropbox.com/s/15ap2vduq8vxgpq/DebianFinal.png)
  
##Ejercicio4
Crear una máquina virtual Linux con 512 megas de RAM y entorno gráfico LXDE a la que se pueda acceder mediante VNC y ssh.

Voy a utilizar una distribución Debian con un entorno gráfico LXDE para ello voy a utilizar qemu. Primero realizaremos la imagen donde trabajará y despues indicaremos que la imagen .iso arranque desde ella. Con la opción -m para crear la máquina con 512 megas. 

  `qemu-img create -f qcow2 disUbu.img 2G`
  `qemu-system-x86_64 -hda disUbu.img -cdrom ../../debian-7.3.0-i386-lxde-CD-1.iso -m 512M`

  ![DedianQemu](https://dl.dropbox.com/s/ietj1vts8j0a6ho/ejer5debian.png)
  
Los pasos para la instalación de Debian son los mismo que hemos realizado en el ejercicio 2.b.

  ![DedianQemu](https://dl.dropbox.com/s/txih87fdo44egz7/ejer4debian.png)
  
  ![DedianQemu](https://dl.dropbox.com/s/kmthct2e4pk953s/ejer4debian1.png)
  
Para iniciar nuestra máquina virtual utilizamos el siguiente comando.

  `qemu-system-x86_64 -boot order=c -drive file=disUbu.img,if=virtio`
  
  ![DedianQemu](https://dl.dropbox.com/s/62htz8gpi4uduav/ejer4debian.png)
  
Ahora tenemos que acceder mediante ssh, para ellos vamos a iniciar la vm con un nuevo parametro. Indicamos con -redir tcp:2222::22, para redirigir un puerto en el sistema anfitrión a un puerto en el sistema virtual.

  `qemu-system-x86_64 -boot order=c -drive file=disUbu.img,if=virtio -redir tcp:2222::22`
  
Y con el comando `ssh -p 2222 debian@localhost` accedemos a nuestra máquina.
  
##Ejercicio5
Crear una máquina virtual ubuntu e instalar en ella un servidor nginx para poder acceder mediante web.


##Ejercicio7
Instalar una máquina virtual Ubuntu 12.04 para el hipervisor que tengas instalado.

