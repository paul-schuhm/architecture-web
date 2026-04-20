# architecture-web

- [architecture-web](#architecture-web)
  - [Exercices](#exercices)
    - [Exercice : se créer ses commandes avec des alias (man, ls, cut, grep, tr)](#exercice--se-créer-ses-commandes-avec-des-alias-man-ls-cut-grep-tr)
  - [Installation et configuration sécurisée du serveur SSH](#installation-et-configuration-sécurisée-du-serveur-ssh)


## Exercices

### Exercice : se créer ses commandes avec des alias (man, ls, cut, grep, tr)

0. **Inspecter** la sortie de `man -f ls cut grep tr` pour savoir ce que fait chaque commande;
1. **Créer** un alias `lls` qui affiche la liste longue triée par taille décroissante (en utilisant `ls -l`);
2. **Créer** un alias `dirs` qui n’affiche que les répertoires du répertoire courant (en utilisant `ls`, `grep` ou `cut`);
3. **Créer** un alias `big` qui affiche uniquement les 5 plus gros fichiers du répertoire courant;
4. **Créer** un alias `owners` qui affiche uniquement propriétaire et nom de fichier (en utilisant `ls`, `cut` et `tr`);
5. **Enregistrer** ces alias dans votre fichier `~/.bash_aliases`.

> Conseil : dès que vous rencontrez un nouveau programme --> `man <nouveau programme>`
> Dans la suite de la formation, nous allons apprendre à créer **nos propres fonctions (programmes ?)** en sh/bash pour créer des commandes encore plus complexes

## Installation et configuration sécurisée du serveur SSH

[Voir le guide](https://ftp.pschuhmacher.com/unix/guide-serveur-ssh.html)
