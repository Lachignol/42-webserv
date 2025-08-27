# Projet Webserv - École 42

## Description
Webserv est un serveur HTTP écrit en C++ 98 conforme aux standards imposés, interprétant et servant les requêtes HTTP selon une configuration fournie. Le serveur implémente une communication non bloquante, gère plusieurs connexions et propose les méthodes HTTP GET, POST, et DELETE. Ce projet vise à comprendre en profondeur le protocole HTTP et le fonctionnement bas-niveau des serveurs web.

## Fonctionnalités

- Serveur HTTP multiclient fonctionnant en mode non bloquant (poll/epoll/select/kqueue).
- Gestion complète des requêtes HTTP GET, POST, DELETE.
- Support des fichiers statiques et CGI (Ruby, Pearl, Python, etc.).
- Analyse et respect d'un fichier de configuration modèle NGINX pour configurer les ports, routes, limites, redirections, pages d'erreur, etc.
- Traitement correct des erreurs HTTP avec pages personnalisées.
- Support des uploads de fichiers via POST.
- Serveur robuste ne plantant jamais même en cas de surcharge ou d'erreurs client.
- Prise en charge de plusieurs ports simultanés.
- Implémentation basée uniquement sur C++ 98 et système POSIX, sans librairies externes (Boost interdit).
- Conformité stricte avec les appels système listés (execve, poll, socket, fork uniquement pour CGI...).

## Règles importantes

- Utilisation obligatoire du mode non bloquant.
- Utilisation d’une seule instance de poll (ou équivalent) pour toutes les opérations I/O.
- Interdiction d'appeler read/write sans passer par poll.
- Pas d’utilisation abusive de errno après read/write.
- Pas de forking sauf pour CGI.
- Respect strict de la norme C++ 98.
- Le serveur doit rester toujours disponible et ne jamais planter.

## Bonus 

- Gestion des cookies et sessions (avec exemples).
- Support de multiples CGI.


## Compilation et exécution

### Compilation
Compilez le projet en lançant simplement la commande :
```
make
```

### Nettoyage
Pour nettoyer les fichiers objets :
```
make clean
```
Pour nettoyer les fichiers objets et l’exécutable :
```
make fclean
```

### Recompilation complète
Pour recompiler proprement :
```
make re
```

### Lancement
L’exécutable s’appelle `webserv` et doit être lancé avec un fichier de configuration en argument, par exemple :
```
./webserv config/default.conf
```

## Utilisation et tests

- Testez votre serveur avec un navigateur web ou par terminal via `telnet` ou `curl`.
- Testez la compatibilité HTTP 1.1 et le comportement des headers.
- Comparez les réponses de votre serveur avec celles de NGINX pour validation.
- Utilisez les scripts de tests en Python dans le dossier `tests` pour des scénarios automatisés.

## Remarques importantes

- Le serveur doit être testé en conditions de charge, il ne doit jamais planter ni rester bloqué.
- Respectez le standard HTTP dans les réponses et les codes d’état.
- Les CGI doivent fonctionner correctement dans leur environnement.
- Aucun backport ou fonction non conforme à C++ 98 ne doit être utilisé.


## Authors
- Arthur Oger | 42: aoger | GitHub: ![arthoge](https://github.com/arthoge)
- Alexandre Scordilis | 42: ascordil | GitHub: lachignol



