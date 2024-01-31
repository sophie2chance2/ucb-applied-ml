# 1/30/2024

- Focus on one thing for a period at a time, then move on
- Senior Data Scientist @ Blue Crew - match blue collar workers with appropriate jobs
- Used to use [streamlit](https://streamlit.io/) at the end of a project - NOW, Start with streamlit to see what the end result should be, then reverse engineer it

- Question:
	- Is using ML the right approach for matching a person to a job
- ![[Pasted image 20240130174619.png]]
- ![[Pasted image 20240130174710.png]]
- ![[Pasted image 20240130174922.png]]
- Reinforcement learning:
	- One of the 3 pillars of learning: supervised, unsupervised, reinforcement
	- TYPE/FRAMEWORK of learning
	- Uses trial and error
- Data important in industry - algorithm important in academia
- If someone gets a job -> reward, if someone does not get a job -> penalty


- Start with STREAMLIT
![[Pasted image 20240130175754.png]]
- Exploration: try a bunch to find the best
- Exploitation: one place over and over

![[Pasted image 20240130180138.png]]
- Q-table: 
	- Initializes at 0
	- States are workers
	- Columns are jobs
![[Pasted image 20240130180310.png]]
- Scores listed, show how good of a match they are
- Synthetic data can show why you need more data and what that data looks like
	- Combine with streamlit to make your case
- Start with the most simple model
	- ![[Pasted image 20240130181924.png]]
	- ![[Pasted image 20240130181953.png]]
	- ![[Pasted image 20240130182034.png]]
### Synthetic Data Generation
![[Pasted image 20240130182849.png]]

![[Pasted image 20240130182927.png]]
![[Pasted image 20240130182946.png]]
- Free text is really hard to synthesize
	- option: embeddings
	- umap
- LLMs is a bubble according to David Stroud
	- Italy banned ChatGPT
	- Reinforcement learning
- Markov Decision Process



# 1/23/2024

- New competitive advantage is going to be who has the best QUALITY of data
- ![[Pasted image 20240123174117.png]]
- Use Poetry
- Good way of checking for nans -> if instance(x, float):
- ![[Pasted image 20240123181555.png]]
- Extensions
	- Live Share Extension Pack
	- Rewrap
	- Todo Tree
- [zed.dev]
- https://docs.google.com/document/d/1XUREwbCaota_nci5SIEmBsx_MDChitP_7aEiDdfkEzY/edit
```
{ // Use IntelliSense to learn about possible attributes. // Hover to view descriptions of existing attributes. // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387 "version": "0.2.0", "configurations": [ { "name": "Python: Current File", "type": "python", "request": "launch", "program": "${file}", "console": "integratedTerminal", "python.formatting.provider": "black", "python.linting.enabled": true, "files.autoSave": "afterDelay", "files.autoSaveDelay": 10000, "python.linting.lintOnSave": true, // "justMyCode": false, } ] }
```

```
{ "todo-tree.tree.showCountsInTree": true, "todo-tree.highlights.defaultHighlight": { "icon": "alert", "type": "tag", "foreground": "white", "background": "white", "opacity": 50, "iconColour": "orange" }, "todo-tree.highlights.useColourScheme": true, "todo-tree.highlights.customHighlight": { "[ ]": { "icon":"pencil", "type": "text", "background": "green", "foreground": "white", "iconColour": "yellow", "gutterIcon": true }, "[x]": { "icon":"check", "background": "green", "foreground": "yellow", "iconColour": "green", "gutterIcon": true }, "TODO": { "icon": "eye", "type": "text", //This highlights the whole line "background": "blue", "foreground": "yellow", "iconColour": "yellow", // "foreground": "#ee00b2", // "iconColour": "#ee00b2", "gutterIcon": true }, "FIXME": { "icon":"flame", "background": "red", "foreground": "green", "iconColour": "green", "gutterIcon": true }, "BUG": { "icon":"bug", "background": "red", "foreground": "white", "iconColour": "red", "gutterIcon": true }, "NOTE": { "icon":"beaker", "foreground": "navy", "background": "orange", "iconColour": "orange", "gutterIcon": true }, "CLASS": { "icon":"package", "background": "red", "foreground": "white", "iconColour": "red", "gutterIcon": true }, "MEAS": { "icon":"log", "type": "text", "foreground": "navy", "background": "orange", "iconColour": "orange", "gutterIcon": true }, "FUNCTION": { "icon":"law", "type": "text", "foreground": "purple", "background": "white", "iconColour": "purple", "gutterIcon": true }, "IDEA": { "icon":"light-bulb", "type": "text", "foreground": "yellow", "background": "blue", "iconColour": "yellow", "gutterIcon": true } }, "todo-tree.general.tags":[ "[ ]", "[x]", "TODO", "FIXME", "BUG", "NOTE", "IDEA", "CLASS", "MEAS", "FUNCTION", ], "python.formatting.provider": "black", "python.defaultInterpreterPath": "${workspaceFolder}/.venv" // "jupyter.alwaysScrollOnNewCell": true }
```

# 1/9/2024
- We are going to be people managers and chat bot managers
- The standard of data scientist is going up
- Top Conferences
	- [NeurIPS](https://nips.cc/)
	- [ICML](https://icml.cc/)
	- Image Specific
		- [ECCV](https://eccv2022.ecva.net/)
		- [ICLR](https://iclr.cc/)
- Synthetic data
	- Okay in some situations, bad in others
	- Synthetic drift - needs to be managed
- Very particular to low end engineers and high level engineers
	- Get models to work or running models
	- Consumer - bargin basement engineer (no mote)
		- Knowing an industry really well can help you be good at this
		- API call to a model - no added intelligence
	- Producer - high level engineer
		- Add more flavor than just an API call
		- Much more resilient 
- AnyScale - company that uses open source - fraction of the cost
- RAG - retrieval augmented generation
- Timeline for projects is being shortened
### Governance
* Dual Use Technology
	* Concern for 5 years in DOD is that all of these tools have DUT
	* ITAR - **International Traffic in Arms Regulations**
		* Self driving car is a military threat
		* Encryption standards are different in different countries
		* Security standards on cell phone
* [Executive Order on the Safe, Secure, and Trustworthy Development and Use of Artificial Intelligence](https://www.whitehouse.gov/briefing-room/presidential-actions/2023/10/30/executive-order-on-the-safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence/)
* Robot revolution is starting to take form
* Worried about accuracy drift
	* Do a retrain/realignment
* [Mistral](https://mistral.ai/) - doesn't mind much who they are going to take over
* Huge incentives for Stanford, open AI, etc. to be in the center
* [Governance in AI Webinar](https://www.fhi.ox.ac.uk/webinar3/)
	* Flexibility of thought is interesting
	* When someone pops up out of the blue, its interesting
	* Listen to more of them
* New data science position
	* Bring data people in / train government people on data
* [Chief Software Officer Article](https://www.linkedin.com/pulse/time-say-goodbye-nicolas-m-chaillan/?trackingId=MZsYNcB7KQFljO4aqqjTcg%3D%3D)
* [Anti-intellectualism in American Life - Book](https://www.amazon.com/Anti-Intellectualism-American-Life-Richard-Hofstadter/dp/0394703170)
	* [Anti-intellectualism Definition](https://study.com/academy/lesson/what-is-anti-intellectualism.html#:~:text=Anti%2Dintellectualism%20is%20broadly%20defined,fascists%20in%20the%2020th%20Century)
* Effective Altruism