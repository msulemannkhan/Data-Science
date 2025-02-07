### Links
https://www.analyticsvidhya.com/blog/2016/11/an-introduction-to-clustering-and-different-methods-of-clustering/  <br/>
https://www.saedsayad.com/clustering_kmeans.htm


### Overview
K-Means clustering intends to partition n objects into k clusters in which each object belongs to the cluster with the nearest mean.
The objective of K-Means clustering is to minimize total intra-cluster variance, or, the squared error function.

##### Algorithm
* Choose the number of clusters initially where k  is predefined. 
* Randomly assign all the data points to any of the k pre-defined clusters
* Centroid of each cluster is calculated based on the points within each cluster.
* Now Re-assign each point to the closest cluster centroid.
* When all objects have been assigned, recalculate the cluster centers (or) centroid
* Repeat steps until the same points are assigned to each cluster in consecutive rounds (or) until the centroids no longer move

##### Choosing K
* Elbow Method - Sum of Squared errors (vs) Number of clusters - k is chosen where Sum of squared erors sharply decreases
  (OR) Percentage of Variance Explained by model = 1- Sum of squared errors  (vs) Number of clusters - k is chosen where Percentage of variance sharply increases
   * Sum of Squared errors is calculated based on each observation and its group's mean
![](https://qph.fs.quoracdn.net/main-qimg-678795190794dd4c071366c06bf32115.webp)
* Silhouette Method - Measures similarity of an object to its own cluster - called cohesion -- when compared to other cluasters-- called separation. Used to determine degree of seperation. 
  * For a particular sample point - Compute the average distance from all data points in the same cluster (ai). Compute the average distance from all data points in the closest cluster (bi). Coeff = (bi - ai)/max(bi,ai)
  * Range is [-1,1]. close to 1 indicates a close relationship with objects in its own cluster, while value close to -1 indicates opposite i.e they are assigned to wrong clusters. 0 implies sample is close to neighboring clusters https://www.kdnuggets.com/2017/02/17-data-science-interview-questions-answers-part-2.html
  * A clustered set of data in a model producing mostly high silhouette values is likely an acceptable and appropriate model.
![](https://scikit-learn.org/stable/_images/sphx_glr_plot_kmeans_silhouette_analysis_003.png)
![](https://scikit-learn.org/stable/_images/sphx_glr_plot_kmeans_silhouette_analysis_004.png)


### Difference between K Means and Hierarchical clustering
* Hierarchical clustering can’t handle big data well but K Means clustering can. This is because the time complexity of K Means is linear i.e. O(n) while that of hierarchical clustering is quadratic i.e. O(n2).
* In K Means clustering, since we start with random choice of clusters, the results produced by running the algorithm multiple times might differ. While results are reproducible in Hierarchical clustering.
* K Means is found to work well when the shape of the clusters is hyper spherical (like circle in 2D, sphere in 3D).
* K Means clustering requires prior knowledge of K i.e. no. of clusters you want to divide your data into. But, you can stop at whatever number of clusters you find appropriate in hierarchical clustering by interpreting the dendrogram




