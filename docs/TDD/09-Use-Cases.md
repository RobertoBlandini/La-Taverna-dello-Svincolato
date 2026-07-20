# Use Cases

**Versione:** 1.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 15 Luglio 2026

---

# Scopo

Questo documento descrive tutti i casi d'uso del sistema.

Un Use Case rappresenta un'interazione significativa tra il giocatore e il dominio.

Non descrive l'implementazione tecnica ma il comportamento atteso.

---

# UC-001 — Avviare una Spedizione

## Scopo

Permettere al giocatore di iniziare una nuova spedizione.

## Attore

Giocatore

## Precondizioni

- Compagnia valida.
- Nessuna spedizione in corso.
- Requisiti della spedizione soddisfatti.

## Flusso Principale

1. Il giocatore seleziona una spedizione.
2. Il sistema verifica i requisiti.
3. Viene generata la spedizione.
4. Il percorso viene inizializzato.
5. La Compagnia entra nello stato "In Spedizione".

## Eccezioni

- Compagnia non valida.
- Requisiti non soddisfatti.
- Spedizione già attiva.

## Postcondizioni

- Spedizione creata.
- Stato persistito.

## Domain Events

- ExpeditionStarted

---

# UC-002 — Risolvere un Nodo

## Scopo

Permettere al giocatore di affrontare un nodo della spedizione.

## Attore

Giocatore

## Flusso Principale

1. Entrata nel nodo.
2. Presentazione del contenuto.
3. Eventuale scelta.
4. Risoluzione.
5. Applicazione effetti.
6. Persistenza.

## Domain Events

- NodeEntered
- PlayerChoiceMade
- NodeResolved

---

# UC-003 — Terminare una Spedizione

## Scopo

Concludere una spedizione.

## Flusso

1. Calcolo ricompense.
2. Aggiornamento Compagnia.
3. Aggiornamento Stagione.
4. Salvataggio.

## Domain Events

- ExpeditionCompleted
- CompanyUpdated
- SeasonProgressed

---

# UC-004 — Gestire la Compagnia

Permette di modificare la composizione della Compagnia all'interno della Taverna.

---

# UC-005 — Consultare il Libro delle Compagnie

Permette di consultare la cronologia delle spedizioni e delle imprese memorabili.

---

# UC-006 — Gestire il Mazzo

Permette di modificare il mazzo di carte utilizzato dalla Compagnia.

---

# UC-007 — Consultare la Stagione

Permette di visualizzare lo stato della stagione corrente e i progressi della Compagnia.

---

# UC-008 — Salvare la Progressione

Permette al sistema di registrare lo stato corrente del dominio.

---

# Raggruppamento

## Sessione

- UC-001
- UC-008

## Compagnia

- UC-004
- UC-006

## Spedizioni

- UC-001
- UC-002
- UC-003

## Stagione

- UC-007

## Lore

- UC-005

---

# Principio Architetturale

Ogni Use Case rappresenta un singolo comportamento del sistema.

Ogni Use Case dovrà essere implementato in modo indipendente e rispettare il principio di responsabilità singola.

---

# Documenti Correlati

- Game Flow
- State Machine
- Domain Model
- Engine Architecture