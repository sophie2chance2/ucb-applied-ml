https://docs.google.com/presentation/d/1yvO1jiPyUXH_YCvuOGDIUvbnVNj5-c76uoqUwDnsO8w/edit#slide=id.g253ebd6bb5f_0_28

https://colab.research.google.com/drive/1ybzGbGbTwKseMriyJ5DL4Z9iK8UdlOev?usp=sharing#scrollTo=CDDtNYMCO8Yc

Ensembles - If you take the average of all the guesses, you will get the correct answer
- Majority vote:  everyone votes and majority wins
	- ![[Pasted image 20240220161441.png]]
- Bagging: Train models in parallel via bootstrap sampling
	- Can't overfit because you are removing the data as you sample it. Overfitting only happens when over sampling the data
	- Can be samples of rows or columns or both
	- ![[Pasted image 20240220161459.png]]
- Boosting: Train additive models in series where each predicts the residual from the previous ones
	- XGBoost
	- ![[Pasted image 20240220162456.png]]
		- Focuses on the "weak learners" - the hard to classify items

### KNN
- ![[Pasted image 20240220163357.png]]
- K means: looks at the center
- ![[Pasted image 20240220163650.png]]
- 

