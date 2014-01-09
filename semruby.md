#Ejercicio1
Instalar Ruby y usar
* ruby --version para comprobar la versión instalada. A la vez, conviene instalar también irb, rubygems y rdoc.

Para instalar Ruby tenemos que instalar "curl" si no lo tenemos en nuestra maquina.

  `sudo apt-get install curl`
  
Una vez instalado ejecutamos el siguiente comando, instalamos RMV.

  `\curl -L https://get.rvm.io | bash -s stable --ruby`
  
El siguiente paso sera instalar Ruby.

  `rvm get stable --autolibs=enable`
  `rvm install ruby`
  `rvm --default use ruby-2.1.0`

Ejecutamos --version para comprobar nuestra versión y obtenemos el siguiente resultado.

  >> ruby --version
  >> ruby 1.9.3p0 (2011-10-30 revision 33570) [i686-linux]

#Ejercicio2
Crear un programa en Ruby que imprima los números desde el 1 hasta otro contenido en una variable.

```
  #! /usr/bin/ruby

  $numeros = 0
  $total = 10

  while $numeros < $total
    puts ("#$numeros")
    $numeros = $numeros+1
  end
```
![Captura Programa1]()

#Ejercicio3
¿Se pueden crear estructuras de datos mixtas en Ruby? Crear un array de hashes de arrays e imprimirlo.
Sí, de la siguiente manera.

```
  #! /usr/bin/ruby

  estruc = {:nombre => 'Rafael',
         :apellido => ['Carrasco','Ruiz'],
         :direccion => 'GranVia'}

  puts estruc.inspect
```
![Captura Programa2]()

#Ejercicio4
Crear una serie de funciones instanciadas con un URL que devuelvan algún tipo de información sobre el mismo: fecha de última modificación, por ejemplo. Pista: esa información está en la cabecera HTTP que devuelve.

```
  #! /usr/bin/ruby

  require 'net/http'

  argumento = ARGV[0]

  http = Net::HTTP.new(argumento, 80)
  out = http.request_head('/')

  puts out['date'].to_s
```

#Ejercicio5
Ver si está disponible Vagrant como una gema de Ruby e instalarla.

  `sudo gem install vagrant` 




