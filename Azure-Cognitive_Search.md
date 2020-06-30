## Azure Cognitive Search

### Introduction
Azure Cogntiive Search provide search engine capability for unstructured, semi-structured (like document with structured header), or structure data. 
After you have index the data based on the search behaviour your need, you can send a search query to retrieve the relevant information you need


### What can it be used for?
1. The most obvious one would be use it to provide search capbility to your document database. Image you have thousands of PDF, ppt, Words , Excel sit in your shared file system.
You can get them indexed and then provide a web UI for user to search for relevant documents, which is common request to different helpdesk team

2. Search engine capability to your web application

3. Reporting and Analytics - 
   Here is the great article talk about using Elastic Search for reporting and analytics. (similar product to Azure Cognitive Search..but they are different and I'll explain.)
   [Using Elasticsearch for Reporting & Analytics](https://medium.com/engineering-tyroo/using-elasticsearch-for-reporting-analytics-3bb1d7c84c19#:~:text=Our%20Implementation%20of%20Elasticsearch%20for%20Reporting%20and%20Analytics&text=Elasticsearch%20is%20a%20search%20engine,and%20schema%2Dfree%20JSON%20documents.)
   
### Why use Azure Cognitive Search instead of other competing product?
I think they are 3 key features I find it developer friendly 
1. Easy to spin up the Azure Cognitive Search based on your use case. The service comes with RestFul API and sufficient code sample/documentation to help you started.
 Since it is search as a service, it takes away to infrastructure setup time for you.
2. AI-enrichment - it comes with out-of-the-box capability to connect with their cognitive services to enrich the document (such as extract sentiment then you can search for ingested email message that are negative and deep dive into them)
3. Knowledge-store -- It is stilli in preview. it can project the enriched data back into Azure Table Storage which give you row and columns for use in Power BI or selected tool for reporting and analytics
![Knowledge Store Intro](https://docs.microsoft.com/en-us/azure/search/knowledge-store-concept-intro)
![Example of knowledge store from Azure documentation](https://docs.microsoft.com/en-us/azure/search/media/knowledge-store-view-storage-explorer/storage-explorer-tables.png)


### Demo
https://adminportal20200629141308.azurewebsites.net/admin/cognitive-search
