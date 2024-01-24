[Course Framing](https://docs.google.com/document/d/1jUDR61z1pCCXnpr2CbXJXywe45MrSabPuijx2BPO0Sg/edit?pli=1)

[FFN Code Example](https://colab.research.google.com/drive/1qiMwu8NNn5DLCIP_FUWZ1lLd-ylbNUQg?usp=sharing)

XOR problem is the purest definition:
X = 
[0, 0, 1],
[0, 1, 1], 
[1, 0, 1],
[1, 1, 1]

y = 
[0]
[1]
[1]
[0]

2007-2015
- Make synthetic columns by defining relationships and creating new features
	- Ex. If you have a clamming license, then you have a fishing license. Or if you have a fishing license, you are more likely to have a boat. 
Deep learning
- You do not have to create the features, the model will create those relationships for you

---
# Fully built out Neural Net
Mathematical way of looking at it

```
# https://iamtrask.github.io/2015/07/12/basic-python-network/

  

syn0 = 2*np.random.random((3,4)) - 1

syn1 = 2*np.random.random((4,1)) - 1

for j in range(1000):

	l1 = 1/(1+np.exp(-(np.dot(X,syn0)))) 
	
	l2 = 1/(1+np.exp(-(np.dot(l1,syn1))))
	
	l2_delta = (y - l2)*(l2*(1-l2))
	
	l1_delta = l2_delta.dot(syn1.T) * (l1 * (1-l1))
	
	syn1 += l1.T.dot(l2_delta)*.01  #.01 is the learning rate
	
	syn0 += X.T.dot(l1_delta)

print(l2)
```

### Sigmoid Activation
syn0 = activations of the neural net
- Initialized automatically by TensorFlow or other packages
- Gives us ability to map something that is not just linear

l1 = 1/(1+np.exp(-(np.dot(X,syn0))))
- Compare to going to lunch with co-workers:
	- Weigh based on what matters most to you, yummy, distance, price
	- Weigh based on how much your co-worker will complain
- If you have stacked dot products you can just multiply the grouped

### ChatGPT explanation of Code

This code snippet is implementing a simple neural network with two layers, using Python and NumPy. Let's break down each part of the code:

1. **Initialization of Weights (syn0 and syn1):**
    
    - `syn0 = 2*np.random.random((3,4)) - 1`: This line creates a 3x4 matrix of random weights. The weights are initialized randomly between -1 and 1. This matrix (`syn0`) represents the weights between the input layer and the first hidden layer of the neural network.
    - `syn1 = 2*np.random.random((4,1)) - 1`: Similarly, this line creates a 4x1 matrix of random weights. These weights (`syn1`) are for the connections between the first hidden layer and the output layer.
2. **Training Loop:**
    
    - The `for j in range(1000):` loop iterates 1000 times. Each iteration represents one step in the training process of the neural network.
3. **Forward Propagation:**
    
    - `l1 = 1/(1+np.exp(-(np.dot(X,syn0))))`: This is the forward propagation for the first layer. It calculates the output of the first hidden layer (`l1`). The `np.dot(X, syn0)` performs the matrix multiplication between the input data `X` and the weights `syn0`. The result is then passed through a sigmoid activation function.
    - `l2 = 1/(1+np.exp(-(np.dot(l1,syn1))))`: This line calculates the output of the second (output) layer (`l2`). It's similar to the previous step but uses the output of the first layer `l1` and the weights `syn1`.
4. **Backpropagation:**
    
    - The backpropagation algorithm is used for training the neural network by adjusting the weights in response to the error in the output.
    - `l2_delta = (y - l2)*(l2*(1-l2))`: This line calculates the error in the output (`y - l2`) and multiplies it with the derivative of the sigmoid function (`l2*(1-l2)`) to get the delta for the second layer.
    - `l1_delta = l2_delta.dot(syn1.T) * (l1 * (1-l1))`: It calculates the delta for the first layer. It takes the delta from the second layer, propagates it back across the weights `syn1`, and multiplies it with the derivative of the sigmoid function for `l1`.
5. **Updating the Weights:**
    
    - `syn1 += l1.T.dot(l2_delta)*.01`: This updates the weights of the second layer (`syn1`). It uses the transpose of `l1`, the delta of `l2`, and a learning rate (0.01 in this case).
    - `syn0 += X.T.dot(l1_delta)`: Similarly, this line updates the weights of the first layer (`syn0`).
6. **Output:**
    
    - `print(l2)`: Finally, the output of the network after training (`l2`) is printed.

In summary, this code is a basic example of a feedforward neural network with backpropagation. It doesn't include some complexities of real-world neural network implementations, like batching or additional layers, but it captures the fundamental concepts of neural network training.

---

# Tensor Flow Example
Same problem as above ^^

```
import tensorflow as tf

  
model = tf.keras.Sequential([

tf.keras.layers.Dense(4, activation='sigmoid', input_shape=(3,)),

tf.keras.layers.Dense(1, activation='sigmoid')])

model.compile(optimizer=tf.keras.optimizers.SGD(learning_rate=0.1), loss='mean_squared_error')

model.fit(X, y, epochs=10000, verbose=0)

model.predict(X)
```


### ChatGPT Explanation 
  
This code snippet is an implementation of a simple neural network using TensorFlow and Keras, which are popular libraries for machine learning and deep learning. The network is designed to perform some form of regression or binary classification (since it uses sigmoid activation functions and mean squared error loss). Here's a breakdown of what each part of the code does:

1. **Import Libraries:**
    
    - `import tensorflow as tf`: This imports TensorFlow, a powerful library for numerical computing and machine learning.
    - `import numpy as np`: This imports NumPy, a library for scientific computing in Python.
2. **Model Creation:**
    
    - `model = tf.keras.Sequential([...])`: This line creates a sequential model. Sequential models in Keras are linear stacks of layers. The code defines the architecture of the neural network.
        - `tf.keras.layers.Dense(4, activation='sigmoid', input_shape=(3,))`: This adds the first dense (fully connected) layer with 4 neurons. The `activation='sigmoid'` specifies that a sigmoid activation function will be used. The `input_shape=(3,)` parameter indicates that the input layer expects arrays with a shape of `(3,)`, meaning there are 3 features in the input data.
        - `tf.keras.layers.Dense(1, activation='sigmoid')`: This adds a second dense layer, which is the output layer of the network, with 1 neuron and a sigmoid activation function.
3. **Model Compilation:**
    
    - `model.compile(...)`: This configures the model for training.
        - `optimizer=tf.keras.optimizers.SGD(learning_rate=0.1)`: It uses Stochastic Gradient Descent (SGD) as the optimization algorithm with a learning rate of 0.1.
        - `loss='mean_squared_error'`: The loss function used is the mean squared error, which is common for regression tasks.
4. **Training the Model:**
    
    - `model.fit(X, y, epochs=10000, verbose=0)`: This line trains the model on the data `X` and labels `y` for 10000 epochs. The `verbose=0` argument hides the training output (progress bar, loss, etc.).
5. **Making Predictions:**
    
    - `model.predict(X)`: After training, this line is used to generate predictions based on input data `X`.

In summary, the code defines, compiles, and trains a simple neural network using TensorFlow and Keras, and then uses the model to make predictions. The specific nature of the problem being solved (regression or binary classification) depends on the data (represented by `X` and `y`) and how the outputs are interpreted.

---
# Torch

```
import torch
import torch.nn as nn
import torch.optim as optim
import numpy as np

# adjust below to be three values and using orginal
x_data = torch.tensor([[0, 0], [0, 1], [1, 0], [1, 1]], dtype=torch.float32)
y_data = torch.tensor([[0], [1], [1], [0]], dtype=torch.float32)

class XORModel(nn.Module):

	def __init__(self):
		super(XORModel, self).__init__()
		self.fc1 = nn.Linear(2, 2)
		self.fc2 = nn.Linear(2, 1)
		self.sigmoid = nn.Sigmoid()
	
	def forward(self, x):
	
		x = self.sigmoid(self.fc1(x))
		x = self.sigmoid(self.fc2(x))
		return x

model = XORModel()
optimizer = optim.SGD(model.parameters(), lr=0.1)

# Train the model
for epoch in range(100):
	optimizer.zero_grad()
	output = model(x_data)
	loss = nn.MSELoss(output, y_data)
	loss.backward()
	optimizer.step()

# Test the model
predictions = model(x_data).detach().numpy()
rounded_predictions = np.round(predictions)
print('Predictions:')

for i in range(len(x_data)):
	print(x_data[i].numpy(), rounded_predictions[i])
```

---
- Tensor flow
	- If you have a GPU cluster
	- At scale at a big company
* Pytorch
	* Development time
	* Flexibility
	* Smaller team
	* Can make dynamic changes 
	* More in front of innovation
* Math - Neural Net
	* Wouldn't be used in business
	* https://numerical.recipes/ - Book on how to make these
	* Want to get down to the lowest level
	* 10 year commitment to learn
	* https://quantumalgorithmzoo.org/ - Descriptions of algos
* If you learn one you can learn the other pretty easily
- Building from scratch includes pytorch/tensor flow
- Advice from google on how to choose an optimizer: https://github.com/google-research/tuning_playbook/blob/main/README.md


- Understanding the shape is important and will mess up your code

Live coding
- CMD + R source - find the most recent thing that you ran in terminal
- Open python in terminal and shift + ___ to copt over to terminal
- pdb; pdb.s