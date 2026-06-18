# Marketing_plexhub

Site marketing de **PlexHubTV** — l'app Android TV qui unifie Plex, Jellyfin et IPTV/Xtream.

Déployé sur [www.plexhubtv.uk](https://www.plexhubtv.uk) via GitHub Pages (CNAME → custom domain).

## Structure

```
.
├── index.html                          ← Landing principale (FR)
├── style.css                           ← Design system dark + composants
├── robots.txt                          ← SEO
├── sitemap.xml                         ← SEO
├── CNAME                               ← www.plexhubtv.uk
├── Screen_recording_*.webm             ← Démo vidéo intégrée dans la section #demo
└── docs/
    └── marketing-plan-2026-06-18.md    ← Plan de refonte de la landing (diagnostic + copy)
```

## Stack

HTML/CSS vanilla, zéro framework, zéro build step. Inter via Google Fonts.

## Liens utiles

- App (releases OTA, repo public) : [ChakirHamzaChahid/PlexhubTV_Release](https://github.com/ChakirHamzaChahid/PlexhubTV_Release)
- Code source de l'app : repo privé `PlexHubTV_new`

## TODO restant

- Créer `og-image.png` (1200×630) pour le partage social — capture maison du Home PlexHubTV avec wordmark, à placer à la racine du repo.
- Quand donations actives : retirer le `disabled` du bouton `#soutenir` + brancher l'URL.
- Quand Play Store live : remplacer les mentions « Bientôt sur Google Play » par le badge officiel.

© 2026 PlexHubTV.
