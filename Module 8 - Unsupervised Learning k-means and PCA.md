
- Distances Review
	- ![](Pasted%20image%2020240225131610.png)
	- Euclidian distance is the distance between the 2 vectors
	- ![](Pasted%20image%2020240225132002.png)
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
		- ![](Pasted%20image%2020240225132859.png)
	- Quantify outliers
		- ![](Pasted%20image%2020240225132512.png)
	- Compress data
		- Reduce the number of colors from 200+ colors to 40 or another amount ![](Pasted%20image%2020240225132651.png)
	- Select/manipulate features
		- Map from a high dimensional space to just 2 features ![](Pasted%20image%2020240225132733.png)

## Agglomerative Clustering
![](Pasted%20image%2020240225133100.png)
- Dendrogram
	![](Pasted%20image%2020240225133247.png)
	- Horizontal is distance between clusters
	- Bringing 2 cities together is a node 
		- ![](Pasted%20image%2020240225133338.png)
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
		- ![](Pasted%20image%2020240225133848.png)
	- Collapse the shortest distance and compare ^ depending on above
		- ![](Pasted%20image%2020240225133817.png)

## K-means