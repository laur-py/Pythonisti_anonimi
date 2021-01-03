<p align="center"> PROGETTO 4: GUARDA CHE FREDDO </p>

## Sommario
1. [Informazioni_generali](#informazioni_generali)
2. [Installazione](#installazione)
3. [Descrizione](#descrizione)
4. [Stato_del_progetto](#stato_del_progetto)
5. [Contributori](#contributori)
6. [Domande_frequenti](#domande_frequenti)
## Informazioni_generali
***
Il progetto si basa, nella sua interezza, sull'analisi di due dataset gratuiti disponibili sul sito Kaggle (per visualizzare i dataset, clicca [qui](https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data)) che sono parte di una ampissima fonte composta da un totale di cinque files. 
La collezione di file è completamente basata su dati che riportano le varie temperature registrate in continenti, oceani, nazioni e città del mondo, dal 1750 al 2013. 

La fonte delle informazioni ivi contenute è [Berkeley Earth] (per maggiori informazioni sull'organizzazione che ha raccolto i dati utilizzati, clicca [qui](http://berkeleyearth.org/archive/about/) ).

Il programma è scritto nella sua quasi totalità in linguaggio Python, ad eccezione di una parte in linguaggio NoSQL che serve in maniera esclusiva per importare nel notebook Jupiter le informazioni dei dataset.

Come anticipato, l'analisi si è basata su due dei cinque dataset contenuti nel link sopra indicato:

1) GlobalLandTemperaturesByCountry.csv
2) GlobalLandTemperatureByMajorCity.csv

Il primo file .csv, è focalizzato sulle rilevazioni di temperatura nelle maggiori città del mondo; il secondo, invece, focalizza la sua attenzione sugli Stati mondiali.


Usando i dati contenuti nei suddetti dataset, il progetto parte dall'analisi statistica di tutte le rilevazioni, fornisce una visualizzazione grafica del variare delle temperature nel tempo (per una corretta visualizzazione, scaricare i file contenuti in questo [link]( https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/110m/cultural/ne_110m_admin_0_countries.zip ) ) ed evidenzia le città in cui si sono registrate le maggiori escursioni termiche nei diversi periodi storici.

Infine, il programma contiene un algoritmo creato per trovare il viaggio che un ipotetico viaggiatore dovrebbe intraprendere per spostarsi da Pechino a Los Angeles, muovendosi tappa dopo tappa verso la città più calda fra le tre a lui più vicine.
***

## Installazione
***
L'utilizzo dello script Jupiter richiede l'installazione di numerose librerie esterne di Python. 
L'installazione è eseguibile su Windows, Linux e Mac. 
Chiaramente, il primo passo indispensabile è installare (Python 3.9)[https://www.python.org/downloads/release/python-390/] e la piattaforma di Python (Anaconda)[https://www.anaconda.com/products/individual], necessaria per utilizzare il notebook Jupiter.

Una volta eseguite queste due semplici installazioni, serviranno una serie di librerie.

Analizzando il solo caso di computer con sistema operativo Windows, le librerie possono essere installate tramite prompt dei comandi di Windows o tramite l'Anaconda Poweshell prompt della piattaforma Anaconda.

Utilizzando il prompt dei comandi, sarà necessario eseguire i seguenti comandi: 
```
- pip install pandas
- pip install datetime
- pip install pymongo
- pip install dns
- pip install geopandas
- pip install matplotlib
- pip install panel
- pip install json
- pip install pycountry
- pip install math
- pip install numpy
- pip install seaborn 
- pip install calendar
- pip install bokeh
- pip install shapely
```
Alternativamente, utilizzando l'Anaconda Poweshell prompt, i comandi da eseguire saranno i seguenti:
```
- conda install pandas
- conda install datetime
- conda install pymongo
- conda install dns
- conda install geopandas
- conda install matplotlib
- conda install panel
- conda install json
- conda install pycountry
- conda install math
- conda install numpy
- conda install seaborn 
- conda install calendar
- conda install bokeh
- conda install shapely
```
***

## Descrizione
***
Gli obiettivi del progetto sono stati:
* una vista d'insieme sui cambiamenti delle temperature nel mondo, in diversi luoghi ed in diversi anni; 
* l'analisi delle città con maggiore escursione termica nel tempo;
* la costruzione del percorso da Pechino a Los Angeles.

I file .csv che hanno permesso l'analisi sono stati dapprima scaricati dalla pagina di [Kaggle](https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data) e poi caricati in un server creato appositamente su MongoDB, un DBMS non relazionale basato sul linguaggio NoSQL. Il database generato è stato così corredato di 2 collection: una basata sul file GlobalLandTemperaturesByCountry.csv e l'altra sul file GlobalLandTemperaturesByMajorCity.csv.

Lo scopo di questa sovrastruttura è stato quello di avere un database che permettesse di eseguire query di ricerca direttamente dal programma scritto in Python, integrando armonicamente i due diversi linguaggi di programmazione.

La prima parte del progetto ha visto la messa in atto di una serie di semplici analisi atte a verificare la presenza di dati mancanti nel dataset di partenza.

Considerando che i dati provenivano da metodi di rilevazione diversi (basti considerare che le temperature più antiche riportate erano state calcolate tramite l'uso di arcaici termometri a mercurio) e considerando che gli autori dei dataset avevano sottolineato la presenza di possibili anomalie, è stato necessario anche effettuare un'analisi prettamente statistica. L'analisi, corredata di grafici boxplot ed istogrammi, ha permesso di identificare e scartare i valori chiaramente affetti da bias (outliers), i quali altrimenti avrebbero reso fallace il resto del progetto.

La seconda parte del progetto è stata basata su più interessanti e coinvolgenti rappresentazioni grafiche delle variazioni di temperatura nel mondo, dal 1900 al 2013. Si è deciso di focalizzarsi sulle sole temperature dell'ultimo secolo data la carenza di informazioni precedenti e data la maggior solidità delle rilevazioni novecentesche. Termina questa parte proprio l'analisi delle città con maggiore escursione termica nei diversi periodi storici, con un grafico suggestivo basato sulla cartina mondiale che ne mostra nomi ed ordine di grandezza della variazione.

La terza ed ultima parte del progetto è composta da un lungo algoritmo, che considera tutti i dati contenuti nella collection MongoDB relativa alle temperature misurate nelle maggiori città mondiali e che permette di pianificare un vero viaggio. Nello specifico, il viaggio scelto inizia da Pechino (Cina) e termina a Los Angeles (USA), rispettando i seguenti criteri:
* data la città di partenza, viene scelta la successiva tappa analizzando le 3 città più vicine alla città in cui ci si trova;
* fra le 3 città più vicine, ci si sposta nella città con temperatura relativamente maggiore.

Punto d'arrivo di questa terza parte finale è un grafico che dimostra anche, su una cartina mondiale, il viaggio che verrebbe intrapreso se si seguissero le varie tappe prescritte dal comando.

***
## Stato_del_progetto
***
Il progetto è stato interamente completato e lo script Python è funzionante.
***

## Contributori
***
Sabrina Cenghialta

[Laura Romano](https://github.com/laur-py)

[Matteo Serra](https://github.com/MrTeoTZR)
***

## Domande_frequenti
***
Ecco una lista dei dubbi che potrebbero sorgere ad un attento analizzatore del progetto:
1. **I dataset disponibili su Kaggle sono cinque ma il progetto ne analizza solo due. Perchè?**
La decisione di basare l'analisi sui due file chiamati "GlobalLandTemperatureByMajorCity" e "GlobalLandTemperatureByCountry" è stata soppesata e valutata adeguatamente. Sono stati scartati gli altri tre files poichè quello nominato "GlobalLandTemperatureByCity" avrebbe compromesso la funzionalità del database NoSQL e quindi l'intera commistione di linguaggi Python e NoSQL, mentre gli altri due ("GlobalLandTemperatureByState" e "GlobalTemperature" non contengono dati utili nè per analizzare variazioni di temperatura nelle città mondiali, nè per ampliare l'analisi focalizzata sugli Stati.
2. **Perchè si è deciso di svolgere un'analisi statistica in un progetto meramente basato su linguaggi di programmazione?**
Nel momento in cui si utilizza un dataset contenente centinaia di migliaia di dati, è indispensabile svolgere un'attenta analisi sul dataset stesso onde evitare di utilizzare dati errati o di giungere a conclusioni sbagliate dettate da una carenza di dati in uno specifico dettaglio.
3. **Il grafico che mostra le temperature mondiali al variare del tempo contiene Stati sempre grigi. Qual è il motivo?**
Essenzialmente, il grafico è stato implementato per rendere più piacevole e più leggibile l'ampio dataset "GlobalLandTemperatureByCountry" a disposizione. Ci sono alcune discordanze con la realtà ma non è possibile fare altro che prenderne atto, considerando anche le dichiarazioni del creatore dataset stesso:
    1) la temperatura dell'Alaska è stata considerata pari a quella degli altri 49 Stati che compongono gli USA
    2) la Groenlandia, in quanto possedimento danese, è stata rappresentata per convenzione con la stessa temperatura della madrepatria
    3) per alcuni Stati (principalmente africani) non si hanno dati nei cinque file del dataset: essi risultano, sulla mappa, anneriti
    4) nel corso dei secoli, le stazioni di rilevamento della temperatura sono state spostate: ciò significa che alcune variazioni possono essere state causate da questo motivo e non da cambiamenti climatici degni di approfondimento.






<p align="center"> PROGETTO 4: GUARDA CHE FREDDO </p>

## Table of Contents
1. [General Info](#general-info)
2. [Technologies](#technologies)
3. [Installation](#installation)
4. [Collaboration](#collaboration)
5. [FAQs](#faqs)
### General Info
***
https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data
### Screenshot
![Image text](https://www.united-internet.de/fileadmin/user_upload/Brands/Downloads/Logo_IONOS_by.jpg)
## Technologies
***
A list of technologies used within the project:
* [Technologie name](https://example.com): Version 12.3 
* [Technologie name](https://example.com): Version 2.34
* [Library name](https://example.com): Version 1234
## Installation
***
A little intro about the installation.
```
$ git clone https://example.com
$ cd ../path/to/the/file
$ npm install
$ npm start
```
Side information: To use the application in a special environment use ```lorem ipsum``` to start
## Collaboration
***
Give instructions on how to collaborate with your project.
> Maybe you want to write a quote in this part. 
> It should go over several rows?
> This is how you do it.
## FAQs
***
A list of frequently asked questions
1. **This is a question in bold**
Answer of the first question with _italic words_. 
2. __Second question in bold__ 
To answer this question we use an unordered list:
* First point
* Second Point
* Third point
3. **Third question in bold**
Answer of the third question with *italic words*.
4. **Fourth question in bold**
| Headline 1 in the tablehead | Headline 2 in the tablehead | Headline 3 in the tablehead |
|:--------------|:-------------:|--------------:|
| text-align left | text-align center | text-align right |
