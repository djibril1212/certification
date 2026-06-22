# Dossier de Certification — Projet de Refonte du Portail B2B
**Direction des Systèmes d'Information**
**Équipe projet DSI — Mai 2026**

---

## Synthèse exécutive

Ce dossier présente le pilotage complet d'un projet de refonte du portail B2B de la DSI, depuis le cadrage initial jusqu'au retour d'expérience et au plan de montée en compétences. Le projet vise une première mise en production en M+4 d'une version exploitable centrée sur quatre chantiers prioritaires : refonte front-end, évolution des API métiers, module de facturation partenaire et dispositif SSO.

La démarche retenue est une approche hybride combinant les apports de Scrum (itérations, démonstrations régulières, feedback partenaire) avec des jalons de gouvernance formels adaptés à un contexte DSI contraint par le délai, le budget et la sécurité. Le dossier met également en évidence la capacité de l'équipe à anticiper les risques, suivre les KPI projet, traiter un incident critique et capitaliser sur les apprentissages.

### Lecture rapide du dossier

| Partie | Finalité |
|--------|----------|
| **5.1 Cadrage et gouvernance** | Définir le besoin, le périmètre, les objectifs, les parties prenantes et les responsabilités |
| **5.2 Planification et chiffrage** | Structurer le travail, estimer les charges, sécuriser le planning, le budget, les risques et la qualité |
| **5.3 Méthodologie et coordination** | Justifier l'approche agile/hybride, organiser le backlog, les rituels et le flux de travail |
| **5.4 KPI et reporting** | Suivre la performance projet et produire un reporting d'avancement exploitable par le sponsor |
| **5.5 Résolution d'incidents** | Décrire la gestion d'un incident critique, l'analyse documentaire et la décision technique retenue |
| **5.6 Montée en compétences** | Transformer l'incident en apprentissage collectif mesurable |

---

# SECTION 5.1 — CADRAGE ET GOUVERNANCE

---

## Note de Cadrage — Refonte du Portail B2B

### 1. Contexte du Projet

#### Situation actuelle

Depuis plusieurs années, l'entreprise s'appuie sur un portail B2B utilisé par ses partenaires pour transmettre leurs demandes, suivre leur traitement et accéder à différents services. Cette solution présente aujourd'hui de nombreuses fragilités :

- **Maintenabilité dégradée** : accumulation de dette technique, difficultés de mise à jour
- **Expérience partenaire insatisfaisante** : parcours peu lisibles, absence d'ergonomie moderne
- **Délais de traitement allongés** : certaines opérations restent partiellement manuelles
- **Interfaces applicatives obsolètes** : les API ne couvrent plus l'ensemble des besoins métier
- **Gestion des accès fragmentée** : absence de mécanisme SSO, multiplication des identifiants

#### Motivations et enjeux

| Dimension | Enjeux |
|-----------|--------|
| **Stratégique** | Renforcer la qualité du service rendu aux partenaires, améliorer l'image de la DSI |
| **Opérationnel** | Réduire de 20 % les délais de traitement, automatiser les opérations manuelles |
| **Financier** | Respecter un budget cible, réduire les coûts de maintenance à long terme |
| **Technique** | Moderniser le front-end, faire évoluer les API, intégrer facturation et SSO |

#### Analyse SWOT

| **Forces** | **Faiblesses** |
|------------|----------------|
| Équipe DSI mobilisée et sponsor identifié | Dette technique accumulée sur le portail existant |
| Demande forte des partenaires pour une expérience modernisée | Couverture API incomplète et documentation insuffisante |
| Capacité à mobiliser les équipes front, back, sécurité et exploitation | Maîtrise SSO/JWT à renforcer dans l'équipe |

| **Opportunités** | **Menaces** |
|------------------|-------------|
| Amélioration visible de la qualité de service partenaire | Délai M+4 contraint avec faible marge de dérive |
| Réduction des tâches manuelles et des coûts de maintenance | Risque de dérive de périmètre si les Should/Could sont intégrés trop tôt |
| Standardisation des API et de l'authentification pour les futurs projets | Dépendances fortes entre front-end, API, facturation et SSO |

---

### 2. Périmètre du Projet

#### Ce qui est dans le périmètre (IN SCOPE)

- Refonte de l'interface front-end du portail (UX/UI modernisée, responsive)
- Évolution des API métiers (REST, documentation OpenAPI)
- Intégration d'un module de facturation partenaire
- Mise en place d'un dispositif SSO (Single Sign-On)
- Tests d'intégration et recette utilisateur
- Documentation technique et utilisateur

#### Ce qui est hors périmètre (OUT OF SCOPE)

- Refonte du système de gestion interne (back-office)
- Migration des données historiques (hors scope M+4, étude à prévoir en phase 2)
- Évolutions des processus métier non liées au portail
- Déploiement sur mobile natif (iOS/Android)

**Clarification importante :** la mise en production M+4 inclut uniquement l'activation ou la reprise technique des comptes partenaires nécessaires au SSO. Elle n'inclut pas la migration de l'historique métier complet, qui fera l'objet d'une étude séparée en phase 2.

---

### 3. Objectifs SMART

| Objectif | Spécifique | Mesurable | Atteignable | Pertinent | Temporel |
|----------|-----------|-----------|-------------|-----------|----------|
| Réduction des délais | Automatiser les étapes manuelles du traitement | -20% délai moyen de traitement partenaire | Suppression de 4 tâches manuelles identifiées | Réponse directe à la demande sponsor | M+4 (mise en production) |
| Respect du budget | Pas de dépassement du budget cible DSI | Dérive budgétaire ≤ 5 % | Budget dimensionné sur la base d'un chiffrage détaillé | Contrainte sponsor explicite | Tout au long du projet |
| Première mise en prod | Livraison d'une v1 exploitable | Go-live effectif | Scope priorisé MoSCoW | Valeur rapide pour les partenaires | M+4 |
| Satisfaction partenaires | Score de satisfaction post-lancement | NPS ≥ 30 / satisfaction ≥ 4/5 | Tests utilisateurs inclus dans le planning | Indicateur de valeur produite | M+5 (mesure post-lancement) |

### 4. Critères de réussite du projet

Le projet sera considéré comme réussi si les conditions suivantes sont réunies :

- La v1 du portail est mise en production en M+4 avec les fonctionnalités Must Have validées
- Le budget final reste dans une marge de dérive maximale de 5 %
- Les tests UAT sont validés à au moins 95 % sans anomalie bloquante
- L'audit sécurité ne remonte aucune vulnérabilité critique avant le go-live
- Les partenaires pilotes attribuent une note de satisfaction moyenne d'au moins 4/5 à M+5
- L'équipe dispose d'une documentation exploitable : OpenAPI, guide utilisateur, ADR SSO/JWT, plan de rollback

---

### 5. Hypothèses de départ

- Le périmètre technique (front + API + facturation + SSO) est confirmé et gelé dès le démarrage
- Les équipes métier partenaires sont disponibles pour les ateliers de recueil des besoins (M+0 à M+1)
- L'environnement d'intégration technique est disponible dès M+1
- Le budget cible est alloué et validé avant le kick-off
- L'équipe projet est constituée à 100 % dès le démarrage
- Les décisions d'arbitrage sont rendues en COPIL sous 5 jours ouvrés maximum
- Les partenaires pilotes acceptent de participer aux ateliers et à la recette UAT selon le calendrier projet
- Les systèmes tiers nécessaires à la facturation et au SSO disposent d'interfaces documentées ou de référents disponibles

---

### 6. Parties Prenantes

| Acteur | Rôle | Niveau d'implication |
|--------|------|----------------------|
| **Sponsor (DSI)** | Décideur stratégique, arbitrages budgétaires | Fort — décision finale |
| **Chef de projet DSI** | Pilotage opérationnel, coordination générale | Fort — quotidien |
| **Équipe développement front** | Refonte UI/UX, intégration composants | Fort — exécution |
| **Équipe développement back** | Évolution API, facturation, SSO | Fort — exécution |
| **Référent sécurité** | Validation architecture SSO, conformité | Moyen — jalons clés |
| **Représentants partenaires** | Expression des besoins, recette | Moyen — ateliers + UAT |
| **Équipe exploitation** | Déploiement, monitoring production | Moyen — mise en prod |
| **Direction métier** | Validation fonctionnelle des livrables | Faible — comités |

---

### 7. Contraintes identifiées

| Type | Contrainte | Impact |
|------|-----------|--------|
| **Délai** | Première mise en prod à M+4 | Planning tendu, priorisation stricte nécessaire |
| **Budget** | Budget cible fixé et non négociable | Scope MoSCoW, pas de dérive possible |
| **Technique** | Intégration simultanée front + API + SSO + facturation | Dépendances fortes entre chantiers |
| **Ressources** | Équipe projet taille fixe | Pas de recrutement possible, priorisation du backlog |
| **Qualité** | Exigence de disponibilité et de sécurité du portail | Tests obligatoires avant tout déploiement |

---

### 8. Classification MoSCoW des fonctionnalités

| Priorité | Fonctionnalités |
|---------|----------------|
| **Must Have** | Nouveau front-end responsive, API REST métiers documentées, SSO fonctionnel, consultation des factures, génération automatique de factures simples |
| **Should Have** | Tableau de bord partenaire, notifications de changement de statut, historique des demandes |
| **Could Have** | Export PDF des factures, multi-langue, interface d'administration avancée |
| **Won't Have** | App mobile native, IA de recommandation, marketplace partenaires |

**Règle d'arbitrage :** en cas de dérive planning ou budget, seuls les Must Have restent protégés pour la v1 M+4. Les Should Have et Could Have sont explicitement reportables en v1.1 afin de sécuriser le go-live.

---

## Proposition de Gouvernance Projet

### Instances de pilotage

| Instance | Fréquence | Participants | Rôle |
|----------|-----------|--------------|------|
| **COPIL** (Comité de Pilotage) | Bimensuel | Sponsor DSI, Chef de projet, Direction métier | Validation stratégique, arbitrages budgétaires, go/no-go jalons |
| **COPROJ** (Comité de Projet) | Hebdomadaire | Chef de projet, Tech Leads, Référent sécurité | Pilotage opérationnel, suivi avancement, levée des blocages |
| **Sprint Review** | Toutes les 2 semaines | Équipe projet + représentants partenaires | Démonstration des livraisons, recueil feedback |
| **Sprint Planning** | Toutes les 2 semaines | Équipe de développement + PO | Planification du sprint suivant |
| **Daily Stand-up** | Quotidien | Équipe de développement | Synchronisation courte (15 min max) |
| **COUTIL** (Comité Technique) | À la demande | Tech Leads + Référent sécurité | Résolution des problèmes techniques complexes |

### Circuits de décision

```
Décisions stratégiques (budget, périmètre, go-live) → COPIL → Sponsor
Décisions opérationnelles (priorités, organisation) → COPROJ → Chef de projet
Décisions techniques (architecture, sécurité) → COUTIL → Tech Lead
Décisions de sprint (backlog, vélocité) → Sprint Planning → Product Owner
```

### Circuits de validation

- Toute évolution de périmètre doit être soumise au COPIL pour arbitrage
- Les livrables techniques sont validés en COPROJ avant intégration
- La recette fonctionnelle est co-validée avec les représentants partenaires
- Le go-live final nécessite la validation explicite du Sponsor

---

## Matrice RACI

| Activité | Sponsor DSI | Chef de Projet | Tech Lead Front | Tech Lead Back | Référent Sécu | PO | Partenaires | Exploitation |
|----------|:-----------:|:--------------:|:---------------:|:--------------:|:-------------:|:--:|:-----------:|:------------:|
| Validation note de cadrage | A | R | C | C | C | C | I | I |
| Planification projet | I | R/A | C | C | C | C | I | I |
| Développement front-end | I | I | R | C | C | A | I | I |
| Développement API | I | I | C | R | C | A | I | I |
| Intégration SSO | I | C | C | R | A | I | I | I |
| Module facturation | I | I | C | R | C | A | C | I |
| Tests d'intégration | I | C | R | R | C | A | C | I |
| Recette utilisateur (UAT) | I | C | C | C | I | A | R | I |
| Validation sécurité | C | C | C | C | R | I | I | I |
| Déploiement production | A | R | C | C | C | I | I | R |
| Pilotage budgétaire | A | R | I | I | I | I | I | I |
| Communication partenaires | I | R | I | I | I | C | A | I |

*R = Responsable, A = Autorité (valideur), C = Consulté, I = Informé*

---

---

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

# SECTION 5.3 — MÉTHODOLOGIE ET COORDINATION

---

## Justification du Choix Agile/Hybride

### Approche retenue : méthode hybride (Scrum adapté + jalons contractuels)

**Pourquoi pas un cycle en V pur ?**

Le cycle en V implique un gel complet des spécifications dès le démarrage. Dans notre contexte, les besoins des partenaires ne sont pas entièrement stabilisés et la contrainte de délai (M+4) impose de livrer de la valeur rapidement, en itérant. Un cycle en V pur aurait reporté la première livraison à la fin du projet sans visibilité intermédiaire.

**Pourquoi pas du Scrum pur ?**

Le Scrum pur est adapté à des équipes produit autonomes avec un périmètre ouvert. Ici, nous avons des contraintes fortes : budget fixé, délai imposé (M+4), et une DSI qui doit rendre des comptes à un sponsor avec des jalons formels. Un Scrum pur sans jalons contractuels ne correspond pas à ces exigences de gouvernance.

**L'approche hybride répond aux contraintes du projet :**

| Contrainte | Réponse méthodologique |
|-----------|----------------------|
| Délai M+4 non négociable | Jalons formels M+1, M+2, M+3, M+4 avec go/no-go |
| Visibilité sponsor | COPIL bimensuel avec rapport d'avancement |
| Valeur rapide | Sprints de 2 semaines avec démo à chaque fin de sprint |
| Scope complexe (4 chantiers) | Backlog structuré en épics, priorisation MoSCoW |
| Coordination multi-équipes | Rituels de synchronisation inter-équipes (Scrum of Scrums) |

---

## Backlog Structuré en Épics et User Stories

### Epic 1 — Refonte du Front-End

| ID | User Story | Priorité | Estimation |
|----|-----------|----------|-----------|
| US-F01 | En tant que partenaire, je veux accéder au portail depuis n'importe quel appareil (responsive) afin de soumettre mes demandes en mobilité | Must | 8 pts |
| US-F02 | En tant que partenaire, je veux visualiser le statut de mes demandes en temps réel afin de réduire mes relances | Must | 5 pts |
| US-F03 | En tant que partenaire, je veux un tableau de bord personnalisé afin d'accéder rapidement à mes services les plus utilisés | Should | 8 pts |
| US-F04 | En tant que partenaire, je veux recevoir des notifications lors des changements d'état de mes demandes afin d'être informé sans me connecter | Should | 5 pts |
| US-F05 | En tant que partenaire, je veux filtrer et rechercher mes demandes historiques afin de retrouver facilement une opération passée | Should | 3 pts |

### Epic 2 — API Métiers

| ID | User Story | Priorité | Estimation |
|----|-----------|----------|-----------|
| US-A01 | En tant que développeur front, je veux une API REST documentée (OpenAPI) pour les demandes partenaires afin d'intégrer le portail sans ambiguïté | Must | 8 pts |
| US-A02 | En tant que système de facturation, je veux un endpoint API pour récupérer les données de commandes afin de générer automatiquement les factures | Must | 5 pts |
| US-A03 | En tant qu'administrateur DSI, je veux des logs d'audit sur toutes les actions API afin de tracer les opérations pour des raisons de sécurité et conformité | Must | 5 pts |
| US-A04 | En tant que partenaire, je veux que les temps de réponse API soient < 500ms afin de bénéficier d'une expérience fluide | Should | 3 pts |

### Epic 3 — Module Facturation

| ID | User Story | Priorité | Estimation |
|----|-----------|----------|-----------|
| US-B01 | En tant que partenaire, je veux consulter mes factures directement sur le portail afin de ne plus recevoir de courriers papier | Must | 8 pts |
| US-B02 | En tant que partenaire, je veux télécharger mes factures en PDF afin de les intégrer dans ma comptabilité | Could | 3 pts |
| US-B03 | En tant que comptable DSI, je veux que les factures soient générées automatiquement à la validation d'une commande afin de réduire les traitements manuels | Must | 8 pts |
| US-B04 | En tant que partenaire, je veux recevoir une notification par e-mail à la mise à disposition d'une nouvelle facture | Should | 3 pts |

### Epic 4 — Single Sign-On (SSO)

| ID | User Story | Priorité | Estimation |
|----|-----------|----------|-----------|
| US-S01 | En tant que partenaire, je veux me connecter au portail avec un identifiant unique (SSO) afin de ne pas gérer plusieurs couples login/mot de passe | Must | 13 pts |
| US-S02 | En tant qu'administrateur DSI, je veux gérer les droits d'accès depuis un annuaire centralisé afin de simplifier l'administration des comptes | Must | 8 pts |
| US-S03 | En tant que partenaire, je veux que ma session reste active de façon sécurisée afin de ne pas me reconnecter à chaque visite | Should | 5 pts |
| US-S04 | En tant qu'administrateur DSI, je veux activer/désactiver un compte partenaire en temps réel afin de sécuriser les accès en cas de départ | Must | 5 pts |

---

## Exemples de Critères d'Acceptation

| User Story | Critères d'acceptation |
|------------|------------------------|
| US-F01 — Portail responsive | Le portail est utilisable sur desktop, tablette et mobile ; les parcours de demande restent accessibles sans perte d'information ; les tests d'affichage sont validés sur les navigateurs cibles |
| US-A01 — API REST documentée | Les endpoints principaux sont disponibles en staging ; la documentation OpenAPI décrit les routes, statuts d'erreur et schémas de données ; les tests de contrat sont passants |
| US-B01 — Consultation factures | Un partenaire authentifié consulte uniquement ses propres factures ; les statuts de facturation sont affichés ; les données sensibles sont masquées selon les règles sécurité |
| US-S01 — Connexion SSO | Un partenaire peut se connecter via l'IdP ; les rôles applicatifs sont correctement mappés ; la déconnexion invalide la session applicative |

---

## Definition of Ready (DoR)

Une User Story est prête à entrer en sprint si et seulement si :

- [ ] Elle est rédigée selon le format "En tant que… je veux… afin de…"
- [ ] Les critères d'acceptation sont définis et compris par l'équipe
- [ ] Elle est estimée en points de complexité par l'équipe
- [ ] Les dépendances techniques sont identifiées et levées (ou un plan est en place)
- [ ] Les maquettes ou spécifications techniques associées sont disponibles
- [ ] Elle est indépendante (peut être développée sans bloquer une autre US)
- [ ] Elle est testable (des scénarios de test peuvent être écrits)
- [ ] Elle a été validée par le Product Owner

---

## Definition of Done (DoD)

Une User Story est terminée ("Done") si et seulement si :

- [ ] Le code est développé et respecte les standards de codage du projet
- [ ] Les tests unitaires sont écrits et passants (couverture ≥ 80 %)
- [ ] La pull request a été revue et approuvée par au moins un pair (Tech Lead)
- [ ] Les tests d'intégration associés sont passants en pipeline CI/CD
- [ ] La documentation technique (README, OpenAPI) est mise à jour
- [ ] La fonctionnalité est déployée en environnement de staging
- [ ] La démo a été réalisée et validée par le Product Owner
- [ ] Aucun bug bloquant ou critique n'est ouvert sur cette story

---

## Rituels de Pilotage et de Coordination

| Rituel | Durée | Fréquence | Participants | Objectif |
|--------|-------|-----------|--------------|---------|
| **Daily Stand-up** | 15 min | Quotidien | Équipe dev | Synchronisation : "Qu'ai-je fait hier ? Que vais-je faire aujourd'hui ? Ai-je un blocage ?" |
| **Sprint Planning** | 2h | Début de sprint (J1) | Équipe + PO | Sélection et découpage des stories du sprint, engagement de l'équipe |
| **Sprint Review** | 1h | Fin de sprint (J14) | Équipe + PO + Partenaires | Démo des fonctionnalités livrées, recueil feedback |
| **Sprint Retrospective** | 1h | Fin de sprint (J14) | Équipe | Amélioration continue : "Keep, Drop, Try" |
| **Backlog Refinement** | 1h | J7 de chaque sprint | Équipe + PO | Affinage et estimation des stories du prochain sprint |
| **Scrum of Scrums** | 30 min | 2× par semaine | Tech Leads front + back + sécu | Synchronisation inter-équipes, levée des dépendances |
| **COPROJ** | 1h | Hebdomadaire | Chef de projet + Tech Leads | Pilotage opérationnel, escalade si nécessaire |
| **COPIL** | 1h30 | Bimensuel | Sponsor + Chef de projet + Direction métier | Pilotage stratégique, arbitrages, validation jalons |

---

## Tableau Kanban

```
┌────────────────┬─────────────────┬──────────────────┬────────────────┬──────────────┐
│   BACKLOG      │   À FAIRE       │   EN COURS       │   EN REVUE     │   TERMINÉ    │
│   (Produit)    │   (Sprint)      │   (WIP max: 3)   │   (WIP max: 2) │   (Done)     │
├────────────────┼─────────────────┼──────────────────┼────────────────┼──────────────┤
│ US-S01 (13pts) │ US-F01 (8pts)  │ US-A01 (8pts)    │ US-F02 (5pts)  │ US-F01 ✓    │
│ US-F03 (8pts)  │ US-B01 (8pts)  │ US-S04 (5pts)    │ US-A03 (5pts)  │ US-A02 ✓    │
│ US-F04 (5pts)  │ US-A04 (3pts)  │ US-B02 (3pts)    │                │              │
│ US-B04 (3pts)  │                │                  │                │              │
│ US-S03 (5pts)  │                │                  │                │              │
└────────────────┴─────────────────┴──────────────────┴────────────────┴──────────────┘
```

---

## Règle de Gestion du WIP (Work In Progress)

**Définition :** Le WIP est le nombre maximum de tâches pouvant être simultanément dans une colonne du tableau Kanban.

**Règles appliquées :**

| Colonne | Limite WIP | Justification |
|---------|-----------|---------------|
| À Faire (Sprint) | 6 stories | Correspond à la capacité d'un sprint de 2 semaines à 5 devs |
| En Cours | **3 stories** | Règle de focalisation : éviter la dispersion et le multitâche |
| En Revue | **2 stories** | Fluidifier la revue de code, éviter les bottlenecks |
| Terminé | Illimité | Archive du sprint |

**Règle d'escalade WIP :** Si la colonne "En Cours" atteint sa limite, tout développeur qui termine une tâche doit d'abord aider à débloquer une story "En Revue" avant d'en démarrer une nouvelle. Cette règle "Stop Starting, Start Finishing" garantit le flux et réduit le temps de cycle.

---

---

# SECTION 5.4 — KPI ET REPORTING

---

## Tableau de Bord KPI

### Indicateurs de délai

| KPI | Définition | Cible | Mesure | Source |
|-----|-----------|-------|--------|--------|
| **Vélocité d'équipe** | Nombre de points livrés par sprint | ≥ 30 pts/sprint | Fin de sprint | Jira |
| **SPI** (Schedule Performance Index) | Valeur acquise / Valeur planifiée | ≥ 0,95 | Hebdomadaire | Planning |
| **Taux d'avancement** | % du backlog livré vs prévu | ≥ planifié | Fin de sprint | Jira |
| **Lead time** | Durée moyenne de traitement d'une story (DoR → DoD) | ≤ 5 jours | Continu | Jira |
| **Écart sur jalons** | Retard en jours sur chaque jalon | 0 jour | À chaque jalon | Planning |

### Indicateurs de coût

| KPI | Définition | Cible | Mesure | Source |
|-----|-----------|-------|--------|--------|
| **CPI** (Cost Performance Index) | Valeur acquise / Coût réel | ≥ 0,95 | Hebdomadaire | Feuille de temps |
| **Budget consommé** | % du budget total dépensé | ≤ planifié | Hebdomadaire | Comptabilité projet |
| **Dérive budgétaire** | Écart entre budget prévu et réel | ≤ 5 % | Mensuel | Comptabilité projet |

### Indicateurs agiles

| KPI | Définition | Cible | Mesure | Source |
|-----|-----------|-------|--------|--------|
| **Taux de stories livrées** | Stories terminées / Stories engagées dans le sprint | ≥ 85 % | Fin de sprint | Jira |
| **Dette technique** | Nombre de bugs ouverts + tickets tech debt | Tendance décroissante | Hebdomadaire | Jira |
| **WIP moyen** | Nombre moyen de stories en cours | ≤ 3 | Continu | Kanban |

### Indicateurs qualité

| KPI | Définition | Cible | Mesure | Source |
|-----|-----------|-------|--------|--------|
| **Couverture de tests** | % du code couvert par des tests auto | ≥ 80 % | Continu (CI) | SonarQube |
| **Taux de bugs critiques** | Bugs bloquants ouverts | 0 avant go-live | Hebdomadaire | Jira |
| **Taux de réussite UAT** | Tests acceptés / Tests totaux | ≥ 95 % | Recette | Cahier de recette |

### Indicateurs de risques

| KPI | Définition | Cible | Mesure |
|-----|-----------|-------|--------|
| **Risques actifs** | Nombre de risques de niveau Critique ou Élevé | ≤ 2 | Hebdomadaire |
| **Actions correctives ouvertes** | Actions de mitigation non clôturées | Tendance décroissante | Hebdomadaire |

### Seuils d'alerte et règles d'escalade

| Domaine | Vert | Orange | Rouge | Action attendue |
|---------|------|--------|-------|-----------------|
| Délai | SPI ≥ 0,95 | 0,85 ≤ SPI < 0,95 | SPI < 0,85 | Orange : plan de rattrapage COPROJ ; Rouge : arbitrage COPIL |
| Budget | CPI ≥ 0,95 | 0,90 ≤ CPI < 0,95 | CPI < 0,90 | Orange : revue de consommation ; Rouge : réduction de scope ou mobilisation réserve |
| Qualité | 0 bug critique | 1 bug critique ouvert | > 1 bug critique ou bug bloquant | Priorisation immédiate avant nouvelle fonctionnalité |
| Risques | ≤ 2 risques élevés/critiques | 3 risques élevés/critiques | > 3 risques élevés/critiques | Mise à jour du plan de mitigation et arbitrage |
| UAT | ≥ 95 % passants | 85 % à 94 % passants | < 85 % passants | Report go-live ou réduction aux parcours validés |

---

## Revue d'Étape Structurée — Modèle Sprint Review

### Ordre du jour type (1h)

| Durée | Point | Animateur |
|-------|-------|-----------|
| 5 min | Rappel des objectifs du sprint | Chef de projet |
| 20 min | Démo des fonctionnalités livrées | Tech Leads |
| 15 min | Résultats vs objectifs (KPI, vélocité, stories) | PO |
| 10 min | Retour des partenaires / parties prenantes | Partenaires présents |
| 5 min | Mise à jour du backlog suite aux feedbacks | PO |
| 5 min | Présentation du prochain sprint (objectifs) | PO + Chef de projet |

### Grille d'analyse des écarts

| Indicateur | Prévu | Réalisé | Écart | Analyse | Action |
|-----------|-------|---------|-------|---------|--------|
| Stories livrées | 6 | 5 | -1 | US-S01 complexité sous-estimée | Re-estimation sprint suivant, découpage |
| Points livrés | 32 | 27 | -5 | Idem | Report US-S01 découpée en 2 stories |
| Budget sprint | 28 000 € | 26 500 € | -1 500 € | Sous-consommation RH | RAS |
| Bugs critiques | 0 | 1 | +1 | Faille CSRF sur API | Patch prioritaire S1 sprint suivant |

---

## Rapport Synthétique d'Avancement

**Projet :** Refonte Portail B2B — DSI
**Période :** Sprint 2 (M+2, semaines 3-4)
**Date du rapport :** Semaine 4 de M+2
**Auteur :** Chef de projet

### Synthèse exécutive

Le projet est **en bonne voie** avec un léger retard sur l'intégration SSO (+3 jours) compensé par une avance sur le module de facturation (-2 jours). Le budget est respecté (consommation à 48 % pour 50 % d'avancement). La qualité est maîtrisée avec 82 % de couverture de tests.

### Avancement global

| Indicateur | Statut | Commentaire |
|-----------|:------:|-------------|
| Délai | Orange | Retard de 3 jours sur SSO, chemin critique surveillé |
| Budget | Vert | Consommation conforme au planning |
| Qualité | Vert | Couverture tests 82 %, 0 bug critique ouvert |
| Risques | Orange | R2 (SSO) activé, plan de mitigation en cours |
| Satisfaction équipe | Vert | Moral bon, pas de départ ni d'absentéisme |

**Légende :** Vert = conforme ; Orange = vigilance et plan d'action ; Rouge = arbitrage immédiat requis.

### Points d'attention et décisions requises

1. **Intégration SSO** : La complexité de l'intégration OAuth2 avec l'annuaire existant est supérieure aux estimations. Le Tech Lead propose de simplifier le périmètre v1 (SSO pour le portail uniquement, extension API SSO reportée en v1.1). **Décision demandée au COPIL.**
2. **Disponibilité des partenaires pour l'UAT** : Seulement 2 des 5 partenaires ciblés ont confirmé leur participation à la recette. **Action : Chef de projet relance les 3 partenaires restants avant fin de semaine.**

### Prévision sprint suivant

Objectif Sprint 3 : Livraison SSO (scope simplifié), finalisation module facturation, début des tests d'intégration.

---

---

# SECTION 5.5 — RÉSOLUTION D'INCIDENTS

---

## Journal d'Incident

**Référence :** INC-2026-001
**Date de détection :** M+3, Sprint 3, Jour 8 (mardi matin, daily stand-up)
**Sévérité :** Critique (bloquant pour la livraison M+4)
**Déclarant :** Tech Lead back-end
**Statut :** Résolu

### Description de l'incident

Au cours du sprint 3, l'équipe back-end a identifié que l'IdP (Identity Provider) SSO déployé (Keycloak) ne supporte pas nativement le format de token attendu par le module de facturation (JWT HS256 requis par le prestataire facturation vs RS256 imposé par Keycloak par défaut). Cette incompatibilité bloque l'intégration entre le SSO et le module de facturation.

**Impact :** Sans résolution, la mise en production M+4 est compromise. Le module de facturation ne peut pas s'authentifier auprès du SSO, rendant les deux fonctionnalités inutilisables ensemble.

---

## Synthèse de la Recherche Documentaire FR/EN

### Recherche en français

Sources consultées :
- Documentation officielle Keycloak — Server Administration Guide : https://www.keycloak.org/docs/latest/server_admin/
- Documentation Red Hat build of Keycloak — Server Administration Guide : https://docs.redhat.com/en/documentation/red_hat_build_of_keycloak/26.0/html-single/server_administration_guide/
- Requêtes documentaires francophones : "Keycloak JWT HS256 RS256 configuration", "sécuriser API OAuth2 JWT Keycloak"
- Articles techniques francophones sur la sécurisation d'API avec OAuth2, JWT et Keycloak

Résultat : Keycloak utilise RS256 par défaut pour raisons de sécurité (clé asymétrique). Il est possible de configurer HS256 au niveau du client, mais cela est déconseillé par RedHat pour les environnements de production car HS256 partage une clé secrète entre toutes les parties.

### Recherche en anglais

Sources consultées :
- Keycloak official docs — "Configuring client policies", "Token Signature Algorithm"
- Auth0 Docs — Signing Algorithms : https://auth0.com/docs/get-started/applications/signing-algorithms
- Auth0 blog — "RS256 vs HS256: What's the difference?" : https://auth0.com/blog/rs256-vs-hs256-whats-the-difference/
- Auth0 blog — "Navigating RS256 and JWKS" : https://auth0.com/blog/navigating-rs256-and-jwks/
- OWASP JWT Cheat Sheet : https://cheatsheetseries.owasp.org/cheatsheets/JSON_Web_Token_for_Java_Cheat_Sheet.html
- RFC 7518 — JSON Web Algorithms : https://www.rfc-editor.org/rfc/rfc7518

Résultat : La documentation anglophone confirme qu'il est techniquement possible de configurer HS256 par client dans Keycloak, mais souligne les risques de sécurité. L'alternative recommandée est de configurer le module de facturation pour accepter RS256, ou d'utiliser un token relay (adaptateur) entre les deux systèmes.

**Date de consultation des sources :** 21 mai 2026.

---

## Options Étudiées et Décision Retenue

| Option | Description | Avantages | Inconvénients | Faisabilité M+4 |
|--------|-----------|-----------|---------------|:--------------:|
| **Option A** | Configurer Keycloak en HS256 pour le client facturation | Simple côté Keycloak | Sécurité dégradée (clé partagée), déconseillé OWASP | Oui |
| **Option B** | Modifier le module facturation pour accepter RS256 | Aligné standards sécurité, propre | Nécessite intervention prestataire facturation, délai incertain | Risqué |
| **Option C** | Token relay : micro-service d'adaptation RS256→HS256 | Sécurité préservée, découplage | Complexité architecturale, nouveau composant à maintenir | Non (délai M+4) |
| **Option D — retenue** | Conserver Keycloak en RS256 et configurer le module facturation pour valider les tokens via le JWKS endpoint | Sécurité optimale, standard OAuth2, solution propre | Légère modification du module facturation (lecture JWKS endpoint) | Oui |

**Décision retenue : Option D**

Après présentation en COUTIL (Comité Technique d'urgence tenu le J+1 de la détection), l'Option D a été retenue unanimement. Elle préserve la sécurité, reste conforme aux standards OAuth2/OpenID Connect, et sa mise en œuvre est estimée à 2 jours-développeur. Le Tech Lead a confirmé que le module de facturation peut lire le JWKS endpoint de Keycloak pour valider les tokens RS256 sans modification majeure.

---

## Mesures Correctives et de Mitigation

### Actions immédiates

| Action | Responsable | Délai | Statut |
|--------|-------------|-------|--------|
| Configurer le JWKS endpoint dans Keycloak | Tech Lead back | J+1 | Fait |
| Modifier le module facturation pour lire le JWKS | Dev back | J+2 | Fait |
| Tests d'intégration SSO ↔ Facturation | QA | J+3 | Fait — Passants |
| Mise à jour de la documentation d'architecture | Tech Lead | J+4 | Fait |

### Mesures préventives pour la suite

1. **Définir un ADR (Architecture Decision Record)** : documenter le choix de RS256 comme standard pour tous les futurs services qui s'intégreront au SSO
2. **Checklist d'intégration SSO** : créer une checklist technique à valider avant toute intégration d'un nouveau service avec le SSO (algorithme, JWKS, scopes, claims)
3. **Spike technique obligatoire** : pour tout nouveau composant tiers, réaliser un spike de 1 à 2 jours avant le sprint d'intégration pour identifier les incompatibilités
4. **Tests de contrat d'interface** : mettre en place des tests automatisés qui vérifient la compatibilité des tokens entre les services

### Bilan de l'incident

- **Durée de résolution :** 4 jours ouvrés (détection → tests passants)
- **Impact planning :** 0 jour de retard sur le chemin critique (résolu dans le sprint)
- **Impact budgétaire :** +2 j/h non prévus, compensés par l'avance sur la facturation
- **Leçons apprises :** La validation des contrats d'interface techniques entre composants tiers doit être réalisée en phase de spécification (M+1), pas en phase de développement

---

---

# SECTION 5.6 — MONTÉE EN COMPÉTENCES

---

## Mini Plan de Montée en Compétences

### Contexte et diagnostic

L'incident INC-2026-001 (incompatibilité SSO/JWT) et l'analyse de la rétrospective Sprint 2 ont révélé deux lacunes collectives :

1. **Sécurité des authentifications OAuth2/JWT** : méconnaissance des standards OAuth2, choix des algorithmes de signature, gestion des JWKS
2. **Gestion des dépendances inter-services** : difficulté à anticiper les incompatibilités entre composants tiers lors de la phase de spécification

### Objectifs de la montée en compétences

- Autonomiser l'équipe sur les sujets OAuth2/SSO pour la v1.1 et les projets futurs
- Réduire le risque d'incidents liés aux intégrations de composants tiers
- Partager la connaissance acquise sur le projet pour éviter les silos

### Plan d'action

| Action | Format | Participants | Durée | Calendrier |
|--------|--------|--------------|-------|-----------|
| Atelier "OAuth2 & JWT : les essentiels" | Atelier interne | Équipe dev (5 pers.) | 2h | M+4, semaine post go-live |
| RETEX incident SSO/JWT | Réunion structurée | Équipe complète (8 pers.) | 1h | M+4, J+3 du go-live |
| Revue de code thématique "sécurité SSO" | Code review collective | Tech Leads + 2 devs | 1h30 | M+4, sprint de stabilisation |
| Documentation ADR + guide d'intégration | Auto-formation + écriture | Tech Lead back | 1j | M+4 |

---

## Proposition d'Action d'Animation : Atelier "OAuth2 & JWT : les essentiels"

### Fiche atelier

**Objectif :** Que chaque développeur de l'équipe soit capable d'expliquer le fonctionnement d'OAuth2, de choisir le bon algorithme JWT, et de configurer une intégration SSO en toute autonomie.

**Format :** Atelier participatif (30 min théorie + 60 min pratique + 30 min Q&A)

**Animateur :** Référent sécurité DSI

**Programme :**

| Durée | Contenu |
|-------|---------|
| 10 min | Rappel du contexte projet : pourquoi OAuth2 et SSO sur ce projet |
| 20 min | Théorie : OAuth2 flows, JWT structure, HS256 vs RS256, JWKS |
| 30 min | Atelier pratique : configuration d'un client Keycloak et validation d'un token JWT |
| 30 min | Retour sur l'incident INC-2026-001 : ce qui s'est passé, pourquoi, comment on l'aurait évité |
| 30 min | Q&A et construction collective d'une checklist d'intégration SSO |

**Livrables produits lors de l'atelier :**
- Checklist d'intégration SSO (document partagé)
- ADR "Algorithme de signature JWT"
- Guide rapide OAuth2 pour l'équipe (1 page)

---

## RETEX — Incident INC-2026-001

### Structure du RETEX

**Méthode :** Format "Keep, Drop, Improve"

| Keep (à garder) | Drop (à abandonner) | Improve (à améliorer) |
|----------------|--------------------|-----------------------|
| La réactivité en COUTIL (réunion tenue en J+1) | Intégration de composants tiers sans spike préalable | Anticiper les contrats d'interface en phase spécification |
| La qualité de la recherche documentaire FR/EN | Hypothèse que les standards sont compatibles par défaut | Formaliser une checklist de validation technique pour chaque intégration tierce |
| La transparence dans le reporting (COPIL informé immédiatement) | | Ajouter un test de contrat d'interface dans le pipeline CI/CD |

---

## Indicateurs d'Impact

### Mesure de l'efficacité des actions de montée en compétences

| Indicateur | Méthode de mesure | Cible | Moment de mesure |
|-----------|------------------|-------|-----------------|
| **Taux de participation** aux ateliers | Présence effective | 100 % des devs | J+0 (atelier) |
| **Score de compréhension** post-atelier | QCM de 10 questions sur OAuth2/JWT | ≥ 8/10 en moyenne | J+0 (fin atelier) |
| **Nombre d'incidents liés à l'intégration SSO** en v1.1 | Tickets Jira catégorie "SSO/Auth" | 0 incident de même nature | M+8 (sprint v1.1) |
| **Utilisation de la checklist SSO** sur les prochaines intégrations | % des intégrations avec checklist complétée | 100 % | M+6 et M+8 |
| **Délai de résolution des incidents techniques** futurs | Durée moyenne de résolution (jours) | ≤ 2 jours (vs 4 jours pour INC-001) | M+8 |
| **Score de confiance équipe** sur le sujet OAuth2/SSO | Auto-évaluation (1-5) avant/après atelier | +2 points en moyenne | J+0 (avant/après) |
| **Qualité des spécifications d'intégration** | Présence de contrats d'interface dans les specs | 100 % des stories d'intégration | Backlog refinement |

### Tableau de suivi des indicateurs d'impact

| Indicateur | Avant action | Cible | Mesure M+6 | Mesure M+8 |
|-----------|:-----------:|:-----:|:---------:|:---------:|
| Incidents SSO/Auth | 1 (INC-001) | 0 | À mesurer | À mesurer |
| Délai résolution incidents | 4 jours | ≤ 2 jours | À mesurer | À mesurer |
| Score compréhension OAuth2 | 5/10 (estimé) | ≥ 8/10 | Après atelier | Réévaluation |
| Checklist SSO utilisée | 0 % | 100 % | À mesurer | À mesurer |
| Confiance équipe (1-5) | 2/5 (estimé) | ≥ 4/5 | Après atelier | Réévaluation |

---

---

# ANNEXES

---

## Annexe A — Récapitulatif des livrables

| Section | Livrable | Statut |
|---------|---------|:------:|
| Introduction | Synthèse exécutive | Complet |
| 5.1 | Note de cadrage | Complet |
| 5.1 | Proposition de gouvernance projet | Complet |
| 5.1 | Matrice RACI | Complet |
| 5.2 | WBS | Complet |
| 5.2 | Estimation des charges et hypothèses budgétaires | Complet |
| 5.2 | Planning prévisionnel avec jalons, dépendances, chemin critique | Complet |
| 5.2 | Registre des risques | Complet |
| 5.2 | Plan qualité | Complet |
| 5.3 | Justification du choix agile/hybride | Complet |
| 5.3 | Backlog structuré en épics et user stories | Complet |
| 5.3 | Critères d'acceptation | Complet |
| 5.3 | Definition of Ready | Complet |
| 5.3 | Definition of Done | Complet |
| 5.3 | Présentation des rituels de pilotage et de coordination | Complet |
| 5.3 | Tableau Kanban | Complet |
| 5.3 | Règle de gestion du WIP | Complet |
| 5.4 | Tableau de bord KPI | Complet |
| 5.4 | Seuils d'alerte et règles d'escalade | Complet |
| 5.4 | Revue d'étape structurée | Complet |
| 5.4 | Rapport synthétique d'avancement | Complet |
| 5.5 | Journal d'incident | Complet |
| 5.5 | Synthèse de la recherche documentaire FR/EN | Complet |
| 5.5 | Présentation des options et décision retenue | Complet |
| 5.5 | Mesures correctives ou de mitigation | Complet |
| 5.6 | Mini plan de montée en compétences | Complet |
| 5.6 | Proposition d'action d'animation | Complet |
| 5.6 | Indicateurs d'impact | Complet |

---

## Annexe B — Matrice de Conformité aux Attendus de Certification

| Attendu évalué | Éléments de preuve dans le dossier |
|----------------|------------------------------------|
| Cadrer un projet numérique | Contexte, enjeux, périmètre in/out, objectifs SMART, hypothèses, contraintes |
| Organiser la gouvernance | Instances COPIL/COPROJ/COUTIL, circuits de décision, circuits de validation, RACI |
| Planifier et chiffrer | WBS, charges, budget, hypothèses de chiffrage, jalons, chemin critique, dépendances |
| Identifier et maîtriser les risques | Registre des risques, mesures préventives, plans de réponse, seuils d'escalade |
| Choisir une méthode projet adaptée | Justification agile/hybride, rituels Scrum adaptés, jalons contractuels |
| Piloter l'exécution | Backlog, user stories, critères d'acceptation, DoR, DoD, Kanban, WIP |
| Suivre la performance | KPI délai, coût, qualité, risques, seuils vert/orange/rouge, rapport d'avancement |
| Résoudre un incident | Journal d'incident, analyse d'impact, recherche documentaire, options, décision, mitigation |
| Capitaliser et faire progresser l'équipe | RETEX, atelier de montée en compétences, indicateurs d'impact post-action |

---

## Annexe C — Bibliographie Synthétique

| Source | Utilisation dans le dossier |
|--------|-----------------------------|
| Keycloak Server Administration Guide — https://www.keycloak.org/docs/latest/server_admin/ | Configuration SSO, clients, tokens, algorithmes |
| Red Hat build of Keycloak Server Administration Guide — https://docs.redhat.com/en/documentation/red_hat_build_of_keycloak/26.0/html-single/server_administration_guide/ | Référence enterprise sur Keycloak et bonnes pratiques |
| Auth0 Signing Algorithms — https://auth0.com/docs/get-started/applications/signing-algorithms | Comparaison RS256/HS256 et justification sécurité |
| Auth0 RS256 vs HS256 — https://auth0.com/blog/rs256-vs-hs256-whats-the-difference/ | Analyse des avantages et risques des algorithmes JWT |
| Auth0 Navigating RS256 and JWKS — https://auth0.com/blog/navigating-rs256-and-jwks/ | Validation des tokens via clé publique/JWKS |
| OWASP JWT Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/JSON_Web_Token_for_Java_Cheat_Sheet.html | Risques de sécurité liés aux JWT et recommandations |
| RFC 7518 JSON Web Algorithms — https://www.rfc-editor.org/rfc/rfc7518 | Référence normative sur les algorithmes JWA |

---

## Annexe D — Glossaire

| Terme | Définition |
|-------|-----------|
| **SSO** | Single Sign-On — mécanisme permettant à un utilisateur de s'authentifier une seule fois pour accéder à plusieurs services |
| **JWT** | JSON Web Token — format de token d'authentification signé, utilisé dans OAuth2 |
| **OAuth2** | Protocole d'autorisation standard pour les API web |
| **RACI** | Matrice de responsabilités : Responsable, Autorité, Consulté, Informé |
| **WBS** | Work Breakdown Structure — décomposition hiérarchique des tâches du projet |
| **WIP** | Work In Progress — nombre de tâches en cours simultanément |
| **DoR** | Definition of Ready — critères qu'une story doit respecter pour entrer en sprint |
| **DoD** | Definition of Done — critères qu'une story doit respecter pour être considérée terminée |
| **UAT** | User Acceptance Testing — recette fonctionnelle par les utilisateurs finaux |
| **SPI** | Schedule Performance Index — indicateur de performance du planning (>1 = en avance) |
| **CPI** | Cost Performance Index — indicateur de performance du coût (>1 = sous budget) |
| **COPIL** | Comité de Pilotage — instance de gouvernance stratégique |
| **COPROJ** | Comité de Projet — instance de pilotage opérationnel |
| **COUTIL** | Comité Technique — instance de résolution des problèmes techniques |
| **RETEX** | Retour d'Expérience — analyse structurée d'un événement pour en tirer des leçons |
| **ADR** | Architecture Decision Record — document traçant les décisions d'architecture |
| **JWKS** | JSON Web Key Set — endpoint standard exposant les clés publiques d'un IdP |
| **IdP** | Identity Provider — fournisseur d'identité (ex : Keycloak) |
| **MoSCoW** | Méthode de priorisation : Must, Should, Could, Won't |

---

*Dossier préparé par l'équipe projet DSI — Certification Gestion de Projet Numérique — Mai 2026*
