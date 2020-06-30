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
   
### Why use Azure Cognitive Search?
I think they are 3 key features I find it developer friendly.
1. Easy to spin up the Azure Cognitive Search based on your use case. The service comes with RestFul API and sufficient code sample/documentation to help you started.
 Since it is search as a service, it takes away to infrastructure setup time for you.
2. AI-enrichment - it comes with out-of-the-box capability to connect with their cognitive services to enrich the document (such as extract sentiment then you can search for ingested email message that are negative and deep dive into them)
3. Knowledge-store -- It is stilli in preview. it can project the enriched data back into Azure Table Storage which give you row and columns for use in Power BI or selected tool for reporting and analytics
![Knowledge Store Intro](https://docs.microsoft.com/en-us/azure/search/knowledge-store-concept-intro)
![Example of knowledge store from Azure documentation](https://docs.microsoft.com/en-us/azure/search/media/knowledge-store-view-storage-explorer/storage-explorer-tables.png)


### Demo
#### Demo Introduction
Here is a demo I build to search for Singapore Standard Occupational Classification - SSOC 2020 (What is [SSOC 2020](https://www.singstat.gov.sg/standards/standards-and-classifications/ssoc) ...? Click the link to know more)
In the demo, I take the PDF from the site, get it indexed by header, then allow users to key in their job title and search for most relevant occupation classfication to their job description and what they do
[Demo Site is here](https://adminportal20200629141308.azurewebsites.net/admin/cognitive-search)

the demo architecture is illustrated here:
![Architecture](https://adminportal20200629141308.azurewebsites.net/static/media/CogSearchAppArchitecture.3f17ad2f.JPG)

#### How it works?
We can look at the architecture from 3 main components - web application, Azure Cogntiive Search, Azure Cogntive Services and Data engineering

##### Web Application
The web app is build with React for front end, .NET Core API for backend. A bit stray away from this post topic...however, I would like to comment that React is really easy to use for building front end. Having been learning/building web app, I find myself have the shortest learning curve with React+.Net Core API, compare with Razor+MVC or Angular+MVC.
Also ,I would like to give credit to [Creative Tim](https://www.creative-tim.com/). They provide fantastic design with very easy and clean code at the back. Recommended!

##### Azure Cogntive Search
Back to our topic, I use Azure provided started code [here](https://docs.microsoft.com/en-us/samples/azure-samples/azure-search-python-samples/python-tutorial-cognitive-search/)
It is pretty straightforward to follow (and most likely get completed if you have a more complicated search index.
Beware of the cost in invoking Azure Cognitive Service, if you don't need any build-in cognitive skillset, then don't add them in to keep the cost low.

##### Azure Cognitive Services(Azure Text Analytics)
I use Azure Text Analytics to extract key phrases that users key in so that users can key in free-form as they like. I'll use the text analytics capability to extract keyword that can be used for search

##### Data Processing
Actually, data processing is the main thing here. In the demo, I would like to allow my web app to return the relevant section only rather than the entire PDF file, so I actually buiild a small data processing script to get the document split by header so that Azure Cogntiive Search can index them by header.
WOuld like to point out that Azure Cogntiive Search has build-in skillset to split the document by page or by sentences count[Link here](https://docs.microsoft.com/en-us/azure/search/cognitive-search-skill-textsplit). So it can help ease the data engineering work load and can focus their energy on other part of data requirement.


