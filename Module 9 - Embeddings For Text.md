# Text Classification
- Text -> number of stars
- Review -> positive / negative
- Why?
	- Insights about brand, products, features, changes over time
	- Investors trying to understand markets
- vocab = token
	- ![](Pasted%20image%2020240304182949.png)
		- OOV = Out of Vocabulary tokens
			- Mapped to empty 0 index
	- ![](Pasted%20image%2020240304202130.png)

# Bag of Words
- One Hot Encoding
	- ![](Pasted%20image%2020240304202704.png)
- Bag of Words Encoding
	- ![](Pasted%20image%2020240304202915.png)
	- End up with one column that has all represented words
	- The sum is what actually goes into the model
	- Model is learning the weights that apply to each word ![](Pasted%20image%2020240304203345.png)
	- Second layer may learn combinations of words and how they work together ![](Pasted%20image%2020240304203533.png)
	- Basic units:
		- Words
		- Characters / groups of characters
		- bytes
		- ![](Pasted%20image%2020240304203958.png)
	- ![](Pasted%20image%2020240304204156.png)
# Contextual Encodings
- Dot product will always be 0