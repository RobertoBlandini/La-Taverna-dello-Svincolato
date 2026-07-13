# 05 - Game Engine

**Versione:** 1.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 13 Luglio 2026

---

# Scopo

Il Game Engine rappresenta il cuore della Taverna dello Svincolato.

È responsabile dell'esecuzione delle regole del gioco, dell'elaborazione delle spedizioni e della gestione delle interazioni tra gli elementi del dominio.

Il Game Engine non conosce l'interfaccia utente né il database.

---

# Filosofia

L'Engine non contiene contenuti.

L'Engine contiene comportamenti.

Ogni contenuto del gioco viene interpretato dal motore attraverso regole generiche.

---

# Responsabilità

Il Game Engine è responsabile di:

- esecuzione delle spedizioni;
- gestione dei Nodi;
- risoluzione degli Eventi;
- calcolo delle probabilità;
- applicazione delle conseguenze;
- gestione della progressione;
- emissione degli eventi interni.

---

# Non è responsabile di

- HTML
- CSS
- JavaScript
- WordPress
- Sessioni
- Login
- SQL
- Rendering

---

# Componenti

Il Game Engine è composto dai seguenti moduli.

## Expedition Engine

Coordina l'intera spedizione.

---

## Node Engine

Esegue i Nodi.

---

## Event Engine

Gestisce gli Eventi.

---

## Rule Engine

Applica le regole del gioco.

---

## Reward Engine

Calcola e distribuisce le ricompense.

---

## RNG Engine

Gestisce tutta la casualità.

---

## Progression Engine

Aggiorna la crescita del mondo.

---

# Flusso generale

Preparazione

↓

Validazione

↓

Avvio spedizione

↓

Nodo

↓

Evento

↓

Scelta

↓

Calcolo

↓

Conseguenze

↓

Persistenza

↓

Nodo successivo

↓

Fine spedizione

---

# Principi

Il Game Engine deve essere:

- deterministico quando possibile;
- estensibile;
- indipendente;
- modulare;
- testabile.

---

# Obiettivo

Consentire la crescita del gioco attraverso nuovi contenuti senza modificare il comportamento del motore.