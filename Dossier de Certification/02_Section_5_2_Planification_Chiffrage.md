# SECTION 5.2 — PLANIFICATION ET CHIFFRAGE

---

## Work Breakdown Structure (WBS)

```
1. PROJET REFONTE PORTAIL B2B
│
├── 1.1 CADRAGE ET INITIALISATION (M+0)
│   ├── 1.1.1 Note de cadrage et gouvernance
│   ├── 1.1.2 Kick-off projet
│   ├── 1.1.3 Constitution de l'équipe
│   └── 1.1.4 Mise en place des outils (Jira, Git, CI/CD)
│
├── 1.2 RECUEIL ET ANALYSE DES BESOINS (M+0 → M+1)
│   ├── 1.2.1 Ateliers avec partenaires
│   ├── 1.2.2 Audit de l'existant
│   ├── 1.2.3 Spécifications fonctionnelles
│   └── 1.2.4 Spécifications techniques
│
├── 1.3 REFONTE FRONT-END (M+1 → M+3)
│   ├── 1.3.1 Design system & maquettes
│   ├── 1.3.2 Développement composants UI
│   ├── 1.3.3 Intégration API front
│   └── 1.3.4 Tests unitaires et d'intégration
│
├── 1.4 ÉVOLUTION API MÉTIERS (M+1 → M+3)
│   ├── 1.4.1 Conception API REST
│   ├── 1.4.2 Développement endpoints
│   ├── 1.4.3 Documentation OpenAPI
│   └── 1.4.4 Tests API (unitaires + contrat)
│
├── 1.5 MODULE FACTURATION (M+1 → M+3)
│   ├── 1.5.1 Modélisation fonctionnelle
│   ├── 1.5.2 Développement module
│   ├── 1.5.3 Intégration portail
│   └── 1.5.4 Tests facturation
│
├── 1.6 DISPOSITIF SSO (M+1 → M+3)
│   ├── 1.6.1 Choix de la solution SSO
│   ├── 1.6.2 Configuration et déploiement IdP
│   ├── 1.6.3 Intégration portail
│   └── 1.6.4 Tests de sécurité
│
├── 1.7 INTÉGRATION ET TESTS (M+3 → M+4)
│   ├── 1.7.1 Tests d'intégration globaux
│   ├── 1.7.2 Recette utilisateur (UAT)
│   ├── 1.7.3 Tests de performance et charge
│   └── 1.7.4 Audit de sécurité
│
└── 1.8 DÉPLOIEMENT ET MISE EN PRODUCTION (M+4)
    ├── 1.8.1 Plan de déploiement
    ├── 1.8.2 Activation/reprise des comptes partenaires actifs (hors historique métier)
    ├── 1.8.3 Formation utilisateurs
    └── 1.8.4 Go-live + monitoring J+7
```

---

## Estimation des Charges

| Lot | Activité | Charge (j/h) | Profil |
|-----|----------|-------------|--------|
| 1.1 | Cadrage & initialisation | 10 j | Chef de projet |
| 1.2 | Recueil & analyse besoins | 15 j | Chef de projet + PO + Tech leads |
| 1.3 | Front-end (design + dev) | 45 j | 2 Dev front + UX/UI |
| 1.4 | API métiers | 35 j | 2 Dev back |
| 1.5 | Module facturation | 25 j | 1 Dev back + 1 Dev front |
| 1.6 | Dispositif SSO | 20 j | 1 Dev back + Référent sécu |
| 1.7 | Intégration & tests | 20 j | Équipe complète |
| 1.8 | Déploiement & mise en prod | 10 j | Chef de projet + Exploitation |
| **TOTAL** | | **180 j** | |
| **Réserve (aléas 15%)** | | **27 j** | |
| **TOTAL AVEC RÉSERVE** | | **207 j** | |

### Répartition par profil

| Profil | Nb personnes | Charge totale | Coût jour estimé | Coût total |
|--------|-------------|--------------|-----------------|-----------|
| Chef de projet | 1 | 35 j | 700 €/j | 24 500 € |
| Dev front-end | 2 | 55 j | 600 €/j | 33 000 € |
| Dev back-end | 2 | 60 j | 600 €/j | 36 000 € |
| UX/UI Designer | 1 | 15 j | 550 €/j | 8 250 € |
| Référent sécurité | 1 | 10 j | 700 €/j | 7 000 € |
| Product Owner | 1 | 20 j | 650 €/j | 13 000 € |
| Exploitation | 1 | 7 j | 600 €/j | 4 200 € |
| **Sous-total charges** | | | | **125 950 €** |
| **Infrastructure & licences** | | | | **15 000 €** |
| **Réserve aléas (15%)** | | | | **21 143 €** |
| **BUDGET TOTAL ESTIMÉ** | | | | **162 093 €** |

### Hypothèses de chiffrage

| Hypothèse | Valeur retenue | Justification |
|-----------|----------------|---------------|
| Unité d'estimation | Jour-homme (j/h) | Permet de convertir les charges en budget et en capacité planning |
| Nombre de jours ouvrés par mois | 20 jours | Hypothèse standard de planification projet |
| TJM moyen développeur | 600 €/j | Base réaliste pour une équipe projet DSI mixte interne/prestation |
| Réserve d'aléas | 15 % | Couvre les risques identifiés : SSO, dépendances API, recette, sécurité |
| Infrastructure & licences | 15 000 € | Environnements, monitoring, licences éventuelles, outillage CI/CD et sécurité |
| Hors budget | Maintenance post M+5, phase 2 migration historique, application mobile native | Éléments explicitement exclus du périmètre v1 |

### Lecture budgétaire

Le budget total estimé s'élève à **162 093 €**, réserve comprise. La réserve d'aléas est calculée sur le sous-total charges + infrastructure, soit 15 % de 140 950 €. Elle n'est pas consommée par défaut : son utilisation nécessite un arbitrage en COPROJ ou COPIL selon l'impact délai/budget.

---

## Planning Prévisionnel

### Vue macro sur 4 mois

| Lot | M+0 | M+1 | M+2 | M+3 | M+4 |
|-----|:---:|:---:|:---:|:---:|:---:|
| Cadrage & initialisation | ████ | | | | |
| Recueil & analyse besoins | ████ | ████ | | | |
| Refonte front-end | | ████ | ████ | ████ | |
| Évolution API métiers | | ████ | ████ | ████ | |
| Module facturation | | ████ | ████ | ████ | |
| Dispositif SSO | | ████ | ████ | ████ | |
| Intégration & tests | | | | ████ | ████ |
| Déploiement & MEP | | | | | ████ |

### Sécurisation du planning M+4

Le planning est volontairement construit autour d'une **v1 minimale exploitable**. Les fonctionnalités Must Have sont priorisées pour garantir la mise en production en M+4, tandis que les Should Have et Could Have restent des variables d'ajustement. Trois leviers de sécurisation sont prévus :

- **Découpage fonctionnel** : chaque chantier livre un incrément testable avant la phase d'intégration globale
- **Spikes techniques** : SSO, facturation et contrats API sont validés tôt afin de réduire les risques d'incompatibilité
- **Go/no-go jalonnés** : chaque jalon donne lieu à une décision explicite de poursuite, réduction de scope ou report v1.1

### Jalons clés

| Jalon | Date cible | Critère de validation |
|-------|------------|----------------------|
| J1 — Kick-off | M+0 S1 | Note de cadrage validée par le Sponsor |
| J2 — Spécifications validées | M+1 S2 | Backlog priorisé approuvé par le PO |
| J3 — Fin Sprint 1 (proto front) | M+2 S2 | Démo front + API de base fonctionnels |
| J4 — Fin Sprint 2 (SSO + facturation) | M+3 S2 | SSO et module facturation intégrés |
| J5 — Recette UAT | M+4 S1 | Recette signée par les représentants partenaires |
| J6 — Go-live v1 | M+4 S3 | Mise en production validée par le Sponsor |

### Chemin critique

```
Spécifications (M+1) → Dev API (M+1→M+3) → Intégration SSO (M+2→M+3) → Tests d'intégration (M+3→M+4) → UAT (M+4 S1) → Go-live (M+4 S3)
```

Le chemin critique passe par le développement des API back-end, car le front-end, la facturation et le SSO en dépendent tous. Tout retard sur les API décale l'ensemble de la livraison.

### Dépendances critiques

| Tâche aval | Dépend de | Type |
|-----------|-----------|------|
| Intégration front-end | Endpoints API disponibles | Fin-Début |
| Module facturation | API métiers (commandes/contrats) | Fin-Début |
| SSO | Environnement d'intégration disponible | Fin-Début |
| Tests d'intégration | Tous les lots de dev terminés | Fin-Début |
| UAT | Tests d'intégration passants | Fin-Début |
| Go-live | UAT signée + audit sécurité OK | Fin-Début |

---

## Registre des Risques

| ID | Risque | Probabilité | Impact | Criticité | Mesure préventive | Plan de réponse |
|----|--------|:-----------:|:------:|:---------:|-------------------|----------------|
| R1 | Dérapage du calendrier (scope trop large) | Élevée | Élevé | Critique | Priorisation MoSCoW stricte, gel du scope dès M+0 | Arbitrage COPIL, réduction du scope Should/Could |
| R2 | Retard sur l'intégration SSO (complexité sous-estimée) | Moyenne | Élevé | Élevé | Spike technique en M+1, choix d'une solution éprouvée | Basculer sur SSO simplifié (OAuth2 uniquement) pour la v1 |
| R3 | Dépendances entre chantiers non maîtrisées | Moyenne | Élevé | Élevé | Architecture API définie en amont, contrats d'interface | Réunion de synchronisation hebdomadaire des Tech Leads |
| R4 | Dépassement budgétaire | Faible | Élevé | Moyen | Suivi hebdomadaire, réserve de 15 % | Arbitrage scope, report des "Could Have" |
| R5 | Indisponibilité d'un membre clé de l'équipe | Faible | Moyen | Moyen | Binômage systématique, documentation continue | Mobilisation de la réserve ou prestataire |
| R6 | Faible adoption par les partenaires | Moyenne | Moyen | Moyen | Implication partenaires dès la phase de spécification | Plan de formation et support renforcé au go-live |
| R7 | Faille de sécurité (SSO, API) | Faible | Critique | Élevé | Revue de code sécurité, audit avant MEP | Rollback immédiat, patch d'urgence sous 48h |
| R8 | Problème de performance en production | Faible | Moyen | Moyen | Tests de charge en M+3 | Optimisation ciblée, mise à l'échelle infra |
| R9 | Non-conformité RGPD sur les données partenaires | Faible | Élevé | Élevé | Revue DPO, minimisation des données, traçabilité des accès | Blocage go-live partiel jusqu'à correction |
| R10 | Faible disponibilité des partenaires pour l'UAT | Moyenne | Moyen | Moyen | Réservation des créneaux UAT dès M+1, panel de secours | Réduction du périmètre UAT aux parcours critiques |

---

## Plan Qualité

### Objectifs qualité

- Taux de couverture des tests automatisés ≥ 80 %
- Zéro défaut bloquant en recette UAT
- Disponibilité cible : 99,5 % en production
- Délai de résolution des incidents critiques < 4h

### Activités qualité

| Activité | Fréquence | Responsable |
|----------|-----------|-------------|
| Revue de code (pull request) | À chaque merge | Tech Lead |
| Tests unitaires automatisés | En continu (CI/CD) | Développeurs |
| Tests d'intégration | Fin de chaque sprint | QA |
| Tests de sécurité (SAST) | En continu (CI/CD) | Référent sécu |
| Tests de performance/charge | M+3 | Tech Lead back |
| Audit de sécurité externe | M+4 avant go-live | Référent sécu |
| UAT (recette utilisateur) | M+4 S1 | PO + Partenaires |

### Critères de Definition of Done (DoD) pour la mise en production

- Tous les tests automatisés passants
- Code review approuvée par le Tech Lead
- Documentation technique à jour
- Tests de performance validés
- Audit sécurité sans vulnérabilité critique
- UAT signée par les représentants partenaires
- Plan de rollback documenté et testé

---

---
