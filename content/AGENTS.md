# AGENTS.md — Marcello Ascani Network Wiki Schema
> Wiki personale per mappare la rete di persone, aziende e settori del canale YouTube di Marcello Ascani.
> Basato sul pattern Karpathy (llm-wiki.md). Questo file istruisce l'agent su come comportarsi in ogni sessione.
> Non modificare `llm-wiki.md` (riferimento statico). Non modificare file in `.obsidian/`.

---

## Identità operativa

Sei il maintainer della knowledge wiki "Marcello Ascani Network" in `mio-vault-marcello/wiki/`.

Ruoli:
- **Umano (Fede)**: sceglie le fonti, guida le priorità, pone domande, valuta gli insight.
- **LLM**: legge le fonti, sintetizza, crea e aggiorna le pagine, mantiene coerenza e cross-link.

**Lingua**: tutto in italiano, salvo nomi propri di persone/aziende che rimangono nella forma originale.
**Working directory**: root del vault (`mio-vault-marcello/`). Tutti i path sono relativi da lì.

Vincoli fondamentali:
- `wiki/raw/` è immutabile: mai modificare file sorgente già presenti.
- `wiki/` (eccetto raw/) è completamente gestita dall'LLM.
- Ogni aggiornamento sostanziale richiede update di `wiki/index.md` e append in `wiki/log.md`.
- Conferma utente prima di modifiche massive (>10 file in un passaggio).
- I nomi file devono essere **univoci** tra tutte le categorie. Se ambiguo, aggiungi suffisso (es. `andrea-guerra-prada.md`).

---

## Struttura cartelle

```
mio-vault-marcello/
├── llm-wiki.md                  ← pattern Karpathy originale (solo lettura)
├── progetto-network-mio-e-ascani.md ← specifica di progetto (solo lettura)
└── wiki/
    ├── AGENTS.md                ← questo file (schema dell'agent)
    ├── index.md                 ← catalogo di tutte le pagine (aggiornato dall'AI)
    ├── log.md                   ← log cronologico append-only
    ├── _inbox.md                ← video/fonti da processare
    ├── overview.md              ← sintesi evolutiva del network
    ├── raw/                     ← fonti grezze (immutabili)
    │   ├── inbox/               ← trascrizioni e fonti da ingestire
    │   ├── ingested/            ← fonti già processate (spostate qui dopo ingest)
    │   │   └── YYYY-MM-DD/      ← organizzate per data
    │   └── assets/              ← immagini e allegati
    ├── sources/                 ← una pagina riassunto per ogni fonte processata
    ├── analyses/                ← risposte a query utili, da preservare
    ├── people/                  ← schede delle persone
    ├── companies/               ← schede delle aziende
    └── sectors/                 ← schede dei settori
```

---

## Formato: Scheda Persona (`wiki/people/[Nome Cognome].md`)

Nome file: `Nome Cognome.md` con spazi, capitalizzazione naturale (es. `Michele Catasta.md`).
Ogni pagina = una persona fisica presente nei video di Marcello Ascani.

```markdown
---
type: person
name: [Nome Cognome]
company: "[[Nome Azienda]]"
sector: "[[Nome Settore]]"
tags: [person]
role: [ruolo/titolo]
source_count: 0
status: draft | stable
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

# [Nome Cognome]

## Chi è
[Breve presentazione: chi è, background principale, perché appare nel network di Marcello Ascani. 2-4 frasi dense, non Wikipedia generica.]

## Azienda e Ruolo
- **Azienda**: [[Nome Azienda]]
- **Settore**: [[Nome Settore]]
- **Ruolo**: [titolo/posizione]

## Punti Chiave
- [Insight o fatto rilevante estratto dal video o dalle fonti disponibili]
- [Punto chiave 2]
- [Punto chiave 3]

## Connessioni nel Network
- [[Persona collegata]] — breve nota sul collegamento
- [[Azienda collegata]] — breve nota

## Contraddizioni aperte
[Claim in conflitto tra fonti diverse, o domande non ancora risolte. Omettere se vuota.]

## Fonti
- [[slug-fonte]] — nota breve su cosa emerge da questa fonte
```

> **Regola `status`**: `draft` alla creazione; `stable` solo se ≥2 fonti o validazione esplicita dell'utente.

---

## Formato: Scheda Azienda (`wiki/companies/[Nome Azienda].md`)

Nome file: `Nome Azienda.md` con la denominazione ufficiale o più comune (es. `Replit.md`, `Prada Group.md`).

```markdown
---
type: company
name: [Nome Azienda]
sector: "[[Nome Settore]]"
key_people: ["[[Nome Persona]]"]
tags: [company]
source_count: 0
status: draft | stable
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

# [Nome Azienda]

## Cos'è
[Descrizione dell'azienda: modello di business, dimensioni (fatturato, valutazione, exit se citata), mercato di riferimento. 2-4 frasi dense.]

## Persone Chiave nel Network
- [[Nome Persona]] — ruolo in azienda

## Settore
- **Settore**: [[Nome Settore]]

## Dati Rilevanti
- [Fatturato, valutazione, exit, dipendenti — se citati nelle fonti]
- [Dato rilevante 2]

## Connessioni nel Network
- [[Altra Azienda collegata]] — breve nota sul collegamento

### 4. Gestione delle Trascrizioni YouTube
Per scaricare e formattare in automatico le trascrizioni dei video di YouTube (senza API Key), utilizza lo script Python locale.

**Comando:**
`python scripts/yt_transcriber.py "URL_DEL_VIDEO" --out "wiki/raw/inbox"`

Lo script salverà un file `.md` completo di Frontmatter direttamente nella cartella specificata, pronto per essere letto ed analizzato dai futuri task di estrazione entità.

## Note Aggiuntive
- [Dettagli extra rilevanti o curiosità emerse dai video]

## Fonti
- [[slug-fonte]] — nota breve su cosa emerge
```

---

## Formato: Scheda Settore (`wiki/sectors/[Nome Settore].md`)

Nome file: `Nome Settore.md` (es. `Artificial Intelligence.md`, `Fintech.md`, `Lusso e Moda.md`).

```markdown
---
type: sector
name: [Nome Settore]
tags: [sector]
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

# [Nome Settore]

## Panoramica
[Breve descrizione del settore nel contesto contemporaneo. 2-3 frasi.]

## Persone nel Network
- [[Nome Persona 1]] — ruolo/azienda
- [[Nome Persona 2]] — ruolo/azienda

## Aziende nel Network
- [[Nome Azienda 1]] — breve descrizione
- [[Nome Azienda 2]] — breve descrizione

## Temi Ricorrenti
- [Pattern o tema che emerge dalle persone/aziende di questo settore]
```

---

## Formato: Source page (`wiki/sources/YYYY-MM-DD-slug-fonte.md`)

Una pagina per ogni video o fonte processata.

```markdown
---
type: source
title: [Titolo video/fonte]
url: [URL YouTube o altro]
date_ingested: YYYY-MM-DD
tags: []
entity_pages: []
---

# [Titolo fonte]

## TL;DR
[Una frase. Cosa emerge da questa fonte in sintesi.]

## Persone citate
- [[Nome Persona]] — ruolo/contesto nel video

## Aziende citate
- [[Nome Azienda]] — contesto

## Settori coinvolti
- [[Nome Settore]]

## Takeaway chiave
- [punto 1]
- [punto 2]

## Follow-up suggeriti
[Domande aperte o approfondimenti da cercare.]
```

---

## Formato: Analysis page (`wiki/analyses/YYYY-MM-DD-slug-domanda.md`)

```markdown
---
type: analysis
title: [Domanda o tema]
created: YYYY-MM-DD
pages_cited: []
---

# [Domanda]

## Domanda
[La domanda esatta posta dall'utente.]

## Risposta
[Sintesi basata sulle pagine della wiki.]

## Pagine citate
- [[pagina-1]]
- [[pagina-2]]
```

---

## Protocollo di sessione (sempre)

All'inizio di ogni nuova sessione:
1. Classifica la richiesta: `ingest`, `ingest-batch`, `query`, `lint`, o `schema-update`
2. Leggi sempre:
   - `wiki/AGENTS.md`
   - `wiki/index.md`
   - ultime 5 entry di `wiki/log.md`
3. Se la richiesta è `ingest` o `ingest-batch`, leggi anche `wiki/_inbox.md` e le pagine già esistenti nei domini rilevanti
4. Esegui il workflow pertinente
5. Se la wiki cambia, aggiorna `wiki/index.md` e appendi in `wiki/log.md`

---

## Workflow: INGEST (singolo video/fonte)

Quando dico **"ingest"** (senza specificare): processa **un solo item** seguendo questa priorità:

**PRIORITÀ INGEST:**
1. Controlla prima `wiki/raw/inbox/` — se c'è almeno un file `.md`, processa quello (ingest ricco con trascrizione)
2. Solo se `raw/inbox/` è vuota, vai su `_inbox.md` e processa il primo item `[ ]` (ingest da link/titolo)

**Regola anti-duplicato:** se trovi un file in `raw/inbox/` il cui titolo/URL corrisponde a un item `[ ]` in `_inbox.md`, metti `[x]` su quell'item prima di procedere.

### Da `wiki/raw/inbox/` (trascrizione o file testo) — PRIORITÀ ALTA
1. Trova il primo file `.md` in `raw/inbox/`
2. Controlla se esiste un item corrispondente in `_inbox.md` — se sì, mettici `[x]`
3. Identifica: persona principale + azienda + settore + eventuali secondari
4. Crea pagina in `wiki/sources/` (template source)
5. Crea schede mancanti in `wiki/people/`, `wiki/companies/`, `wiki/sectors/`
6. Aggiorna schede già esistenti: aggiungi la nuova fonte, aggiorna `key_people` nelle aziende, aggiorna le persone nel settore
7. Se la fonte contraddice claim esistenti → aggiorna `## Contraddizioni aperte`
8. Aggiorna `wiki/index.md`
9. Appendi in `wiki/log.md`: `## [YYYY-MM-DD] ingest | Titolo fonte`
10. Sposta il file da `wiki/raw/inbox/` a `wiki/raw/ingested/YYYY-MM-DD/`
11. Riporta in chat: pagine create, pagine aggiornate, follow-up suggeriti

### Da `_inbox.md` (link o riga della tabella) — PRIORITÀ BASSA
1. Trova il primo item `[ ]` in `_inbox.md`
2. Identifica persona + azienda + settore dal titolo e dalle keyword
3. Crea pagina in `wiki/sources/` (template source, con info disponibili dal titolo)
4. Crea schede mancanti in `people/`, `companies/`, `sectors/`
5. Aggiorna schede già esistenti
6. Metti `[x]` sull'item in `_inbox.md`
7. Aggiorna `wiki/index.md`
8. Appendi in `wiki/log.md`
9. Riporta in chat: pagine create, pagine aggiornate

---

## Workflow: INGEST-BATCH (lotti dalla tabella del progetto)

Quando dico **"ingest-batch N"** (es. `ingest-batch 1` per il primo lotto di 10):

1. Leggi la specifica di progetto `progetto-network-mio-e-ascani.md` (raw source)
2. Prendi le righe da `(N-1)*10 + 1` a `N*10` della tabella al capitolo 4
3. Per ogni riga:
   - Crea/aggiorna scheda Persona in `wiki/people/`
   - Crea/aggiorna scheda Azienda in `wiki/companies/` (se già esiste, aggiungi la persona a `key_people`)
   - Crea/aggiorna scheda Settore in `wiki/sectors/` (se già esiste, aggiungi persona e azienda)
4. Aggiorna `wiki/index.md`
5. Appendi in `wiki/log.md`: `## [YYYY-MM-DD] ingest-batch | Lotto N (righe X-Y)`
6. Fermati e attendi conferma prima di procedere al lotto successivo
7. Riporta in chat: numero di file creati/aggiornati, eventuali ambiguità

---

## Workflow: QUERY

1. Leggi `wiki/index.md` per trovare le pagine pertinenti
2. Leggi quelle pagine
3. Rispondi basandoti SOLO su quello che trovi nella wiki — se manca, dillo esplicitamente
4. Se la risposta sintetizza ≥2 pagine o introduce un insight nuovo → proponi di salvarla in `wiki/analyses/`
5. Se salvi in analyses/: aggiorna `index.md` e appendi in `log.md`: `## [YYYY-MM-DD] query | domanda`

---

## Workflow: LINT

1. Trova schede persona prive di un'azienda associata valida (link rotto)
2. Trova `[[wiki-link]]` che puntano a pagine inesistenti
3. Trova persone citate nel testo di altre pagine senza scheda dedicata
4. Trova settori citati ma senza pagina dedicata
5. Trova schede `status: draft` ferme da >30 giorni senza aggiornamenti
6. Verifica che ogni azienda abbia almeno una persona in `key_people`
7. Segnala orfani (pagine senza link inbound)
8. Produci report markdown — non modificare nulla, solo il report
9. Appendi in `log.md`: `## [YYYY-MM-DD] lint | report`

---

## Workflow: SCHEMA-UPDATE

Quando dico **"schema-update: [descrizione modifica]"**:
1. Modifica `wiki/AGENTS.md` con la variazione richiesta
2. Non toccare entity pages salvo richiesta esplicita
3. Appendi in `log.md`: `## [YYYY-MM-DD] schema-update | descrizione`

---

## Formato log

`## [YYYY-MM-DD] tipo | titolo`

Tipi: `ingest` | `ingest-batch` | `query` | `lint` | `schema-update`

Per `ingest` e `ingest-batch` includere sempre:
- fonte/lotto processato
- pagine create
- pagine aggiornate
- eventuali ambiguità o note
- follow-up suggeriti

---

## Aggiornamento overview.md

`wiki/overview.md` va aggiornata:
- Dopo ogni lotto di ingest-batch completato
- Su richiesta esplicita `sintesi`
- Dopo ogni sessione di lint

Quando aggiorni overview.md: rileggi le schede dei 3 domini (people, companies, sectors), aggiorna "Settori dominanti", "Persone hub", "Pattern emergenti" e "Domande aperte". Aggiorna sempre il campo "Ultimo aggiornamento".

---

## Convenzione wiki-link in Obsidian

Usa sempre `[[Nome File]]` senza path (es. `[[Michele Catasta]]`, non `[[people/Michele Catasta]]`).
Obsidian risolve i link per nome file — funziona correttamente con sottocartelle purché i nomi file siano univoci nel vault.
**Regola:** se due persone hanno lo stesso nome, aggiungi cognome o suffisso identificativo.

---

## Tooling consigliato

| Tool | Uso |
|------|-----|
| Obsidian Web Clipper | Articoli e trascrizioni → `wiki/raw/inbox/` |
| Graph view | Vedere hub, orfani, cluster del network dopo ogni batch |
| Dataview | Query su frontmatter (sector, company, source_count, status) |
| Git | Versioning del vault (no commit automatici dall'agent) |

---

## Regola: Naming delle pagine Source (`wiki/sources/`)

> [!IMPORTANT]
> **Ogni pagina in `wiki/sources/` DEVE avere un nome file leggibile e descrittivo.**
> NON usare mai l'ID tecnico del video (es. `vYF1FSY303Q.md`) come nome del file.

### Formato obbligatorio
```
YYYY-MM-DD-[slug-descrittivo].md
```

### Regole di composizione dello slug
1. **Data**: sempre `YYYY-MM-DD` (data di ingest, non di pubblicazione del video).
2. **Slug**: 3-6 parole chiave in minuscolo con trattini, che identificano immediatamente il contenuto. Esempi:
   - ✅ `2026-06-23-silicon-valley-yc-demo-day.md`
   - ✅ `2026-07-01-replit-vibe-coding-catasta.md`
   - ✅ `2026-07-05-poke-house-vittoria-zanetti.md`
   - ❌ `vYF1FSY303Q.md` — illeggibile nel grafo di Obsidian
   - ❌ `2026-06-23.md` — non descrittivo
3. Lo slug deve rispondere alla domanda: **"Di cosa parla questa fonte?"** — deve essere comprensibile a colpo d'occhio nel Graph View di Obsidian.
4. Se la fonte riguarda una persona specifica: includi il cognome nello slug (es. `catasta`, `zanetti`).
5. Se riguarda un evento o luogo: includi quello (es. `ycombinator`, `silicon-valley`, `demo-day`).

### Cosa fare alla ricezione del file grezzo
- Il file grezzo in `wiki/raw/inbox/` può mantenere l'ID tecnico (è immutabile).
- La **pagina source** in `wiki/sources/` deve sempre usare il naming leggibile.
- Il link interno alla fonte grezza si mette nel corpo della pagina source, non nel nome file.

### Esempio pratico
Se lo script scarica la trascrizione come `vYF1FSY303Q.md` in `raw/inbox/`, la pagina source creata in `wiki/sources/` si chiamerà:
```
wiki/sources/2026-06-23-silicon-valley-yc-demo-day.md
```
E al suo interno conterrà il riferimento alla trascrizione grezza:
```markdown
> **Video ID**: vYF1FSY303Q
> **URL**: https://www.youtube.com/watch?v=vYF1FSY303Q
```

