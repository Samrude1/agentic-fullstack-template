# Tekoälyavusteisen Ohjelmistokehityksen Käyttöopas

Tämä dokumentti on tarkoitettu sinulle (ihmiselle), jotta muistat miten tämä `.agents`-hakemistoon pohjautuva tekoälyavusteinen "Engineering Loop" toimii. Tämän järjestelmän tarkoitus on tuottaa Fullstack-koodia täysin hallitusti ja kurinalaisesti, estäen tekoälyn "hallusinointikierteet" ja koodipohjan rappeutumisen (spagettikoodi).

---

## 1. Järjestelmän Ydin (Miten tämä toimii?)

Kaikki äly asuu projektin juuren `.agents/` -kansiossa. Koska järjestelmä perustuu puhtaasti Markdown-tiedostoihin, se on täysin siirrettävissä (Platform Agnostic). Voit käyttää sitä missä tahansa modernissa tekoäly-IDE:ssä (esim. Antigravity IDE, Cursor, Windsurf tai GitHub Copilot Workspace).

- **`context/`**: Totuuden lähde. Täällä on arkkitehtuuri, tietokantasäännöt ja UI-rekisteri. Tekoäly lukee nämä aina ennen koodausta.
- **`workflows/`**: *Mitä* tehdään. Nämä ovat työnkulkuja (esim. uuden API-reitin tai UI-komponentin tekeminen).
- **`skills/`**: *Miten* tehdään. Nämä ovat tekoälyn kognitiivisia taitoja (esim. `/architect`, `/review`, `/imprint`). *Huom: Antigravity IDE tukee slash-komentoja näille suoraan, muissa työkaluissa voit pyytää tekoälyä lukemaan vastaavan SKILL.md -tiedoston.*

---

## 2. Kuinka palata tauolta (Session palauttaminen)

Koska tekoälyllä ei ole muistia sessioiden välillä, meidän on ladattava konteksti aina uuden session alussa.

**Kun aloitat uuden chatin (esim. seuraavana päivänä):**
1. Sano tekoälylle: *"Aja `/remember restore`."*
2. Tekoäly lukee automaattisesti projektin juuressa olevan `memory.md`-tiedoston sekä koko `.agents/context/` -kansion.
3. Tekoäly kertoo sinulle, mihin viimeksi jäätiin ja varmistaa, voidaanko jatkaa siitä.

---

## 3. Kuinka uusi ominaisuus lisätään (Päivittäinen työnkulku)

Älä koskaan pyydä tekoälyä vain "koodaamaan jotain". Käytä aina työnkulkuja. 

**Esimerkkikomento tekoälylle:**
> *"Haluan lisätä sovellukseen kirjautumissivun. Noudata `new-feature-workflow.md` -työnkulkua ja ota huomioon `ui-registry.md`."*

**Tämän jälkeen tapahtuu automaattinen "Engineering Loop":**
1. **Suunnittelu (`/architect`)**: Tekoäly tutkii kontekstin ja luo sinulle ruudulle interaktiivisen *Implementation Plan* -dokumentin. Ette kirjoita vielä riviäkään koodia.
2. **Hyväksyntä**: Sinä (ihminen) luet suunnitelman. Jos se on hyvä, painat "Approve". 
3. **Koodaus**: Vasta hyväksynnän jälkeen tekoäly kirjoittaa koodin.
4. **Katselmointi (`/review`)**: Kun koodi on valmis, tekoäly tarkistaa sen sääntöjä vasten ja esittää sinulle *Walkthrough* -raportin (esim. varoittaen tietoturvapuutteista).
5. **Tallennus (`/imprint` tai kontekstin päivitys)**: Jos tehtiin UI-komponentteja, tekoäly päivittää `ui-registry.md` -tiedoston uusilla väreillä tai layouteilla tulevaisuutta varten.

---

## 4. Kuinka lopettaa työpäivä (Session tallennus)

Kun olet valmis lopettamaan koodauksen tältä erää, konteksti pitää säästää seuraavaa kertaa varten.

**Ennen kuin suljet ohjelman:**
1. Sano tekoälylle: *"Aja `/remember save`."*
2. Tekoäly tekee yhteenvedon siitä, mitä sessiossa tehtiin, mitkä ongelmat ratkaistiin ja mitä tehdään seuraavaksi.
3. Tämä tieto tallennetaan `memory.md` -tiedostoon projektin juureen.

---

## 5. Mitä tehdä jos kaikki menee pieleen? (Recovery)

Tekoäly tekee virheitä. Jos huomaat, että koodi on rikki ja olette yrittäneet korjata sitä tuloksetta yli kaksi kertaa, **pysähdy**.

**Komenna tekoälyä:**
> *"Ollaan jumissa. Aja `/recover`."*

Tekoäly analysoi tilanteen ja kertoo sinulle yhden kolmesta vaihtoehdosta:
- **Targeted Fix**: Kyseessä on vain pieni bugi, joka voidaan korjata.
- **Hard Reset**: Konteksti on liian sotkussa. Tekoäly pyytää sinua aloittamaan uuden chatin (session).
- **Rethink**: Arkkitehtuurissa on perustavanlaatuinen valuvika, ja tekoäly ehdottaa ominaisuuden suunnittelua kokonaan uudestaan.

---

## 6. Kuinka uusi projekti aloitetaan

Jos haluat aloittaa täysin uuden projektin tällä samalla standardilla, seuraa näitä neljää vaihetta (Quick-Start):

**Vaihe 1: Ihmisen valmistelut**
- Kloonaa tämä koko repo uuteen kansioon (esim. `OmaUusiSaaS`).
- Kirjoita projektin juureen (esim. `docs/project-vision.md`) vapaamuotoinen kuvaus: ydinidea, kohderyhmä ja MVP-ominaisuudet.

**Vaihe 2: Liikkeellelähtö (Tekoälyn herätys)**
- Avaa uusi chat ja sano: *"Moikka! Luodaan uusi sovellus. Lue `docs/project-vision.md` ja päivitetään arkkitehtuuri sen pohjalta."*

**Vaihe 3: Arkkitehtuurin lukitus (Tekoälyn työ)**
- Tekoäly ajaa `/architect` -taidon ja luo sinulle Interaktiivisen Implementation Planin.
- Suunnitelmassa ehdotetaan päivitykset `architecture.md` ja `database-schema.md` -tiedostoihin.
- Paina "Approve", jolloin tekoäly päivittää tiedostot.

**Vaihe 4: Varsinainen kehitys alkaa**
- Komenna: *"Arkkitehtuuri on selvä. Rakenna ensimmäisenä kirjautuminen, käytä `new-feature-workflow.md`."*
- Tästä eteenpäin rullataan tuttua `/architect` -> Koodaa -> `/review` -> `/imprint` -looppia!
