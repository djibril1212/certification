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
