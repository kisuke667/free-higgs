# Changelog

## v13 — PACK VIDÉO GRATUITE (2026-10-28)
- Nouveaux providers : NovAI (vidéo gratuite `cogvideox-flash` async + retry saturation, image `cogview-3-flash`, texte `glm-4.6v-flash`), JSON2Video (`x-api-key`, ~600s offertes, MP4 par plan avec voix FR), Free.ai (texte `/v1/chat/` `qwen7b`, 30k tokens/jour), LinkModel (relais texte `kimi-k3.1-pro`)
- Fix Pollinations palier public : pas d'`Authorization` factice + URL texte corrigée (`text.pollinations.ai/openai`)
- Navigation débloquée : `1. Clés API` + étape en cours accessibles pendant une tâche (ajout de clé à chaud)
- Sauvegarde anti-perte : version allégée (sans `data:`) si quota `localStorage` dépassé
- Adaptateurs vérifiés : `node --check` + harnais mock 10/10 (novai) et 11/11 (json2video)
- Archive `versions/v12.html`, dossier `DRAGON_IVOIRE_DOSSIER.md` commité
- Testé KO (non intégrés) : Replicate 401, ArkRoute 402 sans crédits, GeneratorVideo 401, Rewind, inferenceport sans crédits, LeiaPix (presigned URL requise)

## v12 — MULTI-PROVIDER (2026-10-28)
- Consolide v11.1 (bouton ⬇ IMG unitaire sur chaque carte perso/scène/plan) et v11.2 (moteur image multi-fournisseurs backport FREE HIGGS AUTO)
- Archive `versions/v11.html` (état CINEMA STUDIO pré-multi-provider)

## v11.2 — Moteur image multi-fournisseurs (2026-10-28)
- Backport de FREE HIGGS AUTO : requêtes image par fournisseur (`imgRequest`) — Agnès, OpenAI (`oaSize`, dall-e), OpenRouter (`chat/completions` + `modalities`, refs en `image_url`), Together (`width/height`, `steps=4` pour schnell), endpoints personnalisés
- Extraction universelle (`imgFrom`) : `data[].url`, `b64_json`, `choices[].message.images[]`
- `slot()` : filtre par compatibilité image (`IMAGE_API_COMPAT`), refs limitées à Agnès/OpenRouter (`IMAGE_REF_COMPAT`), modes auto/manuel + fournisseur préféré, score d'échecs (`fimg`) et alternance fournisseurs
- `call()` : bascule automatique vers un autre fournisseur compatible en cas d'échec image (au lieu d'erreur fatale)
- Étape 1 : sélecteurs mode auto/manuel + fournisseur préféré, persistance en config

## v11.1 — IMG unitaire (2026-10-28)
- Bouton `⬇ IMG` sur chaque carte image : personnages (étape 4, IA + import), scènes (étape 5), plans (étape 6)
- Handler `dlimg` : `fetch` → `blob` → téléchargement, nom `titre-kind-id.ext` (extension selon MIME source), fallback lien direct si CORS
- Bouton grisé si aucune image sur la carte
- README à jour (table pipeline, livrables, utilisation)

## v11 — CINEMA STUDIO (2026-10-27)
- Remplace les effets décoratifs v10 par une vraie direction artistique de studio cinéma
- Hero éditorial plein cadre : slogan « Une idée. Un film. En grand. », CTA vers la configuration et affiche originale SVG (éclipse, paysage, silhouette)
- Pipeline 7 étapes en timeline visuelle, immédiatement compréhensible
- Titres de chapitre numérotés sur toutes les étapes, typographie et hiérarchie renforcées
- Responsive iPhone-first : poster recadré, pipeline scroll-snap, aucun asset externe
- Retire le marquee, le curseur et l’overlay de démarrage; conserve la palette `⌘K/Ctrl+K`
- Archive `versions/v10.html` (version précédente)

## v10 — BLUFFANT (2026-10-27)
- Écran de démarrage cinématique : logo HIGGSFREE + barre lime, sortie en fondu
- Bandeau défilant Soul Cinema sous le header (marquee lime, respect `prefers-reduced-motion`)
- Curseur personnalisé lime (point + anneau magnétique, desktop `hover:fine` uniquement)
- Cartes avec spotlight suivant la souris (`--mx/--my`, radial lime 9%)
- Apparition en cascade du contenu à chaque étape (`rise`, délais 60/120ms)
- Palette de navigation `⌘K/Ctrl+K` : saut direct aux 7 étapes, flèches + Entrée
- Toasts avec entrée animée et liseré lime, steps actifs avec glow
- Logo corrigé `HF` + `HIGGSFREE`, badge `v10` (rebrand v9 terminé)
- Archive `versions/v9.html` (état v9 HIGGSFREE pré-bluffant)

## v9 — HIGGSFIELD EDITION (2026-10-26)
- Studio noir obsidienne digne de Higgsfield : fond #060608, surfaces #111113, hairlines 7%, grain cinématographique
- Lime électrique #E8FF42 en accent principal (glow), typographies Space Grotesk + Inter + JetBrains Mono
- Header Higgsfield Studio : marque FH, badge v9 pulsant, steps en pilules, verre dépoli
- Héros éditorial : kicker avec trait lime, titres 42px display, callouts à bande latérale
- Cartes premium 18px radius, hover lift, image scale, ombres studio
- Boutons pilule Higgsfield : primaire lime sur noir, secondaire verre, interactions tactiles
- Barre de progression lime, chips pilule, console verre
- Rétrocompatibilité thème clair maintenue (.light)

## v8 (2026-10-26)
- Refonte UI complète : thème sombre par défaut, palette indigo/violet, glassmorphism, animations
- Cartes, boutons, barres de progression modernisés
- Page d'accueil avec bannière de bienvenue
- Export SRT (sous-titres), copie des dialogues et des prompts
- Thème clair/sombre inversé (toggle)

## v7 (2026-10-26)
- Nouvelle version enrichie : thème sombre, raccourcis clavier, duplication de personnages/scènes/plans
- Export Markdown et copie du synopsis
- Genres supplémentaires (Productivité, Voyage) et format 4:3
- Sessions : duplication, renommage, effacement global, liste des films récents
- Lecteur : lecture en boucle, recherche dans le projet, notes du réalisateur
- Statistiques enrichies (durée estimée)
- Aide rapide et pied de page

## v6 (2026-10-26)
- Restructuration du repo : versions dans `versions/`, README, LICENSE, .gitignore
- Meta tags SEO et Open Graph ajoutés
- Badge de version dans le header
- Documentation complète

## v5 (2026-10-25)
- Itération 5 (FREE HIGGS AUTO v5)

## v4
- Itération 4

## v3
- Itération 3

## v1 (initial)
- Première version du studio créatif IA
