# Parts of Speech Sentiment Analysis Mini-Study

To further my interest in natural language processing using non-text/stylometric data, I created this mini-study with the purpose of showing that sentiment can be observed using only parts-of-speech tags for input. While there is a sizable amount of research dealing with POS and other stylometric data in authorship-attribution tasks, there is very little - if any - research into using solely POS/non-text stylometric data for other common NLP tasks, such as gauging user sentiment. I can't say why this is; maybe this whole thing is just so well-known that nobody is talking about it, or maybe it's the fact that POS and its related data types tend to be slightly less performant than traditional text input which fosters a lack of interest. Regardless, I have a hunch that POS tags generalized nature could make them useful as a strong base for transfer learning. This is an initial proof of concept to what will hopefully be part of a much larger experiment.

I've chosen to use sentiment140 as is somewhat of a NLP "Hello World!" dataset, similar to how MINST is to computer vision. It consists of 1.6 million tweets which have been labeled as either positive or negative. I've built of off Arun Pandian's "NLP Beginner - Text Classification using LSTM" on Kaggle because their kernel does most of what I want to study already and because of how thorough their comments are. I've modified the preprocessing to convert all text to POS tags using nltk. I swapped out the author’s Glove vectorizations for Word to Vec vectorizations. This is because I won't be using transfer learning and because I've had better luck with W2V than Glove when starting from scratch in the past. The model itself has been modified significantly in order to better fit the new POS data. The key takeaways from the changes to the model are dropout, dropout, and a little more dropout, which the generalized POS embeddings appear to thrive under.

In all we scored 64% in overall accuracy, which isn't great considering random guessing would yield us 50%. The good news is that we've accomplished our goal of showing that POS tags alone do in fact convey sentiment. A slight drop in performance with POS is to be expected, and considering that the original model only got 78% using full text input with transfer learning, our results look a little bit better. I plan to graduate to a dataset with larger entries as twitter’s 140 character limit is likely contributing to the low scores across the board for this dataset on Kaggle. 

### Dataset not included because it's too large. See https://www.kaggle.com/datasets/kazanova/sentiment140?datasetId=2477&sortBy=voteCount
