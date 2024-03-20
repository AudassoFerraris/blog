---
title: "Cursori di SQL Server e alternative"
date: 2024-03-20
layout: post
---

L'uso dei cursori in SQL Server è un argomento complesso che ha implicazioni per
quanto riguarda prestazioni e scalabilità.
In linea generale, i cursori offrono un modo per iterare su un insieme di righe
e applicare logica su ciascuna riga alla volta, simile a come si farebbe in un
linguaggio di programmazione procedurale.
Tuttavia, l'uso dei cursori in SQL Server viene spesso messo in contrapposizione
all'approccio basato su set che è tipicamente più performante in operazioni di
database.

Ecco alcuni punti chiave su quando usare i cursori e quando evitarli:

## Quando usare i cursori

1. **Operazioni Row-by-Row**: In casi molto specifici, dove devi eseguire
   operazioni complesse o condizionali su ogni riga individualmente e queste
   operazioni non possono essere facilmente replicate con query basate su set.
2. **Logica Complessa**: Quando la logica da applicare a ogni riga è tropp
   complessa per essere espressa in una singola query SQL o richiede l'uso di
   condizioni o cicli che non sono facilmente gestibili in modo set-based.
3. **Mantenimento del Codice Legacy**: In sistemi legacy dove il riscrivere
   porzioni significative di logica per evitare i cursori sarebbe troppo costoso
   o rischioso dal punto di vista della stabilità del sistema.

## Quando evitare i cursori (sempre?)

1. **Prestazioni**: I cursori tendono ad essere molto più lenti rispetto alle
   operazioni set-based perché processano le righe una alla volta. Questo può
   portare a un significativo overhead di performance su grandi volumi di dati.
2. **Scalabilità**: L'uso dei cursori può ridurre la scalabilità dell'applicazione,
   poiché l'aumento del volume dei dati può portare a un aumento esponenziale
   dei tempi di esecuzione.
3. **Locking e Concorrenza**: L'uso dei cursori può portare a un maggior numero
   di lock a livello di riga o di pagina, influenzando negativamente la concorrenza
   e causando potenziali blocchi in applicazioni ad alto carico.

## Alternative ai Cursori

Per molti scenari in cui potresti considerare l'uso di cursori, esistono
alternative basate su set che possono offrire migliori prestazioni e maggiore scalabilità.
Alcune di queste alternative includono:

- **Operazioni set-based**: Usare query che lavorano con insiemi di dati interi
  piuttosto che iterare su singole righe. Questa è la metodologia che sfrutta
  appieno le potenzialità di un DBMS.
- [**CTE (Common Table Expressions)**](https://learn.microsoft.com/en-us/sql/t-sql/queries/with-common-table-expression-transact-sql?view=sql-server-ver16)
  e **funzioni di finestra** (come le [ranking functions](https://learn.microsoft.com/en-us/sql/t-sql/functions/ranking-functions-transact-sql?view=sql-server-ver16)):
  Per calcoli complessi che devono essere eseguiti su gruppi di righe.
- **Temp Tables e Table Variables**: In alcuni casi, l'uso di tabelle temporanee
  o [variabili di tipo tabella](https://learn.microsoft.com/en-us/sql/relational-databases/tables/use-table-valued-parameters-database-engine?view=sql-server-ver16)
  può aiutare a semplificare le operazioni complesse che altrimenti
  richiederebbero cursori.
- **funzioni definite dall'utente (UDF)**: Permettono di gestire logiche complesse,
  sia per quanto riguarda calcoli scalari che di data set.
  Possono essere utilizzate tramite la clausola CROSS APPLY, ma in questo caso
  possono avere implicazioni sulle performance.
- **processi esterni**: In caso di logiche particolarmente complesse è preferibile
  demandare l'elaborazione a procedure esterne scritte in linguaggi di alto livello
  (quali C#, Java, Python ecc.). Questi linguaggi rispetto a codice scritto in SQL
  permettono una maggiore manutenibilità e permettono inoltre di implementare in
  modo semplice degli unit test per la validazione delle logiche.

In conclusione, l'uso dei cursori in SQL Server dovrebbe essere limitato a casi
specifici in cui le alternative basate su set non sono praticabili o quando la
logica applicativa richiede esplicitamente iterazioni row-by-row.
Prima di decidere di utilizzare un cursore, valuta attentamente se l'operazione
può essere riscritta in un modo più efficiente utilizzando le funzionalità set-based
di SQL Server.

## Risorse aggiuntive

- [What Every DBA Ought to Know About SQL Server Cursors (and Their Alternatives) - Database Journal](https://www.databasejournal.com/ms-sql/what-every-dba-ought-to-know-about-sql-server-cursors-and-their-alternatives/)
