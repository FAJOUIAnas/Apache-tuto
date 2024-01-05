# Apache-tuto

## Téléchargement et installation

`sudo dnf install httpd`

`systemctl enable httpd`

*http://localhost/*

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
	Order allow,deny
 	Allow from all
</Directory>
```

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
