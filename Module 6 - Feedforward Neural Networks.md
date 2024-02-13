# The XOR Problem

![[Pasted image 20240213083431.png]]

### Logical Operators

![[Pasted image 20240213083822.png]]
![[Pasted image 20240213083910.png]]

### Constructing XOR

![[Pasted image 20240213084620.png]]

- XOR can be created using the combination of 3 linear functions: OR, NAND, AND
- The last column is XOR
- ![[Pasted image 20240213084800.png]]
- ^ relates to last weeks class, showing hidden layers in Neural Net

### Learning XOR

Data

```
X = np.array([[0, 0], [0, 1], [1, 0], [1, 1]]) # grid
Y = np.array([0, 1, 1, 0]) # Associated labels
```

![[Pasted image 20240213085114.png]]

Model

```
def build_xor_model(hidden_layer_sizes = []):
	model = keras.Sequential()
	# This loop is the hidden layer
	for hidden_layer_size in hidden_layer_sizes:
		model.add(keras.layers.Dense(units=hidden_layer_size, activation='tanh')) # tanh has range of -1, 1
	model.add(keras.layers.Dense(units=1, activaton='sigmoid')) # single prediction, positive or negative
	model.compile(loss='binary_crossentropy', optimizer=keras.optemizers.SGD(learning_rate=1))
	return model
```

### Linear Model

```
xor_model = build_xor_model(hidden_layer_sizes=[])
history = xor_model.fit(x=X, y=Y, epochs = 500, batch_size=4)
losses = history.history['loss']
plt.plot(losses)
```

### 1 Hidden Layer

```
xor_model = build_xor_model(hidden_layer_sizes=[2])
history = xor_model.fit(x=X, y=Y, epochs = 500, batch_size=4)
losses = history.history['loss']
plt.plot(losses)
```

![[Pasted image 20240213092526.png]]

| x1 | x2 | h1 | h2 | y |
| ---- | ---- | ---- | ---- | ---- |
| 0 | 0 | .9 | .9 | 0 |
|  |  |  |  | 1 |
|  |  |  |  | 1 |
|  |  |  |  | 0 |
- Not necessarily one solution, there is a range of different solutions
- Loss surface has no global minimum because there are many valid solutions

### Lessons of XOR
- XOR function has no linear model solution
- Can compose simple (linear) functions to solve it
- A neural network can learn a solution
- Parameter initialization can be important
- Complex loss landscape with many possible solutions

# Back Propagation
![[Pasted image 20240213101824.png]]
- Gradient Descent
	- Make Predictions - forward pass
	- Compute the loss (compare true y to predicted y)
	- Compute the gradient of the loss
		- How is each parameter implicated in the loss
	- How to compute gradients with more than 1 layer?
- Small changes
	- A small change to any parameter in a neural network should yield a small change in the output
- Chaos
	- Chaotic systems like weather tend to violate small changes requirement
	- Tiny changes lead to large changes in the model
- Non-Chaotic Behavior
	- Limited non-linear functions
		- Large changes can be turned into small changes
	- Differentiable (smooth) loss
		- no jumpy parts, everything will be smoothed out
	- Each unit is a function of units in the previous layer
		- Directly helps us compute derivatives

### Back Propagation - Part 2
- A bad training algorithm
	- Try increasing/decreasing b1 by a small amount and observe the change in the predicted value of y
	- Update b1 so that the predicted y is closer to the true y
	- Repeat this process for all parameters
	- WHY ITS BAD:
		- 1. horribly inefficient - need to do a different forward pass every time you make an adjustment, estimating loss each time
		- 2. We want to change all of the parameters together, not individually
## Chain Rule
![[Pasted image 20240213102247.png]]
- Neural Networks are composite functions
- ![[Pasted image 20240213102700.png]]
$$h(x) = f(g(x))$$
 $$ a_1 = g(x) = w_0x $$
 
$$ a_2 = f(g(x)) = w_1a_1 $$
 
$$ a_2 = w_1(w_0x)
$$

![[Pasted image 20240213102717.png]]
![[Pasted image 20240213103412.png]]
![[Pasted image 20240213104759.png]]
- Libraries with automatic Differentiation
	- TensorFlow, PyTorch, etc.
	- User constructs a computation graph
	- System computes gradients
	- Updates parameters
	- and provides all kinds of tools
	- Don't need to write code for back propagation

# Neural Network Details
- Non-linear functions
	- If f is a linear function and g is a linear function, then their composition f(g(x)) is also a linear function
	- These two chains do the same thing ![[Pasted image 20240213110350.png]]
	- Without non-linear activations, all neural network functions could be reduced to a single layer
![[Pasted image 20240213110453.png]]
		- Derivative of ReLU is trivially easy, 0 or 1
- Optimizers
	- SGD
	- ![[Pasted image 20240213110716.png]]
	- Learning rate schedules
		- choose a learning rate that decays and gets smaller as you continue training
	- Momentum
		- gradients are a combination of gradients before and current gradient
	- Adagrad & Adam
		- Adagrad - Dynamically selects and adjust learning rates of each parameter
		- Adam - Combines adagrad and momentum
	- Distributed optimizers
		- send data to different machines and have each of them make predictions

# Biological Inspiration
Hubel & Wiesel Cat Experiment 1959