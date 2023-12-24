---
date: 18/11/2023
tags:
  - SageMaker
  - ml
  - aws
  - timeseries
---
|Algorithm name|Channel name|Training input mode|File type|Instance class|Parallelizable|
|---|---|---|---|---|---|
|DeepAR Forecasting|train and (optionally) test|File|JSON Lines or Parquet|GPU or CPU|Yes|

### [[DeepAR]]

* algoritmo di **previsione supervisionato** per le **serie** temporali scalari (**unidimensionali**) che utilizza reti neurali ricorrenti (**RNN**).
* utile quando si hanno molte serie temporali simili tra diverse unità trasversali. Ad esempio, potrebbero esserci raggruppamenti di serie temporali per la domanda di diversi prodotti, carichi del server e richieste di pagine web. 
* DeepAR addestra un singolo modello su tutte le serie temporali, superando i metodi standard come ARIMA ed ETS quando il dataset contiene centinaia di serie temporali correlate. 
* È  possibile associare a ciascuna serie temporale di destinazione un **vettore di caratteristiche categoriali statiche e un vettore di serie temporali dinamiche**. Durante l'addestramento, il modello apprende un'approssimazione di questo processo/processi e la utilizza per prevedere l'evoluzione della serie temporale di destinazione. 
* modello DeepAR può essere condizionato o meno alle caratteristiche categoriali e dinamiche delle serie temporali. Durante l'addestramento, il modello viene valutato utilizzando metriche di accuratezza come l'errore quadratico medio (RMSE) e la perdita quantile pesata. 
* Durante l'infrazione, DeepAR accetta formati JSON e richiede campi come "instances" e "configuration" per generare le previsioni. 
* Alcune best practice:
	* addestramento su tante serie temporali quante disponibili 
	* evitare di utilizzare valori molto grandi per "prediction_length" in quanto rendono il modello più lento e meno accurato.
	* Si consiglia di iniziare con un valore per "context_length" uguale a quello utilizzato per "prediction_length". 
* È possibile addestrare DeepAR su istanze EC2 sia GPU che CPU, ma **per l'infrazione supporta solo istanze CPU**. 