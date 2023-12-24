---
tags:
  - ml
  - foundationmodel
  - nlp
  - information-retrieval
aliases:
  - RAG
date: 27/09/2023
source: https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-foundation-models-customize-rag.html?utm_source=pocket_saves
---
**Topics:**

- **[[Embedding language models]]**
- [[Foundation models]]
- [[Natural language processing]]
- **[[Prompt augmentation]]**

![[Pasted image 20230927223132.png]]

**Note:**

Foundation models are usually trained offline on very general domain corpora, making them less effective for domain-specific tasks and agnostic to any data that is created after the model was trained. Retrieval Augmented Generation (RAG) can be used to retrieve data from outside a foundation model and augment prompts by adding the relevant retrieved data in context.

RAG model architectures compare the embeddings of user queries within the vector of the knowledge library. The original user prompt is then appended with relevant context from similar documents within the knowledge library. This augmented prompt is then sent to the foundation model.

The external data used to augment prompts can come from multiple data sources, such as document repositories, databases, or APIs. To make the formats compatible, a document collection, or knowledge library, and user-submitted queries are converted to numerical representations using embedding language models. Embedding is the process by which text is given numerical representation in a vector space.

Knowledge libraries and their relevant embeddings can be updated asynchronously.

For more information, see the following example notebooks:

- [Retrieval-Augmented Generation: Question Answering based on Custom Dataset](- [Retrieval-Augmented Generation: Question Answering based on Custom Dataset](https://sagemaker-examples.readthedocs.io/en/latest/introduction_to_amazon_algorithms/jumpstart-foundation-models/question_answering_retrieval_augmented_generation/question_answering_jumpstart_knn.html))
- [Retrieval-Augmented Generation: Question Answering based on Custom Dataset with Open-sourced LangChain Library](https://sagemaker-examples.readthedocs.io/en/latest/introduction_to_amazon_algorithms/jumpstart-foundation-models/question_answering_retrieval_augmented_generation/question_answering_langchain_jumpstart.html)


