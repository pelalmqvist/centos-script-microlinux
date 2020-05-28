# Script de configuration post-installation pour serveurs CentOS 7

(c) Niki Kovacs, 2020 traduit par TRISTAN AGNELLI

Ce dépot fournit un script de configuration post-installation pour les serveurs sous CentOS 7 ainsi qu'une liste de scripts utiles et des modèles de fichiers de configuration pour des services fréquemment utilisés.

Realiser les tâches suivants :
  
  1. Installer un système d'exploitation CentOS minimal

  2. Créer un utilisateur différent de "root" et sans droits administrateurs 

  3. Installer git : "sudo yum install git"

  4. Récuperer le script : "git clone https://gitlab.com/kikinovak/centos-7.git"

  5. Se placer dans le nouveau répertoire : "cd centos-7"

  6. Lancer le script : "sudo ./centos-setup.sh --setup"

  7. Boire un café pendant que le script fait tout le boulot

  8. Redémarrer le système

## Personaliser un serveur CentOS

Transformer une installation minimale de CentOS en un serveur fonctionnel revient toujours à réaliser une série d'étapes plus ou moins chronophages.
Votre expérience et vos préférences sont peut être différentes des miennes mais voila ce que je configure habituellement sur une nouvelle installation d'un système CentOS :

  * Personnaliser le terminal Bash : invite, alias, etc...

  * Personnaliser Vim

  * Configurer des dépots officiels et/ou tiers

  * Installer un ensemble d'outils en ligne de commandes

  * Supprimer un tas de paquets inutiles

  * Donner à l'utilisateur administrateur l'accès aux journaux système

  * Désactiver l'IPv6 et reconfigurer les services qui en dépendent
  
  * Configurer un mot de passe persistant pour "sudo" 

  * Etc...

Le script "centos-setup.sh" s'occupe de toutes ces étapes.

Configure Bash et Vim ainsi qu'une résolution de la console plus lisible

```
# ./centos-setup.sh --shell
```

Configure les déptos tiers:

```
# ./centos-setup.sh --repos
```

Installe les paquets "Core" et "Base" en plus de quelques outils supplémentaires:

```
# ./centos-setup.sh --extra
```

Supprime quelques paquets non nécessaires:

```
# ./centos-setup.sh --prune
```

Donne la permission à l'administrateur d'accèder aux journaux système:

```
# ./centos-setup.sh --logs
```

Désactive IPv6 et reconfigurer les services dépendant:

```
# ./centos-setup.sh --ipv4
```

Configure un mot de passe persistant pour sudo:

```
# ./centos-setup.sh --sudo
```

Réalise toutes les actions ci-dessus en une seule fois:

```
# ./centos-setup.sh --setup
```

Supprime les paquets et revient à un système de base amelioré:

```
# ./centos-setup.sh --strip
```

Affiche le message d'aide:

```
# ./centos-setup.sh --help
```

Si vous voulez savoir ce qu'il se passe sous le capot, ouvrez un deuxième terminal et regardez les logs:

```
$ tail -f /tmp/centos-setup.log
```

