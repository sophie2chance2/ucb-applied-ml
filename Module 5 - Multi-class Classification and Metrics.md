# Classification Metrics

![[Pasted image 20240211091929.png]]
![[Pasted image 20240211092249.png]]
![[Pasted image 20240211093554.png]]
Accuracy = Correct / Total

![[Pasted image 20240211093733.png]]
Precision = True Positive / (True Positive + False Positives)
- Of all of the sneaker predictions, 90% were correct

![[Pasted image 20240211093752.png]]
Recall = True Positive / (True Positive + False Negative)
- Of all of the sneakers, my model predicted half

 ![[Pasted image 20240211094824.png]]
 Moving the threshold will give you a tradeoff between precision and recall. 
 - Area Under the Curve (AUC)
 - Average Precision (AP)
 - Summarizes how well classifier does in many different situations

# Multiclass Classification
![[Pasted image 20240211103243.png]]
- K binary classigiers
- Each classifier has its own parameters
	- Each one does its own xw^T
	- Apply the sigmoid to each one of those
	- Each classifier will have a value between 0 and 1, so they may not add up to 1 total
- Softmax normalization scales a set of scores to a multinomial probability distribution
	- ![[Pasted image 20240211103808.png]]
	- Multinomial probability distribution - arbitrary vector of values where the sum of those values is 1
		- ex. [0.1, 0.7, 0.2] -> sum = 1
		- [2, 9, 3] -> [2/14, 9/14, 3/14]
	- ![[Pasted image 20240211111338.png]]
		- Use Confusion Matrix to understand why it is making certain strange predictions

# Multiclass Loss
- ![[Pasted image 20240211111710.png]]
	- Sparse Representation: y = 0, y = 1, y = 2, y = 3 ....
	- Dense Representation: [1, 0, 0, 0, 0, 0, 0, 0, 0, 0]
	- Use dense representation in loss formula so that there is only one active term
		- ![[Pasted image 20240211112022.png]]
	- 