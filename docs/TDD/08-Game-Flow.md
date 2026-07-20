# Game Flow & Application Lifecycle

**Versione:** 1.0

**Stato:** 🟢 Congelato

**Ultima modifica:** 15 Luglio 2026

---

# Scopo

Questo documento descrive il flusso applicativo principale della **Taverna dello Svincolato**.

L'obiettivo è definire come il giocatore interagisce con il sistema e come il Domain Model evolve durante una sessione di gioco.

Non descrive l'implementazione tecnica, ma il comportamento atteso dell'applicazione.

---

# Principi

Il Game Flow è guidato dai seguenti principi.

- Il giocatore controlla esclusivamente la propria Compagnia.
- Ogni azione produce un nuovo stato del dominio.
- Il sistema reagisce agli eventi generati dalle azioni del giocatore.
- Nessuna modifica del dominio avviene senza una decisione esplicita del giocatore o una conseguenza deterministica del regolamento.

---

# Ciclo di Vita della Sessione

Ogni sessione segue il seguente flusso.

```text
Accesso

↓

Taverna

↓

Preparazione

↓

Avvio Spedizione

↓

Esplorazione

↓

Risoluzione Eventi

↓

Conclusione

↓

Ricompense

↓

Aggiornamento Compagnia

↓

Ritorno alla Taverna
```

Al termine del ciclo il giocatore può iniziare una nuova spedizione oppure gestire la propria Compagnia.

---

# Fase 1 — Taverna

La Taverna rappresenta l'hub principale del gioco.

Da qui il giocatore può:

- consultare la Compagnia;
- gestire il mazzo;
- visualizzare il mercato;
- consultare il Libro delle Compagnie;
- selezionare una spedizione;
- verificare lo stato della stagione.

Nessun evento casuale viene generato all'interno della Taverna.

---

# Fase 2 — Preparazione

Prima della partenza il giocatore configura la spedizione.

Attività possibili:

- scelta della spedizione;
- verifica dei requisiti;
- selezione della formazione;
- conferma della partenza.

Una volta confermata la spedizione il dominio entra nello stato "In Spedizione".

---

# Fase 3 — Generazione della Spedizione

Il sistema:

- crea una nuova Spedizione;
- genera il percorso;
- inizializza i nodi;
- registra lo stato iniziale.

Da questo momento la spedizione è persistita e può essere ripresa.

---

# Fase 4 — Esplorazione

La spedizione procede nodo dopo nodo.

Per ogni nodo:

1. presentazione del contesto;
2. scelta del giocatore (se prevista);
3. esecuzione dell'evento;
4. applicazione degli effetti;
5. aggiornamento dello stato della Compagnia;
6. avanzamento al nodo successivo.

Ogni nodo è indipendente e produce effetti permanenti sul dominio.

---

# Fase 5 — Conclusione

Quando viene raggiunto l'ultimo nodo:

- la spedizione termina;
- vengono calcolate le ricompense;
- vengono registrati gli eventuali fallimenti;
- viene aggiornato il progresso della stagione.

---

# Fase 6 — Ritorno

La Compagnia ritorna alla Taverna.

Il sistema aggiorna:

- inventario;
- risorse;
- membri;
- progressione;
- statistiche;
- cronologia delle spedizioni.

Il ciclo può ricominciare.

---

# Eventi di Dominio

Durante il flusso possono essere generati eventi quali:

- ExpeditionStarted
- NodeEntered
- PlayerChoiceMade
- NodeResolved
- RewardGranted
- ExpeditionCompleted
- ExpeditionFailed
- CompanyUpdated
- SeasonProgressed

Gli eventi rappresentano la comunicazione interna del Domain Model.

---

# Persistenza

Il dominio viene persistito nei seguenti momenti:

- avvio spedizione;
- completamento di un nodo;
- assegnazione di una ricompensa;
- conclusione della spedizione.

Questo garantisce il ripristino della sessione in caso di interruzione.

---

# Regole

Il giocatore non può:

- modificare la Compagnia durante una spedizione;
- cambiare la formazione dopo la partenza;
- avviare più spedizioni contemporaneamente.

---

# Obiettivo Architetturale

Ogni fase del Game Flow dovrà essere implementata tramite Use Case dedicati.

Il Domain Model non conosce l'interfaccia utente.

L'interfaccia utente si limita a richiedere l'esecuzione dei casi d'uso e a rappresentarne il risultato.

---

# Diagramma Concettuale

```text
Giocatore
      │
      ▼
Presentation
      │
      ▼
Application
      │
      ▼
Domain
      │
      ▼
Domain Events
      │
      ▼
Infrastructure
      │
      ▼
Persistenza
```

---

# Documenti Correlati

- Domain Model
- Engine Architecture
- Domain Events
- Technical Bootstrap
- Use Cases
- State Machine

---

# Stato Finale

Questo documento definisce il comportamento applicativo di riferimento della Taverna dello Svincolato.

Ogni nuovo caso d'uso dovrà integrarsi con il Game Flow qui descritto.