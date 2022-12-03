- Primero actualizamos el servidor e instalamos las utilidades de apache:

```bash
sudo apt-get update
sudo apt-get install apache2-utils
```

![image](/imagenes/20.png)

- Ahora creamos el usuario con el siguiente comando:

```bash
sudo htpasswd -c /etc/apache2/.htpasswd Miriam
```

- Y nos pedirá una contraseña:

![image](/imagenes/21.png)

- Nos vamos al archivo de configuración `/etc/apache2/sites-enabled/departamentos.centro.intranet.conf`, y añadimos lo siguiente:

```apache
<Directory "/var/www/html/departamentos.centro.intranet">
      AuthType Basic
      AuthName "Restricted Content"
      AuthUserFile /etc/apache2/.htpasswd
      Require valid-user
</Directory>
```

![image](/imagenes/22.png)

- Comprobamos que no hay fallos en la sintáxis:

```bash
sudo apache2ctl configtest
```

![image](/imagenes/23.png)

- Reiniciamos apache:

```bash
sudo systemctl restart apache2
```

- Comprobamos en el navegador que nos pide autenticarnos:

![image](/imagenes/24.png)

![image](/imagenes/25.png)

[Volver a la página principal](../README.md)
