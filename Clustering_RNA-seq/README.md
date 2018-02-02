

## Background and Objective

Clustering analysis is a useful technique for studying RNA-seq data. By identifying gene groups sharing similar features, it often provides insights into covered patterns in gene functions and networks. 

Here we plan to **build a clustering and visualization tool for RNA-seq data analysis**, using TabPy to integrate Python’s machine learning capabilities with the visualization power of Tableau. In this use case, users need to input their preprocessed RNA-seq dataset at front dashboard, and decide parameters (eg. the number of clusters — k value) they want. All the input data will be sent to Python back-end through TabPy and results query back from tabpy-client endpoints. 

After the clustering calculation, results will be visualized in front-end dashboard, presenting the clusters overview and detailed content of each cluster. Interactive panel also allows users to drill into details of clustering results, such as applying filters for visualized data, viewing nearby clusters and k evaluation. For users who demand further exploration of clustering models, model selection and comparison settings will be offered as well. Database server can be connected to Tableau, to store the input datasets and output results for future investigation.

##### Workflow:

![Workflow](/Users/jyguo/BRL/Learning-Tableau/Clustering_RNA-seq/image/Workflow.jpg)

## Summary:

Limitation of Tableau: 

* Tableau only read data by columns, not by rows

  * For our data, we need to cluster it by columns, but visualize it by rows

* TabPy Calculation: cannot return multiple results in one calculated field

  * Eg. For a k-means clustering process, we need three separate calculation fields to get all the result of  "List of K-means Label", "Score Evaluation" and "Cluster Size" 

* Need clunky data export & import to get new features from original data 

  * Eg. If we get a list of cluster id from clustering process of original gene data, we cannot do calculations based on each cluster unless export clusters seperately

    ![Cluster_preprocess](/Users/jyguo/BRL/Learning-Tableau/Clustering_RNA-seq/image/Cluster_preprocess.png)



## Folder & Files:

