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
