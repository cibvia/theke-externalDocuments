# Theke − Collection de documents externes
*Collection de documents externes pour enrichir l'index de Theke.*

[Theke](https://github.com/a2ohm/theke) est un logiciel permettant de lire et d'étudier la Bible et l'enseignement de l'Église.

Ce logiciel s'appuie principalement sur des modules [sword](https://www.crosswire.org/sword/modules/index.jsp), mais il est aussi possible d'ajouter à son index des ressources externes. Chacune de ces ressources doit être décrite par une fiche descriptive stockée dans le dossier `~/.local/share/theke/external`. Ce dépôt rassemble une telle collection de fiches.

## Installation

Si besoin, créer le dossier accueillant les fiches des documents externes.

* `mkdir -p ~/.local/share/theke/external`

Si ce dossier existe déjà et qu'il n'est pas vide, déplacer les fichiers qu'il contient dans un répertoire temporaire.

* `mkdir /tmp/theke-external`
* `mv ~/.local/share/theke/external/* /tmp/theke-external/`

Cloner ensuite ce dépôt dans le dossier idoine (⚠️ ne pas oublier le `.` à la fin de la commande `git clone`).

* `cd ~/.local/share/theke/external`
* `git clone https://github.com/a2ohm/theke-externalDocuments.git .`

Si nécessaire, replacer les fiches temporairement mises de côté.

* `mv /tmp/theke-external/* ~/.local/share/theke/external/`
* `rm -r /tmp/theke-external`

## Mise à jour

Pour mettre à jour votre collection de fiches à partir du dépôt git, utilisez les commandes suivantes.

* `cd ~/.local/share/theke/external`
* `git pull`
