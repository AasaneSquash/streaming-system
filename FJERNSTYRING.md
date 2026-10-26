# Fjernstyring – Tailscale og RustDesk

Tailscale gir strømme-PC-en en privat nettverkstilkobling til godkjente enheter. RustDesk brukes til å se og styre Windows-skrivebordet.

## 1. Installer Tailscale

Offisiell nedlasting for Windows: https://tailscale.com/download/windows

1. Last ned og installer Tailscale på HP Mini-PC-en.
2. Åpne Tailscale og logg inn med klubbens eksisterende konto/Tailnet.
3. Ikke opprett et nytt Tailnet hvis klubben allerede har et.
4. Installer Tailscale på kontroll-PC-en du skal bruke.
5. Logg inn på samme Tailnet med en konto som har tillatelse til å nå strømme-PC-en.
6. Kontroller at begge enhetene vises som tilkoblet.

Dokumentasjon: https://tailscale.com/docs/install/windows

### Run unattended

Hvis valget **Run unattended** er tilgjengelig i Tailscale-klienten, kan det aktiveres for en fast, administrert strømme-PC. Dette gjør at Tailscale-tjenesten kan være tilgjengelig uten at en bruker først åpner programmet i skrivebordet.

### Maskintilgang og nøkkelutløp

- Begrens Tailnet-tilgang til betrodde brukere og enheter.
- Noter maskinens Tailscale-IP fra klienten eller administrasjonskonsollen. Den er ofte i `100.x.y.z`-området.
- Tailscale kan ha nøkkelutløp. Deaktivering av nøkkelutløp for en fast maskin reduserer behovet for ny autentisering, men øker konsekvensen dersom enheten kompromitteres. Gjør dette bare hvis klubbens administrator godkjenner det, og vurder tilgang og fysisk sikkerhet jevnlig.

## 2. Installer RustDesk

Offisiell nettside og nedlasting: https://rustdesk.com/

1. Last ned Windows-versjonen fra den offisielle siden.
2. Installer RustDesk på HP-PC-en.
3. Installer RustDesk på kontroll-PC-en.
4. På HP-PC-en: kontroller at RustDesk-tjenesten er installert og at programmet kan starte etter omstart.
5. Noter RustDesk-ID-en som en reserve, men bruk ikke ID-en som eneste dokumenterte tilgangsmetode.

RustDesk-dokumentasjon: https://rustdesk.com/docs/en/client/

## 3. Sikre RustDesk

Menynavn kan variere mellom versjoner.

1. Åpne RustDesk-innstillingene på HP-PC-en.
2. Gå til sikkerhetsinnstillingene og lås dem opp hvis det kreves.
3. Sett et sterkt, unikt permanent passord hvis denne funksjonen er tilgjengelig.
4. Oppbevar passordet i klubbens godkjente passordløsning. Ikke skriv det i dette dokumentet eller i GitHub.
5. Kontroller at tjenesten starter etter omstart.
6. Begrens hvem som har tilgang til PC-en og RustDesk-passordet.

## 4. Direkte IP-tilgang over Tailscale (valgfritt)

Dette er et alternativ hvis dere vil at RustDesk skal koble direkte til HP-PC-ens Tailscale-IP i stedet for å bruke RustDesks ID-/relay-oppsett.

1. Kontroller at Tailscale fungerer mellom begge PC-ene.
2. I RustDesk på HP-PC-en, se etter **Enable direct IP access** under nettverksinnstillingene.
3. Aktiver funksjonen hvis dere ønsker å bruke den.
4. Kontroller hvilken port den installerte RustDesk-versjonen faktisk bruker. Ikke anta at porten er den samme i alle versjoner eller oppsett.
5. Hvis Windows-brannmuren spør, tillat bare nødvendig tilgang for den aktuelle nettverksprofilen og porten.
6. Fra kontroll-PC-en kobler du til HP-PC-ens Tailscale-IP, med eventuell port syntaksen RustDesk-versjonen krever.

Ikke åpne RustDesk-porten mot hele internett i ruteren. Tailscale-tilgangen bør begrenses til godkjente enheter. Hvis direkte IP-tilgang ikke fungerer, bruk RustDesks ID-tilkobling eller feilsøk brannmur, Tailscale-tilgang og RustDesk-konfigurasjon.

## 5. Test fjernstyringen

Test mens skjerm, tastatur og mus fortsatt er tilgjengelig lokalt.

1. Kontroller at Tailscale er tilkoblet på begge PC-ene.
2. Åpne RustDesk på kontroll-PC-en.
3. Koble til strømme-PC-en med den valgte metoden.
4. Autentiser deg.
5. Kontroller at du kan se skrivebordet og åpne et ufarlig program.
6. Start HP-PC-en på nytt.
7. Vent til PC-en er ferdig med oppstart, og prøv å koble til igjen.
8. Koble fra fysisk skjerm, men la HDMI-dummypluggen stå i. Test tilkoblingen igjen.

**Ikke plasser PC-en uten fysisk tilgang før omstartstesten er bestått.**

## 6. Feilsøking

### Tailscale viser ikke tilkobling

- Kontroller internettforbindelsen.
- Kontroller at begge enheter er logget inn på riktig Tailnet.
- Kontroller om enheten er godkjent og om tilgangsregler tillater forbindelsen.
- Start Tailscale-klienten på nytt hvis nødvendig.

### RustDesk kobler ikke til

- Kontroller først at Tailscale fungerer.
- Kontroller RustDesk-ID, eventuell Tailscale-IP og port.
- Kontroller at RustDesk-tjenesten kjører.
- Kontroller Windows-brannmurregler.
- Prøv den andre støttede tilkoblingsmetoden.

### Svart skjerm via RustDesk

- Kontroller at HDMI-dummypluggen står i.
- Kontroller skjermoppløsning og grafikkdriver.
- Test med en fysisk skjerm igjen for å skille skjermemulering fra fjernstyringsproblemer.

Fortsett med [OBS-OPPSETT.md](./OBS-OPPSETT.md).
