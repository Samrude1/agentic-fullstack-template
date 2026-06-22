# Tekoälyavusteisen Ohjelmistokehityksen Käyttöopas

Tämä dokumentti on tarkoitettu sinulle (ihmiselle), jotta muistat miten tämä `.agents`-hakemistoon pohjautuva tekoälyavusteinen "Engineering Loop" toimii. Tämän järjestelmän tarkoitus on tuottaa huippuluokan Fullstack-koodia täysin hallitusti ja kurinalaisesti, estäen tekoälyn "hallusinointikierteet" ja koodipohjan rappeutumisen (spagettikoodi).

---

## 1. Järjestelmän Ydin (Miten tämä toimii?)

Kaikki äly asuu projektin juuren `.agents/` -kansiossa. Tekoäly (Antigravity IDE / Gemini) on aina tietoinen tästä kansiosta.
- **`context/`**: Totuuden lähde. Täällä on arkkitehtuuri, tietokantasäännöt ja UI-rekisteri. Tekoäly lukee nämä aina ennen koodausta.
- **`workflows/`**: *Mitä* tehdään. Nämä ovat työnkulkuja (esim. uuden API-reitin tai UI-komponentin tekeminen).
- **`skills/`**: *Miten* tehdään. Nämä ovat tekoälyn kognitiivisia taitoja (esim. `/architect`, `/review`, `/imprint`).

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

## 6. Kuinka uusi projekti aloitetaan (tulevaisuudessa)

Jos haluat joskus aloittaa täysin uuden projektin tällä samalla huippustandardilla:
1. Alusta projektin runko (esim. `npx create-next-app`).
2. Kopioi tämä olemassa oleva `.agents` -kansio kokonaisuudessaan uuden projektin juureen.
3. Nollaa (tyhjennä) `context/` -kansion tiedostot (`architecture.md`, `database-schema.md` jne.) ja kirjoita niihin uuden projektin visio.
4. Kerro tekoälylle ensimmäisessä viestissä: *"Lue läpi `.agents/AGENTS.md` ja aloitetaan uuden sovelluksen kehitys."*
