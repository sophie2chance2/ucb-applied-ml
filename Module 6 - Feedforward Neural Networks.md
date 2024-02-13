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

| x1 | x2 |  |  |  |
| ---- | ---- | ---- | ---- | ---- |
| 0 | 0 |  |  |  |
