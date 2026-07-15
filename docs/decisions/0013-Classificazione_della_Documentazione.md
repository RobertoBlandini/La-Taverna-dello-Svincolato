# Decisione #0013

## Titolo

Classificazione della Documentazione di Progetto

---

## Stato

🟢 Accepted

---

## Data

15 Luglio 2026

---

## Contesto

Con la crescita del progetto, la documentazione è aumentata sia in quantità che in tipologia.

Inizialmente tutti i documenti erano organizzati principalmente per fase di lavoro (GDD, TDD, Roadmap), ma l'introduzione di documenti trasversali come il Project Charter, gli Architecture Principles e i documenti di progettazione dell'MVP ha evidenziato la necessità di una classificazione più chiara.

Una struttura non organizzata avrebbe reso più difficile individuare il corretto posizionamento dei nuovi documenti e avrebbe aumentato il rischio di duplicazioni o incoerenze.

---

## Decisione

La documentazione ufficiale del progetto viene classificata in quattro famiglie principali, ciascuna con uno scopo ben definito.

### 1. Game Design Document (GDD)

Descrive il gioco dal punto di vista dell'esperienza del giocatore.

Risponde alla domanda:

> **Che gioco stiamo costruendo?**

---

### 2. Technical Design Document (TDD)

Descrive l'architettura e il funzionamento tecnico del software.

Risponde alla domanda:

> **Come è costruito il software?**

---

### 3. Design Documents

Contiene i documenti di progettazione funzionale e di esperienza che definiscono prototipi, MVP e flussi di gioco.

Risponde alla domanda:

> **Come deve funzionare questa parte del gioco?**

---

### 4. Planning (Roadmap)

Contiene la pianificazione evolutiva del progetto.

Risponde alla domanda:

> **Quando realizzeremo questa funzionalità?**

---

## Conseguenze

### Benefici

- Maggiore leggibilità della repository.
- Riduzione delle ambiguità.
- Crescita ordinata della documentazione.
- Maggiore facilità di onboarding per nuovi collaboratori.
- Separazione chiara tra progettazione, architettura e pianificazione.

### Svantaggi

- Richiede maggiore disciplina nella classificazione dei nuovi documenti.
- Alcuni documenti esistenti potrebbero dover essere ricollocati durante l'evoluzione del progetto.

---

## Struttura risultante

```text
docs/
│
├── README.md
├── PROJECT_CHARTER.md
│
├── gdd/
├── tdd/
├── decisions/
├── glossary/
├── architecture/
├── design/
└── roadmap/
```

---

## Motivazione

La documentazione rappresenta una componente fondamentale dell'architettura del progetto.

Classificarla in base al suo scopo, anziché alla fase di sviluppo o alla cronologia con cui viene prodotta, garantisce maggiore coerenza, facilita la manutenzione e consente alla repository di evolvere senza perdere chiarezza.

---

## Decisioni Correlate

- Decisione #0001 – Documentazione come fonte di verità del progetto.
- Decisione #0005 – Glossario come Ubiquitous Language.
- Decisione #0009 – Separazione tra Domain Model e livelli tecnici.
- Decisione #0010 – Comunicazione tramite Domain Events.

---

## Stato Finale

Questa decisione è considerata **congelata** e costituisce la convenzione ufficiale per l'organizzazione della documentazione della repository.