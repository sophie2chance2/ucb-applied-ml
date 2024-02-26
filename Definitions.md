
| **Word** | **Definition** | Link |
| ---- | ---- | ---- |
| Ngram | Sequence of n words that we treat as a unit | [[Module 1 - Introduction & Framing#Machine Learning and Artificial Intelligence]] |
| Machine Learning | Algorithms improve through experience with data, distinct for its adaptability | [[Module 1 - Introduction & Framing#Machine Learning]] |
| Artificial Intellegence | Encompasses any technique enabling machines to mimic human behavior, broader than machine learning. | [[Module 1 - Introduction & Framing#Artificial Intelligence]] |
| Deep Learning | Specialized in processing large, complex datasets using multi-layered neural networks, a deeper subset of machine learning. | [[Module 1 - Introduction & Framing#Deep Learning]] |
| Supervised Learning | Relies on labeled datasets to train algorithms, making it specific for prediction based on known examples. | [[Module 1 - Introduction & Framing#Supervision]] |
| Unsupervised Learning | Identifies patterns or structures in unlabeled data, unique for its ability to find hidden insights without guidance. | [[Module 1 - Introduction & Framing#Supervision]] |
| Reinforcement Learning | Involves learning to make sequences of decisions by trial and error, distinct for its focus on sequential decision-making and reward-based | [[Module 1 - Introduction & Framing#Supervision]] |
| Function | Takes some input (x) applies a transformation f(x) and creates an output y | [[Module 1 - Introduction & Framing#What is a function?]] |
| Generalization | Capability to learn from some examples in a way that transfers to new examples | [[Module 1 - Introduction & Framing#Generalization]] |
| Ocram's Razor | All things being equal, the simpler explanation is better | [[Module 1 - Introduction & Framing#Generalization]] |
| Overfitting | The model has learned to fit the training model too well, at the expense of generalization | [[Module 1 - Introduction & Framing#Generalization]] |
| Calibration | Adjusting a model's output to ensure its predicted probabilities accurately reflect the true likelihood of an event or outcome | [[Module 1 - Introduction & Framing#Example 1 Lung Cancer Screening]] |
| Epoch | A single pass through the data |  |
| Batch | A set of data points processed together in a machine learning algorithm. |  |
| Fold | A subset used in cross-validation to validate a model during training. |  |
| Training data | Data used to train a machine learning model. |  |
| Loss curve | A graph showing the model's loss over time during training. | [[Module 2 - Linear Regression & Gradient Descent#The Loss Function]] |
| Gradient Descent | An optimization algorithm to minimize the loss function in learning. |  |
| Learning Rate | A parameter that determines the step size during gradient descent. | [[Module 2 - Linear Regression & Gradient Descent#Learning Rate]] |
| Convergence | The process of an algorithm approaching a stable solution. | [[Module 2 - Linear Regression & Gradient Descent#Gradient Decent Intuition]] |
| Divergence | When an algorithm moves away from a solution, often due to high learning rate. |  |
| Hyper-parameter | A parameter set prior to the learning process and not learned from data. |  |
| Stochastic Gradient Descent | A variant of gradient descent using a single data point at each iteration. | [[Module 2 - Linear Regression & Gradient Descent#Gradient Descent In Practice]] |
| Non-Convex | A function with multiple local minima and maxima. | [[Module 2 - Linear Regression & Gradient Descent#Differentiable Loss Functions]] |
| Model | An abstract representation learned from data to make predictions. |  |
| Loss | A measure of how far a model's predictions are from the actual values. | [[Module 2 - Linear Regression & Gradient Descent#The Loss Function]] |
| Parameters | Variables in a model that are learned from the training data. |  |
| Objective | The goal or function that a machine learning model is trying to optimize. |  |
| Feature Vector | An array of numerical features representing an instance in data. |  |
| Z-score scaling | Standardization of data by subtracting mean and dividing by standard deviation. |  |
| Bucketing | Grouping continuous variables into discrete categories. |  |
| Log scaling | Applying logarithmic transformation to scale data. | [[Module 3 - Feature Engineering#Feature Engineering]] |
| One-hot vectors | Binary vectors representing categorical data, with exactly one high bit. |  |
| Multi-hot vector | Binary vectors representing categorical data, with multiple high bits. |  |
| Dense Representation | A data representation where most elements are non-zero. |  |
| Sparse Representation | A data representation mostly made up of zeros. |  |
| Sigmoid activation | An S-shaped function mapping inputs to values between 0 and 1. |  |
| Softmax normalization | Scales a set of scores to a multinomial probability distribution | [[Module 5 - Multi-class Classification and Metrics#Multiclass Classification]] |
| Cross Entropy Loss | General way to compute the difference or similarity between two distributions | [[Module 5 - Multi-class Classification and Metrics#Multiclass Loss]] |
| Convolution |  | [[Module 5 - Multi-class Classification and Metrics#Linear Model Limitations]] |
| Parametric | Model has learned parameters |  |
| Non-parametric | No learned parameters | [[Module 7 - KNN, Decision Trees, and Ensembles#Nearest Neighbors]] |
| Internal Nodes | Test the value of a feature | [[Module 7 - KNN, Decision Trees, and Ensembles#Decision Trees]] |
| Leaf nodes | Output a predicted class or value | [[Module 7 - KNN, Decision Trees, and Ensembles#Decision Trees]] |
| Bagging | Train models in parallel via bootstrap sampling | [[Module 7 - KNN, Decision Trees, and Ensembles#Trees to Forests]] |
| Boosting | Train additive models in series where each predicts the residual from previous model | [[Module 7 - KNN, Decision Trees, and Ensembles#Trees to Forests]] |
| Training example | A row in a table representing the dataset and synonymous with an observation, record, instance or sample |  |
| Training | Model fitting for parametric models similar to a parameter estimation |  |
| Feature | A column in a data table or data design matrix |  |
| Target | Synonymous with outcome, output, response variable, dependent variable, label, and ground truth |  |
| Loss Function | ie. error function, loss measured for a single datapoint |  |
| Cost Function | Loss over the entire dataset |  |
| instance based learning | Memorize the training dataset |  |
| GMM Generative Process |  | [[Module 8 - Unsupervised Learning k-means and PCA### Gaussian Mixture Models (GMMs)]] |


| Method | Notes | Learning Type (supervised/reinforcement/ect) | Parametric | Normalization Necessary? | Example used in Class |
| ---- | ---- | ---- | ---- | ---- | ---- |
| Logistic Regression |  |  | Yes | Yes |  |
| Decision Tree | Works well when there are less features, but the features tell a lot about the final label |  | No | No | Churn |
| Neural Network |  |  |  |  |  |
| KNN |  |  | No | Yes |  |
|  |  |  |  |  |  |

# Supervised Learning
![photos/Pasted image 20240109170956.png]
