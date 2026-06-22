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
│ US-S01 (13pts) │ US-B01 (8pts)  │ US-A01 (8pts)    │ US-F02 (5pts)  │ US-F01 ✓    │
│ US-F03 (8pts)  │ US-S02 (8pts)  │ US-S04 (5pts)    │ US-A03 (5pts)  │ US-A02 ✓    │
│ US-F04 (5pts)  │ US-A04 (3pts)  │ US-B03 (8pts)    │                │ US-B02 ✓    │
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
