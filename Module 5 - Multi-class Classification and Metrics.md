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
- Cross Entropy Loss - General way to compute the difference or similarity between two distributions
	- True Distribution
	- Predicted Distribution
	- ![[Pasted image 20240211114337.png]]
# Network Graphs
- ![[Pasted image 20240211114740.png]]
	- Lines are the weights. In order to compute output class 0, you need 4 weights ie the green lines
	- No dependencies between xs or ys to each other. Inputs are independent, outputs are independent
	- ![[Pasted image 20240211115026.png]]
		- W input, output
	- ![[Pasted image 20240211115508.png]]
		- Results in the y values 
	- Can do with multiple batches, could be 10x4 or any size
		- ![[Pasted image 20240211115650.png]]
		- Keys that allows training to have training happen efficiently
	- Neural Networks
		- ![[Pasted image 20240211115802.png]]
		- h's are Computational nodes
		- Can create as many hidden layers as you want
		- Just a stack of logistic regression layers and you can have as many as you want

# Linear Model Limitations
```
weights, bias = model.layers[1].get_weights()
for i in range(10):
	plt.imshow(weights[:,i].reshape(28,28))
```
- first layer flattens to 784
- second layer changes to (784, 10)

![[Pasted image 20240211120342.png]]
- Scale: Purple = -.5, White = neutral, Green = .5
- ![[Pasted image 20240211120503.png]]
	- Gap between the legs
- Weaknesses
	- Sensitive to size, color, orientation
	- No concept of edges
	- No concept of structure, relation between pixels
	- Each pixel is looked at individually, no relationship to one another
- Edge Detection
	- ![[Pasted image 20240211120924.png]]
	- Find sharp changes in pixel intensity
	- This is a (spatial) gradient
	- The gradient computation can be approximated by a special computation -- a convolution
- Convolution
	- Certain type of matrix multiplication
	- Apply the kernel by placing it over the image
	- Input = Image, Kernel = formula, output = Sum (image x kernel)
	- Slide the kernel all around the image and create the output matrix
	- ![[Pasted image 20240211121644.png]]
- Convolution for Edge detection
	- Smooth by averaging it with its neighboring pixels
	- ![[Pasted image 20240211121856.png]]
```
kernel = np.array([[1, 0, -1],
					[1, 0, -1],
					[1, 0, -1]])
orig = X_train[4]
smoothed = scipy.ndimage.gaussian_filter(orig, sigma = 1)
filtered = scipy.signal.convolve2d(smoothed, filter, boundry='symm', mode='same')
```
- When applied to sentiment analysis, it is important that words are associated to one another. Like "not" cannot be looked at without using other words too.  

# Digit Classification History
- MNIST Dataset - Modified National Institutes of Standards and Technology
	- They come up with benchmarks in science and allow others to compare to it
	- Mix of Census Bureau workers (40k) and High school students (30k). High school students handwriting is much worse, but all were mixed together
	- When using dataset, think about what the source of the data was, does that apply to your project
	- Image pre-processing
		- Scaled to 20x20 pixels
		- centered in 28x28 pixels (center of mass)
		- Smoothed (anti-aliasing) producing grey-scale values
	- Other methods that have worked, usually better than linear models ![[Pasted image 20240211131043.png]]
	- Mail Sorting
		- Recognizing zip codes has extra challenges
			- Locating the zip code span (within the address)
			- Size and spacing variability
			- Separation between digits
		- Needs to have high precision, when not sure sends to a human