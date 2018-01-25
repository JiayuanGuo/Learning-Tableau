
# Methods and Algorithms in Clustering Feature of Tableau 10

Clustering is a method of grouping a set of objects in such a way that objects in the same group (called a cluster) are more similar (in some sense or another) to each other than to those in other groups (clusters). It is used as a coarse summary of the structure in the data that helps move the data exploration in a direction worth exploring and being a tool for slicing the data (forcing a structure on the data) as opposed to serving an exact answer on a silver platter.
<p>Tableau 10.0 comes with new clustering feature (k-means clustering as a built-in function)，to group similar data points and find patterns your dataset may not be able to sufficiently explain by itself. 

### K-Means Clustering Algorithm

Tableau uses K-Means clustering algorithm with a variance-based partitioning method that ensures consistency between runs.

K-means is a popular method in clustering analysis. The objective of K-Means is to partition n observations into k clusters in which each observation belongs to the cluster with the nearest mean, serving as a prototype of the cluster.

<p>k-means implementations use random initializations 
That means:
1. Subsequent runs over same data will return different results
2. With a single random initialization, the results will most likely be suboptimal (local optimum)

<p>The common solution for the second problem is to start over thousand times and pick up a best result at the expense of long wait time. 

### The Value of K
You can specify the number of clusters you’d like to get. Tableau also recommends the number of splits, which is very handy if you’re exploring your data set to see if there are groupings.

Tableau looks for the maximum value of Calinski-Harabasz index which happens when between group sum of squares is high and within group sum of squares is low.
Tableau does k-means with different values of k ranging from 2 to 25 and compares each result with the previous. If current result is less than the previous, returns the previous result. Since it is looking for a local maximum, it will terminate early which means better performance and conservative estimates of cluster count.

### Categorical fields
Tableau uses **Multiple Correspondence Analysis (MCA)** to convert categories into numeric distances before clustering, so you can use both numeric and categorical fields as inputs to clustering.

### Transformation & Scaling Method
**Min-Max Scaling Method** subtracts the minimum of the column from each value then divide the result by the difference between max and min of the column. As a result of this transformation each column get transformed to a range between 0 and 1.



**References:**

1. [Uncover patterns in your data with Tableau 10’s clustering feature](https://www.tableau.com/about/blog/2016/7/uncover-patterns-your-data-tableau-10s-clustering-feature-56373) by Bora Beran
2. [Understanding Clustering in Tableau 10](https://boraberan.wordpress.com/2016/07/19/understanding-clustering-in-tableau-10/) by Bora Beran