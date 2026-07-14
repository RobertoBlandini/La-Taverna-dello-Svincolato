# Architecture Overview

## Obiettivo

Questo documento fornisce una panoramica dell'architettura della Taverna dello Svincolato.

---

# Visione Generale

```

Player

↓

Presentation Layer

↓

Application Services

↓

Game Engine

↓

Domain Model

↓

Repository

↓

Database

↑

External Integration

```

---

# Livelli Architetturali

## Presentation

Interfaccia utente.

---

## Application

Coordina i casi d'uso.

---

## Engine

Implementa il comportamento del gioco.

---

## Domain

Rappresenta il significato del mondo di gioco.

---

## Persistence

Gestisce la memorizzazione dei dati.

---

## External Integration

Importa dati provenienti da sistemi esterni.

---

# Documentazione Correlata

- Software Architecture
- Domain Model
- Engine Architecture
- Application Services
- Database Model
- External Integration
- Technical Infrastructure

---

# Principio Fondamentale

Ogni livello può dipendere esclusivamente dal livello sottostante.

Il Domain Model non dipende da alcun livello tecnico.

L'Engine interpreta il dominio.

L'Application coordina il motore.

La Presentation utilizza gli Application Services.