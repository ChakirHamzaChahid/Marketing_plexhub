# Marketing_plexhub

Site marketing de **PlexHubTV** — l'app Android TV qui unifie Plex, Jellyfin et IPTV/Xtream.

Déployé sur [www.plexhubtv.uk](https://www.plexhubtv.uk) via GitHub Pages (CNAME → custom domain).

## Structure

```
.
├── index.html                          ← Landing principale (FR)
├── en/
│   └── index.html                      ← Version anglaise (assets partagés via ../)
├── style.css                           ← Design system dark + composants (partagé FR/EN)
├── robots.txt                          ← SEO
├── sitemap.xml                         ← SEO multilingue (hreflang xhtml:link)
├── CNAME                               ← www.plexhubtv.uk
├── Screen_recording_*.webm             ← Démo vidéo intégrée dans la section #demo
├── og-image.png                        ← Open Graph FR 1200×630
├── og-image-en.png                     ← Open Graph EN 1200×630
├── favicon.{ico,svg}                   ← Favicons multi-format
├── favicon-{16,32}x{16,32}.png         ← Favicons PNG
├── apple-touch-icon.png                ← iOS Safari (180×180)
├── android-chrome-{192,512}x{192,512}.png ← PWA Android
├── site.webmanifest                    ← PWA manifest
└── docs/
    ├── marketing-plan-2026-06-18.md    ← Plan de refonte de la landing (diagnostic + copy)
    └── announcements-2026-06-18.md     ← Brouillons d'annonces Reddit (r/PlexAndroidTV, r/jellyfin, etc.)
```

## Multilingue

- Architecture deux pages : `/` (FR) + `/en/` (EN), aucun framework, zéro JS de translation.
- `hreflang` réciproque + `x-default → FR` dans chaque `<head>` et dans `sitemap.xml`.
- Toggle FR|EN dans le header des deux versions, navigation par URL (pas de cookie / localStorage).
- Assets partagés (CSS, vidéo, favicon) référencés depuis `/en/` via `../path`.
- OG image dédiée par langue (`og-image.png` / `og-image-en.png`).

## Stack

HTML/CSS vanilla, zéro framework, zéro build step. Inter via Google Fonts.

## Liens utiles

- App (releases OTA, repo public) : [ChakirHamzaChahid/PlexhubTV_Release](https://github.com/ChakirHamzaChahid/PlexhubTV_Release)
- Code source de l'app : repo privé `PlexHubTV_new`

## TODO restant

- Remplacer `og-image.png` (mockup stylisé v1) par une vraie capture du Home PlexHubTV quand la dernière passe UI sera prête.
- Quand donations actives : retirer le `disabled` du bouton `#soutenir` + brancher l'URL.
- Quand Play Store live : remplacer les mentions « Bientôt sur Google Play » par le badge officiel.

© 2026 PlexHubTV.
