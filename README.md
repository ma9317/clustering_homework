# clustering_homework
**Assignment**  
Goal is to use scikit learn to mimic the whiskey clustering problem using the associated dataset attached below. Start a new colab notebook and add appropriate text to help orient the reader. Prepare and cluster the data using KMeans and a hierarchical clustering algorithm.   
**Description**  
The goal of this project is to identify meaningful groupings of whiskies based on their flavor characteristics using unsupervised learning techniques. the dataset (whiskey) represents each whiskey using a large set f binary features that indicate the presence (1) or absence (0) of specific tasting notes (e.g "peaty" "sweet" "fruity). Each whiskey is a datapoint in a 80-dimensional space composed of binary indicators. For this reason, I found that hierarchical clustering is more appropriate than KMeans clustering.  
Hierarchical clustering is better suited for this type of data because it dosen't assume any particular geometric structure and instead groups observations based on similarity. In contrast, KMeans relies on euclidean distance and attempts to partition the data into clusters around centroids, which works best when the data is continuous, but in a dataset like this wone where features are binary and sparse, the otion o an "average whiskey" (which is how the centroids are defined) is not meaningful. So KMeans produced imbalanced and uninterpretable clusters. Basically, KMeans can't find clean groups, so it dumps most points together and isolates a few outliers.  
<img width="1288" height="690" alt="image" src="https://github.com/user-attachments/assets/711bbc1a-e7b6-4303-81ed-846f21ad09fa" />

This issue became evident in the results. I was initially afraid I did something wrong, because it made no sense.  
<img width="796" height="295" alt="image" src="https://github.com/user-attachments/assets/a7af4d6b-3f19-4f09-9526-0a013b84d620" />  
One cluster had the majority of observations (around 100) while the remaining clusters had <10. The "optimal" number of clusters for KMeans clustering was identified using the "elbow" method--k turned out to be 2. But even when adjusting the number of clusters, the algorithm continued to produce skewed distributions, suggesting that it wasn't capturing meaningful structure in the data. For example:  
<img width="858" height="228" alt="image" src="https://github.com/user-attachments/assets/46a78d27-54d6-462c-9dbb-497aa120db2b" />
<img width="802" height="267" alt="image" src="https://github.com/user-attachments/assets/ae9e3a14-aef1-4233-bbb9-0c876821b586" />
<img width="798" height="301" alt="image" src="https://github.com/user-attachments/assets/5258e85a-e92f-47bf-b554-ea7757c239f3" />

Long story short: although the elbow method suggested an optimal k, in practice it was misleading because the underlying assumptions of kmeans were violated by the data structure. 
Hierarchical clustering, on the other hand, focuses on the similarities between the individual instances and how similarities link them together. By constructing a dendrogram, I was able to visualize how whiskies group togeter at differen levels of similarity, rather than forcing tem into a fixed number of clusters from the beginning. 

**Understanding the Results of Clustering**
The high dimensionality and binary structure of the data likely conributed to weak separation between clusters, as distance measures become less informative in high-dimensional spaces. 
