# Rapport d'Audit SEO — ecole-gustave.com

**Date :** 9 Juin 2026
**URL :** https://ecole-gustave.com
**CMS :** WordPress (Yoast SEO)
**Score Global :** 71/100 ⚠️

---

## Résumé Exécutif

Le site ecole-gustave.com a des bases SEO solides (balises de base OK, schéma présent, pas de liens brisés) mais souffre de **problèmes critiques en SEO technique, mobile, et contenu** qui freinent son positionnement.

| Catégorie | Score | Priorité |
|-----------|:-----:|:--------:|
| 🏗️ Technique & Sécurité | 55/100 | 🔴 Haute |
| 📱 Mobile & UX | 45/100 | 🔴 Haute |
| 📝 Contenu & Rédaction | 55/100 | 🔴 Haute |
| 🖼️ Images & Médias | 67/100 | 🟡 Moyenne |
| 🔗 Structure & Liens | 90/100 | 🟢 Bonne |
| 🏷️ Balises & Métadonnées | 85/100 | 🟡 Moyenne |
| 📊 Schéma & Données Structurées | 65/100 | 🟡 Moyenne |
| 📣 Social & Partage | 70/100 | 🟡 Moyenne |
| 🚀 Performance | 82/100 | 🟢 Bonne |

---

## 🔴 1. Problèmes Critiques (Action Immédiate)

### 1.1 Pages Campus sans Meta Description
**Pages concernées :** Toutes les pages /campus/ (Paris, Bordeaux, Lille, Lyon, Marseille, Rennes)
**Exemple :** `/campus/paris/` — meta description **ABSENTE**
**Impact :** Google affichera un extrait aléatoire, mauvais CTR dans les SERP
**Correctif :** Ajouter `<meta name="description">` avec 120-160 chars sur chaque page campus

### 1.2 Pas de Schema LocalBusiness
**Problème :** L'école a 6 campus physiques mais utilise seulement `Organization` (générique)
**Impact :** Pas de rich results pour les recherches locales ("école bâtiment Paris", "formation plomberie Lyon")
**Correctif :** Ajouter un schéma `LocalBusiness` pour chaque campus avec :
```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "École Gustave Paris",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Paris",
    "addressRegion": "Île-de-France"
  },
  "telephone": "...",
  "openingHours": "..."
}
```

### 1.3 OG Image surdimensionnée (Homepage)
**Problème :** `og:image` fait 2560×1551px (recommandé : 1200×630px)
**Impact :** Les réseaux sociaux recadrent l'image aléatoirement, previews moches
**Correctif :** Redimensionner à 1200×630px (ou utiliser le helper `buildSocialMetadata`)

### 1.4 Pas de Sitemap dans robots.txt
**Problème :** Le fichier robots.txt existe mais ne contient **aucune directive** Sitemap
**Impact :** Google découvre le sitemap mais lentement ; pas de crawl prioritaire
**Correctif :** Ajouter dans `/robots.txt`:
```
Sitemap: https://ecole-gustave.com/sitemap.xml
```

### 1.5 Site Non Compatible Mobile (détecté)
**Problèmes :**
- Scroll horizontal sur mobile
- 71/75 cibles tactiles < 48×48px (standard Google)
- Interstitiel (bannière cookies) intrusive
**Impact :** Google pénalise les sites non mobile-friendly depuis l'index Mobile-First
**Correctif :** 
- CSS `overflow-x: hidden` sur le body
- Agrandir les boutons/liens (min 48×48px)
- Revoir le CSS du bandeau cookies

---

## 🟡 2. Problèmes de Contenu & Rédaction

### 2.1 Lisibilité Trop Difficile
| Page | Score Flesch | Niveau |
|------|:-----------:|--------|
| Accueil | 19.7/100 | Universitaire |
| Formation Électricien | 28.0/100 | Universitaire |
| Campus Paris | ~25 (estimé) | Universitaire |

**Cible :** Flesch 50-65 (niveau lycée) pour un public d'apprenants en reconversion
**Correctif :** Phrases plus courtes (< 20 mots), vocabulaire simplifié, aérer le texte

### 2.2 Texte insuffisant sur l'Accueil
**Problème :** 783 mots, ratio texte/HTML de 7.3% (< 10% recommandé)
**Impact :** Google considère la page comme pauvre en contenu
**Correctif :** Ajouter 500-1000 mots de contenu original (témoignages, chiffres clés, valeurs)

### 2.3 Phrases Trop Longues
**Moyenne :** 30.1 mots/phrase sur l'accueil (recommandé : 15-20)
**Correctif :** Couper les phrases longues en 2-3 phrases plus digestes

### 2.4 Keywords déséquilibrés
- "formations" (1.53%) : OK
- "école" (1.4%) : OK
- "gustave" (1.15%) : correct
- "bâtiment" (0.64%) : **faible** pour le mot-clé principal du site
- "plombier", "électricien" etc : trop rares sur l'accueil

**Correctif :** 
- Augmenter la densité de "bâtiment" à 1.5%+
- Ajouter les mots-clés des métiers dès l'accueil
- Ajouter une section "Nos chiffres" avec des données (ex: "300+ apprenants formés")

---

## 🟡 3. Problèmes Techniques

### 3.1 Headers de Sécurité Manquants
| Header | Statut | Correctif |
|--------|--------|-----------|
| `X-Content-Type-Options` | ❌ Manquant | `nosniff` |
| `X-Frame-Options` | ❌ Manquant | `DENY` ou `SAMEORIGIN` |
| `Content-Security-Policy` | ❌ Manquant | À configurer |
| `Referrer-Policy` | ❌ Manquant | `strict-origin-when-cross-origin` |
| `Permissions-Policy` | ❌ Manquant | À configurer |
| `Cache-Control` | ❌ Manquant | `public, max-age=3600` |

**Correctif :** Configurer dans Cloudflare (Dashboard → Speed → Optimization)

### 3.2 HSTS max-age trop faible
**Actuel :** 16000000s (~185 jours)
**Recommandé :** 31536000s (1 an) pour HSTS Preload
**Correctif :** Modifier dans Cloudflare → Edge Certificates

### 3.3 Render-Blocking Resources
**Problème :** 3 ressources bloquent le rendu (CSS/JS)
**Impact :** Ralentit l'affichage du contenu visible
**Correctif :** 
- Inline les CSS critiques
- `defer` ou `async` sur les JS non-critiques
- Reporter le CSS des polices/icons

### 3.4 Serveur : Cloudflare (bon)
- **SSL :** ✅ OK
- **HTTP/2 :** ✅ Supporté (h3, alt-svc)
- **Compression :** ✅ gzip actif

---

## 🟡 4. Images & Médias

### 4.1 14 Images sans Alt Text (42%)
**Exemples :** Photos des formations (couvreur, électricien, maintenance, menuiserie) sans alt
**Impact :** Accessibilité (WCAG échoué), perte de contexte SEO
**Correctif :** Ajouter des alt text descriptifs :
```html
alt="Apprenti en formation couverture-zinguerie sur le campus Paris"
```

### 4.2 20 Images au Format Obsolète (61%)
**Problème :** 11 JPG + 9 PNG = formats lourds
**Solution :** Convertir en WebP (perte ~25-50% du poids) ou AVIF
**Outil recommandé :**
```bash
mcp-seo images <url>
# Puis convertir avec sharp/cwebp
```

### 4.3 13 Images sans Dimensions Explicites
**Impact :** CLS (Cumulative Layout Shift) — Google pénalise
**Correctif :** Ajouter `width` et `height` sur toutes les balises `<img>`

---

## 🟡 5. Schéma & Données Structurées

### 5.1 Schéma Présent mais Incomplet
✅ WebSite (avec SearchAction)
✅ Organization (avec logo + réseaux sociaux)
✅ WebPage
✅ BreadcrumbList

❌ **LocalBusiness** — MANQUANT (6 campus physiques !)
❌ **Course** — MANQUANT (pour les formations)
❌ **EducationalOccupationalCredential** — MANQUANT (titres RNCP)
❌ **FAQPage** — MANQUANT (section FAQ présente mais non balisée)
❌ **Product/SoftwareApplication** — MANQUANT (si formations payantes)

### 5.2 Correctifs Schéma Prioritaires
1. **LocalBusiness** pour chaque campus → Rich Results locaux
2. **Course** pour chaque formation → Affichage enrichi dans les SERP formations
3. **FAQPage** pour la section FAQ → Rich Results "Questions fréquentes"
4. **EducationalOccupationalCredential** pour les titres RNCP → Crédibilité

---

## 🟡 6. Problèmes de Structure

### 6.1 Titres Dupliqués (9 occurrences)
Les headings suivants apparaissent en double (version desktop + mobile) :
- "Les campus" ×3
- "Électricité" ×2
- "Plomberie-Chauffage" ×2
- "Maintenance CVC" ×3
- "Couverture-Zinguerie" ×3

**Correctif :** Les sections dupliquées pour responsive devraient avoir `aria-hidden="true"` sur la version cachée, ou utiliser `display: none` CSS proprement

### 6.2 Liens sans Texte d'Ancre
**Pages concernées :** Icônes réseaux sociaux (LinkedIn, Instagram, TikTok, Facebook)
**Impact :** Perte de pertinence SEO pour ces liens
**Correctif :** Ajouter `aria-label` :
```html
<a href="https://linkedin.com/..." aria-label="LinkedIn École Gustave">
```

---

## 🟢 7. Points Positifs (À Conserver)

✅ **Yoast SEO** bien configuré (title, description, OG, Twitter)
✅ **Canoniques** auto-référencées sur toutes les pages
✅ **Aucun lien brisé** (0/114)
✅ **Structure de headings** hiérarchique correcte (1 H1)
✅ **Core Web Vitals** bons (LCP 1.2s, CLS 0.0003, TBT 0ms)
✅ **TTFB** bon (552ms)
✅ **Images lazy loadées** (31/33)
✅ **Attributs srcset** présents (26/33)
✅ **Favicon** présente
✅ **Cloudflare** (SSL, CDN, H3)
✅ **Google Analytics** (via Site Kit)
✅ **HubSpot** intégré
✅ **Complianz** GDPR (cookies consent)
✅ **EcoIndex** présent (mention développement durable)

---

## 📋 Plan d'Action Priorisé

### 🔴 Semaine 1 — Correctifs Critiques
| # | Action | Page | Impact | Effort |
|---|--------|------|:------:|:------:|
| 1 | Ajouter meta descriptions aux 6 pages campus | /campus/* | 🔴 Haut | 🟢 10min |
| 2 | Ajouter Sitemap dans robots.txt | /robots.txt | 🔴 Haut | 🟢 2min |
| 3 | Redimensionner OG image à 1200×630 | Accueil | 🔴 Haut | 🟢 5min |
| 4 | Corriger scroll horizontal mobile | Global CSS | 🔴 Haut | 🟢 15min |
| 5 | Augmenter cibles tactiles à 48×48px min | Global CSS | 🔴 Haut | 🟡 30min |
| 6 | Ajouter X-Content-Type-Options + X-Frame-Options | Cloudflare | 🔴 Haut | 🟢 5min |

### 🟡 Semaine 2 — Contenu & Images
| # | Action | Page | Impact | Effort |
|---|--------|------|:------:|:------:|
| 7 | Ajouter 500-1000 mots sur l'accueil | Accueil | 🟡 Haut | 🟡 1h |
| 8 | Simplifier la rédaction (Flesch > 40) | Toutes | 🟡 Haut | 🟡 2h |
| 9 | Ajouter LocalBusiness schema (×6 campus) | /campus/* | 🟡 Haut | 🟡 1h |
| 10 | Ajouter Course schema aux formations | /formations/* | 🟡 Haut | 🟡 1h |
| 11 | Ajouter FAQPage schema | Accueil | 🟡 Moyen | 🟡 30min |
| 12 | Convertir JPG/PNG en WebP | Global | 🟡 Haut | 🟡 1h |
| 13 | Ajouter alt text aux 14 images manquantes | Global | 🟡 Moyen | 🟢 15min |
| 14 | Ajouter dimensions aux 13 images | Global | 🟡 Moyen | 🟡 30min |

### 🟢 Semaine 3 — Optimisation
| # | Action | Page | Impact | Effort |
|---|--------|------|:------:|:------:|
| 15 | Ajouter aria-label aux icônes sociales | Footer | 🟢 Faible | 🟢 10min |
| 16 | Corriger headings dupliqués | Accueil | 🟢 Faible | 🟡 30min |
| 17 | Réduire render-blocking resources | Global | 🟡 Moyen | 🟡 1h |
| 18 | Ajouter Cache-Control header | Cloudflare | 🟡 Moyen | 🟢 5min |
| 19 | Augmenter HSTS à 31536000s | Cloudflare | 🟢 Faible | 🟢 2min |
| 20 | Ajouter Referrer-Policy | Cloudflare | 🟢 Faible | 🟢 2min |

---

## 📊 Estimation d'Impact Global

| Métrique | Avant | Après (estimé) | Gain |
|----------|:-----:|:--------------:|:----:|
| Score SEO | 71/100 | 90/100 | +19 pts |
| Mobile Friendly | ❌ Non | ✅ Oui | Passage index mobile |
| Pages indexées | ~150 | ~185 | +20% |
| Trafic organique | Réf. | +40-80% | ×1.5-1.8 |
| CTR (clics) | Moyen | ✅ Optimisé | +15-25% |
| Core Web Vitals | ✅ Bons | ✅ Excellents | Maintien |
| Rich Results | Breadcrumb | +LocalBusiness+Course+FAQ | ×4 |

---

*Rapport généré avec SEO École Gustave Agent — Outils : mcp-seo, @autom8minds/seo-mcp, @rog0x/mcp-seo-tools*
