# Installasjonsguide – Åsane Squash Streaming System

Denne guiden tar deg fra en ny eller klargjort HP Mini-PC til en strømmerigg som kan administreres eksternt og sende squashkamper til YouTube Live.

Guiden gjelder Windows-PC-en som kjører OBS Studio, Tailscale og RustDesk. Følg trinnene i rekkefølge. De detaljerte innstillingene står i de tilhørende dokumentene under `docs/`.

## Dokumentasjon

- [PC-oppsett: Windows og BIOS](./PC-OPPSETT.md)
- [Fjernstyring: Tailscale og RustDesk](./FJERNSTYRING.md)
- [OBS Studio-oppsett](./OBS-OPPSETT.md)
- [YouTube-oppsett](./YOUTUBE-OPPSETT.md)
- [Teknisk oppsett og arkitektur](../OPPSETT.md)
- [Brukerveiledning for kampdag](../BRUKERVEILEDNING.md)

## Før du begynner

Ha dette tilgjengelig:

- HP Mini-PC og strømforsyning
- Skjerm, tastatur og mus for førstegangsoppsett
- Ethernet-kabel, helst
- HDMI-dummyplugg som passer til PC-ens videoutgang
- Kamera, mikrofon og nødvendige kabler/adaptere
- Tilgang til klubbens Tailscale-nettverk
- Tilgang til klubbens RustDesk-oppsett
- Tilgang til YouTube-kanalen og YouTube Studio
- Tilgang til RankedIn-oppsettet som brukes av scoreboard-overlayet

Ikke legg passord, YouTube-strømmenøkler, gjenopprettingskoder eller andre hemmeligheter i dette GitHub-repoet.

## Installasjonsrekkefølge

### 1. Klargjør Windows og HP-PC-en

Følg [PC-OPPSETT.md](./PC-OPPSETT.md).

- [ ] Windows er installert, aktivert og oppdatert.
- [ ] HP-drivere og relevante fastvareoppdateringer er kontrollert.
- [ ] PC-en er koblet til nettverket.
- [ ] BIOS er kontrollert for oppstart etter strømbrudd.
- [ ] Hvilemodus er konfigurert for drift uten tilsyn.
- [ ] HDMI-dummypluggen gir et stabilt skrivebord.

### 2. Installer fjernstyring

Følg [FJERNSTYRING.md](./FJERNSTYRING.md).

- [ ] Tailscale er installert på strømme-PC-en.
- [ ] Strømme-PC-en og kontroll-PC-en er på samme godkjente Tailnet.
- [ ] Tailscale kan koble seg til etter omstart.
- [ ] RustDesk er installert og sikret med et sterkt passord.
- [ ] Fjernstyring fungerer fra en annen maskin.

**Ikke gå videre før fjernstyringen er testet.** Den må fungere før PC-en plasseres uten skjerm, tastatur og mus.

### 3. Installer og konfigurer OBS

Følg [OBS-OPPSETT.md](./OBS-OPPSETT.md).

- [ ] OBS Studio er installert.
- [ ] Oppløsning, FPS, encoder og bitrate er satt.
- [ ] Kamera og mikrofon vises som kilder.
- [ ] Scoreboard er lagt til som Browser Source.
- [ ] Automatisk lokal opptakslagring er deaktivert.
- [ ] OBS-scener og profil er eksportert som sikkerhetskopi.

### 4. Konfigurer YouTube Live

Følg [YOUTUBE-OPPSETT.md](./YOUTUBE-OPPSETT.md).

- [ ] Brukeren har nødvendig tilgang til klubbens YouTube-kanal.
- [ ] Direktesending er aktivert på kanalen.
- [ ] OBS er koblet til riktig YouTube-sending.
- [ ] En teststrøm er gjennomført og kontrollert.

### 5. Kontroller automatisk oppstart

Når de enkelte delene fungerer, test hva som skjer etter en vanlig omstart.

- [ ] Tailscale kobler seg til igjen.
- [ ] RustDesk kan nås uten at noen trenger å åpne programmet manuelt.
- [ ] Windows forblir våken når den skal stå klar.
- [ ] OBS kan åpnes og viser riktige kilder.
- [ ] Ingen sending starter utilsiktet.
- [ ] Du kan koble til PC-en eksternt etter omstart.

OBS kan legges i Windows' oppstartsmappe hvis det er ønskelig. Dette starter OBS etter at brukeren har logget inn, men starter ikke nødvendigvis en YouTube-sending. Automatisk Windows-innlogging innebærer en sikkerhetsmessig avveining og skal bare aktiveres etter en vurdering av fysisk tilgang og kontobeskyttelse.

## Sluttest før riggen settes i hallen

1. Start PC-en på nytt mens skjerm og nettverk er tilkoblet.
2. Kontroller at Tailscale og RustDesk fungerer.
3. Koble fra den fysiske skjermen, men la HDMI-dummypluggen stå i.
4. Koble til med RustDesk fra en annen maskin.
5. Kontroller kamera, lyd og scoreboard i OBS.
6. Gjennomfør en privat eller uoppført teststrøm, hvis kanalens oppsett tillater det.
7. Kontroller bilde, lyd, forsinkelse og YouTube-status.
8. Stopp teststrømmen på riktig måte.

Ikke trekk ut strømmen som en normal avslutningsmetode. Test av strømbrudd bør gjøres uten aktiv sending og etter at arbeidet er lagret.

## Vedlikehold

- Installer sikkerhetsoppdateringer kontrollert og test etter omstart.
- Kontroller jevnlig at fjernstyring fortsatt fungerer.
- Oppbevar passord og strømmenøkler i klubbens godkjente passordløsning, ikke i repoet.
- Eksporter OBS-profil og scenekolleksjon etter endringer.
- Oppdater dokumentasjonen når innstillinger eller utstyr endres.

Se også [BRUKERVEILEDNING.md](../BRUKERVEILEDNING.md) for rutinen på kampdag.
