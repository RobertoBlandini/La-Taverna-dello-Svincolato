# 04 - Application Services

**Versione:** 1.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 14 Luglio 2026

---

# Scopo

Questo documento descrive il livello Application dell'architettura della **Taverna dello Svincolato**.

Gli Application Services rappresentano il punto di ingresso dei casi d'uso dell'applicazione.

Coordinano il flusso delle operazioni senza implementare regole di business.

---

# Filosofia

Gli Application Services:

- ricevono una richiesta;
- recuperano le entità necessarie;
- invocano il Game Engine;
- gestiscono la persistenza;
- restituiscono il risultato.

Le regole del gioco appartengono esclusivamente al Domain Model e al Game Engine.

---

# Responsabilità

Gli Application Services sono responsabili di:

- orchestrazione dei casi d'uso;
- gestione delle transazioni;
- caricamento delle entità;
- salvataggio delle modifiche;
- gestione degli errori applicativi;
- pubblicazione di eventi applicativi.

Non sono responsabili di:

- regole del gioco;
- rendering della UI;
- accesso diretto all'utente;
- calcoli di gameplay.

---

# Flusso Generale

```
Presentation Layer

↓

Application Service

↓

Repository

↓

Game Engine

↓

Repository

↓

Presentation Layer
```

L'Application Service coordina il flusso ma non prende decisioni di gameplay.

---

# Catalogo degli Application Services

## Expedition Service

Gestisce il ciclo di vita di una spedizione.

Responsabilità:

- avvio spedizione;
- caricamento della Compagnia;
- caricamento della Spedizione;
- invocazione dell'Engine;
- persistenza del risultato.

---

## Company Service

Gestisce la Compagnia.

Responsabilità:

- creazione;
- modifica formazione;
- gestione membri;
- equipaggiamento;
- validazione.

---

## Card Service

Gestisce le Carte.

Responsabilità:

- acquisizione;
- consultazione;
- evoluzione;
- sincronizzazione con la Carta Stagionale.

---

## Inventory Service

Gestisce l'inventario.

Responsabilità:

- aggiunta oggetti;
- rimozione;
- utilizzo;
- trasferimenti.

---

## Progression Service

Coordina la crescita dell'Allenatore.

Responsabilità:

- esperienza;
- livelli;
- sblocco contenuti.

---

## Synchronization Service

Coordina la sincronizzazione con le fonti esterne.

Responsabilità:

- import stagioni;
- aggiornamento listoni;
- aggiornamento statistiche;
- pubblicazione dei Domain Events conseguenti.

---

## Authentication Service

Gestisce:

- login;
- logout;
- sessione;
- autorizzazioni.

---

## Profile Service

Gestisce il profilo dell'Allenatore.

Responsabilità:

- statistiche;
- reputazione;
- achievement;
- preferenze.

---

# Pattern Operativo

Ogni Application Service segue lo stesso schema.

```
Ricezione richiesta

↓

Validazione applicativa

↓

Caricamento dati

↓

Invocazione Engine

↓

Persistenza

↓

Restituzione risultato
```

---

# Dipendenze

Gli Application Services possono dipendere da:

- Repository
- Game Engine
- Domain Model
- Servizi infrastrutturali

Non possono dipendere dalla Presentation Layer.

---

# Gestione della Persistenza

L'Application Layer è l'unico responsabile del salvataggio delle modifiche prodotte dal Game Engine.

Il Game Engine non esegue operazioni di persistenza.

---

# Gestione degli Errori

Gli Application Services intercettano:

- errori di validazione;
- errori di persistenza;
- errori infrastrutturali.

Gli errori di dominio vengono propagati dal Game Engine.

---

# Obiettivo

Gli Application Services costituiscono il punto di coordinamento dell'applicazione.

Devono rimanere sottili, prevedibili e privi di logica di business, limitandosi a orchestrare il flusso dei casi d'uso.

---

# Decisioni Correlate

- Decisione #0009 – Il Game Engine è indipendente dalla UI e dalla persistenza
- Decisione #0010 – Comunicazione tramite Domain Events
- Decisione #0011 – La Stagione è un Aggregate Root
- Decisione #0012 – Separazione tra Carta, Carta Stagionale e Membro della Compagnia

---

# Documenti Correlati

- 00 - Software Architecture
- 01 - Domain Model & Ubiquitous Language
- 03 - Engine Architecture
- 05 - Database Model
- 06 - Synchronization
- 07 - Technical Infrastructure