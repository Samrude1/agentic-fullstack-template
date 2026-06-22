# Arkkitehtuuri ja Teknologiapino

Tämä projekti on "Full Stack Systems Architecture App", joka on rakennettu ilman suljettuja SaaS-palveluita (kuten Clerk, Trigger.dev, Liveblocks), hyödyntäen avointa lähdekoodia ja AWS-pilvipalveluita.

## Teknologiapino
- **Frontend & UI**: Next.js 15, TailwindCSS, React Flow (arkkitehtuurikaavioiden piirtämiseen selaimessa).
- **Autentikaatio**: Auth.js / NextAuth (korvaa Clerkin).
- **Taustatyöt & Jonot**: AWS SQS + Lambda (korvaa Trigger.devin).
- **Reaaliaikaisuus**: AWS API Gateway WebSockets tai Yjs (korvaa Liveblocksin).
- **Tekoäly (AI Agent)**: Oma FastAPI-taustajärjestelmä (LangGraph/CrewAI), joka analysoi kaavioita, antaa tietoturvasuosituksia ja optimointiehdotuksia.

## Arkkitehtuuriset säännöt
- Emme koodaa satunnaisesti; jokainen uusi ominaisuus suunnitellaan ja hyväksytetään ensin.
- Kaikki backend-toiminnot (lukuun ottamatta Auth.js ja perus-API:t) pyritään eristämään AWS:ään (Lambdat) tai omaan FastAPI-palveluun.
- React Flow toimii käyttöliittymän keskiössä kaavioiden käsittelyssä.
