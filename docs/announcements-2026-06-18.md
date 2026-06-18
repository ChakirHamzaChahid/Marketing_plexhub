# Brouillons d'annonces — 2026-06-18 (v2.0 du site marketing)

Trois brouillons prêts à coller. **Tous évitent les logos déposés** Plex/Jellyfin (le brief le demande explicitement) et restent factuels (le code est traçable, pas de promesse Play Store comme acquise, donation présentée comme « en préparation »).

À adapter avant publication selon ton ton personnel, ta préférence FR/EN, et l'historique de chaque sub Reddit (lire les règles de chaque sub d'abord — r/PlexAndroidTV et r/Jellyfin tolèrent généralement les auto-promotions tierces tant qu'elles ne ressemblent pas à du spam).

---

## 1) r/PlexAndroidTV — version EN

**Title** : `[Sideload] PlexHubTV v1.0.26 — a multi-source Android TV client (Plex + Jellyfin + IPTV) — looking for feedback`

**Flair suggéré** : `App` ou `Discussion` (lire les flairs du sub avant de poster)

**Body** :

```
Hi r/PlexAndroidTV,

I have been building PlexHubTV for the past several months as a personal project, scratching my own itch: I run a Plex server, my partner runs a Jellyfin server, and I subscribe to a couple of IPTV providers. Jumping between three apps with three separate histories felt absurd, so I built a single Android TV client that unifies all of them.

What it does today (v1.0.26, sideload only for now):

- Multi-server Plex with SQL-level deduplication. The same movie on two of your servers is ONE movie in the unified library, with source picker at playback.
- Native Jellyfin client. Same library view, no second app.
- Xtream Codes accounts and M3U playlists, with a real EPG grid (sidebar categories, channel row, now+12h timeline, QuickZap on D-pad up/down, mini-player at the top).
- Dual playback engine: Media3 / ExoPlayer 1.9.0 + MPV as automatic fallback for exotic codecs. ass-media for ASS/SSA subs. Server transcode as last resort.
- AI subtitle translation on the fly, via Groq Llama 3.3 70B or Gemini 2.5 Flash. You bring your own API key (it's stored encrypted on your TV, never bundled).
- Skip Intro / Recap multi-providers: Plex chapters first, then IntroDB, AniSkip, ARM.
- Profiles with real PIN (PBKDF2 hashed) and database-level isolation. Kids profile with age rating. Per-profile history, watchlist, favorites, resume offset.
- Trakt sync (OAuth device flow, watchlist + history + progress + offline outbox).
- OTA self-update from the sideload flavor — first install is sideload, the rest are automatic.

Stack for the curious: Kotlin 2.2, Compose for TV, Clean Architecture multi-module, Room v64 (with materialized media_unified rebuild), Hilt, Coroutines, Coil 3. Targets Android TV 8.0+, tested daily on Mi Box S, Nvidia Shield, Chromecast with Google TV.

Free, no ads, no third-party tracking. A donation premium is being planned — the core app stays free.

Landing: https://www.plexhubtv.uk
Releases (public repo for OTA): https://github.com/ChakirHamzaChahid/PlexhubTV_Release/releases/latest

I'm not affiliated with Plex GmbH in any way. Happy to answer questions, take feedback, hear about bugs, or discuss the multi-source design choices.
```

---

## 2) r/jellyfin — version EN

**Title** : `[Android TV] PlexHubTV — a unified client that treats Jellyfin as a first-class source (not Plex-with-Jellyfin-bolted-on)`

**Flair suggéré** : `Tool` ou `Discussion`

**Body** :

```
Hi r/jellyfin,

Posting here because I want to be upfront about the framing. PlexHubTV is an Android TV client that started Plex-first but has grown into a true multi-source app, and Jellyfin is treated as a first-class source — not an afterthought.

If you run both Jellyfin and another media server (or several Jellyfin servers across friends), this might be useful:

- Native Jellyfin client. URL + token connection. Multi-server.
- Unified library where movies that exist on both your Jellyfin and a Plex / Xtream source appear as ONE entry with a source picker at playback.
- Dual playback engine: Media3 / ExoPlayer 1.9.0 + MPV automatic fallback for exotic codecs / containers. Server-side transcode kicks in as a last resort.
- AI subtitle translation (Groq or Gemini, your key). Skip Intro multi-providers. Real EPG grid for IPTV sources.
- Profiles with PIN (PBKDF2 hashed) and database-level isolation. Per-profile history, watchlist, favorites, resume — not a display filter.

Stack: Kotlin, Compose for TV, Clean Architecture, Room. Distributed as sideload via GitHub Releases (Play Store is being prepared). Free, no ads, no third-party tracking.

What I'd love feedback on specifically from this sub:
1) Anything obvious that the Jellyfin official Android TV app does that PlexHubTV doesn't yet.
2) Edge cases in the Jellyfin API I might be missing (transcoding profiles, weird subtitle codecs, live TV via Jellyfin, downloads).
3) Whether you'd actually want a unified Plex + Jellyfin view, or whether you'd prefer to keep them strictly separate.

Landing: https://www.plexhubtv.uk
Releases: https://github.com/ChakirHamzaChahid/PlexhubTV_Release/releases/latest

Not affiliated with the Jellyfin project. PlexHubTV is a third-party client.
```

---

## 3) r/iptv ou r/Smartphones (Android TV) — version EN, courte

**Title** : `PlexHubTV v1.0.26 — Android TV app that puts Plex, Jellyfin and IPTV (Xtream/M3U) in the same library, with a real EPG grid`

**Body** :

```
Built it because no Android TV client handles all three well. Free, sideload (Play Store coming).

- Real EPG grid for Xtream / M3U (sidebar categories, now+12h, QuickZap on D-pad).
- Dual engine playback (ExoPlayer + MPV fallback) so exotic codecs don't bounce you back to the home screen.
- AI subtitle translation (you bring your Groq or Gemini key).
- Profiles with PIN, multi-server unified library.

Landing: https://www.plexhubtv.uk
Direct APK (sideload, 32 / 64 bit): https://github.com/ChakirHamzaChahid/PlexhubTV_Release/releases/latest
```

---

## 4) Version FR courte — pour /r/france_android, forum HFR, Discord perso

```
PlexHubTV v1.0.26 — une app Android TV qui réunit Plex, Jellyfin et IPTV (Xtream/M3U) dans la même bibliothèque.

Pourquoi : aucune app Android TV ne fait les trois correctement. Vue unifiée multi-serveur, déduplication SQL réelle (un même film présent sur Plex et Jellyfin = UN film), lecteur double moteur (Media3 + MPV en repli), sous-titres IA (Groq ou Gemini, ta clé), grille EPG complète pour le Live TV, profils PIN avec isolation BDD.

Gratuit, sans pub. Sideload pour l'instant (Play Store en préparation).

Site : https://www.plexhubtv.uk
APK direct (32/64 bit) : https://github.com/ChakirHamzaChahid/PlexhubTV_Release/releases/latest
```

---

## Conseils de publication

- **Publier en heures pleines US (matin US ou soir UK)** pour r/PlexAndroidTV et r/jellyfin — les pics de trafic et de votes sont là.
- **Premier commentaire toi-même** avec un ou deux extras : "Quick FAQ" rappelant que tu n'es pas affilié, que c'est sideload pour l'instant, qu'il faut autoriser les sources inconnues, et que le repo des releases est public.
- **Modération** : surveiller les 2 premières heures pour répondre aux objections (sécurité du sideload, vérification SHA256, gestion des permissions Android, etc.). Une réponse honnête et rapide gagne plus de points qu'un titre racoleur.
- **Ne pas cross-poster brut** : reformule à chaque sub (les modérateurs détectent les crossposts mécaniques et flairent en spam).
- **Capture/GIF** : si tu as 15 secondes de démo (multi-source, popup source picker, EPG), poste-la en image attachée à l'OP. La conversion est nettement meilleure qu'un lien texte seul.

## Garde-fous (rappel)

- Aucune feature inventée (toutes traçables dans CLAUDE.md §5/§10.4 ou dans le code).
- Aucune mention LBP / Storm / Firco.
- Aucun logo Plex/Jellyfin déposé.
- "Bientôt sur Play Store" — jamais "disponible Play Store".
- Donation = "en préparation" — pas de promesse, pas de prix.
