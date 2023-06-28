---
title: "Migrazione a nuove versioni di SQL Server e tool a supporto"
date: 2023-06-28
layout: post
---

La politica dei rilasci di SQL Server è cambiata da quando è stato rilasciato SQL Server 2017. Ora i rilasci sono più frequenti e sono disponibili anche per le versioni precedenti. Di conseguenza anche gli aggiornamenti di SQL Server sono più frequenti e quindi è necessario avere un metodo per gestirli in modo semplice e veloce.

Se si utilizza una versione particolarmente datata di SQL Server, la migrazione sulla nuova versione può preoccupare e potrebbe portare con se diverse incognite. Per cui è opportuno essere preparati, definire una strategia e utilizzare gli strumenti giusti per semplificare il processo di migrazione.

## Documentarsi prima di tutto

Il primo passo per affrontare un aggiornamento è quello di documentarsi. Bisogna capire quali sono i prerequisiti per l'aggiornamento e quali sono le novità introdotte dalla nuova versione. In questo modo si può capire se l'aggiornamento è fattibile e quali sono i benefici che si possono ottenere.

Una parte importante nel valutare la migrazione è quella di capire quali sono i breaking changes introdotti dalla nuova versione ed in particolare eventuali funzionalità che non sono più disponibili nelle nuove versioni.
La pagina [Discontinued Database Engine functionality in SQL Server](https://learn.microsoft.com/en-us/sql/database-engine/discontinued-database-engine-functionality-in-sql-server?view=sql-server-ver16#discontinued-features-in-) elenca le funzionalità che non sono più disponibili nelle nuove versioni di SQL Server.

Altro aspetto importante è valutare i requisiti di sistema. Anche qui la documentazione ci viene in aiuto, ad es. per SQL Server 2022 è disponibile [SQL Server 2022: Hardware and software requirements](https://learn.microsoft.com/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2022?view=sql-server-ver16).

## Valutare l'impatto dell'aggiornamento

Una volta compreso quali sono i prerequisiti per l'aggiornamento, è necessario eseguire un'analisi approfondita dei sistemi da aggiornare per individuare eventuali problematiche che potrebbero determinare il fallimento stesso dell'aggiornamento.

Tali problemi devono essere risolti prima di procedere con l'aggiornamento. Per questo motivo è buona norma pianificarlo solo dopo la fase di analisi. Ci sarà così tutto il tempo di predisporre ed eseguire interventi preliminari correttivi sul sistema.

## Ma devo fare tutto da solo? I tools a supporto degli aggiornamenti

La risposta è no. Microsoft ha rilasciato una serie di tools che permettono di analizzare l'ambiente e di fornire una serie di informazioni utili per la migrazione.

Vediamo di seguito alcuni di questi tools.

### Microsoft Assessment and Planning Toolkit (MAP)

Il tool [Microsoft Assessment and Planning Toolkit (MAP)](https://www.microsoft.com/en-us/download/details.aspx?id=7826) permette di analizzare l'ambiente e di fornire una serie di informazioni utili per la migrazione.

In realtà il tool non è solo legato alle attività di migrazione, ma permette di effettuare un assessment (come intuibile dal nome del tool stesso) dei sistemi in azienda per tenere sotto controllo le installazioni e le licenze dei prodotti Microsoft. Oltre che nel caso specifico di SQL Server, analizzare nel dettaglio le caratteristiche dei database presenti in ogni sistema.

In particolare, il tool riesce a raccogliere in modo automatico tutte quelle informazioni che possono interessare nel processo di migrazione, come ad esempio:

- Versioni di SQL Server installate, comprese le versioni Express e Developer, oltre al numero di istanze per ogni server;
- L'abilitazione di CLR e relativa versione;
- Numero di database presenti in ogni istanza;
- Numero di utenti, e modalità di autenticazione (integrated security only oppure mixed mode);
- Tipo di licenza;
- Elenco dei database presenti con informazioni quali:
  - Dimensione;
  - Data di creazione e di ultimo backup;
  - Compatibility level;
  - Numero di oggetti presenti (tabelle, stored procedure, viste, etc.);
  - Filegroup e filename;
- Elenco delle utenze con i relativi privilegi.

Tutte queste informazioni sono ottenibili anche manualmente, ma un tool di raccolta automatico è sicuramente un aiuto importante.

Dal link di [download del tool](https://www.microsoft.com/en-us/download/details.aspx?id=7826) è possibile scaricare un insieme di esempi di reportistica Excel prodotta dal tool. Questi esempi possono essere utili per capire quali informazioni è possibile ottenere dal tool e come queste informazioni possono essere utilizzate per la migrazione. Di seguito un esempio di un foglio Excel generato dal tool con le informazioni raccolte per ogni database:
![Esempio di raccolta dati MAP](/assets/images/MAPExcelForDatabaseDetails.png)

> Allo stato attuale il tool sembra gestire solo fino alla versione 2019, ma dato che si sta parlando di aggiornamento da versioni precedenti, questo non è un problema.

### Microsoft Data Migration Assistant (DMA)

Il tool [Microsoft Data Migration Assistant (DMA)](https://www.microsoft.com/en-us/download/details.aspx?id=53595) permette di analizzare i databases presenti in un'istanza di SQL Server e di fornire una serie di informazioni utili per la migrazione.

A differenza di MAP il tool è focalizzato solo sulle attività di migrazione tra le versioni di SQL Server (anche verso Azure).

In particolare, dal tool è possibile gestire progetti sia per l'analisi della migrazione, sia di migrazione vera e propria.

Attraverso i progetti di analisi è possibile andare a verificare se ci sono problemi che potrebbero impedire la migrazione, come ad esempio:

- Oggetti che non sono più supportati nella nuova versione;
- Oggetti che sono stati deprecati nella nuova versione;
- Oggetti che sono stati modificati nella nuova versione;
- Oggetti che potrebbero avere problemi di performance nella nuova versione;
- Oggetti che potrebbero avere problemi di compatibilità nella nuova versione.

Mentre i progetti di migrazione vera e propria permettono di migrare uno o più databases da una versione/istanza di SQL Server ad un'altra.

### Azure Migrate

Nel caso in cui si stia valutando il porting verso Azure, uno strumento di grande interesse è  [Azure Migrate](https://azure.microsoft.com/en-us/services/azure-migrate/) che permette di analizzare i sistemi presenti in azienda e di fornire una serie di informazioni utili per la migrazione verso Azure.

Questo tool può essere utile anche per valutare la migrazione verso una nuova versione di SQL Server. In linea di massima le informazioni che è possibile ottenere sono le stesse che si possono ottenere con MAP, ma in questo caso il tool è focalizzato solo sulla migrazione verso Azure.

### Database Experimentation Assistant (DEA)

Il tool [Database Experimentation Assistant (DEA)](https://www.microsoft.com/en-us/download/details.aspx?id=54090) sebbene non specificatamente dedicato alla migrazione può avere un ruolo fondamentale per l'aggiornamento di database mission critical.

Infatti, tale tool permette di valutare le performance di un database sulla base di dati raccolti in un ambiente di test. In questo modo è possibile valutare se l'aggiornamento di un database può avere un impatto negativo sulle performance o viceversa migliorare le performance.

## Conclusioni

In questo articolo abbiamo visto come sia possibile utilizzare alcuni tools per semplificare le attività di migrazione verso nuove versioni di SQL Server.

In particolare, abbiamo visto come MAP e DMA possano essere utilizzati per analizzare l'ambiente e fornire una serie di informazioni utili per la migrazione.

Inoltre, abbiamo visto come Azure Migrate possa essere utilizzato per valutare la migrazione verso Azure, ma anche per valutare la migrazione verso una nuova versione di SQL Server.

La migrazione di un database mission critical è un'attività che richiede un'analisi approfondita e una pianificazione accurata.
Attività che devono essere alla base di ogni migrazione, ma che possono comunque essere supportate dai tools che abbiamo visto.

## Riferimenti

- [Microsoft Assessment and Planning Toolkit(MAP) - Getting Started](https://social.technet.microsoft.com/wiki/contents/articles/1640.microsoft-assessment-and-planning-map-toolkit-getting-started.aspx)
- [SQL Server Discovery using the Microsoft Assessment and Planning (MAP) toolkit - Corso MS Learn](https://learn.microsoft.com/en-us/training/modules/sql-server-discovery-using-map/)
- [Overview of Data Migration Assistant - MS Learn](https://learn.microsoft.com/en-us/sql/dma/dma-overview)
- [About Azure Migrate - MS Learn](https://learn.microsoft.com/en-us/azure/migrate/migrate-services-overview)
- [Testare e ottimizzare i database di SQL Server usando Database Experimentation Assistant (DEA) - Corso MS Learn](https://learn.microsoft.com/it-it/training/modules/test-optimize-sql-server-databases-using-dea/?ns-enrollment-type=learningpath&ns-enrollment-id=learn-sqlserver.sql-server-2017-upgrades)

## Contattaci

Se sei in procinto di valutare l'aggiornamento a SQL Server 2019 o 2022 e desideri assistenza, non esitare a contattarci [info@audris.it](mailto:info@audris.it). I nostri contatti li trovi anche sul nostro sito [audris.it](https://www.audris.it/).
