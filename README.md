# Groma

Posti, eventi, meteo e notizie di Roma in una pagina sola, da tenere sul telefono come app.

Indirizzo: https://yellow-john.github.io/groma/

## Come è fatta

- `index.html`: tutta l'app (stili, mappa, posti, metro, agenda, notizie). I posti fissi sono nell'array `PLACES`, le fonti delle notizie in `LISTEN` e `READ`.
- `data/agenda.json`: gli eventi. Li aggiorna ogni mattina il Radar, un'attività programmata di Claude.
- `data/news.json`: le notizie del giorno, aggiornate dallo stesso Radar.
- Meteo: arriva in tempo reale da [Open-Meteo](https://open-meteo.com/) (zona Basilica di San Paolo) direttamente dal browser.
- `manifest.webmanifest`, `icons/`, `sw.js`: servono a installare l'app e a farla funzionare offline. Quando cambi `index.html` aggiorna `VERSION` in `sw.js`.

## Formato dei dati

`data/agenda.json`

```json
{"updated": "2026-11-16T08:15:00+01:00", "freq": "ogni giorno", "events": [
  {"id": "2026-11-17-marlene-kuntz-monk", "t": "Titolo", "d": "2026-11-17", "e": "fine (solo se dura più giorni)",
   "h": "21:00", "c": "cinema|mercatini|fotografia|mostre|musica", "v": "luogo", "p": "nome esatto di un posto in PLACES",
   "lat": 41.9, "lng": 12.5, "u": "https://link", "s": "fonte", "n": "una o due frasi"}
]}
```

`data/news.json`

```json
{"updated": "2026-11-16T07:40:00+01:00", "items": [
  {"k": "roma|italia|mondo", "t": "titolo", "n": "riassunto breve", "u": "https://link", "s": "fonte"}
]}
```

Le notizie più vecchie di due giorni non vengono mostrate.
