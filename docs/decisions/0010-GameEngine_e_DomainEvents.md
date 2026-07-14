# Decisione #0010

## Titolo

Il Game Engine comunica attraverso Domain Events

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

Il Game Engine comunica internamente esclusivamente attraverso Domain Events.

Un Domain Event rappresenta un fatto già accaduto all'interno del dominio di gioco e costituisce il meccanismo ufficiale di comunicazione tra i diversi moduli dell'Engine.

I Domain Events sono distinti dagli Eventi di gioco (Spedizioni) e non contengono elementi narrativi.

---

## Definizione

Un Domain Event descrive un cambiamento di stato del sistema.

Esempi:

- ExpeditionStarted
- ExpeditionCompleted
- NodeEntered
- NodeCompleted
- RewardGranted
- PlayerLevelUp
- ItemEquipped
- MercenaryHired
- AchievementUnlocked

---

## Principio

Ogni componente dell'Engine pubblica Domain Events ma non conosce i componenti che li consumeranno.

Ogni modulo interessato può sottoscrivere uno o più Domain Events e reagire autonomamente.

---

## Obiettivi

- Ridurre l'accoppiamento tra i moduli.
- Favorire l'estendibilità del sistema.
- Consentire l'aggiunta di nuove funzionalità senza modificare il codice esistente.
- Centralizzare la propagazione degli effetti di gioco.

---

## Benefici

- Modularità
- Elevata testabilità
- Semplicità di estensione
- Riduzione delle dipendenze
- Maggiore leggibilità del flusso applicativo

---

## Distinzione

### Evento di gioco

Rappresenta un contenuto vissuto dal giocatore durante una spedizione.

Esempi:

- Mercante Errante
- Trappola
- Fontana Sacra
- Boss Finale

---

### Domain Event

Rappresenta un fatto accaduto nel sistema.

Esempi:

- ExpeditionCompleted
- RewardGranted
- CardLevelUp

---

## Impatto sul progetto

Questa decisione influenza direttamente:

- Game Engine
- Event System
- Application Services
- Progression Engine
- Reward Engine
- Achievement System
- Logging
- Future Notification System

---

## Decisioni correlate

- Decisione #0008 – Il motore della Taverna è basato su Nodi e non su Eventi
- Decisione #0009 – Il Game Engine è indipendente dall'interfaccia utente e dalla persistenza

---

## Note

L'introduzione di nuovi sistemi dovrà avvenire preferibilmente tramite l'ascolto dei Domain Events esistenti.

L'emissione di nuovi Domain Events dovrà essere limitata ai casi in cui rappresentino un effettivo cambiamento dello stato del dominio.