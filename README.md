# VibeNow — landingspagina (getthevibe.now)

Statische landingspagina voor **VibeNow**. Geen build-stap, geen framework — gewoon
HTML/CSS/JS die je direct kunt hosten.

## Bestanden
De site bestaat uit **twee bestanden die bij elkaar horen**:

- **`index.html`** — de landingspagina.
- **`app-preview.html`** — interactieve telefoon-preview, die door `index.html` wordt
  ingeladen via `<iframe src="app-preview.html">`. Zonder dit bestand blijft het
  telefoonframe leeg.

## Aanmeldingen (Supabase)
Het inschrijfformulier schrijft naar de Supabase-tabel `signups` via `supabase-js`.
De **anon/public key** staat bewust in de frontend — dat is veilig: de beveiliging zit
in Row Level Security (RLS), die alleen `insert` toestaat en geen `select`. Er staat
**nooit** een `service_role`/secret key in de frontend.

## Lokaal testen
Er is geen build nodig. Start een statische server vanuit deze map:

```bash
python -m http.server 8080
# of:
npx serve .
```

Open daarna **http://localhost:8080** in je browser.

> Let op: de echte kaarttegels in de telefoon-preview vereisen internet. In een
> afgeschermde omgeving valt de kaart terug op zijn eigen tekening — dat is normaal.

## Deploy
Statische site, publish-map is de **root** (`.`). Zie `netlify.toml`. Geen build-command.
