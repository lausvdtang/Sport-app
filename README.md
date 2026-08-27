# Sport-app

Statische website die via GitHub Pages wordt gepubliceerd.

## Structuur

```
index.html                        de pagina die bezoekers zien
assets/                           css, javascript, afbeeldingen
.nojekyll                         schakelt Jekyll-verwerking uit
.github/workflows/deploy-pages.yml  publiceert de site automatisch
```

## Publiceren

De site wordt gebouwd door GitHub Actions bij elke push naar `main`.
Eenmalig instellen:

1. Ga naar **Settings → Pages** in deze repository.
2. Zet bij **Build and deployment** de bron (*Source*) op **GitHub Actions**.

Daarna verschijnt de site op `https://lausvdtang.github.io/Sport-app/`.
Een nieuwe deploy kun je ook handmatig starten via het tabblad **Actions →
Deploy to GitHub Pages → Run workflow**.

## Lokaal bekijken

```bash
python3 -m http.server 8000
```

Open vervolgens http://localhost:8000 in je browser.

## Let op bij paden

De site staat in een submap (`/Sport-app/`), niet op de root van het domein.
Gebruik daarom relatieve paden in je HTML — `assets/css/style.css` werkt,
`/assets/css/style.css` niet.
