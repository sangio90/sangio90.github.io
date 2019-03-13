---
title: "Versioning, git Github e affini (part 2)"
date: 2019-03-12T20:17:53+01:00
archives: "2019"
tags: [versioning, development, devops, best-practice]
author: Guido Sangiovanni
---

Nello scorso articolo abbiamo visto una panoramica dei problemi che il Versioning risolve, inoltre abbiamo introdotto i concetti che stanno alla base di git (il sistema di versioning più diffuso).

Ora è tempo di fare stretching e iniziare a scrivere.
Prima di cominciare una nota importante: esistono tante applicazioni "grafiche" che semplificano molto la gestione di git, io personalmente prediligo la linea di comando per due motivi:
1. Sapere cosa sto facendo mi da più sicurezza, e con la linea di comando faccio esattamente ciò che voglio.
2. Quando si verifica un caso particolare o un problema, sono già in grado di muovermi e lo gestisco meglio. 

Bene, in questa prima prova vedremo come:

0. Installare git
1. Creare una nuova repository git
2. Versionare i nostri primi file
3. Aggiornare alcuni di questi file
4. Tornare ad una versione precedente


### Installazione
Per prima cosa è necessario disporre del software "git" installato sul proprio computer, io lavoro con un Macbook quindi l'ho installato tramite **brew**, 
se l'argomento fosse di interesse scriverò un breve post anche su quello.

il comando è semplicissimo: `brew install git`

Per chi lavorasse su Windows può scaricarlo dal sito di (git)[https://git-scm.com] nella sezione Downloads.
Una volta scaricato, è sufficiente lanciare l'installer e seguire il wizard.
Durante questo wizard vi verranno fatte alcune domande per configurare l'applicazione, per ora non preoccupiamocene ed utilizziamo i valori proposti, più avanti sarà utile confrontarsi con il proprio team di sviluppo per prendere delle decisioni.

Per chi utilizza Ubuntu il comando è semplicemente `apt install git`.

### Prima Repository
Ora possiamo iniziare a lavorare, creiamo una nuova cartella che conterrà il nostro progetto.
A questo punto dobbiamo aprire un terminale nella cartella appena creata e lanciare il comando `git init`

![git init](/1gitinit.png)

Unica nota per chi usa Windows, dovrete fare click col tasto destro e aprire un "git terminal" anzichè il terminale di Windows.
Fatto. visto? non era così difficile.
In pratica cosa è successo? Il sistema operativo ha creato una cartella nascosta chiamata *.git* nella quale immagazzina dei metadati sul nostro progetto e sulle sue versioni.

### Aggiungiamo dei file
Creiamo il nostro primo file da versionare, per ora facciamo un semplice file di testo chiamato *prova.txt* e inseriamo del contenuto.
Una volta creato dovremo indicare a git che questo file deve essere considerato parte della prossima commit, questo step non è automatico:
nessun file viene considerato parte della commit successiva finchè noi non lo dichiariamo esplicitamente.

Per fare ciò digitiamo `git add prova.txt`

![git add](/2gitadd.png)

### La nostra prima commit

A questo punto siamo pronti a "committare", ovvero a comunicare a git che una nuova "versione" del nostro progetto è pronta.
È importantissimo chiarire che git ragiona per intero progetto e non per singolo file, quindi se volete "viaggiare indietro nel tempo" ricordatevi che non lo state facendo su un singolo file, ma su tutto il progetto.

`git commit -m 'prima commit'`

![git commit](/3gitcommit.png)

Il parametro -m serve per aiutare gli sviluppatori a capire che modifiche sono state fatte con questa commit, usatelo con sapienza.  

### Tornare ad una commit precedente

Per mostrarvi questa funzionalità dovremo prima modificare il nostro file prova.txt e committare nuovamente.

Aggiungiamo al file una riga, quindi salviamolo, aggiungiamolo alla prossima commit tramite git add e committiamo (con un messaggio, magari "seconda commit")

A questo punto supponiamo di voler tornare indietro nel tempo, e recuperare il file alla prima commit.

Ogni commit è identificata da un messaggio, ma soprattutto da un codice univoco simile a questo:

`6aad11e3ffc481b8d71640ed57009f60ad16e906`

Quando vogliamo spostarci fra una commit e l'altra dobbiamo riferirci a loro usando questi codici, o meglio i loro primi 8 caratteri (e.g. `6aad11e3`)

Per vedere tutte le commit e i loro codici utilizziamo il comando 

`git log`  

![git log](/4gitlog.png)

Ora scegliamo la commit a cui vogliamo tornare, prendiamo i primi 8 caratteri e lanciamo (ad esempio) il comando

`git checkout 6aad11e3`

Il progetto e tutti i suoi file saranno riportati a questa versione.
Stiamo attenti che da questo momento siamo in situazione di DETACHED HEAD. 
Per ora ricordiamoci solo di non fare modifiche mentre siamo in questo stato, partiamo sempre dall'ultima commit disponibile.

Bene, per oggi abbiamo visto come muovere i primi passi con git, per ora sempre tutto "offline".
La prossima parte ci introdurrà alla collaborazione fra più utenti e all'uso dei branch dedicati alle diverse feature di sviluppo.

