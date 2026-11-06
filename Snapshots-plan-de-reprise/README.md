# Snapshots et plan de reprise d'un serveur critique

> **Jean-Pierre Gallego Santillan** · Apprenti informaticien CFC (1re année) · Octobre 2026

**Mots-clés :** `VMware Workstation` `Snapshots` `Plan de reprise` `RTO / RPO` `IIS` `Windows`

> [!NOTE]
> **En bref** : SRV-APP est une VM Windows qui héberge l'application interne d'une PME (une page web publiée par IIS). J'ai pris un snapshot propre, simulé un incident qui casse l'application, puis restauré la VM en chronométrant. **L'application était de nouveau en ligne en environ 3 minutes.** Pour finir, j'ai activé les snapshots automatiques et rédigé un plan de reprise avec des objectifs RTO et RPO.

![Le snapshot de l'état d'origine dans VMware Workstation](https://hackmd.io/_uploads/BJ2-McMifx.png)
*Le snapshot de l'état d'origine, disponible dans le menu Snapshot de VMware Workstation.*

## Ce que ce projet montre

- **Créer des snapshots propres**, numérotés, datés et décrits, à froid ou à chaud.
- **Simuler un vrai incident** : suppression du fichier de l'application dans le dossier d'IIS.
- **Restaurer et mesurer** le temps de reprise, plutôt que de le deviner.
- **Automatiser** avec AutoProtect (un snapshot par jour).
- **Rédiger un plan de reprise** avec des objectifs chiffrés.

## Objectifs de reprise

| Indicateur | Objectif fixé | Résultat |
|---|---|---|
| RTO (temps maximum pour remettre en service) | 15 minutes | Environ 3 minutes mesurées → objectif atteint |
| RPO (perte de données maximum) | 24 heures | AutoProtect crée un snapshot par jour |
| RPO avant une mise à jour | 0 | Un snapshot manuel juste avant chaque mise à jour |

## Outils

VMware Workstation Pro 17 · Windows · IIS · Snapshot Manager · AutoProtect

## Rapport complet

Toutes les étapes, l'incident et la restauration en captures d'écran : **[voir le rapport complet sur HackMD](https://hackmd.io/@jpgallego/Sy8hWcfifl)**

---

[← Retour à mes projets](../README.md)
