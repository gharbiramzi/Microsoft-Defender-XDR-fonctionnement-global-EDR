# Microsoft Cybersecurity Architect – Knowledge Base

> Bibliothèque technique dédiée à l’architecture, à l’intégration, à la sécurisation et à l’exploitation des solutions Microsoft Security.

**Statut :** En cours de construction  
**Dernière mise à jour :** 08/11/2026

## 1. Objectifs

Cette base documentaire centralise les architectures, procédures de configuration, contrôles de sécurité, scénarios BUILD/RUN et références Microsoft Learn utiles aux environnements Microsoft Cloud, hybrides et On-Premises.

Les documents distinguent :
- les notes et éléments de référence d’origine ;
- les compléments et analyses techniques ;
- les corrections et points nécessitant une validation dans le tenant.

## 2. Index de la bibliothèque

| Domaine | Répertoire | Contenu attendu |
|---|---|---|
| Gouvernance documentaire | `00-GOVERNANCE/` | Notes originales, conventions, décisions et historique |
| Defender XDR | `01-DEFENDER-XDR/` | Architecture XDR, incidents, corrélation, investigation, Advanced Hunting, Action Center et RBAC |
| Defender for Endpoint | `02-DEFENDER-ENDPOINT/` | Onboarding, antivirus, EDR, ASR, Firewall, Device Control, Vulnerability Management et réponse |
| Defender for Identity | `03-DEFENDER-IDENTITY/` | Architecture MDI, capteurs DC/Standalone, AD DS, flux, santé et troubleshooting |
| Microsoft Sentinel | `04-MICROSOFT-SENTINEL/` | Workspace, connecteurs, ingestion, AMA/DCR, KQL, ASIM, UEBA, Analytics Rules, SOAR et Workbooks |
| Defender for Office 365 | `05-DEFENDER-OFFICE365/` | Exchange Online, Teams, anti-phishing, Safe Links, Safe Attachments et gouvernance RUN |
| Defender for Cloud Apps | `06-DEFENDER-CLOUD-APPS/` | CASB, Cloud Discovery, App Governance, politiques et intégrations |
| Defender for Cloud | `07-DEFENDER-CLOUD/` | CSPM, CWPP, recommandations, posture cloud, alertes et conformité |
| Transverse | `08-TRANSVERSE/` | Zero Trust, RBAC, automatisation, PowerShell, Microsoft Graph, API, reporting et RACI |

## 3. Méthodologie BUILD

Les dossiers techniques suivent, selon le périmètre, le cycle suivant :

1. **ANALYSER** — étudier l’existant, les composants, versions, flux, dépendances, licences, rôles et risques.
2. **CONCEVOIR** — définir l’architecture cible, les composants, les flux, les politiques et les responsabilités.
3. **CHALLENGER** — identifier les écarts, limites, risques, dépendances et alternatives.
4. **INTÉGRER** — configurer les solutions, connecteurs, permissions et mécanismes de sécurité.
5. **INDUSTRIALISER** — automatiser, standardiser et produire les scripts et contrôles.
6. **EXPLOITER** — formaliser la supervision, le traitement des alertes, les incidents et les changements.
7. **AMÉLIORER** — mesurer les résultats, traiter les écarts et maintenir une roadmap.

## 4. Structure standard d’un document technique

Selon le sujet, chaque document doit couvrir :

- Métadonnées, version, date et statut ;
- Synthèse et objectifs ;
- Contexte, périmètre et hypothèses ;
- Architecture logique et composants ;
- Flux réseau et dépendances ;
- Prérequis et licences ;
- RBAC, permissions et moindre privilège ;
- Configuration dans les portails Microsoft ;
- PowerShell, Microsoft Graph ou REST API lorsque pertinent ;
- Contrôles de validation et résultats attendus ;
- Tests fonctionnels, sécurité et non-régression ;
- Exploitation RUN, supervision et troubleshooting ;
- Risques, limites, rollback et recommandations ;
- Références Microsoft Learn et historique des modifications.

## 5. Conventions documentaires

- **OBLIGATOIRE** : exigence nécessaire à la sécurité ou au fonctionnement.
- **RECOMMANDÉ** : bonne pratique d’architecture ou d’exploitation.
- **À VALIDER** : élément dépendant du tenant, des licences, de la version ou du contexte client.
- **BUILD** : conception, intégration, déploiement et recette.
- **RUN** : supervision, administration, incidents, changements et amélioration.
- **PREVIEW** : fonctionnalité en préversion, à distinguer de la disponibilité générale (GA).

Les notes d’origine ne sont pas corrigées silencieusement. Les évolutions de produit, corrections et compléments doivent être explicitement identifiés et sourcés.

## 6. Document déjà présent dans le dépôt

### Endpoint Security — Intune et Defender

- [Microsoft Intune et Microsoft Defender — Baselines et benchmarks de sécurité](SECURITY-BASELINES-INTUNE-DEFENDER-ASSESSMENT.md)  
  Distingue les baselines de configuration administrées dans Intune de la fonctionnalité Defender Security baselines assessment. Présente les benchmarks CIS/STIG, les prérequis, les limites, le workflow BUILD/RUN et les KPI.

## 7. Références officielles

- [Microsoft Learn — Microsoft Defender](https://learn.microsoft.com/en-us/defender/)
- [Microsoft Learn — Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/)
- [Microsoft Learn — Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/)
- [Microsoft Learn — Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/)
- [Microsoft Learn — Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/)
- [Microsoft Learn — Microsoft Intune](https://learn.microsoft.com/en-us/intune/)

---

*Ce document est un index de navigation et une convention de structuration. Il ne remplace pas les documentations techniques détaillées des composants.*