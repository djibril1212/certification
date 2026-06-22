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

|  | **Forces** | **Faiblesses** |
|--|------------|----------------|
| **Opportunités** | Équipe DSI mobilisée et sponsor identifié — Demande forte des partenaires pour une expérience modernisée — Capacité à mobiliser les équipes front, back, sécurité et exploitation | Dette technique accumulée sur le portail existant — Couverture API incomplète et documentation insuffisante — Maîtrise SSO/JWT à renforcer dans l'équipe |
| **Menaces** | Amélioration visible de la qualité de service partenaire — Réduction des tâches manuelles et des coûts de maintenance — Standardisation des API et de l'authentification pour les futurs projets | Délai M+4 contraint avec faible marge de dérive — Risque de dérive de périmètre si les Should/Could sont intégrés trop tôt — Dépendances fortes entre front-end, API, facturation et SSO |

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
