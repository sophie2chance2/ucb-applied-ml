
- Distances Review
	- ![](photos/Pasted%20image%2020240225131610.png)
	- Euclidian distance is the distance between the 2 vectors
	- ![](photos/Pasted%20image%2020240225132002.png)
# Unsupervised Learning
- Supervised learning:
	- (X, Y) examples
	- Predict Y from X
- Unsupervised learning
	- (x) examples 
	- Measure distances between examples of X
- No labels
	- Imagine you collect observations of some flowers 
	- But don't know their names
- Unsupervised learning
	- Understand data
		- ![](photos/Pasted%20image%2020240225132859.png)
	- Quantify outliers
		- ![](photos/Pasted%20image%2020240225132512.png)
	- Compress data
		- Reduce the number of colors from 200+ colors to 40 or another amount ![](photos/Pasted%20image%2020240225132651.png)
	- Select/manipulate features
		- Map from a high dimensional space to just 2 features ![](photos/Pasted%20image%2020240225132733.png)

## Agglomerative Clustering
![](photos/Pasted%20image%2020240225133100.png)
- Dendrogram
	![](photos/Pasted%20image%2020240225133247.png)
	- Horizontal is distance between clusters
	- Bringing 2 cities together is a node 
		- ![](photos/Pasted%20image%2020240225133338.png)
	- Leaves are items
	- Nodes are clusters
	- Root contains all items
	- Distance between clusters
		- Min (single linkage)
			- chaining behavior
		- Max (complete linkage)
			- Crowding behavior
		- Average
			- More balance
		- ![](photos/Pasted%20image%2020240225133848.png)
	- Collapse the shortest distance and compare ^ depending on above
		- ![](photos/Pasted%20image%2020240225133817.png)

## K-Means
- Comes up all the time, even if you aren't doing it it shows up in other unexpected places
- Partitioning
	- Hierarchical clustering
	- Partitioning
		- Assignment of items to clusters
		- Given some fixed number of clusters
		- ![](photos/Pasted%20image%2020240225141901.png)
	- Assignment of items to k clusters
		- $$c(i) = \{1, ..., n\} -> \{1, ..., K\}$$
		- $$n_k = num \{i:c(i) = k\} $$
		- ![](photos/Pasted%20image%2020240225142433.png)
		- Within cluster scatter, we want to minimize this ^
			- Sum over all of the distances twice
			- Left is the better cluster, since cluster scatter is minimized ![](photos/Pasted%20image%2020240225142651.png)
	- Quantifying Clusters
		- Use a centroid for each cluster
			- Instead of calculating the distance between each of the points, calculate the distance to the center of the cluster
				- ![](photos/Pasted%20image%2020240225143005.png)
			- ![](photos/Pasted%20image%2020240225143019.png)
- K means Algorithm
	- Minimize W by altering minimizing over *c* and *m*:
		0. Initialize some centroids: *m*
			- Don't know if they are good or not when assigned
		1. Update *c* by assigning each item to its closest centroid
		2. Update *m* by computing an average over items assigned to each centroid
		3. Iterate steps (2) and (3) to convergence
- K-means properties
	- W is guaranteed to decrease after each iteration
	- Algorithm always converges to a local minimum
	- Sensitive to initialization

### K - Means for Quantization
- Image color Quantization
- ![](photos/Pasted%20image%2020240225143917.png)
- With k-means k = 64  ![](photos/Pasted%20image%2020240225144122.png)
	- With each of the colors mapped, this is the new image ![](photos/Pasted%20image%2020240225144311.png)
		- Huge difference in size
- K-means with k = 2 ![](photos/Pasted%20image%2020240225144452.png)
	- ![](photos/Pasted%20image%2020240225153011.png)
- Vector Quantization
	- Signal processing / density estimation
	- Lossy data comparison
	- Codebook maps items to a smaller set of IDs
	- K-means is one way to build the codebook

### The Normal (Gaussian) Distribution
- We can make shaped elipses instead of circles using GMM
- ![](photos/Pasted%20image%2020240225153627.png)
- Normal Distribution Properties
	- Central Limit Theorem: The sum of the samples from any random variable tends to look normally distributed
		- ![](photos/Pasted%20image%2020240225154043.png)
	- Sums and differences of Normal distributions are also normal
	- Negative log of the probability density function (PDF) looks like weighted euclidean distance
		- ![](photos/Pasted%20image%2020240225153957.png)
	- ![](photos/Pasted%20image%2020240225154635.png)
	- ![](photos/Pasted%20image%2020240225155022.png)
### Normal Parameter Estimation
- Maximum Likelihood
	- Assuming our model for is correct, 
		- Choose parameters that maximize the probability (likelihood) of the data
		- Maximum Likelihood Estimates are the best we can do given infinite data

### Gaussian Mixture Models (GMMs)
- Not all data is normally distributed
- You can use a mixture of normals, using multiple Guassians 
- ![](photos/Pasted%20image%2020240225160920.png)
- The probability of each observation is a weighted combination of Gaussians
	- Component weights are p multinomial
	- Can approximate any distribution... with enough Gaussians
- GMM Generative Process
	- ![](photos/Pasted%20image%2020240225161329.png)
- MLE for GMMs
	- Need to estimate means, co-variances and mixture weights
	- Mixture weights are hidden variables
	- No straightforward way to get the argmax over parameters

### GMM Parameter Estimation
- Hidden variables
	- Suppose we had a cluster assignment for each datapoint
	- Now we can get the MLE for the GMM parameters
	- Given Gaussian parameters, we can generate cluster assignments
	- Sounds like K-means algorithm
- Expectation Maximization (EM)
	- Hard assignment:
		- Assign a single cluster for each x_i
		- Similar to k-means
		- convergence guarantees don't hold
	- Soft assignment:
		- x_i gets a partial assignment to each cluster j
		- Also called "fractional counts"
		- Parameters converge to local optimum

### Dimensionality Reduction
- Singular Value Decomposition (SVD)
	- Factorization of any rectangular matrix
	- Sigma contains singular values
	- U and V contain singular vectors
	- Can reconstruct the original data matrix M from this product
	- ![](photos/Pasted%20image%2020240227123758.png)
	- ![](photos/Pasted%20image%2020240227124100.png)
	- ![](Pasted%20image%2020240227124504.png) (150 x 4) -> (150 x 2)
	- ![](Pasted%20image%2020240227124453.png) reconstructed is pretty close to the original features
	- ![](Pasted%20image%2020240227124652.png)
	Why Reduce Dimensions?
	- Remove noise from the data
	- Reduce the number of features and thus model complexity
	- Help visualize relationships
- SVD ~ PCA very similar, almost the same thing
- ![](Pasted%20image%2020240227125126.png)