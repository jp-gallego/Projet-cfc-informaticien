# Installation de Windows 11 sur VMware Workstation

> **Jean-Pierre Gallego Santillan** · Apprenti informaticien CFC · Classe E1A · Septembre 2026

Rapport de formation : procédure complète, de la récupération de l'image ISO jusqu'au premier démarrage du bureau.

Ce document décrit, étape par étape, la procédure suivie pour installer Windows 11 dans une machine virtuelle à l'aide de VMware Workstation Pro. La procédure est découpée en cinq parties : la récupération de l'image ISO, la création de la machine virtuelle, la personnalisation du matériel, l'installation de Windows 11, puis la configuration initiale du système et la connexion au compte Microsoft.

## Sommaire

- [Partie 1 — Récupération de l'image ISO de Windows 11](#partie-1--récupération-de-limage-iso-de-windows-11)
- [Partie 2 — Création de la machine virtuelle sous VMware Workstation](#partie-2--création-de-la-machine-virtuelle-sous-vmware-workstation)
- [Partie 3 — Personnalisation du matériel virtuel](#partie-3--personnalisation-du-matériel-virtuel)
- [Partie 4 — Démarrage de la machine virtuelle et installation de Windows 11](#partie-4--démarrage-de-la-machine-virtuelle-et-installation-de-windows-11)
- [Partie 5 — Configuration initiale (OOBE) et compte Microsoft](#partie-5--configuration-initiale-oobe-et-compte-microsoft)


---

## Partie 1 — Récupération de l'image ISO de Windows 11

### Étape 1 : téléchargement du fichier ISO

Le fichier ISO d'installation de Windows 11 a été transmis par transfert de fichiers sécurisé (SwissTransfer). La page reçue permet de télécharger l'archive contenant l'image disque nécessaire à l'installation.

![Étape 1 - Téléchargement du fichier ISO](images/01.png)
*Page de réception du fichier ISO envoyé par transfert sécurisé (adresse de l'expéditeur floutée).*

---

## Partie 2 — Création de la machine virtuelle sous VMware Workstation

### Étape 2 : création d'une nouvelle machine virtuelle

Dans VMware Workstation, l'assistant de création est lancé en cliquant sur **« Create a New Virtual Machine »** depuis l'écran d'accueil.

![Étape 2 - Création d'une nouvelle VM](images/02.png)

### Étape 3 : choix du type de configuration

L'assistant propose deux modes : **« Typical (recommended) »**, qui crée la machine virtuelle en quelques étapes simples, et **« Custom (advanced) »**, réservé à des besoins spécifiques (contrôleur SCSI, compatibilité avec d'anciennes versions, etc.). Le mode Typical est sélectionné, car il est suffisant pour cette installation.

![Étape 3 - Choix du mode de configuration](images/03.png)

### Étape 4 : sélection de l'image ISO

Le fichier ISO téléchargé à l'étape 1 est sélectionné comme disque d'installation de la machine virtuelle.

![Étape 4 - Sélection de l'ISO](images/04.png)

### Étape 5 : sélection du système d'exploitation invité

Le système d'exploitation invité est défini sur **« Microsoft Windows »**, avec la version **« Windows 11 x64 »**.

![Étape 5 - Système d'exploitation invité](images/05.png)

### Étape 6 : nom de la machine et emplacement de stockage

Un nom est attribué à la machine virtuelle, et l'emplacement où seront stockés ses fichiers sur le disque est choisi.

![Étape 6 - Nom et emplacement](images/06.png)

### Étape 7 : mot de passe de chiffrement

Windows 11 nécessitant un module de plateforme sécurisée (TPM), VMware Workstation demande de définir un mot de passe de chiffrement pour protéger les fichiers liés au TPM virtuel. Un mot de passe est donc défini à cette étape (il n'est pas indiqué dans la version publique).

![Étape 7 - Mot de passe de chiffrement](images/07.png)

### Étape 8 : capacité du disque virtuel

La taille recommandée pour Windows 11 x64 est de 64 Go. Compte tenu de l'espace disponible sur le disque C de la machine hôte, la capacité a été réduite à **50 Go**.

![Étape 8 - Capacité du disque](images/08.png)

### Étape 9 : récapitulatif avant création

Un écran récapitule la configuration retenue (nom, emplacement, version, disque, mémoire, réseau, périphériques). Le bouton **« Customize Hardware »** permet d'ajuster le matériel avant de finaliser la création avec **« Finish »**.

![Étape 9 - Récapitulatif avant création](images/09.png)

---

## Partie 3 — Personnalisation du matériel virtuel

### Étape 10 : ajustement du matériel

La fenêtre **« Hardware »** permet de personnaliser les ressources allouées à la machine virtuelle : quantité de mémoire vive, nombre de processeurs et de cœurs par processeur, lecteur CD/DVD, carte réseau, contrôleur USB et carte son.

![Étape 10a - Fenêtre Hardware, processeurs](images/10.png)
![Étape 10b - Fenêtre Hardware, mémoire](images/11.png)
![Étape 10c - Fenêtre Hardware, lecteur CD/DVD](images/12.png)

---

## Partie 4 — Démarrage de la machine virtuelle et installation de Windows 11

### Étape 11 : premier démarrage sur le lecteur CD/DVD

Au premier démarrage, la machine virtuelle affiche le message **« Press any key to boot from CD or DVD »** : une touche doit être pressée rapidement pour démarrer sur l'image ISO plutôt que sur le disque dur, encore vide.

![Étape 11 - Premier démarrage](images/13.png)

### Étape 12 : paramètres de langue

L'installateur de Windows 11 démarre et demande de sélectionner la langue à installer ainsi que le format de l'heure et de la devise. Le français (France) est choisi pour les deux paramètres.

![Étape 12 - Paramètres de langue](images/14.png)

### Étape 13 : lancement de l'installation

L'option **« Installer Windows 11 »** est sélectionnée pour démarrer l'installation du système.

![Étape 13 - Sélection de l'option d'installation](images/15.png)

### Étape 14 : clé de produit

Aucune clé de produit n'étant disponible pour cette formation, l'installation est poursuivie via le lien **« Je n'ai pas de clé de produit »**.

![Étape 14 - Clé de produit](images/16.png)

### Étape 15 : choix de l'édition de Windows 11

Parmi les éditions proposées (Famille, Éducation, Professionnel, etc.), c'est **« Windows 11 Professionnel »** qui est sélectionnée.

![Étape 15 - Choix de l'édition](images/17.png)

### Étape 16 : emplacement d'installation

L'espace disque non alloué de 64 Go créé précédemment est sélectionné comme emplacement d'installation de Windows 11.

![Étape 16 - Emplacement d'installation](images/18.png)

### Étape 17 : lancement effectif de l'installation

L'écran **« Prêt pour l'installation »** résume les choix effectués (édition Windows 11 Professionnel, aucune donnée conservée). Après confirmation avec le bouton **« Installer »**, la copie et la configuration des fichiers système démarrent, avec un pourcentage de progression affiché à l'écran.

![Étape 17a - Prêt pour l'installation](images/19.png)
![Étape 17b - Installation en cours](images/20.png)

---

## Partie 5 — Configuration initiale (OOBE) et compte Microsoft

### Étape 18 : lancement de l'assistant de configuration

Une fois l'installation terminée et la machine redémarrée, l'assistant de configuration initiale de Windows (OOBE) démarre et demande de confirmer le pays ou la région.

![Étape 18 - Assistant de configuration](images/21.png)

### Étape 19 : nom de l'appareil

Un nom est attribué à l'appareil ; les étapes suivantes de l'assistant (réseau, compte, préférences de confidentialité) s'enchaînent ensuite normalement.

![Étape 19 - Nom de l'appareil](images/22.png)

### Étape 20 : contournement de la connexion réseau obligatoire

Pour accélérer la configuration, l'étape de connexion réseau obligatoire est contournée à l'aide du raccourci clavier **SHIFT + F10**, qui ouvre une invite de commandes, dans laquelle la commande **`OOBE\BYPASSNRO`** est saisie. La machine redémarre alors sur une configuration allégée qui permet de poursuivre sans connexion réseau.

![Étape 20a - Écran avant contournement](images/23.png)
![Étape 20b - Invite de commandes, OOBE\BYPASSNRO](images/24.png)

### Étape 21 : connexion au compte Microsoft

L'assistant propose ensuite de se connecter avec un compte Microsoft (ou d'en créer un), afin de synchroniser les paramètres et d'accéder aux services Microsoft.

![Étape 21 - Connexion au compte Microsoft](images/25.png)

### Étape 22 : arrivée sur le bureau

Une fois la configuration terminée, le bureau de Windows 11 s'affiche : l'installation de la machine virtuelle est achevée et le système est prêt à être utilisé.

![Étape 22 - Bureau Windows 11](images/26.png)

---

**[⬅ Retour aux projets](../README.md)** · [Mon profil](https://jp-gallego.github.io) · [LinkedIn](https://www.linkedin.com/in/jean-pierre-gallego-santillan-6b4701433)
