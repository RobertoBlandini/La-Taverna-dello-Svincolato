# Decisione #0006

## Titolo

Modello di Dominio e Regole di Proprietà

---

## Categoria

💻 Tecnica

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

L'architettura della Taverna dello Svincolato è basata su un Domain Model in cui ogni entità possiede responsabilità e confini ben definiti.

Ogni oggetto del dominio appartiene ad un unico proprietario logico, evitando duplicazione dei dati e responsabilità condivise.

Il Domain Model rappresenta la fonte di verità del software e precede la progettazione del database e dell'implementazione.

---

## Aggregate Root

L'Allenatore rappresenta l'Aggregate Root principale del dominio.

Da esso dipendono:

- Compagnia
- Inventario
- Progressione
- Album
- Achievement
- Missioni

Ogni operazione del giocatore viene avviata attraverso l'Allenatore.

---

## Regole di Proprietà

| Entità | Proprietario |
|---------|--------------|
| Allenatore | Sistema |
| Compagnia | Allenatore |
| Inventario | Allenatore |
| Album | Allenatore |
| Progressione | Allenatore |
| Achievement | Allenatore |
| Istanza | Allenatore |
| Equipaggiamento | Inventario |
| Carta | Sistema |
| Anagrafica | Sistema |
| Evento | Sistema |
| Spedizione | Allenatore (istanza della spedizione) |
| Lega | Sistema |

---

## Principi

Ogni entità possiede una sola responsabilità.

Le informazioni non devono essere duplicate tra entità differenti.

Le entità comunicano esclusivamente attraverso relazioni definite dal Domain Model.

---

## Motivazione

La separazione delle responsabilità rende il dominio più leggibile, semplifica l'implementazione e riduce il rischio di inconsistenze durante l'evoluzione del progetto.

---

## Impatto sul progetto

Questa decisione influenza direttamente:

- Domain Model
- Database
- Architettura Backend
- API
- Sistema di salvataggio
- Gestione delle spedizioni

---

## Decisioni correlate

- Decisione #0002 – L'Allenatore è il vero protagonista
- Decisione #0005 – Separazione tra Anagrafica, Carta e Istanza del Calciatore

---

## Note

Il database dovrà rappresentare il Domain Model e non determinarne la struttura.

Ogni nuova entità introdotta nel progetto dovrà dichiarare esplicitamente il proprio proprietario logico.