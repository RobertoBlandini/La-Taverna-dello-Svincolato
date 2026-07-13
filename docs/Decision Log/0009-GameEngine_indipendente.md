# Decisione #0009

## Titolo

Il Game Engine è indipendente dall'interfaccia utente e dalla persistenza

---

## Categoria

🏛️ Fondamentale

---

## Stato

🟢 Attiva

---

## Versione

v0.1

---

## Data

13 Luglio 2026

---

## Responsabile

Roberto Blandini

---

## Decisione

Il Game Engine costituisce il cuore della Taverna dello Svincolato.

L'Engine contiene tutte le regole del gioco e non deve dipendere direttamente né dall'interfaccia utente né dal sistema di persistenza.

Ogni meccanica di gioco deve poter essere eseguita indipendentemente dalla tecnologia utilizzata per presentare l'interfaccia o memorizzare i dati.

---

## Motivazione

Separare il motore di gioco dalle tecnologie esterne garantisce maggiore modularità, testabilità ed evoluzione del progetto.

L'interfaccia utente e il database rappresentano dettagli implementativi, mentre il comportamento del gioco costituisce il vero valore dell'applicazione.

---

## Architettura

L'applicazione è organizzata in livelli.

Presentation Layer

↓

Application Services

↓

Game Engine

↓

Domain Model

↓

Persistence Layer

↓

MySQL

Ogni livello comunica esclusivamente con quello immediatamente sottostante.

Sono vietate dipendenze che saltino uno o più livelli.

---

## Responsabilità del Game Engine

Il Game Engine è responsabile di:

- esecuzione delle spedizioni;
- gestione dei Nodi;
- applicazione delle regole di gioco;
- calcolo degli esiti;
- gestione della casualità;
- generazione delle ricompense;
- applicazione delle conseguenze.

Il Game Engine non è responsabile di:

- rendering HTML;
- gestione delle richieste HTTP;
- interrogazioni SQL;
- autenticazione;
- gestione della sessione utente.

---

## Benefici

- Separazione delle responsabilità
- Elevata manutenibilità
- Facilità di testing
- Possibilità di sostituire il frontend
- Possibilità di sostituire il layer di persistenza
- Maggiore riutilizzabilità del codice

---

## Impatto sul progetto

Questa decisione influenza direttamente:

- Software Architecture
- Application Services
- Domain Model
- Behavior Model
- Event System
- Repository Layer
- Frontend
- Database

---

## Decisioni correlate

- Decisione #0006 – Modello di Dominio e Regole di Proprietà
- Decisione #0008 – Il motore della Taverna è basato su Nodi e non su Eventi

---

## Note

Il Game Engine rappresenta il nucleo dell'applicazione.

Ogni nuova funzionalità dovrà essere progettata in modo da preservarne l'indipendenza.

L'interfaccia utente e la persistenza sono considerate adattatori verso il mondo esterno e non devono influenzare le regole del gioco.