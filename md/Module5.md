# <span style="color:green"> Gestion des Sessions et des Cookies

**On va stocker des informations avec des variables tout en les conservant de page en page. Nous utiliserons pour cela deux méthodes, les sessions ou les informations sont stockées de manière temporaire sur le serveur et les cookies ou c'est le navigateur qui les stockera.**

## Les Sessions

Les Sessions `$_SESSION` permettent de stocker des informations pendant la session de navigation de l'utilisateur. Pour travailler avec les sessions il faut commencer par initialiser la session :

```php
session_start()
```

> session_start() crée une session ou restaure celle trouvée sur le serveur, via l'identifiant de session passé dans une requête GET, POST ou par un cookie.

Une fois la session démarrée vous pourrez accéder à la variable `$_SESSION` qui se comporte comme un tableau. Vous pourrez l'utiliser pour sauvegarder ou récupérer des informations qui seront transférées aux pages suivantes.

## Les Cookies

Les Sessions sont automatiquement perdues quand l'utilisateur quitte le navigateur. Les Cookies vous permettent de stocker les informations de manière plus durable même après la fermeture du navigateur.

Attention cependant ! Les cookies sont stockés sur le navigateur de l'utilisateur et envoyés au serveur à chaque requête. Ils peuvent être modifié et consulté par l'utilisateur donc ne sauvegardez pas d'information sensible dans les Cookies (on utilisera un token plutôt qu'un id pour mettre en place une connexion persistante par exemple par exemple).

Pour sauvegarder une information dans un Cookie on utilisera la fonction `setcookie()`qui prendra en paramètre la date d'expiration :

```php
$fin = time() * 60 * 60 * 24;
setcookie('nom', 'John Doe', $fin);

echo $_COOKIE['nom'];
```

Contrairement aux Sessions, il n'est pas possible de stocker des types de variables complexes (tableau, objet...) donc si vous souhaitez sauvegarder un tableau dans un cookie il faudra le [serializer](http://php.net/manual/fr/function.serialize.php)

Plus d'informations sur le [fonctionnement des cookies](http://php.net/manual/fr/function.setcookie.php)
