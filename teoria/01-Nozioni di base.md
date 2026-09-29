# Nozioni di base

## Esempi di sistemi operativi

- Windows
- macOS
- Linux Ubuntu

## Cosa fa un sistema operativo?

Il sistema operativo utilizza l'hardware di un computer per fornire dei servizi all'utente.

In particolare, il sistema operativo si occupa di **gestire le risorse del computer** e di fornire un'interfaccia e dei servizi ai programmi e agli utenti.

## Come è composto un computer?

Un computer è composto principalmente da:

- una CPU;
- una memoria;
- dei moduli di input/output (I/O).

Questi componenti sono collegati tra di loro tramite il **system bus**.

La **CPU** si occupa dell'esecuzione delle computazioni e delle istruzioni.

La **memoria primaria** è volatile: in caso di spegnimento del computer, i dati contenuti al suo interno vengono persi.

I **moduli di input/output** sono numerosi e molto diversi tra loro. Alcuni esempi sono:

- memoria secondaria: hard disk, SSD, floppy disk;
- schede per la comunicazione: scheda di rete, scheda Bluetooth.

Il **system bus** si occupa di permettere la comunicazione tra le diverse parti del computer.

> **Nota:** il system bus può essere visto come un insieme di linee di comunicazione utilizzate per trasferire dati, indirizzi e segnali di controllo tra CPU, memoria e dispositivi di I/O.

## Registri della CPU

I registri della CPU possono essere suddivisi in:

- registri visibili dall'utente;
- registri di controllo e di stato;
- registri interni.

### Registri visibili dall'utente

Sono utilizzabili direttamente durante la programmazione e possono contenere:

- dati;

- indirizzi:

  - puntatori diretti;
  - puntatori a indice;
  - puntatori a segmento;
  - puntatori allo stack.

### Registri di controllo e di stato

#### Registri di controllo

- **Contatore di programma (PC, Program Counter)**
- **Registro di istruzione (IR, Instruction Register)**
- **Registro di stato del programma**

#### Registri di stato

- **Codici di condizione (flag)**

I **flag** contengono informazioni relative al risultato delle operazioni eseguite dalla CPU, come ad esempio se il risultato è zero, negativo o se si è verificato un overflow.

### Registri interni

- Registro dell'indirizzo di memoria
- Registro di memoria temporanea
- Registro dell'indirizzo di input/output
- Registro di memoria temporanea per l'input/output

> **Nota:** la presenza e la denominazione esatta di questi registri può variare a seconda dell'architettura del processore.

## Esecuzione di istruzioni

Il processore esegue continuamente un ciclo di **fetch-execute**:

1. Il processore preleva un'istruzione dalla memoria primaria.
1. Il processore esegue l'istruzione letta.

Più nel dettaglio, il processore preleva l'istruzione dalla memoria primaria e la inserisce nell'**Instruction Register (IR)**.

L'indirizzo dell'istruzione successiva viene mantenuto nel **Program Counter (PC)**, che normalmente viene incrementato dopo ogni prelievo.

In caso di **jump (salto)**, il PC viene modificato dall'istruzione stessa, indicando l'indirizzo della nuova istruzione da eseguire.

### Registro dell'istruzione

L'istruzione che viene prelevata dalla memoria viene inserita nell'**IR (Instruction Register)**.

Esistono diverse categorie di istruzioni:

- processore e memoria;
- processore e input/output;
- manipolazione dei dati;
- controllo.

> **Nota:** le istruzioni di controllo comprendono, ad esempio, salti e istruzioni utilizzate per modificare il normale flusso di esecuzione.

## Interruzioni

Le **interruzioni (interrupt)** sono eventi che richiedono l'attenzione del processore e possono temporaneamente interrompere l'esecuzione del programma corrente.

Possono essere dovute a molteplici cause, per esempio:

- **Input/output:** i dispositivi di I/O possono essere molto più lenti del processore. Un'interruzione può segnalare al processore che un'operazione di I/O è terminata, evitando che debba rimanere continuamente in attesa.
- **Programma:** ad esempio, in caso di overflow o di errori come un segmentation fault (segfault).
- **Timer:** un timer può generare periodicamente un'interruzione.
- **Fallimento hardware:** un malfunzionamento di un componente hardware può generare un'interruzione.

Durante i cicli di **fetch-execute** viene controllato anche se sono avvenute delle interruzioni.

Se viene rilevata un'interruzione, il processore sospende temporaneamente l'esecuzione corrente e passa alla gestione dell'interruzione.

> **Nota:** la gestione completa di un'interruzione comprende il salvataggio dello stato del programma corrente e il trasferimento del controllo a una specifica routine di gestione dell'interruzione.

## Multiprogrammazione

La **multiprogrammazione** permette al sistema operativo di gestire più programmi presenti in memoria, alternando l'esecuzione tra di essi.

Un singolo processore non può eseguire realmente più istruzioni contemporaneamente sullo stesso core, ma può **alternare rapidamente l'esecuzione** tra diversi programmi, dando l'impressione che vengano eseguiti contemporaneamente.

La sequenza con cui i programmi vengono eseguiti dipende, tra le altre cose, dalla loro **priorità** e dal loro stato.

Un programma può, ad esempio, trovarsi in attesa di un'operazione di **I/O**. In questo caso il processore può essere assegnato a un altro programma invece di rimanere inutilizzato.

Alla fine della gestione di un'interruzione, il controllo **potrebbe non tornare al programma che era precedentemente in esecuzione**. Il sistema operativo può infatti decidere di assegnare il processore a un altro programma.

> **Nota:** questo meccanismo è alla base dello **scheduling della CPU**, attraverso il quale il sistema operativo decide quale processo deve essere eseguito.

## Gerarchia della memoria

La memoria di un computer è organizzata secondo una **gerarchia**, in cui i diversi livelli presentano caratteristiche differenti in termini di velocità, costo e capacità.

Una possibile gerarchia, dal livello più vicino e veloce al processore a quello più lontano e lento, è:

1. **Registri della CPU**
1. **Memoria cache**
1. **Memoria primaria (RAM)**
1. **Memoria secondaria**, come SSD e hard disk
1. **Memoria offline / storage esterno**, come supporti rimovibili o sistemi di archiviazione utilizzati non continuamente

Scendendo nella gerarchia:

- **diminuisce la velocità di accesso**;
- **diminuisce il costo per bit**;
- **aumenta la capacità di memoria**;
- **diminuisce la frequenza con cui il processore accede a quel livello di memoria**.

Quindi, le memorie più vicine alla CPU sono generalmente **più veloci, più costose per bit e di capacità inferiore**, mentre quelle più lontane sono **più lente, meno costose per bit e di capacità maggiore**.

> **Nota:** la gerarchia può essere rappresentata anche come una piramide: in alto si trovano i registri e la cache, molto veloci ma piccoli; scendendo si trovano RAM e memoria secondaria, progressivamente più lente ma con capacità maggiore.

## Memoria secondaria

La **memoria secondaria** corrisponde allo **storage non volatile** utilizzato per conservare dati e programmi anche quando il computer viene spento.

Può essere considerata parte della memoria ausiliaria e comprende, ad esempio:

- hard disk (HDD);
- SSD;
- altri dispositivi di archiviazione.

È una memoria **non volatile**, quindi i dati non vengono persi quando il computer viene spento.

Viene utilizzata per memorizzare:

- file;
- programmi;
- dati dell'utente;
- sistema operativo.

## Memoria cache

Anche all'interno della memoria **inboard** esistono importanti differenze di velocità.

La CPU è molto più veloce della memoria principale (RAM). Se dovesse aspettare continuamente la RAM per ogni operazione, una parte significativa del tempo di elaborazione verrebbe sprecata in attesa.

Per ridurre questi tempi di attesa, i computer utilizzano una **memoria cache**.

La cache è una memoria:

- **piccola**;
- **molto veloce**;
- situata vicino alla CPU;
- utilizzata per conservare temporaneamente dati e istruzioni utilizzati frequentemente.

La cache sfrutta il **principio di località**, secondo il quale i programmi tendono ad accedere più volte agli stessi dati o a dati vicini tra loro.

Esistono principalmente due forme di località:

- **località temporale:** se un dato è stato utilizzato recentemente, è probabile che venga utilizzato nuovamente a breve;
- **località spaziale:** se viene utilizzato un determinato indirizzo di memoria, è probabile che vengano utilizzati anche indirizzi vicini.

Grazie a questi principi, la cache può mantenere al suo interno i dati e le istruzioni che è più probabile vengano richiesti dalla CPU, riducendo il numero di accessi alla memoria principale.

> **Nota:** nei moderni processori esistono generalmente più livelli di cache, indicati come **L1, L2, L3**. In generale, L1 è più piccola e veloce, mentre livelli successivi hanno capacità maggiore e tempi di accesso più elevati.

### Funzione di mappatura

La **funzione di mappatura** stabilisce **dove mettere nella cache** un dato che viene preso dalla memoria principale.

In pratica, quando la CPU cerca un dato:

1. controlla se il dato è già nella cache;
1. se non c'è, bisogna caricarlo dalla memoria principale;
1. la funzione di mappatura stabilisce **in quale posizione della cache può essere inserito**.

Esistono diversi tipi di mappatura:

- **Mappatura diretta:** ogni blocco della memoria può essere inserito in una specifica posizione della cache.
- **Mappatura associativa:** un blocco può essere inserito in qualsiasi posizione libera della cache.
- **Mappatura set-associativa:** la cache è divisa in gruppi (set) e ogni blocco può essere inserito in una delle posizioni appartenenti al proprio set.

> **In parole semplici:** la mappatura risponde alla domanda **"Dove metto questo dato nella cache?"**

### Algoritmo di rimpiazzamento

La cache ha una capacità limitata. Se è piena e bisogna inserire un nuovo dato, bisogna **eliminare un dato già presente**.

L'**algoritmo di rimpiazzamento** stabilisce quale dato eliminare.

Un esempio è **LRU (Least Recently Used)**: viene eliminato il dato che **non viene utilizzato da più tempo**.

> **In parole semplici:** il rimpiazzamento risponde alla domanda **"La cache è piena: quale dato tolgo per fare spazio?"**

### Politica di scrittura

Quando la CPU **modifica un dato**, bisogna decidere cosa fare con la copia presente nella cache e con quella presente nella memoria principale.

Le principali politiche sono:

- **Write-through:** quando un dato viene modificato nella cache, la modifica viene fatta **subito anche nella memoria principale**.
- **Write-back:** quando un dato viene modificato, viene modificata inizialmente solo la copia nella cache. La memoria principale viene aggiornata **successivamente**, quando il blocco viene rimosso dalla cache.

> **In parole semplici:** la politica di scrittura risponde alla domanda **"Quando modifico un dato nella cache, quando aggiorno la memoria principale?"**
