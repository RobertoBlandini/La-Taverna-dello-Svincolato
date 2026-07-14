# Decisione #0011

## Titolo

La Stagione è un Aggregate Root del dominio

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

14 Luglio 2026

---

## Responsabile

Roberto Blandini

---

## Decisione

La Stagione rappresenta un Aggregate Root del dominio.

Ogni stagione costituisce un contesto autonomo contenente tutte le informazioni ufficiali necessarie al funzionamento del gioco.

Le modifiche introdotte da una nuova stagione non alterano le stagioni precedenti.

Ogni stagione rappresenta una fotografia completa dello stato ufficiale del mondo calcistico e delle configurazioni di gioco.

---

## Responsabilità

Una Stagione definisce:

- listone ufficiale;
- ruoli dei calciatori;
- statistiche ufficiali;
- quotazioni;
- configurazioni di sincronizzazione;
- regole stagionali;
- contenuti stagionali;
- eventi esclusivi;
- regioni abilitate.

---

## Principi

Le stagioni sono immutabili una volta concluse.

La creazione di una nuova stagione non modifica i dati storici.

Ogni Compagnia evolve attraversando le stagioni.

---

## Benefici

- Conservazione dello storico
- Supporto a modifiche annuali
- Aggiornamenti non distruttivi
- Maggiore stabilità del dominio
- Possibilità di eventi esclusivi per stagione

---

## Impatto sul progetto

Questa decisione influenza:

- Domain Model
- Synchronization
- Database Model
- Progressione
- Carte
- Spedizioni

---

## Decisioni correlate

- #0006
- #0008
- #0009
- #0010

---

## Note

La Stagione rappresenta il punto di ingresso del dominio verso il mondo reale (Fantacalcio, statistiche ufficiali, regolamenti e contenuti annuali).