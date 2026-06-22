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
