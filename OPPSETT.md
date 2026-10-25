# Teknisk oppsett og arkitektur: Strømmerigg

Dette dokumentet beskriver maskinvare, fysisk kobling og programvarekonfigurasjon for strømmeriggen til Åsane Squash. Dokumentet fungerer som mal ved nyinstallasjon, feilsøking eller oppskalering til flere baner.

---

## 1. Systemarkitektur

Systemet er bygget som en «headless» strømmerigg (uten fysisk skjerm, mus eller tastatur):
1. **Lyd og bilde:** Kamera og mikrofon ved banen er koblet direkte i en lokal HP Mini PC.
2. **Prosessering:** HP Mini PC-en kjører **OBS Studio**, som kombinerer kamerafeed, mikrofon og et webbasert scoreboard-overlay ([rankedin-scoreboard](https://github.com/AasaneSquash/rankedin-scoreboard)).
3. **Distribusjon:** OBS sender videostrømmen via RTMP direkte til **YouTube Live** uten lokal mellomlagring (ingen lokal *Recording*).
4. **Administrasjon:** PC-en fjernstyres fra en annen maskin over nettverket ved hjelp av **Tailscale** (VPN) og **RustDesk** (fjernskrivebord).

---

## 2. Maskinvare og budsjett (BOM)

Oversikt over komponenter og kostnader per bane:

| Leverandør | Produkt | Stk. | Pris (NOK) | Total Pris (NOK) | Rolle i oppsettet |
| :--- | :--- | :---: | :---: | :---: | :--- |
| SDTNOVA | Kamera | 1 | 2 108,00 | 2 108,00 | Hovedkamera mot squashbanen |
| Kjell & Company | Overgangsplugg USA | 1 | 130,00 | 130,00 | Adapter for strømforsyning til kamera/utstyr |
| Sound1 | Mikrofon | 1 | 251,00 | 251,00 | Fanger opp banelyd |
| Bergen Brukt PC | HP Mini PC | 1 | 2 500,00 | 2 500,00 | Strømme-PC som kjører OBS, Tailscale og RustDesk |
| Nördic Sweden | HDMI Plugg | 1 | 180,00 | 180,00 | Dummy-plugg som simulerer tilkoblet skjerm |
| - | Hann-Hann 1/4" skrue | 1 | 66,67 | 66,67 | Overgangsskrue for kamerafeste |
| **Totalt** | | | | **5 235,67** | |

---

## 3. Fysisk montering

1. **Kamera:** Monteres med 1/4" hann-hann-skruen i vegg-/takfeste med utsyn over hele banen. Strømadapter kobles i stikkontakt via overgangsplugg (USA til EU), og signalkabel trekkes til HP Mini PC.
2. **Mikrofon:** Plasseres slik at den fanger opp lyd fra banen uten å ta opp unødig støy fra tilskuerområdet, og kobles i HP Mini PC-en.
3. **HDMI Plugg (Dummy Plug):** Plugges i HDMI-utgangen (eventuelt via DisplayPort-adapter) på HP Mini PC-en.
   * *Teknisk begrunnelse:* Uten en aktiv skjerm tilkoblet vil Windows deaktivere GPU-rendring. Dette fører til at både OBS Studio og RustDesk feiler eller viser svart skjerm ved ekstern tilkobling.
4. **Nettverk:** HP Mini PC skal være tilkoblet kablet nettverk (Ethernet) for stabil opplastingshastighet til YouTube.

---

## 4. Konfigurasjon av HP Mini PC (Windows & BIOS)

For at HP Mini PC-en skal kreve minimalt med fysisk tilsyn etter strømbrudd eller oppdateringer, må følgende settes opp:

### A. BIOS-innstillinger
- Trykk `F10` under oppstart for å gå inn i HP BIOS.
- Finn **After Power Loss** (eller *Restore on AC Power Loss*) og sett denne til **Power On**. Maskinen vil da starte automatisk så snart strømmen kommer tilbake etter et strømbrudd.

### B. Windows-innstillinger
- **Strøm og hvilemodus:** Gå til *Innstillinger -> System -> Strøm og hvilemodus*. Sett både **Skjerm** og **Hvilemodus (Sleep)** til **Aldri (Never)**.
- **HDMI Dummy Plug-oppløsning:** Sett skjermoppløsningen på den emulerte skjermen til `1920x1080` (60 Hz).
- **Automatisk innlogging (Autologon):**
  * Kjør `netplwiz` eller bruk *Microsoft Sysinternals Autologon* slik at Windows logger automatisk inn på brukerkontoen ved omstart (kritisk for at OBS og brukergrensesnittet skal være klart etter nattlige Windows-oppdateringer).

---

## 5. Oppsett av fjernstyring (Tailscale & RustDesk)

### A. Tailscale (VPN)
1. Installer Tailscale på HP Mini PC-en og logg inn på klubbens Tailnet.
2. Høyreklikk på Tailscale-ikonet i systemstatusfeltet og huk av for **Run unattended**. Dette sikrer at VPN-tunnelen kjører som en systemtjeneste i bakgrunnen selv før en Windows-bruker er logget inn.
3. Deaktiver nøkkelutløp (*Disable key expiry*) for maskinen i Tailscale Admin Console, slik at den ikke mister tilkoblingen etter 180 dager.

### B. RustDesk (Fjernskrivebord)
1. Installer RustDesk (fullversjon, ikke bare portabel, slik at systemtjenesten kjører ved oppstart).
2. Gå til *Settings -> Security -> Unlock security settings*:
   * Sett **Use permanent password** og definer et sterkt passord.
   * Under *Network*, aktiver **Enable direct IP access** (standardport 21118). Dette lar styrings-PC-en koble seg direkte til HP Mini PC-ens Tailscale IP-adresse uten å gå via eksterne relay-servere, noe som gir lavest mulig forsinkelse.

---

## 6. OBS Studio & Scoreboard-konfigurasjon

### A. Generelle innstillinger i OBS
- **Settings -> Video:**
  * *Base (Canvas) Resolution:* `1920x1080`
  * *Output (Scaled) Resolution:* `1920x1080`
  * *Common FPS Values:* `60` (eller `30`, avhengig av kameraets spesifikasjoner og CPU/GPU-belastning på HP Mini PC-en).
- **Settings -> Output (Streaming):**
  * *Video Encoder:* Velg maskinvarebasert koding (**QuickSync H.264 / QSV**) for å avlaste prosessoren på HP Mini PC-en.
  * *Rate Control:* `CBR`
  * *Bitrate:* `6000 Kbps` (for 1080p30) eller `8000–9000 Kbps` (for 1080p60).
- **Settings -> General (Output):**
  * Sørg for at **Automatically record when streaming** er **AVSLÅTT**. Ingen videofiler skal lagres lokalt på disken.

### B. Scener og Kilder (Sources)
I hovedscenen legges kildene i følgende rekkefølge (fra øverst til nederst):

1. **Scoreboard (Browser Source):**
   * *URL:* Lenke til [rankedin-scoreboard](https://github.com/AasaneSquash/rankedin-scoreboard) (lokal eller hostet URL med gjeldende bane-ID).
   * *Width:* `1920` / *Height:* `1080`
   * Huk av for **Refresh browser when scene becomes active**.
2. **Kamera (Video Capture Device):**
   * Velg tilkoblet kamera fra SDTNOVA.
   * Lås kilden (hengelås-ikonet) når utsnittet er riktig tilpasset.
3. **Banelyd (Audio Input Capture):**
   * Velg mikrofonen fra Sound1.
   * Legg gjerne på et **Limiter**-filter (f.eks. på `-3.0 dB`) under *Filters* for å unngå at lyden vrenger ved harde slag mot veggen.

### C. Backup av oppsett
Ved endringer i OBS-oppsettet skal konfigurasjonen alltid eksporteres via **Scene Collection -> Export** og **Profile -> Export**, og lagres i GitHub-repoet under en egen `obs-backup/`-mappe.
