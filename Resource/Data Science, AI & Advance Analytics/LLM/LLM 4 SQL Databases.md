---
tags:
  - LLMs
  - AI
  - SideProject
source: https://arxiv.org/pdf/2311.07509.pdf
---
> **Abstract**:  Enterprise applications of ... LLMs hold promise for question answering on enterprise SQL databases. However, the extent to which LLMs can accurately respond to enterprise questions in such databases remains unclear ... the potential of Knowledge Graphs (KGs) to enhance LLM-based question answering by providing business context is not well understood. This study aims to evaluate the accuracy of LLM-powered question answering systems in the context of enterprise questions and SQL databases, while also exploring the role of knowledge graphs in improving accuracy. To achieve this, we introduce a benchmark comprising an enterprise SQL schema in the insurance domain, a range of enterprise queries encompassing reporting to metrics, and a contextual layer incorporating an ontology and mappings that define a knowledge graph. Our primary finding reveals that question answering using GPT-4, with zero-shot prompts directly on SQL databases, achieves an accuracy of 16%. Notably, this accuracy increases to 54% when questions are posed over a Knowledge Graph representation of the enterprise SQL database. Therefore, investing in Knowledge Graph provides higher accuracy for LLM powered question answering systems.

**Repository**: : https://github.com/datadotworld/cwd-benchmark-data

Issue related to standard Text-To-SQL benchmarks
1. these tipically overlook complex data schema
2. undervalue questions with business focus and missing questions related to BI, KPIs, metrics, etc.
3. missing business layer (metadata, context, transformations, ontologies, etc.)

Risk for business:
* disconnected answers -> lack of usefulness
* hallucinations and uncontrolled outcomes -> lack of trust

### Article Contribution 
1. a benchmark consisting of three elements (Enterprise SQL Schema, Enterprise Question-Answer, Context Layer)
2. Results of the benchmark, using GPT-4 and zero-shot prompting

## Setup
* DDL as a text file
* sample data for the table defined as .csv
* OWL file describing the ontology of the KG
* R2RML file describing the mappings
* Questions and reference queries

#### SQL Zero-shot Prompt
```
Given the database described by the following DDL:
INSERT SQL DDL
Write a SQL query that answers the following quesion. Do not explain the query. Return just the query, so it can be run verbatim from your response.
Here's the question: 
"INSERT QUESTION"
```

#### SPARQL Zero-shot Prompt
```
Given the OWL model described in the following TTL file:
INSERT OWL ontology
Write a SPARQL query that answer the question. The data for your query is available in a SERVICE identified by <mapped>. Do not explain the query. Return just the query, so it can be run verbatim from your response. 
"INSERT QUESTION"
```

#### SQL/SPARQL Inaccuracy
Set of pattern erros which have been observed:
* Column name hallucination (sql)
* Value Hallucinations (sql)
* Join Hallucinations (sql)
* Incorrect Path (sparql)
* Incorrect Direction (sparql)