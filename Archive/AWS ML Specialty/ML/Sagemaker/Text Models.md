---
tags:
  - "#aws"
  - ml
  - nlp
  - SageMaker
date: 18/11/2023
---

|Algorithm name|Channel name|Training input mode|File type|Instance class|Parallelizable|
|---|---|---|---|---|---|
|BlazingText|**train**|File or Pipe|**Text file **(one sentence per line with space-separated tokens)|**GPU (single instance only)** or CPU|No|
|LDA|train and (optionally) test|File or Pipe|recordIO-protobuf or CSV|CPU **(single instance only)**|No|
|Neural Topic Model|train and (optionally) validation, test, or both|File or Pipe|recordIO-protobuf or CSV|GPU or CPU|**Yes**|
|Object2Vec|train and (optionally) validation, test, or both|File|**JSON** Lines|GPU or CPU **(single instance only)**|No|

### [[Blazing Text]]

* Il **BlazingText** è un algoritmo di Amazon SageMaker che fornisce implementazioni altamente ottimizzate degli algoritmi **Word2vec e di classificazione** del testo. 
* L'algoritmo Word2vec mappa le parole in vettori distribuiti di alta qualità, chiamati word embedding, che catturano le relazioni semantiche tra le parole. 
* L'implementazione di BlazingText **dell'algoritmo di classificazione del testo multi-classe e multi-label** estende il classificatore di testo fastText per utilizzare l'accelerazione GPU con CUDA personalizzato. 
* Supporta l'addestramento su **CPU multi-core o su GPU** e fornisce implementazioni ottimizzate per l'addestramento su grandi set di dati. 
* Supporta la generazione di vettori significativi per **parole fuori vocabolario** rappresentando i loro vettori come la somma dei vettori di caratteri n-gram (subword). 
* L'algoritmo BlazingText supporta diverse modalità su diversi tipi di istanze, tra cui istanze con CPU singola, istanze con GPU singola e istanze con CPU multiple. Inoltre, i modelli binari (*.bin) prodotti da BlazingText possono essere consumati anche da fastText e viceversa. L'uso di modelli generati con BlazingText con fastText è supportato. Ad esempio, i binari prodotti da BlazingText possono essere utilizzati con fastText. Tuttavia, i binari sono supportati solo durante l'addestramento su CPU e su singola GPU; l'addestramento su multi-GPU non produrrà binari. 
* Per l'addestramento in **modalità cbow e skipgram**, BlazingText supporta **istanze** con CPU singola e GPU **singola**. 
* Per la **modalità** **batch_skipgram**, BlazingText supporta istanze con **CPU** singola o multiple. 
* Per la **modalità di classificazione del testo supervisionata**, si consiglia di utilizzare un'istanza **C5 se il set di dati di addestramento è inferiore a 2 GB**. 
* **Per set di dati più grandi**, si consiglia di utilizzare un'istanza con **una singola GPU**. BlazingText supporta le istanze P2, P3, G4dn e G5 per addestramento e inferenza. Per ulteriori 

### [[Latent Dirichlet Allocation]]

*  algoritmo di apprendimento **non supervisionato** che cerca di descrivere un insieme di osservazioni come una miscela di categorie distinte. L'LDA è comunemente utilizzato per **scoprire** un **numero specificato dall'utente di argomenti condivis**i dai documenti all'interno di un corpus di testo. 
* Ogni osservazione è un documento, le caratteristiche sono la presenza (o il conteggio di occorrenze) di ciascuna parola e le categorie sono gli argomenti. Poiché il metodo è non supervisionato, gli argomenti non sono specificati in anticipo e non è garantito che si allineino con il modo in cui un essere umano potrebbe naturalmente categorizzare i documenti. Gli argomenti sono appresi come una distribuzione di probabilità sulle parole che compaiono in ciascun documento. A sua volta, ciascun documento è descritto come una miscela di argomenti. Il contenuto esatto di due documenti con miscele di argomenti simili non sarà lo stesso. 

* La **scelta** tra LDA e Neural Topic Model (NTM) dipende dall'obiettivo e dalle esigenze specifiche del progetto. Recentemente, la ricerca condotta da Amazon ha dimostrato che **NTM** è promettente per ottenere un'**alta coerenza degli argomenti**, ma **LDA** addestrato con il campionamento di Gibbs collassato ottiene una **migliore perplessità**. 
* Dal punto di vista della praticità riguardo all'**hardware** e alla potenza di calcolo, l'hardware di SageMaker **NTM** è più flessibile rispetto a LDA e **può scalare meglio** perché NTM può essere eseguito su CPU e GPU e può essere parallelizzato su più istanze di GPU, mentre **LDA supporta solo l'addestramento su CPU a singola istanza.**
* Supporta sia **formati di file recordIO-wrapped-protobuf (densi e sparsi) che CSV.** 
	* Per l'infrazione, sono supportati i tipi di contenuto text/csv, application/json e application/x-recordio-protobuf. 
	* L'infrazione LDA restituisce previsioni di application/json o application/x-recordio-protobuf, che includono il vettore di miscela degli argomenti per ciascuna osservazione.
* **L'LDA attualmente supporta solo l'addestramento su CPU a singola istanza e si raccomandano istanze CPU per l'hosting/infrazione.**

### [[Neural Topic Modeling]]

* algoritmo di apprendimento **non supervisionato** utilizzato per organizzare un corpus di documenti in argomenti che contengono raggruppamenti di parole basati sulla loro distribuzione statistica. Questo modello può essere utilizzato per classificare o riassumere documenti in base agli **argomenti rilevati** o per recuperare informazioni o consigliare contenuti in base a somiglianze di argomento.
*  supporta quattro canali di dati: train, validation, test e auxiliary. I canali di dati di train, validation e test supportano sia formati di **file recordIO-wrapped-protobuf (densi e sparsi) che CSV**. Per il formato CSV, ogni riga deve essere rappresentata in modo denso con conteggi zero per le parole non presenti nel documento corrispondente e avere una dimensione pari a: (numero di record) * (dimensione del vocabolario). 
* È possibile utilizzare **per addestrare modelli su dati formattati come recordIO-wrapped-protobuf o come CSV**. 
	* canale ausiliario = file di testo con vocabolario. Fornendo il file di vocabolario, gli utenti sono in grado di vedere le prime parole per ciascuno degli argomenti stampate nel log anziché i loro ID interi. Inoltre, avere il file di vocabolario consente all'NTM di calcolare i punteggi di coerenza degli argomenti delle parole incorporate (WETC), una nuova metrica visualizzata nel log che cattura efficacemente la somiglianza tra le prime parole di ciascun argomento.

* Per l'infrazione, sono supportati i tipi di contenuto text/csv, application/json, application/jsonlines e application/x-recordio-protobuf. L'infrazione dell'NTM restituisce previsioni di application/json o application/x-recordio-protobuf, che includono il vettore di pesi dell'argomento per ciascuna osservazione.

* L'addestramento dell'NTM supporta sia tipi di istanze GPU che CPU. 

### [[Object2Vec]]

* algoritmo di **embedding neurale generale altamente personalizzabile**. 
* Può apprendere embedding densi a bassa dimensione di oggetti ad alta dimensione. Gli embedding vengono appresi in modo da preservare la semantica della relazione tra coppie di oggetti nello spazio di embedding originale. Gli embedding appresi possono essere utilizzati per calcolare efficientemente i vicini più prossimi degli oggetti e visualizzare cluster naturali di oggetti correlati in uno spazio a bassa dimensione. Possono anche essere utilizzati come feature degli oggetti corrispondenti in attività supervisionate successive, come classificazione o regressione. 
* **Object2Vec generalizza la ben nota tecnica di embedding Word2Vec** per le parole ottimizzata nell'algoritmo SageMaker BlazingText. L'algoritmo supporta diversi tipi di input, tra cui coppie di frasi-frasi, coppie di etichette-sequenza, coppie di clienti-clienti, coppie di prodotti-prodotti e coppie utente-oggetto recensione. Per trasformare i dati di input nei formati supportati, è necessario preelaborarli. 
* Object2Vec supporta nativamente **due tipi di input**: un **token discreto**, rappresentato come un elenco di un singolo ID intero, **e sequenze di token discreti**, rappresentate come un elenco di ID interi. L'algoritmo supporta semplici embedding come encoder per input token e supporta l'uso di embedding medi, reti neurali convoluzionali gerarchiche e LSTM bidirezionali multistrato come encoder per sequenze di vettori di token. 
* Le etichette di input per ciascuna coppia possono essere etichette categoriche che esprimono la relazione tra gli oggetti nella coppia o un punteggio che esprime la forza della similarità tra i due oggetti. Per le etichette categoriche utilizzate nella classificazione, l'algoritmo supporta la funzione di perdita di entropia incrociata. Per le etichette basate su punteggi utilizzate nella regressione, l'algoritmo supporta la funzione di perdita del mean squared error (MSE). 
* L'algoritmo supporta l'addestramento su istanze EC2  Per l'addestramento su CPU, si consiglia di iniziare con un'istanza ml.m5.2xlarge, mentre per l'addestramento su GPU, si consiglia di iniziare con un'istanza ml.p2.xlarge. Per l'**inferenza** con un modello Object2Vec addestrato con una rete neurale profonda,**si consiglia di utilizzare un'istanza GPU** ml.p3.2xlarge.

### [[Seq2Seq]]
* un algoritmo di apprendimento supervisionato in cui l'input è una sequenza di token (ad esempio, testo, audio) e l'output generato è un'altra sequenza di token. 
* Le applicazioni di esempio includono la **traduzione** automatica, la **sintesi** del testo e la **trascrizione** del parlato. 
* Questo algoritmo utilizza reti neurali ricorrenti (RNN) e modelli di rete neurale convoluzionale (CNN) con attenzione come architetture codificatore-decodificatore. 
* Per l'addestramento, l'algoritmo richiede tre canali: **train, validation e vocab**. 
* Per l'elaborazione, l'algoritmo supporta due formati di dati per l'inferenza: application/json e recordio-protobuf.
* L'algoritmo supporta **solo tipi di istanze GPU** e può addestrare solo **su una singola macchina (non di può parallelizzare)**. Tuttavia, supporta istanze con più GPU. 
### [[Text Classification]]

* supporta il trasferimento di apprendimento con molti modelli preaddestrati dal TensorFlow Hub. L'algoritmo supporta il trasferimento di apprendimento utilizzando modelli TensorFlow preaddestrati compatibili e ogni modello preaddestrato ha un model_id univoco. 
* È possibile utilizzare l'algoritmo Text Classification - TensorFlow come algoritmo integrato di Amazon SageMaker e supporta l'addestramento su istanze EC2 di Amazon. 
* The Text Classification - TensorFlow algorithm supports all CPU and GPU instances for training
* recommend GPU instances with more memory for training with large batch sizes. Both CPU (such as M5) and GPU (P2, P3, G4dn, or G5) instances can be used for inference.