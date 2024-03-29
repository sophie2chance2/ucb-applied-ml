
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


### Features
- Features are the mechanisms by which we decompose whole objects in common pieces that are shared amongst those objects
* Without those pieces we cannot generalize about new cars
	- Ex. Size, Engine type, horse power, seats, trunk size

### How does learning work?
* How would I describe the process of making an informed prediction.
* Usually using logic, like this flow diagram
* ![](<photos/Pasted image 20240114124546.png>)
	* This didn't work^^^^^^^
* Then, turned the learning process into the optimization problem
* ![](<photos/Pasted image 20240114124723.png>)
	* Minimize the loss function
* ML is pretty different from what happens in your brain
	* We don't really know how we learn. Describing how you learn is different from how we probably are doing it. 
	* Computers are good at computation, so thats how ML works.

# Linear Regression
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
		* ![](<photos/Pasted image 20240115155529.png>)
			* Use MSE to answer "which is better?"
				* Look at the difference between the actual and the predicted
				* ![](<photos/Pasted image 20240115155641.png>)
				* ![](<photos/Pasted image 20240115155922.png>)
					* General to any model - not just regression 
					* yi^ = w0 + w1x
				* Model 1:  W = [w0 = 38, w1 = 3]
					* MSE = 3.25
				* Model 2: W = [w0 = 48, w1 = 2]
					* MSE = 0.825
					* THIS ONE IS BETTER!
### Loss & Linear Regressions
- Need a way to measure success
	- For regression problems, MSE is the standard measurement
- ![](<photos/Pasted image 20240115160124.png>)
- m = 10 in this dataset (number of examples in dataset)
- Goal is to minimize loss!
	- Choose w0, w1 that make J the smallest

### Linear Regression Review 
![](<photos/Pasted image 20240115160407.png>)
- Model = functional form for a prediction function
- Parameters = To fully specify the model, we need to provide values for the parameters in the model
- Loss = Different from the model, compares predictions from the model with the labels in the labeled dataset and gives an overall value summarizing how well the parameters really fit the data
- Objective = Minimize the loss to find the parameter values that vie the smallest loss, the best fit for the data

# The Loss Function
* *The model is a function of the inputs, while the loss is a function of the parameters of the model*
* Loss function is a parabola
* ![](<photos/Pasted image 20240115161749.png>)
	* This loss function shape is derived from our data points, won't be the same shape every time
	* Doesn't reach 0 because that would mean there is NO difference between the model and the actuals. Would be very difficult to do with most data, would usually be overfitting.
	* This is a trial method, very brute force. We want an algorithm to compute the loss function less frequently. 

# Gradient Decent: Intuition
* Analogy: 
	* Topography
	* You might not be able to see the mountain, but you can tell if you are going up or down.
		* If you are trying to get to the top, just keep going up.
		* A gradient is a vector that points in the steepest direction along each axis
* ![](<photos/Pasted image 20240115172659.png>)
* Loss = J
* Parameter = w
* Order to get this curve you have to test every parameter - super inefficient
- Process
	1. Choose some initial value for w
	2. Should we increase or decrease w?
		- If there is a positive gradient, w should be smaller
		- Negative gradient: w larger
		- The steeper the slope, the larger the step we should take
	1. ![](<photos/Pasted image 20240115173151.png>)
- Convergence: when the value of w should stop changing
- alpha = learning rate
#### Learning Rate
* Need to choose the learning rate carefully
	* If too large, J diverges
* Hyper-parameter
* You need to choose the alpha yourself

# Gradient Descent: Derivation
- Central algo relies on taking derivatives - software does all the math for you
- ![](<photos/Pasted image 20240115182419.png>)
- ![](<photos/Pasted image 20240115182929.png>)

# Gradient Descent: In Practice
#### Batch Size, Epochs, Stochastic Gradient Descent
* Stochastic Gradient Descent: Randomly chosen examples to calculate the gradient
	* One example to compute the gradient
* Gradient Descent: estimate gradient from ALL data
	* Inefficient for large datasets
	* Unnecessarily precise estimate of gradient
* Mini-batch Stochastic Gradient Descent: estimate gradient from small batches of examples
	* Used in practice
	* Batch size is a hyper-parameter
	* Referred to as SGD
* Epoch: A single pass through the data
	* Every time you try to compute the gradient with all the data
	* In a SGD, you are only getting batches, so you would need many passes before you get an epoch
		* How many epochs do you need before you reach convergence?
			* It depends: how large alpha is, what you are estimating, etc.
	* The more times you look over the training data, the more likely you are to overfit

#### Differentiable Loss Functions
* Not all functions are differentiable
* Tools like TensorFlow or PyTorch have built-in tricks
* Need to be mindful of global minimums v local minimums
	* ![](<photos/Pasted image 20240115184641.png>)
		* Run a few times if you know that you have a non-convex shaped function
		* Linear regression is convex
* ![](<photos/Pasted image 20240115184823.png>)
	- One trick is to keep track of the momentum of the gradient
		- Can look at the average of previous gradients
		- Hard to know when you are at a global min v plateau
- Notes on gradient
	- Compute a partial derivative for each parameter (holding others constant)
	- Stack the partial derivatives in a vector
	- ![](<photos/Pasted image 20240115185104.png>)
	- ^ notation
	- Vector points in the direction of steepest descent

# Review
* Model, Loss, Parameters, Objective
* What does learning by optimization mean?
	* Most successful for computers
	* Specifying loss relative to our training data and specifying how we can take derivatives to give us an algorithm that the computer can use
* Why do we need gradient descent?
	* Make process of optimization more efficient
	* Eliminates need to do exhaustive testing for ALL data
	* Which direction the next step should be
* What does a batch refer to in SGD?
	* Randomly choose little mini batches of examples from training data to compute the gradient rather than all of the examples
	* More efficient
* Do we stop SGD when the loss reaches 0?
	* No, it is possible that the loss could reach 0. But we don't expect that our model will perfectly fit. 
	* If it is 0 it probably means the data is overfit.