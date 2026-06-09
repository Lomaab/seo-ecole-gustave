# Recommandations SEO — ecole-gustave.com

**Date :** 09/06/2026
**Source :** Audit technique multi-couches + Google Search Console (01/2025 → 06/2026)
**Score actuel :** 71/100

---

## Résumé Exécutif

Le site bénéficie d'une **excellente notoriété de marque** (24K impressions/mois pour "ecole gustave", CTR 37%, pos 1.3) mais souffre de **problèmes critiques de cannibalisation** et de **faible performance sur les requêtes génériques à fort volume**.

**Potentiel immédiat :** +300 à +500 clics/mois sur les requêtes formation à fort volume (19K imp pour "formation plombier" à 1.2% CTR → 5-10% possible).

---

## Données Clés GSC

| Métrique                      | Valeur                |
| ----------------------------- | --------------------- |
| Impressions totales (18 mois) | 686 696               |
| Clics totaux                  | 26 244                |
| CTR moyen                     | 3.8%                  |
| Position moyenne              | 23.6                  |
| Trafic mobile                 | 50.6% des impressions |
| Trafic France                 | ~95%                  |

### Top Requêtes par Type

| Type              | Exemples                                      | Volume   | CTR  | Position |
| ----------------- | --------------------------------------------- | -------- | ---- | -------- |
| **Marque** 🟢     | "ecole gustave", "ecole gustave lyon"         | 24K/mois | 37%  | 1.3      |
| **Formation** 🟡  | "formation plombier", "formation electricien" | 19K/mois | 1.2% | 9.8      |
| **CAP/CFA** 🟡    | "cap plomberie", "cfa plomberie"              | 10K/mois | 1.5% | 9.9      |
| **Génériques** 🔴 | "plombier chauffagiste", "electricien"        | 7K/mois  | 0.1% | 39.9     |

---

## Plan d'Action Priorisé

### 🔴 Semaine 1 : Quick Wins (Impact Fort, Effort Faible)

#### 1.1 Meta Descriptions Manquantes — 6 pages campus

**Problème :** Les pages campus (`/campus/lyon/`, `/campus/marseille/`, etc.) n'ont pas de meta description. Google affiche un extrait aléatoire → CTR réduit.

**Action :** Ajouter une meta description unique par campus :

```
Formation [métier] à [ville] | École Gustave
Formation plombier-chauffagiste à Lyon en {durée}.
{Financement} — {rythme} — Certification RNCP.
```

**Impact attendu :** +15-30% de CTR sur les pages campus (actuellement 5.5% → ~7%)

#### 1.2 Balises Title Non-Optimisées

**Problème :** Les pages formation ont des titles trop génériques. Exemple : les 3 pages "formation plombier chauffagiste" ont des titles similaires.

**Action :** Différencier les titles par ville/spécialité :

- Page Paris : `Formation Plombier Chauffagiste à Paris | École Gustave`
- Page générique : `Formation Plombier Chauffagiste | {durée} | {certification}`

#### 1.3 Images Sans Alt (14 images) + Non-WebP (20 images)

**Problème :** Images sans texte alternatif = perte de trafic Google Images.

**Action :** Ajouter des alt texts descriptifs + Convertir en WebP.

---

### 🟡 Semaine 1-2 : Cannibalisation (Impact Fort, Effort Moyen)

#### 2.1 Cannibalisation "formation plombier chauffagiste"

**Problème :** 3 pages se battent pour les mêmes mots-clés :

| URL                                            | Impressions | Position | CTR  |
| ---------------------------------------------- | ----------- | -------- | ---- |
| `/formation-plombier-chauffagiste-paris/`      | 11 411      | 8.8      | 1.4% |
| `/formations/formation-plombier-chauffagiste/` | 2 779       | 11.8     | 0.4% |
| `/formation-plombier-chauffagiste/`            | 2 096       | 16.7     | 0.2% |

**Total cannibalisé :** ~16K impressions gaspillées (position 9-17 au lieu de top 3)

**Action :**

1. Garder **1 seule page** comme page principale (recommander `/formation-plombier-chauffagiste-paris/` car meilleure perf)
2. Ajouter des **balises canoniques** sur les 2 autres pages pointant vers la page principale
3. Rediriger (301) si les contenus se recouvrent à 100%

#### 2.2 Doublons URLs Campus

**Problème :** Deux patterns d'URL pour les mêmes campus :

| Pattern                       | Exemple                          |
| ----------------------------- | -------------------------------- |
| `/campus/lyon/`               | Position 3.4, 22 889 impressions |
| `/campus-ecole-gustave/lyon/` | Position 6.8, 20 656 impressions |

**Action :** Définir un pattern unique (recommander `/campus/lyon/` car mieux positionné) et ajouter canoniques + redirections si possible.

#### 2.3 Pages "Marque" Qui Cannibalisent l'Accueil

**Problème :** Au moins 5 pages classent pour "ecole gustave" :

| Page                     | Position | CTR pour "ecole gustave" |
| ------------------------ | -------- | ------------------------ |
| `/`                      | 1.3      | 30.6%                    |
| `/trades/plombier/`      | 1.9      | 1.8%                     |
| `/metiers-artisanat/`    | 1.9      | 1.1%                     |
| `/ecole-gustave/`        | 4.0      | 0.6%                     |
| `/campus-ecole-gustave/` | 2.1      | 0.6%                     |

**Impact :** ~300 clics/mois perdus (1.8% → 30% si redirigés vers accueil)

**Action :** Si ces pages n'ont pas besoin de classer pour "ecole gustave", ajouter un lien explicite vers l'accueil ou ajuster le contenu pour ne pas cibler la requête de marque.

---

### 🟡 Semaine 2 : Optimisation Pages Formation (Impact Moyen, Effort Moyen)

#### 3.1 Stratégie de Contenu pour Requêtes Génériques

**Problème :** Les requêtes "formation plombier" (19.8K imp, CTR 1.2%), "formation plomberie" (10.4K imp, CTR 1.1%), "formation electricien" (9.5K imp, CTR 0.5%) sont en position 9-15.

**Cause racine :** Contenu insuffisamment riche et optimisé sur les pages formations. Les pages manquent de profondeur pour Google.

**Action :**

- Page unique "formation plombier" : atteindre 1500+ mots avec sections dédiées (programme, débouchés, financement, témoignages)
- Ajouter FAQ avec balisage schéma FAQPage
- Ajouter une section "Par rapport aux autres écoles" (avec E-E-A-T)
- Utiliser le skill **seo-redaction-humanisee** pour générer le contenu

#### 3.2 Schéma LocalBusiness par Campus

**Problème :** Audit a détecté l'absence de schéma LocalBusiness pour chaque campus.

**Action :** Ajouter JSON-LD LocalBusiness par campus avec adresse, téléphone, horaires.

#### 3.3 Améliorer la Lisibilité (Flesch 19.7 → 60+)

**Problème :** Score Flesch de 19.7 (très difficile). Requêtes formation ciblent un public peu diplômé.

**Action :** Simplifier les phrases (max 20 mots), utiliser un vocabulaire courant, structurer en listes à puces.

---

### 🔵 Semaine 3 : Technique & Performance (Impact Faible à Moyen)

#### 4.1 Images : Dimensions + WebP

- 60% des images sans dimensions explicites → CLS amélioré
- 20 images en JPEG/PNG à convertir en WebP

#### 4.2 Mobile : Cibles Tactiles + Scroll Horizontal

- 4 cibles tactiles < 48px à corriger → Mobile Friendly score 71/75
- Scroll horizontal à éliminer

#### 4.3 Headers de Sécurité Manquants

- CSP, X-Frame-Options, X-Content-Type-Options, Referrer-Policy
- Ajout via Cloudflare (Firewall Rules) ou .htaccess

---

## Analyse des Requêtes Zéro-Clic

**Définition :** Requêtes pour lesquelles le site apparaît dans les résultats mais ne reçoit aucun clic.

| Requête                                   | Impressions | Position | Cause probable                |
| ----------------------------------------- | ----------- | -------- | ----------------------------- |
| `formation plomberie ecoledestravaux`     | 24 239      | 5.5      | Recherche concurrent direct   |
| `cours plomberie ecoledestravaux`         | 12 171      | 8.8      | Recherche contenu pédagogique |
| `formation plomberie lesavoirfairedeco`   | 7 728       | 5.1      | Recherche concurrent          |
| `apprendre plomberie mon-institut-du-btp` | 6 203       | 6.6      | Recherche contenu cours       |
| `formation electricite ecoledestravaux`   | 7 483       | 9.6      | Recherche concurrent          |

**Stratégie :** Ne pas cibler ces requêtes (les visiteurs cherchent un concurrent spécifique). Se concentrer sur les requêtes où l'intention correspond à l'offre.

---

## Métriques de Suivi (KPI)

| KPI                           | Actuel   | Objectif S1 | Objectif S2 | Objectif S3 |
| ----------------------------- | -------- | ----------- | ----------- | ----------- |
| Score SEO                     | 71/100   | 78/100      | 85/100      | 90/100      |
| CTR "formation plombier"      | 1.2%     | 3%          | 5%          | 8%          |
| Position "formation plombier" | 9.8      | 7           | 5           | 3           |
| Images avec alt               | 86%      | 95%         | 100%        | 100%        |
| Images WebP                   | 66%      | 80%         | 100%        | 100%        |
| Flesch score                  | 19.7     | 40          | 55          | 65          |
| Meta descriptions manquantes  | 6        | 0           | 0           | 0           |
| Pages cannibalisées           | 3 paires | 0           | 0           | 0           |

---

## Prochaines Étapes

1. Validation des redirections/canoniques proposées
2. Rédaction des meta descriptions (outil : skill seo-redaction-humanisee)
3. Consolidation des pages formation plombier chauffagiste
4. Audit de contenu des formations (qualité, longueur, E-E-A-T)
5. Suivi GSC à J+15 pour mesurer l'impact
