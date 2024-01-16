
Learned Functions = Models

### ML Framing: Car Pricing
* Inputs & Outputs
	* Input: Car Features
	* Output: Dollars
* Labeled data
	* Horsepower, number of seats, etc.
* Split train/test
	* 80% for training
	* 20% for testing
	* Selected randomly
* Evaluation
	* Average absolute difference in $ from predicted $ and actual $
* Baseline
	* Average Price of car in training dataset
	* *Cannot look at test set - baseline should be on training set only*
* Use in practice
	* Use the model to price a new car


## Features
- Features are the mechanisms by which we decompose whole objects in common pieces that are shared amongst those objects
* Without those pieces we cannot generalize about new cars
	- Ex. Size, Engine type, horse power, seats, trunk size

## How does learning work?
* How would I describe the process of making an informed prediction.
* Usually using logic, like this flow diagram
* ![[Pasted image 20240114124546.png]]
	* This didn't work^^^^^^^
* Then, turned the learning process into the optimization problem
* ![[Pasted image 20240114124723.png]]
	* Minimize the loss function
* ML is pretty different from what happens in your brain
	* We don't really know how we learn. Describing how you learn is different from how we probably are doing it. 
	* Computers are good at computation, so thats how ML works.

### Linear Regression
* Taking optimization strategy - starting with linear regression - Focused on prediction
* Originally used to plan planetary movements
* In ML
	* Much more focused on outcomes than restrictions
* Gradient descent
	* Useful for training much more complicated models
* f(x) = mx+b => f(x) = w0 + w1x
	* Model => f(x) = w0 +w1
		* Can have millions of parameters (w) on better models
	* Parameters
		* W = [w0, w1]
	* Mapping parameter values
		* W = [w0 = 38, w1 = 3]
		* W = [w0 = 48, w1 = 2]
		* ![[Pasted image 20240115155529.png]]
			* Use MSE to answer "which is better?"
				* Look at the difference between the actual and the predicted
				* ![[Pasted image 20240115155641.png]]
				* ![[Pasted image 20240115155922.png]]
					* General to any model - not just regression 
					* yi^ = w0 + w1x
				* Model 1:  W = [w0 = 38, w1 = 3]
					* MSE = 3.25
				* Model 2: W = [w0 = 48, w1 = 2]
					* MSE = 0.825
					* THIS ONE IS BETTER!
### Loss
- Need a way to measure success
	- For regression problems, MSE is the standard measurement
- ![[Pasted image 20240115160124.png]]
- m = 10 in this dataset (number of examples in dataset)
- Goal is to minimize loss!
	- Choose w0, w1 that make J the smallest