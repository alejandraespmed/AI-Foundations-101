# AI Foundations 101

One real example of each concept, with a short explanation.

---

## 1. Token count

I pasted this text into a tokenizer (GPT-5.x & o1/o3 setting):

> Learn about language model tokenization.
> How many tokens are in this text?

**Result: 74 characters = 15 tokens.**

Adding a single extra space after the punctuation of the first sentence changed the result to 75 characters and 16 tokens. One space can cost a full additional token.

I then tried the same sentence in other languages:

| Language | Characters | Tokens |
|----------|-----------:|-------:|
| English  | 74         | 15     |
| Spanish  | 85         | 17     |
| French   | 90         | 19     |
| German   | 98         | 20     |

The same meaning costs more tokens in Spanish, French and German than in English. Since usage is priced per token, it is more cost-efficient for me to keep my prompting in English from now on.

---

## 2. Context overflow

**First message:** "I'm planning a family trip. Key facts: There are 3 vegans in the party, our budget is $4,000 per person, and we are traveling with our grandmother, who can't walk far."

**Messages 2 to 30:** chat about flights, hotels, weather, packing lists and day trips.

**Message 31:** "Can you suggest a dinner spot for the first night?"

**Message 32 (model):** "Sure! There's a great seafood place by the harbor, and it's a 40-minute walk from the hotel."

The early messages have scrolled out of the context window, so the vegan requirement and the grandmother's mobility limit are gone from what the model can see. The model isn't ignoring this information. It can't see it anymore.

---

## 3. Temperature comparison

**Prompt 1:** "Could you give me name ideas for a family dog?"

The answers were very average: Buddy, Max, Daisy, Bailey, Charlie, Molly. These are probably the most common dog names there are, and I have met dogs with several of them. I liked that the chatbot still invited me to share the breed, size or personality so it could narrow things down.

**Prompt 2 (same conversation):** "Could you be more creative?"

The ideas were far more thought-out and varied (Gatsby, Crumpet, Bark Twain, Zephyr, Marrakesh, Gary), and it even gave "personal" favourites.

**What this shows:** the first answer sits close to the most probable, predictable names, and the second moves toward less likely, more varied ones. That is the idea behind temperature: low temperature favours the most likely words, high temperature allows more varied ones. Note that asking the chatbot to "be more creative" is a prompt change, not the temperature setting itself, which is normally an API or tool setting. It shows the same effect, though.

---

## 4. Hallucination

Getting the chatbot to hallucinate was harder than I expected. I spent half an hour trying to get it to give me a study backing up anti-vaccine claims, and it pushed back. I then asked it what I should ask in order to get a hallucination. That was my mistake, because it prepared the model for its own trap, and it caught my test question even after I changed the place and date.

**Prompt:** "What happened at the 1999 Treaty of Peruvian Fishing Accords?"

**What the model did:** it said it could not find any such treaty, and pointed to real events that sit nearby (the 1998 Brasilia Presidential Act, the Peru-Chile maritime dispute ruled on in 2014, and the 1952 Santiago Declaration). Models are trained to push back on false premises, so they often catch obvious traps, but they are not immune, so it is always worth double-checking.

**What a hallucinated answer would have looked like (staged example, not a real model output):**

> "The 1999 Treaty of Peruvian Fishing Accords was signed in Lima on March 14, 1999, by Peru, Chile, and Ecuador. It established a shared anchovy quota of 4.2 million tonnes per year and created the Pacific Fisheries Commission, headquartered in Valparaiso. The treaty was negotiated by Ambassador Rodrigo Salazar and is widely credited with stabilizing regional fish stocks after the 1997-98 El Nino."

**The three signatures that would give it away:**

1. **Too specific.** A date, a city, a tonnage figure, a named ambassador and a commission with a headquarters. None of it can be traced to a source. It also borrows real context (El Nino, anchovy fishing, Lima), so the fiction blends in with the truth.
2. **Too confident.** The tone is certain throughout, with no "I'm not sure" or "I can't verify this".
3. **Unverifiable.** The premise is false. No such treaty exists, and searching for it anywhere else would turn up nothing that matches.
