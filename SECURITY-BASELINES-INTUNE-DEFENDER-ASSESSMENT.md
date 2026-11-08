# Microsoft Intune et Microsoft Defender — Baselines et benchmarks de sécurité

> **Type :** Référence d'architecture Endpoint Security  
> **Périmètre :** Microsoft Intune, Microsoft Defender for Endpoint (MDE) et Microsoft Defender Vulnerability Management (MDVM)  
> **Date de rédaction :** 8 novembre 2026  
> **Statut :** Document de référence. Vérifier les versions, licences et fonctionnalités disponibles dans le tenant avant déploiement.

## 1. Objectif

Ce document explique les deux consoles présentées dans la capture de référence :

- **Microsoft Intune Admin Center** : configuration, affectation et déploiement des politiques de sécurité sur les terminaux.
- **Microsoft Defender portal – Security baselines assessment** : évaluation de la configuration des appareils par rapport à des benchmarks pris en charge.

Ces fonctions sont complémentaires, mais ne remplissent pas le même rôle. **Intune configure et déploie ; Security baselines assessment évalue et mesure.**

## 2. Lecture de la capture

### 2.1 Microsoft Intune Admin Center

URL : https://intune.microsoft.com

Chemin principal : `Endpoint security`

| Entrée visible | Périmètre fonctionnel |
|---|---|
| Microsoft Defender for Endpoint (Setup) | Configuration de l'intégration entre Intune et Defender for Endpoint. |
| Endpoint detection and response | Politiques EDR et paramètres d'intégration/onboarding pris en charge. |
| Antivirus | Configuration de Microsoft Defender Antivirus et des paramètres antimalware. |
| Firewall | Configuration de Microsoft Defender Firewall. |
| Attack surface reduction | Règles ASR et paramètres associés à la réduction de la surface d'attaque. |
| Account protection | Paramètres de protection des comptes et mécanismes d'authentification pris en charge. |
| Device compliance | Règles d'évaluation de conformité des appareils ; les signaux de conformité peuvent être utilisés par Conditional Access. |
| Conditional access | Accès conditionnel, en association avec Microsoft Entra ID. |
| Disk encryption | Paramètres de chiffrement, notamment BitLocker sur Windows. |
| Security baselines | Profils de paramètres de sécurité recommandés et déployables depuis Intune. |

**Attention :** Antivirus, Firewall, EDR, ASR, Account protection et Device compliance sont des catégories de politiques Endpoint security. Elles ne sont pas toutes des « Security Baselines ».

Documentation :
- [Intune Endpoint security](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security)
- [Intune security baselines overview](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview)

### 2.2 Microsoft Defender portal — Security baselines assessment

Chemin présenté dans la capture :

`Endpoints` → `Vulnerability management` → `Baselines assessment` → onglet `Profiles`

| Élément de l'interface | Signification |
|---|---|
| Overview | Vue de synthèse des évaluations. |
| Profiles | Profils d'évaluation créés dans Defender. |
| Settings | Paramètres de la fonctionnalité. |
| Active profiles | Nombre de profils d'évaluation actifs. |
| Configurations passed | Nombre de contrôles évalués comme conformes. |
| Devices compliant | Indicateur des appareils conformes selon les profils. |
| Create | Création d'un profil d'évaluation. |
| Export | Export des résultats disponibles. |
| Benchmark | Référentiel sélectionné pour le profil. |
| Benchmark version | Version du référentiel évalué. |

La capture montre des compteurs vides (`-`) et aucune ligne de profil. Elle ne permet donc pas de déterminer quel benchmark est activé dans le tenant.

Documentation : [Security baselines assessment – Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-baselines)

## 3. Benchmarks utilisables

La documentation Microsoft de Security baselines assessment décrit la prise en charge des référentiels suivants. La disponibilité précise dépend du système d'exploitation, de la version et des choix proposés dans l'assistant de création du profil.

| Référentiel | Périmètre OS indiqué dans la documentation | Utilisation |
|---|---|---|
| CIS Benchmarks | Windows 10, Windows 11 et Windows Server 2008 R2 et versions ultérieures | Évaluer les paramètres système par rapport aux recommandations CIS. |
| DISA STIG | Windows 10 et Windows Server 2019 | Évaluer la configuration par rapport aux exigences de durcissement STIG. |

### 3.1 CIS Benchmarks

Le Center for Internet Security (CIS) publie des recommandations de configuration sécurisée, organisées par produit, version et niveau.

- **Level 1** : durcissement généralement destiné à préserver l'usage courant du système.
- **Level 2** : durcissement plus strict, susceptible d'avoir des impacts applicatifs et opérationnels.

Ne pas supposer que tous les niveaux, systèmes ou versions CIS sont proposés dans chaque profil Defender. Vérifier le sélecteur `Benchmark` et `Benchmark version` du tenant.

Référence : [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks)

### 3.2 DISA STIG

Les Security Technical Implementation Guides (STIG) sont des guides de configuration de sécurité publiés par la Defense Information Systems Agency (DISA). Ils sont utilisés dans des environnements soumis à des exigences de durcissement strictes.

Référence : [DISA STIGs](https://www.cyber.mil/stigs/)

### 3.3 NIST, ISO 27001 et ANSSI

NIST CSF, NIST SP 800-53, ISO/IEC 27001 et les recommandations ANSSI sont des référentiels de gouvernance, de contrôle ou de conformité. Ne pas les présenter comme des benchmarks directement sélectionnables dans Security baselines assessment sans preuve dans la documentation et dans le tenant.

Ils peuvent être utilisés pour établir une correspondance (mapping) entre les contrôles techniques évalués et les exigences de l'organisation. Ce mapping est un travail distinct de l'évaluation native.

### 3.4 Benchmarks Microsoft

Ne pas annoncer la disponibilité d'un benchmark Microsoft dans cette fonctionnalité sans vérifier sa présence effective dans le sélecteur `Benchmark` et dans la documentation Microsoft correspondant à la version du service. Les référentiels explicitement décrits dans la documentation de la fonctionnalité doivent rester la référence.

## 4. Différence entre les deux consoles

| Critère | Microsoft Intune | Defender Security baselines assessment |
|---|---|---|
| Rôle | Configurer et déployer | Évaluer et mesurer |
| Nature | Gestion de configuration MDM | Évaluation de posture par benchmark |
| Action sur le poste | Applique des paramètres via les mécanismes de gestion pris en charge | Compare les paramètres observés aux valeurs attendues |
| Référentiels | Baselines Microsoft Intune et politiques Endpoint security | Benchmarks pris en charge, notamment CIS et STIG |
| Affectation | Groupes, filtres et affectations Intune | Périmètre d'appareils du profil d'évaluation |
| Résultat | État de déploiement et de configuration des politiques | Conformité par appareil et par configuration |
| Remédiation | Modification de la politique ou action de gestion | Correction via l'outil de configuration approprié |

### 4.1 Schéma fonctionnel

```text
             PLAN DE CONFIGURATION
                       |
                Microsoft Intune
                       |
       +---------------+----------------+
       |               |                |
  Security        Endpoint security   Configuration
  Baselines          Policies           Profiles
       |               |                |
       +---------------+----------------+
                       |
                 Windows devices
                       |
             Paramètres réellement appliqués
                       |
                       v
               PLAN D'ÉVALUATION
                       |
          Microsoft Defender portal
                       |
          Vulnerability management
                       |
              Baselines assessment
                       |
               Profils CIS / STIG
                       |
           Résultats et écarts détectés
                       |
           Analyse et remédiation via
            Intune / GPO / outil adapté
```

**Point de vigilance majeur :** Microsoft documente actuellement pour cette évaluation la prise en charge des configurations **Group Policy Object (GPO)**, et non des configurations Microsoft Intune / Configuration Manager. Il ne faut donc pas supposer que les paramètres déployés par Intune seront automatiquement évalués comme une configuration prise en charge par cette fonctionnalité. Vérifier les limitations et évolutions de la documentation avant de concevoir le dispositif.

## 5. Prérequis et limites de Security baselines assessment

Vérifier les points suivants avant activation :

1. **Licence** : selon le scénario de souscription, Microsoft Defender Vulnerability Management Standalone ou Microsoft Defender for Endpoint Plan 2 avec l'option/add-on Defender Vulnerability Management appropriée.
2. **Systèmes d'exploitation** : vérifier la matrice OS/version pour le benchmark sélectionné.
3. **Source de configuration** : la documentation de la fonctionnalité indique la prise en charge des configurations GPO ; ne pas présumer une prise en charge Intune.
4. **Langue du système** : la documentation mentionne une limitation concernant les systèmes Windows dont la langue système n'est pas l'anglais.
5. **PowerShell** : le Constrained Language Mode doit être désactivé pour que l'évaluation fonctionne correctement.
6. **WDAC** : si des politiques WDAC sont utilisées, prévoir les règles d'autorisation nécessaires à l'exécution des scripts MDE en FullLanguage.
7. **Contrôles manuels** : certains paramètres peuvent nécessiter une vérification manuelle et ne sont pas évalués automatiquement.
8. **Problèmes connus** : vérifier les limitations et problèmes connus de la documentation Microsoft avant d'utiliser les résultats comme preuve d'audit.

Ces prérequis concernent la fonctionnalité Security baselines assessment et ne doivent pas être généralisés à toutes les fonctions Intune ou MDE.

## 6. Workflow de création d'un profil Defender

Chemin : `Vulnerability management` → `Baselines assessment` → `Profiles` → `Create`

Workflow de haut niveau :

1. Définir le nom et la description du profil.
2. Définir le système/logiciel, le benchmark et la version proposés.
3. Sélectionner les configurations à inclure.
4. Examiner les contrôles nécessitant une validation manuelle.
5. Créer le profil.
6. Analyser les résultats par configuration et par appareil.
7. Exporter les résultats si nécessaire.
8. Traiter les écarts via le mécanisme de configuration autorisé.

Les vues de résultats peuvent présenter l'état de conformité, la valeur attendue, la source de la valeur actuelle, les appareils concernés et les contrôles en échec. Vérifier les champs effectivement exposés dans le tenant.

### Gestion des exceptions

Toute exception doit être :
- limitée au contrôle et aux appareils concernés ;
- justifiée par un besoin métier ou une contrainte technique ;
- approuvée par le responsable désigné ;
- associée à des mesures compensatoires ;
- dotée d'une date d'expiration et d'une revue périodique.

## 7. Advanced Hunting et reporting

Les tables documentées pour l'analyse des évaluations comprennent :

| Table | Usage |
|---|---|
| `DeviceBaselineComplianceProfiles` | Informations sur les profils d'évaluation. |
| `DeviceBaselineComplianceAssessment` | Informations relatives à l'évaluation de conformité des appareils. |
| `DeviceBaselineComplianceAssessmentKB` | Informations de référence sur les paramètres des benchmarks CIS/STIG. |

Vérifier le schéma et la disponibilité des tables dans Advanced Hunting du tenant avant d'industrialiser une requête KQL. Ne pas construire un reporting de production sur des colonnes supposées.

## 8. Démarche BUILD / RUN

### BUILD

1. Inventorier les OS, versions, populations et sources de configuration (Intune, GPO, Configuration Manager, scripts).
2. Identifier le benchmark pertinent pour chaque population et exigence.
3. Vérifier les licences et prérequis de collecte.
4. Créer un profil pilote sur un périmètre maîtrisé.
5. Analyser les écarts et les contrôles manuels.
6. Mapper chaque écart vers le mécanisme de remédiation autorisé : Intune, GPO, script contrôlé ou autre outil.
7. Tester les corrections sur un groupe pilote.
8. Formaliser les exceptions, compensations, propriétaires et dates de révision.

### RUN

- Surveiller les profils actifs et les tendances de conformité.
- Suivre les appareils et contrôles les plus fréquemment en échec.
- Vérifier les changements de version des benchmarks.
- Contrôler les erreurs de collecte et les contrôles manuels.
- Réexaminer les exceptions à échéance.
- Produire un reporting par population, entité, OS et criticité.
- Assurer la traçabilité entre écart, ticket, changement, validation et résultat après remédiation.

### KPI proposés

| KPI | Calcul / lecture |
|---|---|
| Taux de conformité appareils | Appareils conformes / appareils évalués × 100 |
| Taux de conformité des contrôles | Contrôles réussis / contrôles automatiquement évalués × 100 |
| Nombre d'écarts prioritaires | Nombre de contrôles prioritaires en échec |
| Taux d'exceptions | Exceptions actives / contrôles applicables |
| Délai moyen de remédiation | Temps entre détection et conformité constatée |
| Couverture d'évaluation | Appareils évalués / appareils dans le périmètre cible × 100 |

Les seuils doivent être définis avec le RSSI et les métiers ; ne pas présenter un seuil arbitraire comme une exigence Microsoft.

## 9. Décisions d'architecture et pièges à éviter

- Ne pas confondre `Intune > Endpoint security > Security baselines` avec `Defender > Vulnerability management > Baselines assessment`.
- Ne pas confondre les politiques Antivirus, Firewall, ASR, EDR et Device compliance avec les profils d'évaluation de benchmark.
- Ne pas considérer que Security baselines assessment déploie les paramètres : sa fonction est l'évaluation.
- Ne pas supposer que l'évaluation CIS/STIG valide automatiquement les paramètres déployés par Intune.
- Ne pas déclarer une conformité CIS, STIG, NIST ou ISO sur la seule base du déploiement d'une baseline Microsoft.
- Versionner les profils, documenter les adaptations et conserver les preuves de remédiation.

## 10. Documentation officielle

1. [Microsoft Learn — Security baselines assessment (Defender Vulnerability Management)](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-baselines)
2. [Microsoft Learn — Defender Vulnerability Management FAQ](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-faq)
3. [Microsoft Learn — Intune security baselines overview](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview)
4. [Microsoft Learn — Configure security baseline policies in Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/security-baselines-configure)
5. [CIS — CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks)
6. [DISA — STIGs](https://www.cyber.mil/stigs/)

## 11. Synthèse exécutive

**Intune configure et déploie. Defender Security Baselines Assessment mesure et évalue.**

Intune constitue le plan de contrôle de configuration des terminaux gérés : il distribue les paramètres au moyen des Security Baselines, des politiques Endpoint security et des profils de configuration.

Microsoft Defender Vulnerability Management Security Baselines Assessment évalue la configuration par rapport aux benchmarks pris en charge, notamment CIS et STIG. Les écarts doivent être analysés puis corrigés par le mécanisme de configuration approprié. La limitation documentée concernant la prise en charge GPO, et non Intune, doit être prise en compte dans l'architecture cible.
