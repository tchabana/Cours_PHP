
# <span style="color:green">Introduction au Développement Web


## C'est quoi le développement web ?

**Apparu avec Internet, le développement web fait référence au processus d'écriture d'un site ou d'une page web dans un ou plusieurs langages de programmation**.


## Architecture Client-Serveur

 **Une architecture client-serveur représente l'environnement dans lequel des applications de machines clientes communiquent avec des applications de machines de type serveurs**.


## Installation

Apache: `sudo apt install apache2`
Php : `sudo apt install  php  libapache2-mod-php`

## Configuration

### Pour afficher les erreur de script dans le navigateur
`display_errors = On`
/etc/php/8.1/apache2/php.ini

### Pour afficher les erreur de script dans le navigateur
Ajouter dans le ficher `/etc/apache2/mods-avallable/php8.1.conf` la directive 
`php_value display_errors on`


## PHP hello world

- créer un ficher .php dans le répertoire /var/www/html
- ajouter le contenue suivant
```
<?php
	phpinfo();
?>
```
- ouvrer le navigateur , allez à l'adresse 127.0.0.1/[nom_de_votre ficher_php]