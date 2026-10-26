# PC-oppsett – Windows og HP Mini-PC

Dette dokumentet beskriver klargjøring av HP Mini-PC-en før Tailscale, RustDesk og OBS settes opp. Menyer og tilgjengelige valg varierer med HP-modell, BIOS-versjon og Windows-versjon.

## 1. Førstegangsoppsett

1. Koble til skjerm, tastatur, mus, strøm og nettverk.
2. Fullfør Windows-oppsettet.
3. Opprett en egen Windows-brukerkonto for strømmeriggen.
4. Koble til Ethernet hvis tilgjengelig.
5. Kontroller at dato, klokkeslett og tidssone er riktige.
6. Kontroller at Windows er aktivert.

Bruk en egen konto til strømmeriggen. Unngå å lagre personlige dokumenter eller bruke kontoen til vanlig privat arbeid.

## 2. Windows Update og drivere

1. Åpne **Innstillinger → Windows Update**.
2. Velg **Se etter oppdateringer**.
3. Installer tilgjengelige oppdateringer og start PC-en på nytt når det kreves.
4. Gjenta til det ikke finnes flere relevante oppdateringer.
5. Kontroller HPs støtteside for modellspesifikke drivere og BIOS-oppdateringer: https://support.hp.com/

Oppdater BIOS bare når det er nødvendig og følg HPs instruksjoner nøye. Sørg for stabil strøm under en BIOS-oppdatering.

## 3. BIOS – oppstart etter strømbrudd

Målet er at PC-en skal starte av seg selv når strømmen kommer tilbake etter et strømbrudd.

1. Start PC-en på nytt.
2. Trykk gjentatte ganger på `F10` under oppstart for å åpne HP BIOS Setup.
3. Se etter et valg med navn som **After Power Loss**, **Restore on AC Power Loss** eller tilsvarende.
4. Hvis valget finnes, sett det til **Power On**.
5. Lagre endringene og avslutt.

Navn og plassering varierer mellom modeller. Hvis valget ikke finnes, sjekk dokumentasjonen for den konkrete HP-modellen. Ikke endre andre BIOS-innstillinger uten å vite hva de gjør.

## 4. Strøm og hvilemodus

Åpne Windows' strøminnstillinger. I Windows 11 ligger disse vanligvis under **Innstillinger → System → Strøm og batteri**; på andre versjoner kan menyen hete **Strøm og hvilemodus**.

- Sett hvilemodus til **Aldri** når PC-en er koblet til strøm, dersom dette er ønsket driftsmåte.
- Kontroller innstillingene for skjermavslåing. Når PC-en brukes uten fysisk skjerm, er HDMI-dummypluggen fortsatt tilkoblet.
- Ikke deaktiver sikkerhetsoppdateringer for å unngå omstarter. Planlegg heller omstarter utenom kampdag.

## 5. Nettverk

- Bruk Ethernet når det er mulig.
- Kontroller at PC-en får tilgang til internett.
- Unngå å endre brannmur eller åpne porter på ruteren uten et konkret behov.
- Tailscale brukes senere for privat tilgang mellom godkjente enheter.

## 6. HDMI-dummyplugg og oppløsning

HDMI-dummypluggen simulerer en tilkoblet skjerm. Den skal stå i PC-en når riggen brukes uten fysisk skjerm.

1. Koble dummypluggen til en passende HDMI-utgang, eventuelt via en kompatibel adapter.
2. Åpne **Innstillinger → System → Skjerm**.
3. Velg den emulerte skjermen.
4. Velg `1920 × 1080` og `60 Hz` hvis disse valgene er tilgjengelige.
5. Kontroller senere via RustDesk at skrivebordet vises riktig.

Hvis Windows ikke viser 1920 × 1080 eller skrivebordet blir svart, kontroller dummypluggen, adapteren, grafikkdriveren og hvilken skjermutgang som brukes.

## 7. Automatisk Windows-innlogging – vurder sikkerheten

Automatisk innlogging kan gjøre at skrivebordet og programmer som starter ved brukerinnlogging, er tilgjengelige etter en omstart. Det betyr også at en person med fysisk tilgang kan få tilgang til en åpen brukerøkt.

Før automatisk innlogging eventuelt aktiveres:

- Bruk en egen konto for strømmeriggen.
- Begrens fysisk tilgang til PC-en.
- Ikke lagre private eller sensitive filer på maskinen.
- Bruk sterke passord på relevante kontoer.
- Vurder klubbens sikkerhetskrav før du lagrer eller konfigurerer innloggingsinformasjon.

Microsoft Sysinternals Autologon er dokumentert her: https://learn.microsoft.com/en-us/sysinternals/downloads/autologon

Ikke aktiver automatisk innlogging uten at klubbens ansvarlige har vurdert risikoen. `netplwiz` og tilgjengelige innloggingsvalg kan variere mellom Windows-versjoner og konfigurasjoner.

## 8. Kontroller før du går videre

- [ ] Windows er oppdatert og aktivert.
- [ ] Nettverk/internett fungerer.
- [ ] PC-en går ikke automatisk i hvilemodus.
- [ ] BIOS er kontrollert for oppstart etter strømbrudd.
- [ ] Dummypluggen er tilkoblet og gir ønsket oppløsning.
- [ ] Du har notert HP-modell og prosessor for senere feilsøking.

Fortsett med [FJERNSTYRING.md](./FJERNSTYRING.md).
