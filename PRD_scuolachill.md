# PDR ScuolaChill - Barbazza

## Informazioni sul documento

|              |                  |
| ------------ | ---------------- |
| **Prodotto** | ScuolaChill      |
| **Team**     | Barba industries |
| **Autori**   | Matteo Barbazza  |
| **Versione** | 1.0              |
| **Data**     | 23/09/2026       |
| **Stato**    | Bozza            |

#### Storico delle versioni

| Versione | Data       | Autore          | Cosa è cambiato e perché |
| -------- | ---------- | --------------- | ------------------------ |
| 1.0      | 23/09/2026 | Matteo Barbazza | Prima stesura            |

# Prima parte - Il cosa

## Scopo e perimetro

#### Perché esiste ScuolaChill

**Dal lato business**: facilita i tre utenti (Direttore, Docente, Studente) nello svolgimento della vita scolastica, con gestione e organizzazione delle varie attività scolastiche

**Dal lato tecnico**: velocizza e rende efficiente l'organizzazione di varie funzionalità

#### Cosa è incluso

- Gestione di classi, docenti e studenti da parte del Direttore

- Caricamento di materiale scolastico, verifiche e voti da parte del Docente

#### Cosa non è incluso

- Avvisi comunicativi da parte della scuola alle famiglie

- Un sistema di appello per le presenze

# Stakeholder

| Stakeholder                 | Cosa fa                                                     | Cosa gli interessa                                        | Come lo coinvolgete                                                                     |
| --------------------------- | ----------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| Direttore                   | Fornisce gli accessi e i dati necessari allo sviluppo       | Gestisce/crea profili e classi, è il ruolo più importante | Riunioni costanti per ridefinire il progetto e ottenere info e feedback dai suoi test   |
| Docente                     | Usa il sistema quotidianamente per le proprie materie       | Carica il materiale, crea le verifiche e assegna i voti   | Riunioni periodiche per ridefinire il progetto e ottenere info e feedback dai suoi test |
| Studente                    | Usa il sistema per studiare e consultare i propri risultati | Vede materiale, svolge verifiche, controlla i voti        | Collaudo diretto come utente reale del primo anno                                       |
| Docente del corso           | Valida il PRD                                               | Che le scelte siano motivate e coerenti                   | Presentazione e domande di validazione                                                  |
| Collaudatori del primo anno | Usano ScuolaChill come utenti reali                         | Un'app semplice da usare senza aiuto                      | Intervista e collaudo guidato                                                           |

## Destinatari e contesto d'uso

#### La scuola che avete immaginato

il software è progettato per l'istituto superiore don bosco san donà di piave "SFB don bosco (istituto tecnico)".

|                    | Valore                                                                                                     |
| ------------------ | ---------------------------------------------------------------------------------------------------------- |
| Numero di studenti | 400                                                                                                        |
| Numero di docenti  | 46                                                                                                         |
| Numero di classi   | 18-20                                                                                                      |
| Orario scolastico  | Lun/Mer/Ven 8:00-13:30, Mar/Gio 8:00-16:30                                                                 |
| Connettività       | Wi-Fi scolastico condiviso per gli studenti in aula; connessione personale (dati mobili/casa) fuori orario |

### Gli archetipi

| ID      | Archetipo | Contesto d'uso                                                                  | Competenze digitali                                    | Dispositivo principale                                          | Frequenza d'uso |
| ------- | --------- | ------------------------------------------------------------------------------- | ------------------------------------------------------ | --------------------------------------------------------------- | --------------- |
| ARC-001 | Direttore | Usa il registro per controllare l'attività giornaliera, gestire classi e utenti | Medie (uso quotidiano di strumenti gestionali)         | Computer, a volte cellulare                                     | Frequente       |
| ARC-002 | Docente   | Carica materiale, crea verifiche, assegna voti per le proprie materie e classi  | Variabili da materia a materia                         | Computer o cellulare                                            | Frequente       |
| ARC-003 | Studente  | Consulta materiale, svolge verifiche, controlla i propri voti                   | Alte (nativi digitali, ma collaudatori del primo anno) | Smartphone come dispositivo principale, computer in laboratorio | Frequente       |

## Panoramica e casi d'uso

ScuolaChill è un registro elettronico che permette a Direttore, Docenti e Studenti di gestire comodamente la vita scolastica: creazione di classi e utenti, materiale didattico, verifiche e voti. Tramite il login, ogni utente accede solo alle operazioni e ai dati previsti dal proprio ruolo.

### User flow e scenari

**Storia: DIR-01 · Creare account docente**

User flow:

1. Il Direttore effettua il login
2. Apre la sezione "Crea utente"
3. Inserisce i dati del docente (nome, cognome, email)
4. Conferma la creazione

Scenario principale: il Direttore crea l'account di un nuovo docente assunto a inizio anno; l'account viene creato con ruolo Docente e compare subito nell'elenco.

Scenari alternativi: se l'email inserita è già registrata, il sistema mostra l'errore e non crea nulla; il Direttore corregge l'email e riprova.

**Storia: DIR-03 · Creare classi e comporle**

User flow:

1. Il Direttore effettua il login
2. Apre la sezione "Classi" e crea una nuova classe
3. Assegna gli studenti alla classe
4. Assegna un docente a una materia per quella classe

Scenario principale: a inizio anno il Direttore crea la classe 1A Informatica, vi assegna 24 studenti e assegna il docente di Sistemi e Reti per quella classe e quella materia.

Scenari alternativi: se prova ad assegnare uno studente già iscritto a un'altra classe, il sistema chiede conferma del trasferimento prima di procedere (vedi decisione FR-DOM-02); se il docente da assegnare non ha ancora un account, il Direttore deve prima crearlo (DIR-01).

**Storia: DIR-04 · Vedere tutto**

User flow:

1. Il Direttore effettua il login
2. Apre la dashboard
3. Consulta classi, docenti e andamento voti in forma aggregata
4. Filtra o scorre le pagine dei risultati se necessario

Scenario principale: il Direttore apre la dashboard il lunedì mattina per avere un quadro generale prima dell'inizio delle lezioni, e vede il numero di studenti per classe e la media dei voti per materia.

Scenari alternativi: se un Docente o uno Studente prova ad accedere alla stessa vista, l'operazione viene negata; se gli elenchi superano la dimensione di una pagina, i risultati vengono paginati automaticamente.

**Storia: STU-02 · Svolgere una verifica**

User flow:

1. Lo studente effettua il login
2. Apre la sezione "Verifiche" della materia
3. Seleziona la verifica disponibile per la propria classe
4. Compila le risposte e consegna

Scenario principale: uno studente apre la verifica di Sistemi e Reti alle 9:00 insieme al resto della classe, risponde e consegna entro l'orario previsto.

Scenari alternativi: se lo studente ha già consegnato, il sistema nega un secondo tentativo; se la connessione cade durante lo svolgimento, al rientro lo studente ritrova le risposte già date (vedi decisione FR-DOM-04).

**Storia: STU-01 · Consultare il materiale didattico**

User flow:

1. Lo studente effettua il login
2. Apre la materia di interesse della propria classe
3. Consulta l'elenco dei materiali caricati dal docente
4. Apre o scarica il materiale desiderato

Scenario principale: uno studente apre la sezione di Matematica prima di un'interrogazione per rivedere le slide caricate dal docente.

Scenari alternativi: se lo studente prova ad accedere al materiale di una classe diversa dalla propria, l'operazione viene negata.

**Storia: STU-03 · Consultare i propri voti**

User flow:

1. Lo studente effettua il login
2. Apre la sezione "Voti"
3. Visualizza i voti raggruppati per materia, con la media

Scenario principale: uno studente controlla i propri voti di Sistemi e Reti dopo la correzione di una verifica, per vedere come sta andando la media in quella materia.

Scenari alternativi: se lo studente prova a consultare i voti di un compagno di classe, l'operazione viene negata.

**Storia: DOC-03 · Assegnare i voti**

User flow:

1. Il Docente effettua il login
2. Apre la verifica svolta dalla classe
3. Seleziona uno studente che ha consegnato
4. Inserisce il voto e conferma

Scenario principale: il Docente corregge le consegne della sua verifica e assegna un voto a ciascuno studente; ogni voto diventa visibile allo studente corrispondente.

Scenari alternativi: se il Docente inserisce un voto fuori scala, il sistema rifiuta e chiede un valore valido; se il Docente prova ad assegnare un voto su una verifica non sua, l'operazione viene negata.

**Storia: DOC-01 · Caricare materiale didattico**

User flow:

1. Il Docente effettua il login
2. Apre la sezione materiale della propria materia e classe
3. Carica un file con un titolo
4. Conferma: il materiale diventa visibile agli studenti della classe

Scenario principale: la Docente di Elettrotecnica carica le slide della lezione prima della lezione stessa, così gli studenti le trovano già pronte quando entrano in aula.

Scenari alternativi: se il Docente non è assegnato a quella classe e materia, l'operazione viene negata; se il Docente prova a modificare un materiale caricato da un collega, l'operazione viene negata perché il materiale non è suo.

**Storia: DOC-02 · Creare le proprie verifiche**

User flow:

1. Il Docente effettua il login
2. Apre la sezione verifiche della propria materia e classe
3. Inserisce titolo, data di svolgimento e contenuto
4. Pubblica la verifica

Scenario principale: il Docente crea la verifica di fine modulo con data fissata per la settimana successiva; la verifica compare subito nella lista degli studenti della classe.

Scenari alternativi: se il Docente prova a modificare la verifica dopo la data di svolgimento, l'operazione viene negata (vedi decisione FR-DOM-03); se carica una verifica con lo stesso titolo di una già esistente per la stessa classe e materia, riceve un avviso di conferma prima di procedere.

## Le User stories

Gli ID seguono esattamente quelli della traccia, così restano stabili in commit, test e validazione. Gli AC minimi sono quelli della traccia; quelli aggiuntivi sono marcati "(aggiunto dal team)".

**Direttore**

_DIR-01 — Creare account docente_: come Direttore voglio creare gli account dei docenti così da dare al personale l'accesso al sistema con il ruolo corretto.

    AC-01: Dato che sono autenticato come Direttore, Quando creo un docente con dati validi, Allora l'account viene creato con ruolo Docente e compare nell'elenco dei docenti.

    AC-02: Dato che esiste già un utente con la stessa email, Quando provo a crearne un altro, Allora ricevo un errore chiaro e nessun account viene creato.

    AC-03: Dato che sono autenticato come Docente o Studente, Quando provo a creare un docente, Allora l'operazione viene negata.

_DIR-02 — Creare account studente_: come Direttore voglio creare gli account degli studenti così da permettere a ogni iscritto di usare l'applicazione.

    AC-01: Dato che sono autenticato come Direttore, Quando creo uno studente con dati validi, Allora l'account viene creato con ruolo Studente.

    AC-02: Dato che invio dati incompleti o non validi, Quando confermo la creazione, Allora ricevo l'indicazione puntuale dei campi errati e nessun account viene creato.

    AC-03: Dato che sono autenticato come Docente o Studente, Quando provo a creare uno studente, Allora l'operazione viene negata.

_DIR-03 — Creare classi e comporle_: come Direttore voglio creare le classi e assegnarvi studenti e docenti con le rispettive materie così da riprodurre l'organizzazione reale della scuola.

    AC-01: Dato che sono autenticato come Direttore, Quando creo una classe e vi assegno studenti, Allora ogni studente risulta appartenere a quella classe.

    AC-02: Dato che una classe esiste, Quando vi assegno un docente per una materia, Allora il docente vede quella classe fra le proprie e può operarvi solo per quella materia.

    AC-03: Dato che uno studente è già assegnato a una classe, Quando provo ad assegnarlo a una seconda classe, Allora il sistema mi chiede conferma e, se confermo, gestisce il trasferimento in modo esplicito (vedi decisione FR-DOM-02).

_DIR-04 — Vedere tutto_: come Direttore voglio una vista complessiva su classi, docenti, studenti e voti così da monitorare l'andamento della scuola senza entrare in ogni singola pagina.

    AC-01: Dato che sono autenticato come Direttore, Quando apro la vista complessiva, Allora vedo i dati aggregati della scuola (classi con numero di studenti, docenti con materie, andamento dei voti).

    AC-02: Dato che gli elenchi superano la dimensione di una pagina, Quando li consulto, Allora i risultati sono paginati.

    AC-03: Dato che sono autenticato come Docente o Studente, Quando provo ad accedere alla vista complessiva, Allora l'operazione viene negata.

**Docente**

_DOC-01 — Caricare materiale didattico_: come Docente voglio caricare il materiale didattico per le mie materie e classi così da metterlo a disposizione degli studenti in un posto solo.

    AC-01: Dato che sono autenticato come Docente e assegnato a una classe per una materia, Quando carico un materiale per quella classe e materia, Allora gli studenti della classe lo vedono nell'elenco della materia.

    AC-02: Dato che non sono assegnato a una classe, Quando provo a caricarvi materiale, Allora l'operazione viene negata.

    AC-03: Dato che ho caricato un materiale, Quando lo modifico o lo elimino, Allora l'operazione riesce solo se il materiale è mio.

_DOC-02 — Creare le proprie verifiche_: come Docente voglio creare verifiche per le mie classi così da valutare gli studenti sulle mie materie.

    AC-01: Dato che sono autenticato come Docente e assegnato a una classe per una materia, Quando creo una verifica con titolo, materia, data e contenuto, Allora la verifica risulta visibile agli studenti di quella classe.

    AC-02: Dato che una verifica è mia, Quando la modifico prima della data di svolgimento, Allora le modifiche sono salvate; dopo la data di svolgimento la modifica viene negata (vedi decisione FR-DOM-03).

    AC-03: Dato che una verifica appartiene a un altro docente, Quando provo a modificarla, Allora l'operazione viene negata.

    AC-04 (aggiunto dal team): Dato che carico una verifica con lo stesso titolo di una già esistente per la stessa classe e materia, Quando confermo, Allora ricevo un avviso di conferma prima di procedere (non un blocco, perché due verifiche omonime in periodi diversi sono un caso legittimo).

_DOC-03 — Assegnare i voti_: come Docente voglio assegnare i voti delle mie verifiche così da registrare formalmente la valutazione di ogni studente.

    AC-01: Dato che uno studente ha svolto una mia verifica, Quando gli assegno un voto valido, Allora il voto è registrato e lo studente può vederlo fra i propri.

    AC-02: Dato che inserisco un voto fuori dalla scala prevista (0-10, step 0.5 — vedi decisione FR-DOM-01), Quando confermo, Allora ricevo un errore e il voto non viene registrato.

    AC-03: Dato che la verifica appartiene a un altro docente, Quando provo ad assegnare un voto, Allora l'operazione viene negata.

**Studente**

_STU-01 — Consultare il materiale didattico_: come Studente voglio consultare il materiale caricato da ogni docente delle mie materie così da avere tutto ciò che serve per studiare in un unico posto.

    AC-01: Dato che sono autenticato come Studente, Quando apro una materia della mia classe, Allora vedo il materiale caricato dal docente di quella materia.

    AC-02: Dato che un materiale appartiene a una classe diversa dalla mia, Quando provo ad accedervi, Allora l'operazione viene negata.

_STU-02 — Svolgere una verifica_: come Studente voglio svolgere le verifiche assegnate alla mia classe così da essere valutato sulle materie che seguo.

    AC-01: Dato che una verifica è disponibile per la mia classe, Quando la svolgo e consegno, Allora le mie risposte sono salvate e la verifica risulta consegnata.

    AC-02: Dato che ho già consegnato una verifica, Quando provo a svolgerla di nuovo, Allora l'operazione viene negata.

    AC-03: Dato che la verifica appartiene a un'altra classe, Quando provo ad accedervi, Allora l'operazione viene negata.

    AC-04 (aggiunto dal team): Dato che sono autenticato come Studente, Quando apro la sezione verifiche, Allora le vedo organizzate per data di scadenza, anche quelle non ancora disponibili per lo svolgimento.

    AC-05 (aggiunto dal team): Dato che la connessione cade durante lo svolgimento, Quando mi riconnetto prima della consegna, Allora ritrovo le risposte già date fino a quel momento (vedi decisione FR-DOM-04).

_STU-03 — Consultare i propri voti_: come Studente voglio consultare i miei voti raggruppati per materia così da sapere come sto andando in ciascuna.

    AC-01: Dato che ho voti registrati, Quando apro la pagina dei voti, Allora li vedo raggruppati per materia con l'indicazione della verifica di provenienza e la media per materia.

    AC-02: Dato che sono autenticato come Studente, Quando provo a consultare i voti di un altro studente, Allora l'operazione viene negata.

> **Nota di riconciliazione**: nella bozza precedente "Stu-02" era "vedere i compiti assegnati" — concetto diverso da STU-02 della traccia, che è "svolgere una verifica". L'idea di consultare le verifiche in arrivo non è persa: è diventata l'AC-04 di STU-02 sopra, mentre lo svolgimento vero e proprio (con blocco su doppia consegna) segue gli AC della traccia ed è già implementato nel contratto API come `/api/verifiche/{id}/consegne`.

### Le decisioni lasciate aperte dalla traccia

> **FR-DOM-01 · Scala dei voti** (collegato a DOC-03)
> Scala da 0 a 10, con step di 0.5 (niente segni "+"/"−"). Motivazione: coerente con la scala in uso nelle scuole superiori italiane, semplice da validare lato API con un controllo numerico.

> **FR-DOM-02 · Trasferimento di uno studente fra classi** (collegato a DIR-03)
> Il trasferimento è un'azione esplicita del Direttore, confermata con un popup. Nel modello dati non si sovrascrive la classe dello studente: si chiude l'iscrizione corrente (`data_fine = oggi`) e se ne apre una nuova nella classe di destinazione. Motivazione: i voti già dati restano storicamente legati alla classe in cui sono stati presi, nessun dato va perso, e il Direttore mantiene uno storico consultabile.

> **FR-DOM-03 · Modifica di una verifica dopo lo svolgimento** (collegato a DOC-02)
> Dopo la data di svolgimento la verifica non è più modificabile dal Docente (l'API risponde `409`). Motivazione: una verifica già consegnata da alcuni studenti non deve poter cambiare contenuto a metà, altrimenti si rischia disparità fra chi l'ha svolta prima e dopo la modifica.

> **FR-DOM-04 · Connessione che cade durante una verifica** (collegato a STU-02)
> Le risposte dello studente vengono salvate progressivamente (non solo al momento della consegna finale); se la connessione cade, al rientro lo studente ritrova le risposte già date e può continuare fino alla consegna o alla scadenza. Motivazione: perdere le risposte per un problema di rete sarebbe percepito come un'ingiustizia grave da chi sostiene una verifica.

> **FR-DOM-05 · Fallimento del servizio esterno di invio email** (collegato a DIR-01, DIR-02)
> Se l'invio dell'email con le credenziali fallisce, l'account viene comunque creato ma resta marcato come "credenziali non inviate"; il Direttore può reinviarle manualmente dall'elenco utenti. Motivazione: un servizio esterno che fallisce non deve bloccare un'operazione critica come la creazione di un account a inizio anno.

> **FR-DOM-06 · Strategia di generazione degli identificatori**
> Tutte le entità usano ID interi auto-incrementali, non UUID. Motivazione: più leggibili in log, debug e nei test durante lo sviluppo; non ci sono casi di esposizione pubblica di ID in URL non autenticati che renderebbero preferibile un UUID non enumerabile.

## Requisiti non funzionali

| ID | Famiglia | Requisito | Soglia e condizione | Come si verifica | Storie collegate |
| --- | --- | --- | --- | --- | --- |
| NFR-01 | Prestazioni | Comparsa dei materiali e delle verifiche | Meno di 5 secondi con un carico di 100 studenti | Test di carico | STU-01, STU-02, STU-03 |
| NFR-02 | Sicurezza | Protezione delle operazioni non autorizzate | Ogni richiesta senza token valido o con ruolo non permesso riceve 401/403, mai dati parziali | Collezione Postman con casi negativi per ogni ruolo | Tutte le storie con AC "operazione negata" |
| NFR-03 | Usabilità | Reperibilità del materiale e delle verifiche | Uno studente del primo anno trova e apre una verifica assegnata senza aiuto, in al massimo 3 tocchi | Osservazione diretta durante il collaudo | STU-01, STU-02 |
| NFR-04 | Disponibilità | Raggiungibilità del sistema | Almeno 99% di uptime durante l'orario scolastico (8:00-16:30) | Monitoraggio Azure (Application Insights / alert) | STU-02, DOC-03 |
| NFR-05 | Ambientale | Funzionamento su reti diverse | Il sistema resta utilizzabile sia su Wi-Fi scolastico condiviso sia su rete mobile personale, con payload leggeri nei picchi | Test manuale su connessione throttled/simulata | STU-02 |
| NFR-06 | Supporto | Assistenza in caso di problemi | L'utente può contattare l'indirizzo email di supporto e riceve una risposta entro una giornata lavorativa | Verifica che l'indirizzo sia attivo e monitorato | — |
| NFR-07 | Scalabilità | Tenuta nel picco delle 9:00 | Il sistema scala automaticamente le repliche senza intervento manuale, con degrado del tempo di risposta non oltre il 20% rispetto al carico normale | Test di carico a gradini, confronto normale vs picco | STU-02 |
| NFR-08 | Conformità | Trattamento dati di minorenni | Dati residenti in regione UE (Italy North), password sempre hashate, nessun dato sensibile loggato in chiaro | Revisione del codice e della configurazione regione/log | DIR-01, DIR-02, STU-03 |
| NFR-09 | Interazione | Dialogo con il servizio email esterno | Se il servizio esterno non risponde entro 5 secondi, la creazione account non viene bloccata (FR-DOM-05) | Test con servizio email disabilitato/simulato in errore | DIR-01, DIR-02 |
| NFR-10 | Usabilità | Anteprima del materiale prima del download (emerso dall'intervista a Studente 1) | Per i formati PDF e immagine, lo studente vede un'anteprima in pagina senza dover scaricare il file, in meno di 2 secondi | Test manuale su materiali di prova nei formati più comuni | STU-01 |
| NFR-11 | Usabilità | Indicatore di contenuti non ancora visti (emerso dall'intervista a Studente 3) | Lo studente vede un indicatore (badge) su materiale/voti aggiunti dopo il suo ultimo accesso, calcolato lato server al login — niente notifiche push (fuori scope per VIN-01/VIN-03) | Test manuale: login dopo l'aggiunta di un nuovo voto o materiale | STU-01, STU-03 |

# Requisiti impliciti

Intervista fatta a tre collaudatori del primo anno, identificati solo con un numero per non riportare dati personali di minori (coerente con NFR-08 sulla conformità).

| Chi avete intervistato | Cosa ha detto | Requisito che ne avete ricavato |
| --- | --- | --- |
| Studente 1 (classe 1ª, collaudatore) | "Vorrei poter scaricare le slide e le tabelle del docente in un formato leggibile, e vedere un'anteprima prima di scaricarle, come su Google Drive" | NFR-10 — anteprima del materiale didattico prima del download |
| Studente 2 (classe 1ª, collaudatore) | "Vorrei vedere il mio andamento in una materia e il voto con la descrizione di quale verifica era" | Nessun nuovo NFR: conferma indipendente di STU-03 AC-01, già previsto nel documento |
| Studente 3 (classe 1ª, collaudatore) | "Vorrei essere avvisato nel menu o in qualche modo se è stato aggiunto qualcosa, tipo nuovi voti o materiale" | NFR-11 — indicatore di contenuti non ancora visti (scope ridotto rispetto a notifiche push vere, vedi nota sotto la tabella NFR) |

## Assunzioni, vincoli e dipendenze

### Assunzioni

| ID | Assunzione | Cosa succede se è falsa |
| --- | --- | --- |
| ASS-01 | La scuola ha 400 studenti, 46 docenti, 18-20 classi | Il dimensionamento (Container Apps, database, costi) va rifatto da zero |
| ASS-02 | Nel picco delle 9:00 sono concorrenti 150-200 utenti (6-8 classi che iniziano una verifica insieme) | NFR-01/NFR-07 e la configurazione di autoscaling vanno rivisti; il database potrebbe non reggere senza upgrade |
| ASS-03 | La connettività è mista: Wi-Fi scolastico condiviso in aula, rete personale fuori orario | NFR-05 va rivisto; con solo Wi-Fi a banda limitata servirebbe ottimizzare ulteriormente i payload |
| ASS-04 | Un docente insegna più materie in più classi, ma su ogni combinazione materia+classe è assegnato un solo docente (nessuna compresenza) | Il modello `ASSEGNAZIONE` andrebbe esteso per permettere più docenti sulla stessa materia/classe |
| ASS-05 | Orario scolastico: Lun/Mer/Ven 8:00-13:30, Mar/Gio 8:00-16:30 | La finestra di disponibilità garantita (NFR-04) e le fasce di manutenzione pianificata vanno ricalcolate |

### Vincoli

| ID | Vincolo | Da dove viene |
| --- | --- | --- |
| VIN-01 | Un solo sviluppatore sul progetto (non in team di 2) | Scelta dichiarata a inizio progetto |
| VIN-02 | Stack tecnologico limitato a quanto già noto (Node.js, React, MySQL/MariaDB) per restare nei tempi | Competenze dichiarate dallo sviluppatore |
| VIN-03 | Budget cloud limitato ai crediti gratuiti disponibili (es. Azure for Students) | Traccia del progetto / risorse economiche dello studente |
| VIN-04 | Consegna e collaudo entro il calendario scolastico del corso | Traccia del progetto |

### Dipendenze

| ID | Dipendenza | Serve entro | Chi se ne occupa |
| --- | --- | --- | --- |
| DIP-01 | Account Azure attivo con credito disponibile | Prima dell'inizio dello sviluppo | Matteo Barbazza |
| DIP-02 | Servizio email esterno attivo e dominio verificato (Azure Communication Services o SendGrid) | Prima del primo invio di credenziali / collaudo | Matteo Barbazza |
| DIP-03 | Disponibilità del Direttore e di un docente reale per fornire dati di test realistici | Prima del collaudo con il primo anno | Direttore, docente del corso |
| DIP-04 | Dominio o sottodominio pubblico per Static Web Apps e Container Apps | Prima del deployment in produzione | Matteo Barbazza |

# Seconda parte - Il come

## Stima del carico

### Utenti concorrenti

_Uso normale durante la giornata:_

- Utenti concorrenti stimati: 50-80
- Studenti/docenti che consultano materiale o voti in modo sparso durante le ore

_Picco delle verifiche 9.00:_

- Utenti concorrenti stimati: 150-200
- Caso peggiore: 6-8 classi iniziano insieme, 20-30 studenti ciascuna, più il traffico di fondo

_Fine quadrimestre_

- Utenti concorrenti stimati: 80-120
- più o meno 40 docenti inseriscono voti in parallelo, più studenti che controllano subito dopo

### Profilo di carico

| Operazione | Frequente? | Pesante? | Critica? |
| --- | --- | --- | --- |
| Login | Sì | No | Sì |
| Apertura verifica | Concentrata nel picco | Leggera singolarmente, pesante in aggregato | Sì |
| Consegna verifica | Concentrata nel picco | Scrittura su DB in burst | Sì, molto |
| Dashboard Direttore | Rara | Pesante (query aggregate su più tabelle) | No |
| Caricamento materiale | Rara | Dipende dalla dimensione del file | No |

## Scelte tecnologiche

| Area             | Scelta                                                                                                                                     | Alternativa considerata                                         | Perché ho scelto così                                                                                                                                                                                                                                                             |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Backend          | Node.js (NestJS)                                                                                                                           | Python (FastAPI/Django)                                         | Stesso linguaggio di React: un solo linguaggio su tutto lo stack, meno context-switching per uno sviluppatore solo. NestJS genera OpenAPI quasi automaticamente, requisito obbligatorio della traccia                                                                             |
| Frontend         | React, SPA                                                                                                                                 | Server-side rendering                                           | L'app è tutta dietro login: il SEO (vantaggio principale dell'SSR) non serve. React è anche l'argomento di studio di quest'anno                                                                                                                                                   |
| Database         | MySQL/MariaDB                                                                                                                              | PostgreSQL                                                      | Lo conosco già; il dominio ha relazioni dirette senza bisogno delle funzionalità avanzate di PostgreSQL (JSON complessi, CHECK avanzati)                                                                                                                                          |
| Provider cloud   | Microsoft Azure                                                                                                                            | AWS, GCP                                                        | Esperienza pregressa (seppur solo su Azure DevOps); resto coerente su un solo provider invece di imparare più ecosistemi in parallelo                                                                                                                                             |
| Servizi cloud    | Azure Container Apps (backend), Azure Database for MySQL Flexible Server, Azure Blob Storage (materiale), Azure Static Web Apps (frontend) | Azure Kubernetes Service (AKS), Azure Container Instances (ACI) | AKS è sovradimensionato per un solo sviluppatore (alta complessità operativa); ACI non scala e non è adatto a un sistema in produzione con utenti reali. Container Apps scala automaticamente nel picco delle 9:00 e resta vicino al piano gratuito per un carico di questa scala |
| Regione          | Italy North                                                                                                                                | West Europe                                                     | Più vicina fisicamente alla scuola (minore latenza) e residenza dei dati in Italia, rilevante per dati di minorenni (voti, anagrafiche)                                                                                                                                           |
| Servizio esterno | Azure Communication Services – Email (alternativa: SendGrid)                                                                               | —                                                               | Invio email delle credenziali ai nuovi account; resta dentro l'ecosistema Azure già scelto. Gestione del fallimento: vedi decisione FR-DOM-05                                                                                                                                     |
