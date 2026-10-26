# FREE HIGGS — Studio Créatif IA

> Studio créatif alimenté par l'IA pour générer des films, des images et des vidéos.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## Description

FREE HIGGS est une application web monopage (single-file HTML) qui utilise l'API Agnes AI pour générer :
- **Scénarios** et synopsis de films
- **Personnages** avec descriptions détaillées
- **Plans/scènes** avec prompts visuels
- **Images** générées par IA
- **Vidéos** à partir des images générées

## Fonctionnalités

- 🎬 Génération de scénarios complets (genre, synopsis, personnages, scènes)
- 🖼️ Génération d'images par IA (modèle Agnes Image 2.5 Flash)
- 🎥 Génération de vidéos (modèles Agnes Video v2.0 / v2.5 Flash)
- 📊 Suivi de progression en temps réel
- 💾 Sauvegarde locale (IndexedDB)
- 🎨 20+ genres cinématographiques (fiction, animation, expérimental, etc.)
- 📱 Interface responsive

## Versions

| Version | Fichier | Description |
|---------|---------|-------------|
| v3 | `versions/v3.html` | Itération 3 |
| v4 | `versions/v4.html` | Itération 4 |
| v5 | `versions/v5.html` | Itération 5 |
| v6 | `index.html` | Dernière version (actuelle) |

## Utilisation

1. Ouvrir `index.html` dans un navigateur moderne
2. Entrer ta clé API Agnes (https://apihub.agnes-ai.com)
3. Choisir un genre et un synopsis
4. Laisser l'IA générer le film

## Stack technique

- HTML5 / CSS3 / Vanilla JavaScript
- IndexedDB (stockage local)
- API Agnes AI (texte, image, vidéo)
- Google Fonts (Inter)

## Déploiement

Le projet est un fichier HTML statique. Il peut être déployé sur :
- **Vercel** : `vercel --prod` (après configuration)
- **Netlify** : `netlify deploy --prod`
- **GitHub Pages** : activer dans les settings du repo

## Licence

MIT

## Auteur

[@kisuke667](https://github.com/kisuke667)
