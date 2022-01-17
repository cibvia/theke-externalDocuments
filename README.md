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

## Règles de nettoyage des documents

(fonctionnalité expérimentale)

Chaque fiche peut contenir des règles de nettoyage permettant un plus bel affichage des documents dans Theke.

**Attention.** Cette fonctionnalité n'est pas encore disponible dans la version principale de Theke.

### Syntaxe

Les règles de nettoyage aide Theke à isoler le contenu d'un document externe et à éliminer tout ce qui est inutile. Ces indications sont données à partir d'un certain nombre de mots clés et de [sélecteurs](https://facelessuser.github.io/soupsieve/selectors/).

Voici un exemple de règles.

```
cleaning_rules:
    version: 1
    content:
        selector: div.documento div.text:nth-child(2)

    remove:
        - p[align=center]:has(:not(b))

    layouts:
        h2:
            selector: p[align=center]:has(b)
        h3:
            selector: p:has(b)
```

* `version` : numéro de version de l'API (pour le moment 1).
* `content` (obligatoire) : désigne le contenu du document.
* `remove` : liste de balises à supprimer.
* `layouts` : règles permettant d'identifier les éléments structurants du document.