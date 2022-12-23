# Tags on Trends

*StuckOverflow : Berkay Doner, Elif Sema Balcioglu, Iman Najwa Binti Masrun, Germain Vu*

## Abstract 
  
Social media posts often reflect popular concepts in the world, which can represent themselves as hashtags or tags. Using the [YouNiverse](https://zenodo.org/record/4650046#.Y3gE2nbMJPY) dataset, we examine the characteristics of tags on YouTube, a platform where content creation is relatively more effortful. We examine the evolution of the use of trending tags and whether events in the world can influence the emergence of tags. We also analyze if trending tags interact more with other tags with the help of graph networks. While some people use irrelevant trending hashtags to increase engagement for their posts, it causes a nuisance for other users who are looking for up-to-date information and news. Twitter is a platform facing this problem (hashtag hijacking), due to its rapid nature in spreading information. In this project, our results also reveal cases of misuse and show that the YouTube community is facing the same issue.

## Research Question
This project aims to investigate the following research questions:

* How do users use the tags? Do people go to great lengths to include tags in their videos?
* How do tags evolve and die? When do they start to appear as popular tags, do these coincide with the emergence of real-life events? 
* How do clusters of tags that are used together behave temporally? Do trending tags gain importance in these clusters during their popularity?
* Do people misuse video tags on unrelated video categories to exploit trending topics?   

## Methods

### Dataset
#### Storage

We use Google Drive and Google Colab for our analysis since they allow easy collaboration. Given the large size of the dataset, it is unfeasible to read the whole data. To overcome this problem, we read the data in chunks and create separate datasets for each category and each timeframe. In this analysis, we consider monthly periods.

#### Pre-processing

Given we deal with textual data, our pre-processing related to tags is removing punctuations and changing letters to lowercase. There are videos without categories, and they are eliminated. Also if a video has no tags, naturally it is not included in the analysis. We also create dictionaries for each timeframe-category pair containing tag pairs used together as keys and their frequency as values.

From the YouNiverse dataset, we use the [Video Metadata Dataset](https://github.com/epfl-dlab/YouNiverse#video-metadata). The only features we are interested in are "categories", "upload_date", "tags" and "titles".  

### Tag Analysis

We first analyze the usage of tags in a general sense. We examine the number of consecutive months a tag is used. We also also investigate some periodic tags such as "olympics" and "halloween". 

#### Tag Popularity Analysis

In alignment with our initial research question, we analyze the usage of tags in terms of the number of videos containing the tag. The specific behavior is analyzed to see the period a tag stays popular. We use a z-score based approach inspired by [this answer](https://stackoverflow.com/a/826509). We find several tags that correlate with real-life events such as "world cup", "geneva motor show". We also answer the question "How long does popularity last?". We visualize the number of months popular tags stay relevant in general and for each category.

![Timeline](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/timeline.PNG)

#### Centrality Analysis

Tags that are used together in a video may also reveal some important insights. We use an undirected graph network that consists of tags as nodes. We increase the edge weight between nodes when they are used together in a video. We interpret the tag-video pairs as a bipartite graph, with tags on one side and videos on the other and use the projection with tags to construct the tag network for each month. We examine the "importance" of popular tags over time by using various [centrality measures](https://en.wikipedia.org/wiki/Centrality). Analysis shows that popular tags indeed gain some importance during their popularity.

#### Misuse Analysis

We also focus on detecting videos with misuse. Given that misuse is related to the video content, we assume that the title represents the content of the video and therefore we take advantage of the titles of the videos in our analysis. The first thing that comes to mind may be to check the presence of the tag in the title, however, this would not take us further as videos with titles not containing the tag may still be relevant. To tackle this problem, we first find the most related tags with the tag, and use those as a hint of relevance.
We take the following approach to find relevant tags:

- Filter out the tags whose usage is less than 90% of the population. With this approach, we only get tags that are widely used.
- For each tag, find the number of videos it is used. num_used
- For each tag, find the number of videos it is used with the tag, num_used_tag.
- Ratio = num_used_tag / num_used * 100
- Take the tags with length > 2 and with ratio > 0.5

These relevant tags are checked in video title, if title does not include any of these words but includes the tag, we mark it as possible misuse. To see the performance of this approach, we manually label a portion of this data for the tag "trump". Among all randomly selected 613 videos, 59.2% were labeled as misuse, 19.6% as Related and 21.2% as N/A. If we exclude N/A, 75.2% of the videos would fall under the category of misuse. Sports category for example has a misuse rate of 84.2%, which can be considered high. Our manual labeling can be found [here](https://docs.google.com/spreadsheets/d/1cK55fl4xL9sktpDxsKsMGiQ0cb6Nw_bDg4K7s_CbfGE/edit?usp=sharing).

![Label](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-stuckoverflow/main/figures/total_labeling.PNG)

## Proposed Timeline & Task Delivery Dates
* 18/11/2022 - Deliver Milestone 2
* 27/11/2022 - Implement Clustering on Tags
* 05/12/2022 - Perform Popularity and Centrality Analysis
* 10/12/2022 - Create Graph Visualizations
* 21/12/2022 - Data Story and Page Design
* 23/12/2022 - Deliver Milestone 3

## Team Organisation 
- Berkay Doner: Popularity analysis, page design
- Elif Sema Balcioglu: Misuse and centrality analysis, page design
- Iman Najwa Binti Masrun: Data Story, page design
- Germain Vu: Website maintanence, page design
