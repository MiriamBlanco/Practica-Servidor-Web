- Creamos el siguiente árbol de directorios dentro de /var/www/html/ para montar toda la aplicación:

```bash
sudo mkdir departamentos.centro.intranet
sudo mkdir mypythonapp
sudo mkdir public_html
```

![image](/imagenes/14.png)

![image](/imagenes/15.png)

- Dentro del directorio mypythonapp creamos la app controller.py:

```bash
sudo nano controller.py
```

- Escribimos lo siguiente:

```python
# -*- coding: utf-8 -*-

def application(environ, start_response): 
    # Genero la salida HTML a mostrar al usuario 
    output = "<p>Bienvenido a mi <b>PythonApp</b>!!!</p>" 
    # Inicio una respuesta al navegador 
    start_response('200 OK', [('Content-Type', 'text/html; charset=utf-8')]) 
    # Retorno el contenido HTML 
    return output
```

![image](/imagenes/16.png)

- Escribimos el siguiente contenido de VirtualHost dentro del archivo de configuración departamentos.centro.intranet.conf:

```bash
sudo nano /etc/apache2/sites-available/departamentos.centro.intranet.conf
```

```apache
<VirtualHost *:80> 
  ServerName python-web

  DocumentRoot /home/yo/curso-python/trunk/python-web/public_html 
  WSGIScriptAlias / /home/yo/curso-python/trunk/python-web/mypythonapp/controller.py 
  ErrorLog /home/yo/curso-python/trunk/python-web/logs/errors.log 
  CustomLog /home/yo/curso-python/trunk/python-web/logs/access.log combined 

  <Directory /> 
    Options FollowSymLinks 
    AllowOverride All 
  </Directory> 
</VirtualHost>
```

![image](/imagenes/17.png)

- Habilitamos el sitio web:

```bash
sudo a2ensite departamentos.centro.intranet.conf
```

![image](/imagenes/18.png)

- Recargamos apache

```bash
sudo service apache2 reload
```

- Y por último introducimos en el navegador la siguiente URL: http://departamentos.centro.intranet

![image](/imagenes/19.png)
