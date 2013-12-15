##Ejercicio6
1 - Instalar juju.

  En primer lugar añadimos un nuevo repositorio y despues realizamos la instalación de juju. Ejecutamos los siguientes comandos.
  
    sudo add-apt-repository ppa:juju/stable
    sudo apt-get update && sudo apt-get install juju-core
    
  Iniciamos juju, esto crea el archivo de configuración environments.yaml.
  
    juju init
    
    - A boilerplate environment configuration file has been written to /home/rafa/.juju/environments.yaml.
    - Edit the file to configure your juju environment and run bootstrap.
    
  Modificamos el archivo de configuración kate .juju/environments.yaml
  
    Comentamos la linea, #default: amazon y añadimos la siguiente, default: local.
  
  Podemos cambiar de entorno con
  
    juju switch local
    
  Si no tenemos instalado Mongodb, ejecutamos el siguiente comando
  
    sudo apt-get install mongodb-server
    
  Ahora ya podemos crear un contenedor juju con

    sudo juju bootstrap
  

2 - Usándolo, instalar MySql en un táper.

  Integramos Mediawiki ademas de mysql que es requerido por este, con los siguientes comandos
  
    sudo juju deploy mediawiki
    sudo juju deploy mysql
    
  Mediante el siguiente comando relacionamos mediawiki y mysql
  
    juju add-relation mediawiki:db mysql
    
  Por ultimo para que pueda ser usado por el resto (conecte con el servidor) ejecutamos,
  
    juju expose mediawiki y comprobamos que todo esta 'ok' con, juju status

##Ejercicio7
1 - Destruir toda la configuración creada anteriormente

  Para destruir toda la configuracion ejecutamos los siguientes comandos
  
    sudo juju remove-unit mediawiki/0 mysql/0
    sudo juju destroy-environment

2 - Volver a crear la máquina anterior y añadirle mediawiki y una relación entre ellos.

  Creamos de nuevo la máquina y añadimos mediawiki
  
    sudo juju switch local
    sudo juju bootstrap
    sudo juju deploy mediawiki
    sudo juju deploy mysql
    sudo juju add-relation mediawiki:db mysql
    sudo juju expose mediawiki
    
    Esperamos hasta que indiquen que esta todo 'ok'.

3 - Crear un script en shell para reproducir la configuración usada en las máquinas que hagan falta.

  Realizamos un script con las ordenes que utilizmos anteriormente, debemos ejecutarlo con privilegios 'sudo'.
  
    #!/bin/bash
    
    juju init
    juju switch local
    juju bootstrap
    juju deploy mediawiki
    juju deploy mysql
    juju add-relation mediawiki:db mysql
    juju expose mediawiki

##Ejercicio8
Instalar libvirt. Te puede ayudar esta guía para Ubuntu.
  

