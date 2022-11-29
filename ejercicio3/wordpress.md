- Primero descargamos WordPress desde su página oficial.

- Copiamos la carpeta dentro del dominio `centro.intranet`:

```bash
sudo cp -r /home/miriam/Desktop/wordpress-6.1.1-es_ES /var/www/centro.intranet/
```

- Le damos permisos:

```bash
sudo chown -R www-data:www-data centro.intranet
```

- Abrimos mysql:

```bash
sudo mysql -u root -p
```

![image](/imagenes/6.png)

- Creamos una base de datos wordpress:

```sql
create database wordpress;
```

- Le otorgamos todos los permisos al usuario que vamos crear:

```sql
grant all on wordpress.* to 'wordpressuser'@'localhost' identified by 'wordpressuser';
```

![image](/imagenes/7.png)

- Nos vamos al navegador e introducimos http://centro.intranet:

![image](/imagenes/8.png)

- Introducimos los datos:

![image](/imagenes/9.png)

- Y se iniciará el instalador:

![image](/imagenes/10.png)

- Una vez finalizada la instalación, iniciamos sesión:

![image](/imagenes/11.png)

- Y ya tendríamos todo listo:

![image](/imagenes/12.png)


[Volver a la página principal](../README.md)
