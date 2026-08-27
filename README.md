# Sport-app

Statische website die via GitHub Pages wordt gepubliceerd.

## Structuur

```
index.html                          wachtwoordpagina, dit is de landingspagina
dashboard.html                      het Lesdag Dashboard, alleen na inloggen
.nojekyll                           schakelt Jekyll-verwerking uit
.github/workflows/deploy-pages.yml  publiceert de site automatisch
```

## Wachtwoordbeveiliging

`index.html` vraagt om een wachtwoord voordat `dashboard.html` wordt getoond.
Dit is **alleen een client-side drempel**, geen echte beveiliging: GitHub
Pages is statische hosting zonder server-side controle, dus wie de directe
URL naar `dashboard.html` kent of naar de paginabron kijkt, kan de inhoud
alsnog opvragen. Zet hier geen echt gevoelige of persoonsgebonden gegevens
in. Het wachtwoord staat niet in platte tekst in de code — `index.html`
vergelijkt een SHA-256-hash van de invoer met de opgeslagen hash.

Wachtwoord wijzigen:

1. Bepaal het nieuwe wachtwoord.
2. Genereer de hash ervan, bijvoorbeeld met:
   ```bash
   printf '%s' 'nieuw-wachtwoord' | sha256sum
   ```
3. Vervang de waarde van `PASSWORD_HASH` in `index.html` door deze hash.

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

Open vervolgens http://localhost:8000 in je browser. Let op: `crypto.subtle`
(gebruikt voor de wachtwoordcontrole) werkt alleen op `localhost` of via
https — dat werkt dus prima lokaal en op GitHub Pages zelf.
