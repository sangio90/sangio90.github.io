---
title: "Versioning, git Github e affini"
date: 2019-03-11T20:36:01+01:00
author: "Guido Sangiovanni"
tags: [versioning, development, devops, best-practice]
---

Ho deciso di cominciare questo mio blog personale con un argomento particolarmente importante, il **Versioning**.<!--more-->

Mi piacerebbe che tutte le aziende e i professionisti ne facessero uso, questo ci permetterebbe di risparmiare davvero tanto tempo e di concentrarci meglio sulla scrittura di buon codice. 

In questo post vi parlerò di git, il sistema di versioning più diffuso.

N.B. Il tema del Versioning richiede più di un post, oggi mi dedico ad un'introduzione del tema, nei prossimi giorni seguiranno articoli più tecnici con esempi pratici.

### Che cos è

Un CVS è un sistema di gestione delle versioni concorrenti: per farla breve un sistema che tiene traccia di tutte le modifiche che vengono fatte da uno o più utenti a tutti i file di un progetto.

**Quali sono i principali benefici?**
1. Posso **tornare indietro nel tempo**: se mi accorgo di aver sbagliato una modifica, posso sempre tornare ad ogni "salvataggio" fatto in precedenza.
    Per ogni salvataggio (o "commit") ho anche a disposizione la data, l'utente e lista di modifiche fatte rispetto alla versione precedente (riga per riga).
2. Posso gestire più modifiche contemporaneamente (in modo isolato).

    Supponiamo che stiamo lavorando ad un progetto, in particolare stiamo sviluppando una nuova feature.
    Riceviamo una segnalazione urgente e dobbiamo fare un bugfix proprio sullo stesso file su cui stavamo lavorando.
    Con un CVS possiamo "salvare ed archiviare lo stato attuale" (utilizzando un branch), quindi sviluppare il bugfix, e tornare a lavorare sulla nostra nuova feature.
    Inoltre è possibile integrare automaticamente il bugfix nella modifica che stavamo facendo.
3. Semplifica la collaborazione fra più utenti, se hai provato a lavorare in team senza un software di versioning sicuramente ti sarà capitato di sentire o dire "*non modificare il file xxxx.yy perchè ci sto lavorando io*".
    Questo problema fa perdere tempo al tuo lavoro e costa al cliente.
    
### Come funziona

Git tiene traccia di ogni modifica fatta al progetto in modo incrementale.
All'inizio del progetto bisognerà inizializzare una repository, quindi ogni volta che creiamo un file dobbiamo aggiungerlo alla lista dei file da "tenere d'occhio".
Quando vogliamo possiamo salvare uno "snapshot" del progetto tramite una "commit".
In qualsiasi momento possiamo muoverci fra una commit e l'altra.

È importante ricordare che tutto quello che ho scritto qui sopra non richiede nessuna connessione e nessun contatto con server esterni.
 
Se git mi serve solo per tener traccia di tutte le modifiche fatte ad un file/progetto, posso limitarmi ai comandi di base.

Vediamone alcuni:

`` git init ``
Inizializza una repository, ovvero crea una cartella nascosta ".git" che contiene tutte le informazioni che servono a git per poter tenere traccia dello stato del progetto.

`` git add filename ``
Aggiunge un file "filename" alla lista dei file da tenere controllati

`` git status ``
Ci da alcune informazioni sullo stato del progetto, ad esempio ci dice se rispetto all'ultima commit abbiamo modificato/aggiunto/rimosso qualche file.

`` git commit ``
Salva lo stato del progetto.

### Servizi di Hosting

Cosa succede se perdo la cartella del progetto?
Stando a quanto spiegato fin ora se perdo l'hard disk ho perso tutti i miei progetti.

Ecco che entrano in gioco altri attori, ovvero i servizi di hosting.
Questi provider di servizi si prendono l'onere di mantenere i nostri sorgenti, e ci permettono di scaricarli, modificarli e condividerli, ovviamente tenendo traccia di 
ogni modifica che viene fatta.
Il più famoso servizio di hosting per progetti git si chiama Github (https://github.com).

Tramite questi servizi possiamo creare dei "team" di sviluppo pubblici o privati e condividere i nostri progetti.
Uno dei tanti vantaggi offerti da questi servizi è la possibilità di far lavorare più persone contemporaneamente sugli stessi file.
**Quando entrambi gli sviluppatori hanno committato lo stesso file cosa succede?**
La maggior parte delle volte git è abbastanza intelligente da *sommare* le modifiche.

Nei casi in cui non dovesse riuscire, viene presentato un editor di test con il quale possiamo manualmente decidere cosa tenere e cosa scartare.

**Ok, ma prima mi hai detto che tutti i comandi vengono eseguiti off-line, come faccio a comunicare con i miei colleghi?**
Git ci permette di comunicare con il "Server git" (nel nostro esempio github) tramite due comandi:

`` git pull ``
Verifica se qualcuno ha modificato il progetto ed eventualmente scarica le modifiche e le applica al mio progetto

`` git push ``
Invia al server (github) le mie modifiche, in modo che gli altri utenti possano vederle, e in modo che siano "al sicuro" sui server (ad esempio) di Github. 

### Post successivi

Come indicato prima restate sintonizzati, nei prossimi giorni pubblicherò degli articoli più pratici per iniziare a fare qualcosa di concreto.
Intanto vi segnalo questo link [Hello World](https://guides.github.com/activities/hello-world/) dove trovate un esempio banalissimo di gestione progetto tramite github. 


Alla prossima!
