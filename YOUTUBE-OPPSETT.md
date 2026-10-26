# YouTube Live – kanal og OBS-tilkobling

Denne guiden beskriver hvordan strømme-PC-en kobles til Åsane Squash sin YouTube-kanal. Du trenger en Google-konto med riktige rettigheter til kanalen.

YouTube Studio: https://studio.youtube.com/  
YouTubes veiledning for direktesending: https://support.google.com/youtube/answer/2474026

## 1. Kontroller kanaltilgang

1. Åpne YouTube Studio.
2. Logg inn med kontoen som har tilgang til klubbens kanal.
3. Kontroller at du kan åpne **Create/Opprett → Go Live/Send direkte**.
4. Hvis du ikke har tilgang, må kanalens eier gi deg riktig tilgang. Ikke del eierens passord for å omgå dette.

Førstegangsaktivering av direktesending kan kreve ventetid. Gjør dette i god tid før en planlagt kamp.

## 2. Opprett eller planlegg sendingen

1. Åpne YouTube Studio: https://studio.youtube.com/
2. Velg **Opprett → Send direkte**.
3. Opprett en ny sending eller velg en eksisterende planlagt sending.
4. Sett en tydelig tittel, for eksempel `Åsane Squash – Bane 1 – [dato]`.
5. Velg synlighet:
   - **Offentlig (Public):** Alle kan finne og se sendingen.
   - **Uoppført (Unlisted):** Personer med lenken kan se den.
   - **Privat (Private):** Begrenset til kontoer som har fått tilgang.
6. Kontroller dato, klokkeslett og øvrige innstillinger.
7. La YouTube Studio stå tilgjengelig under testen.

Velg synlighet etter klubbens rutiner. Ikke anta at en uoppført lenke er konfidensiell hvis den deles videre.

## 3. Koble OBS til YouTube

Åpne OBS på strømme-PC-en.

1. Gå til **Settings → Stream**.
2. Velg YouTube som tjeneste hvis dette støttes av OBS-versjonen.
3. Bruk den støttede kontotilkoblingen, eller velg strømmenøkkelmetoden dersom klubbens oppsett bruker den.
4. Hvis du bruker strømmenøkkel, kopier den fra YouTube Studio og lim den inn i OBS.
5. Lagre innstillingene.

**Sikkerhet:** Strømmenøkkelen gir tilgang til å sende til kanalen/strømmen. Ikke publiser den i GitHub, dokumenter, skjermbilder eller chat. Hvis den blir eksponert, tilbakestill den i YouTube Studio og oppdater OBS.

## 4. Gjennomfør en teststrøm

Før første kamp:

1. Kontroller OBS-scenen, kamera, mikrofon og scoreboard.
2. Kontroller at riktig YouTube-sending er valgt.
3. Klikk **Start Streaming** i OBS.
4. Gå til YouTube Studio og kontroller at innkommende strøm registreres.
5. Se på forhåndsvisningen og kontroller bilde, lyd og eventuelle advarsler.
6. Hvis YouTube krever en egen bekreftelse for å starte den offentlige sendingen, følg instruksjonene i Studio.
7. Kontroller at sendingen vises med riktig tittel og synlighet.
8. Stopp teststrømmen på riktig måte.

Det kan være en kort forsinkelse før forhåndsvisningen vises. Ikke vurder strømmen som mislykket utelukkende fordi bildet ikke kommer umiddelbart.

## 5. Rutine på kampdag

1. Opprett eller åpne riktig sending i YouTube Studio.
2. Kontroller tittel, bane og synlighet.
3. Åpne OBS via RustDesk.
4. Kontroller kamera, mikrofon og scoreboard.
5. Start strømmen i OBS.
6. Bekreft i YouTube Studio at strømmen mottas og at sendingen er live.
7. Følg [BRUKERVEILEDNING.md](../BRUKERVEILEDNING.md) for resten av kampdagsrutinen.

Ikke trykk **Start Recording** i OBS. Dette systemet skal ikke lagre lokale opptak.

## 6. Avslutte sendingen

Følg klubbens etablerte rutine:

1. Koble til strømme-PC-en via RustDesk.
2. Klikk **Stop Streaming** i OBS.
3. Gå til YouTube Studio og avslutt sendingen hvis Studio viser at det kreves.
4. Kontroller at sendingen faktisk er avsluttet.

Se [BRUKERVEILEDNING.md](../BRUKERVEILEDNING.md) for full kampdagsrutine.

## 7. Feilsøking

### OBS kobler ikke til YouTube

- Kontroller internett og nettverk.
- Kontroller at riktig YouTube-tjeneste eller RTMPS-server er valgt.
- Kontroller strømmenøkkelen dersom denne metoden brukes.
- Oppdater eller tilbakestill nøkkelen hvis den er ugyldig eller eksponert.
- Kontroller YouTube Studios statusmeldinger.

### YouTube viser ingen forhåndsvisning

- Kontroller at OBS faktisk sender.
- Se etter advarsler i OBS' statusfelt.
- Vent litt og oppdater Studio.
- Kontroller at sendingen er aktiv og at riktig kanal er valgt.

### Dårlig kvalitet eller ustabil strøm

- Kontroller opplastingskapasiteten fra hallens nettverk.
- Bruk OBS-statistikk for å undersøke droppede bilder og encoder-overbelastning.
- Reduser FPS eller bitrate ved behov.
- Følg YouTubes gjeldende anbefalinger for valgt oppløsning og bildefrekvens.

## 8. Sikkerhet og tilgang

- Bruk tofaktorautentisering på Google-kontoen.
- Gi bare nødvendige kanalrettigheter til de som administrerer sendingene.
- Ikke del kontoens passord.
- Ikke lagre strømmenøkkelen i GitHub.
- Fjern tilganger som ikke lenger trengs.
