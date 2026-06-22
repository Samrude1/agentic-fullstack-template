# Project Vision: Agentic Architecture Builder (SaaS)

## 1. Ydinkonsepti (The Core Idea)
Visuaalinen, tekoälyohjattu ohjelmistokehitysalusta, joka muuttaa liiketoimintaideat valmiiksi Fullstack-sovelluksiksi **askel askeleelta** (Human-in-the-Loop -periaatteella). Alusta ei ole "musta laatikko", joka sylkee ulos koodia sattumanvaraisesti, vaan se toimii kuten oikea Senior Arkkitehti ja devaajatiimi.

## 2. Pääominaisuudet (Key Features)

### A. Visiosta Arkkitehtuuriksi (Visual Canvas)
Käyttäjä syöttää promptin (esim. "Haluan Instagramin koirille"). Alusta generoi välittömästi visuaalisen arkkitehtuurikaavion (React Flow), josta näkee mitä palikoita sovellukseen tulee (Tietokannat, API-reitit, UI-näkymät). Käyttäjä voi muokata kaaviota vapaasti ennen koodauksen aloittamista.

### B. Automaattinen Työnkulun Päättely (Workflow Inference)
Käyttäjän ei tarvitse tietää mitään "työnkuluista" (workflows). Kun tekoäly siirtyy seuraavaan vaiheeseen, järjestelmä päättelee automaattisesti oikean työnkulun (esim. `new-feature-workflow.md` tai `database-workflow.md`) ja antaa sen AI-agentin ohjeistukseksi taustalla.

### C. Itsekorjautuva Testauslooppi (The RALPH Loop)
Jokaisen vaiheen sisällä tekoäly suorittaa autonomisen TDD-kehän (Test-Driven Development / Read-Act-Loop-Plan-Halt):
1. **Koodaa:** Agentti luo koodin.
2. **Testaa:** Agentti ajaa automaattiset testit (esim. Jest tai Cypress) tai käännöksen (Build).
3. **Korjaa:** Jos terminaali antaa virheen, agentti lukee virheilmoituksen, korjaa koodin ja ajaa testin uudelleen.
4. **Luovuttaa:** Vasta kun kaikki testit menevät vihreällä läpi, järjestelmä pysähtyy ja luovuttaa ominaisuuden ihmisen testattavaksi.

### D. Vaiheittaiset Tarkastuspisteet (Human-in-the-Loop)
1. **Perustus:** Tietokannan migraatiot ja mallit (Data Models).
2. **Taustalogiikka:** Autentikaatio ja API-reitit (Backend).
3. **Design System:** Peruskäyttöliittymän tyylit ja komponentit (UI).
4. **Ominaisuudet:** Yksittäiset sivut ja ominaisuudet yksitellen (Features).

*Jokaisen vaiheen välissä on "Approve & Generate Next" -painike.*

## 3. Kohderyhmä
- **Sooloyrittäjät (Solopreneurs):** Jotka haluavat rakentaa nopeasti laadukkaita SaaS-tuotteita ilman koodausosaamista tai kallista tiimiä.
- **Ohjelmistokehittäjät:** Jotka haluavat nopeuttaa projektien aloitusvaihetta ja automatisoida "boilerplate"-koodin kirjoittamisen luotettavasti.

## 4. Teknologia (SaaS-alustan oma pino)
- **Frontend / Dashboard:** Next.js (App Router), Tailwind CSS, React Flow (Kaaviot).
- **Taustatyöt (Orkestrointi):** AWS SQS (Jonotus) + AWS Lambda (Työntekijät pitkäkestoiseen koodin generointiin).
- **Tekoälymoottori:** FastAPI + LangGraph/CrewAI (Agenttitiimit, esim. Arkkitehti, Koodari, Arvostelija).
- **Autentikaatio:** Auth.js.

## 5. Miksi tämä voittaa kilpailijat?
Nykyiset tekoälykoodarit yrittävät tehdä liikaa kerralla, jolloin virheiden sattuessa koko projekti romahtaa. Integroimalla "Interactive Pause" -pysähdykset ja visuaalisen arkkitehtuurikankaan, käyttäjä säilyttää täyden kontrollin ja luottamuksen koodipohjan laatuun.
