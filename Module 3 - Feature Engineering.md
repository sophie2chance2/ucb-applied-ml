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