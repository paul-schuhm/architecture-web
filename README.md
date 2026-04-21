# architecture-web

- [architecture-web](#architecture-web)
  - [TP 1 : Apache first steps](#tp-1--apache-first-steps)
    - [Extension du TP](#extension-du-tp)
  - [Exercices](#exercices)
    - [Exercice : se créer ses commandes avec des alias (man, ls, cut, grep, tr)](#exercice--se-créer-ses-commandes-avec-des-alias-man-ls-cut-grep-tr)
  - [Installation et configuration sécurisée du serveur SSH](#installation-et-configuration-sécurisée-du-serveur-ssh)
  - [Vim, first steps](#vim-first-steps)


## TP 1 : Apache first steps

[Apache HTTP Server : guide pratique (vhosts, TLS, performances)](https://blog.stephane-robert.info/docs/services/web/apache/#servir-un-site-statique), de Stéphane Robert. Service un site statique avec Apache. Réaliser le TP jusqu'à [Activer HTTPS avec Let’s Encrypt](https://blog.stephane-robert.info/docs/services/web/apache/#activer-https-avec-lets-encrypt) (exclus).

### Extension du TP

1. Comment Apache sait quel site afficher quand j’ai plusieurs domaines et plusieurs sites web ?
2. Comment tester le fonctionnement de ma configuration multisite avec le client cURL ?
3. Que fait la commande `sudo chown -R www-data:www-data /var/www/monsite` ? Qui est l'utilisateur `www-data` ?
4. A quoi sert la directive suivante :

~~~
    <Directory /var/www/monsite>
        Options -Indexes +FollowSymLinks
        AllowOverride None
        Require all granted
    </Directory>
~~~

5. Que fait la commande `sudo apache2ctl configtest` ?
6. Que signifie la directive `<VirtualHost *:80>` ?
7. A quoi sert la directive `ServerName` ?
8. Peut-on *surcharger* (*override*) une configuration d'un site web avec Apache ? Si oui, comment ?
9. A quoi sert le programme `apache2ctl` ?
10. A quoi servent les directives `<Directory>`, `<Files>` et `<FilesMatch>`. Où se placent-elles ?

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

## Vim, first steps

~~~bash
apt install git
git init
git config --global user.name "votre name"
git config --global user.emaim "votre emails"
git config --list
git config --global core.editor "votre éditeur préféré"
git config --global --edit
#renommer branche 'master' en 'main'
git branch --move master main
#lister les branches
git branch
~~~

