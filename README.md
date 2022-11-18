# Tags on Trends

*StuckOverflow : Berkay Doner, Elif Sema Balcioglu, Iman Najwa Binti Masrun, Germain Vu*

## Abstract 
  
Social media posts often reflect popular concepts in the world, which can represent themselves as hashtags or tags. Using the [YouNiverse](https://zenodo.org/record/4650046#.Y3gE2nbMJPY) dataset, we will examine the characteristics of "trending" tags on YouTube, a platform where content creation is relatively more effortful. We want to examine the evolution of the use of trending tags and whether events in the world can influence the emergence and decline of tags. We also want to analyze if trending tags interact more with other tags with the help of graph networks. This analysis may also reveal cases of misuse. While some people use irrelevant trending hashtags to increase engagement for their posts, it causes a nuisance for other users who are looking for up-to-date information and news. Twitter is a platform facing this problem, due to its rapid nature in spreading information. In this project, we investigate whether the YouTube community is facing the same issue.

## Research Question
This project aims to investigate the following research questions:

* How do tags evolve and die? When do they start to appear as popular tags, do these coincide with the emergence of real-life events? 
* How do clusters of tags that are used together behave temporally? Do trending tags get more important in these clusters during their popularity?
* Do people misuse video tags on unrelated video categories to exploit trending topics?   

## Methods

### Dataset
#### Storage

We use Google Drive and Google Colab Pro for our analysis since they allow easy collaboration. Given the large size of the dataset, it is unfeasible to read the whole data. To overcome this problem, we read the data in chunks and created separate datasets for each category and each timeframe. In this analysis, we consider monthly periods.

#### Pre-processing

Given we deal with textual data, our pre-processing related to tags is removing punctuations and changing letters to lowercase. There are videos without categories, and they are eliminated. Also if a video has no tags, naturally it is not included in the analysis. We also create dictionaries for each timeframe-category pair containing tag pairs used together as keys and their frequency as values.

From the YouNiverse dataset, we use the [Video Metadata Dataset](https://github.com/epfl-dlab/YouNiverse#video-metadata). Only features we are interested are "categories", "upload_date" and "tags".  

### Tag Graph Analysis

Throughout our analysis, we will use an undirected graph network that consists of tags as nodes. We will increase the edge weight between nodes when they are used together in a video.  
We will create a series of graphs for each category and period and analyze the evolution of the connections and emergence of nodes.

#### Tag Clustering

Since tags are entered by users, the use of natural language increases the complexity of the graph analysis as the options are endless for a topic and different people can come up with various similar tags. For example, while one user adds the tag "olympics", others may add "olympic games". Handling these separately increases the size of the graph extremely. To overcome this issue, we will cluster similar tags and use them as a single node. We plan to explore two options, 
using pre-trained NLP networks such as BERT to calculate word embeddings whose similarities will be used for clustering 
using co-occurring frequencies of tags to uncover clusters. 
We will analyze the performance of these two approaches and decide on the best approach.

#### Tag Popularity Analysis

In alignment with our initial research question, we will analyze the usage of tags in terms of the number of videos containing the tag. The specific behavior will be analyzed to see the period a tag stays popular, and if this timeframe is related to the importance of the tag. 

During our initial analysis, as a case study, we focused on the "Sports" category and "Olympics" as the trending topic. 
As we analyzed popular tags using [word clouds](https://en.wikipedia.org/wiki/Tag_cloud) at each timeframe, we observed increased usage during Olympic times, which ended after a while. 


<table width="100%">
  <tr>
    <th>June 2012</th>
    <th>July 2012</th>
    <th>August 2012</th>
    <th>September 2012</th>
  </tr>
  <tr>
  <td width="25%">
      <img  src="https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/june2012.png">
   </td>
  <td width="25%">
      <img  src="https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/july2012.png">
   </td>
    <td width="25%">
      <img  src="https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/august2012.png">
   </td>
    <td width="25%">
      <img  src="https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/september2012.png">
   </td>
  </tr>
</table>
 
The images above show the emergence and disappearance of tags related to the Olympics during London 2012, as the size of tags such as "olympics" first increase and then decrease. [WordSwarm tool](https://github.com/thisIsMikeKane/WordSwarm), which is later updated by [PetrKorab](https://github.com/PetrKorab/Animated-Word-Cloud-in-Economics) is used for visualization and the up-to-date code can be found on [our repository](https://github.com/epfl-ada/ada-2022-project-stuckoverflow/tree/main/WordSwarm). [The video](https://drive.google.com/file/d/1-rYRuiiHMzSUtf9zgNV3TmrUluXinNv-/view?usp=share_link) showing the whole evolution popular tags in the "Sports" category can be found on ["Olympics Case Study"](https://github.com/epfl-ada/ada-2022-project-stuckoverflow/blob/main/Descriptive_Analysis.ipynb).

#### Centrality Analysis

"What characterizes an important vertex?"   
To answer this question, we will use various [centrality measures](https://en.wikipedia.org/wiki/Centrality) to analyze the importance of trending tags. These measures give us an idea of how a tag interacts with others. We plan to use this notion especially to answer the question of misuse, assuming that increased centrality is related to usage with more tags, which may be irrelevant considering they were not interacting before popularity.  
On ["Olympics Case Study"](https://github.com/epfl-ada/ada-2022-project-stuckoverflow/blob/main/Descriptive_Analysis.ipynb), we observed centrality increases during the Olympic years.

<p align="center">
  <img src="https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/centrality.png">
</p>

### Visualisation

We plan to visualize the graphs using one of the following libraries:
- [Cosmograph](https://cosmograph.app/)
- [sigma.js](https://www.sigmajs.org/)  

While both libraries can be used, sigma has the advantage of better search and node-specific visuals. However, Cosmograph can handle bigger graphs better. As we create networks, we will choose the better one for our use case.

## Proposed Timeline & Task Delivery Dates
* 18/11/2022 - Deliver Milestone 2
* 27/12/2022 - Implement Clustering on Tags
* 05/12/2022 - Perform Popularity and Centrality Analysis
* 10/12/2022 - Create Graph Visualizations
* 21/12/2022 - Data Story and Page Design
* 23/12/2022 - Deliver Milestone 3

## Team Organisation 
- Berkay Doner: Popularity analysis, page design
- Elif Sema Balcioglu: Clustering, centrality analysis
- Iman Najwa Binti Masrun: Data Story, page design
- Germain Vu: Graph visualizations, data story
