Business Intelligence and, in general, data insights are nowadays a key component for strategic decision making in business and operations. 
For this reason, every year hard skills related to data analysis and data specialists are more and more important. 
Automation related to their tasks may have a great impact but nowadays the risk of wrong result is too high. 

In this note, I want to hypothize the structure of a chatter that business users or data specialists can use to ask question related to data and solve tasks.
## Type of questions

* **Data catalog** - corresponding to talking to a Data Steward. Correspond to technical and business questions related to metadata, data model, etc. The answer is a simple textual explanation
* **Key Insights and highlights** - corresponding to talking to a Data Analyst. Correspond to the extraction of a single number to answer a precise question. The answer is a number or a single value
* **Data Extraction and Aggregation** - correspond to talking to a Data Engineer or Analyst. Correspond to querying a database and providing the result as a (aggregated) table, a pivot or a list.
* **Business Intelligence (Visualization)** - correspond to talking to a Data Analyst. Correspond to producing a chart based on what kind of data is retrieved from the database. There may be two possibility:
	* (optional step) after Data Extraction
	* adding a Data Extraction step before

![[Querying Data Graph.canvas|Querying Data Graph]]