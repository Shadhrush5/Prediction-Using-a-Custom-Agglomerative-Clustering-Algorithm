# Prediction-Using-a-Custom-Agglomerative-Clustering-Algorithm
This project is focused on the Breast Cancer Wisconsin (Diagnostic) dataset, aiming to classify data points as Malignant or Benign. Here I am using Agglomerative clustering for classification, preceded by specific pre-processing steps. Though using classifiaction models would have been a better choice, this shows that clustering can also be used.

## Requirements
1. Download the dataset from here https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data.
2. Python along with Jupyter Notebook environmen set up.

## DataSet
Talking about the data set, each data point has 32 columns indicating the attributes of a patient and their tumor. The target column or the column which needs to be predicted is the ’Diagnosis’ column. The diagnosis of each patient/data point is either malignant or benign which indicates the nature of the tumor. There about 569 data points in the given data set. 

## Goal
The motivation is to use Agglomerative clustering to try and predict the diagnosis for a data point. To do this I had to first do pre-processing and used the respective methods from an off-the shelf source. The evaluation for the same was done as well. For the final part of the project each of us implemented the methods from scratch on our own and evaluated the same in two ways. One using the real-world data set and the other using the artificial data set to check implementation correctness.

## Agglomerative Clustering

Agglomerative clustering is a hierarchical clustering method which
uses a bottom up approach to clustering. The main idea behind the algorithm is that at the beginning each point is a cluster on its own. On each iteration, we add to a cluster one or more points closest to the cluster based on the specified linkage. For the scope of this project I have used single linkage as directed.

1. fitAggScratch(): Here at each iteration, one point nearest to the cluster is added to it. This process continues until we reach the number of specified clusters. For the sake of the given data set, considering the types of diagnosis, 2 clusters would be the right choice.
2. distanceMatrix(): We need to initially calculate the dis- tance of each point to every other point and store this in a distance matrix. This matrix needs to be updated every itteration when a point is added to a cluster. This updated values would be used for the next iteration.
3. distanceFuntions(): Here at each iteration, one point near- est to the cluster is added to it. This process continues until we reach the number of specified clusters. For the sake of the given data set, considering the types of diagnosis, 2 clusters would be the right choice. The distance function used to find the nearest data point is also something that we can spec- ify out of 3 options. The options are Euclidean, Manhattan and Cosine metrics. This is the hyper parameter which I am trying to optimize for this problem. The above steps were coded as part of my from the scratch implementation. Before this, I am doing a few pre-processing steps.

## Pre-processing the data

1. Removed null values from the dataset.
2. Dropped ’Unnamed: 32’ and ’id’ columns because they
were irrelevant in determining the result.
3. Used LASSO method which performs both feature selec-
tion and regularization by shrinking the coefficients of
less important features to zero.
4. Used t-SNE since it was particularly effective in dimen-
sionality reduction of our dataset. This helps us visualize out model in 2-D space.

## Evaluation

Silhouette score and NMI (Normalized Mutual Information) are evaluation metrics used to assess the quality of clustering algorithms.

1. The Silhouette score measures how well each data point fits within its assigned cluster. It takes into account both the average distance to other data points in the same cluster (cohesion) and the average distance to data points in the nearest neighboring cluster (separation). A higher Silhouette score indicates better clustering, with values ranging from -1 to 1, where 1 represents well-separated clusters and -1 represents poorly assigned data points.

2. NMI, on the other hand, evaluates the agreement between the true class labels and the clusters assigned by the algorithm. It calculates the mutual information between the two sets of labels, normalized by the entropy of each label set. NMI ranges from 0 to 1, where 1 indicates perfect agreement between the clustering and true labels.

Both Silhouette score and NMI provide quantitative measures to assess the performance of clustering algorithms. Higher Silhouette scores and NMI values indicate better clustering results, indicating higher cohesion within clusters and better agreement with the true class labels, respectively.

<img width="228" alt="Screenshot 2023-06-18 at 9 56 37 AM" src="https://github.com/Shadhrush5/Prediction-Using-a-Custom-Agglomerative-Clustering-Algorithm/assets/119898772/57d46027-7164-45de-8920-4237f98f7a0f">


## Clustering Results

<img width="343" alt="Screenshot 2023-06-18 at 9 57 17 AM" src="https://github.com/Shadhrush5/Prediction-Using-a-Custom-Agglomerative-Clustering-Algorithm/assets/119898772/7b30b25a-98c1-4a40-b841-917498f299f7">

## Tuning Results

<img width="343" alt="Screenshot 2023-06-18 at 9 57 31 AM" src="https://github.com/Shadhrush5/Prediction-Using-a-Custom-Agglomerative-Clustering-Algorithm/assets/119898772/244b419f-4a47-4eea-9151-4d806452a802">

## Validating Correctness

Using a smaller data set having just 2 diemntions, we can compare the results of my algorithm along with that of an off the shelf implementation from scikit learn. On doing that these were the results.
### Clusters comparison
<img width="343" alt="Screenshot 2023-06-18 at 10 03 04 AM" src="https://github.com/Shadhrush5/Prediction-Using-a-Custom-Agglomerative-Clustering-Algorithm/assets/119898772/f6415819-d483-4076-ba81-cc16e759664e">

### Dendrogram

A dendrogram is a hierarchical tree-like diagram used to visualize the results of agglomerative clustering, which is a type of hierarchical clustering algorithm. It represents the merging process of individual data points or clusters into larger clusters.

In agglomerative clustering, the algorithm starts with each data point as a separate cluster and iteratively merges the closest pairs of clusters based on a chosen distance metric. The dendrogram visually displays these merging steps. The vertical axis of the dendrogram represents the distance or dissimilarity between clusters, while the horizontal axis represents the individual data points or clusters.

The height at which two clusters merge in the dendrogram indicates the dissimilarity at which they were combined. The longer the vertical line connecting two clusters, the more dissimilar they are. By analyzing the dendrogram, one can identify the optimal number of clusters based on the desired level of dissimilarity.

The correctness of agglomerative clustering can be measured by examining the structure of the dendrogram. Ideally, correct clustering results in a dendrogram with distinct and well-separated branches, indicating clear boundaries between clusters. In contrast, incorrect clustering may result in overlapping or tangled branches, indicating poor separation of clusters.

By analyzing the dendrogram, one can assess the correctness of agglomerative clustering and make decisions regarding the appropriate number of clusters or the level of dissimilarity required to obtain meaningful clusters.

<img width="302" alt="Screenshot 2023-06-18 at 10 03 21 AM" src="https://github.com/Shadhrush5/Prediction-Using-a-Custom-Agglomerative-Clustering-Algorithm/assets/119898772/a8669912-771d-4225-ab9e-ed3058a734cf">




