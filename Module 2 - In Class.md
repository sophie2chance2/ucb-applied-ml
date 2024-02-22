[Course Framing](https://docs.google.com/document/d/1jUDR61z1pCCXnpr2CbXJXywe45MrSabPuijx2BPO0Sg/edit?pli=1)

[Good ML Podcast - TWIML](https://twimlai.com/)

https://colab.research.google.com/drive/10umkNtjwgsrTuhX_Lk9YU0JuecPLCb1b?usp=sharing#scrollTo=Fr9MDsg5iedT

- Need to make sure you are finding the global min, not the local min
- ![](<photos/Pasted image 20240116162254.png>)
- Need to jump up pretty far to run down to find the true bottom. 
- Deep learning makes it easier, more stretched out
- ![](<photos/Pasted image 20240116162551.png>)
	- Most cutting edge: there can be multiple global minima 
- Measurement
- How big steps are
	- Step sizes can change based on the situation
	- Steps get smaller the closer you are to the optimum
- Stopping criteria
- SDG examples are equally weighted
- * Epochs
	* 5 is a good number
	* smaller datasets need more epochs
	* going through the FULL dataset without necessarily hitting every data point
* Shuffle data in pre-processing so that there aren't errors from the way that the data was collected
* You never know how many epochs you need. You may give up one step too short
* Efficiency is important - try many different options in order to do well
* Transformers solve most issues
	* Build transformers to not get fired 

# Fiddle Sticks
- Joseph Schueder - Generative AI for SMU (RTX, Ratheon, Collins Aerospace)
- Considerations
	- Pricing
	- Scalability/Response Time
	- Quality
	- Privacy & Security
	- Bias
- ![](<photos/Pasted image 20240116174752.png>)
- ![](<photos/Pasted image 20240116174901.png>)
- Uses a second LLM to look for un-secure prompts
	- External model
- Orchestration -> is a set of models
- Go external as much as we can
	- Confidence in that falls to chief AI scientist
	- Text is the beginning, next is text, video, etc.
	- Just call the models
	- In a small company a differentiator could be the model if you build it from scratch. If you are a big company, cost is more of the factor.
- Tech Stack ![](<photos/Pasted image 20240116175815.png>)
- 