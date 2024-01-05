# Apache-tuto

## Téléchargement et installation

`sudo dnf install httpd`

`systemctl enable httpd`

*http://localhost/*

## Manuel

`sudo dnf install httpd-manual`

## user et groupe

`grep apache /etc/group`

`grep apache /etc/passwd`

`grep apache /etc/shadow`

## Lancer Apache

`systemctl start httpd`

`/etc/rc.d/init.d/httpd start`

## Ajouter index.html

`/var/www/html`

```html
<html>
  <head>
    <title>My Website</title>
  </head>
  <body>
    <h1>Welcome to My Website!</h1>
  </body>
</html>
```

## Fichier de configuration

*/etc/httpd/conf/httpd.conf*

```
<Directory /var/www/html>
	Order allow, deny
 	Allow from all
</Directory>
```

Verifier la syntax :

`apachectl configtest`

## Les modules

Lister les modules :

`httpd -M`

`/etc/httpd/modules`

Installer module :

`sudo yum install mod_suphp.x86_64`

info.php :

```
<?php
phpinfo();
```

## Configuration du module server-info

```
<Location /server-info>
    SetHandler server-info
</Location>
```

## Virtual Hosts

utilisation du */etc/hosts*

httpd.conf :
```
<VirtualHost *:80>
    DocumentRoot "/var/www/exemple1"
    ServerName exemple1

</VirtualHost>
```
## HTTPS

`ssl_module`

Generer la certif :

`sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt`

```
<VirtualHost *:80>
    ServerName exemple
    Redirect / https://exemple/
</VirtualHost>


<VirtualHost *:443>
   ServerName exemple
   DocumentRoot /var/www/exemple

   SSLEngine on
   SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
   SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key
</VirtualHost>
```
