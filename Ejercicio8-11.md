##Ejercicio8
2. Implementar usando el fichero de configuración de cgcreate una política que dé menos prioridad a los procesos de usuario que a los procesos del sistema (o viceversa)

Para realizar el ejercicio seguimos los pasos que han sido explicados en el ejercicio anterior, debemos modificar el archivo de configuración /etc/cgconfig.conf. Si tenemos alguna duda de cómo priorizar los procesos de un usuario con los del sistema podemos seguir la explicación de esta guía, https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Resource_Management_Guide/sec-cpu_and_memory-use_case.html. En este caso vamos asignar un 40% de la cpu ha este grupo.

Para realizar el ejercicio modificamos el archivo /etc/cgconfig.conf y añadimos las siguientes líneas:
Antes creamos el grupo “usuario”: sudo cgcreate –g memory,cpu,cpuacct:usuario

	group usuario{

                cpu.shares = 40;
        }

Para que los procesos del usuario del sistema se vean afectados por esta medida, tenemos que modificar el archivo /etc/cgrules.conf. Añadimos el nombre del usuario, el tipo de control y su grupo.

[Captura](https://github.com/rafacruiz/IV/blob/master/foto1.jpg)

3. Usar un programa que muestre en tiempo real la carga del sistema tal como htopy comprobar los efectos de la migración en tiempo real de una tarea pesada de un procesador a otro (si se tiene dos núcleos en el sistema). 

4. Configurar un servidor para que el servidor web que se ejecute reciba mayor prioridad de entrada/salida que el resto de los usuarios.



##Ejercicio9
Comprobar si el procesador o procesadores instalados lo tienen. ¿Qué modelo de procesador es? ¿Qué aparece como salida de esa orden?

Tipo de procesador: Intel core2 duo P8600 2.4 GHz.

Más info: http://ark.intel.com/es-es/products/35568/Intel-Core2-Duo-Processor-P8600-3M-Cache-2_40-GHz-1066-MHz-FSB

Al ejecutar el comando egrep '^flags.*(vmx|svm)' /proc/cpuinfo, no devuelve nada indicando que si contiene virtualización de intel. Este resultado puede ser motivo de estar utilizando actualmente una maquina virtual, mientras preparo el pc para instalar Ubuntu correctamente. Una vez efectuada la instalación volveré a ejecutar el comando para ver el resultado real, ya que en la características del pc su página web oficial indica que si soporta virtualización.

##Ejercicio10
Comprobar si el núcleo instalado en tu ordenador contiene este módulo del kernel usando la orden kvm-ok.
Al igual que en el ejercicio anterior me indica que el cpu no soporta la extensión KVM, también puede estar motivado al utilizar maquina virtual.

[Captura KVM](https://github.com/rafacruiz/IV/blob/master/foto2.jpg)

##Ejercicio11
Comentar diferentes soluciones de Software as a Service de uso habitual.
Mcafee saas – Elimina la administración local y la mejor asignación a recursos propios.
http://www.mcafee.com/es/products/saas-total-protection.aspx

Otros ejemplos que usan Saas mucho más conocidos y que utilizamos a diario son
 * Google Docs
 * Dropbox
 * Gmail

http://www.genbetadev.com/programacion-en-la-nube/entendiendo-la-nube-el-significado-de-saas-paas-y-iaas

##Ejercicio12
Instalar un entorno virtual para tu lenguaje de programación favorito (uno de los mencionados arriba, obviamente).

El entorno virtual que instale fue Spyder para el lenguaje de programación Python.

Pero para este ejercicio instalamos un entorno virtualizado de los cuales se indican, como es virtualenv para el lenguaje de programación python.

[Captura Spyder](https://github.com/rafacruiz/IV/blob/master/foto3.jpg)
 
 * Para su instalación seguimos los pasos de http://www.virtualenv.org/en/latest/
   pip install virtualenv

