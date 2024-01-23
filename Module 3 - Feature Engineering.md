# Gradient Descent Review
- Metaphor: Descending in the dark
	- Minimizing loss function is like descending a mountain in the dark. Stick foot out until it feels like the direction is down
		- Take a step in the steepest direction, thats following the gradient
	- Usually not in 3D, we usually have many dimensions making the metaphor not as strong
- Procedure
	1. Start with labeled data (inputs, outputs)
		- Shoe size & height
		- ![[Pasted image 20240121190002.png]]
	2.  Linear Regression that seeks to fit a line that minimizes loss
		- ![[Pasted image 20240121190101.png]]
	3. Calculate the loss (MSE)
		- ![[Pasted image 20240121190200.png]]
	4. Update w0 and w1
		- ![[Pasted image 20240121190633.png]]
	5. Repeat to fit the data better and better until convergence

# Multivariate Regression
- More than just a single feature
- Matrix Representation
	- Single variate: ![[Pasted image 20240121192815.png]]
		- y^ ~ predicted values for y
			- This matrix says "let me get all of the predicted values at once for all of the values of x in the dataset"
		- y^ = product of 2 matrices (X * W *transposed*)
		- **Every row is an example**
		- **Every column is a feature**
			- Column 0 is a column of 1s -> allows us to express the intercept/bias term as if its a feature
				- f(x) = w0x0 + w1x1
					- ^ x0 is a "fake feature"
		- W matrix (w0 & w1)
			- learned parameters
			- (2, 1) matrix size
		- (m, 2)(2, 1) -> (m, 1)
			- We want "m predictions" -> one prediction for every example
		- Example: ![[Pasted image 20240121194011.png]]
	- Two Features
		- Just adding another column to the matrix ![[Pasted image 20240121194049.png]]
		- x0, x1, x2
		- matrix sizes: (m, 3)(3, 1) -> (m, 1)
	- N features
		-  ![[Pasted image 20240121194219.png]]
		- matrix sizes: (m, n)(n, 1) -> (m, 1)
	- ![[Pasted image 20240121194421.png]]
		- Predictions size: (m, 1)
		- Differences size: (m, 1)
		- Gradient size: (m, 1)
		- Gradient is an average over all of the examples

# Features Overview
- Data needs to be numeric
- Need to take raw data and transform it into a feature vector ![[Pasted image 20240121195251.png]]
- Each row is an example
- Numeric values may or may not have a linear relationship with output
- Feature Engineering
	- Cleaning raw data
		- Handle missing values, outliers
	- Produce numeric features
		- Covert categories, text, images, audio
		- Transform to similar scales
	- Combine to form new features
	- Keep only useful features

# Feature Engineering

- Goals of example:
	- Predict price as accurately as possible
		- For cars that have not been seen before
	- Using numeric features
		- You can feed to a model
	- A minimal set of features
		- Is more efficient 
		- And easier to interpret
- Anscombe's Quartet
	- Need to be very familiar with YOUR data and how it should be grouped/edited ![[Pasted image 20240122175931.png]]
		- All of these have the same regression line, but VERY different data. 
		- Outliers and shapes can make a really big difference
- Missing features
	- Raw data can be missing information
		- Remove rows with missing value
		- Replace missing values with an average
		- Special "missing" value
- Transforming Features
	- Linear regression assumes linear relationships
- Log Scaling
	- Many natural distributions are exponential
		- Like popularity
		- Lots of ratings for the *head*
		- Few ratings for the *tail*
		- ![[Pasted image 20240122231214.png]]
- Z-Score Scaling
	- Move distribution to have mean = 0, variance = 1
		- Subtract the mean
		- Divide by the standard deviation
		- ![[Pasted image 20240122231305.png]]
	- Allows you to have all of your features in the same range
- Bucketing
	- Some distributions are more complex (multimodal)
	- ex. lat/long tells you what city
	- ![[Pasted image 20240122231453.png]]
	- Let the model learn weights based on buckets, split up into 10 different buckets
	- Even Space Bucketting ![[Pasted image 20240122231537.png]]
	- Bucketing - Quantities ![[Pasted image 20240122231638.png]]
- Categorical Features
	- ex.
		- All-wheel drive [true, false] -> [1, 0]
			- 1 is indicator
		- Color [black, white, red] -> [0, 1, 0]
		- Make [ford, bmw, audi, honda] -> [0, 0, 0, 1]
			- One-hot vector
	- Dense Representation: [1, 0, 0, 1, 0, 0, 0, 0, 1]
		- Combination of each of the above
		- Need to know what each index represents
	- Sparse Representation: [0, 2, 7]
		- Index of each of the 1s
- Feature Scaling
	- Suppose each feature has a different scale
	- ![[Pasted image 20240123075112.png]]
	- [horsepower, peak-rpm, city-mpg] = [27, 195, 1.8]
		- Usually choose 1 learning rate that applies to all which won't work if they are on different scales
		- Scale to the largest feature (peak-rpm)
		- Use mean and var to scale
	- Want to put all of the features into a similar scale
	- Helps so that the gradient is comparable
- Feature Crosses
	- Consider the relationships
		- HP vs price - Linear
		- Seats vs price - Linear
		* (HP x Seats) vs Price - Non-linear U shape
* Feature Selection
	* We don't want a model with a bunch of random features
	* Only useful features
		* Bottom up: add features one at a time
			* Start with no features
			* Try each feature alone and see which of the features improves things the most
		* Top-down: remove features one at a time
