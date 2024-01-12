---
title: "Come chiedere a ChatGPT di aiutarci nel ripasso per una verifica o una certificazione"
abstract: "Quando si sta studiando per un esame, una certificazione, o un'interrogazione un metodo che sicuramente aiuta è quello di avere qualcuno con cui confrontarsi. Una o più persone che stanno affrontando il nostro stesso percorso o che sono preparati sull'argomento che stiamo studiando. Purtroppo, questo non è sempre possibile, ma con l'avvento dell'intelligenza artificiale generativa possiamo comunque trovare una sponda sulla chat per avere un 'confronto'."
date: 2024-01-11
author: Roberto Ferraris
layout: post
keywords: intelligenza artificiale generativa, studio, ChatGPT
---

Quando si sta studiando per un esame, una certificazione, o un'interrogazione un metodo che sicuramente aiuta è quello di avere qualcuno con cui confrontarsi.
Una o più persone che stanno affrontando il nostro stesso percorso o che sono preparati sull'argomento che stiamo studiando.

Purtroppo, questo non è sempre possibile, ma con l'avvento dell'intelligenza artificiale generativa possiamo comunque trovare una sponda sulla chat per avere un "confronto".

![AI in study](/assets/images/AIStudy.jpg)
_Immagine generata con [Bing Image Creator](https://www.bing.com/images/create)_

## Il caso di studio

Proprio in questi giorni mi sto preparando per una certificazione (relativa alla piattaforma cloud Microsoft Azure), ed una volta terminato il materiale di studio ed aver sfruttato le simulazioni di esame disponibili, mi sono chiesto se fosse possibile tramite ChatGPT fare una carrellata sugli argomenti dell'esame.

Dopo un po' di prove sono riuscito a generare una richiesta (prompt) che ha fatto in modo che la piattaforma mi facesse un elenco di domande sull'argomento e mi verificasse le risposte, oltre a fornire una valutazione finale.

Questa la richiesta di partenza:  
_"Come sviluppatore software mi sto preparando per la certificazione Microsoft AZ-900 Azure Fundamentals.
Vorrei fare con il tuo aiuto una valutazione in cui tu mi proponi una domanda, io inserisco una risposta e tu mi indichi se la risposta è coerente e corretta. Dopo di che, ti chiederò di fare altre domande con la richiesta 'Altra domanda'. Alla fine,  ti chiederò 'Dammi una valutazione' e mi potrai riassumere la situazione delle competenze."_

Per quanto riguarda il risultato è stata una sessione che ha spaziato su vari concetti dell'argomento coperto dalla certificazione e mi ha permesso di fare approfondimenti specifici. Di seguito un piccolo esempio.

![Interazione con ChatGPT](/assets/images/AIStudyGPTSession.png)
_Esempio di interazione con ChatGPT per una sessione di ripasso_

C'è comunque da osservare che non può essere lo strumento definitivo perché ha comunque alcuni limiti legati alla natura stessa della piattaforma, che tento di articolare di seguito.

## Avvertenze per l'uso

Come dicevo lo strumento ha comunque dei limiti, che nel caso particolare possono riassumersi nei seguenti punti:

- La piattaforma non è aggiornata frequentemente.
- Il sistema è intrinsecamente accondiscendente.
- La base di conoscenza, benché molto grande, è limitata.
- I sistemi di IA generativa soffrono di allucinazioni.

Vediamo quindi di approfondire questi punti.

### Aggiornamenti

Come prima cosa, vediamo quale può essere il problema sull'aggiornamento di un sistema come ChatGPT.

La versione ChatGPT gratuita è attualmente aggiornata al gennaio 2022.
Questo vuol dire che la base di conoscenza è "ferma" a quella data e pertanto le informazioni più recenti sono escluse.

In relazione al tema specifico dell'esame un esempio è il sistema di autenticazione che ultimamente è stato rinominato da `Azure Active Directory` a `Azure Entra ID`. ChatGPT questo non lo può sapere; pertanto, nelle domande il termine utilizzato era quello vecchio.

### Accondiscendenza

Con l'affermazione che il sistema è intrinsecamente accondiscendente, mi riferisco alla mia esperienza personale ed al fatto che, nell'utilizzo di queste piattaforme, sembra sempre che il sistema voglia darti ragione. Pertanto, a meno di domande che richiedono risposte ben precise e brevi, è possibile che il sistema non individui alcune inesattezze.

Ad es. ho provato a rispondere a una domanda che chiedeva di spiegare le tipologie di scalabilità in Azure (le modalità con cui si possono adeguare le risorse del sistema al crescere delle richieste) andando volutamente a inserire una risposta sbagliata.

La dove i tipi di scalabilità erano "orizzontale" e "verticale", ho volutamente risposto che erano "orizzontale" ed "obliquo". Il sistema ha accettato la risposta, anche se poi nella valutazione ha utilizzato i termini corretti.

### Base di conoscenza

L'addestramento delle IA generative avviene praticamente sulla base della conoscenza disponibile in internet.  
Pertanto, alcuni argomenti potrebbero non essere "nelle corde" del sistema perché poco trattati online o perché argomento di nicchia, per cui il sistema non potrà essere di aiuto.

### Allucinazioni

I sistemi di IA generativa non sono dei sistemi di calcolo. Forniscono una risposta su base statistica partendo dalla base di conoscenza sottostante.

Pertanto, soffrono di allucinazioni dovute al fatto che danno una risposta plausibile (in base ai dati statistici) e non necessariamente corretta.

Questo è tanto più vero se si affrontano calcoli matematici. Infatti, questi sistemi non lavorano come un calcolatore vero e proprio, ma forniscono una risposta probabile, il che li rende poco adatti a essere utilizzati per verifiche in ambito matematico.

Come esperienza riporto quanto successo chiedendo di gestire una sessione di valutazione per il ruolo di studente del secondo anno di un istituto tecnico che doveva prepararsi per l'argomento radicali in algebra.

Ad un certo punto il sistema ha chiesto di spiegare come si poteva risolvere la radice di 36 scomponendo il numero. Una volta fornita la risposta il sistema mi ha corretto dicendo che la scomposizione di 36 nel prodotto tra 4 e 9 era corretta, ma la conclusione era sbagliata perché tramite scomposizione la radice quadrata risultava dalla somma della radice di 4 e di 9, per cui 2 + 3. Risultato secondo il sistema 5.

## Conclusioni: non resta che provare

Sicuramente è uno strumento che ho trovato utile per ripassare e per fare un po' di pratica, ma non può sostituire un confronto con un compagno di studi, un esperto o con un collega.

Potete partire dall'esempio che ho fornito per provare a creare una sessione di valutazione, utilizzando il seguente prompt:

"Come [ruolo] mi sto preparando per la [descrizione esame|certificazione].
Vorrei fare con il tuo aiuto una valutazione in cui tu mi proponi una domanda, io inserisco una risposta e tu mi indichi se la risposta è coerente e corretta. Dopo di che ti chiederò di fare altre domande con la richiesta 'Altra domanda'. Alla fine, ti chiederò 'Dammi una valutazione' e mi potrai riassumere la situazione delle competenze."
