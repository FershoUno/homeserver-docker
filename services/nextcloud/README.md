# Nextcloud

Implementación de Nextcloud Local ejecutando:  

~~~
docker-compose up -d
~~~

> La instalación puede demorar dependiendo la velocidad de internet y los recursos de hardware que tenga.

Ingrese esta URL en el navegador:
~~~
http://localhost:8000
~~~
## Credenciales
Una vez que este en marcha Nextcloud, le va pedir crear una cuenta de administrador, se recomienda que uno mismo cree las credenciales, si no, puede optar por usar esta credencial de ejemplo:
~~~
  user      : administrador
  contraseña: c74e988c3962494db0cbc76ad8e126ce
~~~

## Configuración Adicional
Esta configuración adicional se debe realizar ya que Nextcloud por defecto no va a permitir que otros dispositivos de la red puedan acceder, y desde luego arroja el siguiente mensaje:  

#### Mensaje
Este mensaje se debe a que el dominio que utiliza Nextcloud es 0.0.0.0, los que significa que se tiene que configurar el archivo __config.php__ para asingar otro dominio de __confianza__.
~~~
Acceso a través de un dominio del que no se confía
etc.. etc..


~~~

Editar el archivo config.php, para este ejemplo se edita con __nano__ 

~~~
nano nextcloud/config/config.php
~~~

Agregar la dirección IP estatica del servidor en el array de __trusted_domains__ que se muestra de ejemplo:  
~~~
'trusted_domains' =>
array (
0 => '0.0.0.0:8000',
)
~~~
> Ejemplo de asignación IP estatica en el servidor: 192.168.2.150  

Añadir la dirección IP con el puerto que esta corriendo el Nextcloud
~~~
'trusted_domains' =>
array (
0 => '0.0.0.0:8000', '192.168.2.150:8000',
)
~~~

# Ultimo paso
Ya una vez editado, se procede a reiniciar el Nextcloud con __docker-compose__

~~~
docker-compose restart
~~~

Ahora si se puede acceder al Nextcloud desde otros dispositivos.

