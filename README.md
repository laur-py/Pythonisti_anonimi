# PROGETTO "GUARDA CHE FREDDO!"

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

La fonte delle informazioni ivi contenute è Berkeley Earth (per maggiori informazioni sull'organizzazione che ha raccolto i dati utilizzati, clicca [qui](http://berkeleyearth.org/archive/about/) ).

Il programma è scritto nella sua quasi totalità in linguaggio Python, ad eccezione di una parte in linguaggio NoSQL che serve per importare nel notebook Jupiter le informazioni dei dataset e per compiere query necessarie all'analisi approfondita.

Come anticipato, l'analisi si è basata su due dei cinque dataset contenuti nel link sopra indicato:

1) GlobalLandTemperaturesByCountry.csv
2) GlobalLandTemperatureByMajorCity.csv

Il primo file .csv, è focalizzato sulle rilevazioni di temperatura nelle maggiori città del mondo; il secondo, invece, focalizza la sua attenzione sugli Stati mondiali.


Usando i dati contenuti nei suddetti dataset, il progetto parte dall'analisi statistica di tutte le rilevazioni, crea due collection contenenti i dati senza outliers e valori nulli, fornisce una visualizzazione grafica del variare delle temperature nel tempo (per una corretta visualizzazione, scaricare i file contenuti in questo [link]( https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/110m/cultural/ne_110m_admin_0_countries.zip ) ) ed evidenzia le città in cui si sono registrate le maggiori escursioni termiche nei diversi periodi storici.

Infine, il programma contiene un algoritmo creato per trovare il viaggio che un ipotetico viaggiatore dovrebbe intraprendere per spostarsi da Pechino a Los Angeles, muovendosi tappa dopo tappa verso la città più calda fra le tre a lui più vicine. 
***

## Installazione
***
L'utilizzo dei 3 scripts Jupiter richiede l'installazione di numerose librerie esterne di Python. 
L'installazione è eseguibile su Windows, Linux e Mac. 
Chiaramente, il primo passo indispensabile è installare [Python 3.9](https://www.python.org/downloads/release/python-390/) e la piattaforma di Python [Anaconda](https://www.anaconda.com/products/individual), necessaria per utilizzare il notebook Jupiter.

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
Gli obiettivi del progetto (composto da 3 diversi file Jupiter) sono stati:
* una vista d'insieme sui cambiamenti delle temperature nel mondo, in diversi luoghi ed in diversi anni; 
* l'analisi delle città con maggiore escursione termica nel tempo;
* la costruzione del percorso da Pechino a Los Angeles.

La prima parte del progetto (inserita nel file "Exploration_Data") è iniziata dopo aver semplicemente scaricato dalla pagina di [Kaggle](https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data) i dataset oggetto dell'intero progetto. In questo primo step, per poter essere agevolmente utilizzati con Python, i file .csv che racchiudevano i dataset sono stati trasformati in DataFrame utilizzando la libreria Pandas. Ciò ha permesso di giungere allo scopo di questa parte: l'analisi, dal punto di vista statistico, dei dati. Considerando che i dati climatici erano stati ottenuti con metodi di rilevazione diversi (basti considerare che le temperature più antiche riportate erano state calcolate tramite l'uso di arcaici termometri a mercurio) e considerando che gli autori dei dataset avevano sottolineato la presenza di possibili anomalie, la sudetta analisi è stata indispensabile per rendere più solido l'intero progetto. Per mantenere una facile comprensione dei vari comandi, si è ritenuto necessario illustrare i vari passaggi usando grafici boxplot ed istogrammi che mostrano visibilmente i cambiamenti effettuati sui dati tramite le varie formule statistiche. 

Dopo aver eliminato valori nulli ed outliers, i due DataFrame sono stati caricati in un server creato appositamente su MongoDB, un DBMS non relazionale basato sul linguaggio NoSQL. Il database generato è stato così corredato di 2 collection: una basata sul file GlobalLandTemperaturesByCountry.csv e l'altra sul file GlobalLandTemperaturesByMajorCity.csv. Lo scopo di questa sovrastruttura è stato quello di avere un database che permettesse di eseguire query di ricerca direttamente dal programma scritto in Python, integrando i due diversi linguaggi di programmazione ed ottimizzando le prestazioni degli script.

La seconda parte del progetto (inserita nel file "Graphic_Visualization_and_Analysis") è basata su più interessanti e coinvolgenti rappresentazioni grafiche delle variazioni di temperatura nel mondo, dal 1750 al 2013. Si è deciso di mostrare tutte le temperature disponibili nel dataset anche se, fino al 1880 circa, vi sono grosse carenze di informazioni e dati sicuramente meno attendibili. Termina questa parte proprio l'analisi delle città con maggiore escursione termica nei diversi periodi storici, con un grafico suggestivo basato su una cartina mondiale che mostra nomi ed ordine di grandezza della variazione.

La terza ed ultima parte del progetto (inserita nel file "Cold_Traveller") è composta da un lungo algoritmo, che considera tutti i dati contenuti nella collection MongoDB relativa alle temperature misurate nelle maggiori città mondiali e che permette di pianificare un vero viaggio. Nello specifico, il viaggio scelto inizia da Pechino (Cina) e termina a Los Angeles (USA), rispettando i seguenti criteri:
* data la città di partenza, viene scelta la successiva tappa analizzando le 3 città più vicine alla città in cui ci si trova;
* fra le 3 città più vicine, ci si sposta nella città con temperatura relativamente maggiore.

Punto d'arrivo di questa terza parte finale è un grafico che dimostra anche, su una cartina mondiale, il viaggio che verrebbe intrapreso se si seguissero le varie tappe prescritte dal comando. Per chiarezza, i vari step del viaggio sono inseriti in un dataframe e poi mostrati nella suddetta mappa mondiale (dotata di uno slider che, permettendo di variare l'anno del viaggio, mostra anche direttamente sulla mappa il miglior percorso a seconda dell'anno scelto).
***
## Stato_del_progetto
***
Il progetto è stato interamente completato e lo script Python è funzionante.
***

## Contributori
***
[Sabrina Cenghialta](https://github.com/CenghialtaSabrina)

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
Essenzialmente, il grafico è stato implementato per rendere più piacevole e più leggibile l'ampio dataset "GlobalLandTemperatureByCountry" a disposizione. Ci sono alcune discordanze con la realtà ma non è possibile fare altro che prenderne atto, considerando anche le dichiarazioni del creatore del dataset stesso:
    1) la temperatura dell'Alaska è stata considerata pari a quella degli altri 49 Stati che compongono gli USA
    2) per alcuni Stati (principalmente africani) non si hanno dati nei cinque file del dataset: essi risultano, sulla mappa, anneriti
    3) nel corso dei secoli, le stazioni di rilevamento della temperatura sono state spostate: ciò significa che alcune variazioni possono essere state causate da questo motivo e non da cambiamenti climatici degni di approfondimento.
