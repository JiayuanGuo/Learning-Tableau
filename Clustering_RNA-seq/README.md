

## Background and Objective

Clustering analysis is a useful technique for studying RNA-seq data. By identifying gene groups sharing similar features, it often provides insights into covered patterns in gene functions and networks. 

Here we plan to **build a clustering and visualization tool for RNA-seq data analysis**, using TabPy to integrate Python’s machine learning capabilities with the visualization power of Tableau. In this use case, users need to input their preprocessed RNA-seq dataset at front dashboard, and decide parameters (eg. the number of clusters — k value) they want. All the input data will be sent to Python back-end through TabPy and results query back from tabpy-client endpoints. 

After the clustering calculation, results will be visualized in front-end dashboard, presenting the clusters overview and detailed content of each cluster. Interactive panel also allows users to drill into details of clustering results, such as applying filters for visualized data, viewing nearby clusters and k evaluation. For users who demand further exploration of clustering models, model selection and comparison settings will be offered as well. Database server can be connected to Tableau, to store the input datasets and output results for future investigation.

##### Workflow:

![Workflow](https://github.com/JiayuanGuo/Learning-Tableau/blob/master/Clustering_RNA-seq/image/Workflow.jpg)



## Summary:

##### Progress:

* Generate Python Script for TabPy Client   **✓**

* Evaluate and deploy py script in calculated fields   ✓

* Visualize clustering results in interactive dashboard    **X**  （cannot proceed to do visualization. Reasons in "Limitation of Tableau" part）

  ​

##### Limitation of Tableau: 

* Tableau only read data by columns, not by rows

  * For our data, we need unpivoted data to do clustering analysis by columns (shown as Unpivoted_Workbook), but visualize it by rows (shown as Pivoted_Workbook)

  * Eg. Pivoted Data:

    ![Pivoted_Data_Example](https://github.com/JiayuanGuo/Learning-Tableau/blob/master/Clustering_RNA-seq/image/Pivoted_Data_Example.png = 30x40)

    Visualization based on rows:![visualization_by_pivoted_data](https://github.com/JiayuanGuo/Learning-Tableau/blob/master/Clustering_RNA-seq/image/visualization_by_pivoted_data.png)

    Failed Clustering:![](https://github.com/JiayuanGuo/Learning-Tableau/blob/master/Clustering_RNA-seq/image/failed_clustering_by_pivoted_data.png)

* TabPy Calculation: cannot return multiple results in one calculated field

  * Eg. For a k-means clustering process, we need three separate calculation fields to get all the result of  "List of K-means Label", "Score Evaluation" and "Cluster Size" 

* Need clunky data export & import to get new features from original data 

  * Eg. If we get a list of cluster id from clustering process of original gene data, we cannot do calculations based on each cluster unless export clusters seperately

    ![ClustersProcess](https://github.com/JiayuanGuo/Learning-Tableau/blob/master/Clustering_RNA-seq/image/Cluster_preprocess.png)

## Future Plan:

1. Stick with TabPy integration method: Fix the gap of clustering and visualization in Tableau by extracting and re-inputting data.

   ![Future Plan with TabPy](https://github.com/JiayuanGuo/Learning-Tableau/blob/master/Clustering_RNA-seq/image/Future_Plan_TabPy.png)

2. Give up TabPy and use Python for data manipulation & building clustering model

   ![Future Plan with Python](https://github.com/JiayuanGuo/Learning-Tableau/blob/master/Clustering_RNA-seq/image/Future_Plan_Python.png)

## Folder & Files:

**df5_log2_ratio.csv:** Transcriptomics data from [Cu_transition_time_course-](https://github.com/gilmana/Cu_transition_time_course-) , containing 4410 gene as rows, and 40 samples as columns. 

**TabPy_Client.ipynb:** Jupyter Notebook, containing python script to publish the clustering function to TabPy server.

**Unpivoted_Clustering.twb:** Tableau Workbook, starting with original data (df5_log2_ratio.csv), using TabPy to run k-means clustering and get clusters overview.

**Pivoted_Visualization.twb:** Tableau Workbook, starting with pivoted data, visualizing genes and their expression level trends through all 40 samples, but failing to do clustering analysis.

**[Image Folder](https://github.com/JiayuanGuo/Learning-Tableau/tree/master/Clustering_RNA-seq/image):** Folder containing important images that are extracted from workbook or used for README discription.

