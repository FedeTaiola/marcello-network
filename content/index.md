# 🗺️ Indice Generale del Network

> Aggiornato automaticamente tramite query Dataview.
> **Ultimo aggiornamento**: 2026-06-23 — Ingest Piccoli Mondi (22 video) + consolidamento settori duplicati completato.

Questo vault contiene il network completo di **Marcello Ascani** e dei suoi progetti editoriali (canale YouTube principale + Piccoli Mondi), mappato in persone, aziende e settori industriali.

**Conteggio attuale (approssimativo):**
- 👤 ~97 persone
- 🏢 ~95 aziende  
- 📂 ~61 settori (inclusi redirect)

---

## 👤 Tutte le Persone
```dataview
TABLE company AS "Azienda", sector AS "Settore", role AS "Ruolo"
FROM "wiki/people"
SORT file.name ASC
```

---

## 🏢 Tutte le Aziende
```dataview
TABLE sector AS "Settore", key_people AS "Persone Chiave"
FROM "wiki/companies"
SORT file.name ASC
```

---

## 🏭 Tutti i Settori
```dataview
LIST
FROM "wiki/sectors"
WHERE type = "sector"
SORT file.name ASC
```

---

## 📹 Fonti Elaborate (Trascrizioni)
```dataview
LIST
FROM "wiki/sources"
SORT file.name ASC
```

---

## 🏷️ Per tag

### Solo persone da Piccoli Mondi
```dataview
LIST
FROM "wiki/people"
WHERE contains(tags, "piccolimondi")
SORT file.name ASC
```
