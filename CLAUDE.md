# CLAUDE.md

Site vitrine du projet musical **XIORAN** (noise, chiptune, LSDj, Strudel,
pédale), servi par GitHub Pages.

## Projet à part

XIORAN a sa propre identité : les pages ne renvoient pas aux autres sites de
l'utilisateur et ne reprennent ni leur code ni leur style. Être hébergé sous
le même compte GitHub ne pose pas de problème (choix de l'utilisateur,
2026-10-28) : seul le contenu reste séparé.

## Principes

- **Presque uniquement du HTML** : aucune feuille de style. Le thème sombre
  vient des attributs de `<body>` (`bgcolor="#0b0b0b" text="#a8a8a8"
  link="#e0e0e0" vlink="#7a7a7a" alink="#ffffff"`), plus
  `<meta name="color-scheme" content="dark">` pour les lecteurs audio. Mise en
  page avec `<pre>`, `<hr noshade size="1">` et `<table>`.
- **Aucun fichier audio ni aucune image dans le dépôt** : les sons et les
  pochettes sont hébergés sur l'Internet Archive et chargés directement depuis
  `https://archive.org/download/ITEM/FICHIER` (CORS ouvert).
- Lecteur : une balise `<audio controls preload="none">` par piste, avec une
  source OGG puis une source MP3 en secours. Pas d'iframe de l'Internet
  Archive (testé puis abandonné). Les métadonnées d'un item (fichiers, durées)
  se lisent sur `https://archive.org/metadata/ITEM`.
- JavaScript réduit au minimum : un petit script en bas de la page d'album
  (une seule piste à la fois, enchaînement automatique). La page doit rester
  utilisable sans JavaScript.
- Logo : « XIORAN » en ASCII art (police figlet « THIS »), en rouge `#b00000`
  dans un `<pre>` sur l'accueil.

## Arborescence

- `index.html` : accueil (logo, liste des sorties, liens).
- `ID-SORTIE/index.html` : une page par sortie (pochette, fiche, pistes).
  L'exemple actuel `lfsf-net048/` (album d'un autre artiste) ne sert qu'à la
  maquette.

## Aperçu local et déploiement

Dossier : `~/code/04-web/xioran`. Le serveur doit être lancé par
l'utilisateur, hors du sandbox : `python3 -m http.server 8765` dans ce
dossier, puis http://localhost:8765/.

Dépôt `mathematovitch/xioran`, site de projet GitHub Pages servi depuis
`main` à https://mathematovitch.github.io/xioran/ : liens internes
toujours relatifs (jamais `/…`, qui mènerait à la racine du compte). Ne jamais
committer ni pousser sans demande explicite de l'utilisateur.
