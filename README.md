# Network analysis with R

## Summary
* Centrality metrics are measures used to identify the most important or influential nodes (points) in a network or graph.
* In this network analysis, the main aim is to search for product co-purchasing insights and how products get sold on Amazon.
* We analysed 5 datasets from stanford data library (https://snap.stanford.edu/data/index.html#amazon) which shows the products sold on Amazon and the products that are bought together. The amazon-meta dataset contains information on each of the products and the other 4 datasets contain the product co-purchasing network on 2 March, 12 March, 5 May, and 1 June 2003 respectively.
  <img width="704" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/fe997001-b83a-468d-9f45-bce961d090d6">
* This was a trio work which all of us contributed respectively. As I was better at tidyverse in the team, the parts which I mainly contributed to were the entire bulk of data cleaning & manipulation, and analysing the top 100 products by each metric in search of customer purchasing behaviour insights.

## Data Cleaning and Manipulation
### amazon-meta data
As one can see, the data format of amazon-meta resembles that of noSQL and needs to be firstly processed and reshaped to conduct any form on analysis.

<img width="715" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/df036e60-0a12-437c-a22f-604f4a34816b">
<img width="284" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/94c7ea7c-a969-43b7-ab48-2a705a0d4178">


Using regular expressions, I managed to arrive at the table view we need (ainfo):
<img width="500" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/f6257353-97ce-4249-9322-f2ddef6eab6f">
<img width="800" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/71b19a7a-1586-44b2-b0ff-655a793ff2d8">

#### Network data (four data sets)
In the meantime, we also computed the centrality metrics for each of the four network datasets, resulting in 16 arrays - four metrics for four days. These separate dataframes were then combined 

## Computing Centrality Metrics
With the cleaned meta data, we were able to perform analysis on the co-purchasing network documents, in which the nodes are the IDs of the product and the edges are linked by products that are co-purchased. In the amazon-meta dataset, we identified 10 product categories. However, given that the bottom 6 categories only made up less than 0.0001% of the overall dataset, we decided to focus on the 4 main categories, which are Books (71.7%), Music (18.8%), Video (4.8%), and DVD (3.6%). In addition, NAs were removed from our subsequent computation as they represent discontinued products. 

<img width="1272" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/ead8245b-7953-4393-92e8-17c01171330b">

With the merged data, we proceeded to compute the top 100 products of each category group. We will be using this dataset to compare and contrast the buying behaviour based on the centrality metrics, degree centrality, closeness centrality, betweenness centrality and page rank across the four dates. 

## Comparison by Centrality Metrics
Firstly, we compared the top products on the same day by each metric. The first 4 columns represent the total number of duplicated products for each of the metrics on the 4 main categories. The last column below represents the total number of products that appeared more than once in the top 100 based on category. 

Dates | Degree | Closeness | Betweenness | Page Rank | Total number of products that appeared >1 in the Top 100
--- | ---

<img width="682" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/07042e2d-1939-4b6d-a8cd-33aeef7e5b56">

With respect to the last column, we found that there are 267, 255, 290, and 296 unique products for the 4 metrics on 2 March, 12 March, 5 May, and 1 June, respectively. This means that even though there should be 400 products on the 4 metrics (each with top 100), there are on average only 277 [(267+255+290+296)/4] out of 400, or 69.3% of products that are unique. On the other hand, it means that 30.7% of the products are the same. This shows that about 30% of the time, a product that appears high on degree centrality also appears high on betweenness centrality, as well as other metrics. 

In addition, the number of unique values in the closeness data is small compared to the other metrics. This shows that a small number of products in each group are very closely connected to all the nodes in the network. This is interesting as considering a huge network with over 500,000 unique ids, only a small number of ids are close to the centre of the network. Another observation is that on the 12 March, the betweenness is of lower value than the rest of the dates. This suggests that on that day, there might be a product promotion that may have caused the value to be lower. 

We would like to pay particular attention to those products that appear in the top 100 for 3-4 metrics. By appearing on the top list frequently, it shows that this particular product is highly in-demand as it is most frequently co-purchased with other products, on a relative basis. For example, as shown below, the product “Losing Matt Shepard” appeared 3 times on the top 100 for degree centrality (dg), page rank (pr), and betweenness centrality (bn) on 2 March. This shows that it is co-purchased more frequently than “How the Other Half Lives”, which only appeared 2 times.

<img width="522" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/3c46d4bb-0fe0-4256-aa83-7bcbe8a901c2">

With this information, Amazon can make more strategic decisions to promote products that are frequently co-purchased to increase sales. 

Comparison by Date
The analysi by date could possibly show the importance of a product over time. Firstly, we took the top 100 products of each category and looked at their degree centrality over time. We use degree centrality as it is arguably the most informative in telling us how the product is connected and co-purchased with other products. 

Similarly, we like to pay attention to those products that consistently appear on the top 100 in degree of centrality across time. For example, as shown below, the product “How the Other Half Lives” appeared consistently in the top 100 for degree of centrality, across the four dates. This is compared to “Life Application Bible Commentary” and “Prayers That Avail Much for Business”, which only appeared on 5 May and 1 June. The longer a product remains at the top for degree of centrality, the better we can tell that this product is a popular co-purchasing item across time. The consistency of this product should be utilised by marketers, and more resources should be placed in to continue the sales growth of this product. 

<img width="530" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/490f39ad-c785-4582-8d62-de090969e25a">

Furthermore, to ensure that our analysis is correct, we also looked at the top 100 for betweenness centrality, closeness centrality, and page rank centrality. The more times a product id appears, the more we can pinpoint the exact product we want to spend resources on. 
