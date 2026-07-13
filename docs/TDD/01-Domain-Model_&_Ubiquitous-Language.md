# 01 - Domain Model & Ubiquitous Language

**Versione:** 2.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 13 Luglio 2026

---

# Scopo

Questo documento definisce il modello di dominio della **Taverna dello Svincolato**.

Il Domain Model rappresenta il linguaggio ufficiale del progetto e descrive gli oggetti fondamentali, le loro responsabilità e le relazioni reciproche.

Non rappresenta il database.

Non rappresenta il codice.

Rappresenta il mondo del gioco.

---

# Filosofia

Ogni elemento del dominio possiede:

- una responsabilità;
- uno stato;
- un comportamento.

Le entità non sono semplici contenitori di dati.

Le regole del gioco appartengono al dominio.

---

# Ubiquitous Language

I termini riportati in questo documento sono gli unici nomi ufficiali utilizzabili nel progetto.

Lo stesso termine dovrà essere utilizzato nel:

- GDD;
- TDD;
- Codice PHP;
- Database (quando possibile);
- Documentazione tecnica.

---

# Entità Principali

## Allenatore

Rappresenta il giocatore.

È il proprietario della progressione.

Possiede:

- Compagnia
- Album
- Inventario
- Reputazione
- Achievement
- Storico Spedizioni
- Statistiche

L'Allenatore persiste tra le stagioni.

---

## Compagnia

Rappresenta il gruppo operativo utilizzato nelle spedizioni.

La Compagnia è un'entità persistente.

Contiene:

- Membri
- Formazione
- Morale
- Coesione
- Inventario condiviso
- Bonus

Responsabilità:

- validare la formazione;
- calcolare la coesione;
- verificare i requisiti di partenza;
- applicare bonus di gruppo.

---

## Membro della Compagnia

Rappresenta una specifica istanza di un calciatore all'interno della Compagnia.

Possiede:

- livello;
- esperienza;
- equipaggiamento;
- stato;
- statistiche derivate;
- progressione.

Non coincide con la Carta.

---

## Carta

Rappresenta la definizione permanente di un calciatore.

Contiene:

- identità;
- statistiche base;
- ruolo;
- rarità;
- artwork;
- metadati.

La Carta è immutabile durante una stagione.

---

## Equipaggiamento

Oggetto equipaggiabile da un Membro della Compagnia.

Può modificare:

- statistiche;
- abilità;
- sinergie.

---

## Mercenario

Unità temporanea reclutabile.

Non appartiene permanentemente alla Compagnia.

Può partecipare a una o più spedizioni in base alle proprie regole.

---

## Nodo

Unità comportamentale del Game Engine.

Definisce:

- input;
- scelte;
- logica;
- output.

Non contiene elementi narrativi.

---

## Evento

Istanza narrativa di un Nodo.

Contiene:

- titolo;
- descrizione;
- personaggi;
- ricompense;
- varianti.

Non contiene logica.

---

## Spedizione

Sequenza ordinata di Nodi.

Rappresenta una singola avventura affrontata dalla Compagnia.

---

## Regione

Area geografica del mondo di gioco.

Contiene:

- spedizioni;
- bioma;
- fazioni;
- nemici;
- ricompense;
- eventi esclusivi.

La Regione rappresenta il contenitore narrativo delle Spedizioni.

---

## Inventario

Insieme degli oggetti posseduti dall'Allenatore o dalla Compagnia.

Gestisce:

- consumabili;
- equipaggiamenti;
- materiali;
- reliquie.

---

## Album

Sistema di collezione permanente.

Registra le Carte ottenute e i relativi progressi.

---

## Achievement

Obiettivi permanenti del profilo.

Sono indipendenti dalla stagione.

---

# Relazioni

Allenatore

↓

possiede

↓

Compagnia

↓

contiene

↓

Membri

↓

utilizzano

↓

Equipaggiamento

---

Allenatore

↓

possiede

↓

Album

↓

contiene

↓

Carte

---

Compagnia

↓

affronta

↓

Spedizione

↓

composta da

↓

Nodi

↓

generano

↓

Eventi

---

# Value Object

Nel dominio esistono oggetti privi di identità.

Esempi:

- Esperienza
- Oro
- Livello
- Coordinate
- Ricompensa
- Probabilità
- Modificatore
- Statistiche

Sono definiti esclusivamente dal proprio valore.

---

# Domain Events

Il dominio produce eventi che rappresentano cambiamenti di stato.

Esempi:

- ExpeditionStarted
- ExpeditionCompleted
- NodeCompleted
- RewardGranted
- CardLevelUp
- MercenaryHired

I Domain Events non sono Eventi narrativi.

---

# Invarianti

Le seguenti regole devono essere sempre rispettate.

- Una Carta non può appartenere a più Allenatori.
- Un Membro appartiene a una sola Compagnia.
- Una Compagnia appartiene a un solo Allenatore.
- Una Spedizione utilizza una sola Compagnia.
- Un Evento deriva sempre da un Nodo.
- Un Nodo può avere molte istanze Evento.

---

# Obiettivo

Il Domain Model rappresenta il contratto semantico dell'intero progetto.

Qualsiasi evoluzione del software dovrà rispettare il linguaggio e le relazioni qui definite.

---

# Decisioni Correlate

- Decisione #0006 – Modello di Dominio e Regole di Proprietà
- Decisione #0007 – La Compagnia è un'entità persistente
- Decisione #0008 – Il motore è basato su Nodi
- Decisione #0009 – Il Game Engine è indipendente dalla UI e dalla persistenza
- Decisione #0010 – Comunicazione tramite Domain Events

---

# Documenti Correlati

- 00 - Software Architecture
- 02 - Behavior Model
- 03 - Application Services
- 04 - Engine Architecture
- GDD/06 - Compagnia
- GDD/07 - Spedizioni
- GDD/08 - Event System


