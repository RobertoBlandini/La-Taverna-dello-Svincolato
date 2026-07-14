# Decisione #0005

## Titolo

Separazione tra Anagrafica, Carta e Istanza del Calciatore

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

Nel sistema della Taverna dello Svincolato un calciatore è rappresentato da tre entità distinte:

### Anagrafica

Rappresenta il calciatore reale.

Contiene esclusivamente informazioni oggettive e condivise tra tutti gli utenti, come identità, squadra, ruolo e statistiche ufficiali.

Esiste una sola anagrafica per ogni calciatore.

---

### Carta

Rappresenta la trasposizione fantasy del calciatore all'interno della Taverna.

Contiene gli attributi derivati, l'archetipo, il mestiere, la rarità, l'aspetto grafico e tutte le informazioni comuni a quella specifica versione della carta.

Possono esistere più carte per la stessa anagrafica (ad esempio differenti stagioni, eventi o edizioni speciali).

---

### Istanza

Rappresenta la copia posseduta da un Allenatore.

Ogni istanza mantiene la propria progressione individuale, compresi:

- livello;
- esperienza;
- equipaggiamento;
- affinità;
- fedeltà;
- cronologia delle spedizioni;
- personalizzazione.

Ogni Allenatore possiede le proprie istanze indipendentemente dagli altri.

---

## Motivazione

La separazione tra Anagrafica, Carta e Istanza permette di distinguere chiaramente i dati reali del calciatore dalle informazioni fantasy e dalla progressione personale del giocatore.

Questa architettura rende il sistema più scalabile, evita duplicazioni di dati e consente di introdurre facilmente nuove versioni delle carte senza compromettere la progressione degli Allenatori.

---

## Impatto sul progetto

Questa decisione influenza direttamente:

- Database
- Sistema Carte
- Progressione
- Equipaggiamento
- Album
- Collezionismo
- Spedizioni
- Interfaccia Utente
- Sistema Stagioni

---

## Decisioni correlate

- Decisione #0002 – L'Allenatore è il vero protagonista
- Decisione #0004 – Adozione degli Attributi Fondamentali della Taverna

---

## Note

La progressione appartiene sempre all'Istanza e mai all'Anagrafica.

Le Carte rappresentano il collegamento tra il mondo reale del calcio e il mondo fantasy della Taverna.