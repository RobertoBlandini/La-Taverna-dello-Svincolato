# ADR-0014 — Technology Stack & Engineering Standards

**Status:** 🟢 Accepted

**Data:** 2026-07-15

**Autori:** Roberto Blandini

**Versione:** 1.0

---

# Contesto

La Taverna dello Svincolato è un progetto a lungo termine che richiede una base tecnologica stabile, moderna e facilmente manutenibile.

Lo stack tecnologico deve supportare lo sviluppo incrementale del progetto, garantire semplicità di manutenzione e consentire una futura evoluzione dell'infrastruttura senza influenzare il Domain Model.

Attualmente il progetto verrà distribuito su un server Linux dedicato con Hestia Control Panel, utilizzato anche per altri progetti aziendali.

L'ambiente di produzione supporta PHP 8.0 e rappresenta il vincolo tecnologico iniziale del progetto.

---

# Decisione

Il progetto adotterà il seguente stack tecnologico.

---

# Backend

| Componente | Tecnologia |
|------------|------------|
| Linguaggio | PHP 8.0 |
| Framework | Laravel 9 LTS |
| ORM | Eloquent |
| CLI | Artisan |

---

# Frontend

| Componente | Tecnologia |
|------------|------------|
| Template Engine | Blade |
| Reactive Components | Livewire 3 |
| JavaScript | Alpine.js |
| CSS Framework | Tailwind CSS |

---

# Database

| Componente | Tecnologia |
|------------|------------|
| Database | MySQL 8 |

---

# Cache

Redis

---

# Queue

Laravel Queue

Driver Redis.

---

# Session

Database Driver.

---

# Storage

Laravel Storage.

Driver Local.

Predisposizione futura per storage compatibili con Amazon S3.

---

# Testing

Il progetto adotterà:

- Pest
- Laravel Testing Framework

---

# Code Quality

Il progetto utilizzerà:

- Laravel Pint
- PHPStan

L'analisi statica farà parte del normale ciclo di sviluppo.

---

# Versionamento

Git

GitHub

GitHub Flow

Il branch `main` conterrà esclusivamente codice stabile.

---

# Runtime Environment

## Ambiente di Produzione

Server Linux dedicato

Hestia Control Panel

Nginx

Apache (Reverse Proxy)

PHP-FPM

MySQL

HTTPS

L'attuale runtime di produzione utilizza PHP 8.0.

L'eventuale aggiornamento della versione di PHP sarà considerato una decisione infrastrutturale e non dovrà richiedere modifiche al Domain Model.

---

# Development Environment

Lo sviluppo dovrà essere indipendente dall'ambiente di produzione.

Il progetto prevede l'utilizzo di Docker (Laravel Sail) come ambiente di sviluppo standard.

L'obiettivo è garantire un ambiente riproducibile e facilmente configurabile su qualsiasi macchina di sviluppo.

---

# Engineering Standards

Il codice dovrà rispettare i seguenti principi:

- PSR-12
- Strict Types
- SOLID
- Domain Driven Design
- Repository Pattern (solo quando necessario)
- Dependency Injection
- Separation of Concerns
- Composition over Inheritance

---

# Tecnologie escluse

Per l'MVP non verranno adottate:

- Microservizi
- Event Sourcing
- CQRS completo
- GraphQL
- Framework JavaScript SPA (React, Vue, Angular)
- Architetture distribuite

L'obiettivo è mantenere il progetto semplice e facilmente evolvibile.

---

# Motivazione

Lo stack scelto privilegia stabilità, produttività e semplicità di manutenzione.

Le tecnologie adottate sono ampiamente consolidate nell'ecosistema PHP e Laravel e consentono di sviluppare rapidamente nuove funzionalità senza introdurre complessità non necessarie.

La separazione tra ambiente di sviluppo e ambiente di produzione garantisce inoltre la possibilità di evolvere l'infrastruttura senza impatti sull'architettura applicativa.

---

# Conseguenze

## Benefici

- Stack moderno e maturo.
- Ampia documentazione e community.
- Facilità di onboarding.
- Ridotta complessità tecnologica.
- Evoluzione indipendente dell'infrastruttura.

## Svantaggi

- Compatibilità iniziale limitata a PHP 8.0.
- Alcune funzionalità delle versioni più recenti di PHP non saranno disponibili fino all'aggiornamento del runtime.

---

# Alternative Valutate

## PHP 8.4 + Laravel 12

Scartata.

Richiede un aggiornamento dell'infrastruttura attualmente non disponibile.

---

## Framework JavaScript SPA

Scartati.

Per l'MVP introdurrebbero una complessità non giustificata.

Livewire offre tutte le funzionalità necessarie mantenendo un'architettura più semplice.

---

## PostgreSQL

Valutato.

Non adottato poiché MySQL rappresenta lo standard già utilizzato nell'infrastruttura esistente e soddisfa pienamente i requisiti del progetto.

---

# Decisioni Correlate

- ADR-0006 — Regole di proprietà del dominio
- ADR-0009 — Separazione tra Domain Model e livelli tecnici
- ADR-0013 — Classificazione della Documentazione di Progetto

---

# Documenti Correlati

- Project Charter
- Technical Design Document
- Technical Infrastructure
- Technical Bootstrap
- Product Backlog

---

# Stato Finale

Questa ADR definisce lo stack tecnologico e gli standard ingegneristici ufficiali della Taverna dello Svincolato.

Eventuali modifiche future dovranno essere formalizzate tramite una nuova ADR o mediante la sostituzione della presente decisione.