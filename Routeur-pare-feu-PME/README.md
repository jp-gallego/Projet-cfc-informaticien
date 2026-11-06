# Routeur et pare-feu pour une petite entreprise (NAT + ACL)

> **Jean-Pierre Gallego Santillan** · Apprenti informaticien CFC (1re année) · Octobre 2026

**Mots-clés :** `GNS3` `Cisco IOS` `NAT/PAT` `ACL` `Pare-feu` `Sécurité réseau`

> [!NOTE]
> **En bref** : une petite entreprise veut relier son réseau local à Internet de façon sécurisée. J'ai configuré un routeur Cisco qui partage l'accès Internet entre les postes grâce au NAT, et qui joue le rôle de pare-feu : il bloque le HTTP non chiffré et Telnet, et laisse passer le reste. Chaque règle est prouvée par des tests avant/après.

![Topologie finale dans GNS3](https://hackmd.io/_uploads/HkTFC5ooGx.png)
*La topologie finale : le routeur R1-FW entre le LAN de l'entreprise (2 postes) et Internet.*

## Ce que ce projet montre

- **Interfaces WAN et LAN** : la patte WAN reçoit son adresse en DHCP, la patte LAN sert de passerelle aux postes.
- **NAT avec overload (PAT)** : tous les postes sortent sur Internet avec une seule adresse.
- **Une ACL étendue nommée** (FW-LAN-OUT), commentée et appliquée dans le bon sens sur la bonne interface.
- **Prouver qu'une règle marche** : tests avant/après depuis les deux postes, puis compteurs de l'ACL sur le routeur.

## Les règles du pare-feu

| N° | Action | Protocole / port | Raison |
|---|---|---|---|
| 10 | Refuser | TCP 80 (HTTP) | HTTP non chiffré : les données circulent en clair |
| 20 | Refuser | TCP 23 (Telnet) | Telnet transmet les mots de passe en clair |
| 30 | Autoriser | IP (tout le reste) | Le reste du trafic du LAN reste permis |

## Résultat des tests

| Test | Avant pare-feu | Après pare-feu |
|---|---|---|
| Ping 8.8.8.8 (Internet) | OK | OK |
| TCP 443 (HTTPS) | OK | OK |
| TCP 80 (HTTP) | OK | **Bloqué** |

## Outils

GNS3 2.2.61 · routeur Cisco c7200 · switch · 2 postes VPCS · nœud Cloud (VMnet8) pour l'accès réel à Internet

## Rapport complet

Toutes les étapes, les commandes et les captures d'écran : **[voir le rapport complet sur HackMD](https://hackmd.io/@jpgallego/r1j4CqiiGl)**

---

[← Retour à mes projets](../README.md)
