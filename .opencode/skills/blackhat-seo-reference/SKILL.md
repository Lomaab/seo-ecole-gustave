---
name: blackhat-seo-reference
description: "Référence complète des techniques Black Hat SEO pour analyse défensive. Détection, prévention et correction de pratiques SEO abusives."
---

# Skill : Black Hat SEO — Référence Défensive

⚠️ **AVERTISSEMENT** : Ce skill est fourni à titre éducatif et défensif uniquement. L'objectif est de **reconnaître** et **corriger** les techniques black hat, pas de les appliquer. Google pénalise sévèrement ces pratiques.

---

## Catégorie 1 : Manipulation de Contenu

### 1.1 Content Spinning
La réécriture automatique d'articles pour éviter la détection de duplicate content.

| Technique | Niveau Risque | Détection |
|-----------|:-----------:|-----------|
| Synonyme simple | 🔴 Élevé | Très facile (synonymes visibles, phrases artificielles) |
| NLP sémantique | 🟡 Moyen | Plus difficile (phrases grammaticalement correctes) |
| Block spinning | 🟡 Moyen | Templates détectables par similarité structurelle |
| Markov chain | 🟠 Très élevé | Phrases incohérentes, non-sens |
| Translation chain | 🔴 Élevé | Traces de traduction, formulations étranges |

**Outils de détection :**
```bash
# pSEO Lint - détection clusters near-duplicate
npx pseolint <url>
```
```bash
# Vérifier la similarité cosinus entre pages
python3 -c "
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
import sys

texts = sys.argv[1:]  # Passer les textes en arguments
vectorizer = TfidfVectorizer()
tfidf = vectorizer.fit_transform(texts)
sim = cosine_similarity(tfidf[0:1], tfidf[1:])
print(f'Similarité: {sim[0][0]:.2%}')
"
```

### 1.2 Doorway Pages
Pages créées spécifiquement pour ranker sur une requête, sans valeur réelle.

**Signaux d'alerte :**
- Pages avec contenu très fin (< 200 mots)
- URLs avec paramètres de tracking agressifs
- Redirection automatique vers une autre page
- Contenu générique sans expertise
- Liens entrants uniquement depuis des PBNs

**Outil de détection : pSEO Lint**
```bash
npx pseolint https://example.com
# Vérifie les clusters de pages similaires
# SpamBrain Risk Score 0-100
```

### 1.3 Keyword Stuffing
Surcharge de mots-clés anormale.

**Seuils :**
- Densité mot-clé principal > 5% = suspect
- Densité > 8% = très probablement du stuffing
- Apparition du mot-clé dans 100% des headings = artificiel

**Vérification :**
```bash
mcp-seo content <url> | grep -i "keyword density\|keyword stuffing"
```

### 1.4 Hidden Text / Cloaking
Texte invisible ou contenu différent selon l'user-agent.

**Types :**
- `color: white` sur fond blanc
- `font-size: 0` ou `display: none`
- `position: absolute; left: -9999px`
- Contenu dans des divs superposés
- CSS media queries ciblant Googlebot

**Outil de détection :**
```python
# Comparer contenu rendu pour Googlebot vs user normal
# Utiliser Tirith ou SEO Cloaking Detector
```
```bash
git clone https://github.com/sheeki03/tirith
cd tirith && python check.py <url>
```

---

## Catégorie 2 : Manipulation de Liens

### 2.1 Private Blog Networks (PBN)
Réseaux de sites créés uniquement pour passer des backlinks.

**Signaux :**
- Même adresse IP/hébergeur pour plusieurs sites
- Patterns de whois identiques (même créateur, même date)
- Contenu pauvre, templates identiques
- Liens sortants quasi-exclusifs vers les sites cibles
- Pas de trafic organique réel

**Vérification :**
```bash
# Vérifier IP partagées
dig +short <site1.com>
dig +short <site2.com>
# Si mêmes IP → suspect

# Vérifier whois (dates création proches = suspect)
whois <site1.com> | grep -i "creation\|created"
```

### 2.2 Link Schemes
Achat/vente de liens, échanges massifs.

**Types :**
- Liens sponsorisés sans `rel="sponsored"`
- Annuaires de liens de faible qualité
- Échanges de liens (link pyramids)
- Footer links sur des réseaux de sites
- Commentaires de blog spammés

**Correction :**
```html
<!-- AJOUTER ces attributs si des liens sont sponsorisés -->
<a href="https://example.com" rel="sponsored nofollow">...</a>
<a href="https://example.com" rel="ugc nofollow">...</a>  <!-- User Generated Content -->
```

### 2.3 Negative SEO
Backlinks toxiques envoyés volontairement vers un site concurrent.

**Détection :**
- Pic soudain de backlinks de sites pornos/casinos
- Backlinks en langues étrangères pour un site local
- Ancre de lien sur-optimisée ("meilleur casino", "viagra")

**Action :**
- Google Disavow Tool (Google Search Console)
- Désavouer les domaines toxiques
- Surveiller régulièrement le profil de liens

---

## Catégorie 3 : Automatisation & Manipulation Technique

### 3.1 Auto-Generated Content
Contenu généré automatiquement sans révision humaine.

**Google Guidelines (2026) :**
- Contenu généré par scripts = spam
- Contenu AI sans révision = spam (depuis l'update Helpful Content 2024)
- Traduction automatique sans relecture = spam

**Bonnes pratiques :**
- Toujours réviser et humaniser
- Ajouter une valeur ajoutée unique à chaque page
- Minimum 300 mots de contenu original humain par page
- Marquer les pages générées avec `noindex` jusqu'à révision

### 3.2 Crawl Budget Manipulation
Forcer Google à crawler des pages spécifiques (ou éviter certaines).

**Techniques black hat :**
- Créer des sitemaps gonflés de pages sans valeur
- Cache-busting pour forcer le recrawl
- Injecter des URLs via Google Indexing API
- Link bombing interne vers des pages prioritaires

**Défense :**
- Limiter le nombre d'URLs dans le sitemap (< 1000 utiles)
- Utiliser `noindex` pour les pages sans valeur
- Configurer le crawl rate dans GSC
- Surveiller le budget de crawl

### 3.3 Indexing API Abuse
Utilisation excessive de l'Indexing API pour forcer l'indexation.

**Limites Google (2026) :**
- 200 URLs/jour pour l'Indexing API
- Usage non-légitime = ban de l'API
- Réservé aux pages avec "job posting" ou "broadcast event"

**Vérification :**
```bash
# Vérifier via GSC si beaucoup de pages "Discovered - currently not indexed"
# Signe d'un crawl budget mal utilisé
```

### 3.4 Click Fraud / Traffic Bots
Génération artificielle de trafic.

**Outils black hat :** trafficbot, Tor-based clickers
**Détection :**
- Bounce rate anormal (> 90%)
- Session duration < 2 secondes
- Trafic depuis des datacenters
- Pages vues / session très bas
- Click-through rate irréaliste

---

## Catégorie 4 : Manipulation SERP

### 4.1 Rich Result Spam
Marquage schema.org abusif pour obtenir des rich results.

**Exemples :**
- FAQPage schema sans vraies questions/réponses
- Review schema sans avis réels
- HowTo schema pour des simples listes
- Recipe schema pour des pages non-culinaires
- Product schema pour des produits indisponibles

**Détection avec les outils MCP :**
```bash
mcp-seo structured-data <url>
# Vérifier la validité et la pertinence
```

### 4.2 Clickbait Titles
Titres trompeurs pour augmenter le CTR dans les SERP.

**Signaux :**
- Mismatch entre le titre et le contenu de la page
- Titres avec points d'exclamation excessifs
- "Vous ne croirez pas..." "Incroyable..."
- Listes numérotées trompeuses

### 4.3 Google Business Profile Spam
Manipulation des fiches Google Business.

**Techniques :**
- Fausses adresses (suite, étage, sans local physique)
- Catégories d'activité non pertinentes
- Avis et notes manipulés
- Photos volées ou génériques

**Vérification :**
- Google Maps / Google Business Profile
- Cross-référencement avec d'autres annuaires
- Vérification NAP (Name, Address, Phone)

---

## Catégorie 5 : AMP & Core Web Vitals Manipulation

### 5.1 Faux Core Web Vitals
Optimisation trompeuse des métriques de performance.

**Techniques :**
- Lazy loading agressif qui cache le contenu
- Chargement différé des CSS critiques
- CLS masqué par des animations
- FCP artificiellement bas (contenu invisible)

### 5.2 AMP Abuse
Utilisation d'AMP pour forcer un positionnement.

**Depuis 2025 :** AMP n'est plus un facteur de classement direct.
**Risque :** Pages AMP avec contenu moins riche que la page canonique.

---

## Grille d'Évaluation des Risques

| Technique | Risque Google | Risque Legal | Détectabilité | Recommandation |
|-----------|:----------:|:----------:|:------------:|----------------|
| Content Spinning (NLP) | 🔴 Haut | 🟢 Aucun | 🟡 Moyenne | Utiliser pour A/B testing seulement |
| Keyword Stuffing | 🔴 Haut | 🟢 Aucun | 🟢 Facile | Ne jamais faire |
| Hidden Text | 🔴 Très Haut | 🟡 Possible | 🟢 Facile | Ne jamais faire |
| Cloaking | 🔴 Très Haut | 🟡 Possible | 🟡 Moyenne | Ne jamais faire |
| PBN Links | 🔴 Très Haut | 🟡 Possible | 🟡 Moyenne | Identifier et désavouer |
| Link Buying | 🔴 Haut | 🟢 Aucun | 🟡 Moyenne | Ne pas faire |
| Negative SEO | 🔴 Très Haut | 🔴 Légal | 🟢 Facile | Signaler à Google |
| Auto-Generated Content | 🟡 Moyen | 🟢 Aucun | 🟡 Moyenne | Toujours humaniser |
| Clickbait Titles | 🟡 Moyen | 🟢 Aucun | 🟢 Facile | Éviter, mauvaise UX |
| Fake Reviews | 🔴 Très Haut | 🔴 Légal | 🟡 Moyenne | Ne jamais faire |

---

## Processus Défensif Recommandé

1. **Auditer** avec les outils MCP (mcp-seo, seo-mcp, mcp-seo-audit)
2. **Détecter** les patterns black hat avec pSEO Lint et cloaking detectors
3. **Corriger** toutes les pratiques risquées
4. **Surveiller** GSC pour les pénalités (Manual Actions, Security Issues)
5. **Humaniser** tout contenu pour éviter les pénalités Helpful Content
6. **Rapporter** les éventuels abus à Google

### Ressources
- Google Search Central Spam Policies : https://developers.google.com/search/docs/essentials/spam-policies
- Google Search Central Blog : https://developers.google.com/search/blog
- Google Disavow Tool : https://search.google.com/search-console/disavow-links
- Outils : pSEO Lint (`npx pseolint`), Tirith (cloaking detection)
