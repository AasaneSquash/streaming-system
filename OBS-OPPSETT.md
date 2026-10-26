# OBS Studio – installasjon og konfigurasjon

OBS Studio kombinerer kamerabilde, banelyd og RankedIn-scoreboard og sender videostrømmen til YouTube Live.

Offisiell nedlasting: https://obsproject.com/download  
Windows-installasjon: https://obsproject.com/kb/windows-installation

## 1. Installer OBS Studio

1. Last ned OBS Studio fra den offisielle nettsiden.
2. Installer programmet.
3. Start OBS.
4. Hvis automatisk konfigurasjonsveiviser vises, kan den brukes som et utgangspunkt. Kontroller innstillingene nedenfor etterpå.

## 2. Video

Åpne **Settings → Video**.

| Innstilling | Startverdi |
| --- | --- |
| Base (Canvas) Resolution | `1920x1080` |
| Output (Scaled) Resolution | `1920x1080` |
| Common FPS Values | `60` eller `30` |

Bruk `30 FPS` som startpunkt hvis PC-ens kapasitet eller kameraets spesifikasjoner er ukjent. Test `60 FPS` dersom kameraet støtter det og PC-en klarer stabil koding. Kontroller at kameraet faktisk leverer ønsket oppløsning og bildefrekvens.

## 3. Output og encoder

Åpne **Settings → Output**. Velg Advanced Output Mode hvis det er nødvendig for å se alle innstillingene.

| Innstilling | 1080p30 | 1080p60 |
| --- | --- | --- |
| Rate Control | `CBR` | `CBR` |
| Video Bitrate | `6000 Kbps` | `8000–10000 Kbps` som startpunkt |
| Keyframe Interval | `2 s` | `2 s` |
| Encoder | Intel Quick Sync H.264/QSV hvis tilgjengelig | Intel Quick Sync H.264/QSV hvis tilgjengelig |

Bitrate er et utgangspunkt, ikke en garanti for riktig kvalitet eller kompatibilitet. Kontroller YouTubes gjeldende anbefalinger og test den faktiske opplastingskapasiteten. Hvis Quick Sync ikke finnes, undersøk hvilken prosessor og grafikkmaskinvare PC-en har før du velger en annen encoder.

## 4. Ikke ta opp lokalt

Åsane Squash-oppsettet skal sende direkte til YouTube uten lokal opptakslagring.

- Kontroller at **Automatically record when streaming** er deaktivert, dersom valget finnes i OBS-versjonen.
- Ikke trykk **Start Recording** på kampdag.
- Kontroller at det ikke finnes en annen automatisk opptaksregel eller planlagt oppgave som lagrer store videofiler lokalt.

## 5. Scener og kilder

Lag eller kontroller hovedscenen. Kilderekkefølgen skal være slik, fra øverst til nederst:

1. **Scoreboard** – Browser Source
2. **Kamera** – Video Capture Device
3. **Banelyd** – Audio Input Capture

Kilder høyere i listen tegnes normalt foran kilder under. Kontroller at scoreboard-overlayet dekker riktig del av kamerabildet.

### Scoreboard (Browser Source)

1. Legg til eller åpne kilden **Scoreboard**.
2. Kontroller at URL-en peker til riktig scoreboard-side og kamp-/bane-ID.
3. Sett bredde til `1920` og høyde til `1080`, dersom overlayet er laget for dette formatet.
4. Aktiver **Refresh browser when scene becomes active** hvis valget finnes og passer til oppsettet.
5. Kontroller at poengsummen oppdateres.

Scoreboard-prosjektet: https://github.com/AasaneSquash/rankedin-scoreboard

Bruk den faktiske URL-en som prosjektet krever. Ikke legg inn en eksempel-URL som om den var klubbens fungerende adresse. Se [BRUKERVEILEDNING.md](../BRUKERVEILEDNING.md) for rutinen for oppdatering av scoreboard på kampdag.

### Kamera

1. Legg til eller åpne kilden **Video Capture Device**.
2. Velg kameraet som er koblet til HP-PC-en.
3. Kontroller oppløsning, FPS og utsnitt.
4. Sørg for at hele squashbanen er synlig.
5. Lås kilden når plasseringen er riktig, for å unngå utilsiktet flytting.

### Banelyd

1. Legg til eller åpne **Audio Input Capture**.
2. Velg riktig mikrofon.
3. Spill av lyd på banen og kontroller at Audio Mixer-måleren beveger seg.
4. Lytt til teststrømmen for å kontrollere nivå og kvalitet.
5. Vurder et Limiter-filter dersom lydtopper gir forvrengning. Juster etter faktisk testing.

## 6. YouTube-tilkobling

YouTube-konfigurasjonen beskrives i [YOUTUBE-OPPSETT.md](./YOUTUBE-OPPSETT.md).

Ikke legg strømmenøkkelen i dette dokumentet, OBS-skjermbilder som deles offentlig eller GitHub. Bruk den private OBS-konfigurasjonen på strømme-PC-en.

## 7. Test før sending

- [ ] Kameraet viser hele banen.
- [ ] Scoreboard vises foran kamerabildet.
- [ ] Poengsummen oppdateres for riktig kamp.
- [ ] Mikrofonen viser signal i Audio Mixer.
- [ ] Ingen lyd forvrenges.
- [ ] OBS viser ingen vedvarende encoder-overbelastning.
- [ ] Nettverksstatusen er stabil.
- [ ] Teststrømmen ser riktig ut i YouTube Studio.
- [ ] Lokal opptakslagring er deaktivert.

## 8. Eksporter sikkerhetskopi

Etter at oppsettet er testet:

1. Bruk OBS-funksjonen for å eksportere scenekolleksjonen.
2. Eksporter profilen via OBS' profilmeny.
3. Lagre sikkerhetskopien på et godkjent sted med begrenset tilgang.
4. Kontroller filene før de deles.

Ikke legg inn passord, YouTube-strømmenøkler eller andre hemmeligheter i GitHub. Dersom eksportfilene inneholder private tilkoblingsdetaljer, må de ikke publiseres i et offentlig repo.

## 9. Feilsøking

### Svart bilde

- Kontroller at dummypluggen er tilkoblet.
- Kontroller at riktig kamera er valgt.
- Kontroller USB-/videokabel og kameraets strøm.
- Test kameraet lokalt og kontroller oppløsningen.

### Scoreboard viser gammel kamp

- Åpne scoreboard-kildens egenskaper.
- Kontroller URL og kamp-/bane-ID.
- Bruk **Refresh cache of current page** hvis knappen finnes.
- Kontroller at scoreboard-tjenesten/URL-en faktisk er tilgjengelig.

### Ingen lyd

- Kontroller valgt mikrofon i Audio Input Capture.
- Kontroller Windows' mikrofontillatelser og inngangsnivå.
- Kontroller Audio Mixer i OBS.

### Droppede bilder eller encoder-overbelastning

- Test 30 FPS.
- Reduser utgangsoppløsning midlertidig som feilsøking.
- Kontroller at maskinvareencoder brukes hvis den er tilgjengelig.
- Test nettverk og opplastingskapasitet.

Når OBS er kontrollert, fortsett med [YOUTUBE-OPPSETT.md](./YOUTUBE-OPPSETT.md).
