# AI Foundations 101

*Document **one real example of each**, with a one-sentence explanation, and publish it to a public link:*

### A **token count**:

The sentences in grey below count as 74 characters and 15 tokens. 
Note that an added space “ “ after the punctuation of the first sentence would mean a full additional token.

Learn about language model tokenization.
How many tokens are in this text?

![image 1.png](AI%20Foundations%20101/image.png)

![image 2.png](AI%20Foundations%20101/image%201.png)

Additionally I tried counting the tokens of the same sentence but in different languages, and it would be more cost efficient for me to keep all prompting in English from now on.

![image 3.png](AI%20Foundations%20101/image%202.png)

![image 4.png](AI%20Foundations%20101/image%203.png)

![image 5.png](AI%20Foundations%20101/image%204.png)

### A **context overflow** you caused:

**First Message:** "I'm planning a family trip. Key facts: There are 3 vegans in the party, our budget is $4,000 per person, and we are traveling with our grandmother, who can't walk far."

**Messages (2…30):** *You chat about flights, hotels, weather, packing lists, and day trips.*

**Message 31:** "Can you suggest a dinner spot for the first night?"

**Message 32:** "Sure! There's a great seafood place by the harbor, and it's a 40-minute walk from the hotel."

The early messages have scrolled out of the window, so the food requirements, and the grandmother's mobility are gone from the dialogue. The model isn't ignoring this information. It can't see it anymore.

### A **temperature comparison**:

the same prompt giving different answers (or one run "be more creative").

When asking for dog-name ideas the first prompt gave me very average answers, probably the most common dog names available. I can confidently say that I have met some dogs with the names listed at first. I appreciate how Claude still tried to prompt me back to start a conversation and brainstorm possible names based on other variables.

When asking the ai-chatbot if they could be more creative, it came with significantly more thought-out ideas and it even gave “personal” favourites.

![image 6.png](AI%20Foundations%20101/image%205.png)

![image 7.png](AI%20Foundations%20101/image%206.png)

### A **hallucination** (you spotted in the wild), and which of the three signatures gave it away.

Getting the chat-bot to give me an hallucination was harder than I thought it would be, after half an hour trying to convince it to give me a study that could back up anti-vax claims. I asked it what should I ask in order for it to give me an hallucination, which (my mistake) prepared it to be ready for his own question, even when changing the place and dates of the original sentence. Apparently Claude is trained to push back on false premises and say "I don't know" or "I can't verify that," so it will often catch the obvious traps. 

It is not immune, though so one should always double check and try to verify it.

![image 8.png](AI%20Foundations%20101/image%207.png)

![image 9.png](AI%20Foundations%20101/image%208.png)

**Prompt:** "What happened at the 1999 Treaty of Peruvian Fishing Accords?”

**Staged hallucinated answer:**

> "The 1999 Treaty of Peruvian Fishing Accords was signed in Lima on March 14, 1999, by Peru, Chile, and Ecuador. It established a shared anchovy quota of 4.2 million tonnes per year and created the Pacific Fisheries Commission, headquartered in Valparaíso. The treaty was negotiated by Ambassador Rodrigo Salazar and is widely credited with stabilizing regional fish stocks after the 1997-98 El Niño."
> 

**Three signatures could give it away.**

**Too specific**

Exact figures, names, dates, or citations that would be hard to actually know.

- **Specific details make it feel credible:** a date, a city, a tonnage figure, a named ambassador, and a commission with a headquarters. None of it can be traced to a source.
- **It borrows real context.** El Niño, anchovy fishing, and Lima all fit Peru, so the fiction blends in with the truth.

**Too confident**

No hedging at all on something genuinely uncertain.

- **The tone is confident throughout.** There's no "I'm not sure" or "I can't verify this."

**Unverifiable**

You cannot find an independent source that confirms it.

- **The premise is false.** No such treaty exists, but the model treated it as real, and if one tries to look it up anywhere else you wouldn’t be able to find anything that matches what’s stated.
