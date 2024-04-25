# Network analysis with R

## Summary
* In this network analysis, the main aim is to search for product co-purchasing insights and how products get sold on Amazon.
* We analysed 5 datasets from stanford data library (https://snap.stanford.edu/data/index.html#amazon) which shows the products sold on Amazon and the products that are bought together. The amazon-meta dataset contains information on each of the products and the other 4 datasets contain the product co-purchasing network on 2 March, 12 March, 5 May, and 1 June 2003 respectively.
  <img width="704" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/fe997001-b83a-468d-9f45-bce961d090d6">
* This was a trio work which all of us contributed respectively. As I was better at tidyverse in the team, the parts which I mainly contributed to were the entire bulk of data cleaning & manipulation, .

## Data Cleaning and Manipulation
As one can see, the data format resembles that on Javascript and needs to be firstly processed and reshaped to conduct any form on analysis.

<img width="715" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/df036e60-0a12-437c-a22f-604f4a34816b">
<img width="284" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/94c7ea7c-a969-43b7-ab48-2a705a0d4178">


Using regular expressions, I managed to arrive at the table view we need:
<img width="1069" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/71b19a7a-1586-44b2-b0ff-655a793ff2d8">



<img width="897" alt="image" src="https://github.com/tltxyyy/page-rank/assets/69724535/f6257353-97ce-4249-9322-f2ddef6eab6f">


With the data now in the view we want to see, we can run compute the respective centrality metrics to conduct analysis.
