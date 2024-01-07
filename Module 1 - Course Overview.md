### Machine Learning is going Mainstream
* "Data is the new Oil"
* "AI is the new electricity"
* "Privacy is the new luxury"
* "Machine Learning is the future"
* Market Size is over 10 billion $
* Growing increasingly important in the economy
* *Comes with responsibility*

### Course Goals
- Practical introduction to the machine learning field
- Building blocks and theory or neural networks
	- USING programming tools like Tensorflow
	- Following "mainstream" of machine learning
- Learning how to stay current as the field changes

### Structure of the Course
* Weekly notebooks are the interactive textbook of the course
	* Jupyter notebooks - need to install libraries
	* Google Collab - everything is installed
* Weekly modules and lectures

### Course Work
* Weekly notebook exercises
* Final Project
	* Small groups
	* Kaggle competitions
	* Run experiments
	* Write a summary report and present to class

### Machine Learning and Artificial Intelligence
- "Programming agents by hand can be very tedious; some more expeditious method seems more desirable" - Turing
- Machine Learning & AI - often show overlapping meanings - both replicating human, calculating based on sensory input, using human intelligence to produce other intelligence
- Ngram Viewer
	- Ngram - sequence of n words that we treat as a unit
![[Pasted image 20240105162128.png]]
*Number of times ML or AI appeared divided by the total number of words*
- Neural networks were an ancient concept that worked with the punch card era of computers
	- Stars aligned and AI took off: increase processing power
- Now: 
	- Phone recognizes voice
	- Face detection
### Artificial Intelligence
- Decision making under uncertainty
- Computational rationality
### Machine Learning
* Subfield of AI
* Finding patterns in data
* Learned functions
	* Inputs and outputs
* Machine learning has expanded to cover most of AI
### Deep Learning
* Subfield of Machine Learning
* Deep learning has expanded to cover most of ML

### Autonomous Driving
- Tasks in order of difficulty
	- Input -> output
	1. Object identification
		1. Image -> label
	2. Object detection
		1. Image -> Object bounding boxes
	3. Object tracking/prediction
		1. Video -> Moving bounding boxes
	4. Route Planning
		1. Video, Map, Coordinates -> Actions
	5. Fully autonomous driving
		1. Video, Map, Coordinates, Ethics -> Actions
- These are all classical machine learning - pattern recognition

#### Supervision
- Supervised learning (inputs, labels)
	- At the heart of all machine learning
- Unsupervised learning (inputs)
- Reinforcement learning (inputs, eventual rewards)
	- indirect supervision
	- Child points to a dog and says "cat" then mom/dad corrects

# What is a function?
* Takes some input (x) applies a transformation f(x) and creates an output y
* Mapping between sets, for each input there is one corresponding output item
* One value of x cannot map to multiple ys, but y can map to many xs
* Circle is not a function
* Input/output can be many different datatypes
* *Deterministically* = always
### Function Testing
* Similar to testing any function you code
* need to check the yi against the yi^ to know how far off predictions were, and if the model is running well
* Results in Mean Squared error - common for regression problems
 ![[Pasted image 20240105174832.png]]

### Generalization
* The dataset for training and testing cannot be the same data
* Learning = training
* Both the blue and the black lines are possible
 ![[Pasted image 20240106185046.png]]
 * The blue model goes through every single point making the Mean Squared Error (MSE) = 0 
 * The black model will have a higher MSE
	 * Does that make it better?
* When testing data is added, how do each of the models preform?
	* Calculating the MSE on the test data is critical - must be different from training
* Generalization - Capability to learn from some examples in a way that transfers to new examples
	* Single term that summarizes the goal of supervised machine learning
* Simulate generalization by splitting data into train and test
	* Could be a random split 
	* Could depend on other properties of the data
	* 80% train, 20% test
* Blue model (above) is an example of overfitting
	* **Ocram's razor** - All things being equal, the simpler explanation is better
* Overfitting - it has learned to fit the training model too well, at the expense of generalization

### ML Framing
- Logical functions 
	- Outputs are deterministic
	- Testing is logical and typically checks extreme cases
- ML is about learning *statistical functions* 