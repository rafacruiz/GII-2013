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


  
  
  
