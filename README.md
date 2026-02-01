# VoirDrama Stremio Addon (Perso)

Addon Stremio (catalogue + metadata + streams) basé sur le scraping de `voirdrama.org` et le SDK officiel.

## Pré-requis
- Node.js >= 18

## Lancer en local
```bash
npm start
```

Le manifest sera disponible ici :
```
http://localhost:7000/manifest.json
```

Dans Stremio :
- Addons → Community Addons → coller l’URL du manifest.

## Notes importantes
- Usage personnel uniquement. Vérifie que tu as le droit d’accéder aux contenus.
- Le resolveur Vidmoly tente d’extraire une URL directe (mp4/m3u8). En fallback, `externalUrl`.
- Le scraping peut casser si le site change sa structure.

## Structure
- `server.js` : serveur HTTP + scraping
- `package.json` : scripts

## Débogage rapide
- Ouvre `/catalog/series/voirdrama-ongoing.json` pour les en cours.
- Ouvre `/catalog/series/voirdrama-recent.json` pour les récents.
- Ouvre `/catalog/series/voirdrama-search.json?search=judge` pour la recherche dédiée.
- Ouvre `/meta/series/voirdrama:the-judge-returns.json` pour la fiche.
- Ouvre `/stream/series/voirdrama:the-judge-returns:the-judge-returns-05-vostfr.json` pour les lecteurs.

## Pagination
Stremio envoie `skip` dans le catalogue. L’addon mappe `skip` sur `/drama/page/{n}/` (pages de 10 éléments).
