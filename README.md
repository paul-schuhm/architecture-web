# architecture-web

- [architecture-web](#architecture-web)
  - [Objectifs](#objectifs)
  - [Programme](#programme)
  - [Fonctionnement d'Internet](#fonctionnement-dinternet)
  - [Serveur web Apache](#serveur-web-apache)
    - [TP 1 : Apache 2, first steps](#tp-1--apache-2-first-steps)
      - [Extension du TP](#extension-du-tp)
    - [Réécriture d'URL](#réécriture-durl)
  - [Unix](#unix)
    - [Installation et configuration sécurisée d'un serveur SSH](#installation-et-configuration-sécurisée-dun-serveur-ssh)
    - [Exercices](#exercices)
      - [Exercice 1 : Apprivoiser un éditeur de texte](#exercice-1--apprivoiser-un-éditeur-de-texte)
      - [Exercice 2 : se créer ses commandes avec des alias (man, ls, cut, grep, tr)](#exercice-2--se-créer-ses-commandes-avec-des-alias-man-ls-cut-grep-tr)
  - [Git, first steps](#git-first-steps)
  - [Références](#références)
  - [Ressources connexes](#ressources-connexes)

## Objectifs

Maîtriser les environnements d'hébergements web sous GNU/Linux et savoir administrer un système GNU/Linux pour le web.

## Programme

- Rappels sur le fonctionnement des réseaux et d'Internet (design, protocoles et matériel)
- Fonctionnement du protocole TCP
- Présentation de Debian
- Mise en place d'une machine virtuelle Debian avec publication de ports
- Initiation à la philosophie des systèmes UNIX
- Administration de base sur GNU/Linux :
  - Utiliser les commandes de base du *shell* (rappels)
  - Créer des alias et utiliser `.bashrc`
  - Utiliser un éditeur de texte (nano, vi(m) ou emacs)
  - Créer un utilisateur
  - Comprendre et gérer correctement les droits sur les fichiers
  - Gérer les paquets avec `apt` (mise à jour, installation/suppression)
  - Installer et configurer un serveur SSH
  - Sécuriser une connexion SSH (usage de clés de chiffrement)
  - Installer et configurer le serveur web Apache 2
  - Savoir utiliser les services de `systemd` (démarrage, arrêt, status, *enabled/disabled*)
  - Afficher les sockets
  - Scanner les ports
- Introduction à Git et Github
- Déploiement de clé publique sur Github
- Déploiement manuel d'un site/application web avec git et un dépôt *remote*
- Fonctionnement d'Apache :
  - Configurations d'Apache (principale, par site, `.htaccess`)
  - Mise en place d'un site web (activer/désactiver)
  - Les *Virtual Host*
  - Mise en place de plusieurs sites web
  - Les directives principales
  - Mise en place d'un site web PHP avec le module Apache
  - La réécriture d'URL avec le module `mod_rewrite`
  - Installation et usage d'un certificat TLS

## Fonctionnement d'Internet

- Parcours d'une requête HTTP sur Internet
- [Consulter le glossaire (protocoles, matériel, modèle OSI et couches, etc.)](./glossaire.md) associé

## Serveur web Apache

### TP 1 : Apache 2, first steps

[Apache HTTP Server : guide pratique (vhosts, TLS, performances) : *Servir un site statique avec Apache*](https://blog.stephane-robert.info/docs/services/web/apache/#servir-un-site-statique), de [Stéphane Robert](https://blog.stephane-robert.info/). **Réaliser le TP** jusqu'à [Activer HTTPS avec Let’s Encrypt](https://blog.stephane-robert.info/docs/services/web/apache/#activer-https-avec-lets-encrypt) (exclus).

#### Extension du TP

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
11. Apache enregistre des *logs* (activité du site et erreurs du serveur). Où les trouvent-on ? Inspecter les avec `cat`. Monitorer les logs en temps réel avec `tail -f /path/vers/fichier_log`.

> N'hésitez pas à [utiliser la documentation très complète](https://httpd.apache.org/docs/current/) (et traduite en français) d'Apache pour vous former, confirmer ou vérifier des informations. La documentation offre des guides, des conseils (sécurité, etc.), des exemples ainsi que la référence de toutes les directives.

### Réécriture d'URL

[Consulter la documentation officielle](https://httpd.apache.org/docs/current/fr/rewrite/intro.html)

1. À quoi sert la réécriture d'URL ? Peut-elle être placée dans un fichier .htacess ?
2. Comment *activer* le module `rewrite` et vérifier qu'il est bien installé ?
3. A l'aide des directives d'Apache de réécriture d'URL, implémenter les URL suivantes :
   1. Client : `/ancien-contact` réécrite en `/ancien-contact.html`
   2. Client : `/a-propos.html` réécrite en `/a-propos.php`
   3. Client : `/article-42` réécrite en `/article.php?id=42`, où `id` est un entier positif

4. À quoi servent les *flags* suivants :
   1. [L]
   2. [R]
   3. [NC]
   4. [QSA]
   5. [F]

<!-- 
1. RewriteRule ^ancien-contact$ ancien-contact.html [L]
2. RewriteRule ^a-propos\.html$ a-propos.php [L], si l'utilisateur tape` monsite.com/a-propos.html`, le serveur va chercher silencieusement le fichier `a-propos.php` sans changer l'adresse dans la barre du navigateur.
3. 
 -->

> Utiliser l'excellent site [Regexr](https://regexr.com/) pour tester vos expressions régulières et réviser les éléments de syntaxe des expressions.

## Unix

### Installation et configuration sécurisée d'un serveur SSH

[Consulter et suivre le guide](https://ftp.pschuhmacher.com/unix/guide-serveur-ssh.html)

### Exercices

#### Exercice 1 : Apprivoiser un éditeur de texte

Pour travailler sur des serveurs GNU/Linux, il est **indispensable de maîtriser les bases d'un éditeur de texte dans le shell**.

**Choisissez** un éditeur de texte parmi `nano`, `vim` ou `emacs` et **réalisez un/son tutoriel** pour apprendre les bases : **créer**, **parcourir** et **éditer** un fichier, faire une **recherche** par *pattern*.

- nano : `man nano`, liste des commandes `Ctr+ G` ;
- vim : `vimtutor`
- emacs : emacs, puis `Ctr + h t`

> L'avantage de `nano` et de `vi`(m), c'est qu'**ils sont installés par défaut** sur toutes les distributions GNU/Linux. Ainsi, si vous de disposez pas des privilèges pour installer un autre éditeur de texte, vous êtes en mesure de travailler sereinement.

#### Exercice 2 : se créer ses commandes avec des alias (man, ls, cut, grep, tr)

0. **Inspecter** la sortie de `man -f ls cut grep tr` pour savoir ce que fait chaque commande;
1. **Créer** un alias `lls` qui affiche la liste longue triée par taille décroissante (en utilisant `ls -l`);
2. **Créer** un alias `dirs` qui n’affiche que les répertoires du répertoire courant (en utilisant `ls`, `grep` ou `cut`);
3. **Créer** un alias `big` qui affiche uniquement les 5 plus gros fichiers du répertoire courant;
4. **Créer** un alias `owners` qui affiche uniquement propriétaire et nom de fichier (en utilisant `ls`, `cut` et `tr`);
5. **Enregistrer** ces alias dans votre fichier `~/.bash_aliases`.

> Conseil : dès que vous rencontrez un nouveau programme/commande, utiliser le manuel `man <nouveau programme>`. Apprenez à utiliser `man` (navigation, recherche par *pattern* pour retrouver rapidement une option)

## Git, first steps

~~~bash
#installer
apt install git
#créer un dépôt
git init
#configurer git
git config --global user.name "votre name"
git config --global user.emaim "votre emails"
git config --global core.editor "votre éditeur préféré"
#vérifier la configuration
git config --list
#éditer la configuration
git config --global --edit
#renommer branche 'master' en 'main'
git branch --move master main
#lister les branches
git branch
#préparer un commit
git add
#faire un commit
git commit -m "message"
#inspecter
git status
git log
~~~

## Références

> Ouvrages recommandés !

- [Les réseaux de zéro : comprendre les réseaux par la pratique](https://www.editions-eyrolles.com/livre/les-reseaux-de-zero), publié chez Eyrolles, par Vincent Sénétaire, Jean-Manassé Pouabou, 2022. **Excellent ouvrage**, LP++
- [TCP/IP Network Administration](https://www.oreilly.com/library/view/tcp-ip-network-administration/0596002971/), publié chez O'Reilly, par Craig Hunt, 2002. LP+

## Ressources connexes

- [Glossaire](./glossaire.md) : définition des protocoles, modèle OSI, matériel, etc.
