- Entry point for deep learning
- Why and how you can build these models easily
- Jobs want to know if you can do deep learning
  - Hire you for skills in deep learning
  - In job do SQL queries
- Exam, 10 homeworks, final projects
- [Course Framing](https://docs.google.com/document/d/1jUDR61z1pCCXnpr2CbXJXywe45MrSabPuijx2BPO0Sg/edit?pli=1)
- [YouTube Channel](https://www.youtube.com/@santerreai)
- Best way to contact: Slack

### [3 Matrix Structures](https://www.youtube.com/watch?v=UckHb9QfcqY)

- Main goal of statistics:
  - What is the smallest number of rows required to say x is related to y?
  - Problems
    - Expensive to have more rows/columns
    - When columns > rows, cannot calculate p value
- Machine Learning
  - limited number of rows, lots of columns
- Deep learning
  - Lots of columns

### [Example](https://colab.research.google.com/drive/1dXyE15qbFU_DvFouBH_cYNUvgjPBU4HT?usp=sharing)

- Linear Regression "The Old Way"
  - Can say explicitly how much each feature contributes (transparent)
- Random Forest "The New Old Way"
  - Function calls
  - Don't need to know whats going on under the hood
  - Directionally know features (moderately transparent)
- Deep Learning "The Current Fancy Way"
  - Tensor flow is best at scale - need 2-3 optimizers
  - PiTorch is good for smaller scale
  - Tensor flow <> Torch are pretty interchangeable
  * need to design the actual structure of each layer
  * Don't know anything about how the features are contributing (opaque)
  * Should start with a baseline - start with a random forest and the compare to the deep learning solution
  * Often memorize feature spaces - looks like overfitting

### Overfitting ![](<photos/Pasted image 20240109165920.png>)

- Separate out the columns, don't learn anything from those, test, then train and test another "fold"
- ![](<photos/Pasted image 20240109170406.png>)
- You stop training when the loss curve starts to flatten out.
  - Test on hold out set - hold out set is the % that you will use
- ![](<photos/Pasted image 20240109170522.png>)
- There are 3 separations: training, testing, holdout set

![](<photos/Pasted image 20240109170956.png>)

Clusters are _linearly separable_

![](<photos/Pasted image 20240109171249.png>)
![](<photos/Pasted image 20240109171350.png>)
Average is when the left equals the right, same things happens when fitting.
Add them up and divide -> closed form solution

### Learning Objectives

- Why we are moving from stats -> ML -> Deep learning
- Exposure to Deep learning
  - Highly structured, only changing a small portion

Other Notes

- Numpy
  - Good at matrix algebra
  - Much faster because it is done in C
- Pandas
  - Never designed for optimization
  - "Gateway drug for python"
  - Makes your life easier, not the software run faster

Follow up to do

- Super smart guys to read about:
  - Noam Chomsky
  - Andrew Ang
- Transparency
  - **[Norvig_vs_Chomsky debate](http://norvig.com/chomsky.html)**
  - **[The Great AI debate in 2017](https://www.youtube.com/watch?v=93Xv8vJ2acI&ab_channel=TheArtificialIntelligenceChannel)**
