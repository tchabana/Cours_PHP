
## Port non disponible

```
apachectl[13331]: (98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
apachectl[13331]: (98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
```

1. **Utiliser `sudo` :** Ajoutez `sudo` avant la commande pour exécuter en tant que superutilisateur.
    
    bashCopy code
    
    `sudo lsof -t -i :80 | xargs sudo kill -9`
    
    Entrez votre mot de passe si nécessaire.
    
2. **Vérifier les permissions :** Assurez-vous que l'utilisateur exécutant la commande a les autorisations nécessaires pour tuer les processus. Vous pouvez être en mesure de le faire en tant qu'utilisateur root.
    
3. **Utiliser `fuser` comme alternative :** Si `lsof` n'est pas disponible ou ne fonctionne pas, vous pouvez utiliser `fuser` :
    
    bashCopy code
    
    `sudo fuser -k 80/tcp`
    
    Cette commande cherche à tuer les processus utilisant le port 80.

### Error AH00558: Could not reliably determine the server's fully qualified domain name

```
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
```


1.  Add a line containing `ServerName 127.0.0.1` to the end of the file:
/etc/apache2/apache2.conf

```
sudo nano /etc/apache2/apache2.conf
```

```
. . .
# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
ServerName 127.0.0.1
```



```
sudo apachectl configtest
```


resolve-link: https://www.digitalocean.com/community/tutorials/apache-configuration-error-ah00558-could-not-reliably-determine-the-server-s-fully-qualified-domain-name


## Le serveur renvoi le code source php, il ne génére pas le html attendue

### supprimer libapache2-mod-php
```
sudo apt purge libapache2-mod-php7.0 libapache2-mod-php
```
### Reinstaler libapache2-mod-php
```
sudo apt install libapache2-mod-php7.0 libapache2-mod-php
```
### Activer module php

La commande `sudo a2enmod php7.0` est utilisée pour activer le module PHP 7.0 dans le serveur web Apache sur un système Ubuntu
 ```
sudo a2enmod php7.0
```


