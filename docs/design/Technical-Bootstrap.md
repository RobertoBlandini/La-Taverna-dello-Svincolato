# Technical Bootstrap

**Versione:** 2.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 15 Luglio 2026

---

# Scopo

Questo documento rappresenta la checklist operativa per iniziare lo sviluppo della **Taverna dello Svincolato**.

Ogni attività dovrà essere completata nell'ordine indicato.

Il bootstrap sarà considerato concluso solamente quando tutte le attività risulteranno completate.

---

# Milestone

**Obiettivo finale**

> Ottenere una prima installazione funzionante del progetto, pronta ad ospitare il Domain Model e il Game Engine.

---

# Fase 1 — Repository

## Repository

- [ ] Clonare la repository GitHub
- [ ] Verificare il branch principale
- [ ] Verificare la struttura della repository
- [ ] Verificare la documentazione

---

# Fase 2 — Ambiente di sviluppo

## Prerequisiti

- [ ] Git installato
- [ ] Composer installato
- [ ] Node.js LTS installato
- [ ] Docker Desktop installato
- [ ] PHP installato (compatibile con Laravel)
- [ ] IDE configurato (PhpStorm o VSCode)

---

# Fase 3 — Creazione del progetto Laravel

- [ ] Creare il progetto Laravel
- [ ] Verificare l'avvio dell'applicazione
- [ ] Primo commit del framework

---

# Fase 4 — Configurazione

## Composer

- [ ] composer install

---

## Ambiente

- [ ] Creare `.env`
- [ ] Configurare `.env`
- [ ] Generare APP_KEY

---

## Database

- [ ] Creare database locale
- [ ] Configurare connessione
- [ ] Verificare connessione

---

# Fase 5 — Frontend

- [ ] Installare dipendenze Node
- [ ] Configurare Vite
- [ ] Verificare compilazione asset

---

# Fase 6 — Docker

- [ ] Configurare Laravel Sail
- [ ] Verificare avvio container
- [ ] Verificare MySQL
- [ ] Verificare Redis

---

# Fase 7 — Quality Tools

## Laravel Pint

- [ ] Installazione
- [ ] Configurazione

---

## PHPStan

- [ ] Installazione
- [ ] Livello massimo compatibile
- [ ] Prima analisi

---

## Pest

- [ ] Installazione
- [ ] Primo test
- [ ] Verifica esecuzione

---

# Fase 8 — GitHub

- [ ] Configurare `.gitignore`
- [ ] Configurare Branch Protection
- [ ] Configurare GitHub Actions
- [ ] Primo workflow CI

---

# Fase 9 — Architettura

Preparazione delle directory del progetto.

- [ ] Domain
- [ ] Application
- [ ] Infrastructure
- [ ] Presentation
- [ ] Shared

---

# Fase 10 — Verifica Finale

Il bootstrap è completato quando:

- [ ] L'applicazione si avvia correttamente
- [ ] Il database è connesso
- [ ] Gli asset vengono compilati
- [ ] Docker funziona correttamente
- [ ] Tutti i test sono verdi
- [ ] PHPStan non segnala errori
- [ ] Pint non rileva problemi
- [ ] La pipeline GitHub termina con successo

---

# Primo Commit Applicativo

Il bootstrap termina con il primo commit dedicato al progetto.

**Commit suggerito**

```text
chore: bootstrap Laravel application
```

---

# Uscita dal Bootstrap

Il progetto è considerato **Code Ready** quando:

- tutte le attività di questo documento sono completate;
- lo stack tecnologico è operativo;
- il repository è configurato;
- gli strumenti di qualità sono attivi;
- il primo ambiente di sviluppo è funzionante.

Da questo momento può iniziare l'implementazione del Domain Model.

---

# Documenti Correlati

- ADR-0014 — Technology Stack & Engineering Standards
- Technical Infrastructure
- Repository Standards
- Architecture Overview