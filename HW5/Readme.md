# Reading
Section 1 and 2 in 
https://robjhyndman.com/papers/DMKD.pdf

# Homework
Reproduce the lab and turn it in. 

What I want to see:

1. A plot of each of the 4 cluters for the population data showing the cluster members and the cluster centers. (with caption describing the design of the plot and you see and what is interesting!) You can use whatever metjod for clustering here: kmeans (https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html), hierarchical clustering (https://scikit-learn.org/stable/modules/generated/sklearn.cluster.AgglomerativeClustering.html#sklearn.cluster.AgglomerativeClustering), DBSCAN (https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html#sklearn.cluster.DBSCAN). Clearly describe the hyperparameters you chose and why (and if you just guessed its ok, say so). If you use  hierarchical clustering I recommand you do a dandrogram of your cluster history (https://scikit-learn.org/stable/auto_examples/cluster/plot_agglomerative_dendrogram.html#sphx-glr-auto-examples-cluster-plot-agglomerative-dendrogram-py)
2. A plot of the intracluster variance when you cluster with N=2,3,4,5,6,7,8,9,10 clusters with k-means:

![img](Screen Shot 2022-03-12 at 8.22.37 AM.png?raw=true "Equation")
