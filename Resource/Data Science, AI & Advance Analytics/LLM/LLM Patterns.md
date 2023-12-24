---
tags:
  - LLMs
  - patterns
  - problems
  - nlp
  - ml
date: 28/09/2023
author: Eugene Yan
source: https://eugeneyan.com/writing/llm-problems/
---
## Matching LLM Patterns to Problems

This article discusses how to match LLM patterns to various LLM problems. It is divided into three sections:

1. External vs. internal LLMs, data vs. non-data patterns
2. Matching patterns to problems
3. Customer experience paper cuts, lack of visibility on customer impact

## External vs. internal LLMs, data vs. non-data patterns

* **External LLMs** are models we don't have full control over. We can't fine-tune them, are constrained by rate/token limits, and may have concerns with sending them confidential or proprietary data.
* **Internal LLMs** are those we develop and host ourselves. While they may not have the constraints of external LLMs, we incur the cost of developing and hosting these LLMs.

* **Data patterns** are those that are tied to data, such as evals and fine-tuning.
* **Non-data patterns** are those that have more to do with infra and UI than data, such as caching, defensive UX, and guardrails.

## Matching patterns to problems

Here are some LLM problems and the patterns that help address them:

| Problem | Pattern |
|---|---|---|
| Lack of performance metrics for our specific task | Evals, collect user feedback |
| External model performing poorly | [[Retrieval Augmented Generation (RAG)]], evals |
| Internal model performing poorly | Fine-tuning, collect user feedback |
| Constraints on external models | Fine-tuning, evals, collect user feedback |
| Latency exceeds UX requirements | Caching |
| Unreliable or unusable model output | Guardrails (guidance + syntax checks), guardrails (semantic checks) |
| Customer experience paper cuts | Defensive UX (for onboarding), defensive UX (for paper cuts), collect user feedback |
| Lack of visibility on customer impact | Monitoring, collect user feedback |

**Note**: user feedback collection has been cited several times. 
## Conclusion

Matching the right LLM pattern to the right problem is essential for success. By understanding the different patterns available and the problems they can address, you can make sure that your LLM product or feature is meeting the needs of your users.