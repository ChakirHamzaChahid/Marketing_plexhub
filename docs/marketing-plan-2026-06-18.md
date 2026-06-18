# Plan de refonte landing PlexHubTV — 2026-06-18

> **Auteur** : refonte assistée par Claude, brief chakir.
> **Repo** : `ChakirHamzaChahid/Marketing_plexhub` (déployé sur `www.plexhubtv.uk`).
> **Source de vérité features** : `CLAUDE.md` + `COMPARE-ARVIO-2026-06-11.md` du dépôt code `PlexHubTV_new` (privé).
> **Release courante** : v1.0.26 (publiée le 2026-06-18) sur le repo public `ChakirHamzaChahid/PlexhubTV_Release`.

## 1. Diagnostic du site existant

État avant refonte (commit `e7cf74b`) :

| # | Problème | Conséquence | Sévérité |
|---|---|---|---|
| 1 | Positionnement **Plex-only** (`<title>` = « Le client Plex ultime pour Android TV ») | Aucune capture des power users **Jellyfin** (qui sont l'autre moitié de la cible), alors que l'app supporte Jellyfin nativement (`feature/jellyfin/`, `core/network/jellyfin/`, `JellyfinSourceHandler`, `JellyfinPlaybackReporter`) | **P0** |
| 2 | CTA dominant « Télécharger sur Google Play » | Mensonger : le lien va vers un APK direct, pas vers le Play Store. Viole le garde-fou « pas de promesses non tenues » | **P0** |
| 3 | Lien APK pointe vers `github.com/ChakirHamzaChahid/PlexHubTV_new/releases/download/v1.0.14/...` — repo **privé**, version **v1.0.14** | **404 pour tous les visiteurs non authentifiés**. Le repo OTA public est `PlexhubTV_Release`. La release courante est **v1.0.26** | **P0** |
| 4 | Section « Tarifs » vide (« Détails à venir ») | Aucun signal sur le modèle gratuit/donation, pas de CTA donation | **P1** |
| 5 | Features avancées livrées (Vague D) **absentes du site** : Jellyfin, Trakt sync, sous-titres IA Groq/Gemini, Skip Intro/Recap multi-providers, EPG Live TV complet, OTA self-update | Le site sous-vend gravement l'app livrée | **P1** |
| 6 | Pas de meta OG/Twitter ni de `robots.txt`/`sitemap.xml` | Partage social cassé, SEO sous-optimal | **P2** |
| 7 | Footer : « Plex est une marque déposée de Plex, Inc. » seul — pas de mention Jellyfin/MIT | Évoluera avec le repositionnement | **P2** |

## 2. Repositionnement

| Avant | Après |
|---|---|
| « Le client Plex ultime pour Android TV » | **« Plex, Jellyfin et IPTV — réunis dans une seule app Android TV »** |
| « Vos serveurs Plex. Une seule interface. » | **« Vos bibliothèques. Vos flux live. Vos profils. Une seule télécommande. »** |
| Tarifs : vide | **« Gratuit aujourd'hui. Donation premium à venir. »** |
| Téléchargement : 1 bouton APK cassé | **2 boutons APK (arm64-v8a + armeabi-v7a) vers `PlexhubTV_Release/latest` + mention « Bientôt sur Google Play »** |

## 3. Structure du nouveau site (ordre des sections)

1. **Header** (sticky, blur) — logo wordmark + nav + CTA APK
2. **Hero** — promesse multi-source + sous-titre bénéfice + CTA APK + CTA donation
3. **Pourquoi PlexHubTV** (storytelling court, 3 paragraphes) — le « pourquoi cette app existe »
4. **Sources unifiées** (NEUF) — 4 cards : Plex, Jellyfin, Xtream Codes, M3U
5. **Démo vidéo** (existant, garder le `.webm` 7,6 Mo)
6. **Fonctionnalités** (6 cards bénéfice-orientées, pas 8 — concentration)
7. **Lecteur en détail** (existant, mettre à jour : ajouter sous-titres IA + Skip Intro multi-providers + MPV fallback)
8. **Profils & contrôle parental** (existant, mettre à jour : PIN PBKDF2, isolation données par profil, mode Kids)
9. **Live TV + EPG** (NEUF, fusion de l'ancienne section IPTV + ajout EPG grille)
10. **Multi-serveur** (existant, mettre à jour pour inclure Jellyfin)
11. **Métadonnées enrichies** (existant, simplifier)
12. **Comparatif PlexHubTV vs Plex officiel vs Jellyfin officiel** (REFONDU à 3 colonnes au lieu de 2)
13. **Spécifications techniques** (mettre à jour : Media3 **1.9.0**, Room v64, Kotlin/Compose, OTA self-update)
14. **Téléchargement** — 2 boutons ABI + checksum SHA256 + alerte sideload (autorisation sources inconnues)
15. **Soutenir le projet** (NEUF, donation placeholder + remerciements open-source)
16. **Roadmap publique** (NEUF) — Bientôt Play Store, donation premium, mobile/tablet, addons communautaires
17. **FAQ** (refonte : ajouter sideload, OTA, donation, Play Store, Jellyfin)
18. **CTA final** + Footer

## 4. Copy par section (français en priorité)

### 4.1 Header
- Nav : Accueil · Fonctionnalités · Live TV · Téléchargement · Soutenir · FAQ
- CTA droit : « Télécharger » (vers `#telecharger`)

### 4.2 Hero
- **H1** : « Plex, Jellyfin et IPTV. Une seule télécommande. »
- **Sous-titre** : « PlexHubTV unifie vos serveurs Plex et Jellyfin, vos flux Xtream/M3U et votre EPG Live TV dans une interface Compose for TV pensée pour le D-pad. Gratuit, sans pub, sans télémétrie intrusive. »
- **CTA primaire** : « Télécharger l'APK » → ancre `#telecharger`
- **CTA secondaire** : « Soutenir le projet » → ancre `#soutenir`
- **Mini bandeau** : « Compatible Android TV 8.0+ · Bientôt sur Google Play »

### 4.3 Pourquoi PlexHubTV
Trois courts paragraphes :
1. **Le constat** : « Aucune app Android TV ne fait à la fois Plex, Jellyfin et IPTV correctement. Les utilisateurs multi-source jonglent entre 3 apps avec 3 historiques séparés. »
2. **La promesse** : « PlexHubTV unifie ces sources avec une vraie déduplication multi-serveur, une UI Netflix-style pensée pour la télécommande, et un lecteur double moteur (ExoPlayer + MPV) qui ne rend jamais un fichier injouable. »
3. **Le modèle** : « Gratuit, code source en architecture stricte (Clean Architecture multi-module Kotlin), distribué en sideload aujourd'hui, Play Store à venir. Une option de donation premium est prévue pour soutenir le développement. »

### 4.4 Sources unifiées (4 cards)
- **Plex Media Server** — Multi-serveur, multi-bibliothèque, déduplication intelligente, lecture des parts originales.
- **Jellyfin** — Connexion native, lecture directe, métadonnées combinées avec Plex dans la vue unifiée.
- **Xtream Codes** — VOD, séries et live, multi-comptes, EPG dédié quand disponible.
- **Playlists M3U** — Import direct, parsing optimisé, compatible IPTV grand public.

Petit texte sous les cards : « Une vue unifiée fusionne ces sources en bibliothèque unique, ou bibliothèques séparées si vous préférez. »

### 4.5 Démo vidéo
Garder la section existante avec le `.webm`. Ajuster la copy :
- **Title** : « Voyez PlexHubTV en action. »
- **Sub** : « Quelques secondes pour comprendre la navigation D-pad, le lecteur, le multi-source et le Live TV. »

### 4.6 Fonctionnalités (6 cards bénéfice-orientées)

1. **Toutes vos bibliothèques, un seul écran.** — Plex multi-serveur, Jellyfin, Xtream et M3U fusionnés. La dédup SQL par `groupKey` reconnaît qu'un même film présent sur deux serveurs n'est UN film, avec choix de la source au moment de la lecture.
2. **Lecteur double moteur, zéro fichier injouable.** — Media3/ExoPlayer 1.9.0 pour le streaming adaptatif, MPV en repli automatique pour les codecs exotiques. H.265, VP9, AV1, DTS, Atmos, ASS — tout passe.
3. **Profils familiaux avec PIN, isolation réelle des données.** — Jusqu'à 5 profils avec PIN par profil (hash PBKDF2), mode Kids avec restriction d'âge configurable, historique et favoris **scopés en base de données** — pas un simple filtre d'affichage.
4. **Skip Intro/Recap multi-providers.** — Plex chapters d'abord, puis IntroDB, AniSkip et ARM. Saute le générique, le récap et la fin automatiquement, avec préférence par profil.
5. **Sous-titres IA à la volée.** — Traduction de vos sous-titres dans la langue de votre choix via Groq Llama 3.3 70B ou Gemini 2.5 Flash. Clé API à fournir (jamais bundlée). Gère LTR/RTL.
6. **Live TV avec vraie grille EPG.** — Catégories en sidebar, channel row vertical, grille EPG horizontale now+12h, QuickZap au DPAD up/down, mini-player en haut. Le mode IPTV qui mérite son nom.

### 4.7 Téléchargement
Section dédiée avec 2 boutons :
- **Mi Box S, Fire TV Stick 4K (32 bit)** → `PlexHubTV-1.0.26-armeabi-v7a.apk`
- **Nvidia Shield, Chromecast Google TV récents (64 bit)** → `PlexHubTV-1.0.26-arm64-v8a.apk`
- Ligne dessous : « Versions signées, checksums SHA256 disponibles dans les notes de release. »
- Encart bleu/orange : « Distribution actuellement en sideload. Sur Android TV, allez dans Paramètres → Applications → Sécurité → Autoriser les sources inconnues pour l'installation. Le futur lancement Play Store dispensera de cette étape. »

### 4.8 Soutenir le projet (NEUF)
- **Title** : « Soutenir PlexHubTV »
- **Body** : « PlexHubTV est entièrement gratuit, sans publicité ni télémétrie tierce. Le projet est porté par une seule personne sur du temps personnel. Si l'app vous fait gagner du temps au quotidien, vous pouvez la soutenir financièrement. Une donation premium est en préparation : elle débloquera quelques fonctions confort (à définir avec la communauté) tout en gardant le cœur de l'app gratuit pour tous. »
- **CTA** : « Soutenir (bientôt) » — bouton désactivé visuellement avec libellé « Donation premium en préparation »
- En dessous : « En attendant, étoiler le repo public et faire connaître l'app à d'autres power users multi-source aide énormément. »

### 4.9 Roadmap publique (NEUF)
Liste de 5 jalons publics :
- **Maintenant (sideload)** — Plex multi-serveur, Jellyfin, IPTV/Xtream, Live TV EPG, profils PIN, sous-titres IA, Skip Intro, lecteur double moteur, OTA self-update.
- **Bientôt** — Donation premium (libère le développement long terme).
- **Q3 2026** — Lancement Play Store (flavor `play` déjà prêt côté code).
- **Plus tard** — Support tablette/mobile (compositionnal `LocalDeviceType` déjà étudié).
- **Idée à l'étude** — Plugins/addons façon Stremio pour sources tierces communautaires (revue sécurité préalable indispensable).

### 4.10 FAQ (refondue)
Garder l'existant + ajouter :
- « Pourquoi un sideload et pas le Play Store ? » → réponse : projet jeune, validation Play Store en cours, l'OTA self-update intégrée comble le besoin entretemps.
- « L'app collecte-t-elle mes données ? » → réponse : Sentry/Firebase Crashlytics en opt-out (toggle dans Réglages → Système → Confidentialité), aucune télémétrie tierce hors clé de votre choix pour les sous-titres IA. Pas de pub.
- « Quelle différence avec Plex officiel ? » → réponse synthétique : multi-source, dédup, MPV, profils PIN réels, IPTV, sous-titres IA, EPG, Skip Intro multi-providers, gratuit.
- « Quelle différence avec Jellyfin officiel ? » → similaire + multi-bibliothèque cross-serveur.
- « Comment fonctionne la mise à jour ? » → OTA intégrée vérifie `PlexhubTV_Release/latest`, télécharge l'APK et lance l'installateur système. Pas de magasin requis.
- « Que se passe-t-il quand la donation premium arrivera ? » → le cœur de l'app reste gratuit. Les fonctions premium seront définies avec la communauté avant déploiement.

### 4.11 Footer
- Logo + claim
- Liens : GitHub repo public (releases) · Politique de confidentialité (à créer / lier vers `docs/privacy-policy-fr.md` du repo code si déjà publié)
- Mentions :
  - « PlexHubTV est un client tiers. Plex est une marque déposée de Plex GmbH. Jellyfin est un logiciel libre sous licence GPLv2. PlexHubTV n'est pas affilié, sponsorisé ou approuvé par Plex GmbH ni par le projet Jellyfin. »
  - « Construit sur AndroidX Media3 (Apache 2.0), Jetpack Compose, MPV (libmpv), Coil 3, Hilt, Room. »
  - © 2026 PlexHubTV.

## 5. Charte visuelle (préservée)

| Élément | Valeur | Source |
|---|---|---|
| Fond principal | `#0a0a0f` | `style.css:16` |
| Fond alternatif | `#111118` | `style.css:17` |
| Accent | `#e5a00d` (Plex amber) | `style.css:22` |
| Highlight | `#ff6a3d` (orange chaud) | `style.css:26` |
| Gradient text | `linear-gradient(135deg, #e5a00d, #ff6a3d)` | `style.css:27` |
| Font | `Inter` 400-900 | `style.css:32` |
| Radius | 12 px | `style.css:28` |
| Header height | 72 px sticky blur | `style.css:31` |

→ pas de refonte de palette. Ajouts CSS confinés aux nouvelles sections (Sources, Donation, Roadmap, Download Cards).

## 6. CTA dominants & secondaires

| Position | CTA primaire | CTA secondaire |
|---|---|---|
| Hero | Télécharger l'APK (`#telecharger`) | Soutenir le projet (`#soutenir`) |
| Header (sticky) | Télécharger | — |
| Sources unifiées | (none, info) | — |
| Section Téléchargement | armeabi-v7a (32 bit) + arm64-v8a (64 bit) | « Bientôt sur Google Play » (badge désactivé) |
| Soutenir | « Donation premium en préparation » (button disabled) | « Étoiler le repo public » → lien GitHub `PlexhubTV_Release` |
| Footer | Lien releases | Privacy |

## 7. Social proof réaliste

À ce stade : **pas de chiffres inventés**. On utilisera ce qui est vérifiable :
- Badge GitHub stars du repo public (live shield via `img.shields.io`)
- Mention « Distribution OTA active : v1.0.26 publiée le 2026-06-18 »
- Pas de témoignages utilisateurs faux.

## 8. Accessibilité, perf, SEO

- Mobile-first (viewport meta déjà OK, refonte CSS responsive existante préservée).
- Pas de JS framework ni de bundler — HTML/CSS/JS vanilla pour rester < 50 KB hors vidéo et font.
- Meta OG/Twitter avec image de poster vidéo (capture frame statique à fournir plus tard).
- `robots.txt` + `sitemap.xml` à la racine.
- Lazy loading des images (le seul média lourd est le `.webm` qui a déjà `preload="metadata"`).
- `prefers-reduced-motion` respecté (déjà partiel via `transition` sans `transform` lourd dans le CSS existant).
- Pas de tracker tiers ajouté. La cible (power users) le rejette.

## 9. Garde-fous respectés

- Aucune feature inventée : tout ce qui est mentionné est traçable dans le code (chemins `feature/`, ports `domain/repository/`, services `core/network/`) ou dans `CLAUDE.md` (§5, §10.4).
- Aucune mention LBP / Storm / Firco (projet perso, totalement disjoint).
- Pas de logos Plex/Jellyfin déposés — mention textuelle sobre uniquement.
- Pas de fausse social proof.
- Pas d'annonce Play Store comme acquise : « Bientôt sur Google Play » + roadmap publique transparente.

## 10. Livrables du commit

1. `index.html` refondu
2. `style.css` enrichi (additions confinées en bas du fichier, sections nouvelles)
3. `robots.txt`
4. `sitemap.xml`
5. `docs/marketing-plan-2026-06-18.md` (ce fichier)
6. Aucun fichier média ajouté (la vidéo `Screen_recording_*.webm` existante reste utilisée).
