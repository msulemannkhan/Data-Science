### Links


### Overview
Builds hierarchy of clusters. This algorithm starts with all the data points assigned to a cluster of their own. Then two nearest clusters 
are merged into the same cluster. In the end, this algorithm terminates when there is only a single cluster left.
The results of hierarchical clustering can be shown using dendrogram.
![](https://www.analyticsvidhya.com/wp-content/uploads/2016/11/clustering-6.png)
The decision of the no. of clusters that can best depict different groups can be chosen by observing the dendrogram. The best choice of the no. of clusters is the no. of vertical lines in the dendrogram cut by a horizontal line that can transverse the maximum distance vertically without intersecting a cluster.
![](https://www.analyticsvidhya.com/wp-content/uploads/2016/11/clustering-7.png)
* This algorithm has been implemented above using bottom up approach. It is also possible to follow top-down approach starting with all data points assigned in the same cluster and recursively performing splits till each data point is assigned a separate cluster.
* The decision of merging two clusters is taken on the basis of closeness of these clusters. There are multiple metrics for deciding the closeness of two clusters :
  * Euclidean distance: ||a-b||2 = √(Σ(ai-bi))
  * Squared Euclidean distance: ||a-b||22 = Σ((ai-bi)2)
  * Manhattan distance: ||a-b||1 = Σ|ai-bi|
  * Maximum distance:||a-b||INFINITY = maxi|ai-bi|
  * Mahalanobis distance: √((a-b)T S-1 (-b))   {where, s : covariance matrix}
 
### Difference between K Means and Hierarchical clustering
* Hierarchical clustering can’t handle big data well but K Means clustering can. This is because the time complexity of K Means is linear i.e. O(n) while that of hierarchical clustering is quadratic i.e. O(n2).
* In K Means clustering, since we start with random choice of clusters, the results produced by running the algorithm multiple times might differ. While results are reproducible in Hierarchical clustering.
* K Means is found to work well when the shape of the clusters is hyper spherical (like circle in 2D, sphere in 3D).
* K Means clustering requires prior knowledge of K i.e. no. of clusters you want to divide your data into. But, you can stop at whatever number of clusters you find appropriate in hierarchical clustering by interpreting the dendrogram
