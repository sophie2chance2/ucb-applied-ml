# Review

- Supervised Learning
  - Input
  - Output
  - Function
  - Data
  - ![](<photos/Pasted image 20240215113848.png>)
- Predictive Generalization
  - Training Data (x, y)
  - Test Data
  - Generalization - Ability to apply the model to data outside of the training model
  - Overfitting
  - Red Dots: Test/New data, black line: linear regression model, blue line: overfit model ![](<photos/Pasted image 20240215113932.png>)
- Optimization by Gradient Descent
  - Model
  - Parameters [w0, w1]
  - Loss - Difference between the predicted values SUM(y^ - y)^2
  - Objective - Choose the parameters that reduce loss
  - ![](<photos/Pasted image 20240215114231.png>)
- Adding Complexity with Layers
  - ![](<photos/Pasted image 20240215115936.png>)
  - Adding intermediate variables, h1 and h2
  - y = b3 + w1h1 + w2h2
    - h1 = b1 + w01x1 + w02x2
  - Parameters: 9 - all the things in blue
  - Loss = yhat - y
  - Objective, the same, but more complicated because propagating loss back
- Learning Non-Linear Transformations
  - ![](<photos/Pasted image 20240215121054.png>)
- Experimental Process
  - Baseline
  - Add complexity gradually
  - Analyze errors
  - Iterate on a model or data
  - ![](<photos/Pasted image 20240215121317.png>)
  - If you over train the data, the test error rate will go up meaning that the data is overfit ![](<photos/Pasted image 20240215121514.png>)

# Nearest Neighbors

- Parametric v Non-parametric
  - Parametric: Model has learned parameters
  - Non-parametric: No learned Parameters
    - Memorizes the training data and predicts only based on what it has memorized
- Nearest Neighbor
  - Training: no training!
  - Inference
    - Find the closest training example
    - Return its label
  - ![](<photos/Pasted image 20240215123912.png>)
- Calculating Distances
  - ![](<photos/Pasted image 20240215124156.png>)
- Norm of A
  - ![](<photos/Pasted image 20240215124243.png>)
- Dot Products
  - The larger the dot product the MORE similar they are
  - ![](<photos/Pasted image 20240215140020.png>)
  - Min similarity: -1
  - Max similarity: 1
- K-nearest neighbor
  - Training: no training!
  - Inference
    - Find the closest k training examples
    - Return an average over the k labels
      - May be weighted average
  - Way of smoothing out nearest neighbor
  - Commonly compute distances using dot products
- Decision Boundaries
  - KNN produces complex decision boundaries
  - Increasing K smooths the boundary
  - ![](<photos/Pasted image 20240215151430.png>)
- Occam's Razor

  - Principle of Parsimony
    - Prefer the simplest explanation (fewest assumptions)
    - Only add complexity as needed
  - ![](<photos/Pasted image 20240215153420.png>) ![](<photos/Pasted image 20240215153456.png>)

- KNN vs FFNN Classifiers
  - KNN Approach
    - Use the input vector space
    - Many examples of each class
    - Apply the label from the closest example
  - Neural Network Approach
    - The network contorts the input vector space into a new vector space
    - A single example of each class
    - Apply the label from the closest "example"

# Decision Trees

- Baseline/ combined with Neural Networks
- KNN Pros and Cons
  - Pro
    - Predictions are easy to understand (interpretable)
    - Might work with very few labeled examples
  - Con
    - Relies on a distance metric
    - Easily fooled by outliers (noisy training examples)
    - Poor scaling (slow)
    - Poor generalization
- Good case for a decision tree:
  - ![](<photos/Pasted image 20240215160608.png>)
  - ![](<photos/Pasted image 20240215160630.png>)
    - Internal Nodes: Test the value of a feature
    - Leaf nodes: Output a predicted class or value
  - Expressiveness
    - Express any logical function of the features
    - Equivalent to a truth table for binary variables
    - ![](<photos/Pasted image 20240215193100.png>)
  - Decision Boundaries
    - Boundaries are rectangular partitions
    - Approximate diagonal lines with steps
      - Won't be a true diagonal, will just be a bunch of little rectangles
    - ![](<photos/Pasted image 20240215193223.png>)
  - Learning for Decision Trees
    - Many possible trees
      - Cannot just try every tree and see what works, we need to target it more than that
    - Balance generalization and memorization
      - Avoid learning trees that are unnecessarily deep
      - We want the shallowest possible tree that still describes the data well
    - Learned function derived from an algorithm
      - Instead of learning by optimization, we are going to describe an algo that does the learning
    - Like KNN, non-parametric

# Decision Tree Learning

- Decision Tree algorithm

  - Goal: find a (small) tree consistent with the training data
  - Note: greedy feature selection; when to stop growing?
  - ![](<photos/Pasted image 20240215194340.png>)

  1.  Check for complete purity of the labels -> would turn it into a leaf
  2.  Choose the best feature -> splits the data into true/false based on best feature
  3.  Make recursive call back to GrowTree
      - In example above blue true branch would return 1 leaf
      - Yellow example would split again

- Choosing the next feature
  - Ideal feature selection creates "pure" subsets
    - Need to measure purity
    - Left example has [0, 20] making it very pure, where as vmail plan has a 50/50 split ![](<photos/Pasted image 20240215195245.png>)
  - Interesting tidbit: ![](<photos/Pasted image 20240215195650.png>)
  - Entropy
    - Entropy is a measure of uncertainty
    - More uncertainty requires longer codes (more information)
    - ![](<photos/Pasted image 20240215195842.png>)
  - Information Gain
    - Information Gain = Entropy before - entropy after
    - Weighted by number of examples
    - ![](<photos/Pasted image 20240215200111.png>)
    - ![](<photos/Pasted image 20240215200206.png>)
    - .24 is the information gain of the international plan. This needs to be compared to others in order to be useful
  - Non-Binary Features
    - Categorical Features
      - Convert to binary
        - one-hot-encode
      - Or use higher branching factor
        - Instead of having state with 2 branches, you have state with 50 branches
    - Numerical features
      - Choose a split point (threshold)
        - (0-30), (30+)
      - Using information gain
    - Note: no normalization necessary!
  - Notes
    - On the churn metric Decision tree works much better than logistic regression because there are only about 8 features
    - Regression trees
      - Use MSE comparing average node output with the target values
        - Average number of minutes this group used
        - Instead of using Information gain, use MSE

# Trees to Forests

- Pro
  - Emulates human descriptions of decision logic
  - Arbitrary complexity (non-linear functions)
  - Minimal pre-processing and scaling
- Con
  - Greedy search is non-optimal
  - Poor generalization
- Random Forest - Build k decision trees - Must each be different - Use each tree to predict an output - Take a vote - ![](<photos/Pasted image 20240215203553.png>) - Sources of randomness: - Random sampling of training examples - Bootstrap sampling: sample training examples with replacement - Random subset of features - Only look at ⅝ of the features. Then all trees get different features to look at - Important hyperparameters: - Number of trees - Max tree depth - With one tree you don't want leaves with only one example, but with a forest it can help differentiate the trees - Each individual tree will not generalize well, but in aggregate they will generalize better - Gradient Boosting 1. First decision tree is created 2. Second decision tree looks at the errors of the first tree and accommodates for errors. Inputs are data and errors from first tree. 3. Repeat step 2.
  ![](<photos/Pasted image 20240215204720.png>) - Ensemble Methods - Bagging: train models in parallel via bootstrap sampling - Boosting: train additive models in series where each predicts the residual from previous model
  ![](<photos/Pasted image 20240215205120.png>)
