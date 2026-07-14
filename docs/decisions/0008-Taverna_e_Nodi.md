# Decisione #0008

## Titolo

Il motore della Taverna è basato su Nodi e non su Eventi

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

11 Luglio 2026

---

## Responsabile

Roberto Blandini

---

## Decisione

Il motore di gioco della Taverna dello Svincolato è costruito attorno al concetto di Nodo.

Un Nodo rappresenta un comportamento generico del motore e definisce una precisa struttura di interazione con il giocatore.

Gli Eventi rappresentano invece le istanze narrative dei Nodi.

Il motore interpreta il tipo di Nodo e ne gestisce automaticamente il flusso di esecuzione.

---

## Definizioni

### Nodo

Un Nodo rappresenta un comportamento.

Definisce:

- input richiesti;
- regole di esecuzione;
- scelte disponibili;
- logica di risoluzione;
- output prodotti.

Il Nodo non contiene elementi narrativi specifici.

---

### Evento

Un Evento rappresenta un contenuto.

Un Evento è un'istanza di un Nodo e ne eredita il comportamento, aggiungendo:

- ambientazione;
- testo;
- personaggi;
- immagini;
- ricompense;
- varianti.

---

## Esempio

Nodo:

Mercato

Può generare Eventi differenti:

- Mercante Errante
- Nano Fabbro
- Carovana del Deserto
- Collezionista di Reliquie
- Bazar Goblin

Tutti condividono lo stesso comportamento, ma differiscono per contenuto.

---

## Obiettivi

Separare completamente:

- logica di gioco;
- contenuti;
- narrativa.

Consentire l'aggiunta di nuovi Eventi senza modificare il codice del motore.

---

## Benefici

- Maggiore modularità
- Elevata riusabilità
- Riduzione del codice duplicato
- Facilità di bilanciamento
- Espandibilità del gioco
- Semplificazione del lavoro sui contenuti

---

## Impatto sul progetto

Questa decisione influenza direttamente:

- Event System
- Spedizioni
- Regioni
- Story Mode
- Motore di gioco
- Tool di authoring
- Database
- Backend PHP

---

## Decisioni correlate

- Decisione #0003 – Le Spedizioni costituiscono il Gameplay principale
- Decisione #0006 – Modello di Dominio e Regole di Proprietà
- Decisione #0007 – La Compagnia è un'entità persistente

---

## Note

Il numero dei Nodi dovrà rimanere limitato e stabile nel tempo.

La crescita del progetto avverrà principalmente attraverso la creazione di nuovi Eventi, senza introdurre nuovi comportamenti salvo casi eccezionali.

Questa separazione rappresenta uno dei principi architetturali fondamentali del motore della Taverna.