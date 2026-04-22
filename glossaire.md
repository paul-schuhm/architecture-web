# Architecture d'Internet (et du web) - Glossaire

- [Architecture d'Internet (et du web) - Glossaire](#architecture-dinternet-et-du-web---glossaire)
  - [Modèle OSI](#modèle-osi)
  - [Domain Name Service (DNS)](#domain-name-service-dns)
  - [Autonomous System (AS)](#autonomous-system-as)
  - [Trame (Ethernet)](#trame-ethernet)
  - [Adresse MAC (*Media Access Control*)](#adresse-mac-media-access-control)
  - [ARP (Address Resolution Protocol)](#arp-address-resolution-protocol)
  - [IP (Internet Protocol)](#ip-internet-protocol)
  - [ICMP (Internet Control Message Protocol)](#icmp-internet-control-message-protocol)
  - [TCP (Transmission Control Protocol)](#tcp-transmission-control-protocol)
  - [UDP (User Datagram Protocol)](#udp-user-datagram-protocol)
  - [Border Gateway Protocol (BGP)](#border-gateway-protocol-bgp)
  - [HTTP (HyperText Transfert Protocol)](#http-hypertext-transfert-protocol)
  - [FTP (File Transfert Protocol)](#ftp-file-transfert-protocol)
  - [FTPS (File Transfer Protocol Secure)](#ftps-file-transfer-protocol-secure)
  - [SSH (Secure Shell)](#ssh-secure-shell)
  - [SFTP (SSH File Transfer Protocol )](#sftp-ssh-file-transfer-protocol-)
  - [SMTP (Simple Mail Transfer Protocol)](#smtp-simple-mail-transfer-protocol)

## Modèle OSI

Le [modèle *Open Systems Interconnection* (OSI)](https://fr.wikipedia.org/wiki/Mod%C3%A8le_OSI) est une façon *standardisée* de segmenter en plusieurs *couches* le processus de communication entre deux entités. 

Une *couche* est un *ensemble de services* accomplissant un but précis. Chaque couche du modèle OSI communique avec les couches au-dessus et au-dessous d'elle. La couche en-dessous fournit des services que la couche en cours utilise et cette dernière pourvoit des services dont la couche au-dessus d'elle aura besoin pour assurer son rôle.

![](./osi-diagram.svg)

Chaque couche *expose une interface à la couche supérieure* et dispose de son implémentation.

Ainsi, l'*implémentation* de chaque couche peut changer, évoluer, être remplacée sans impacter les autres. Par exemple, cela explique pourquoi nous avons pu passer de l'Internet filaire au Wi-Fi sans avoir à réécrire le protocole HTTP : seule l'implémentation des couches basses a changé, tandis que les couches supérieures sont restées identiques. C'est un cas classique d'application du [*polymorphisme*](https://en.wikipedia.org/wiki/Polymorphism_(computer_science)) et de la [Separation of Concerns (SoC)*](https://en.wikipedia.org/wiki/Separation_of_concerns).

Grâce à ces principes, chaque couche n'a besoin de connaître que l'*interface* de la couche inférieure, sans se soucier de ses détails d'implémentation (*abstraction*) et de fournir une interface à la couche supérieure. En masquant la complexité des couches inférieures, le modèle OSI permet au développeur·se web de se concentrer sur la logique métier et la formation correcte de ses messages HTTP, avec la certitude que les octets arriveront à destination, sans avoir à se soucier de *comment* ces octets sont transmis sur le réseau.

Le modèle OSI segmente le processus de communications en *sept* couches :

- Application
- Présentation
- Session
- Transport
- Réseau
- Liaison (de données)
- Physique

> Un moyen mnémotechnique pour s'en souvenir "**P**artout **L**e **R**oi **T**rouve **S**a **P**lace **A**ssise"

## Domain Name Service (DNS)

Un service informatique *distribué* dont la fonction principale est de maintenir et de fournir les associations entre les *noms de domaine* Internet avec *leurs [adresses IP](#ip-internet-protocol)*.

## Autonomous System (AS)

Un ensemble de réseaux informatiques IP intégrés à Internet et dont la politique de routage interne (routes à choisir en priorité, filtrage des annonces) est cohérente. Un AS est généralement sous le contrôle d'une entité ou organisation unique, typiquement un fournisseur d'accès à Internet. [Environ 120 000 en 2026](https://www-public.telecom-sudparis.eu/~maigron/rir-stats/rir-delegations/world/world-asn-by-number.html).

## Trame (Ethernet)

Une trame Ethernet est un message écrit en système binaire. Afin de limiter la taille de l'affichage, on choisit parfois de grouper ces bits en octets et de les représenter sous forme hexadécimale. 

## Adresse MAC (*Media Access Control*)

Une adresse MAC (*Media Access Control*), parfois nommée *adresse physique*, est un identifiant physique stocké dans une carte réseau ou une interface réseau similaire. Chaque adresse MAC est unique au monde. Toutes les cartes réseau ont une adresse MAC, même celles contenues dans les PC et autres appareils connectés (tablette tactile, smartphone, consoles de jeux, réfrigérateurs, montres, etc.).

## ARP (Address Resolution Protocol)

L'Address Resolution Protocol (ARP, protocole de résolution d’adresse) est un protocole utilisé pour *associer l'adresse de protocole de couche réseau* (typiquement une adresse IPv4) d'un hôte distant, *à son adresse de protocole de couche de liaison* (typiquement une adresse MAC). 

> Il se situe à l’interface entre la couche réseau (couche 3 du modèle OSI) et la couche de liaison (couche 2 du modèle OSI).

La couche réseau construit une voie de communication de *bout à bout* à partir de voies de communication avec ses voisins directs. Ses apports fonctionnels principaux sont 1) le routage (trouver un chemin reliant 2 machines) 2) relayage/retransmission des données.

## IP (Internet Protocol)

Une famille de protocoles de communication de réseaux informatiques permettent un service d'adressage unique pour l'ensemble des terminaux connectés. 

> Couche Réseau (Couche 3 du modèle OSI)

## ICMP (Internet Control Message Protocol)

Le [protocole IP](#ip-internet-protocol) ne gérant que le transport des paquets et ne permettant pas l'envoi de messages d'erreur, on lui associe ICMP pour contrôler les erreurs de transmission. ICMP permet de transporter des messages de contrôle et d’erreur pour qu'une machine émettrice sache qu'il y a eu un incident de réseau, par exemple lorsqu’un service ou un hôte est inaccessible. La commande Ping est un exemple d'application utilisant des messages de contrôle ICMP.

> Couche Réseau (Couche 3 du modèle OSI)

## TCP (Transmission Control Protocol)

TCP est un protocole de transport fiable, en mode connecté, basé sur un *stream* (flux) d'octets découpé en *segments*.

> Couche Transport (Couche 4 du modèle OSI)

## UDP (User Datagram Protocol)

UDP permet la transmission de données (sous forme de [datagrammes](https://fr.wikipedia.org/wiki/Datagramme)) de manière très simple entre deux entités, chacune étant définie par une adresse IP et un numéro de port. Aucune communication préalable n'est requise pour établir la connexion, au contraire de TCP (qui utilise le procédé de *handshaking*). UDP utilise un mode de transmission *sans connexion*. 

> Couche Transport (Couche 4 du modèle OSI)

## Border Gateway Protocol (BGP)

Protocole d'échange de route externe. Permet aux routeurs de s'échanger les "meilleurs" path (adresses IP) pour passer d'[un AS](#autonomous-system-as) à l'autre : chemin le plus stable et conforme à des accords commerciaux, souveraineté des états, etc. (pas le chemin le plus cours). Ce protocole dote les routeurs d'une table de routage. 

> Couche Application (Couche 7 du modèle OSI)


## HTTP (HyperText Transfert Protocol)

> Couche Application (Couche 7 du modèle OSI)

## FTP (File Transfert Protocol)

> Couche Application (Couche 7 du modèle OSI)

## FTPS (File Transfer Protocol Secure)

> Couche Application (Couche 7 du modèle OSI)


## SSH (Secure Shell)

> Couche Application (Couche 7 du modèle OSI)

## SFTP (SSH File Transfer Protocol )

> Couche Application (Couche 7 du modèle OSI)

## SMTP (Simple Mail Transfer Protocol)

> Couche Application (Couche 7 du modèle OSI)
