# mieline.be

Root-site voor alle feesten en evenementen van **Miel & Eline**.

**Live:** https://mieline.be/

## Architectuur

Dit is de GitHub Pages **user-site** (`mielkurris123.github.io`) die gemapped staat op het domein `mieline.be`. Eén landing page met links naar elk evenement, dat telkens zijn eigen project-repo heeft.

```
mielkurris123.github.io   →  mieline.be/              (deze repo, landing page)
cantus2026                →  mieline.be/cantus2026/   (project repo)
<nieuw-feestje>           →  mieline.be/<naam>/       (gewoon nieuwe repo)
```

## Een nieuw evenement toevoegen

1. Maak een nieuwe **public** repo onder `mielkurris123`, bv. `bbq2027`.
2. Zet er `index.html` in.
3. Activeer GitHub Pages (Settings → Pages → Source: `main` / root).
4. De site is automatisch live op `https://mieline.be/bbq2027/`.
5. Voeg een link toe in de `index.html` van **deze** repo zodat hij in het overzicht verschijnt.

Geen extra DNS-config nodig — alles loopt automatisch via het domein van de user-site.

## Hosting & DNS

- **Domein:** `mieline.be` (geregistreerd via Combell)
- **Nameservers:** `ns1.combell.eu`, `ns3.combell.net`, `ns4.combell.net`
- **Hosting:** GitHub Pages (gratis)

### DNS-records bij Combell

| Type | Host | Waarde | TTL |
|---|---|---|---|
| A | `@` | `185.199.108.153` | 3600 |
| A | `@` | `185.199.109.153` | 3600 |
| A | `@` | `185.199.110.153` | 3600 |
| A | `@` | `185.199.111.153` | 3600 |
| CNAME | `www` | `mielkurris123.github.io` | 3600 |

De 4 A-records zijn de load balancers van GitHub Pages — samen zorgen ze voor redundantie, load balancing en geografische routing via anycast.

Het bestand `CNAME` in deze repo (inhoud: `mieline.be`) vertelt GitHub Pages dat dit domein bij deze repo hoort. Niet verwijderen.

### HTTPS

GitHub Pages genereert automatisch een Let's Encrypt certificaat zodra DNS correct gepropageerd is. Daarna staat in **Settings → Pages** de knop **"Enforce HTTPS"** klikbaar — aanvinken.

## Lokaal draaien

```bash
python -m http.server 8000
# open http://localhost:8000
```

## Evenementen

- [Cantus Afsnee 2026](https://github.com/mielkurris123/cantus2026) — 4 juli 2026
