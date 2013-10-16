#Prática1

Para realizar la primera práctica he utilizado como Paas Heruku y como lenguaje Python. Ya que en la asignatura de Desarrollo de aplicaciones para internet estamos empezando con Python me parecio bueno idea realizar la práctica con este lenguaje.
Heroku, es una de las primeras plataformas de computación en la nube. El servidor Git de Heroku maneja los repositorios de las aplicaciones que son subidas por los usuarios.

Para comenzar realizamos este primer paso tenemos que tener instalado Python, Virtualenv y tener descargado toolbelt de heroku, la cual nos podemos descargar desde https://toolbelt.heroku.com/debian.
	
* Una vez tengamos heroku instalado realizamos los siguientes pasos:
	
		  “$ easy_install pip”
		  “$ pip install virtualenv”
	
* Iniciaremos Heroku:
	
		  “$ heroku login (Donde nos pide nuestro email y password de heroku)”
		  
		Creara una clave ssh publica si lo deseamos.
	
* Nuestro siguiente paso sera crear una carpeta para nuestro proyecto:
	
		  “$ mkdir practica1”
		  “$ cd practica1”
	
* Una vez dentro ejecutamos para poder utilizar Python. Para poder utilizarlo tenemos que activarlo.
	
		  “$ virtualenv venv –distribute”
		  “$ source venv/bin/activate”

* A continuación instalamos las dependencias de nuestra aplicación con pip. 
En este caso instalamos Flask el framework web y Gunicorn como servidor web.

		  “$ pip install Flask gunicorn”

* Una vez que tenemos todo estos pasos, desarrollamos nuestro proyecto en Python. 
Para ejecutar nuestro proyecto tenemos que utilizar un archivo ProcFile que debe estar en el directorio raiz 
con la siguiente linea:
		
		  “web: gunicorn pro:app”

* Iniciamos los servicios en nuestro ProcFile local:
	
		  “$ foreman start”

* Para que Heroku reconozca las aplicaciones Python necesitamos un arhivo 
con el nombre requirements.txt que debe estar en directorio raiz del proyecto con las siguientes lineas:
	
		  “$ pip freeze > requirements.txt”
	
			Flask==0.9
			Jinja2==2.6
			Werkzeug==0.8.3
			gunicorn==0.17.2

* Una vez realizados todos los pasos anteriores, creamos el repositorio con git:
		  
		  "$ git init”
	          “$ git add .”
	          “$ git commit -m "init"”
	
* Despues creamos nuestro proyecto en Heroku:

	          “$ heroku create” y por ultimo subimos el proyecto con: “$ git push heroku master”


Para poder visitar la aplicación, lo podremos realizar desde este link:
	
	http://young-bastion-6671.herokuapp.com/
	
[Captura Pratica1](https://github.com/rafacruiz/IV/blob/master/f.png)

