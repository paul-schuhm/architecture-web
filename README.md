# architecture-web

- [architecture-web](#architecture-web)
  - [Objectifs](#objectifs)
  - [Programme](#programme)
  - [Serveur web Apache](#serveur-web-apache)
    - [TP 1 : Apache first steps](#tp-1--apache-first-steps)
      - [Extension du TP](#extension-du-tp)
  - [Unix](#unix)
    - [Exercice : se créer ses commandes avec des alias (man, ls, cut, grep, tr)](#exercice--se-créer-ses-commandes-avec-des-alias-man-ls-cut-grep-tr)
    - [Installation et configuration sécurisée d'un serveur SSH](#installation-et-configuration-sécurisée-dun-serveur-ssh)
  - [Git, first steps](#git-first-steps)
  - [Références](#références)


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
  - Gérer des droits sur les fichiers
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


## Serveur web Apache

### TP 1 : Apache first steps

[Apache HTTP Server : guide pratique (vhosts, TLS, performances)](https://blog.stephane-robert.info/docs/services/web/apache/#servir-un-site-statique), de Stéphane Robert. Service un site statique avec Apache. Réaliser le TP jusqu'à [Activer HTTPS avec Let’s Encrypt](https://blog.stephane-robert.info/docs/services/web/apache/#activer-https-avec-lets-encrypt) (exclus).

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

## Unix

### Exercice : se créer ses commandes avec des alias (man, ls, cut, grep, tr)

0. **Inspecter** la sortie de `man -f ls cut grep tr` pour savoir ce que fait chaque commande;
1. **Créer** un alias `lls` qui affiche la liste longue triée par taille décroissante (en utilisant `ls -l`);
2. **Créer** un alias `dirs` qui n’affiche que les répertoires du répertoire courant (en utilisant `ls`, `grep` ou `cut`);
3. **Créer** un alias `big` qui affiche uniquement les 5 plus gros fichiers du répertoire courant;
4. **Créer** un alias `owners` qui affiche uniquement propriétaire et nom de fichier (en utilisant `ls`, `cut` et `tr`);
5. **Enregistrer** ces alias dans votre fichier `~/.bash_aliases`.

> Conseil : dès que vous rencontrez un nouveau programme/commande, utiliser le manuel `man <nouveau programme>`. Apprenez à utiliser `man` (navigation, recherche par *pattern* pour retrouver rapidement une option)

### Installation et configuration sécurisée d'un serveur SSH

[Consulter et suivre le guide](https://ftp.pschuhmacher.com/unix/guide-serveur-ssh.html)

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