> NGINX es un famoso software de servidor web de código abierto. En su versión inicial, funcionaba en servidores web HTTP. Sin embargo, hoy en día también sirve como proxy inverso, balanceador de carga HTTP y proxy de correo electrónico para IMAP, POP3 y SMTP.

- Primero introducimos el siguiente comando para instalar `NGINX`:

```bash
sudo apt install nginx
```

![image](/imagenes/35.png)

- Ajustamos el firewall para permitir el acceso al servicio:

```bash
sudo ufw app list
```

![image](/imagenes/36.png)

- Habilitamos el servicio `Nginx HTTP`:

```bash
sudo ufw allow 'Nginx HTTP'
```

![image](/imagenes/37.png)

- El servicio ya estaría activo pero debemos cambiar el puerto del servidor para verlo correctamente:

```bash
sudo nano /etc/nginx/sites-available/default
```

![image](/imagenes/38.png)

- Reiniciamos el servicio:

```bash
sudo service nginx restart
```

- Y comprobamos que podemos visualizarlo en el navegador:

![image](/imagenes/39.png)

[Volver a la página principal](../README.md)
