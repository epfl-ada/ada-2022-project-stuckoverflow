# Tags on Trends

*StuckOverflow : Berkay Doner, Elif Sema Balcioglu, Iman Najwa Binti Masrun, Germain Vu*

## Abstract 
  
Social media posts often reflect popular concepts in the world, which can represent themselves as hashtags or tags. Using the YouNiverse dataset, we will examine the characteristics of "trending" tags on YouTube, a platform where content creation is relatively more effortful. We want to examine the evolution of the use of trending tags and whether events in the world can influence the emergence and decline of tags. We also want to analyze if trending tags interact more with other tags with the help of graph networks. This analysis may also reveal cases of misuse. While some people use irrelevant trending hashtags to increase engagement for their posts, it causes a nuisance for other users who are looking for up-to-date information and news. Twitter is a platform facing this problem, with its rapid nature in spreading information. In this project, we investigate whether the YouTube community is facing the same issue.

## Research Question
The aim of this project is to investigate the following research questions:

* How do tags evolve and die? When do they start to appear as popular tags, do these coincide with emergence of real-life events? 
* How do clusters of tags that are used together behave temporally? Do trending tags get more importance in these clusters during their popularity?
* Do people misuse video tags on unrelated video categories to exploit trending topics?   

## Methods

### Dataset
#### Storage
We use Google Drive and Google Colab Pro for our analysis since they allow easy collaboration. Given the large size of the dataset, it is unfeasible to read the whole data. To overcome this problem, we read the data by chunks and created separate datasets for each category and each timeframe. In this analysis, we consider monthly periods.

#### Pre-processing
Given we deal with textual data, our pre-processing related to tags is removing punctiations and changing letters to lowercase. We also create dictionaries for each timeframe-category pair containing tag pairs used together as key and their frequency as value.

### Tag Graph Analysis

Throughout our analysis, we will use a undirected graph network of that consists of tags as nodes. We will increase the edge weight between nodes when they are used together in a video.  
We will create a series of graphs for each category and period and analyze the evolution of the connections and emergence of nodes.

#### Tag Clustering

Since tags are entered by users, the use of natural language increases the complexity of the graph analysis as the options are endless for a topic and different people can come up with various similar tags. For example, while one user add the tag "olympics", others may add "olympic games". Handling these separately increases the size of the graph extremely. To overcome this issue, we will cluster similar tags and use them as single node. We plan to explore two options, using pre-trained NLP networks such as BERT and use similarity of their embeddings for clustering or using co-occuring frequencies of tags to uncover clusters. We will analyze the performance of these two approaches.

#### Tag Popularity Analysis

In aligned with our initial research question, we will analyze the usage of tags in terms of number of videos containing the tag. The specific behaviour will be analyzed to see the period a tag stays popular, and if this timeframe is related to the importance of the tag. 

During our initial analysis, as a case study, we focused on "Sports" category and "Olympics" as the trending topic. 
As we analyzed popular tags using [word clouds](https://en.wikipedia.org/wiki/Tag_cloud) at each timeframe, we observed increased usage during olympic times, which ended after a while. 

June 2012 | July 2012 | August 2012 | September 2012  
:-----:|:-----:|:-----:|:-----:
 ![](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/june2012.png)  |  ![](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/july2012.png) | ![](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/august2012.png) | ![](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/september2012.png)
 
The images above show the emergence and disapperance of tags related to olympics during London 2012, as the size of tags such as "olympics" first increase and then decrease. [WordSwarm](https://github.com/thisIsMikeKane/WordSwarm) later updated by [PetrKorab](https://github.com/PetrKorab/Animated-Word-Cloud-in-Economics) is used for visualization, a video can be found on ["Olympics Case Study"]().

#### Centrality Analysis

"What characterizes an important vertex?"   
To answer this question, we will use various [centrality measures](https://en.wikipedia.org/wiki/Centrality) to analyze the importance of the trending tags. These measures give us an idea on how a tag interact with others. We plan to use this notion especially to answer the question of misuse, assuming that increased centrality is related to usage with more tags, that may be irrelevant considering they were not interacting prior to popularity.  
On ["Olympics Case Study"](), we observed centrality increases during olympic years.

 ![](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/centrality.png)

### Visualisation

We plan to visualize the graphs using one of the following libraries:
- [Cosmograph](https://cosmograph.app/)
- [sigma.js](https://www.sigmajs.org/)
While both libraries can be used, sigma has the advantage of better search and node specific visuals. However Cosmograph has better handle on bigger graphs. As we create graphs, we will choose the better one for our use case.


## Proposed Timeline & (DD-MM-YYY)
* 18/11/2022 - Step X and project on hold to proceed with Homework 2
* 02/12/2022 - Step X, Y, Z
* 09/12/2022 - Step X, Y, Z
* 16/12/2022 - Step X, Y, Z
* 23/12/2022 - Step X, Y, Z

## Team Organisation 
- Berkay Doner:
- Elif Sema Balcioglu:
- Iman Najwa Binti Masrun:
- Germain Vu:
