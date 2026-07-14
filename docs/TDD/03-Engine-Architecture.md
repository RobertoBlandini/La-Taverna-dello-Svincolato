# 03 - Engine Architecture

**Versione:** 1.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 14 Luglio 2026

---

# Scopo

Questo documento descrive l'architettura interna del Game Engine della **Taverna dello Svincolato**.

L'Engine è il cuore del sistema: interpreta il Domain Model, esegue le regole del gioco e coordina lo svolgimento delle spedizioni.

L'Engine è completamente indipendente da:

- Interfaccia Utente
- Database
- Framework
- Hosting
- CMS

---

# Filosofia

Il Game Engine implementa esclusivamente comportamenti.

Non contiene:

- contenuti narrativi;
- logiche di presentazione;
- codice di persistenza.

I contenuti sono dati.

Le regole appartengono al motore.

---

# Principi Architetturali

L'Engine segue i seguenti principi:

- Modularità
- Single Responsibility
- Event Driven
- Domain Driven
- Testabilità
- Estensibilità

Ogni modulo possiede una responsabilità ben definita.

Le comunicazioni avvengono tramite Domain Events.

---

# Architettura Generale

```
                   Game Engine

                         │

        ┌────────────────┼────────────────┐

        │                │                │

   Core Engine     Gameplay Engine   Domain Events

        │                │

        └────────────────┼────────────────┘

                 Domain Model
```

---

# Core Engine

Il Core Engine contiene i moduli fondamentali necessari all'esecuzione del gioco.

## Expedition Engine

Coordina il ciclo di vita di una spedizione.

Responsabilità:

- avvio;
- avanzamento;
- conclusione;
- gestione dello stato della spedizione.

---

## Node Engine

Gestisce il Nodo corrente.

Responsabilità:

- eseguire il Nodo;
- proporre le scelte disponibili;
- raccogliere l'azione del giocatore;
- restituire l'esito.

---

## Rule Engine

Implementa le regole del gioco.

Responsabilità:

- calcolo delle probabilità;
- verifica dei requisiti;
- applicazione delle abilità;
- applicazione dei modificatori;
- determinazione degli esiti.

---

## Validation Engine

Garantisce la coerenza del dominio prima dell'esecuzione delle azioni.

Esempi:

- formazione valida;
- requisiti della spedizione soddisfatti;
- equipaggiamento compatibile;
- scelta consentita;
- nodo raggiungibile.

---

## RNG Engine

Gestisce ogni componente casuale del gioco.

Tutte le estrazioni casuali devono transitare attraverso questo modulo.

---

## Event Dispatcher

Gestisce la propagazione dei Domain Events.

I moduli dell'Engine non comunicano direttamente tra loro.

Ogni interazione avviene mediante pubblicazione e sottoscrizione di Domain Events.

---

# Gameplay Engine

Il Gameplay Engine contiene i sistemi che implementano la progressione del giocatore.

Nuovi moduli possono essere aggiunti senza modificare il Core Engine.

---

## Reward Engine

Calcola e distribuisce:

- esperienza;
- oro;
- materiali;
- equipaggiamenti;
- carte;
- ricompense speciali.

---

## Progression Engine

Aggiorna:

- livello;
- esperienza;
- crescita della Compagnia;
- progressione del profilo.

---

## Achievement Engine

Gestisce gli obiettivi permanenti.

---

## Reputation Engine

Gestisce la reputazione dell'Allenatore.

---

## Album Engine

Aggiorna la collezione permanente del giocatore.

---

## Statistics Engine

Aggiorna statistiche e storico delle attività.

---

# Flusso di una Spedizione

```
Compagnia

↓

Validation Engine

↓

Expedition Engine

↓

Node Engine

↓

Rule Engine

↓

Domain Events

↓

Gameplay Engine

↓

Risultato
```

Il salvataggio del risultato è responsabilità dell'Application Layer e non del Game Engine.

---

# Domain Events

L'Engine comunica esclusivamente tramite Domain Events.

Esempi:

- ExpeditionStarted
- ExpeditionCompleted
- NodeEntered
- NodeCompleted
- RewardGranted
- PlayerLevelUp
- MercenaryHired
- AchievementUnlocked

I Domain Events rappresentano fatti accaduti nel dominio e non eventi narrativi.

---

# Estendibilità

Nuove funzionalità devono essere implementate come nuovi moduli o nuovi listener di Domain Events.

Il Core Engine non deve essere modificato per introdurre nuovi contenuti di gioco.

---

# Responsabilità escluse

Il Game Engine non gestisce:

- rendering HTML;
- CSS;
- JavaScript;
- autenticazione;
- sessioni;
- query SQL;
- accesso al database;
- API esterne;
- sincronizzazione con Fantacalcio.

Queste responsabilità appartengono rispettivamente al Presentation Layer, all'Application Layer e all'Infrastructure Layer.

---

# Obiettivo

Il Game Engine deve rappresentare un motore indipendente, modulare ed estensibile, capace di eseguire qualsiasi contenuto del gioco senza dipendere dalla tecnologia utilizzata.

---

# Decisioni Correlate

- Decisione #0008 – Il motore è basato su Nodi
- Decisione #0009 – Il Game Engine è indipendente da UI e Database
- Decisione #0010 – Comunicazione tramite Domain Events
- Decisione #0011 – La Stagione è un Aggregate Root del dominio
- Decisione #0012 – Separazione tra Carta, Carta Stagionale e Membro della Compagnia

---

# Documenti Correlati

- 00 - Software Architecture
- 01 - Domain Model & Ubiquitous Language
- 02 - Behavior Model
- 04 - Application Services
- 05 - Database Model
- 06 - Synchronization