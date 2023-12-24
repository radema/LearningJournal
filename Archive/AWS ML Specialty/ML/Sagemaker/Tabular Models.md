---
date: 12/11/2023
tags:
  - aws
  - SageMaker
  - ml
---
|Algorithm name|Channel name|Training input mode|File type|Instance class|Parallelizable|
|---|---|---|---|---|---|
|AutoGluon-Tabular|training and (optionally) validation|File|CSV|CPU or GPU (single instance only)|**No**|
|CatBoost|training and (optionally) validation|File|CSV|CPU (single instance only)|**No**|
|Factorization Machines|train and (optionally) test|File or Pipe|recordIO-protobuf|CPU (GPU for dense data)|Yes|
|K-Nearest-Neighbors (k-NN)|train and (optionally) test|File or Pipe|recordIO-protobuf or CSV|CPU or GPU (single GPU device on one or more instances)|Yes|
|LightGBM|training and (optionally) validation|File|CSV|**CPU (single instance only)**|**No**|
|Linear Learner|train and (optionally) validation, test, or both|File or Pipe|recordIO-protobuf or CSV|CPU or GPU|Yes|
|TabTransformer|training and (optionally) validation|File|CSV|CPU or GPU (single instance only)|**No**|
|XGBoost (0.90-1, 0.90-2, 1.0-1, 1.2-1, 1.2-21)|train and (optionally) validation|File or Pipe|CSV, LibSVM, or Parquet|CPU (or GPU for 1.2-1)|Yes|

### [[AutoGluon-Tabular]] 
* è un algoritmo integrato in Amazon [[SageMaker]] che può essere utilizzato per l'addestramento di modelli di machine learning su dati tabulari. È possibile utilizzare l'algoritmo come un contenitore di addestramento predefinito, senza dover sostituire lo script di addestramento. 
* L'algoritmo supporta l'addestramento su dati **CSV** e richiede che la variabile target sia nella prima colonna del file CSV. 
* È possibile fornire i dati di addestramento e di convalida tramite due percorsi S3 separati o tramite un singolo percorso S3 per il canale di addestramento.
* Inoltre, è possibile specificare le caratteristiche categoriche dei dati di addestramento tramite un file JSON. 
* SageMaker AutoGluon-Tabular supporta l'**addestramento su istanze CPU e GPU singole**, ma non supporta l'addestramento su più GPU. SageMaker AutoGluon-Tabular utilizza il modulo autogluon.tabular.TabularPredictor per serializzare o deserializzare il modello, che può essere utilizzato per salvare o caricare il modello. È possibile utilizzare un modello addestrato con SageMaker AutoGluon-Tabular con il framework AutoGluon.
* Riconosce automaticamente il tipo di dati in ogni colonna per un preprocessing robusto dei dati, inclusa la gestione speciale dei campi di testo.  
* I modelli sono impilati in più strati e addestrati in modo che i dati grezzi possano essere tradotti in previsioni di alta qualità entro un determinato vincolo di tempo. Questo processo mitiga l'overfitting suddividendo i dati in vari modi con un attento monitoraggio degli esempi fuori dal fold. 
* AutoGluon-Tabular può essere utilizzato per problemi di regressione, classificazione (binaria e multiclasse) e ranking. 
### [[CatBoost]] 
* è un algoritmo di boosting al gradiente che introduce due tecniche innovative per il trattamento di **feature categoriche** e per la gestione di un particolare tipo di perdita di informazione presente in tutti gli algoritmi di boosting al gradiente. 
* Il documento fornisce anche informazioni sulla formattazione dei dati di input per il modello CatBoost e sulle raccomandazioni per la scelta dell'istanza EC2 per l'addestramento del modello. 
* Supporta **CSV** per il training e l'inference. Per il training, i dati devono essere in formato text/csv e il target variable deve essere nella prima colonna. 
* CatBoost attualmente utilizza solo **CPU**. Si raccomanda di utilizzare un'istanza di tipo **M5**, in quanto CatBoost è un algoritmo **memory-bound**. Inoltre, è necessario disporre di memoria sufficiente per contenere l'intero dataset di training. 


# [[Factorization Machines]] 
* è un algoritmo di apprendimento supervisionato che può essere utilizzato per compiti di classificazione e regressione.
* È un'estensione di un modello lineare progettato per catturare le interazioni tra le caratteristiche all'interno di **set di dati sparsi ad alta dimensionalità**. 
* L'implementazione di [[Amazon SageMaker]] dell'algoritmo Factorization Machines considera solo le interazioni a coppie tra le caratteristiche. L'algoritmo può essere eseguito in modalità di classificazione binaria o di regressione.
* In modalità di **regressione**, il set di dati di test viene valutato utilizzando l'errore quadratico medio (**RMSE**). In modalità di **classificazione** binaria, il set di dati di test viene valutato utilizzando l'entropia incrociata binaria (**log loss**), l'**accuratezza** (a soglia = 0,5) e il punteggio **F1** (a soglia = 0,5).
* Per l'**addestramento**, l'algoritmo Factorization Machines supporta **solo** il formato **recordIO-protobuf con tensori Float32**. 
* Per l'**inference**, l'algoritmo supporta i formati **application/json e x-recordio-protobuf**. 
* Si **consiglia** di utilizzare istanze **CPU** per l'addestramento e l'infrazione con dati sparsi e densi. In alcune circostanze, l'addestramento con una o più GPU su dati densi potrebbe fornire alcuni vantaggi. L'addestramento con **GPU** è disponibile **solo su dati densi**. L'algoritmo Factorization Machines **supporta** le istanze **P2, P3, G4dn e G5** per l'addestramento e l'infrazione.

### [[K-Nearest Neighbors]]
* L'Algoritmo di Amazon SageMaker è un algoritmo basato su un indice che utilizza un metodo non parametrico per la classificazione o la regressione. 
* Per i problemi di classificazione, l'algoritmo interroga i k punti più vicini al punto di campionamento e restituisce l'**etichetta** **più** frequentemente **utilizzata** della loro classe come etichetta prevista. 
* Per i problemi di **regressione**, l'algoritmo interroga i k punti più vicini al punto di campionamento e restituisce la **media** dei loro valori di caratteristica come valore previsto. 
* L'addestramento con l'algoritmo k-NN ha **tre fasi: campionamento, riduzione della dimensione e costruzione dell'indice**. L'obiettivo principale dell'addestramento di k-NN è costruire l'indice. L'indice consente ricerche efficienti delle distanze tra i punti il cui valore o le cui etichette di classe non sono ancora state determinate e i k punti più vicini da utilizzare per l'infrazione. 
* Il K-Nearest Neighbors (k-NN) Algorithm di Amazon SageMaker supporta i canali di dati di addestramento e test. Per i dati di addestramento, si utilizza un canale di addestramento per i dati che si desidera campionare e costruire nell'indice k-NN. Si utilizza un canale di test per emettere punteggi nei file di registro. 
* Per i dati di input, k-NN supporta i formati di dati **text/csv e application/x-recordio-protobuf**. Per i dati di output, k-NN supporta i formati di dati application/json e application/x-recordio-protobuf. 
* Si consiglia di addestrare su un'istanza **CPU** (come ml.m5.2xlarge) o su un'istanza **GPU**. L'algoritmo k-NN **supporta** le famiglie di istanze **P2, P3, G4dn e G5 GPU** per l'addestramento e l'infrazione.

###  [[LightGBM]]
- LightGBM è un algoritmo integrato in Amazon SageMaker che può essere utilizzato per il training di modelli di machine learning.
- È possibile utilizzare LightGBM con il SageMaker Python SDK o con l'interfaccia utente di SageMaker Studio.
- L'algoritmo LightGBM funziona con dati tabulari in formato **CSV**, con la variabile target nella prima colonna e le feature nelle colonne rimanenti.
- È possibile fornire i dati di training e di validazione tramite due percorsi S3 separati o tramite un singolo percorso S3 per il canale di training.
- LightGBM **supporta il training distribuito** su più istanze EC2.


### [[Linear Learner]] 
* è un algoritmo di apprendimento supervisionato utilizzato per risolvere problemi di classificazione o regressione.
- Per i problemi di classificazione binaria, l'etichetta deve essere 0 o 1, mentre per i problemi di classificazione multiclasse, le etichette devono essere da 0 a num_classes - 1. Per i problemi di regressione, l'etichetta è un numero reale.
- L'algoritmo apprende una funzione lineare, o per i problemi di classificazione, una funzione di soglia lineare, e mappa un vettore x a un'approssimazione dell'etichetta y.
- L'algoritmo fornisce una soluzione per entrambi i problemi di classificazione e regressione e consente di esplorare diversi obiettivi di formazione e scegliere la migliore soluzione da un set di validazione.
- L'algoritmo richiede una matrice di dati, con le righe che rappresentano le osservazioni e le colonne che rappresentano le dimensioni delle caratteristiche. Richiede anche una colonna aggiuntiva che contiene le etichette che corrispondono ai punti dati.
- L'algoritmo supporta **sia istanze CPU che GPU** per la formazione e l'elaborazione delle previsioni.
* supporta **CSV** e **application/x-recordio-protobuf**, sono supportati solo i tensori Float32.  È possibile utilizzare la modalità File o Pipe per addestrare i modelli di apprendimento lineare sui dati formattati come recordIO-wrapped-protobuf o CSV. 
* Per l'elaborazione, il Linear Learner Algorithm supporta i formati application/json, application/x-recordio-protobuf e text/csv. 

### [[TabTransformer]]
* It is a novel deep tabular data modeling architecture for supervised learning. The TabTransformer architecture is built on **self-attention-based Transformers**.
* The Transformer layers transform the **embeddings of categorical features** **into robust contextual embeddings** to achieve higher prediction accuracy. Furthermore, the contextual embeddings learned from TabTransformer are **highly robust against both missing and noisy data features**, and provide better **interpretability**.
* The SageMaker implementation of TabTransformer **supports CSV** for training and inference
* SageMaker TabTransformer supports **single-instance CPU and single-instance GPU training**. Despite higher per-instance costs, **GPUs** train more quickly, making them **more cost effective**. To take advantage of GPU training, specify the instance type as one of the GPU instances (for example, P3). SageMaker TabTransformer currently **does not support multi-GPU training**.

### [[XGBoost]]
* is a popular and efficient open-source implementation of the gradient boosted trees algorithm. You can use XGBoost for regression, classification (binary and multiclass), and ranking problems.
* You can use the new release of the XGBoost algorithm either as a Amazon SageMaker built-in algorithm or as a framework to run training scripts in your local environments.
* This implementation has a smaller memory footprint, better logging, improved hyperparameter validation, and an expanded set of metrics than the original versions. It provides an XGBoost `estimator` that executes a training script in a managed XGBoost environment. The current release of **SageMaker XGBoost is based on the original XGBoost versions 1.0, 1.2, 1.3, 1.5, and 1.7.**
* Due to required compute capacity, version 1.7-1 of SageMaker XGBoost is not compatible with GPU instances from the P2 instance family for training or inference.
* The SageMaker implementation of XGBoost supports the following data formats for training and inference: **text/libsvm , text/csv , application/x-parquet, application/x-recordio-protobuf** 
* SageMaker XGBoost supports CPU and GPU training and inference. Instance recommendations depend on training and inference needs, as well as the version of the XGBoost algorithm. GPU training is cost effective