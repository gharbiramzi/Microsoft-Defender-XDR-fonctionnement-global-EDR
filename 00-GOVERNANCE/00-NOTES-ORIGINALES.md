# 00 — Notes originales

> **Nature du document :** transcription et consolidation des notes de travail initiales.  
> **Objectif :** préserver les éléments fournis avant leur analyse et leur enrichissement technique.  
> **Statut :** notes non validées techniquement.

## Règle de conservation

Ce document conserve les formulations, termes, listes et chemins d’interface tels qu’ils ont été consignés dans les notes de départ, dans la mesure où ils sont disponibles. Il ne constitue pas une procédure validée ni une référence de configuration à appliquer directement en production.

Les chemins de menus, libellés, modes et affirmations peuvent varier selon l’évolution des portails, les licences, le tenant ou la version des produits. Ils ne sont pas corrigés silencieusement ici. Les vérifications, corrections et mises à jour doivent être consignées dans des documents techniques distincts.

---

## 1. Manage access

- Limit access to related alert and data to specific Entra ID user groups with assigned RBAC access.
- Configure specific remediation levels to apply during automated investigations for different sets of devices.

### UI notations

- `Microsoft Defender > Setting > XDR > role > Security operations`
- `Microsoft Defender > Setting > Endpoint > Device Group`
- Assignation : MS Entra Group

### Remediation levels

- Full - remediate threats automatically
- Semi - require approval for any remediation
- Semi - require approval for core folders remediation
- Semi - require approval for non-temp folders remediation
- No automated response

---

## 2. Microsoft Defender > Setting > Endpoint

- Configure and manage automation.
- Configure advanced features.
- Manage automation upload and folder settings :
  - file content analysis
  - memory content analysis
  - automation folder exclusions (folders, extensions, file names)
- Manage alert tuning.
- Manage indicators :
  - files
  - IP addresses
  - URLs/domains
  - certificates

---

## 3. Microsoft Defender Endpoints – Vulnerability Management

Éléments de navigation et rubriques relevés :

- Dashboard
- Recommendations
- Remediation
- Inventories
- Weaknesses
- Event timeline
- Baselines Assessment
- Partners and APIs

---

## 4. Threat Intelligence / Defender for Cloud

### Rapports de renseignement

Informations à rechercher ou à présenter dans les rapports :

- groupes d’activités ;
- campagnes ;
- résumé des menaces ;
- objectifs des attaquants ;
- tactiques, outils et procédures ;
- identité ou affiliations si disponibles ;
- campagnes passées et actuelles ;
- IoC (URL/hash) ;
- victimologie (secteur/géographie) ;
- atténuation et remédiation.

### Alertes Defender for Cloud

Répondre aux alertes relatives à :

- Defender for Key Vault ;
- DNS ;
- Resource Manager.

---

## 5. Architecture hardening

### Référentiels et niveaux

- CIS Level 1 comme point de départ général.
- CIS Level 2 pour postes sensibles.
- STIG lorsque justifié.

### Démarche

1. Évaluer l’existant.
2. Identifier les écarts.
3. Tester un groupe pilote.
4. Déployer via Intune/GPO.
5. Contrôler les écarts.
6. Documenter les exceptions.

### Notes complémentaires

- Defender Vulnerability Management peut aider à évaluer certains benchmarks.
- Intune peut auditer les STIG pris en charge.
- Évaluation de conformité et application effective des paramètres sont deux opérations distinctes.
- CIS Benchmark Windows n’est pas un inventaire exhaustif des GPO Windows.
- Group Policy Analytics : importer des rapports XML GPO, analyser la prise en charge Intune et préparer la migration vers Settings Catalog.

### Référence fournie

- https://www.systemcenterdudes.com/intune-security-baseline/

### Définitions

- **Vulnérabilité :** faiblesse exploitable par un attaquant.
- **Durcissement :** mesures préventives pour supprimer/réduire les faiblesses de configuration.
- **Conformité :** vérification des configurations contre un référentiel/politique.

---

## 6. Block at risk devices with Microsoft Endpoint Manager

Étapes relevées :

1. Turn on Intune connection from Defender XDR portal.
2. Turn on Defender for Endpoint integration in Intune admin center.
3. Create compliance policy in Intune.
4. Assign policy.
5. Create Entra ID Conditional Access policy.

---

## 7. Attack Surface

### Capacités et domaines cités

- ASR
- hardware-based isolation
- Web protection
- Windows Defender Firewall
- Application control
- Controlled folder access
- Exploit protection
- Removable storage protection
- Network protection

### ASR rules dans Intune

Chemin noté :

`Endpoint Security > Manage > Attack surface reduction > Create Policy > Windows > profile`

La note d’origine mentionne le profil « Microsoft Defender Antivirus » ; le chemin et le profil exacts sont à vérifier selon l’interface et le scénario.

### Modes

- Not configured
- Off (0)
- Block (1)
- Audit (2)
- Warn (6)

### Exemples de règles / comportements

- bloquer les scripts obfusqués ;
- bloquer les processus enfants Office ;
- bloquer l’utilisation de Win32 API depuis les macros Office ;
- bloquer les exécutables non fiables ;
- bloquer les comportements suspects.

---

## 8. Defender Vulnerability Management

### Capacités et intégrations relevées

- Corrélation EDR avec les vulnérabilités.
- Contexte de vulnérabilité lors des enquêtes.
- Correction via Intune et Configuration Manager.

### Request Remediation

Types d’actions relevés :

- Software update
- Software Uninstall
- Attention required

### Task management tools

- Open a ticket in Intune (for AAD joined devices).

### Informations de suivi

- Date de remédiation.
- Priorité.
- Note.

### Exception options

- Third party control
- Alternate mitigation
- Risk accepted
- Planned remediation (Grace)
- Durée d’exception.

---

## Historique et statut

| Élément | Valeur |
|---|---|
| Type | Notes de travail originales |
| Validation technique | Non effectuée dans ce document |
| Corrections | Aucune correction silencieuse |
| Utilisation | Source de départ pour les analyses et documents techniques détaillés |

## Suite documentaire

Les analyses, vérifications de disponibilité, prérequis, licences, chemins de configuration actualisés, permissions, commandes, limites produit et recommandations BUILD/RUN doivent être traités dans des documents dédiés. Toute divergence avec les notes originales doit être explicitement signalée et accompagnée d’une référence lorsque disponible.
