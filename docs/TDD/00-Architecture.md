# 00 - Software Architecture

**Versione:** 1.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 13 Luglio 2026

---

# Scopo

Questo documento definisce l'architettura software ufficiale della **Taverna dello Svincolato**.

Costituisce il riferimento tecnico per tutte le decisioni di sviluppo e descrive la suddivisione del sistema nei suoi principali livelli logici.

Ogni nuovo componente software dovrà rispettare le regole qui descritte.

---

# Filosofia Architetturale

La Taverna dello Svincolato è progettata seguendo un'architettura **Layered + Domain Driven + Event Driven**.

Le regole del gioco rappresentano il vero valore dell'applicazione e devono rimanere completamente indipendenti da:

- interfaccia utente;
- database;
- framework;
- CMS;
- tecnologia di persistenza.

L'interfaccia e la persistenza sono considerate adattatori verso il mondo esterno.

---

# Architettura Generale

```
Browser
    │
Presentation Layer
    │
Application Services
    │
Game Engine
    │
Domain Model
    │
Persistence Layer
    │
MySQL
```

Ogni livello comunica esclusivamente con quello immediatamente sottostante.

Sono vietate dipendenze che saltino uno o più livelli.

---

# Layer dell'applicazione

## Presentation Layer

Responsabilità:

- Rendering HTML
- CSS
- JavaScript
- Gestione richieste HTTP
- Gestione Sessione
- Interazione con l'utente

Non contiene alcuna regola di business.

---

## Application Services

Coordina i casi d'uso dell'applicazione.

Responsabilità:

- orchestrazione dei flussi;
- validazioni applicative;
- gestione delle transazioni;
- coordinamento dei componenti.

Non implementa regole di gioco.

---

## Game Engine

Rappresenta il cuore del sistema.

Responsabilità:

- esecuzione delle spedizioni;
- gestione dei Nodi;
- applicazione delle regole;
- risoluzione degli Eventi;
- gestione della casualità;
- emissione dei Domain Events.

Il Game Engine non conosce né il database né l'interfaccia utente.

---

## Domain Model

Descrive il mondo della Taverna.

Contiene:

- Entità;
- Value Object;
- Regole del dominio;
- Relazioni;
- Invarianti.

Il Domain Model rappresenta il linguaggio ufficiale del progetto.

---

## Persistence Layer

Responsabile esclusivamente della persistenza.

Comprende:

- Repository;
- Mapper;
- Query;
- Database.

Non contiene logica di business.

---

# Flusso di una richiesta

```
Utente

↓

Presentation

↓

Application Service

↓

Game Engine

↓

Domain Model

↓

Repository

↓

Database
```

Il risultato percorre il flusso inverso fino alla presentazione.

---

# Principi Fondamentali

## Single Responsibility

Ogni componente possiede una sola responsabilità.

---

## Separation of Concerns

Ogni layer gestisce esclusivamente il proprio ambito.

---

## Domain First

Le regole del dominio hanno sempre priorità rispetto alle esigenze tecniche.

---

## Event Driven

La comunicazione tra i moduli del Game Engine avviene tramite Domain Events.

---

## Data Driven

Contenuti e configurazioni sono rappresentati come dati.

Il codice implementa i comportamenti.

---

## Engine First

Il motore deve poter essere eseguito senza interfaccia grafica.

---

# Dipendenze Consentite

```
Presentation

↓

Application

↓

Engine

↓

Domain

↓

Persistence
```

Sono vietate dipendenze inverse.

---

# Tecnologie

## Linguaggio

PHP 8.x

---

## Database

MySQL

---

## Frontend

HTML5

CSS3

JavaScript

---

## Versionamento

Git

GitHub

---

## Hosting

Hosting condiviso

FTP

---

# Obiettivo

L'architettura deve consentire la crescita del progetto senza richiedere modifiche strutturali al Game Engine.

Nuove funzionalità dovranno essere introdotte attraverso nuovi componenti o nuovi contenuti, preservando la stabilità del nucleo applicativo.

---

# Decisioni Correlate

- Decisione #0006 – Modello di Dominio e Regole di Proprietà
- Decisione #0008 – Il motore è basato su Nodi
- Decisione #0009 – Il Game Engine è indipendente da UI e Database
- Decisione #0010 – Comunicazione tramite Domain Events

---

# Documenti Correlati

- 01 - Domain Model
- 02 - Behavior Model
- 03 - Application Services
- 04 - Game Engine