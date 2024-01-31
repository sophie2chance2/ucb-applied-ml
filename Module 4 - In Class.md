![[Pasted image 20240130160719.png]]
- Linear decision maker
- Fixed before/after
- Precision
	- How precise do you want to be?
	- Airport
		- Do not want anything to slip through the cracks
	- Choose one side (find weapons) that you are deciding how precise you want it to be. 

# In Class Example
[PytorchBuildUp](https://colab.research.google.com/drive/1MvuyQ7ARJb3QpHsU7lPG0nCeXKH3o7ll?usp=sharing#scrollTo=2mlgKX76obWL)
### Mnist
![[Pasted image 20240130162223.png]]
- Invariance: Rotational Invariance - If you turn the number on its side will the model still work?
	- Centered and oriented correctly is important for model to work
- Important to see that the loss is going down, that means it is learning
	- Sometimes the loss will plateau, but that doesn't mean it is done learning. Could have a breakthrough at any point
- Once you train too much you start overfitting ![[Pasted image 20240130165401.png]]
- Optuna - tries all of the different options until it finds a fit that provides the best outcome
	- Grid search (alternative)
- Run random forest or XGboost
	- Monday Random forest - Get baseline
	- Tuesday - Next Thursday for Deep learning
		- Is the accuracy better?
			- If not, then use the basic one
	- Friday Present Work


- Random forest is going to work no matter what
	- Can run it at scale
	- Idiot proof
- XGboost - will be slightly better than random forest, but only 1-2%
- Logistic regression
	- You need to tune it
- Deep learning - as soon as there is a problem the whole thing will break