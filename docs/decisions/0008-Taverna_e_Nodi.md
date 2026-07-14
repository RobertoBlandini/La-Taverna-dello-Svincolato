# 08 - Event System

**Versione:** 2.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 11 Luglio 2026

---

# Scopo del documento

L'Event System definisce la struttura con cui il motore della Taverna genera, presenta e risolve tutti gli eventi che avvengono durante una spedizione.

L'obiettivo è realizzare un sistema completamente data-driven, nel quale nuovi eventi possano essere aggiunti senza modificare il codice applicativo.

---

# Filosofia

Ogni evento rappresenta una decisione.

Il valore di un evento non dipende dalla sua difficoltà, ma dalle conseguenze che produce sulla Compagnia e sulla storia dell'Allenatore.

---

# Struttura di un Evento

Ogni evento è composto dalle seguenti sezioni.

1. Trigger
2. Contesto
3. Requisiti
4. Presentazione
5. Scelte
6. Risoluzione
7. Conseguenze
8. Persistenza

Questa struttura è comune a qualsiasi evento del gioco.

---

# Trigger

Definisce quando un evento può essere selezionato.

Esempi:

- ingresso in una spedizione;
- raggiungimento di un nodo;
- possesso di un oggetto;
- reputazione minima;
- achievement ottenuto;
- probabilità casuale.

---

# Contesto

Descrive l'ambiente in cui avviene l'evento.

Può dipendere da:

- Regione;
- Bioma;
- Tipo di spedizione;
- Meteo;
- Ora del giorno;
- Stato della Compagnia.

---

# Requisiti

Stabiliscono le condizioni necessarie affinché l'evento possa essere eseguito.

Possono riguardare:

- livello della Compagnia;
- membri presenti;
- oggetti posseduti;
- mercenari;
- morale;
- coesione;
- reputazione;
- statistiche specifiche.

---

# Presentazione

L'evento viene mostrato attraverso:

- titolo;
- descrizione narrativa;
- eventuale illustrazione;
- dialoghi;
- effetti sonori (versioni future).

---

# Scelte

Ogni evento deve proporre almeno una scelta significativa.

Le opzioni possono essere:

- garantite;
- condizionate;
- nascoste;
- sbloccabili.

Le scelte possono dipendere da:

- statistiche;
- equipaggiamento;
- composizione della Compagnia;
- achievement;
- oggetti;
- eventi precedenti.

---

# Risoluzione

Ogni scelta produce una risoluzione.

La risoluzione può essere:

- automatica;
- deterministica;
- probabilistica.

Il risultato può dipendere da:

- statistiche;
- bonus;
- sinergie;
- casualità controllata.

---

# Conseguenze

Ogni evento modifica almeno un elemento persistente del gioco.

Ad esempio:

- esperienza;
- oro;
- morale;
- coesione;
- inventario;
- equipaggiamento;
- reputazione;
- progressione narrativa;
- achievement.

---

# Persistenza

Al termine dell'evento il motore aggiorna lo stato della partita.

Le modifiche vengono registrate prima del passaggio all'evento successivo.

---

# Classificazione degli Eventi

Gli eventi possono appartenere a differenti categorie.

- Narrativi
- Combattimento
- Esplorazione
- Sociali
- Commerciali
- Puzzle
- Casuali
- Speciali
- Boss

Ogni categoria utilizza la stessa struttura logica.

---

# Principi di Design

Ogni evento deve:

- raccontare qualcosa;
- offrire almeno una decisione interessante;
- avere conseguenze misurabili;
- poter essere riutilizzato;
- poter essere esteso senza modificare il motore.

---

# Data Driven Design

Gli eventi rappresentano dati, non codice.

Il motore interpreta la definizione dell'evento e ne gestisce automaticamente il ciclo di vita.

Questo approccio permette di aggiungere nuovi contenuti senza intervenire sull'implementazione del sistema.

---

# Obiettivo

L'Event System costituisce il linguaggio attraverso cui il gioco racconta il mondo della Taverna.

Ogni avventura nasce dalla combinazione di eventi indipendenti che, insieme, generano esperienze sempre diverse per il giocatore.