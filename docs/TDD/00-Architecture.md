# 00 - Software Architecture

## Obiettivo

Descrivere l'architettura software della Taverna dello Svincolato.

---

# Filosofia

L'applicazione è organizzata in livelli.

Ogni livello comunica esclusivamente con quello immediatamente sottostante.

Nessun componente può saltare un livello.

---

# Livelli

## Presentation Layer

Browser

HTML

CSS

JavaScript

---

## Application Layer

Coordina i casi d'uso.

Non contiene logica di business.

---

## Game Engine

Contiene tutte le regole del gioco.

Rappresenta il cuore dell'applicazione.

---

## Domain Layer

Contiene gli oggetti del dominio.

Allenatore

Compagnia

Carta

Evento

Nodo

Equipaggiamento

...

---

## Persistence Layer

Repository

Mapper

MySQL

---

# Principi

- Separazione delle responsabilità
- Single Responsibility
- Nessuna logica SQL nel Domain
- Nessuna logica HTML nel Domain
- Motore indipendente dall'interfaccia