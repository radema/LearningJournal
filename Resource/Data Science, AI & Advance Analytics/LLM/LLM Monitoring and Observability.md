---
tags:
  - LLMs
  - monitoring
  - observability
  - ml
date: 28/09/2023
source: https://towardsdatascience.com/llm-monitoring-and-observability-c28121e75c2f?utm_source=pocket_saves
---
## LLM Monitoring and Observability

This article presents a practical taxonomy for monitoring and observing large language models (LLMs) in production. It is divided into three sections:

1. **Evaluating LLMs**
2. **Tracking LLMs**
3. **Monitoring LLMs**

## Evaluating LLMs

Evaluating a traditional machine learning (ML) model involves checking the accuracy of its output or predictions. This is usually measured by well-known metrics such as Accuracy, RMSE, AUC, Precision, Recall, and so forth. Evaluating LLMs is a lot more complicated. Several methods are used today by data scientists.

* **Classification and Regression Metrics**
* **Standalone text-based Metrics**
    * Perplexity
    * Reading Level
    * Non-letter Characters
    * Embedding analysis
* **Evaluation Datasets**
    * ROUGE
    * Embeddings distance metrics
    * Benchmark tests
* **Evaluator LLMs**
    * Toxicity metric
* **Human Feedback**

## Tracking LLMs

Tracking is the precursor to monitoring. The low-hanging fruit of tracking involves capturing the number of requests, response time, token usage, costs, and error rates. Standard system monitoring tools play a role here alongside the more LLM-specific options.

Deep insights are gained from capturing input prompts and output responses for future analysis. This can be challenging, especially in sophisticated LLM applications where it can be difficult to nail down the final prompt call. Practitioners will want to leverage software that helps with unpacking these complexities.

## Monitoring LLMs

While most LLMs and LLM applications undergo at least some form of evaluation, too few have implemented continuous monitoring. We’ll break down the components of monitoring to help you build a monitoring program that protects your users and brand.

* **Functional Monitoring**
    * Number of requests
    * Response time
    * Token usage
    * Costs
    * Error rates
* **Monitoring Prompts**
    * Readability
    * Toxicity
    * Embedding distances from the reference prompts
    * Adversarial attempts or malicious prompt injections
* **Monitoring Responses**
    * Relevance
    * Topic divergence
    * Sentiment
    * Prompt leakage
