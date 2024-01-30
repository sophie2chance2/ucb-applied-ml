Review:

| Term | Associations |
| ---- | ---- |
| Features | Input (x) |
| Labels | Output (y) |
| Train/Test split | Data |
| Normalization | Input |
| Parameters | Model |
| Loss | All of the above |
# Classification
![[Pasted image 20240128195529.png]]
- Could we model this with linear regression?
	- Yes, but it wouldn't be very good
- Does it make sense?
	- No, not really. Values should be 0 or 1.
- Binary Classification: labels are in {0, 1}

### Binary Classification
- Binary Classification: labels are in {0, 1}
- Examples:
	- Spam classification
	- Fraudulent transactions
	- Speaker identification - security
	- Cat detection

# The Logistic Function
aka Sigmoid function
![[Pasted image 20240128200310.png]]
- Initially used for population. First grows exponentially and then as outside constraints occur, it flattens
- What is the range for x?
	- Unbounded
- What is the range for y?
	- 0, 1
	- Scales to the probabilities range
### Applied to Binary Classification
![[Pasted image 20240128200710.png]]

Linear Regression: $\hat{y} = xw^T + b$
x $[x_1, x_2, ...]$
w $[w_1, w_2, ...]$
$xw^t = x_1 w_1 + x_2 w_2$

Logistic regression: $$
\hat{y} = \frac{1}{1 + e^{-(xw^T+b)}}
$$
- This is an application of the sigmoid function to the linear regression model
![[Pasted image 20240128201541.png]]
- b = midpoint

# Classification Example
- Passing Grade Classifier
![[Pasted image 20240129221734.png]]
- Fully specified model:
	- ![[Pasted image 20240129222118.png]]
	- 0 hours:  $$ \frac{1}{(1+e^{-3})} = 0.047 $$
	- 2 hours: $$ \frac{1}{(1+e^{1})} = 0.269 $$
		- "If you study for 2 hours, then you have a 27% chance of passing the class"
	- 4 hours: .73
	- 8 hours: .993

# The Decision Boundary

- Logistic regression predicts a probability
- Example:
	- ![[Pasted image 20240129223016.png]]
- Use a threshold to get a label
	- y' >= 0.5 -> class 1
	- y' < 0.5 -> class 0
- ![[Pasted image 20240129223231.png]]
	- Accuracy = correct/total
- ![[Pasted image 20240129223913.png]]

# Logistic Loss

- How can we use the error rate as our loss function?
	- ![[Pasted image 20240130080952.png]]
		- You are either right or wrong. Either 0 or 1.
- ![[Pasted image 20240130081020.png]]
- $$ \text{LogLoss} = \frac{1}{m} \sum_{i} -y_i \log(\hat{y}_i) - (1 - y_i)\log(1 - \hat{y}_i) $$
### Formula Broken Down
- Multiply the true label, by the log of the predicted label. Works when y_i = 1 $$y_i \log(\hat{y}_i)$$
- Active when y_i = 0 $$ - (1 - y_i)\log(1 - \hat{y}_i) $$
- ![[Pasted image 20240130082443.png]]

# Gradient Descent with Log Loss

- ![[Pasted image 20240130082636.png]]
- Log loss is differentiable
- and convex
	- We will get to the global minimum
- and the gradient computation is exactly the same as linear regression with squared error loss
### Taking the derivative: 
![[Pasted image 20240130083102.png]]
![[Pasted image 20240130083136.png]]
