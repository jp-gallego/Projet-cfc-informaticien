# Routage statique, NAT vers Internet et SSH : 3 routeurs Cisco sous GNS3

> **Jean-Pierre Gallego Santillan** · Apprenti informaticien CFC (1re année) · Octobre 2026

**Mots-clés :** `GNS3` `Cisco IOS` `Routage statique` `VLSM` `NAT/PAT` `SSH` `Wireshark` `VMware Workstation`

> [!NOTE]
> **En bref** : deux réseaux locaux reliés par trois routeurs Cisco, avec un routeur central qui sort sur Internet grâce au NAT. Les postes des deux LAN sont de vraies VM Windows sous VMware Workstation, branchées sur la maquette GNS3. Ensuite, j'ai sécurisé l'accès aux routeurs et comparé Telnet et SSH avec une capture Wireshark.

![Topologie finale dans GNS3](https://hackmd.io/_uploads/S1BkIG6qGg.png)
*La topologie finale dans GNS3 : PC1 et PC2 (VM Windows) de chaque côté, R3 au centre qui sort sur Internet.*

## Ce que ce projet montre

- **Découper un réseau en sous-réseaux (VLSM)** : un /26 pour LAN1 (50 hôtes), un /27 pour LAN2 (20 hôtes) et deux /30 pour les liens entre routeurs.
- **Routage statique** : toutes les routes écrites à la main, avec une route par défaut vers le routeur central.
- **NAT/PAT** sur R3, pour que les deux LAN partagent une seule adresse vers Internet.
- **Relier GNS3 et VMware Workstation** : réseaux VMnet ajoutés dans le Virtual Network Editor et nœuds Cloud dans GNS3.
- **Sécuriser l'accès aux routeurs** : Telnet, puis SSH. La capture Wireshark montre que Telnet envoie le mot de passe en clair, alors que SSH chiffre tout.

## Plan d'adressage

| Réseau | Lien | Masque | Plage utilisable |
| --- | --- | --- | --- |
| 192.168.10.0/26 | LAN1 – PC1 / R1 (50 hôtes) | 255.255.255.192 | .1 → .62 |
| 192.168.10.64/27 | LAN2 – PC2 / R2 (20 hôtes) | 255.255.255.224 | .65 → .94 |
| 192.168.11.0/30 | WAN1 – R1 / R3 | 255.255.255.252 | .1 → .2 |
| 192.168.11.4/30 | WAN2 – R3 / R2 | 255.255.255.252 | .5 → .6 |
| DHCP | R3 → Internet | auto | auto |

## Outils

GNS3 2.2.61 · routeurs Cisco c7200 (IOS 15.2) · VMware Workstation Pro 17 · Solar-PuTTY · Wireshark

## Rapport complet

Toutes les étapes, les configurations des routeurs et les captures d'écran : **[voir le rapport complet sur HackMD](https://hackmd.io/@jpgallego/B1vR2ZTcze)**

---

[← Retour à mes projets](../README.md)
