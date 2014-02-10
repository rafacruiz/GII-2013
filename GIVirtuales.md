##Ejercicio1
Instalar chef en la máquina virtual que vayamos a usar.

Instalamos los paquetes Ruby y Ruby Gems que seran necesarios.

  `sudo apt-get install ruby1.9.1 ruby1.9.1-dev rubygems`
  
Una vez instalado usamos el gestor de gem de Ruby para instalar chef.

  `sudo gem install ohai chef`

##Ejercicio2
Crear una receta para instalar nginx, tu editor favorito y algún directorio y fichero que uses de forma habitual.

Para empezar creamos el directorio donde almacenar la receta:

  `mkdir -p ~/chef/cookbooks/nginx/recipes`

Una vez creado, almacenamos la receta dentro del directorio, default.rb:

```
package 'nginx'
directory '/home/rafamv/'
file "/home/rafamv/LEEME" do
	owner "rafamv"
	group "rafamv"
	mode 00777
	action :create
	content "Directorio para documentos"
end
```

Ahora indicamos con el archivo node.json, la receta que queremos instalar:

```
{
	"run_list": [ "recipe[nginx]"]
}
```

Y por ultimo el archivo, solo.rb:

```
file_cache_path "/home/rafamv/chef"
cookbook_path "/home/rafamv/chef/cookbooks"
json_attribs "/home/rafamv/chef/node.json"
```

Ejecutamos, sudo chef-solo -c chef/solo.rb

![captura](https://dl.dropbox.com/s/u8o5n539jvqcls2/nginx2.png)

Realizamos los mimos pasos para instalar el editor de textos:

`mkdir -p ~/chef/cookbooks/nginx/recipes`

```
package 'emacs'
directory '/home/rafamv/'
file "/home/rafamv/LEEME" do
	owner "rafamv"
	group "rafamv"
	mode 00777
	action :create
	content "Directorio para documentos"
end
```

```
{
	"run_list": [ "recipe[emacs]"]
}
```

##Ejercicio3
Escribir en YAML la siguiente estructura de datos en JSON: { uno: &quot;dos&quot;,
  tres: [ 4, 5, &quot;Seis&quot;, { siete: 8, nueve: [ 10, 11 ] } ] }

```
uno: "dos"
tres:
  - 4
  - 5
  - "seis"
  -
    - siete: 8
      nueve
        - 10
        - 11
```

##Ejercicio4
Desplegar los fuentes de la aplicación de DAI o cualquier otra aplicación que se encuentre en un servidor git público en la máquina virtual Azure (o una máquina virtual local) usando ansible.

Instalamos ansible:

`sudo pip install ansible`




