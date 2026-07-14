# 07 - Technical Infrastructure

**Versione:** 1.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 14 Luglio 2026

---

# Scopo

Questo documento descrive l'infrastruttura tecnica della **Taverna dello Svincolato**.

L'obiettivo è documentare l'ambiente di sviluppo, distribuzione ed esecuzione dell'applicazione.

L'infrastruttura è considerata un dettaglio implementativo e non influenza il Domain Model o il Game Engine.

---

# Filosofia

La tecnologia deve adattarsi all'architettura.

Mai il contrario.

Il Domain Model e il Game Engine devono poter sopravvivere a qualsiasi cambiamento tecnologico.

---

# Stack Tecnologico

## Linguaggio

PHP 8.x

---

## Database

MySQL 8.x

---

## Frontend

HTML5

CSS3

JavaScript (Vanilla)

---

## Versionamento

Git

GitHub

---

## IDE

Visual Studio Code

---

## Hosting

Hosting condiviso con supporto:

- PHP
- MySQL
- FTP
- HTTPS

---

# Repository

La repository GitHub rappresenta l'unica fonte ufficiale del codice sorgente.

Il branch principale contiene esclusivamente codice stabile.

Le modifiche vengono sviluppate su branch dedicati e integrate tramite Pull Request.

---

# Struttura del Progetto

```
docs/
src/
public/
config/
storage/
tests/
vendor/
```

La documentazione è mantenuta separata dal codice applicativo.

---

# Configurazione

I parametri di configurazione sono esterni al codice.

Esempi:

- connessione database;
- credenziali API;
- percorsi;
- modalità debug;
- ambiente di esecuzione.

I dati sensibili non devono essere versionati.

---

# Logging

Il sistema registra:

- errori applicativi;
- errori di dominio;
- sincronizzazioni;
- eventi critici;
- operazioni amministrative.

I log devono consentire la ricostruzione delle operazioni rilevanti.

---

# Backup

Devono essere previsti backup periodici di:

- database;
- file di configurazione;
- contenuti statici.

Le procedure di ripristino devono essere documentate.

---

# Deployment

Ogni rilascio deve seguire una procedura controllata.

Flusso consigliato:

```
Sviluppo

↓

Commit

↓

Push

↓

Pull Request

↓

Merge

↓

Deploy

↓

Verifica
```

---

# Gestione delle Dipendenze

Le librerie di terze parti devono essere ridotte al minimo.

Ogni dipendenza introdotta deve essere motivata, documentata e facilmente sostituibile.

---

# Sicurezza

L'applicazione deve adottare almeno le seguenti pratiche:

- utilizzo esclusivo di HTTPS;
- validazione degli input;
- escaping dell'output;
- gestione sicura delle sessioni;
- protezione CSRF;
- password cifrate;
- principio del minimo privilegio.

---

# Ambienti

Sono previsti almeno due ambienti:

## Sviluppo

Utilizzato per l'implementazione e il testing.

---

## Produzione

Ambiente stabile accessibile agli utenti finali.

Ogni modifica deve essere validata prima del rilascio.

---

# Monitoraggio

Devono essere monitorati:

- errori PHP;
- disponibilità del servizio;
- sincronizzazioni;
- backup;
- prestazioni del database.

---

# Evoluzione Tecnologica

L'infrastruttura potrà evolvere nel tempo.

Eventuali cambiamenti di framework, hosting o database non dovranno richiedere modifiche al Domain Model o al Game Engine.

---

# Obiettivo

Garantire un'infrastruttura stabile, documentata e facilmente evolvibile, mantenendo separata la tecnologia dalle regole del dominio.

---

# Decisioni Correlate

- Decisione #0009 – Il Game Engine è indipendente dalla UI e dalla persistenza.
- Decisione #0010 – Comunicazione tramite Domain Events.

---

# Documenti Correlati

- 00 - Software Architecture
- 03 - Engine Architecture
- 04 - Application Services
- 05 - Database Model
- 06 - External Integration