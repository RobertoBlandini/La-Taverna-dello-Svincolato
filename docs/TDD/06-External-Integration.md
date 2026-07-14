# 06 - External Integration

**Versione:** 1.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 14 Luglio 2026

---

# Scopo

Questo documento descrive il sistema di integrazione tra la Taverna dello Svincolato e le sorgenti dati esterne.

L'obiettivo è importare informazioni dal mondo reale senza introdurre dipendenze nel Domain Model o nel Game Engine.

Il dominio non conosce l'origine dei dati.

Conosce solamente il loro significato.

---

# Filosofia

Le sorgenti esterne sono considerate adattatori.

Ogni integrazione traduce dati esterni in oggetti del dominio.

Nessuna API esterna è visibile al Game Engine.

---

# Architettura

```
Sorgente Esterna

↓

Provider

↓

Synchronization Engine

↓

Mapper

↓

Domain Events

↓

Repository

↓

Database
```

---

# Responsabilità

Il sistema di integrazione è responsabile di:

- importazione dati;
- validazione;
- mapping;
- versionamento;
- gestione errori;
- pubblicazione dei Domain Events.

Non implementa regole di gioco.

---

# Provider

Ogni sorgente viene implementata tramite un Provider dedicato.

Esempi:

- Fantacalcio Provider
- EA Sports Provider
- CSV Provider
- Manual Provider

Ogni Provider restituisce dati in un formato comune.

---

# Synchronization Engine

Coordina il processo di importazione.

Responsabilità:

- pianificazione;
- esecuzione;
- confronto;
- rilevamento modifiche;
- aggiornamento del dominio.

---

# Mapper

I Mapper convertono i dati esterni in oggetti del dominio.

Esempi:

- Player Mapper
- Team Mapper
- Season Mapper
- Statistics Mapper

Il mapping è l'unico punto in cui vengono utilizzati identificativi esterni.

---

# Versionamento

Ogni sincronizzazione produce una nuova versione dei dati.

Le informazioni storiche non vengono sovrascritte.

---

# Stagioni

Ogni stagione rappresenta un contesto indipendente.

Una nuova stagione genera:

- nuove Carte Stagionali;
- nuovi ruoli;
- nuove statistiche;
- nuove quotazioni;
- nuove configurazioni.

La progressione del giocatore rimane invariata.

---

# Domain Events

Il sistema pubblica Domain Events come:

- SeasonCreated
- SeasonActivated
- SeasonalCardCreated
- SeasonalCardUpdated
- SynchronizationCompleted
- SynchronizationFailed

---

# Gestione Errori

Il sistema distingue:

- errori di rete;
- errori di parsing;
- errori di validazione;
- errori di mapping.

Gli errori non compromettono l'integrità del dominio.

---

# Storico

Ogni sincronizzazione produce un log permanente contenente:

- sorgente;
- versione;
- data;
- durata;
- risultato;
- modifiche effettuate.

---

# Estendibilità

Nuove sorgenti possono essere aggiunte implementando un nuovo Provider e i relativi Mapper.

Il Domain Model e il Game Engine rimangono invariati.

---

# Obiettivo

Consentire l'evoluzione del gioco attraverso dati provenienti da sistemi esterni mantenendo il dominio completamente indipendente.

---

# Decisioni Correlate

- Decisione #0009 – Il Game Engine è indipendente dalla persistenza
- Decisione #0010 – Comunicazione tramite Domain Events
- Decisione #0011 – La Stagione è un Aggregate Root
- Decisione #0012 – Separazione tra Carta, Carta Stagionale e Membro della Compagnia

---

# Documenti Correlati

- 01 - Domain Model & Ubiquitous Language
- 03 - Engine Architecture
- 04 - Application Services
- 05 - Database Model
- 07 - Technical Infrastructure