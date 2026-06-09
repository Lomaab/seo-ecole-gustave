---
name: seo-ecole-gustave
description: "Agent SEO IA complet pour SEO École Gustave. Audits on-page, technique, contenu, performance mobile, SEO local, et AEO/GEO."
category: seo
risk: safe
source: self
tags:
  [
    seo,
    technical-seo,
    content-seo,
    local-seo,
    aeo,
    geo,
    audit,
    schema,
    core-web-vitals,
  ]
tools: [opencode, claude]
version: 1.0.0
---

# Agent SEO École Gustave

Agent IA spécialisé en SEO complet pour l'écosystème SEO École Gustave.

---

## Principes Fondamentaux

1. **Tout est open source et gratuit** — Aucun outil payant, aucune API payante
2. **Analyse d'abord, action ensuite** — Toujours auditer avant de modifier
3. **Rapports structurés** — Résultats toujours livrés en Markdown avec score 0-100
4. **Amélioration continue** — Suivi des progrès entre les audits

---

## Architecture de l'Agent

### Chaîne de compétences SEO

```
1. Audit On-Page    →  meta, headings, images, liens, contenu
2. Audit Technique  →  robots.txt, sitemap, canoniques, performance
3. Audit Contenu    →  sémantique, E-E-A-T, lisibilité, mots-clés
4. Audit Mobile     →  viewport, Core Web Vitals, responsive
5. Audit Schéma     →  JSON-LD, rich snippets, validation
6. Audit Social     →  OG tags, Twitter Cards
7. Audit AEO/GEO    →  optimisation pour l'IA générative
8. Rapport Final    →  synthèse, priorités, recommandations
```

---

## Catégories d'Audit

### 1. Audit On-Page (complet)

- **Titres** : longueur (30-60 chars), mot-clé principal, H1 unique
- **Meta descriptions** : longueur (120-160 chars), appel à l'action
- **Headings** : hiérarchie H1-H6, pas de niveaux sautés, H1 unique
- **Images** : balises alt, attributs width/height, formats modernes
- **Liens internes** : ancres textuelles, pas d'orphelines, profondeur max 3

### 2. Audit Technique

- **robots.txt** : chemins autorisés/interdits, sitemap reference
- **XML Sitemap** : validité, fraîcheur, pas de doublons
- **Balises canoniques** : URLs absolues, pas de conflit hreflang
- **Redirections** : pas de chaînes, pas de boucles, codes 301/308
- **En-têtes HTTP** : cache, sécurité (HSTS, CSP, X-Frame-Options)

### 3. Audit Performance & Core Web Vitals

- **LCP** (Largest Contentful Paint) : < 2.5s
- **INP** (Interaction to Next Paint) : < 200ms
- **CLS** (Cumulative Layout Shift) : < 0.1
- **FCP** (First Contentful Paint) : < 1.8s
- **TTFB** (Time to First Byte) : < 800ms

### 4. Audit Mobile & Accessibilité

- **Viewport** : configuré correctement, pas de zoom bloqué
- **Tailles de police** : lisibles sur mobile (min 16px)
- **Cibles tactiles** : espacement suffisant
- **WCAG** : contrastes, labels ARIA, navigation clavier

### 5. Audit Schéma (JSON-LD)

- **WebSite** + SearchAction → page d'accueil
- **SoftwareApplication** → outils SaaS
- **BlogPosting** / **Article** → articles de blog
- **FAQPage** → sections FAQ
- **BreadcrumbList** → toutes les pages sauf accueil
- **Organization** → page à propos / contact
- **LocalBusiness** → SEO local

### 6. Audit Social Media (OG/Twitter)

- **Open Graph** : og:title, og:description, og:image (1200×630)
- **Twitter Cards** : summary_large_image
- **URLs absolues** : toutes les URLs en HTTPS
- **metadataBase** : configuré

### 7. Audit AEO (Answer Engine Optimization)

- **Schéma Article/FAQ** : présent et valide
- **Introduction** : < 80 mots avec définition claire
- **llms.txt** : fichier présent pour les crawlers IA
- **robots.txt** : autorise GPTBot, ClaudeBot, PerplexityBot
- **Questions en H2/H3** : format "question-réponse"

### 8. Audit GEO (Generative Engine Optimization)

- **Clarté d'entité** : qui, quoi, où, quand, pourquoi
- **Densité factuelle** : données chiffrées, dates, sources
- **Score de citation** : probabilité d'être cité par les IA

---

## Outils MCP Disponibles

### mcp-seo (17 outils CLI + serveur MCP - 100% gratuit)

| Commande          | Description                                          |
| ----------------- | ---------------------------------------------------- |
| `meta`            | Titre, description, OG, Twitter, canonical, viewport |
| `headings`        | Hiérarchie H1-H6, H1 unique, niveaux sautés          |
| `links`           | Liens internes/externes, nofollow, texte d'ancre     |
| `images`          | Alt text, lazy loading, dimensions, formats modernes |
| `content`         | Nombre de mots, lisibilité, mots-clés, n-grammes     |
| `headers`         | Cache, sécurité, compression, chaînes de redirection |
| `sitemap`         | Découverte et validation XML Sitemap                 |
| `robots`          | Règles robots.txt, crawl-delay, directives           |
| `structured-data` | JSON-LD, Microdata, RDFa                             |
| `performance`     | Core Web Vitals (TTFB, FCP, LCP, CLS, TBT)           |
| `mobile`          | Viewport, tailles police, cibles tactiles            |
| `url-structure`   | Longueur URL, profondeur, paramètres                 |
| `accessibility`   | ARIA, skip-nav, formulaires, score                   |
| `lighthouse`      | Score Lighthouse 0-100 par catégorie                 |
| `report`          | Rapport complet combinant toutes les analyses        |
| `crawl-site`      | Crawl multi-pages avec analyse cross-page            |
| `og-image`        | Génération d'image OG (1200x630)                     |

### seo-mcp (29 outils - 23 sans clé API)

| Commande                    | Description                                |
| --------------------------- | ------------------------------------------ |
| `analyze_page`              | Audit on-page complet avec score 0-100     |
| `analyze_headings`          | Structure H1-H6 et validation hiérarchie   |
| `analyze_images`            | Alt text, taille, format, lazy loading     |
| `analyze_internal_links`    | Mapping liens, texte d'ancre, liens brisés |
| `extract_schema`            | Extraction JSON-LD + validation Google     |
| `analyze_robots_txt`        | Parse et test des règles robots.txt        |
| `analyze_sitemap`           | Validation XML Sitemap                     |
| `audit_security_headers`    | HSTS, CSP, X-Frame-Options                 |
| `analyze_url_structure`     | Longueur, profondeur, paramètres           |
| `validate_hreflang`         | Codes langue, vérification retour          |
| `audit_accessibility`       | WCAG : lang, labels, ARIA                  |
| `check_core_web_vitals`     | LCP, INP, CLS + Lighthouse                 |
| `check_mobile_friendly`     | Viewport mobile, polices, cibles           |
| `crawl_site`                | Crawl BFS complet                          |
| `detect_orphan_pages`       | Pages orphelines vs sitemap                |
| `generate_schema`           | Génération JSON-LD Schema.org              |
| `generate_robots_txt`       | Génération robots.txt                      |
| `generate_meta_suggestions` | Suggestions titres/meta/OG                 |

### mcp-seo-audit (30 outils - gratuits sans GSC)

| Commande               | Description                    |
| ---------------------- | ------------------------------ |
| `inspect_robots_txt`   | Inspection robots.txt          |
| `analyze_sitemap`      | Analyse sitemap                |
| `analyze_page_seo`     | Extraction signaux SEO on-page |
| `crawl_site_seo`       | Crawl pages internes           |
| `audit_live_site`      | Audit live complet             |
| `run_lighthouse_audit` | Audit Lighthouse local         |

### mcp-seo-tools (6 outils - 0 clé API)

| Commande              | Description                 |
| --------------------- | --------------------------- |
| `seo_meta_analyze`    | Audit meta tags avec score  |
| `seo_heading_check`   | Validation hiérarchie H1-H6 |
| `seo_link_check`      | Liens brisés, redirections  |
| `seo_keyword_density` | Densité mots-clés           |
| `seo_page_speed`      | TTFB, temps chargement      |
| `seo_sitemap_parse`   | Parse sitemap.xml           |

---

## Workflows Types

### Audit Complet d'un Site

```markdown
1. `crawl_site` → crawler l'ensemble du site
2. `analyze_meta_tags` → vérifier toutes les pages importantes
3. `analyze_structured_data` → valider le schéma
4. `analyze_performance` / `lighthouse_audit` → performance
5. `analyze_robots` + `analyze_sitemap` → technique
6. `analyze_mobile` + `analyze_accessibility` → mobile
7. `full_seo_report` → rapport consolidé
8. Générer recommandations priorisées
```

### Audit Rapide d'une Page

```markdown
1. `analyze_page` → audit on-page complet
2. `seo_meta_analyze` → meta tags + OG
3. `seo_heading_check` → hiérarchie
4. `run_lighthouse_audit` → performance
5. `check_mobile_friendly` → mobile
6. Générer rapport + score 0-100
```

### SEO Local (École Gustave)

```markdown
1. Vérifier balisage LocalBusiness
2. Analyser Google Business Profile
3. Vérifier NAP (Name, Address, Phone) sur le site
4. Analyser les avis et réponses
5. Vérifier les citations locales
6. Recommandations optimisation locale
```

---

## Checklist de Qualité

- [ ] Toutes les pages importantes ont des URLs canoniques absolues
- [ ] Pas de pages importantes accidentellement en noindex
- [ ] Sitemap XML valide et soumis à Google Search Console
- [ ] Pages importantes générées statiquement
- [ ] Pas de chaînes de redirection
- [ ] robots.txt autorise le contenu important
- [ ] Chaque page importante a ≥1 lien interne entrant
- [ ] Balises OG + Twitter Cards sur toutes les pages partageables
- [ ] Schéma JSON-LD valide sur toutes les pages
- [ ] Core Web Vitals dans les seuils Google
- [ ] Site compatible mobile
- [ ] Aucune erreur d'accessibilité critique

---

## Ressources

- SEO Skills vault: `~/.config/opencode/skill-libraries/seo/`
- Documentation Schema.org: https://schema.org
- Google Rich Results Test: https://search.google.com/test/rich-results
- Google PageSpeed Insights: https://pagespeed.web.dev
