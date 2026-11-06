# Réseau d'une PME sur deux sites : Genève et Lausanne

> **Jean-Pierre Gallego Santillan** · Apprenti informaticien CFC (1re année) · Octobre 2026

**Mots-clés :** `Conception réseau` `Plan d'adressage` `VLAN` `Trunk 802.1Q` `Routage inter-VLAN` `Routage statique` `GNS3`

> [!NOTE]
> **En bref** : un travail de conception pour une PME fictive, AlpTech Services SA, avec un siège à Genève et une agence à Lausanne. Je suis parti des besoins de l'entreprise pour construire le schéma, le plan d'adressage, les VLAN et la liaison entre les deux sites, en justifiant chaque choix. La maquette tourne dans GNS3 : 2 routeurs, 2 switchs et 6 PC, avec les VLAN configurés sur les switchs.

![Schéma d'architecture avec VLAN et adresses IP](https://hackmd.io/_uploads/Bk1C0WAiGg.png)
*Le schéma d'architecture complet, avec les VLAN et les adresses IP de chaque site.*

## Ce que ce projet montre

- **Partir des besoins** avant de choisir les adresses : qui doit accéder à quoi, combien de postes, quel serveur.
- **Un plan d'adressage lisible** : 192.168.X.0/24, où X est le numéro du VLAN, et un /30 pour la liaison entre les sites.
- **Séparer les postes et le serveur avec des VLAN**, et faire passer plusieurs VLAN sur un seul câble grâce à un trunk 802.1Q.
- **Comparer deux façons de relier les sites** (ligne dédiée ou VPN) et choisir en connaissance de cause.

## Récapitulatif des choix techniques

| Domaine | Choix | Pourquoi |
|---|---|---|
| Architecture | 1 routeur + 1 switch par site | Chaque site est autonome |
| Adressage | 192.168.X.0/24, X = VLAN | Facile à lire, place pour grandir |
| Liaison | 192.168.255.0/30 | Seulement 2 adresses nécessaires |
| VLAN | VLAN 10 et 20 à Genève, VLAN 30 à Lausanne | Séparer les postes du serveur |
| Lien switch–routeur à Genève | Trunk 802.1Q + sous-interfaces | Faire passer 2 VLAN sur un seul câble |
| Interconnexion | Ligne dédiée simulée | Simple, privée, compatible avec un futur VPN |
| Routage | Routes statiques | Seulement 2 sites : pas besoin de routage dynamique |

## Outils

GNS3 2.2.61 · routeurs Cisco · switchs Ethernet · postes VPCS

## Rapport complet

Les besoins, le schéma annoté, le plan d'adressage détaillé et la configuration des switchs : **[voir le rapport complet sur HackMD](https://hackmd.io/@jpgallego/SJ8FAbAjfl)**

---

[← Retour à mes projets](../README.md)
