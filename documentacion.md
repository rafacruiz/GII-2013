Actualización de pedidos
========================

Esta es una vista solamente para los trabajadores de la empresa. Desde aquí los diferentes trabajadores de las distintas secciones de la empresa, cambiaran el estado del pedido según donde este se encuentre.

La apariencia de actualizar pedido es la siguiente:

![captura_update](https://dl.dropbox.com/s/5d6y6sm3rkraoh9/AcEs.jpg)

Se trata de un simple formulario, con el cual pueden ir cambiando el estado del pedido. Para ello el pedido tiene que estar inicializado en la aplicación, esta operación se realiza desde la vista asignar pedido. 
Solamente necesitamos indicar el número del pedido que queremos cambiar y el nuevo estado al que queremos pasar el pedido y pulsamos actualizar para que la acción se complete.

Otra opción que contiene este apartado es la de enviar un correo electrónico, se puede ver en el código “.py”. Cuando el pedido pasa al estado completado, será enviado un correo al cliente indicado que su pedido está finalizado. 

Se ha utilizado el siguiente código:

Documento .py:

~~~~~~{.python}
def actualizar_pedido(request):
    usuario = request.session["usuario"]
    if usuario != '': 
        lista_estado1 = Pedidos.objects.filter(estado=1)
        lista_estado2 = Pedidos.objects.filter(estado=2)
        lista_estado3 = Pedidos.objects.filter(estado=3)
        lista_estado4 = Pedidos.objects.filter(estado=4)
        lista_estado5 = Pedidos.objects.filter(estado=5)
        lista_estado6 = Pedidos.objects.filter(estado=6)
        lista_estado7 = Pedidos.objects.filter(estado=7)
        lista_estado8 = Pedidos.objects.filter(estado=8)
        lista_estado9 = Pedidos.objects.filter(estado=9)
	
        if request.POST:
            form = SearchPedidoForm(request.POST)
            if form.is_valid():
		 npedidos = form.data['num_pedido']
		 nestado = form.data['estado']
		 Pedidos.objects.filter(num_pedido = npedidos).update(estado = nestado)
		 e = Pedidos.objects.filter(estado=9)
		 for datos in e:
		    asunto = "Ingenia Digital. Pedido: " + datos.concepto
		    men = "<h3>Ingenia Tracking:</h3>Estimado " + datos.usuario.nombre + ". <br> Su pedido con referencia: " + datos.num_pedido + " ha pasado al estado: Completo <br><br><hr>Ingenia Digital <br> Phone: (+34) 958 430 175 - Email: pedidos@ingenia-digital.com <br> Twitter: @Ingenia_Digital - Google plus: https://plus.google.com/+Ingenia-digital"
		    mensaje = """ <html> <body> %s </body> </html>""" % (men)
		    email = EmailMultiAlternatives(asunto, mensaje, to = [datos.usuario.correo_electronico])
		    email.attach_alternative(mensaje, "text/html")
		    email.send()
		 return render(request,'pedidos/actualizar_pedido.html', {'form' : form, 'lista_estado1': lista_estado1, 'lista_estado2': lista_estado2,'lista_estado3': lista_estado3,'lista_estado4': lista_estado4,'lista_estado5': lista_estado5, 'lista_estado6': lista_estado6, 'lista_estado7': lista_estado7, 'lista_estado8': lista_estado8, 'lista_estado9': lista_estado9})
        else:
	  form = SearchPedidoForm()
	return render(request,'pedidos/actualizar_pedido.html', {'form' : form, 'lista_estado1': lista_estado1, 'lista_estado2': lista_estado2,'lista_estado3': lista_estado3,'lista_estado4': lista_estado4,'lista_estado5': lista_estado5, 'lista_estado6': lista_estado6, 'lista_estado7': lista_estado7, 'lista_estado8': lista_estado8, 'lista_estado9': lista_estado9})
      
    else:
        form = LoginForm()
        args = {}
        args.update(csrf(request))
        args['form'] = form
        return render(request,'pedidos/index.html',args)
~~~~~~

Documento .html:

Forma de mostrar un estado.

~~~~~~{.html}
<div class="panel-heading">
	<a class="panel-title" data-toggle="collapse" data-parent="#panel-854654">Revisión</a>
</div>
	<div id="panel-element-590421" class="panel-collapse collapse in">
	{% if lista_estado1 %}							
	     
	      {% for npe in lista_estado1 %}
			<div class="panel-body">
			    <b>Número Pedido:</b> {{ npe.num_pedido }}
			    <b>Cliente:</b> {{ npe.usuario }}
			    <b>Concepto:</b> {{ npe.concepto }}
			    <b>Recepción:</b>{{ npe.forma_de_recepcion }}
			</div>
		{% endfor %}
		
	{% else %}
		<div class="panel-body">
			<p>No existen pedidos en este estado.</p></td>						
		</div>
	{% endif %}
										
	</div>
</div>
~~~~~~
