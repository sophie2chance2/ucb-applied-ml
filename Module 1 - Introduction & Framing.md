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
- ML is about learning *statistical functions* from data
	- Outputs are predictions
	- Testing is statistical and typically checks *average case*
- Supervised ML depends on labeled data
	- Behavior of the model reflects the data
	- Need separate test data to evaluate generalization
	- Model is ONLY going to reflect what is IN the data
	![[Pasted image 20240106190444.png]]
	* We have been taking about step 3 but pre-processing is SUPER important
	* START with the data THEN ask the question of what that would help you answer. Be concrete about it.
* Framing: Defining a Task
	* What are the inputs and outputs?
	* What is the labeled data?
	* How will you evaluate predictions?
	* Considerations for train/test split?
		* Is there some reason that a random split would not be a good fit for this data?
		* What are the circumstances under which that this model will be used in the real world?
	* How will your function be used?
	* What is a baseline predictor?
		* Important for collaborating the model. Is this model preforming well? What is the comparison?
**Questions:**
- What are the inputs and outputs?
- What is the labeled data?
* Considerations for train/test split?
* How will your function be used?
* How will you evaluate predictions?
* What is a baseline predictor?

### Example 1: Lung Cancer Screening
* Diagnostic screening has gotten even better than human screening
* Questions to ask ourselves:
	* What are the inputs and outputs?
		* Input: CT/Cat scan images (3Dish)
		* Output: Cancer Probability (yes/no) - prob .9
		* Output: image regions and probabilities
			* Output will probably be the most useful when used in conjunction with an expert
	* What is the labeled data?
		* Scans annotated by human experts
			* We can't say with 100% certainty yes/no, but we can use expertly annotated scans, but they could disagree
				* Have many annotations of one scan to see if they agree
					* May add a rule that says must have ___ agreement in order to use the scan
			* With multiple annotators, you must have agreement
	* Considerations for train/test split
		* No patient with scans in both train and test
			* If there are some patients with multiple scans, need to split on PATIENTS not scans
	* How will your function be used?
		* By doctors
		* By patients
			* Don't want to alarm them
		* By insurance companies
			* How will the info be used for/against patients
		* Does training population match usage population?
			* Are the predictions relevant when applied to users?
				* ie. if you train in North America and apply in Asia
	* How will you evaluate predictions?
		* Classification accuracy
			* Correct/total
		* Mistakes have 2 types
			* False positives
				* Model says "yes, cancer" - scary for patients
			* False negatives
				* Model says "no cancer" - dangerous for patients
			* Might weigh these mistakes differently based on the end users
		* Calibration
			* What does a prediction of .9 mean? -> 90% confidence that it is cancer
			* Actual likelihood v predicted 
	* What is a baseline predictor?
		* Always predict "no cancer" because the general person with a lung scan will no have cancer
		* If 1000 scans, 900 no cancer, 100 cancer, default of "no cancer" gives 90% accuracy - in that case 91% in the model needs to be calibrated
### Example 2: Sports Outcomes

- What are the inputs and outputs?
	- Inputs: Team1 and Team2
	* Outputs: win/loss (Did team 1 win?)
	* Outputs: point difference (T1points - T2points)
- What is the labeled data?
	- Previous games and the results (from the current season)
* Considerations for train/test split?
	* Use past games to predict future results (rolling predictions)
	* Need it to be predicting future uses
	* On day 30 of season, make training set of 25 days, then use the last 5 days to test
* How will your function be used?
	* Gambling: setting lines
* How will you evaluate predictions?
	* Accuracy
	* MSE
* What is a baseline predictor?
	* Team win/loss records 
	* Baseline is the total win/loss record of the teams

### Example 3: Energy Usage
![[Pasted image 20240106222854.png]]
How much energy is needed at different times of the day to make sure people's power doesn't go out.

- What are the inputs and outputs?
	- Inputs: features describing situation - date, time, weather (15 min intervals)
	- Outputs: energy usage (KW)
- What is the labeled data?
	- Previous observations
* Considerations for train/test split?
	* Rolling predictions - trying to get future predictions
* How will your function be used?
	* Coordinating mixture of power sources
* How will you evaluate predictions?
	* MSE
* What is a baseline predictor?
	* Average usage

# Review
* What is a **function**?
	* Mappings from x to y
* What is a **model**?
	* Learned function
* What is meant by **generalization**?
	* Measure of the ability of our models to be usefully applied to new data
* What is **overfitting**?
	* Condition of intricacies of the training data at the expense of generalization
	* Simple model might work better
* Why do we need a train/test split?
	* Allows us to simulate how the model will be used in the real world
	* Use test set to calculate MSE
* Why do we want a **baseline**?
	* Calibrate expectations
	* What does an MSE of 17 mean? It is relative to the baseline.