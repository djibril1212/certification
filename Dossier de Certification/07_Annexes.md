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
