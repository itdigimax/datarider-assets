## 🔄 Versione 1.12.0 – 2026-03-25

### 👤 Utente

#### Nuove funzionalità
* [FEAT] La tabella risultati supporta ora filtri KPI con card dedicate, preset configurabili, riordino drag-and-drop e sidebar comprimibile, così è più rapido applicare viste mirate e confrontare indicatori chiave senza ricostruire i filtri ogni volta.

#### Miglioramenti
* [IMPROVEMENT] Il flusso di import Excel è stato reso più leggibile e robusto: upload collassabile, gestione file e manifest più chiara, anteprima dati più affidabile e modali tipizzate aiutano a controllare meglio il contenuto prima dell'esecuzione.
* [IMPROVEMENT] La griglia evidenzia meglio le colonne riservate agli amministratori tramite tooltip contestuali, riducendo l'ambiguità sui campi visibili solo con permessi elevati.

### 🛠️ Admin

#### Nuove funzionalità
* [FEAT] Introdotto lo storico degli import Excel con archivio dedicato, ricerca configurabile, dettaglio esecuzioni e paginazione, così è più semplice ricostruire esiti, file processati e operazioni già eseguite.
* [FEAT] Aggiunto il nuovo workflow di import Python con configurazione pacchetti, gestione campi manifest e processo in due fasi con anteprima e conferma, utile per validare i dati prima dell'avvio effettivo dell'elaborazione.
* [FEAT] Le schedulazioni email mostrano ora una scheda dettaglio con frequenza, destinatari, filtri, oggetto e SQL copiabili, mentre i messaggi inviati includono un riepilogo sintetico della configurazione attiva per facilitare verifiche e supporto.

#### Correzioni
* [FIX] Normalizzata la gestione delle date e ore SQL Server tra backend, schedulazioni, pannello aggiornamenti e notifiche, evitando conversioni UTC implicite che potevano produrre scostamenti negli orari mostrati o pianificati.

#### Miglioramenti
* [IMPROVEMENT] La configurazione Admin dei filtri KPI è più guidata e stabile grazie a validazioni dedicate e riordino dei preset, riducendo errori nella pubblicazione dei filtri disponibili agli utenti.
* [IMPROVEMENT] La gestione utenti è stata snellita con caricamento dinamico dei ruoli e ricerca nella modale, rendendo più veloce assegnare o verificare i permessi.
* [IMPROVEMENT] Il pannello aggiornamenti consente di copiare il changelog con testo già normalizzato, facilitando la condivisione delle note di rilascio senza correzioni manuali.
* [IMPROVEMENT] Il pannello comandi evidenzia meglio l'impatto dei pulsanti custom mostrando il conteggio delle tab coinvolte, così la configurazione risulta più immediata da verificare.

#### Documentazione
* [DOCS] Aggiornate guide e documentazione tecnica su filtri KPI, storico import Excel, import Python, schedulazioni email, installazione stage e gestione degli aggiornamenti, mantenendo l'operatività Admin allineata ai nuovi flussi.

## 🔄 Versione 1.11.3 – 2026-03-12

### 👤 Utente

* Nessuna modifica rilevante.

### 🛠️ Admin

#### Nuove funzionalità
* [FEAT] Il pannello Aggiornamento DataRider mostra ora anche il changelog pubblicato insieme alla versione remota e filtra automaticamente le sole versioni successive a quella installata, così la verifica pre-update è più immediata.
* [FEAT] La gestione parametri nel pannello Admin è stata semplificata, rendendo più rapida la configurazione dei form comando.
* [FEAT] Le email schedulate includono un riepilogo della configurazione attiva con SQL, frequenza e filtri, utile per validare più facilmente il contenuto effettivo degli invii automatici e dei test send.

#### Correzioni
* [FIX] Il testo introduttivo delle email schedulate conserva gli a capo inseriti in configurazione, evitando messaggi compattati e meno leggibili.
* [FIX] Lo script di aggiornamento applicativo gestisce meglio le dipendenze npm necessarie al deploy e registra le variabili ambientali rilevanti, facilitando la diagnosi degli update falliti o incompleti.

#### Miglioramenti
* [IMPROVEMENT] La pubblicazione degli asset di release è stata resa più robusta: `CHANGELOG.md` viene distribuito insieme a `VERSION.txt` e il workflow evita errori inutili quando il token di pubblicazione non è configurato.

#### Sicurezza
* [SECURITY] Il template SQL dell'Excel Import usa ora un riferimento esplicito al database `DgxUty` per la tabella di staging suggerita, riducendo il rischio di costruzioni SQL ambigue o vulnerabili.

#### Documentazione
* [DOCS] Aggiornate le guide Admin e le regole di redazione del changelog con istruzioni più dettagliate su parametri comando, update applicativi e contenuti delle note di rilascio.

## 🔄 Versione 1.11.2 – 2026-03-11

### 👤 Utente

* [FIX] Modifica righe senza perdere il contesto: dopo un salvataggio nella griglia, i filtri applicati restano attivi e la vista continua a riflettere correttamente la selezione corrente.
* [FIX] Pulsanti custom più affidabili in tabella: il posizionamento usa il nome colonna, così i pulsanti restano associate alla colonna giusta anche quando l'ordine dei campi cambia.

### 🛠️ Admin

* Gestione date e orari riallineata al tempo locale SQL: filtri dinamici, notifiche e task schedulati evitano conversioni UTC implicite, riducendo gli scarti temporali tra backend e database.
* Template procedure CUD e guida Admin potenziati: aggiunti esempi pratici su `updatedData`, refresh della riga e comportamento runtime dei permessi, per configurare stored procedure più prevedibili.
* Configurazione pulsanti custom evoluta end-to-end: introdotto il nuovo campo `CB_ColumnName`, con aggiornamenti a schema, migration, API e pannello Admin per scegliere e mantenere la colonna in modo piu stabile.
* Documentazione tecnica estesa su import Excel e dominio dati: aggiunta una proposta per automatizzare le validazioni, con materiale di supporto aggiornato per analisi funzionale e operativa.
* Export `datarider-config` riallineato al database `dgxuty`: aggiornate le snapshot dei comandi e ripuliti diversi oggetti operativi esportati, mantenendo il pacchetto di configurazione piu coerente con lo stato reale.

## 🔄 Versione 1.11.1 – 2026-02-27

### 👤 Utente

* Accesso da tablet semplificato: la schermata di login supporta ora la modalità con codice pairing e nome dispositivo, con passaggio rapido tra login classico e login tablet.

### 🛠️ Admin

* Workflow Excel Import riallineato alla connessione del comando: scenario e tracking operativo (`dr.ExcelImport`, `dr.ExcelImport_Execution`) vengono gestiti sul pool di esecuzione, riducendo errori nei contesti multi-server e mantenendo centralizzati solo metadata e log applicativi.
* Processo di update backend più robusto in ambienti Linux: introdotti controlli su esecuzione root/sudo, avvio detached più affidabile (`nohup`) e logging tecnico arricchito per diagnosi più rapide.
* Device mode consolidato lato autenticazione: aggiunti scambio pairing, refresh token dispositivo e logout dedicato, con documentazione Admin/tecnica aggiornata sui flussi operativi.

## 🔄 Versione 1.11.0 – 2026-02-23

### 👤 Utente

* Nuova modalità Tablet con profili dispositivo: l’accesso da device dedicati è più rapido e mirato, con visibilità dei comandi governata dal profilo assegnato al dispositivo.
* Gestione import Excel più chiara: il download del modello supporta metadati opzionali sulle colonne, migliorando la preparazione dei file prima del caricamento con istruzioni per ogni campo e menu a tendina per convalida sui campi a selezione.

### 🛠️ Admin

* Device Mode introdotto end-to-end: nuove tabelle DB, token/device profile dedicati, aggiornamenti su auth/permessi e nuove API per gestire dispositivi, profili e associazione comandi.
* Schedulazione e sicurezza operativa migliorate per i dispositivi: il backend distingue meglio i contesti utente/device e applica controlli coerenti sui flussi di autenticazione e autorizzazione.
* Tooling Admin su Import Excel/SQL affinato: aggiornate route e componenti del pannello (incluso `sql-textarea`) per una configurazione più robusta e leggibile.
* Documentazione e versioning allineati ai nuovi flussi: guide Admin/feature aggiornate e stato release consolidato con il nuovo ciclo di rilascio.

## 🔄 Versione 1.10.2 – 2026-02-18

### 👤 Utente

* Schedulazioni email più flessibili per configurare email automatiche che restano sempre allineate alla finestra temporale desiderata (es. righe modificate nelle ultime XX ore).

### 🛠️ Admin

* Schedulazioni email più flessibili: nel wizard filtri puoi usare valori dinamici relativi al momento d’invio (es. ultime ore/giorni), così le email automatiche restano sempre allineate alla finestra temporale desiderata.
* Anteprima e selezione colonne più chiare nelle email schedulate: quando disponibili vengono mostrati anche i label configurati, migliorando leggibilità e coerenza tra pannello Admin e contenuto ricevuto.
* Processo di update più controllato: introdotte notifiche email di esito (success/failure) con dettagli operativi e tail log, oltre a una gestione più robusta dell’avvio script e degli errori durante l’aggiornamento.
* Tooling tecnico aggiornato: i profili TypeScript sono stati allineati per supportare meglio output dichiarazioni/composite e sono stati aggiunti script npm utili per auditing e manutenzione dipendenze.

## 🔄 Versione 1.10.1 – 2026-02-17

### 👤 Utente

* Export Excel massivo più affidabile in reti instabili: richiesta e avvio  ora gestiscono retry automatici sugli errori transitori, riducendo i fallimenti dovuti a timeout o interruzioni momentanee.
* Avvio export più sicuro contro duplicazioni involontarie: introdotta idempotenza per il `start` upload, così i ritentativi client non generano doppioni.

### 🛠️ Admin

* Tracciamento esiti export potenziato: il backend salva anche le righe effettivamente scritte per file e genera un `manifest_export_massivo.json` nello ZIP con riepilogo completo di file riusciti/falliti e conteggi attesi/reali.
* Gestione nomi file/cartelle resa più robusta su Windows: sanitizzazione separata per segmenti cartella e file per evitare path non validi senza perdere leggibilità.
* Tooling dipendenze migliorato: aggiunti script npm per auditing/aggiornamento pacchetti e migliorato `update-datarider_source.sh` con fallback automatico (`npm install` + nuovo `npm ci`) quando lockfile e dipendenze risultano disallineati.

## 🔄 Versione 1.10.0 – 2026-02-16

### 👤 Utente

* Nuova funzionalità di Export Excel massivo: nuova esperienza con modale dedicata, e possibilità di generare centinaia di file excel dinamicamente a partire da un comando.
* Condivisione link con parametri di input: i parametri possono essere condivisi con un semplice copia e incolla dell'URL, così aprendo il collegamento si ritrovano i valori già pronti senza reinserimento manuale.
* Migliorata la modale di caricamento per comandi in background, ora i secondi di progressione avanzano correttamente e la chiusura a fine caricamento dati avviene puntualmente.

### 🛠️ Admin

* Export Excel massivo esteso end-to-end: introdotte API/server route dedicate, nuovo service backend, configurazione colonne esportabili e ordinamento, con migliore efficienza di elaborazione lato server.
* Osservabilità e gestione errori rafforzate: tracciamento preflight/progresso più dettagliato, logging operativo ampliato e gestione errori più esplicita nei flussi di export e monitoraggio job.
* Monitor job e risultati più solidi: affinata la gestione dei risultati in backend e nella modale di monitoraggio, con test server aggiornati per coprire i nuovi scenari.
* Tooling e documentazione tecnica aggiornati: aggiunta guida completa per installazione stage su VM Linux e allineate le risorse operative correlate al nuovo flusso di export.


## 🔄 Versione 1.9.0 – 9 febbraio 2026

### 👤 Utente

* Dettaglio righe più ricco: la modale mostra la sequenza corrette delle colonne e formatta i valori in modo coerente, rendendo più chiara la lettura dei dati.
* Notifiche meno invasive: rimossa la toast di successo sull'esecuzione comando, lasciando spazio agli errori e riducendo il rumore visivo ed evitando anomalie mentre si stanno digitando i filtri di colonna.
* Formattazione numeri più fedele: i pattern decimali personalizzati ora vengono interpretati per mostrare la precisione attesa nelle celle.

### 🛠️ Admin

* Colonne comando: disponibile l'anteprima SQL con gestione parametri migliorata, utile per verificare la query direttamente dal pannello colonne.
* Job risultati: gestione file più robusta con percorsi case-insensitive, evitando errori in download/lettura su filesystem non uniformi.
* Configurazioni comandi: aggiunti preset di filtri/gruppi e job per numerosi comandi pricing/migrazione, con aggiornamenti correlati ai log e agli input parametri.
* Schedulazioni email: il SQL della schedulazione è sempre visibile con messaggio guida (anche senza parametri) e pulsante copia integrato per riuso rapido.

## 🔄 Versione 1.8.0 – 29 gennaio 2026

### 👤 Utente

* Esecuzione in background: i comandi lunghi possono partire asincroni con checkbox dedicata e una modale di monitoraggio che mostra avanzamento, log, tempo trascorso e pulsanti per annullare o aprire i risultati appena pronti.
* Notifiche in testata: i banner globali compaiono in alto con severità e messaggio leggibile, con possibilità di chiuderli senza perdere il lavoro in corso.
* Avvio automatico più prudente: le query con parametri inline o stored procedure non partono finché i parametri sono stati caricati, evitando esecuzioni premature.

### 🛠️ Admin

* Job asincroni: nuove API e worker per creare, monitorare, annullare e scaricare risultati dei job con logging eventi e gestione errori; documentazione aggiornata e test dedicati.
* Scheduler e notifiche: introdotte rotte admin per task pianificati, service di update, scheduler backend e servizi frontend per gestire notifiche utenti e operazioni schedulate.

## 🔄 Versione 1.7.3 – 28 gennaio 2026

### 👤 Utente

* Il tasto validazione ora riporta messaggi coerenti anche dopo timeout/abort.

### 🛠️ Admin

* `/api/execute/:id` ora logga durata, requestId, userId e stato (compresa la classificazione lato errore in caso di timeout o abort), e imposta `requestTimeout` dal `C_CommandTimeout` del comando; la documentazione Admin aggiunge la checklist “Diagnosi timeout e risposte non JSON” con suggerimenti di proxy e server.
* Validazione Excel: ogni regola scrive in `dr.ExcelImport_Execution` lo stato, l’errore e i dati coinvolti, le eccezioni vengono loggate con severità e il messaggio finale preferisce la prima regola fallita anche quando non ci sono righe di errore.

Commit range: 9a656f60b974b2bb871ae5c4bb314267b949a885..e44efb7512c255248095dec7a217c81cf51ba672

## 🔄 Versione 1.7.2 – 27 gennaio 2026

### 👤 Utente

* Esecuzione comandi più robusta: se il server risponde con HTML o va in timeout, l’app mostra un messaggio leggibile con riepilogo e dettaglio copiabile, evitando l’errore “Unexpected token <”.

### 🛠️ Admin

* Logging e timeout: l’esecuzione comando registra durata, requestId e tipo di errore; il timeout `mssql` ora rispetta quello del comando.
* Documentazione operativa: aggiunta checklist end‑to‑end su timeout (frontend, backend, proxy) con prova riproducibile per query lente.
* Release: versioning e note di rilascio allineate al ciclo di distribuzione.

## 🔄 Versione 1.7.1 – 26 gennaio 2026

### 👤 Utente

* Copia rapida: nei risultati con tag/descrizioni il click copia il valore già formattato, evitando di dover selezionare manualmente il testo grezzo.

### 🛠️ Admin

* Default filtri/gruppi: nuovo manager in Admin e API dedicate per creare, validare e applicare predefiniti di filtri e raggruppamenti per comando; DataTable e CommandExecutor li applicano automaticamente.
* Import Excel: tracking potenziato con nome file, esiti e messaggi di errore salvati in `dr.ExcelImport_Execution`; migliorata la gestione degli esiti di validazione e il logging degli step.

## 🔄 Versione 1.7.0 – 22 gennaio 2026

### 👤 Utente

* Filtri avanzati: nuovo operatore “Copia e incolla lista” con modale dedicata che deduplica i valori incollati, mostra quante righe corrispondono e permette di evidenziare quelli mancanti prima di applicare il filtro.
* Navigazione home più chiara: clic (o invio/spazio) su logo e titolo riporta alla home, azzera selezioni/pannello admin e mantiene l’icona animata solo durante il caricamento.

### 🛠️ Admin

* Import Excel: logga il completamento su `dr.ExcelImport_Execution` risolvendo l’utente, accetta `ResultFlag/ResultMsg` anche in recordset successivi, e rende opzionale la stored di validazione mostrando un avviso finché il pulsante non è salvato; documentazione allineata.
* Prompt/generazione guide: endpoint `/api/commands/:id/prompt` restituisce anche regole di validazione Excel (con definizione SQL) e schedulazioni email, e il pannello Admin le include insieme a stile tabella, export e pulsanti personalizzati nella richiesta generata.
* Log diagnostici più leggibili: la modale di dettaglio è più ampia e forza il ritorno a capo di stack trace e context per consultazioni lunghe.
* Tooling: rimosso lo script `release:notes` non utilizzato per evitare riferimenti a comandi inesistenti.


## 🔄 Versione 1.6.10 – 20 gennaio 2026

### 👤 Utente

* Aggiunta pagina **Guida** con link dal menu superiore e richiamo dalla home: raccoglie la documentazione utente aggiornata per orientarsi rapidamente.

### 🛠️ Admin

* Rotta server `/api/help` e route FE dedicate alla documentazione; header e index mostrano l’accesso rapido alla guida.
* Import Excel: validazione più robusta con gestione errori migliorata e fallback di connessione, per ridurre blocchi durante upload/transform/validate.
* Logger color-coded per livelli log in console; query di esportazione config aggiornata (command groups) e gestione stringhe di connessione negli script allineata.
* Refactor struttura codice (help, import) per leggibilità/manutenibilità senza cambi di comportamento.

## 🔄 Versione 1.6.9 – 20 gennaio 2026

### 👤 Utente

* Nessuna modifica lato utente in questa versione.

### 🛠️ Admin

* Nessuna modifica registrata nei commit odierni.

## 🔄 Versione 1.6.8 – 19 gennaio 2026

### 👤 Utente

* Anteprima XML migliorata: finestra più ampia con evidenziazione sintassi e pulsante copia; la preview compatta nella tabella resta leggibile senza aprire file esterni.
* Dettaglio righe più chiaro: la modale applica etichette e visibilità definite dal comando (colonne nascoste o solo Admin) e normalizza i tipi numero/data/boolean/percent anche con alias SQL comuni per un rendering coerente.

### 🛠️ Admin

* Schedulazioni email: le configurazioni salvano anche il `commandSql`, mostrato in UI e usato dal worker/test-send per avere log e invii coerenti con la query schedulata.
* Pannello colonne: il refresh propone un’anteprima del comando con parametri di default (da saved parameters o `SELECT`), permette di lanciare l’anteprima guidata e mantiene il focus/patching delle righe più stabile.
* Log diagnostici: nuova tabella `dr.DiagnosticLog` con middleware di error handling che registra `requestId` e utente; API e pannello Admin dedicati per consultare rapidamente gli errori recenti con dati sanitizzati.
* Documentazione: aggiunte istruzioni di installazione/configurazione (Linux VM, PM2, Nginx) e guide aggiornate nella sezione docs.

## 🔄 Versione 1.6.7 – 16 gennaio 2026

### 👤 Utente

* Colonne **% Percentuale**: i valori vengono formattati come percentuali con barra di avanzamento (0–100) per leggere subito lo stato di completamento.
* Colonne **XML**: un clic apre una modale di anteprima formattata per leggere rapidamente il contenuto senza scaricare file.

### 🛠️ Admin

* Nuovi tipi campo nel tab **Colonne**: `% Percentuale` e `XML`, con suggerimenti di formato precompilati.
* Rendering tabella aggiornato: gestione coerente di percentuali (clamp 0–100, progress bar) e preview XML riutilizzabile anche con formattazione condizionale.
* Helper client aggiornati (`commandApi`, `tableFormat`, `DataTable`) per i nuovi tipi, mantenendo compatibilità con filtri e export.


## 🔄 Versione 1.6.6 – 16 gennaio 2026

### 👤 Utente

* Import Excel: l'anteprima mostra ora correttamente le righe anche quando la tabella di staging è su connessioni/database diversi da quello standard.

### 🛠️ Admin

* Le rotte di anteprima/PUT/DELETE e cancel dell'import Excel riutilizzano `C_ConnectionId`, allineando la connessione di staging a quella del comando.
* La validazione Excel apre il pool sul database del comando (stessa connessione di staging), evitando letture su DB sbagliati.

## 🔄 Versione 1.6.5 – 14 gennaio 2026

### 👤 Utente

* Le email schedulate rispettano ora l'orario configurato (es. 07:47) senza spostamenti di un'ora in invio o in fase di modifica.

### 🛠️ Admin

* Aggiunto pulsante **Duplica** nelle azioni del tab Schedulazioni email: crea una copia con suffisso "- Copia x" e calcola il prossimo run automaticamente.
* Salvataggio e rilettura dell'orario di invio normalizzati (TIME senza shift di timezone, UI mostra `HH:mm` coerenti).
* Nuovo endpoint `POST /api/commands/:commandId/email-schedules/:scheduleId/duplicate` e relativo metodo client per gestire la duplicazione da pannello.

## 🔄 Versione 1.6.4 – 29 dicembre 2025

### 👤 Utente

* In Import Excel, il pulsante **Scarica Modello** ora genera correttamente il file anche quando il comando usa una **connessione/database specifici** (evitando errori “procedura non trovata” dovuti al database sbagliato).

### 🛠️ Admin

* L’endpoint di esecuzione Import Excel usa ora il `C_ConnectionId` del comando (stessa logica di staging/transform) per aprire l’`execPool` sul **database del comando**.
* Migliorata coerenza tra Import/Transform/Download modello: la stored procedure viene risolta nello stesso contesto DB previsto dalla configurazione comando.

## 🔄 Versione 1.6.3 – 29 dicembre 2025

### 👤 Utente

* Le **email schedulate** supportano ora segnaposto dinamici nell’**Oggetto** (es. `{{TODAY}}`, `{{WEEKDAY}}`, `{{MONTH}}`, `{{COUNT}}`), sostituiti automaticamente al momento dell’invio.
* Nel pannello Admin, accanto al campo Oggetto trovi un piccolo aiuto e pulsanti rapidi per inserire i segnaposto senza errori di digitazione.

### 🛠️ Admin

* Aggiunta gestione dei segnaposto nell’oggetto durante l’invio (worker) e durante il **test-send**.
* Token supportati:
  * `{{TODAY}}` = data invio in formato `dd/mm/yy`
  * `{{WEEKDAY}}` = giorno della settimana (IT)
  * `{{MONTH}}` = mese corrente in formato `MM - Nome`
  * `{{COUNT}}` = numero righe risultanti (dopo filtri/colonne per email)
* Il calcolo rispetta la timezone della schedule (default `Europe/Rome`) e l’oggetto viene limitato a 255 caratteri.
* Aggiornata la guida Admin con la sezione dedicata ai segnaposto.

## 🔄 Versione 1.6.2 – 19 dicembre 2025

### 🛠️ Admin

* Nuovo editor **Stili colonne** più compatto: tabella + pannello Inspector a destra (senza scroll orizzontale) con navigazione rapida.
* Aggiunto campo **Etichetta** per colonna (salvato in configurazione comando) e utilizzato in UI al posto del nome tecnico, mantenendo inalterata la logica interna.
* Migliorata configurazione di **Seq/Larghezza** con controlli rapidi `-25px / +25px`.
* Allineamento colonna reso più immediato (controlli inline sul tipo).
* Campo **Formato** con elenco di formati comuni in base al tipo (resta possibile inserire un formato manuale).
* Editor aspetto integrato: **Dimensione font** + toggle **B/I** + selezione colori testo/sfondo (stabile su Edge durante l’uso del color picker).

## 🔄 Versione 1.6.1 – 19 dicembre 2025

### 👤 Utente

* Migliorata l’esportazione **CSV/XLSX** per evitare righe “spezzate” quando un campo contiene a capo (`\r`, `\n`).
* I valori testuali che “sembrano numeri o date” (es. codici con zeri iniziali, notazione scientifica, date, codici con punto decimale) vengono preservati come **testo** più fedelmente durante l’apertura in Excel.
* In fase di export, DataRider sanifica gli a capo nei campi testo e applica una protezione per ridurre le conversioni automatiche di Excel.

### 🛠️ Admin

* L’export CSV applica una protezione “Excel-safe” per stringhe a rischio auto-conversione, così i codici restano invariati in apertura (es. niente trasformazioni in date o separatori migliaia non voluti).
* L’export XLSX forza le celle delle colonne configurate come **stringa** a restare testo, riducendo la conversione automatica (scientifica/date/numerica) da parte di Excel.
* L’export considera la configurazione colonne (tipo/formato) quando disponibile, per mantenere coerenza tra visualizzazione e file esportato.

## 🆕 Versione 1.6.0 – 18 dicembre 2025

### 👤 Utente

#### 📧 Report via e-mail programmati

* Ora puoi ricevere **report automatici via e-mail** con i risultati di un comando SQL, includendo solo le **colonne** e i **filtri** configurati.
* Il corpo dell’e-mail include un pulsante **“Apri in DataRider”** per aprire direttamente il comando.
* La tabella nell’e-mail applica la **formattazione condizionale** del comando (colori testo/sfondo e icone) per evidenziare subito anomalie o soglie.

### 🛠️ Admin

* Introdotta la schedulazione e-mail per comando: puoi creare **più schedulazioni** per lo stesso comando.
* Pianificazione supportata: `DAILY`, `WEEKLY`, `MONTHLY` o `CRON`, con **timezone configurabile** (default `Europe/Rome`).
* Nuova configurazione SMTP centralizzata (singleton) con password **cifrata lato server**.
* Disponibile invio di **test e-mail** per verificare template e destinatari prima dell’attivazione.
* Worker in-process resiliente con **lock su DB + TTL** per evitare doppie esecuzioni e recuperare schedulazioni rimaste “in progress”.
* Log esecuzioni schedulazioni con esito, destinatari, numero righe ed eventuale errore per diagnosi rapide.
* Supporto a mittente per schedulazione (`From`/`Reply-To`) con **fallback automatico** quando il provider SMTP rifiuta l’override del mittente.

## 🔄 Versione 1.5.22 – 20 novembre 2025

### 👤 Utente

* Aggiunto riferimento della connessione (Server, Database, Utente) sotto il titolo "Comando SQL" per visibilità immediata delle risorse utilizzate.

## 🔄 Versione 1.5.21 – 19 novembre 2025

### 👤 Utente

* Corretta filtro su elenchi nella maschere di modifica riga che non permettevano la ricerca

## 🔄 Versione 1.5.20 – 04 novembre 2025

### 👤 Utente

* Corretta esecuzione procedura di trasformazione da import da excel rispetto a configurazioni del comando.
* Migliorata velocemente di elaborazione delle regole di validazione dati da import da excel

## 🔄 Versione 1.5.19 – 03 novembre 2025

### 👤 Utente

* Migliorata la validazione in fase di importazioni file da excel per segnalare meglio errori riscontrati.


## 🔄 Versione 1.5.18 – 31 ottobre 2025

### 👤 Utente

* L'import Excel mostra una modale di avanzamento quando premi **Valida**: ogni regola
  viene elencata con stato live (spinner, successo o errore) e la finestra si chiude
  automaticamente al termine del controllo.

## 🔄 Versione 1.5.17 – 31 ottobre 2025

### 👤 Utente

* Gli errori mostrati durante l'import Excel riportano ora il contenuto reale della risposta
  HTTP (inclusi eventuali HTML o messaggi proxy), facilitando la diagnosi senza dover
  ispezionare manualmente la console.
* Le procedure Importa/Trasforma/Valida/Esegui ereditano il timeout configurato sul comando,
  evitando chiusure premature della modale quando le stored SQL 2016 richiedono più tempo.

### 🛠️ Admin

* Il client `commandApi` centralizza il parsing delle risposte tramite l'helper riutilizzabile
  `parseApiResponse`, eseguendo il fallback su `response.text()` quando il JSON è assente o
  invalido e propagando messaggi chiari con lo stato HTTP.
* Le chiamate Excel import utilizzano `fetchWithTimeout` e accettano `timeoutMs` opzionale,
  propagato dalla UI in millisecondi per condividere lo stesso limite di rete del comando.

## 🔄 Versione 1.5.16 – 22 ottobre 2025

### 👤 Utente

#### 🧮 Allineamento dei totali

* La **riga dei totali** ora resta perfettamente allineata anche quando la colonna di selezione viene nascosta.
* Le celle ad inizio riga di **Info** e **Azioni** rimangono sincronizzate con le colonne superiori, garantendo un layout pulito e leggibile.

#### 🔔 Esperienza utente migliorata

* La **duplicazione riga** mostra sempre il riepilogo e il toast di conferma (“Duplicazione riga”) anche quando la stored utilizza `@Modality='insert'`, mantenendo la coerenza visiva con le altre azioni.

---

### 🛠️ Admin

#### 🧩 Wizard di Formattazione Condizionale

* Aggiunto il pulsante **“Apri Wizard”** accanto al campo *Espressione* nella scheda **Formattazione Condizionale**.
* Il nuovo **wizard interattivo** consente di:

  * scrivere e testare formule **JavaScript tipizzate**,
  * usare riferimenti come `row['Nome Completo']` con operatori sicuri (`??`),
  * validare la sintassi in tempo reale,
  * inserire automaticamente l’espressione nella regola selezionata.

#### 🧱 Sincronizzazione e layout tabella

* Il **footer di `DataTable`** eredita le classi sticky dalle sezioni Info e Azioni, mantenendo l’allineamento anche con `hideSelection` attivo.
* Il comportamento di **scroll e blocco colonne** è ora coerente in tutte le visualizzazioni, inclusa quella con colonne virtualizzate.

#### 🧰 Ottimizzazioni tecniche

* Rimossa la prop non booleana `closeOnClick={false}` nel componente `Toast`, sostituita con la gestione tramite `onPointerDownCapture` su elementi `data-toast-selectable="true"`.
* Eliminato l’avviso React *“Received `false` for a non-boolean attribute”* mantenendo inalterato il blocco della chiusura accidentale dei toast.
* Le richieste `POST /api/commands/:commandId/edit/insert` impostano sempre `@Modality='insert'`, assicurando compatibilità completa con stored SQL Server 2016 anche durante duplicazioni e inserimenti automatici.

---

## 🔄 Versione 1.5.15 – 10 ottobre 2025

### 👤 Utente

* **Duplicazione dati**: la modale di inserimento riconosce ora la modalità "duplica" e mostra un messaggio dedicato quando si crea una copia della riga originale, mantenendo precompilati i valori di partenza.
* **Filtri tabella**:

  * Il filtro rapido delle colonne richiede ora la conferma esplicita con **Invio** o uscendo dal campo; compare il suggerimento “Invio per filtrare” e l’applicazione avviene solo al commit, evitando aggiornamenti indesiderati durante la digitazione. Niente più “lampeggi” o ritorni al valore precedente durante la digitazione lenta
  * Quando si cancella completamente il testo del filtro rapido la tabella si aggiorna all’istante senza attendere blur o Invio.
  * Navigazione tastiera nei filtri rapidi: **Tab** passa al campo successivo e **Shift+Tab** a quello precedente con focus circolare, per applicare più criteri senza uscire dalla griglia.
  * La ricerca globale della tabella e i filtri rapidi reagiscono in modo più fluido: l’input viene applicato dopo una pausa di circa 320 ms e lo svuotamento aggiorna subito i risultati.
  * Ogni filtro rapido delle colonne mostra ora una **X** interna: basta un click per svuotare il campo e aggiornare subito la tabella senza dover premere Invio.
  * Anche la ricerca veloce sopra la tabella nel database espone la stessa **X**: cancelli il testo in un istante e i risultati tornano all’elenco completo.

* **Import da Excel**:

  * mantengono apostrofi e accenti grazie a parametri SQL (niente più concatenazioni che corrompono il testo);
  * mostrano il **valore reale** dei campi indicati come `[Campo]`, così l’operatore capisce subito cosa correggere nella riga evidenziata.
  * I messaggi dei toast di import/transform/validate Excel vanno ora a capo automaticamente e consentono lo **scroll verticale** quando molto lunghi, così puoi leggere/copiarne l’intero contenuto.
  * Un pulsante **Copia** compare nell'angolo in basso a destra delle notifiche; annuncia l'esito con screen reader e consente di salvare negli appunti messaggi multi-riga.

* **Vario**:
  * La barra superiore mostra una sola icona per ogni persona connessa, evitando duplicazioni quando lo stesso utente apre più sessioni.
  * I pulsanti di testata ora applicano le azioni solo alle righe ancora visibili dopo un filtro; le righe selezionate conservano l’indice originale anche dopo filtri/ordinamenti, mantenendo corretta evidenziazione e azioni inline.
  * Le icone dei colleghi connessi nel bordo superiore mostrano ora da quanto tempo sono attivi in DataRider, così capisci subito se sono ancora online.
---

### 🛠️ Admin

* **Permessi duplicazione**: l'endpoint `POST /commands/:id/edit/insert` accetta il parametro `mode=duplicate`, verifica il flag `allowDuplicate` separatamente da `allowInsert`, imposta `@Modality='duplicate'` verso SQL Server e garantisce copertura Jest per ruoli che possono duplicare ma non inserire.
* **Presenza utenti**:
  * deduplica lato client degli utenti attivi da API (per ID/email) per evitare avatar duplicati in UI.
  * Gli amministratori vedono un pulsante **Refresh** sotto le icone: un click aggiorna istantaneamente la lista senza attendere l'intervallo automatico.
* **QuickSearchInput / DataTable**:

  * Il commit del filtro avviene solo via `applyFilter` (Enter/blur); rimosso il debounce interno.
  * Mantiene testo grezzo durante l’editing (`draftValueRef`) e applica formato normalizzato solo al commit, ignorando aggiornamenti props finché il campo è attivo (`lastFormattedValueRef`).
  * `onChange(null)` viene emesso solo quando il campo viene realmente svuotato; al reset via `onChange` viene chiamato `applyFilter`.
  * Focus automatico applicato solo quando cambia `autoFocus` e il campo non è già attivo, evitando selezioni involontarie del testo.
  * Espone `onBlur`; `DataTable` lo usa per azzerare `focusedQuick` (insieme a `onFocus` del filtro globale) confinando gli auto-focus alla colonna selezionata.
  * Pulsante di reset accanto al filtro resta **a singolo click**; ripuliti stato interno, draft e formattazione quando non esiste più un filtro esterno, evitando re-invii su blur.
  * Tracciamento con `console.debug` di commit/reset e mutazioni di `quickFilterValues` per diagnosi.
* **Formattazione/Operatori**:

  * `formatFilterValue` gestisce `equals`/`in`/`not_equals` e normalizza operatori con valore singolo, multiplo e intervalli; riuso della stessa logica in `DataTable` per popolare `quickFilterValues` anche da imbuto avanzato.
* **Sincronizzazione & Focus**:

  * Effetti di sync rilevano quando il parent non ha ancora propagato il filtro e preservano `search`/`lastFormattedValueRef`, azzerando `draftValueRef` solo su reset reale.
  * Early-exit quando `formatted` è vuoto ma `lastFormattedValueRef` contiene il testo confermato, per non svuotare UI in transito.
  * `hasDirtyInputRef` distingue cancellazioni intenzionali da vuoti transitori in blur/rerender, ripristinando `search` se l’utente non ha digitato modifiche.
  * `DataTable` memorizza l’ultimo filtro rapido confermato per colonna e lo ripropone a `QuickSearchInput` via prop `committedValue`.
  * `DataTable` differisce l’azzeramento di `focusedQuick` dopo blur con un timeout minimo; il timeout è cancellato quando un nuovo filtro riceve focus (prevenzione race condition).
  * Nuovo hook `useQuickFilterFocus` per la gestione centralizzata del focus tra filtri; tutti gli input con `data-quick-search-input` supportano **Tab/Shift+Tab** con focus circolare via DOM API.
* **Ricerca globale**:

  * Usa `useDebouncedCallback` con `QUICK_SEARCH_DEBOUNCE_MS = 320`; personalizzazione del ritardo disponibile solo per la ricerca globale (rimosso `debounceMs` da `QuickSearchInput`).
  * `pendingGlobalSearchRef` mantiene allineati input e valore effettivo, evitando overwrite durante digitazione lenta.
* **Azioni su righe/indici**:

  * `DataTable.executeHeaderButton` usa `processedData` e salta righe non più visibili; evita azioni su record filtrati via.
  * `processedData` produce `{ row, originalIndex, visibleIndex }`; catena di filtri/ordinamenti/paginazione e `executeButtonAction` propagano `originalIndex` verso backend e `applyRowUpdateHighlight` per aggiornare la riga corretta.
* **Excel / Validazioni**:

  * `dr.sp_Excel_Import_Validation_0001`: utilizza `sp_executesql` con parametro `@ErrMsgParam` per l’`UPDATE` della staging, sostituendo i placeholder `[Campo]` con `REPLACE` nidificati; protezione da injection e gestione apostrofi.
  * `dr.sp_Excel_Import_Validation`: risolve dinamicamente i placeholder `[Campo]` partendo da `sys.columns` e li sostituisce con `COALESCE(CONVERT(NVARCHAR(MAX), T.[Campo]), '')`; placeholder non risolti restano testuali come segnale di configurazione errata.
* **Toast & UI di debug**:

  * `ToastDescription` abilita wrapping e scrollbar verticale per contenuti estesi; la variante base del toast usa `overflow-y-auto` (al posto di `overflow-hidden`) così i dettagli delle stored sono copiabili integralmente durante il debug.
  * `ToastCopyButton` tenta `navigator.clipboard.writeText` e, quando l'API non è disponibile o fallisce (es. contesto non HTTPS), ricade su `document.execCommand('copy')`, ripristinando la selezione iniziale e annunciando il successo tramite `aria-live`.
  * `Toaster` aggiunge `min-w-0` al contenitore del contenuto dei toast per permettere la compressione corretta della colonna flessibile e prevenire overflow laterali nelle descrizioni estese, lasciando invariati i controlli di chiusura e copia.
* **Test & qualità**:

  * Suite Jest/integrazione aggiornata per i percorsi `Enter → blur`, click → commit → reset, gestione `undefined` temporanei di `value`/`committedValue`, e per la reattività del pulsante **Reset Filtri** al primo click.
  * Copertura dedicata per `useQuickFilterFocus` e per i casi blur da pulsante vs passaggio focus a un altro input.
* **Configurazione comandi**:

  * Il form conserva `tableStyle` durante gli update; la duplicazione apre subito la copia completa di ruoli, parametri e stili per verifica e ritocchi senza perdere configurazioni avanzate.
  * I report che usano bande/colore alternato mantengono la formattazione anche dopo modifiche admin ai comandi: lo stile tabellare non viene più azzerato dai salvataggi del tab Comandi.

## 🔄 Versione 1.5.11 – 30 settembre 2025

### 👤 Utente

### 🛠️ Admin

- Le etichette del tab Import parlano ora di "pulsanti" (Esegui/Trasformazione/Validazione) e della relativa procedura SQL, rendendo più intuitiva la configurazione dei passaggi della modale.
- L'anteprima modificabile dei dati Excel mantiene la larghezza iniziale delle colonne ma permette ora di trascinare il bordo destro dell'intestazione per espanderle o comprimerle rapidamente, rendendo più leggibili i valori lunghi senza perdere spazio orizzontale.
- 📤 L'importazione Excel dei comandi collegati a server remoti crea ora la tabella temporanea `dr.zz_*` direttamente sul server configurato per il comando, così gli step successivi (Trasforma/Valida/Esegui) trovano sempre i dati senza dover ripetere l'upload.
- 🔍 La preview delle tabelle di staging (`GET/PUT/DELETE /preview`, `DELETE /cancel`) funziona ora anche per i comandi configurati su server remoti, eliminando l'errore "Invalid object name" quando la tabella temporanea viene creata fuori dal database principale.
- 🌐 Le rotte di anteprima e manutenzione (`GET/PUT/DELETE /preview`, `DELETE /cancel`) ricostruiscono `stagingConfig` con `loadConnectionConfig`, forzano il database su quello dichiarato in `dbConfig` e aprono un pool dedicato per interrogare `dr.zz_*`, mantenendo `dbConfig` per `dr.ExcelImport` e il logging.
- 🗄️ L'endpoint `POST /api/commands/:commandId/upload` carica la configurazione `C_ConnectionId`, forza il database su `DgxUty`, armonizza `requestTimeout`/`trustServerCertificate` e apre un pool dedicato per `CREATE TABLE` e `bulk`, lasciando il pool principale per log e `dr.ExcelImport`.
- ✅ In caso di errore nell'apertura della connessione di staging l'API interrompe l'operazione con un messaggio esplicito: verificare manualmente, tramite `SELECT @@SERVERNAME` o l'elenco tabelle del server remoto, che `dr.zz_*` venga creata dove atteso prima di lanciare le stored successive.

---

## 🔄 Versione 1.5.10 – 25 settembre 2025

### 👤 Utente

#### 🔢 Ordinamento condivisibile via URL

* I link ai comandi supportano ora il parametro `orderby` (es. `orderby=Cliente-asc,Fatturato-desc`) che memorizza l'ordinamento configurato nella tabella risultati e lo ripristina automaticamente al caricamento della pagina.

#### 🪟 Importazione da excel

* La finestra **Monitoraggio esecuzione** resta in primo piano fino al completamento del processo.
* Il pulsante **Chiudi**, i tasti **ESC** e l'overlay sono disabilitati fino alla fine, evitando interruzioni accidentali dell’import massivo.
* Ogni step (Importa → Trasforma → Valida → Esegui) mostra messaggi chiari, contatori di righe elaborate e indicatori di severità, direttamente nella modale.
* I pulsanti della procedura si sbloccano uno alla volta: in caso di errore, la UI spiega come intervenire prima di consentire l’avanzamento.
* Ogni modifica fatta dall’anteprima Excel è registrata automaticamente per migliorare il supporto e la diagnostica post-esecuzione.
* Corretto il layout della sezione “Tipi colonne” e la gestione visiva dei pulsanti, che ora sono sempre accessibili e coerenti con lo step attivo.
*-* La finestra **Monitoraggio esecuzione** mostra ora sempre il messaggio conclusivo della procedura Excel, anche in caso di errore, così non resta più vuota quando la stored restituisce solo `ResultMsg`.

#### 🔐 Filtri contestuali sui parametri

* Le tendine popolate da query personalizzate possono sfruttare i placeholder contestuali (`@CurrentUser`, `@CurrentUserId`, `@IsAdmin`) per mostrare all’utente solo i valori pertinenti al proprio account, lasciando agli amministratori la visibilità completa.

---

### 🛠️ Admin

#### 🗃️ Logging avanzato su `dr.LogTable`

* Tutti gli step (`Upload`, `Transform`, `Validate`, `Execute`) scrivono log centralizzati tramite gli helper `logEvent`/`logExcelEvent`.
* Ogni entry include: scenario (`LT_Modality`), step (`LT_ExecutionType`), severità e metadati serializzati in `LT_RowData`.

#### 📑 Contratto standard di output per stored procedure Excel

* Le stored devono restituire:

  * `ResultFlag`: determina l'esito e blocca/sblocca la prosecuzione degli step.
  * `ResultMsg`: alimenta i messaggi utente e il log.
  * `ProcessedRows`, `AffectedRows`, `RowsWithError`, ecc.: usati per popolare il riepilogo.

#### 🧾 Audit trail completo

* Le rotte `PUT/DELETE /preview` registrano ID riga e contenuti aggiornati o rimossi con severità `INFO`, facilitando rollback e verifiche.

#### 🏷️ Nomenclatura pulsanti Import Excel

* Gli switch "Configura Import/Trasformazione/Validazione" sono stati rinominati in "Configura pulsante ..." per legarli visivamente ai pulsanti della modale di esecuzione.
* I campi "Azione SQL ..." mostrano ora "Procedura SQL pulsante ..." esplicitando che devono contenere la stored procedure invocata dal relativo bottone.

#### 📘 Documentazione operativa aggiornata

* Aggiornato il `README` con:

  * Linee guida sul logging sicuro.
  * Formato atteso per gli output delle stored.
  * Raccomandazioni per evitare serializzazione di dati sensibili.

#### 🧩 Placeholder contestuali per SELECT

* Il backend inietta automaticamente le variabili contestuali (`@CurrentUser`, `@CurrentUserId`, `@IsAdmin`) nelle query `SELECT` dei parametri tramite binding MSSQL, evitando l’uso di `SYSTEM_USER` e mantenendo le interrogazioni parametrizzate.
* Documentata nel `README` la sintassi dei placeholder e il pattern `(@IsAdmin = 1 OR Campo = @CurrentUser)` così che gli admin mantengano accesso completo senza rimuovere il filtro per gli altri ruoli.

#### 🛠 Rifattorizzazione JSX in `ExcelImportModal`

* Corretta la chiusura di container JSX e condizioni `if`.
* Garantita la coerenza visiva e funzionale nella sequenza Importa → Trasforma → Valida → Esegui.
* La rotta `POST /api/commands/:commandId/execute` normalizza l'oggetto `finalResult` utilizzando `ResultMsg`/`ResultError` e `EIE_ResultError` come fallback per titolo, messaggio e icona: anche le stored che non valorizzano `Title`/`Message` producono ora log coerenti e un esito visibile alla UI.
* Introdotti gli helper `pickFirstString` e `normalizeFinalResult` in `server/routes/excelImport.ts` per sanificare le stringhe, ridurre la duplicazione di codice e forzare `status` su valori ammessi (`success`/`error`), migliorando tracciabilità e sicurezza.

---


## 🔄 Versione 1.5.8 – 1 settembre 2025

### 👤 Utente
- Nessuna modifica lato utente in questa versione.

### 🛠️ Admin
- 🔄 **Aggiornamento applicazione più fluido**:
  - Migliorato il sistema di **monitoraggio dello stato di aggiornamento** con polling progressivo.
  - L'utente riceve aggiornamenti in tempo reale durante l'installazione delle nuove versioni.
- ✍️ Ora è possibile **modificare manualmente il prompt** nella scheda *Guida* del pannello amministrativo per generare la guida utente dei comandi SQL.
- ⚙️ **Ottimizzazioni sistema di aggiornamento**:
  - Lo script di aggiornamento ora viene **eseguito in modalità asincrona** e con `nohup`, garantendo maggiore affidabilità.
  - Aggiunto **timeout per arresto forzato di PM2**.
  - Introdotto il **ripristino automatico dei file `.env` e `package-lock.json`** in caso di errore.
  - I log PM2 includono ora **timestamp** per una tracciabilità più precisa.
  - Le variabili d’ambiente vengono caricate da file in modo standardizzato.
  - Migliorato il formato dei commenti e la leggibilità dello script `update-datarider_source.sh`.

- 🧠 Le **configurazioni dei ruoli** vengono ora **mantenute anche dopo l’aggiornamento dei comandi**, evitando sovrascritture involontarie.

---


## 🔄 Versione 1.5.7 – 29 agosto 2025

### 👤 Utente

- 👥 **Visualizzazione utenti attivi**: ora nella **barra in alto** è possibile vedere chi è attualmente connesso all'applicazione.
- ✅ **Gestione sessioni utente**: viene tracciata la presenza attiva e la disconnessione automatica degli utenti non più attivi.
- 🎨 **Personalizzazione tabella**: introdotta la possibilità di applicare uno **stile configurabile alla tabella dei risultati** (es. colorazione righe alternate).

---

### 🛠️ Admin

- ⚙️ **Servizio di presenza utenti**: implementato un sistema per **monitorare in tempo reale le sessioni attive** degli utenti via WebSocket.
- 🧪 **Logging avanzato**: 
  - I tentativi falliti di connessione WebSocket vengono ora **registrati nei log**.
  - La procedura SQL personalizzata ora **logga automaticamente i dati della riga** al termine della transazione.
- 🧼 **Template procedure ottimizzati**: rimossi i comandi `GO` per una maggiore compatibilità con esecuzioni automatizzate.
- 🛑 **Controllo e gestione aggiornamenti**:
  - Verificato che lo **script di aggiornamento** abbia permessi eseguibili.
  - In caso di errore, viene **restituito un messaggio utile**.
  - Gestito il **timeout e il risultato del comando `pm2 stop`**.
- 🧩 **Messaggi di errore migliorati**: se un aggiornamento dell'app fallisce, viene mostrato un **messaggio chiaro** all'utente.
- 📏 **Modale parametri SQL ottimizzata**: l'altezza della finestra è ora bloccata per evitare problemi di visualizzazione su schermi piccoli.
- 🛠️ **Compatibilità estesa per pulsanti**: tutti i **pulsanti comando** vengono ora mostrati anche se non legati direttamente al ruolo utente (utile per debugging o sviluppo).
- 🧪 **Debug avanzato SSH**: aggiunti **log dettagliati** per il monitoraggio delle connessioni SSH Tail.
- 🧩 **Gestione WebSocket migliorata**: ottimizzato il logging per connessioni real-time.
- 🧱 **Procedura SQL da comando**: ora è possibile **creare automaticamente una stored procedure** a partire da un comando.
- 🧠 **Integrazione OpenAI migliorata**:
  - La rotta per la generazione guidata ora gestisce correttamente l’**assenza della chiave API OpenAI**.
  - Aggiunte le **istruzioni su come configurare la chiave OpenAI** nella documentazione.

---


## 🔄 Versione 1.5.6 – 28 agosto 2025

### 👤 Utente

- ✅ **Importazione Excel migliorata**:
  - Ora è possibile gestire un pulsante di validazione in fase di importazione, prima di aggiornare i dati a database. Possono essere eseguite più validazioni prima di effettuare l'import definitivo
  - Visualizzazione più chiara degli **errori di validazione Excel** direttamente nella finestra di controllo.

---

### 🛠️ Admin

- 🧩 **Nuovo sistema di regole di validazione Excel**:
  - Introdotto un **pannello per la gestione delle regole di validazione** dei file Excel.
  - Possibilità di configurare e visualizzare **le regole applicate prima dell’importazione**.

- ⚙️ **Gestione avanzata dell'import massivo**:
  - Estesa la configurazione per l’importazione di grandi volumi di dati.
  - Aggiunte rotte dedicate per **servizi di validazione Excel** e configurazione backend.
  - Migliorata la formattazione dei comandi SQL precompilati.
  - Corretta la gestione dei **flag e colonne** durante l’import massivo.
  - La **finestra di validazione Excel** è stata **ingrandita** per facilitare la consultazione.

- 🧹 Altri miglioramenti tecnici:
  - Ottimizzato il flusso di gestione e validazione dei dati importati.
  - Aggiunti ID dei pulsanti e comandi all'interno dei processi di importazione.


## 🔄 Versione 1.5.5 - 27 agosto 2025

### 🛠️ Admin

- Aggiunto tab per gestire la sequenza dei comandi visualizzati all'interno di un gruppo. La sequenza può essere cambiata tramite drag and drop per ogni gruppo ed è presenta la possibilità di filtrare gruppi e ricerca comandi
- Aggiunta maschera modale su comando SQL in tab parametri per facilitare la scrittura del codice SQL. E' presente anche un tasto di esecuzione per visualizzare il risutlato.

## 🔄 Versione 1.5.4 - 26 agosto 2025

### 🛠️ Admin

- Aggiunta gestione visibilità pulsanti per ruolo utente così da permettere di abilitare determinati pulsanti solamente a determinati utenti
- Aggiunta gestione inserimenti, modifiche, eliminazioni e duplicazione righe per ruolo così da permettere di abilitare le rispettive funzionalità solamente a determinati utenti
- Modifica logica di aggiornamento dell'applicazione da pannello admin (WIP)
- Corretto svuotamento campo prompt guida utente quando si cambia comando da pannello admin
- Aggiunta integrazione con openAI chatgpt con pulsante dedicato a cui passare il prompt per generare la guida utente da pannello admin.


## 🔄 Versione 1.5.2 - 30 luglio 2025

### 🛠️ Admin

- Sistemato errore su salvataggio comandi esistenti che non permetteva di modifica il comando SELECT
- Aggiunti tasti rapidi per aumento e diminuzione larghezza campi nel tab Colonne

## 🔄 Versione 1.5.1 – 29 luglio 2025

### 👤 Utente
- Migliorata la disposizione dei **parametri checkbox**, con layout più ordinato e leggibile.
- Aggiunta possibilità di duplicazione righe per i comandi dove è configurata la possibilità di modifica puntuale.

---

## 🔄 Versione 1.5.0 – 28 luglio 2025

### 👤 Utente
- Introdotta una pagina dedicata per **gestire accessi non autorizzati**: ora viene mostrato un messaggio chiaro quando si tenta di eseguire un comando senza permessi.
- Ora i filtri di ricerca veloce sopra la colonna costruiscono un URL, così da permettere il salvataggio di un comando con relativi filtri, che vengono eseguiti all'apertura di quel segnalibro

### 🛠️ Admin
- Aggiunto un sistema di **version tracking** che invia automaticamente la versione dell'app al backend all'avvio, per una migliore gestione delle compatibilità.
- Aggiunta la colonna `u_lastversiontimestamp` nella tabella utenti per tracciare l’ultima versione utilizzata da ogni utente.
- Migliorata la generazione automatica delle descrizioni comando (**prompt generation**) includendo pulsanti e parametri associati.
- Aggiornato il **template SQL** con il nuovo nome per le stored procedure.
- Creati test automatici per:
  - **Login** e tracciamento timestamp.
  - **Endpoint di aggiornamento versione**.
- Nei filtri ricerca veloce sopra le colonne è possibile inserire valori stringhe separati da apici e virgole per costruire filtri in OR, es. 'LPV-60','LPV-150' permette un filtro OR visualizzando entrambi i modelli. L'URL viene costruito con le || ad indicare la clausola OR. Dettagli ulteriori su documentazione admin.

---

## 🔄 Versione 1.4.7 – 22 luglio 2025

### 👤 Utente
- Implementato un **contesto di caricamento globale**: ora le operazioni che richiedono tempo mostrano un'icona animata fighissima.

---

## 🔄 Versione 1.4.6 – 22 luglio 2025

### 👤 Utente
- Corretto un errore di validazione sui **campi data opzionali** nelle modali di modifica.
- Risolto un bug che causava errori in console durante la **chiusura della modale JSON**.
- Migliorata la gestione della selezione delle righe nella tabella con pulsanti personalizzati (CUD).
- Sistemato un problema di **conversione dei valori** in operazioni `edit` per stored procedure personalizzate.

### 🛠️ Admin
- Aggiunto un **pulsante per duplicare i comandi personalizzati (CUD)** nel pannello admin.
- Rifinito il layout della **scheda "Colonne"**: spaziature ridotte, icone migliorate e gestione overflow corretta.
- Corretto il passaggio dei parametri alla stored procedure con override e binding sanitizzati.
- Sistemata l'esecuzione delle azioni su stored procedure in presenza di pulsanti custom.
- Aggiornata la logica di validazione e sanitizzazione dei parametri (es. data, tipi stringa).
- Documentazione aggiornata con istruzioni per **debug logging** nei comandi e nei flussi `execute`.

---

## 🔄 Versione 1.4.5 – 21 luglio 2025

### 👤 Utente
- Migliorato l’effetto visivo di **evidenziazione celle modificate**: ora l’animazione è più fluida.
- L’operazione di modifica in tabella restituisce ora **l'intera riga aggiornata**, utile per visualizzare subito i cambiamenti.
- Aggiunta una **descrizione nella modale di modifica dati**, per orientare meglio l’utente durante l’editing.

### 🛠️ Admin
- Risolta la creazione di procedure SQL contenenti variabili come `@modality`, evitando errori di sintassi.
- Corretto l’**allineamento tra colonne e pulsanti personalizzati (CUD)**.
- Disattivata la riallocazione automatica dell’indice colonna nei pulsanti custom.
- Sistemata la logica di **salvataggio e ordinamento delle colonne** per i pulsanti.
- Aggiunto supporto per il parametro `@ButtonPressed` nelle chiamate alle stored procedure.
- I log ora includono correttamente i **valori JSON** dei campi complessi e lo stato "after" completo della riga.
- I campi dei parametri vengono ora **sanificati** per evitare conflitti SQL o nomi invalidi.

---

## 🔄 Versione 1.4.4 – 18 luglio 2025

### 👤 Utente
- Le righe modificate nella tabella mostrano ora un’**evidenziazione visiva** immediata (highlight).
- Migliorata la gestione dei **timeout su comandi Excel**, evitando blocchi durante lunghe elaborazioni.

### 🛠️ Admin
- Introdotto un nuovo campo nel log: `lt_rowdata`, per salvare l'intera riga elaborata.
- Ripristinato il campo per **impostare il timeout di esecuzione** nei comandi.
- Aggiunto un **pannello di aggiornamento Admin** con endpoint dedicato per forzare aggiornamenti applicativi.
- Aggiunto supporto per **SSH log folder** e **filtro predefinito SSH** tramite la colonna `c_ssh_defaultfilter`.
- Estesa la documentazione per i comandi SSH e chiarita la gestione della password memorizzata.

---

## 🆕 Versione 1.4.3 – 16 luglio 2025

### 👤 Utente
- Migliorata la generazione delle guide automatiche per i comandi SQL, con testi più chiari e formattazione in Markdown.
- Risolto un errore nei campi `select` durante la ricerca, che faceva scomparire le etichette.

### 🛠️ Admin
- Aggiunto un nuovo tab **“Guida”** nel pannello admin per generare automaticamente la descrizione di un comando tramite AI (Prompt API).
- Introdotto supporto per comandi SQL su **view di altri database**, con recupero definizione oggetto.
- Corretta la gestione iniziale e visualizzazione dei valori di default nei `select`.
- Aggiornata la documentazione `DOCUMENTAZIONE_ADMIN.md` con la guida alla generazione automatica dei prompt.
- Refactor del codice per rimuovere ridondanze nei pulsanti CUD del pannello comandi.

---

## 🆕 Versione 1.4.2 – 15 luglio 2025

### 👤 Utente
- Migliorata l’interfaccia dei **filtri condizionali** (es. selezione visiva per valori e date).
- Risolti problemi di visualizzazione e ordinamento dei campi **datetime nella modale JSON**.
- Gestione più chiara delle condizioni sui parametri salvati e dei valori predefiniti.

### 🛠️ Admin
- Aggiunto campo per selezionare la **colonna associata ai pulsanti personalizzati**.
- Corretto il reset automatico dei **valori di default dei parametri** durante modifiche ai comandi.
- Migliorato il logging per il tracciamento di valori salvati e parametri timestamp.

---

## 🆕 Versione 1.4.1 – 14 luglio 2025

### 👤 Utente
- Risolti problemi di formattazione delle date nella modale JSON.
- Rimossa l’icona ⚡ (auto-exec) dai comandi SSH dove non appropriata.

### 🛠️ Admin
- Migliorata la gestione asincrona del logging in comandi **SSH Tail**.

---

## 🆕 Versione 1.4.0 – 14 luglio 2025

### 👤 Utente
- Nuova **modale di validazione Excel** con pulsante di importazione nella UI.
- Corretto il contrasto di testo dei pulsanti per migliore leggibilità.
- Aggiunta un’**icona "lampo gialla"** per i comandi auto-eseguibili (solo se previsti).
- Visualizzazione migliorata dei log SSH con altezza fissa e polling automatico.

### 🛠️ Admin
- Aggiunto supporto completo per comandi **SSH con password**, inclusa la preview della configurazione.
- Documentazione estesa per i comandi SSH e le opzioni dei pulsanti di intestazione (header).
- Nuova opzione per bloccare la configurazione di importazione Excel tramite checkbox.
- Migliorato il comportamento di **abilitazione/disabilitazione dei pulsanti di riga** in base ai dati.

---

## 🔧 Versione 1.3.8 – 11 luglio 2025

### 🖱️ Personalizzazione dei pulsanti nella tabella
- Aggiunta la possibilità di configurare **pulsanti Crea/Aggiorna/Elimina (CUD)** nella tabella dei risultati.
- Introdotta la **scelta del colore personalizzato** per i pulsanti.
- Migliorata la disposizione e l’etichettatura dei tab nel pannello Admin.

### 📋 Migliore esperienza su modali dettagliate
- **Modale RowDetail** riprogettata per migliorare la leggibilità (font più grande e layout riorganizzato).
- Migliorata la gestione degli **indici di riga** per azioni con pulsanti.
- Rafforzato il logging in caso di errori di esecuzione in intestazioni.

---

## 🧩 Versione 1.3.7 – 10 luglio 2025

### 🧪 Azioni condizionali sui dati
- I pulsanti di intestazione e riga ora possono essere **disabilitati dinamicamente** in base alla riga selezionata.
- Gestione corretta dello stato di attivazione/disattivazione durante l’esecuzione.

### 📑 Miglioramenti alla visualizzazione JSON
- Risolti problemi di layout e scrollbar nella **JsonViewerModal**.
- Aggiunta barra orizzontale e spaziatura migliorata per visualizzare righe lunghe.

---

## 🧮 Versione 1.3.6 – 9 luglio 2025

### 📊 Viewer JSON potenziato
- Aggiunto **ordinamento e paginazione** alla tabella JSON.
- Migliorata l’etichettatura delle righe con informazioni utili.
- Il campo `select default` ora si abilita correttamente con precompilazione automatica.

### 🛠️ UX e supporto parametri CUD
- Migliorata la gestione dei parametri nei comandi CUD.
- Introdotta una **modale di caricamento** durante l'esecuzione di comandi.

---

## 🧷 Versione 1.3.5 – 8 luglio 2025

### 🧰 Nuove funzionalità per Admin
- Introdotto un **generatore di stored procedure** con icona dedicata.
- Tab separati per gestire **importazione dati e comandi CUD** nel pannello Admin.
- Possibilità di **copiare con un clic** valori all'interno delle tabelle modali.

### 🖌️ Miglioramenti grafici e performance
- Applicata **formattazione condizionale** a tag e descrizioni (es. colori dinamici).
- Ottimizzata la gestione dello stile e degli eventi nei campi parametro.
- Migliorato il comportamento della cache e delle connessioni nel servizio SSH Tail.

---

## 🔒 Versione 1.3.4 – 8 luglio 2025

### 📥 Importazione Excel migliorata
- Migliorato il rilevamento automatico delle **colonne data nei file Excel**.
- Il sistema ora **proporrà automaticamente il tipo "data"** per i campi che lo sembrano.
- Migliorata la precisione nella gestione di **date e formati Excel complessi**.

### 🔐 Sicurezza e logging
- Rimossi **dati sensibili dai log** di debug per evitare esposizione accidentale in ambienti di produzione.
- Migliorati i **messaggi di errore in fase di login** in caso di problemi di connessione al database.

### 🚀 Affidabilità in produzione
- Aggiunto un **controllo automatico dei file di build** all'avvio del server per evitare errori di deploy incompleti.
- Aggiunta la variabile `DB_PORT` nel file di configurazione per usare **porte database personalizzate**.
- Verifica automatica della presenza delle **variabili d’ambiente obbligatorie** (es. database, credenziali).

### 🧪 Test e diagnostica
- Aggiunto un endpoint `/api/health` per i **controlli di stato** (es. per load balancer o monitoraggio).
- Creati test automatici per la **rotta di login**, migliorando la copertura dei test di autenticazione.

### 📦 Deployment e configurazione
- Reso più robusto lo script di deploy con **pulizia automatica** in caso di errori (`trap`).
- Documentata la configurazione **HTTPS via Nginx** per ambienti di produzione.
- Fornito un esempio commentato di `ecosystem.config.js` per configurazione di **PM2/Node.js in produzione**.

---

## ✅ Versione 1.3.3 – 8 luglio 2025

### 📥 Miglioramenti importazione da Excel
- Corretta l'importazione di **valori numerici da file Excel**, inclusi i casi con separatori localizzati (es. virgola).
- Migliorata la gestione degli **errori di validazione** durante l'importazione: ora le righe vengono aggiornate correttamente anche per i campi numerici.
- Introdotto un sistema automatico di **conversione numerica localizzata**, con test dedicati per garantire affidabilità.

### ⚙️ Esecuzione comandi e parametri
- Corretto un problema che impediva l’esecuzione di **stored procedure senza parametri**.
- Migliorata la stabilità nel passaggio tra comandi con parametri differenti.

---

## 🚀 Versione 1.3.2 – 7 luglio 2025

### 🛡️ Miglioramenti alla sicurezza e compatibilità
- Corretto un errore di autenticazione **con password in HTTPS** per comandi remoti SSH.
- L’app ora utilizza **URL relativi** per le API, rendendola più compatibile con ambienti dietro proxy o reverse proxy.

### 🔧 Affinamenti tecnici
- Corretto un errore su stored procedure dovuto a **parametri aggiuntivi non previsti**.
- Sistemata la **gestione dello stato di esecuzione** e della chiave delle righe nella tabella risultati.
- Allineamento migliorato per campi booleani nella tabella (ora **centrati correttamente**).
- Ulteriore verifica sul **caricamento dei valori predefiniti** quando si cambia comando attivo.

---

## 🛠️ Versione 1.3.2 – 4 luglio 2025

### 🔧 Correzioni e stabilità SSH
- Risolti problemi di connessione e autenticazione per comandi **SSH Tail**.
- Gestione migliorata della **chiusura delle connessioni WebSocket**.
- Aggiunta una nota per indicare che **SSH Tail richiede HTTPS**.
- Corretto un avviso nel browser relativo a campi `textarea` non inizializzati correttamente.

---

## ✨ Versione 1.3.1 – 3 luglio 2025

### 🖥️ Supporto comandi remoti via SSH
- Introdotto un nuovo tipo di comando: **SSH_TAIL**, per eseguire e visualizzare output remoti in tempo reale.
- Aggiunto supporto per:
  - **Gestione chiavi SSH** e caricamento sicuro.
  - **Configurazione specifica dei comandi SSH** nel pannello Admin.
  - **Viewer WebSocket in tempo reale** per visualizzare log o output remoto.
- Documentazione aggiornata con tutte le istruzioni su uso e configurazione.

---

## ⚙️ Versione 1.3.0 – 2 luglio 2025

### 📡 Nuove funzionalità e miglioramenti all’admin
- Supporto completo al nuovo tipo `SSH_TAIL` per esecuzioni da terminale remoto.
- Miglioramenti grafici al **pannello Admin**:
  - Campi multi-riga meglio impaginati.
  - Pulsanti di salvataggio più chiari e allineati.
  - Migliore gestione della mappatura dei dettagli.
- Introdotti nuovi strumenti:
  - **Filtri testuali multivalore** con selezione multipla.
  - **Icona per svuotare i campi** dei comandi con un clic.
  - **Funzione copia SQL** rapida.
- Ottimizzato il comportamento dei **campi select** e migliorato il layout delle **schede verticali** nella UI.

---

## 🔄 Versione 1.2.4 – 1 luglio 2025

### ⚙️ Ottimizzazioni backend e interfaccia
- Rifattorizzata l'intera struttura del backend:
  - Migliorata la gestione delle rotte e dei permessi.
  - Introdotto un **logger centralizzato (Winston)** per audit e debugging.
  - Creati helper per connessione DB, parsing stored procedure e nomi file.
- UI più fluida grazie a hook riutilizzabili per comandi e parametri.
- Risolto un errore nel caricamento dei comandi all’avvio.

---

## 📦 Versione 1.2.3 – 30 giugno 2025

### 🔐 Sicurezza e configurazioni
- Migliorata la **gestione della configurazione dei comandi** e la sicurezza in ambiente di produzione.
- Rifattorizzato il modulo `CommandService` in sottocomponenti riusabili.
- Ottimizzata la struttura del codice lato client e server per miglior manutenzione e performance.

---

## 🧪 Versione 1.2.2 – 27 giugno 2025

### 🆕 Filtri avanzati e selezioni multiple
- Introdotto un **filtro avanzato con checkbox** per selezionare più valori contemporaneamente.
- Migliorata l'esportazione dei dati filtrati dalla tabella.
- Corretta la gestione delle **select multiple** e l’allineamento dei layout tab nel pannello Admin.

---


## 🌟 Versione 1.2.1 – 26 giugno 2025

### 🔍 Miglioramenti a filtri e risultati
- Corretto un problema per cui **i filtri non venivano applicati correttamente** ai risultati mostrati.
- Verificato e migliorato il comportamento dei **filtri in finestre dettagliate** (RowDetailModal).
- Allineata correttamente la tabella quando viene applicata una clausola WHERE.

### ⚙️ Usabilità migliorata
- Aggiunto un nuovo **pulsante per eseguire il comando** direttamente dalla schermata dei parametri.
- Le **notifiche (toast)** ora sono **centrate sullo schermo**, per essere più visibili.
- La selezione del campo "chiave di destinazione" è più stabile e convalidata correttamente.
- Dopo l’importazione di un file, ora è possibile **annullare** l’operazione in modo sicuro.

### 🎨 Personalizzazione avanzata (Admin)
- Aggiunto supporto per **icone di aiuto** e **tooltip descrittivi** nel pannello Admin.
- Nuovo campo configurabile: **"chiave di destinazione"** nei dettagli dei comandi.
- Migliorata la **gestione della formattazione condizionale** (colori delle celle basati sui valori).
- Riorganizzata l’interfaccia per la configurazione dei comandi con nuove opzioni di dettaglio.

---

## 🎨 Versione 1.2.0 – 25 giugno 2025

### 🔧 Nuova funzionalità: **Formattazione Condizionale**
- Aggiunta la scheda “**Formattazione Condizionale**” per evidenziare automaticamente celle in base a regole definite (es. valori al di sopra/sotto una soglia).
- Interfaccia intuitiva per configurare le regole colore nel pannello Admin.
- Applicazione automatica degli stili anche nella vista tabellare dei risultati.

---

## 🔍 Versione 1.1.2 – 24-25 giugno 2025

### 🧩 Migliorie ai parametri e ai filtri
- I **parametri inseriti** nei comandi ora sono visualizzati in **grassetto** nel riepilogo dei filtri.
- Allineamento e leggibilità migliorata per la sezione filtri e per i **campi numerici** (allineati a destra).
- Gestione dei **valori vuoti nei menu a tendina** (select) per una UX più chiara.

### 🛠️ Ottimizzazioni tecniche
- Aggiunto un **timeout automatico** per evitare blocchi durante l’esecuzione dei comandi.
- Migliorato il comportamento in presenza di **tipi booleani** e formati numerici.

---

## 🧮 Versione 1.1.1 – 23-24 giugno 2025

Principali novità:
- Miglioramento visivo della tabella, barra scroll visibile e colonne più leggibili.
- Migliore gestione dei parametri data, ruolo utente, tag speciali e messaggi di sistema.
- Nuova gestione della posizione e layout della sezione comandi.
- Importazione Excel più affidabile.
- Refactor generale del codice, maggiore stabilità e prestazioni.


## 🚀 Versione 1.1.0 – 23 giugno 2025

### 📊 Miglioramenti alla visualizzazione dei risultati
- Maggiore leggibilità delle tabelle:
  - Corretta la gestione della **larghezza colonne** (ora impostata di default a **150px**).
  - Allineamento verticale migliorato per le **intestazioni di colonna**.
  - Corretti comportamenti errati dopo il ridimensionamento manuale delle colonne.
- Ottimizzata la **disposizione della tabella**: ora si adatta meglio allo spazio disponibile sullo schermo.
- Spostata a destra la **sezione di esecuzione dei comandi** per una disposizione più ordinata.
- Il campo **"descrizione" dei comandi** ora va a capo automaticamente se troppo lungo.
- Visualizzazione corretta per **tag speciali e campi JSON**.
- Migliorato il layout dei **filtri tabella**: ora è più compatto e leggibile.
- I comandi ora si caricano **anche se la sidebar non è ancora visibile**, migliorando la velocità percepita.

### 🗓️ Gestione più precisa di date e orari
- Le date mostrate nel **pannello Admin** sono ora convertite correttamente al fuso **GMT+1**.
- Migliorata la gestione del **formato celle data** sia in input che in visualizzazione.
- Corretta l’**importazione dei campi data da Excel**, per una maggiore affidabilità.

### ⚙️ Usabilità e input parametri
- Aggiunto un **campo solo-data** per i parametri nei comandi SQL.
- Ottimizzata l’area di **drag & drop dei parametri** per evitare comportamenti involontari.
- Gestione migliorata del pulsante **Annulla** dopo l’importazione da file.
- Le **notifiche a comparsa (toast)** ora appaiono **centrate** sullo schermo, migliorando la visibilità.

### 🔐 Pannello di amministrazione
- Visualizzazione migliorata delle **righe parametri nei comandi**.
- Ora è più chiara la visualizzazione del **ruolo utente** nella UI.
- Migliorata la struttura e gestione degli **URL dei comandi**, per una navigazione più stabile.

### 🧼 Pulizia e refactoring
- Codice snellito nella gestione:
  - della **larghezza colonne**.
  - dell’**ordinamento tabellare**.
  - delle **aggregazioni nei risultati**.
- Rimossi riferimenti a contenuti interni obsoleti (es. documentazione Lovable).
- Aggiornato il `README.md` con informazioni più recenti e pulite.

---

## 🔧 Versione 1.0.2 – 20 giugno 2025

### 📈 Ottimizzazione della tabella
- Allineamento grafico migliorato e **riordino delle celle** nella tabella dei risultati.
- Aggiunti pulsanti per:
  - **Creare una nuova riga**.
  - **Eliminare tutte le righe** nella configurazione dei comandi (solo per Admin).

### 🎨 Personalizzazione delle colonne (solo Admin)
- Nuove funzionalità per **personalizzare lo stile visivo delle colonne** (es. larghezza, stile).
- Salvataggio automatico delle larghezze impostate, per mantenere una visualizzazione coerente.

### 🧪 Miglioramenti alla stabilità generale
- Risolti problemi con:
  - **Modifica larghezza colonne**.
  - **Ordinamento delle righe**.
  - **Allineamento contenuti** in finestre modali.
- Affinamenti al pannello Admin per una gestione più efficace dei comandi configurati.

---


## 🔧 Versione 1.0.1 – 17 giugno 2025

### 🔐 Sicurezza e permessi
- Corretto un problema nel controllo dei **permessi di modifica e cancellazione**: ora solo gli utenti autorizzati possono eseguire queste azioni.

---

## 🎉 Versione 1.0.0 – 17 giugno 2025

### 🛠️ Funzionalità principali
- **Pannello di amministrazione completo** per gestire:
  - Comandi SQL preconfigurati.
  - Connessioni al database.
  - Utenti e ruoli (inclusa l’**impersonazione** per testare altri ruoli).

- **Esecuzione controllata di comandi SQL**:
  - Supporto sia per **query SELECT** che per **stored procedure**.
  - Possibilità di inserire **parametri dinamici** prima dell’esecuzione.

- **Modifica dei dati**: supportate azioni di **inserimento, modifica ed eliminazione** tramite comandi autorizzati.

- **Importazione massiva da Excel**: caricamento dati in blocco per aggiornamenti rapidi.

### 📤 Esportazione dati
- Esporta i risultati della query in diversi formati:
  - **Excel (.xlsx)**
  - **CSV**
  - **Testo (.txt)**
  - **PDF**
  - **Formato personalizzato**

### 📊 Tabella interattiva
- Tabella dei risultati con:
  - **Filtri avanzati** (stile Excel).
  - **Ordinamento per colonna**.
  - **Paginazione** automatica per grandi dataset.

### 📈 Audit e tracciamento
- **Log dettagliato** di ogni accesso ed esecuzione, utile per controlli e sicurezza.

### 📘 Supporto all’uso
- Per ogni comando SQL è disponibile una **guida utente in formato Markdown**, accessibile direttamente dall’interfaccia. Nella scheda è presente una textarea bloccata che genera un *prompt* per ChatGPT tramite l'icona **Genera Prompt** e lo copia con **Copia Prompt**.

---

## 🔄 Versione 1.5.8 – 17 settembre 2025

### 👤 Utente
- Le tabelle raggruppate aggiornano ora l'altezza della lista senza lampeggi o spazi vuoti, rendendo la consultazione più fluida anche subito dopo il caricamento.

### 🛠️ Admin
- La misurazione di `scrollHeight` viene rimandata a `requestAnimationFrame` subito dopo `resetAfterIndex(0, true)` per evitare letture pari a 0 e garantire log coerenti durante la diagnostica.
- Aggiornata la documentazione tecnica con le indicazioni su quando viene eseguito il controllo dell'altezza virtualizzata e sul perché è preferibile delegarlo al frame successivo.
## 🔄 Versione 1.5.8 – 16 settembre 2025

### 👤 Utente
- L'area per trascinare le intestazioni e i messaggi tecnici sopra la tabella sono stati nascosti, così l'interfaccia resta più semplice mentre le funzioni di raggruppamento vengono rifinite.
- Il campo "data scadenza" del link condiviso ora ha la stessa larghezza del pulsante "Copia link", rendendo più agevole inserire la data anche su schermi piccoli.

### 🛠️ Admin
- Commentato il rendering di `GroupPanel` e della sezione di debug in `DataTable.tsx`, mantenendo `syncVirtualHeights` disponibile per automazioni interne e suggerendo l'uso di `ResizeObserver`/hook sugli eventi di espansione per future riattivazioni.
- Allineato l'input di scadenza in `CommandExecutor.tsx` (classe `w-[110px]`, `h-9`) alla larghezza del pulsante `Button size="sm"`, evitando overflow del layout e mantenendo la coerenza visuale nelle viste amministrative.

## 🔄 Versione 1.5.9 – 23 settembre 2025

### 👤 Utente
- Nella finestra di importazione Excel compare il nuovo pulsante **Trasforma** (colore fucsia) che guida passo passo il flusso Importa → Trasforma → Valida → Esegui, mostrando feedback chiari quando la trasformazione o la validazione non vanno a buon fine.

### 🛠️ Admin
- Introdotto l'endpoint protetto `POST /api/commands/:commandId/transform` e il metodo `commandService.transformExcelImport` che recuperano la stored procedure configurata sul pulsante `excel-transform`, eseguendola con parametri `TableName`, `Scenario`, `UserName` e aggiornando l'anteprima dati dopo l'esito.
- Aggiornato `ExcelImportModal` con stati derivati (`canTransform`, `transformSuccess`, reset della validazione e refresh della griglia) per vincolare l'esecuzione alla sequenza Importa → Trasforma → Valida → Esegui anche in presenza di scenari RBAC complessi.

