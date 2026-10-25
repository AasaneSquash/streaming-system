# Brukerveiledning: Strømming av kamp (Åsane Squash)

Denne veiledningen beskriver hvordan du kobler deg til strømme-PC-en i hallen, setter opp poengtavlen (RankedIn) og starter direktesendingen på YouTube.

---

## 1. Oppstart og tilkobling til strømme-PC

Strømme-PC-en (HP Mini PC) står fastmontert i hallen uten skjerm, mus og tastatur, og skal normalt alltid stå påslått. 

### Steg 1: Koble til nettverket (Tailscale)
1. På din egen PC/Mac: Sjekk at programmet **Tailscale** kjører og står som **Connected**.
2. Hvis du ikke er logget inn, logg inn med klubbens Tailscale-konto (se eget passordark for påloggingsinfo).

### Steg 2: Fjernstyr PC-en (RustDesk)
1. Åpne programmet **RustDesk** på din egen maskin.
2. Koble til HP Mini PC-en ved å skrive inn maskinens **RustDesk-ID** eller **Tailscale IP-adresse** (f.eks. `100.x.y.z`).
3. Skriv inn det faste passordet når du blir bedt om det.
4. Du skal nå se skrivebordet på strømme-PC-en.

> **Hva hvis du ikke får kontakt med PC-en?**
> * Sjekk fysisk i hallen at HP Mini PC-en har strøm (lyser ved av/på-knappen) og at nettverkskabelen sitter i.
> * Hvis den er slått av: Trykk én gang på av/på-knappen. PC-en logger seg automatisk inn i Windows og starter Tailscale/RustDesk i løpet av 1–2 minutter.
> * Viktig: Ikke trekk ut den lille HDMI-pluggen bak på PC-en – den må stå i for at skjermbildet skal fungere via RustDesk.

---

## 2. Klargjøring av YouTube og OBS Studio

### Steg 1: Klargjør sendingen i YouTube Studio
1. Åpne nettleseren (enten på din egen PC eller på strømme-PC-en) og gå til [YouTube Studio](https://studio.youtube.com).
2. Klikk på **Opprett (Create)** øverst til høyre -> **Send direkte (Go Live)**.
3. Velg **Planlegg strøm (Schedule stream)** eller rediger eksisterende oppsett:
  - **Tittel:** F.eks. `Åsane Squash - Turnering / Bane X - [Dato]`
  - **Synlighet:** Offentlig (Public) eller Uoppført (Unlisted).
4. La YouTube Studio-vinduet stå åpent (du kan også kopiere *Strømmenøkkel / Stream Key* hvis den er endret).

### Steg 2: Åpne og sjekk OBS Studio
1. Åpne **OBS Studio** på HP Mini PC-en.
2. Sjekk at følgende kilder (Sources) er synlige og aktive:
  - **Kamera:** Du skal se et klart bilde av squashbanen.
  - **Mikrofon:** Sjekk *Audio Mixer* nederst i OBS og se at den grønne måleren beveger seg når det er lyd på banen.
  - **Scoreboard Overlay:** Poengtavlen skal ligge øverst i kildelisten over kamerabildet.

---

## 3. Oppdatere Scoreboard (`rankedin-scoreboard`)

Poengtavlen henter data direkte fra RankedIn via vårt eget oppsett ([AasaneSquash/rankedin-scoreboard](https://github.com/AasaneSquash/rankedin-scoreboard)).

1. I OBS under **Sources (Kilder)**, dobbeltklikk på **Scoreboard** (Browser Source).
2. Sjekk at **URL**-feltet peker til riktig bane-ID eller kamp-ID fra RankedIn.
3. Hvis poengtavlen ikke oppdaterer seg eller viser gammel kamp, klikk på knappen **Refresh cache of current page** nederst i innstillingsvinduet og trykk **OK**.

---

## 4. Start og avslutt strømming

### Starte strømmen
1. Klikk på **Start Streaming** nederst til høyre i OBS.
2. **VIKTIG:** Trykk **ALDRI** på *Start Recording*. PC-en har begrenset lagringsplass, og alt lagres uansett automatisk på YouTube.
3. Gå tilbake til YouTube Studio og bekreft at det står **LIVE** (det er normalt med 10–20 sekunders forsinkelse).
4. Du kan nå lukke RustDesk-vinduet på din egen maskin. Strømme-PC-en fortsetter å strømme på egen hånd.

### Avslutte strømmen
1. Når kampene for dagen er ferdige, koble deg på strømme-PC-en via RustDesk igjen.
2. Klikk på **Stop Streaming** i OBS.
3. Klikk på **Avslutt strøm (End Stream)** inne i YouTube Studio.
4. Lukk OBS Studio, men **ikke slå av strømme-
