# HIGGSFREE — CINEMA STUDIO · HIGGSFIELD EDITION

> **Noir obsidienne · Lime électrique · Studio brut** — digne de [Higgsfield Soul Cinema](https://higgsfield.ai).
> Studio créatif IA monopage pour générer des films complets : scénario → personnages → scènes → plans → vidéos.
> **Fork enrichi** de [CINÉ-GENESIS d'Agnes AI Film Maker](https://github.com/laurentvoanhofficiel-jpg/Agnes-ai-film-maker-Universal-one-page-HTML-4-all) par Laurent Voan Ho — réinventé en **HIGGSFIELD EDITION**.

[![Preview](https://img.shields.io/badge/Preview-HIGGSFREE-E8FF42?style=for-the-badge)](https://higgsfree-psi.vercel.app)
[![Version](https://img.shields.io/badge/version-v12_MULTI_PROVIDER-111113?style=flat-square)](CHANGELOG.md)
[![License](https://img.shields.io/badge/License-MIT-8E8E93?style=flat-square)](LICENSE)
[![Stack](https://img.shields.io/badge/stack-HTML_·_CSS_·_Vanilla_JS-0A0A0C?style=flat-square)](#stack-technique)

<p align="center">
  <img src="https://img.shields.io/badge/UI-Higgsfield_Studio-060608?style=for-the-badge" alt="Higgsfield Studio">
  <img src="https://img.shields.io/badge/Responsive-iPhone_first-22C55E?style=for-the-badge" alt="iPhone">
  <img src="https://img.shields.io/badge/Livrables-dès_étape_4-E8FF42?style=for-the-badge" alt="Livrables">
</p>

---

## ✨ Démo

**→ https://higgsfree-psi.vercel.app** — preview Vercel protégée par SSO; ouvre `index.html` pour tester en local. 100% navigateur, aucune build.

---

## 🙏 Crédits & Inspiration

**HIGGSFREE** est un **fork enrichi** de [**Agnes AI Film Maker — Universal One-Page HTML 4 All**](https://github.com/laurentvoanhofficiel-jpg/Agnes-ai-film-maker-Universal-one-page-HTML-4-all) par [**Laurent Voan Ho**](https://github.com/laurentvoanhofficiel-jpg) — projet original **CINÉ-GENESIS** (31★, 18 forks).

La base open-source (pipeline 7 étapes *Clés → Genre → Synopsis → Personnages → Scènes → Plans → Vidéos*, `IndexedDB free_higgs_v1`, polling Agnès `agnes-3.0-flash`/`agnes-image-2.5-flash`/`agnes-video-v2.0`, `RPM`, `BACK [3,6,12,24,48,96]`) est conservée et **poussée en HIGGSFIELD EDITION** : obsidienne `#060608`, lime `#E8FF42`, iPhone-first `viewport-fit=cover`, livrables dès l'étape 4 (JSON/MD/CSV/HTML/SRT), 7 adaptateurs vidéo (Higgsfield/Kling, KIE, WaveSpeed, Runware...), typographies `Space Grotesk`/`Inter`/`JetBrains Mono`.

Merci à Laurent pour l'impulsion initiale, à la communauté Agnes AI et à Higgsfield pour l'exigence visuelle.

---

## 🎬 Ce que fait HIGGSFREE

Pipeline **7 étapes** verrouillées, 100% autonome :

| Étape | Module | IA fait quoi ? | Livrable |
|-------|--------|----------------|----------|
| **1** | Clés API | Multi-fournisseurs, multi-clés (Agnès, OpenAI, Higgsfield…) | — |
| **2** | Genre & Ratio | Choix editorial (`16:9`, `9:16`, `1:1`, `4:3`) | `P.genre`, `P.ratio` |
| **3** | Synopsis | Réécriture + 10 alternatives + fusion | `P.final` |
| **4** | Personnages | Casting + costumes + portraits (référence) | Portraits + `⬇ IMG` unitaire |
| **5** | Scènes | `n` scènes (3/5/8/12) + dialogues + images de scène | **Traitement exportable** + `⬇ IMG` unitaire |
| **6** | Plans | Découpage 3-5 plans/scène + images de plan | **Découpage exportable** + `⬇ IMG` unitaire |
| **7** | Vidéos | File vidéo (Agnès, Kling, Veo, Runware, KIE…) + animatic | Vidéos + SRT |

> **Livrables extractibles dès l'étape 4** — pas besoin d'attendre les vidéos.

---

## ⚡ Fonctionnalités v11

### Direction artistique
- **Hero cinéma immersif** : composition éditoriale plein cadre et illustration SVG originale, sans image distante ni dépendance
- **Parcours visible** : pipeline 7 étapes, CTA vers la configuration, titres de chapitre numérotés
- **Accessibilité** : mise en page iPhone-first, `prefers-reduced-motion`, palette clavier `⌘K/Ctrl+K`

### Studio
- **Pipeline verrouillé** : tu valides chaque étape, l'IA n'avance pas sans toi
- **Planificateur multi-clés** : rotation, backoff `60000/RPM*1.15`, `429` → cooldown + `bad>=2` → désactivation
- **Sauvegarde locale** : IndexedDB `free_higgs_v1` + fallback `localStorage` + mémoire, autosave debounced 350ms
- **Reprise** : `poll`/`pollExternalVideo` reprennent seuls au reload

### Génération
- **Texte** : `agnes-3.0-flash`/`2.5-flash` (fallback), `chat_template_kwargs: {enable_thinking:false}`
- **Images** : `agnes-image-2.5-flash`, `size:1K`, `ratio`, `response_format:url`, refs `dataURI` via `ensureRef` + `toData` canvas 1024px
- **Images multi-fournisseurs** (backport FREE HIGGS AUTO) : requêtes dédiées OpenAI/OpenRouter (`modalities` image)/Together/custom, extraction `imgFrom` universelle, `slot()` filtré par compatibilité + refs Agnès/OpenRouter, bascule auto sur échec, modes auto/manuel + fournisseur préféré (étape 1)
- **Vidéos** : Agnès natif (`num_frames:97`, `720P`) + **7 adaptateurs directs** : Pollinations, Runware, KIE AI, WaveSpeed, Magic Hour, Higgsfield, Glif — + proxy générique

### Higgsfield-grade UI (v9)
- **Thème obsidienne** `#060608` / `#111113`, hairlines `7%`, grain cinéma, halos lime/violet
- **Accent lime** `#E8FF42` (glow), typos `Space Grotesk` (display) + `Inter` + `JetBrains Mono`
- **Header studio** : marque `HF`, badge `v11`, steps en pilules `999px`, verre dépoli `blur(16px)`
- **Hero Cinema Studio (v11)** : affiche vectorielle originale (éclipse, décor, silhouette), titre XXL, CTA direct, pipeline 7 étapes
- **Cartes premium** : `18px` radius, `hover lift + scale 1.02`, ombres studio
- **Light mode** conservé (`.light` → `#F6F5EF`)

### Mobile iPhone-first (v9.1)
- Viewport `viewport-fit=cover` + `safe-area-inset` (notch/Dynamic Island)
- Grilles `280px → 1fr` (<700px), `choice`/`grid` en 1 colonne, `mg` en 2
- Inputs `16px` sur mobile (anti-zoom iOS), boutons `44px` touch, `scale 0.98` actif
- Modal bottom-sheet `92vh`, console `52vh`, `scroll-snap` sur steps

### Productivité
- Genres : Fiction (18) + Réel (6) + Animation (5) + Expérimental (5) + Formats courts (4) + Productivité (4) + Voyage (3)
- Duplication personnages/scènes/plans, renommage/duplication sessions, notes réalisateur, recherche projet, lecture en boucle + SRT
- Raccourcis : `Espace` lecture, `Ctrl/Cmd+S` save, `Échap` quitte

### Livrables — dès l'étape 4
> Dock `⬢ LIVRABLES — prêts dès l'étape 4` présent sur **Scènes (4)**, **Plans (5)**, **Vidéos (6)** + bouton `⬇` dans le header dès `scenes.length>0`.

| Format | Contenu | Action |
|--------|---------|--------|
| **JSON** | Dossier complet `P` (genre, synopsis, chars, scènes, shots, notes) | `⬇ JSON` |
| **Markdown** | Traitement lisible `# Titre → Synopsis → Personnages → Scènes → Plans` | `⬇ Markdown` |
| **CSV** | 2 tables : `Scènes` + `PLAN,Scène,Type,Action,Camera,Chars,Who,Line` | `⬇ CSV` |
| **HTML** | Dossier livrable autonome (grilles + images `data:`) | `⬇ HTML` |
| **SRT** | Sous-titres `00:00:00,000 --> 00:00:09,000` par réplique (9s/plan) | `⬇ SRT` |
| **Copy** | Dialogues / Prompts / Synopsis dans le presse-papiers | `📋` |
| **IMG** | Image unitaire de chaque carte (perso / scène / plan), nom `titre-kind-id.ext` (png/jpg/webp selon source) | `⬇ IMG` |

---

## 🗂️ Versions

| Version | Fichier | Description |
|---------|---------|-------------|
| v3 | `versions/v3.html` | Itération 3 |
| v4 | `versions/v4.html` | Itération 4 |
| v5 | `versions/v5.html` | Itération 5 |
| v6 | `versions/v6.html` | Itération 6 — restructure repo |
| v7 | `versions/v7.html` | Enrich studio — dark mode, shortcuts, export MD, genres |
| v8 | `versions/v8.html` | Refonte indigo/violet + exports SRT |
| v9 | `versions/v9.html` | HIGGSFREE rebrand — HIGGSFIELD EDITION v9 archivée |
| v10 | `versions/v10.html` | Effets UI / palette ⌘K (archive) |
| **v12** | **`index.html`** | **MULTI-PROVIDER — moteur image OpenAI/OpenRouter/Together/custom + ⬇ IMG unitaire + modes auto/manuel (actuelle)** |
| v11 | `versions/v11.html` | CINEMA STUDIO — affiche SVG originale, hero éditorial, pipeline film, mobile-first |

Détails : voir [CHANGELOG.md](CHANGELOG.md).

---

## 🚀 Utilisation

1. Ouvre `index.html` ou va sur **https://higgsfree-psi.vercel.app** (preview protégée)
2. **Étape 1** — choisis ton fournisseur, colle ta clé (ex: `https://apihub.agnes-ai.com` + `agnes-3.0-flash`), `Enregistrer`
3. **Étape 2** — choisis genre + ratio
4. **Étape 3** — écris ton idée (2 lignes suffisent) → `✦ Analyser avec l'IA` → coche les alternatives → `Valider`
5. **Étapes 4-6** — laisse l'IA générer, retouche si besoin, **exporte dès l'étape 4** via le dock livrables ou télécharge chaque image via `⬇ IMG` sur sa carte
6. **Étape 7** — `▶ Lancer la production` → vidéos arrivent seules (file Agnès gérée : `3,6,12,24…min`), `🎬 Voir le film`

Tout est stocké dans **ce navigateur** (`Mes films` → ouvrir / dupliquer / renommer / supprimer).

---

## 🧩 Stack technique

- **Single-file HTML** — `index.html` ≈ `115KB`, zéro build, zéro dépendance
- **CSS** — Higgsfield design tokens (`--bg`, `--panel`, `--accent`), `Space Grotesk` + `Inter` + `JetBrains Mono`
- **JS** — Vanilla, `IndexedDB` (`free_higgs_v1`), `fetch` multi-provider, polling `30-60s` + backoff
- **APIs** — [Agnes AI](https://apihub.agnes-ai.com) + OpenAI-compat (Together, Groq, DeepSeek, Mistral…), vidéo : Pollinations / Runware / KIE / WaveSpeed / Magic Hour / Higgsfield / Glif
- **Fonts** — Google Fonts
- **PWA-ready** — `WakeLock`, `localStorage` fallback, `viewport-fit=cover`

---

## 📦 Déploiement

Fichier statique — déploie où tu veux :

```bash
vercel --prod
# ou
netlify deploy --prod
# ou GitHub Pages : Settings → Pages → Source: main / root
```

Vercel : `kisuke667/higgsfree` (alias mis à jour après rename).

---

## 🔑 Fournisseurs vidéo supportés

| Fournisseur | Base | Vidéo model exemple | Auth |
|-------------|------|---------------------|------|
| Agnès AI | `https://apihub.agnes-ai.com/v1` | `agnes-video-v2.0` | `Bearer` |
| Higgsfield | `https://api.higgsfield.ai` | `kling-video/v2.6/pro/text-to-video` | `Key ID:SECRET` |
| KIE AI | `https://api.kie.ai` | `kling-2.6/text-to-video` | `Bearer` |
| WaveSpeed | `https://api.wavespeed.ai/api/v3` | `bytedance/seedance-v1.5-pro/text-to-video` | `Bearer` |
| Runware | `https://api.runware.ai/v1` | `bytedance:2@2` | `Bearer` |
| Pollinations | `https://gen.pollinations.ai` | `google/veo-3.1-fast` | `?key=` |
| Magic Hour | `https://api.magichour.ai` | `default` | `Bearer` |
| Glif | `https://simple-api.glif.app` | `workflow_id` | `Bearer` |

> Ne colle jamais une clé secrète sur un site public partagé.

---

## 📄 Licence

MIT — voir [LICENSE](LICENSE). Code original © Laurent Voan Ho (CINÉ-GENESIS), modifications HIGGSFREE © kisuke667.

## 👤 Auteur

[@kisuke667](https://github.com/kisuke667) — HIGGSFREE Studio.
