# PROGETTO "GUARDA CHE FREDDO!"

## Sommario
1. [Informazioni_generali](#informazioni_generali)
2. [Installazione](#installazione)
3. [Descrizione](#descrizione)
4. [Presentazione](#presentazione)
5. [Stato_del_progetto](#stato_del_progetto)
6. [Contributori](#contributori)
7. [Domande_frequenti](#domande_frequenti)
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


Usando i dati contenuti nei suddetti dataset, il progetto parte dall'analisi statistica di tutte le rilevazioni, crea due collection contenenti i dati senza outliers e valori nulli, fornisce una visualizzazione grafica del variare delle temperature nel tempo (per una corretta visualizzazione delle cartine geografiche interne agli ultimi due script Jupiter, scaricare i file contenuti in questo [link]( https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/110m/cultural/ne_110m_admin_0_countries.zip ) ) ed evidenzia le città in cui si sono registrate le maggiori escursioni termiche nei diversi periodi storici.

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
## Presentazione
***
Il progetto è corredato di una presentazione multimediale (per visualizzarla clicca [qui](https://prezi.com/view/3WqkhqPQo5MsAmfh32bI/)) creata tramite il software Prezi. Essa può servire per agevolarne la comprensione e per sintetizzare in pochi minuti il contenuto dei 3 script Jupiter.
***
## Stato_del_progetto
***
Il progetto è stato interamente completato e i 3 script Python sono funzionanti.
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
La decisione di basare l'analisi sui due file chiamati "GlobalLandTemperatureByMajorCity" e "GlobalLandTemperatureByCountry" è stata soppesata e valutata adeguatamente. Sono stati scartati gli altri tre files poichè quello nominato "GlobalLandTemperatureByCity" avrebbe compromesso la funzionalità del database NoSQL a causa della sua dimensione e quindi l'intera commistione di linguaggi Python e NoSQL, mentre gli altri due ("GlobalLandTemperatureByState" e "GlobalTemperature" non contengono dati utili nè per analizzare variazioni di temperatura nelle città mondiali, nè per ampliare l'analisi focalizzata sugli Stati.
2. **Perchè si è deciso di svolgere un'analisi statistica in un progetto meramente basato su linguaggi di programmazione?**
Nel momento in cui si utilizza un dataset contenente centinaia di migliaia di dati, è indispensabile svolgere un'attenta analisi sul dataset stesso onde evitare di utilizzare dati errati o di giungere a conclusioni sbagliate dettate da una carenza di dati in uno specifico dettaglio.
3. **Il grafico che mostra le temperature mondiali al variare del tempo contiene Stati sempre grigi. Qual è il motivo?**
Essenzialmente, il grafico è stato implementato per rendere più piacevole e più leggibile l'ampio dataset "GlobalLandTemperatureByCountry" a disposizione. Ci sono alcune discordanze con la realtà ma non è possibile fare altro che prenderne atto, considerando anche le dichiarazioni del creatore del dataset stesso:
    1) la temperatura dell'Alaska è stata considerata pari a quella degli altri 49 Stati che compongono gli USA
    2) per alcuni Stati (principalmente africani) non si hanno dati nei cinque file del dataset: essi risultano, sulla mappa, anneriti
    3) nel corso dei secoli, le stazioni di rilevamento della temperatura sono state spostate: ciò significa che alcune variazioni possono essere state causate da questo motivo e non da cambiamenti climatici degni di approfondimento.
***


# PROJECT "LOOK HOW COLD IT IS!"

## Table of contents
1. [General_informations](#general_informations)
2. [Installation](#installation)
3. [Description](#description)
4. [Presentation](#presentation)
5. [Project_status](#project_status)
6. [Contributors](#contributors)
7. [FAQ](#FAQ)
## General_informations
***
The project is entirely based on the analysis of two free datasets available on Kaggle website (to view the datasets, click [here](https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data)) which are a part of a larger source consisting of a total of five files.
The collection of files is composed by data that report the various temperatures recorded in continents, oceans, nations and cities of the world, from 1750 to 2013.

The source of the informations contained in these Kaggle datasets is Berkeley Earth (for more information about the organization that collected the data used, click [here](http://berkeleyearth.org/archive/about/)).

The program is written almost entirely using the Python programming language, with the exception of a part in NoSQL language. NoSQL has been used to import the dataset information into the Jupiter notebook and to perform queries necessary for deeper analysis.

As anticipated, the analysis is based on two of the five datasets contained in the link indicated above:

1) GlobalLandTemperaturesByCountry.csv
2) GlobalLandTemperatureByMajorCity.csv

The first .csv file is focused on temperature measurements in the major cities of the world; the second one, on the other hand, focuses its attention on world States.


Using the data contained in the aforementioned datasets, the project starts from the statistical analysis of all the measurements, it creates two MongoDB collections containing the data without outliers and null values and it provides a graphic display of the temperature variations over time (for a correct visualization of the geographical maps in the last 2 Jupiter scripts, download the files contained in this [link](https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/110m/cultural/ne_110m_admin_0_countries.zip)) and highlights the cities where there have been the biggest temperature excursions in different historical periods.

At the end, the program contains an algorithm created to find the trip that a hypothetical traveler should do to move from Beijing/Peking to Los Angeles, moving stage by stage to the hottest city among the three closest to him.
***

## Installation
***
The use of the 3 Jupiter scripts requires the installation of several external Python libraries.
The installation is executable on Windows, Linux and Mac.
Clearly, the essential first step is to install [Python 3.9](https://www.python.org/downloads/release/python-390/) and the Python platform [Anaconda](https://www.anaconda.com/products/individual)), required to use the Jupiter notebook app.

Once these two simple installations are completed, you will need to download a series of libraries.

Analyzing only the case of computers with Windows OS, the libraries can be installed using the built-in Windows command prompt or through the Anaconda Poweshell prompt, included in the Anaconda platform package.

Using the command prompt, you will need to run the following commands:
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
Alternatively, using the Anaconda Poweshell prompt, the commands to be executed will be as follows:
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

## Description
***
The golas of the project (consisting of 3 different Jupiter files) are:
* an overview about the changes in temperatures in the world, in different places and during different years;
* the analysis of the cities with the greatest temperature range over time;
* the construction of the route for an ipotetycal travel from Beijing/Peking to Los Angeles.

The first part of the project (inserted in the "Exploration_Data" file) starts after the simply download, from the [Kaggle](https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data) page, of the datasets which have been used for the entire project. In this first step, in order to be easily usable on Python, the .csv files that enclosed the datasets have been transformed into DataFrames, using the Pandas library. This allowed us to reach the purpose of this part: the analysis, from a statistical point of view, of data. Considering that the climatic data had been obtained with different methods (for example, the oldest temperatures reported had been calculated through the use of archaic mercury thermometers) and considering that the authors of the datasets had underlined the presence of possible anomalies, the aforementioned analysis has been essential to make the whole project more solid. To make easily understandable the various commands, it has been necessary to illustrate the various steps using boxplot and histograms that visibly show the changes made to the data through the various statistical formulas.

After eliminating null values and outliers, the two DataFrames were loaded into a server created specifically on MongoDB, a non-relational DBMS based on the NoSQL language. The generated database was thus equipped with 2 collections: one based on the GlobalLandTemperaturesByCountry.csv file and the other one on the GlobalLandTemperaturesByMajorCity.csv file. The purpose of this superstructure was to have a performing database to complete search queries directly from the program written in Python, integrating the two different programming languages and optimizing the performance of the scripts.

The second part of the project (inserted in the "Graphic_Visualization_and_Analysis" file) is based on am interesting and engaging graphical representations of temperature variations in the world, from 1750 to 2013. It has been decided to show all the temperatures available in the dataset even if, from 1750 to around 1880, there is a great lack of information and certainly less reliable data. This part ends with the analysis of the cities with the greatest temperature excursion in the different historical periods, with a suggestive graph based on a world map that shows the names and the dimension of each variation.

The third and last part of the project (inserted in the "Cold_Traveller" file) is composed by a long algorithm, which considers all the data contained in the MongoDB collection about the temperatures measured in the major cities of the world and which allows to plan a real trip. Specifically, the chosen trip starts from Beijing/Peking (China) and ends in Los Angeles (USA), respecting the following criteria:
* given the city of departure, the next stop is chosen by analyzing the 3 closest cities to the one where the traveler is;
* among the 3 closest cities, the traveller moves to the one with a relatively higher temperature.

The point of arrival of this third final part is a graph that shows, using a world map as "background", the journey that would be undertaken if the various stages prescribed by the command would be followed. For a netter comprehension, the various steps of the trip have been inserted in a dataframe and then shown in the aforementioned world map (equipped with a slider which, allowing the reader to vary the year of the travel, shows directly on the map the best route depending on the year chosen).
***
## Presentation
***
The project is equipped with a multimedia presentation (to view it click [here](https://prezi.com/view/3WqkhqPQo5MsAmfh32bI/) created using the Prezi software. It can be used to facilitate the understanding of all its parts and to summarize the content of the 3 Jupiter scripts in a few minutes.
***
## Project_status
***
The project has been fully completed and the 3 Python scripts are perfectly working.
***

## Contributors
***
[Sabrina Cenghialta](https://github.com/CenghialtaSabrina)

[Laura Romano](https://github.com/laur-py)

[Matteo Serra](https://github.com/MrTeoTZR)
***

## FAQ
***
Here is a list of doubts that could arise after a careful project analysis:
1. **There are five datasets available on Kaggle but the project analyzes only two of them. Why?**
The decision to focus the analysis on the two files called "GlobalLandTemperatureByMajorCity" and "GlobalLandTemperatureByCountry" has been weighed and evaluated appropriately. The other three files have been discarded because the one named "GlobalLandTemperatureByCity" would have compromised the functionality of the NoSQL database for its dimension and therefore the entire mixture of Python and NoSQL languages, while the other two ("GlobalLandTemperatureByState" and "GlobalTemperature") do not contain useful data nor for analyze temperature variations in cities around the world, nor to deepen the analysis focused on States.
2. **Why have you decided to complete a statistical analysis in a project based purely on programming languages?**
When a project starts using a dataset which contains hundreds of thousands of data, it is essential to perform a careful analysis on the dataset itself in order to avoid using incorrect data or coming to wrong conclusions dictated by a lack of data in a specific detail.
3. **The graph showing world temperatures over time always contains gray States. What's the reason?**
Essentially, the graph has been implemented to make the DataFrame about the "GlobalLandTemperatureByCountry" dataset more enjoyable and more readable. There are some discrepancies with reality but it is not possible to do anything to avoid them, also considering the statements of the creator of the dataset itself:
    1) Alaska's temperature was considered equal to the one of the other 49 States of the USA federation
    2) about some States (mainly African) there are no data in the five files which compose the dataset: they are, on the map, blackened
    3) over the centuries, the temperature measurement stations have been moved: this means that some variations may have been caused by this reason and not by real climate changes worthy of further studies.
***
