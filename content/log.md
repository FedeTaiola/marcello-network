# 📋 Registro Operativo (Log)
> Append-only. Ogni operazione viene aggiunta in fondo a questo file.
> Formato: `## [YYYY-MM-DD] tipo | titolo`

---

## [2026-06-22] schema-update | Inizializzazione del vault

- Creata struttura cartelle del vault `mio-vault-marcello/`
- Creato `wiki/AGENTS.md` con schema adattato al dominio network/persone
- Creati file base: `index.md`, `log.md`, `_inbox.md`, `overview.md`
- Creata struttura `raw/inbox/`, `raw/ingested/`, `raw/assets/`
- Creata struttura `people/`, `companies/`, `sectors/`, `sources/`, `analyses/`
- Il vault è pronto per la fase di ingest-batch dalla tabella del progetto

---

## [2026-06-22] ingest-batch | Lotto 1 (righe 1-10)

- **Fonte**: tabella cap. 4 di `progetto-network-mio-e-ascani.md`, righe 1-10
- **Pagine create (people)**: Francesco Mugnai, Fabrizio Romano, Michele Catasta, Akio Toyoda, Marcello Ascani, Giovanni Bonotto, Gabriele Burgio, Danila De Stefano, Nadia Calviño
- **Pagine create (companies)**: Il Signor Franz, Fabrizio Romano Srl, Replit, Toyota, Chapeau, Race Capital, Bonotto Spa, Alpitour, Unobravo, Banca Europea per gli Investimenti
- **Pagine create (sectors)**: Content Creation, Giornalismo Sportivo, Artificial Intelligence, Automotive, Venture Capital, Tessile e Moda, Turismo e Viaggi, Digital Health, Istituzioni e Finanza
- **Totale file creati**: 28 (9 persone + 10 aziende + 9 settori)
- **Note**: Marcello Ascani appare in due righe (Chapeau + Race Capital) → una sola scheda persona con riferimento a entrambe le aziende. Race Capital precompilata con key_people già noti da video successivi (Alfred Chuang, Trevor Traina).
- **Follow-up**: procedere con ingest-batch 2 (righe 11-20)

---

## [2026-06-22] ingest-batch | Lotto 2 (righe 11-20)

- **Fonte**: tabella cap. 4 di `progetto-network-mio-e-ascani.md`, righe 11-20
- **Pagine create (people)**: Giovanni Ferrero, Cristina Fogazzi, Guido Brera, Tommaso Ebhardt, Pierroberto Folgiero, Raffaella Orsero, Arturo Licenziati, Lorenzo Bertelli, Ninell Sobiecka
- **Pagine create (companies)**: Ferrero, Veralab, Kairos Partners SGR, Bloomberg News, Fincantieri, Orsero Group, IBSA Group, Prada Group, Studio Legale, L'Oréal Italia
- **Pagine create (sectors)**: Agroalimentare, Cosmesi e Beauty, Finanza e Investimenti, Giornalismo Economico, Cantieristica e Difesa, Farmaceutico, Lusso e Moda, Legale
- **Totale file creati**: 27 (9 persone + 10 aziende + 8 settori)
- **Note**: riga 19 (avvocato anonimo) → nessuna scheda persona creata, solo Studio Legale. Prada Group precompilato con Andrea Guerra (atteso nel lotto 3). Agroalimentare e Cosmesi e Beauty hanno già 2 persone/aziende ciascuno.
- **Follow-up**: procedere con ingest-batch 3 (righe 21-30)

---

## [2026-06-22] ingest-batch | Lotto 3 (righe 21-30)

- **Fonte**: tabella cap. 4 di `progetto-network-mio-e-ascani.md`, righe 21-30
- **Pagine create (people)**: Luca Carabetta, Andrea Guerra, Michele Boldrin, Trevor Traina, Sonia Dehò, Gianni Onorato, Dario Amodei, Christine Lagarde, Michele Zocca, Nerio Alessandri
- **Pagine create (companies)**: Trade Republic, Washington University in St. Louis, Svd Consulting, MSC Crociere, Anthropic, Banca Centrale Europea, Michelangelo Production, Technogym
- **Pagine aggiornate (companies)**: Prada Group (aggiunto Andrea Guerra a key_people — era già nel lotto 2); Race Capital (Trevor Traina già in key_people)
- **Pagine create (sectors)**: Fintech, Accademia ed Economia, Wealth Management, Musica e Spettacolo, Fitness e Benessere
- **Totale file creati**: 23 (10 persone + 8 aziende + 5 settori)
- **Note**: Anthropic e BCE aggiungono profondità al cluster AI e Istituzioni già presenti. MSC Crociere si collega a Fincantieri (cliente). Boldrin introduce la prima voce critica/libertarian nel network.
- **Follow-up**: procedere con ingest-batch 4 (righe 31-40)

---

## [2026-06-22] manual-fix | Correzione Flatmates e Chapeau Media

- **Fonte**: Web search / richiesta utente
- **Pagine create (people)**: Michele Pagani, Giacomo Luppi, Filippo Carabelli, Pietro Santini, Simone Roccoli
- **Pagine create (companies)**: Flatmates, Chapeau Media, Cosmico
- **Pagine eliminate**: Chapeau (sostituita da Flatmates)
- **Pagine aggiornate**: Marcello Ascani (aggiornati i dati della exit a 10.8M totali, 3.25M la sua quota per Flatmates)
- **Note**: Chapeau è in realtà un progetto editoriale (Chapeau Media) fondato da 4 ragazzi in cui Marcello Ascani ha investito 140k€. La vera azienda co-fondata e venduta da Ascani e Pagani è Flatmates (acquisita al 100% dalla holding Cosmico).
- **Follow-up**: procedere con ingest-batch 4 (righe 31-40)

---

## [2026-06-22] ingest-batch | Lotto 4 (righe 31-40)

- **Fonte**: tabella cap. 4 di `progetto-network-mio-e-ascani.md`, righe 31-40
- **Pagine create (people)**: Alberto Forchielli, Walter D'Aprile, Salvatore Sanfilippo, Fabio Novembre, Francesco Mutti, Andrea Giunti, Melissa Ferretti Peretti, Demis Hassabis, Vincenzo Esposito, Nicola Drago, Enrico Drago
- **Pagine create (companies)**: Mandarin Capital Partners, nss magazine, Redis, Studio Novembre, Mutti, Giunti Editore, Google Italia, Google DeepMind, Microsoft Italia, De Agostini Group
- **Pagine create (sectors)**: Private Equity, Editoria e Moda, Software Engineering, Architettura e Design, Editoria, Big Tech, Editoria e Holding
- **Totale file creati**: 28 (11 persone + 10 aziende + 7 settori)
- **Note**: Mutti e Giunti aggiungono importanti aziende italiane (Agroalimentare e Editoria), mentre l'introduzione di Google e Microsoft inizia a espandere il cluster Big Tech.
- **Follow-up**: procedere con ingest-batch 5 (righe 41-50)

---

## [2026-06-22] ingest-batch | Lotto 5 (righe 41-50)

- **Fonte**: tabella cap. 4 di `progetto-network-mio-e-ascani.md`, righe 41-50
- **Pagine create (people)**: Dylan Field, Paolo Ardoino, Enrico Pandian, Claudio Domenicali, Federico Marchetti, Silvio Campara, Gary Stevenson, Fabrizio Di Amato, Jannik Sinner, Benedetto Vigna
- **Pagine create (companies)**: Figma, Tether, EasyGlamping, Ducati, YOOX, Golden Goose, Garyseconomics, Maire Tecnimont, Indipendente, Ferrari
- **Pagine create (sectors)**: Software SaaS, Fintech e Crypto, Startup e Turismo, E-commerce e Moda, Economia e Media, Ingegneria Industriale, Sport Professionistico, Automotive e Nautica
- **Totale file creati**: 28 (10 persone + 10 aziende + 8 settori)
- **Note**: Il cluster Lusso/Motori si espande con eccellenze italiane mondiali (Ferrari, Ducati, YOOX, Golden Goose). Inserita anche la figura anomala "Indipendente" per atleti professionisti come Sinner.
- **Follow-up**: procedere con ingest-batch 6 (righe 51-60)

---

## [2026-06-22] ingest-batch | Lotto 6 (righe 51-60)

- **Fonte**: tabella cap. 4 di `progetto-network-mio-e-ascani.md`, righe 51-60
- **Pagine create (people)**: Cinzia Zuffada, Matteo Lunelli, Fabiola Gianotti, Bill Gates, Duccio Vitali, Joshua Motta
- **Pagine create (companies)**: NASA JPL, Kinecta, Ferrari Trento, CERN, Sambonet Paderno Industrie, Bill & Melinda Gates Foundation, Alkemy, Coalition
- **Pagine create (sectors)**: Aerospaziale, Ricerca Scientifica, Manifattura, Filantropia e Big Tech, Digital Consulting, Cybersecurity
- **Totale file creati**: 20 (6 persone + 8 aziende + 6 settori)
- **Note**: Importante aggiunta di figure globali (Bill Gates), centri di ricerca mondiali (NASA JPL, CERN) e nuove nicchie come la Cybersecurity e il Digital Consulting. Trevor Traina e Fabrizio Di Amato erano già stati creati precedentemente, per questo non appaiono tra le nuove persone create, ma i loro link nel network sono ora più ricchi.
- **Follow-up**: procedere con ingest-batch 7 (righe 61-72, finale)

---

## [2026-06-22] ingest-batch | Lotto 7 (righe 61-72, Finale)

- **Fonte**: tabella cap. 4 di `progetto-network-mio-e-ascani.md`, righe 61-72
- **Pagine create (people)**: Claudio Descalzi, Michel Roccati, Federico Faggin, Pierluigi Zappacosta, Alberto Salleo, Mario Zanetti, Alberto Sangiovanni-Vincentelli, Paolo Privitera, Loris Degioanni, Sundar Pichai
- **Pagine create (companies)**: Eni, Onward Medical, Faggin Foundation, Logitech, Stanford University, Costa Crociere, Cadence Design Systems, Evensi, Sysdig, Google, Deloitte Italia
- **Pagine create (sectors)**: Energia e Supercomputing, Biotecnologie, Hardware e Scienza, Hardware e Big Tech, Accademia e Ricerca, Consulenza Aziendale
- **Totale file creati**: 27 (10 persone + 11 aziende + 6 settori)
- **Note**: Ultimo blocco completato. Notevole profondità sulle figure tecnologiche italiane nella Silicon Valley (Faggin, Zappacosta, Sangiovanni-Vincentelli, Degioanni). Inoltre, il file `index.md` è stato completamente riscritto per utilizzare le query Dataview, in modo da generare dinamicamente le tabelle dell'intero network.
- **Stato**: Ingest Iniziale Completato al 100%.

---

## [2026-06-23] network-expansion | Podcast e Divulgazione (Punto 3)

- **Fonte**: Web Search per i crossover di Marcello Ascani su altri format
- **Pagine create (people)**: Marco Montemagno, Gianluca Gazzoli
- **Pagine create (companies)**: Competenze.it, Passa dal BSMT, StartupItalia
- **Pagine create (sectors)**: Divulgazione Tech e Business
- **Script Creato**: `scripts/yt_transcriber.py` (Per estrazione automatica trascrizioni YouTube senza API Key).
- **Note**: Aggiunta della branchia media/podcast. Gazzoli inserito perché intervista frequentemente creator e imprenditori tech in ottica creator economy. Lo script per le trascrizioni è stato creato ed è funzionante. AGENTS.md aggiornato.

---

## [2026-06-23] ingest-sf-vc | Y Combinator e San Francisco

- **Fonte**: Trascrizione video `2026-06-23-silicon-valley-yc-demo-day` (Vlog San Francisco e Demo Day)
- **Pagine create (people)**: Irene Mingozzi, Lorenzo Franzi, Alessandro Cannas, Riccardo Giraldi, Massimo Carnellos
- **Pagine create (companies)**: Y Combinator, Italian Founders Fund, Lombard Street Ventures, Vento Ventures, Hummingbird, Peak Design, Vivid, Lovable
- **Pagine modificate**: Replit, Michele Catasta (dati aggiornati sulla revenue e incontro SF)
- **Pagine create (sectors)**: Venture Capital e Acceleratori
- **Pagine create (sources)**: `2026-06-23-silicon-valley-yc-demo-day.md`
- **Note**: Prima esecuzione completa del pipeline di trascrizione `yt_transcriber.py` su file inbox, conclusa con estrazione automatizzata entità tramite piano e inserimento strutturato.

---

## [2026-06-23] schema-update | Regola naming Sources + rename retroattivo

- Aggiunta regola in `AGENTS.md` (sezione "Naming delle pagine Source"): ogni file in `wiki/sources/` deve usare il formato `YYYY-MM-DD-slug-descrittivo.md`.
- Rinominato retroattivamente `vYF1FSY303Q.md` → `2026-06-23-silicon-valley-yc-demo-day.md`.
- Aggiornati 13 file (people + companies) che contenevano il link `[[vYF1FSY303Q]]` al nuovo nome `[[2026-06-23-silicon-valley-yc-demo-day]]`.

---

## [2026-06-23] ingest-piccoli-mondi | 22 Video del Canale Piccoli Mondi

- **Fonte**: File `progetto-network-mio-e-piccoli-mondi.md` (tabella pre-mappata con 22 video)
- **Pagine create (people)**: Carlo Ferraris, Giacomo Spazzini, Vittoria Zanetti, Paolo Fois, Andrew Propaganda, Ivan Leone, Daniele Francescon, Davide Trabucchi, Bruno Casanovas, Alex Benlloch, Jacopo Mele, Antonio Dikele Distefano, Andrea Muzii, Stefano Callegari, Riccardo Donadon, Sebastiano Fazioli, Giuliano (Caffè Design), Nanni (Caffè Design), Breccia (Caffè Design), Mattia Caramel, Giulio Marchioni, Edoardo Di Lella, Tito Rapetti, Gabriele Locci
- **Pagine create (companies)**: Rolling Square, GS Loft, Poke House, Lexroom, Propaganda Clothing, Donts, Serenis, Dalfilo, Nude Project, Moonstone, Esse Magazine, Accademia Atena, Trapizzino, H-FARM, Big Soup, Caffè Design, Work Louder, Cocci, Starting Finance, Maison Rapito, Insulti Luminosi
- **Pagine create (sectors)**: Consumer Tech, Agroalimentare e Food, Moda e Streetwear, E-commerce e Arredo, Editoria e Media, Education, Venture Capital ed Education, Moda e Vintage, Editoria e Finanza
- **Pagine modificate (sectors)**: Fitness e Benessere, Software SaaS, Digital Health, Venture Capital, Lusso e Moda, Architettura e Design, Consumer Tech, Moda e Streetwear, Agroalimentare e Food, E-commerce e Arredo
- **Pagine modificate (people)**: Marcello Ascani (aggiunto link a Piccoli Mondi come progetto editoriale)
- **Note**: Ingestion completa dei 22 video del format Piccoli Mondi (canale YouTube affiliato a Marcello Ascani), inserito nello stesso vault `mio-vault-marcello`. Le entità sono collegate direttamente al network esistente tramite aggiornamento dei settori già presenti. Totale aggiunto: 24 persone, 21 aziende, 9 settori nuovi + aggiornamenti a 10 settori esistenti.
