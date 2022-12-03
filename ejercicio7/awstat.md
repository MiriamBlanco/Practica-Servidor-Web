`AWStats es una herramienta de informes estadísticos de análisis web, ya sea para servidores de correo, ftp, streaming, web, etc. A raíz de los archivos de log del servidor, AWStats genera informes numéricos y gráficos de barras y tablas, muy sencillos y completos.`

- Para instalar el servicio `AWStats`, introducimos el siguiente comando:

```bash
sudo apt-get install awstats
```

![image](/imagenes/26.png)

- Habilitamos el módulo `cgi` y reiniciamos apache:

```bash
sudo a2enmod cgi
```

![image](/imagenes/27.png)

- Como hay que editar el archivo de configuración `awstas.conf`, lo copiamos para poder recuparlo si se produce algún error:

```bash
sudo cp /etc/awstats/awstats.conf /etc/awstats/awstats.departamentos.centro.intranet.conf
```

- Editamos las siguientes líneas:

```apache
LogFile=”/var/log/apache2/access.log”
SiteDomain=”departamentos.centro.intranet” 
HostAliases=”departamentos.centro.intranet localhost 127.0.0.1” 
AllowToUpdateStatsFromBrowser=1
```

![image](/imagenes/28.png)
---------------------------
![image](/imagenes/29.png)
---------------------------
![image](/imagenes/30.png)
---------------------------
![image](/imagenes/31.png)

- Las estadísticas iniciales las generamos a partir de los registros del servidor para ello:

```bash
sudo /usr/lib/cgi-bin/awstats.pl -config=departamentos.centro.intranet -update
```

![image](/imagenes/32.png)

- Configuramos nuestro dominio `departamentos.centro.intanet` para que `AWStats` pueda hacer las estadísticas sobre él:

```bash
sudo cp -r /usr/lib/cgi-bin /var/www/html/departamentos.centro.intranet
```
```bash
sudo chown -R www-data:www-data /var/www/html/departamentos.centro.intranet/cgi-bin/
```

- Reiniciamos el sistema y comprobamos que se ha implementado `AWStats` correctamente, para saber qué introducir en el navegador he mirado el fichero `/usr/lib/cgi-bin`:

![image](/imagenes/34.png)

- Introduzco lo siguiente:

http://localhost/cgi-bin/awstats.pl?config=departamentos.centro.intranet

![image](/imagenes/33.png)

[Volver a la página principal](../README.md)
