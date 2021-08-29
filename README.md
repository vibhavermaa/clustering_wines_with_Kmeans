# Unsupervised Learning:

Unsupervised learning algorithms are used to find out the groups of observations that share the similar characteristics. So , what is the meaning of unsupervised learning? It means that the observations given in the dataset are not labeled, there is no outcome associated with it. 

Goal/Main Objective: 
In this assignment, I am going to use a wine quality dataset to cluster different types of wine. The data set contains various chemical properties of wine, such as acidity, sugar, pH, and alcohol. It also contains a quality metric (3-9, with highest being better) and a color (red or white).
I will apply clustering algorithms and compare the results to those with regards to wine color by reporting the number of red and white observations in each cluster for both K-means and agglomerative clustering.I will be using all the wine attributes except quality and color to cluster the wines. 
Also, extend the work by using the KMean cluster as a form of feature engineering and apply supervised machine learning algorithms to predict the labels. 

## Data Preview:

The name of the file is Wine_Quality_Data.csv. It has 6497 observations and 13 chemical properties. 
- The number of wine color are Red and  White, and the number of entries for each color is:
Red        4898
White     1599

- The dataset has no missing entries 


## Exploratory Data Analysis:

- the data is imbalanced as the lablel distribution is not uniform across quality levels.
-  there isn't any strong relationship between our features

## Data Preprocessing: 

- Missing Values : This dataset does not have missing observation. Hence need not to apply any data imputation method.

- Examine correlation of variables: High correlation between variables can lead us to the problem of high dimensionality and we know that it causes a problem whenever we work with distance metrics as we are with most of our clustering algorithms. In our case, there are some high correlations but not high enough to exclude certain values.

- There are skewd features, handled by applying log transformation.

- Feature Scaling: standardize the variables except label to express them in the same range of values.


## Clustering Algorithms: 

### K-Means Algorithm: 
> Kmeans,  relies on finding cluster centres to group data points based on minimizing the sum of squared errors between each data point and its cluster center. This algorithm requires a number of  clusters to be passed as a parameter.                
the algorithm works well in separating the unlabeled data into two different clusters that are very highly related to red and white clusters.

### K-Means Algorithm with varying number of clusters: 

Extended the K Mean analysis by running it multiple times on a varying range (1-20) of clusters assuming that we don't know the no of cluster K that we want. Used the inertia (sum of squared distance from each point to a cluster center) value to identify the best no of clusters(K) to be passed to the algorithm. 

Created a line chart between clusters and their inertia value. In order to identify the best K value,used the “Elbow Method”. 
The best practice is that if you know that there will be X labels you can choose that as K. Just like, we used K as 2 , to identify 2 different clusters depicting red and white wine. 

## Agglomerative Clustering Algorithm: 
> In data mining and statistics, hierarchical clustering (also called hierarchical cluster analysis or HCA) is a method of cluster analysis which seeks to build a hierarchy of clusters. Agglomerative is a "bottom-up" approach: each observation starts in its own cluster, and pairs of clusters are merged as one moves up the hierarchy.

When applying this algorithm on the clustered dataset and passing 2 as no of clusters, “ward” as linkage  this algorithm also works well in separating the unlabeled data into two different clusters.



## Comparison of Kmean and Agglomerative clustering results:  

From both the results, we concluded that misclassification/ mismatch count for red and white wine is less in Kmean Algorithm which is 23 and 87 than in Agglomerative clustering which is 31 and 143. KMeans performs better than to Agglomerative clustering algorithm


## Key Findings : 

- Dataset is unbalanced and it doesn't have any highly correlated features.
- KMeans perform better than to Agglomerative clustering algorithm for this dataset
- The best practice to set a no_of_cluster argument is that if you know that there will be X labels you should choose that as K. Just like, we used K as 2 , to identify 2 different clusters depicting red and white wine. 
- If you don't know the no_of_clusters , use the Elbow method to identify it.

## Observations:  
There are few thoughts that can be applied to achieve a better model or better modelling result.

## Possible flaws and Possible Plan of action: 

For the KMeans algorithm, there are two areas where the shortcomings of Kmeans become apparent.
- Highly unbalanced data:  the dataset we have is highly imbalanced. The red wine observations are 4989 and white wine is 1599. Unbalanced dataset introduces difficulty for  KMeans to separate the data points into clusters and tend to pull all centroids to the mean of the majority class. Hierarchical clustering helps to reduce this issue which is not performing well for this dataset.
As a Plan of action, we can increase the data size and check how hierarchical clustering performs as compared to K Means algorithm.

- Data in high dimensional space: Even though the feature set is not very large. As a Plan of action , we can perform Principal component Analysis on the input dataset and follow KMeans algorithm and examine the result.

- How density based algorithms work with this dataset ? We can use a density based clustering algorithm and examine the results.
- Even though, there are no highly correlated features, we can try to exclude features having correlation value greater than 0.5 and run KMeans and examine results.
