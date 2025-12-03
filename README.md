# Práctica Autenticación en Nginx
 - Lo primero es usar de principios el ejercicio de antes. Nos lo bajamos de github. 
 - Comprobamos que funciona perfectamente.
 ![Comprobar](assets/img/Comrpobar.png)
##  Autenticación
 - Debemos comprobar si el openssl esta intalado, se conprueba con (dpkg -l | grep openssl)
 ![Comprobar openssl](assets/img/ComprobarOpenssl.png)
 - Ahora creamos un archivo done van a estar los usuarios y contraseñas 
 ![Creacion archivo Usuario y passwrd](assets/img/CreacionPasswrd.png)
 - Creamos otro usuario y lo comprobamos con el comando cat /etc/nginx/.htpasswd
 ![Comprobar dos usuarios](assets/img/ComprobarDosUser.png)
### Configurar autenticación básica
 - Configuramos el archivo de sites-available y le añadimos las directrices de autenticación
 ![Conf Sites-available](assets/img/ConfiguracionSites-available.png)
 - Si buscamos el nombre del servidor en nuestro caso juanma-davids.test nos sale la autenticacion
 ![Pregunta credenciales](assets/img/PreguntaCredenciales.png)
   - si cancelamos nos sale el error 401 
   ![Error401](assets/img/Error401.png)
   - Y si ponemos credenciales correctas.
   ![Credenciales Bien](assets/img/CredencialesBien.png)
 - Nos iniciamos bien, y iniciamos tambien con otro usuario no dado de alta para dar error, y miramos los logs
 ![Comprobar Logs](assets/img/ComprobarLog.png)
 - Lo siguiente es hacer que una parte solo pida la autenticacion en este caso le pondremos a contact, 
 para eso lo que tenemos que hacer es ir a sites-availables y configurarlo como al principio en la parte de location borrar el auth.
 ![BorrarAuth](assets/img/borrarAuth.png)
 - y creamos un location = /contact.html por que es el que queremos meter la autenticacion, y al ir a contact no nos dejara, nos pedira autenticarnos
 ![Contact Auth](assets/img/authContact.png)
 ![Contact Auth](assets/img/ComprobarContact.png)

## Atentificacion Docker
- Primero descargo las utilidades de OpenSSl con el contenedor stakater/ssl-certs-generator
![Docker Pull](assets/img/cockerPull.png)

- Creo una carpeta donde guardare un bloc de notas para el usuario y contraseña.
![Crear conf](assets/img/htpasswd.png)
- Luego creo un usuario y una contraseña para la web.
![Usuario](assets/img/CrearArchivojuanma-davids.test.conf.png)
- Para despues crear una contraseña de forma no iteerativa 
![Crear contraseña](assets/img/contraseña.png)

- Configuro el contenerdor.
![Configuracion docker](assets/img/PegarBlocNotasjuanma-davids.test.conf.png)
- Luego busco en Internet por local, si me pide el usuario y la contraseña vamos por buen camino.
![Comprobacion Usuario Contraeña](assets/img/UsuarioContraseña.png)


### Acceso a contact.html
- Busco los logs que han intentado iniciar sesion
![Comprobacion Usuario Contraeña](assets/img/Logs.png)
- Aplicamos una restriccion al directorio raiz.
![Comprobacion Usuario Contraeña](assets/img/cambiarblocnotas.png)
- visualizamos en local contact.html
![Comprobacion Usuario Contraeña](assets/img/Visualizacioncontact.png)
- Para terminar la Tarea 2, hay que eliminar 
![Comprobacion Usuario Contraeña](assets/img/Borrar2lineas.png)

### Restriccion acceso IP
- Añadimos la APi dentro de juanma-davids.conf.test
![Comprobacion Usuario Contraeña](assets/img/AñadirlocationApi.png)
- Comprobamos si ha funcionado.
![Comprobacion Usuario Contraeña](assets/img/funcionamientoApi.png)
- Para luego denegar la IP con all el acceso se permite si se satisface al
menos una de las dos condiciones.
![Comprobacion Usuario Contraeña](assets/img/denegarIP.png)
- Comprobamos si funciona deny all con la IP
![Comprobacion Usuario Contraeña](assets/img/comprobardenegar.png)

### Configuracion para tener una IP valida y un usuario valido a la vez
- Modificamos con cat el archivo de bloc de notas para que desde tu máquina anfitriona se tenga que tener tanto una IP válida como
un usuario válido.
![Comprobacion Usuario Contraeña](assets/img/IPvalida.png)