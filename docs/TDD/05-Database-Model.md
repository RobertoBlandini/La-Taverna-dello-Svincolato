# 05 - Database Model

**Versione:** 1.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 14 Luglio 2026

---

# Scopo

Questo documento descrive il modello di persistenza della **Taverna dello Svincolato**.

Il Database Model rappresenta la traduzione del Domain Model in strutture persistenti.

Non definisce le regole del gioco.

Non definisce il comportamento dell'applicazione.

Definisce esclusivamente la memorizzazione dei dati.

---

# Filosofia

Il Database è un dettaglio implementativo.

Il Domain Model rappresenta la fonte di verità.

Le modifiche al database non devono influenzare il dominio.

---

# Principi

## Domain First

Le tabelle derivano dal Domain Model.

Mai il contrario.

---

## Normalizzazione

Le informazioni permanenti vengono memorizzate una sola volta.

La duplicazione è consentita solo quando porta benefici misurabili in termini di prestazioni o storico.

---

## Integrità

Le relazioni devono essere garantite tramite chiavi e vincoli.

---

## Storicizzazione

Il database privilegia la conservazione dello storico rispetto alla sovrascrittura dei dati.

---

## Versionamento

I dati soggetti a variazioni stagionali vengono versionati.

---

# Macroaree

Il database è organizzato nelle seguenti aree logiche.

## Dominio

Contiene le entità principali.

- Allenatori
- Compagnie
- Membri
- Carte
- Carte Stagionali
- Stagioni
- Spedizioni
- Regioni

---

## Progressione

Contiene i dati persistenti del giocatore.

- esperienza
- livelli
- statistiche
- achievement
- reputazione

---

## Inventario

Contiene:

- equipaggiamenti
- materiali
- consumabili
- reliquie

---

## Gameplay

Contiene:

- spedizioni
- nodi
- eventi
- ricompense
- log

---

## Sincronizzazione

Contiene:

- importazioni
- versioni
- sorgenti
- mapping esterni
- cronologia sincronizzazioni

---

# Relazioni principali

Allenatore

↓

Compagnia

↓

Membro della Compagnia

↓

Carta Stagionale

↓

Carta

---

Carta Stagionale

↓

Stagione

---

Spedizione

↓

Nodo

↓

Evento

---

# Persistenza

Ogni Aggregate Root viene salvato tramite il proprio Repository.

Gli aggiornamenti devono mantenere la consistenza dell'intero Aggregate.

---

# Repository

Ogni Aggregate Root possiede un Repository dedicato.

Esempi:

- CoachRepository
- CompanyRepository
- ExpeditionRepository
- SeasonRepository

I Repository rappresentano l'unico punto di accesso al database.

---

# Identificativi

Ogni entità persistente possiede un identificativo univoco.

Gli identificativi sono interni al dominio e indipendenti dagli identificativi delle sorgenti esterne.

---

# Mapping Esterni

Le integrazioni con servizi esterni utilizzano tabelle di mapping dedicate.

Esempi:

- id Fantacalcio
- id FIFA
- id sorgente sincronizzazione

Il dominio non dipende mai dagli identificativi esterni.

---

# Storico

Il database conserva lo storico delle stagioni.

Le modifiche annuali non sovrascrivono i dati delle stagioni precedenti.

---

# Performance

L'ottimizzazione delle query non deve compromettere la chiarezza del modello.

Eventuali denormalizzazioni devono essere motivate e documentate.

---

# Migrazioni

Ogni modifica strutturale del database dovrà essere versionata.

Le migrazioni rappresentano la storia evolutiva della persistenza.

---

# Obiettivo

Garantire una persistenza coerente, stabile e indipendente dal dominio applicativo.

Il Database Model deve poter evolvere senza modificare le regole del gioco.

---

# Decisioni Correlate

- Decisione #0006 – Regole di proprietà del dominio
- Decisione #0007 – La Compagnia è un'entità persistente
- Decisione #0009 – Il Game Engine è indipendente dalla persistenza
- Decisione #0011 – La Stagione è un Aggregate Root
- Decisione #0012 – Separazione tra Carta, Carta Stagionale e Membro della Compagnia

---

# Documenti Correlati

- 00 - Software Architecture
- 01 - Domain Model & Ubiquitous Language
- 03 - Engine Architecture
- 04 - Application Services
- 06 - Synchronization