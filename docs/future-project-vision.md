# Johdon Yhteenveto: Agentic Architecture Builder

## 1. Ydinkonsepti (Core Concept)
Tekoälyohjattu ohjelmistokehitysalusta, joka automatisoi liiketoimintavaatimusten kääntämisen tuotantovalmiiksi Fullstack-sovelluksiksi. Järjestelmä yhdistää "Human-in-the-Loop" -periaatteen autonomisiin tekoälyagentteihin, tarjoten organisaatiolle kyvyn iteroida nopeasti tinkimättä ohjelmistoarkkitehtuurin laadusta ja koodipohjan hallittavuudesta.

## 2. Arkkitehtuuri ja Pääominaisuudet (Architecture & Key Capabilities)

### A. Visuaalinen Arkkitehtuurikangas (Visual Architecture Definition)
Käyttäjä ohjaa kehitystä korkean tason syötteillä, joista alusta generoi välittömästi visuaalisen ja muokattavan arkkitehtuurikaavion (esim. tietokantamallit, API-rajapinnat ja käyttöliittymäkomponentit). Tämä poistaa kuilun liiketoimintavaatimusten ja teknisen toteutuksen väliltä jo ennen koodauksen aloittamista.

### B. Automaattinen Työnkulkujen Orkestrointi (Automated Workflow Inference)
Järjestelmä päättelee ja valitsee oikeat työnkulut dynaamisesti (esim. tietokantamigraatiot vs. käyttöliittymän kehitys). Tekoälyagentit saavat kontekstisidonnaiset ohjeistukset automaattisesti, mikä vähentää manuaalista konfigurointia ja inhimillisiä virheitä.

### C. Autonominen Laadunvarmistus (Self-Healing TDD Loop)
Kehitysprosessi nojaa jatkuvaan testaukseen (Test-Driven Development). Agentti suorittaa "Read-Act-Loop-Plan-Halt" -sykliä:
1. **Toteutus:** Koodin generointi vaatimusten pohjalta.
2. **Validointi:** Automaattisten testien ja käännösten (build) suoritus.
3. **Iteraatio:** Virheilmoitusten analysointi ja automaattinen korjaus.
4. **Luovutus:** Ominaisuus siirtyy asiantuntijan arvioitavaksi vasta, kun kaikki laatuportit (Quality Gates) on läpäisty.

### D. Laatuportit ja "Human-in-the-Loop" (Milestone Validations)
Kehitysprosessi on jaettu loogisiin vaiheisiin, jotka vaativat asiantuntijan hyväksynnän varmistaakseen ohjelmiston laadun ja suunnan:
1. **Tietomallit:** Tietokantaskeemojen ja migraatioiden validointi.
2. **Taustajärjestelmä:** API-rajapintojen ja tietoturvan (esim. autentikaatio) tarkastus.
3. **Design System:** Käyttöliittymäkomponenttien ja brändi-ilmeen vahvistus.
4. **Ominaisuudet:** Yksittäisten toiminnallisuuksien ja liiketoimintalogiikan hyväksyntä.

## 3. Kohderyhmä ja Julkaisustrategia (Target Audience & Delivery Model)
- **Kohderyhmä:** Suunnattu asiantuntijoiden – kuten teknisten perustajien, arkkitehtien ja ohjelmistokehittäjien – työkaluksi. Alusta on tehty skaalaamaan asiantuntijatyötä ja automatisoimaan rutiinit, ei korvaamaan teknistä ymmärrystä.
- **Toimitusmalli (MVP):** "Codebase Export" (Lähdekoodin luovutus). Valmis ratkaisu luovutetaan asiakkaalle täydellisenä ja riippumattomana koodivarastona (Repository) valmiine asennus- ja julkaisuohjeineen. Tämä lähestymistapa poistaa "vendor lock-in" -riskin, sillä asiakas saa täyden omistajuuden tuotettuun ohjelmistoon ja voi integroida sen saumattomasti suoraan omaan pilviympäristöönsä (esim. AWS tai Vercel).

## 4. Teknologiapino (Technology Stack)
- **Frontend / Dashboard:** Next.js (App Router), Tailwind CSS ja React Flow visuaaliseen mallinnukseen.
- **Orkestrointi ja Skaalautuvuus:** Asynkroninen arkkitehtuuri hyödyntäen AWS SQS -jonotuspalvelua ja AWS Lambda -funktioita resurssi-intensiivisten tekoälyprosessien hallintaan.
- **Tekoälymoottori (LangGraph):** LangGraph mahdollistaa monimutkaiset, sykliset työnkulut ja tukee natiivisti "Human-in-the-Loop" -pysäytyspisteitä (checkpoints) hallitummin kuin pelkät vapaat agenttikehykset.
- **Kustannusoptimoitu Mallireititys (Dynamic Model Routing):** Kielimallien resurssien älykäs allokointi tehtävän vaativuuden mukaan:
  - *Arkkitehtuuri ja Kompleksinen Logiikka*: Korkean kapasiteetin mallit (esim. Claude 3.5 Sonnet / GPT-4o / Gemini 1.5 Pro).
  - *Testaus ja Validointi*: Kustannustehokkaat ja nopeat mallit (esim. Gemini Flash / Claude Haiku) mahdollistavat laajan testauskattavuuden edullisesti.

## 5. Käyttökokemus ja Tuottavuus (UX/UI & Workflow)
- **Jaettu Näkymä (Split-View Interface):** Reaaliaikainen näkyvyys visuaaliseen arkkitehtuuriin (Canvas) ja kontekstuaaliseen ohjaukseen (Chat) samanaikaisesti.
- **Kontekstuaalinen Vuorovaikutus:** Älykäs dialogi, joka ehdottaa seuraavia loogisia askeleita laatuporttien kohdalla (esim. testien läpäisyn jälkeen ehdotus siirtymisestä käyttöliittymän kehitykseen). Asiantuntija säilyttää täyden ohjausvallan lisävaatimusten antamiseen milloin tahansa.
- **Reaaliaikainen Esikatselu (Live Preview):** Sisäänrakennettu esikatseluympäristö (esim. Sandpack/WebContainer -integraatio) generoidun sovelluksen välittömään iterointiin ja testaukseen selainympäristössä.
