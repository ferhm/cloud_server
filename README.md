# Implementación de un servidor cloud

## ¿Cómo arrancar un servidor Apache?

La intención es implementar un servidor cloud en Ubuntu Server para aprender con ello sobre gestión de servidores y programación web.

Una vez que tengamos instalado Ubuntu Server, descargable de forma gratuita en la pagina oficial de Ubuntu.

En primer lugar nos aseguramos de tener el índice de paquetes locales actualizado.

~~~
sudo apt update
~~~

A continuación instalamos el servidor HTTP Apache el cual es un servidor web de código abierto para plataformas Unix, Windows, Mac entre otras.

~~~
sudo apt install apache2
~~~

Tenemos que configurar el cortafuegos para que **permita conexiones** al puerto al que se le va a solicitar servicio al servidor HTTP. Este suele ser el **puerto 80**.

Podemos listar los perfiles de las aplicaciones de las cuales tiene constancia el cortafuegos. En nuestro caso nos van a aparecer tres referentes a nuestro servidor.

* **Apache:** el perfil habilita exclusivamente el puerto 80 (normal, tráfico sin encriptar).
* **Apache Secure:** el perfil habilita solo el puerto 443 (tráfico encriptado mediante TLS/SSL).
* **Apache Full:** este perfil habilita ambos puertos, el 80 y el 443.

Se recomiento ser lo más restrictivo posible a la hora de abrir puertos y utilizar los estrictamente necesarios. De momento solo habilitaremos el puerto 80.

~~~
sudo ufw app list
sudo ufw allow Apache2
~~~

Habilitamos el firewall.

~~~
sudo ufw enable
~~~

Por último nos aseguramos de que está todo correcto viendo que el firewall se encuentra activo y nuestro servicio permite conexiones.

~~~
sudo ufw status
~~~

### Administración del servicio Apache

Para ver el estado de nuestro servicio.

~~~
sudo systemctl status apache2
~~~

Para detener el servicio.

~~~
sudo systemctl stop apache2
~~~

Para inicial el servicio.

~~~
sudo systemctl start apache2
~~~

Para reiniciar el servicio.

~~~
sudo systemctl status apache2
~~~

Para deshabilitar que el servicio se inicie automáticamente cuando el servidor arranque.

~~~
sudo systemctl disable apache2
~~~

Si por el contrario queremos habilitar que inicie.

~~~
sudo systemctl enable apache2
~~~

## Probando el servicio HTTP

Podemos obtener nuestra ip de la siguiente manera:
~~~
hostname -I
~~~
o
~~~
ifconfig
~~~
Tambíen podemos conocer cual es nuestra ip publica con alguna de las siguientes sentencias.

~~~
curl ifconfig.me
curl ifconfig.co
curl -4 icanhazip.com
~~~

Entonces ya podemos acceder a la pagina de prueba que tiene por defecto nuestro servicio Apache. Simplemente hay que introducir la dirección IP obtenida de nuestro servidor en la barra de direcciones del navegador y nos mostrara la página de prueba.








