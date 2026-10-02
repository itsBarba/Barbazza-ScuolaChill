# PDR ScuolaChill - Barbazza

## Iformazioni sul documento

**Prodotto** - ScuolaChill
**Team** - Barba industries
**Autori** - Matteo Barbazza
**Versione** - 1.0 (da verificare)
**Data** - 23/09/2026
**Stato** - Bozza

#### Storico delle versioni

(da creare una tabella)
**Versione** - 1.0
**Data** - 23/09/2026
**Autore** - Matteo Barbazza
**Cosa è cambiato e perché** - Prima stesura

# Prima parte - Il cosa

## Scopo e perimetro

#### Perché esiste ScuolaChill

**Dal lato business.**: facilita i tre utenti (Direttore, Docente, Studente) allo svolgimento della vita scolastica/lavorativa con gestione e organizzazione delle varie attività e scolastiche

**Dal lato tecnico**:

#### Cosa non è incluso

........

# Stakeholder

| Stakeholder      | Cosa fa                | Cosa gli interessa    | Come lo Coinvolgete     |
| ---------------- | ---------------------- | --------------------- | ----------------------- |
| Direttore        | Fornisce gli accessi e | Gestisce/crea profili | Riunioni costanti per   |
|                  | i dati necessari allo  | e classi, è il ruolo  | Ridefinire il progetto  |
|                  | sviluppo               | più importante        | e ottenere info e       |
|                  |                        |                       | feedback dai suoi test  |
| ---------------- | ---------------------  | --------------------  | ---------------------   |
| Docente          |                        | Carica il materiale,  | Riunioni periodiche per |
|                  |                        | creare le verifiche e | Ridefinire il progetto  |
|                  |                        | assegnare i voti      | e ottenere info e       |
|                  |                        |                       | feedback dai suoi test  |
| ---------------- | ---------------------  | --------------------  | ---------------------   |
| Docente          |                        | Carica il materiale,  | Riunioni periodiche per |
|                  |                        | creare le verifiche e | Ridefinire il progetto  |
|                  |                        | assegnare i voti      | e ottenere info e       |
|                  |                        |                       | feedback dai suoi test  |
| ---------------- | ---------------------  | --------------------  | ---------------------   |
| Cella A2         | Cella B2               |
| Cella A2         | Cella B2               |
| Cella A2         | Cella B2               |
| Cella A2         | Cella B2               |
| Cella A2         | Cella B2               |

#

#

## Destinatari e contesto d'uso

#### La scuola che avete immgaginato

il software è progettato per l'istituto superiore don bosco san donà di piave "SFB don bosco (istituto tecnico)".

(da creare una tabella)
**Numero di studenti** - 400
**Numero di docenti** - ???
**Numero di classi** - 18-20
**Orario scolastico** - lunedi, mercoledi, venerdi = dalle 8.00 alle 13.30, Martedi, giovedi = dalle 8.00 alle 16.30
**Connettività** - Wifi ....???

### Gli archetipi

| ID      | Archetipo | Contesto d'uso                  | Competenze digitali | Dispostitivo principale | Frequenza d'uso |
| ------- | --------- | ------------------------------- | ------------------- | ----------------------- | --------------- |
| ARC-001 | Direttore | Tramite il registro/software,   |                     |                         |                 |
|         |           | Controllo attivita giornaliere  |                     | Computer o cellulare    | Frequente       |
|         |           | gestire classi e utenti         | ...                 |                         |                 |
| ------- | --------- | ------------------------------- | ------------------- | ----------------------- | --------------- |
| ARC-002 | Docente   | carica verifiche/materiale/voti | ...                 | Computer o cellulare    | Frequente       |
| ------- | --------- | ------------------------------- | ------------------- | ----------------------- | --------------- |
| ARC-003 | Studente  | controllo voti                  | ...                 | Computer o cellulare    | Frequente       |
| ------- | --------- | ------------------------------- | ------------------- | ----------------------- | --------------- |
| ARC-001 | Direttore | ...                             | ...                 | ...                     | ...             |
| ------- | --------- | ------------------------------  | ------------------- | ----------------------- | --------------- |

#

#

#

# DA FARE PANORAMICA E CASI D'uso

(((((((((((((((((((((DA FARE ANCORA)))))))))))))))))))))

#

#

#

## Le User stories

**Direttore**
_Dir-01_: come Direttore voglio poter creare facilmente utenti per i docenti e studenti cosi da poter velocizzare la creazione di utenti ogni nuovo inizio anno

    Ac-01: Dato che sono autenticato come direttore, Quando creo gli utenti, l'account viene creato con il ruolo corretto e compare in uno degli elenchi Docente o studente

    Ac-02: Se creo un utente (sia per lo studente sia per il docente) con una email gia resgistrata ad un altro utente, ritorna l'errore e non viene creato nessun account

    Ac-03: se autenticato con un utente non direttore, quando si prova a creare un utente, l'operazione deve essere negata

_Dir-02_: come Direttore voglio poter creare classi cosi da poter organizzare comodamente gli studenti

    Ac-01: Autenticato come direttore, quando creo una classe e assegno gli studenti, gli studenti risultano appartententi alla classe seleziona

    Ac-02: come direttore se assegno uno studente (già appartenente ad una classe)  ad un'altra classe, il sistema mi specifica (dandomi un pop up di conferma) se desidero far trasfereire uno studente

_Dir-03_: come Direttore voglio poter spostare gli utenti tra le varie classi cosi da poter facilmente gestire eventuali cambiamenti

       Ac-01: come direttore se assegno uno studente (già appartenente ad una classe)  ad un'altra classe, il sistema mi specifica (dandomi un pop up di conferma) se desidero far trasfereire uno studente

_Dir-04_: come Direttore voglio poter visualizzare le classi ed i loro partecipanti

#

#

**Docente**
_Doc-01_: come docente voglio poter caricare il mio materiale scolastico per gli studenti cosi da poter dare la possibilità agli studenti di visualizzare comodamente il materiale da dove vogliono

    Ac-01: Autenticato come docente quando carico il materiale appare disponibile per gli studenti nella sezione del materiale per quella materia

    Ac-02: se autenticato come non docente se provo a caricare materiale nella classe, deve comparire un errore e negare l'operazione

_Doc-02_: come docente voglio poter assegnare verifiche alle classi cosi da farle compilare dagli studenti

    AC-01: Autenticato come docente quando carico una verifica nella sezione apposita, posso assegnarla alla classe desiderata cosi appare anche agli stuenti che possono compilarla

    AC-02: se carico una verifica con lo stesso nome da errore con un avviso

    AC-03: Quando consegnano la verifica arriva una notifica

_Doc-03_: come docente voglio poter assegnare i voti ad ogni studente cosi da poter tener traccia delle loro prestazioni/valutazioni

    AC-01: Autenticato come Docente di una classe, Quando assegno un voto valido a uno studente per la mia materia, Allora il voto viene salvato ed è visibile allo studente.

    AC-02:

    AC-03: Quando provo a dare un voto a uno studente di una classe non mia, Allora l'operazione viene negata.

#

**Studente**
_Stu-01_: come studente voglio poter vedere i miei voti per ogni materia cosi da tener traccia della mia media

    AC-01: Autenticato come studente, Quando apro la sezione voti, Allora vedo solo i miei voti, raggruppati per materia, con la media per materia.

    AC-02: Dato che sono Studente, Quando provo ad accedere ai voti di un altro studente, Allora l'accesso viene negato.

_Stu-02_: come studente voglio poter vedere i compiti che mi hanno assegnato cosi da potermi organizzare

    AC-01: autenticato come studente quando entro nella sezione dei compiti posso vederli organizzati per data di scadenza

    AC-02: se provo a cambiare data o compito mi da errore

_Stu-03_: come studente voglio poter vedere i materiali di studio dati dai docenti cosi da poter studiare

    AC-01: autenticato come studente quando entro nella sezione dei materiale della materia della classe, li vedo

    Ac-02: se provo a caricare del materiale mi da errore

### Le decisioni lasciate aperte dalla traccia
