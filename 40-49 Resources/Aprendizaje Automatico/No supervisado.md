tags: [[Machine Learning]]
## Unsupervised learning
Unsupervised learning is quite similar to supervised learning, except it doesn't have a target column - hence the unsupervised part. 

So what's the point then? 

Unsupervised learning learns from the dataset, and tries to find patterns. That's the reason this technique is so interesting and powerful: ==we can find insights without knowing much about our dataset.==

## Clustering
Clustering consists in identifying groups in your dataset. The observations in these groups share stronger similarities with members of their group, than with members of other groups.

### Clustering example
For example, say we have a dataset with six observations. What clusters would the algorithm detect?
### Species Cluster
It may come up with two groups: dogs and cats.
![[Pasted image 20260211224517.png]]
### Color 
Or, it might make four groups by color: black, grey, white and brown.
![[Pasted image 20260211224552.png]]

### Origin 
it may find origin groups: the top row originate from Europe, while the bottom row are from Japan. In these examples, I've told you what each group represents. 

**However, you usually don't know what differentiates your clusters in real life. Your model won't tell you why or how it decided on these clusters. It's up to you to investigate and find out.**

## Clustering models
Some clustering models, like ==K-Means==, require you to specify in advance the number of clusters you would like to identify. 
Others, like ==DBSCAN==, or - get ready - "Density-based spatial clustering of applications with noise", don't require you to specify the number of clusters in advance. Instead, they require you to define what constitutes a cluster, like the minimum number of observations in one cluster.

# Anomaly detection
Anomaly detection is all about detecting outliers. Outliers are observations that strongly differ from the others.
- Anomaly detection = detecting outliers
- Outliers = observations that differ from the rest


# Association
Let's end with association, which consists in finding relationships between observations.

it's about finding events that happen together. It's often used for market basket analysis, which is just a fancy expression to state "Which objects are bought together?" For example, people who buy jam are likely to buy bread, people who buy beer are likely to buy peanuts, and people who buy wine are likely to buy cheese.