# Práctica Autenticación en Nginx
 - Lo primero es usar de principios el ejercicio de antes. Nos lo bajamos de github. 
 - Comprobamos que funciona perfectamente.
 ![Comprobar](assets/img/Comrpobar.png)
##  Autenticación
 - Debemos comprobar si el openssl esta intalado, se conprueba con (dpkg -l | grep openssl)
 ![Comprobar openssl](assets/img/ComprobarOpenssl.png)
 - Ahora creamos un archivo done van a estar los usuarios y contraseñas 
 ![Creacion archivo Usuario y passwrd](assets/img/CreacionPasswrd.png)

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

