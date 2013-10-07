##Ejercicio5
  Instalamos el paquete git si no lo teníamos ya, apt-get install –y git

##Ejercicio6

* Realizamos un git clone https://github.com/rafacruiz/GII-2013.git  Se descarga el repositorio a nuestra maquina.

* Editamos el archivo README.md para introducir los objetivos.

* Con git add README.md, añadimos el archivo a nuestro repositorio.

* Hacemos un commit para guardar los cambios, git commit –m ‘Primer cambio’.
 
* Y por último push origin master, subimos y salvamos los cambios.

##Ejercicio7

* En este ejercicio en vez de montar cgroup, instalamos el paquete cgroup-bin y trabajamos a partir de ahí.
* Primero creamos los grupos de con el comando, cgcreate –a rafa –g memory,cpu,cpuacct:ejer
* Después creamos 3 subdirectorios diferentes para gestionar un navegador, un editor de texto y un proceso cualquiera.

    Cgcreate –g memory,cpu,cpuacct:ejer/navg
    Cgcreate –g memory,cpu,cpuacct:ejer/wri
    Cgcreate –g memory,cpu,cpuacct:ejer/othr
    
* Una vez creados los subgrupos, asignamos los procesos a los a estos subgrupos últimos que hemos creado con el comando cgexec

  Cgexec –g memory,cpu,cpuacct:ejer/navg firefox
  Cgexec –g memory,cpu,cpuacct:ejer/wri  kate
  Cgexec –g memory,cpu,cpuacct:ejer/othr 

Para analizar comprobamos los siguientes archivos:

Proceso Navg	
* Cpuacct.usege	= 23362972267
* Cpuacct.stat 	=user 1740, system537
* Cpuacct.usage_percpu = 23364280792
* Memory.max-usage-in-bytes = 163987456bytes

Proceso proc	
* Cpuacct.usege = 1230230671
* Cpuacct.stat = user 51, system 64
* Cpuacct.usage_percpu = 1230230671
* Memory.max-usage-in-bytes = 2838528

Proceso Edit
* Cpuacct.usege = 29016411766
* Cpuacct.stat = user 345, system 89
* Cpuacct.usage_percpu = 3913849960
* Memory.max-usage-in-bytes = 6938624
