<H3>NAME : PAVITHRA S</H3>
<H3>REGISTER NO : 212223230147</H3>
<H3>EX. NO.9</H3>
<H3>DATE: 04.09.2026</H3>
<H1 ALIGN =CENTER>Implementation of Text  Summarization</H1>
<H3>Aim: </H3> 
To perform automatic text summarization using Natural Language Processing (NLP) techniques.
 <BR>
<h3>Algorithm:</h3>

Step 1 Import necessary libraries for natural language processing tasks.<BR>
Step 2: Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
Step 3: Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
Step 4: Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
Step 5: Construct the main program to read the paragraph  and perform text summarization<br>
      - Generate and print the original text.<br>
      - Generate and print the text summary using the  Text Summarization function<br>
<H3>Program:</H3>

```py
!pip install nltk

import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize,sent_tokenize
from nltk.stem import PorterStemmer
nltk.download( 'punkt_tab' )
nltk.download( 'stopwords' )

def preprocess_text(text):
	words = word_tokenize(text)
	stop_words= set(stopwords.words( 'english'))
	filtered_words= [word for word in words if word. lower() not in stop_words and word.isalnum()]

	stemmer = PorterStemmer()

	stemmed_words= [stemmer. stem(word) for word in filtered_words]
	return stemmed_words

def generate_summary(text,num_sentences=3):

	sentences= sent_tokenize(text)
	preprocessed_text = preprocess_text(text)
	word_frequencies =nltk. FreqDist (preprocessed_text)

	sentence_scores ={}
	for sentence in sentences:
		for word, freq in word_frequencies.items():
			if word in sentence.lower():
				if sentence not in sentence_scores:
					sentence_scores[sentence] = freq
				else:
					sentence_scores[sentence]+= freq
	summary_sentences= sorted(sentence_scores, key=sentence_scores.get,reverse=True) [ : num_sentences]

	return ' '. join(summary_sentences)


import os

input_file="/content/NLPINTRO.txt"
if not os.path.exists(input_file):
    with open(input_file, 'w') as f:
        f.write("Natural Language Processing (NLP) is a field of artificial intelligence that focuses on enabling computers to understand, interpret, and generate human language. It combines computational linguistics—rule-based modeling of human language—with statistical, machine learning, and deep learning models. Early NLP approaches were rule-based, relying on handcrafted grammatical rules. Modern NLP often uses machine learning algorithms, especially deep learning, to process and analyze vast amounts of text data.")

with open(input_file, 'r') as file:
	input_text = file.read()
summary = generate_summary(input_text)
print( " \nSummary : " )
for sentence in nltk.sent_tokenize(summary):
    print(sentence)
```

<H3>Output</H3>
<img width="1417" height="135" alt="image" src="https://github.com/user-attachments/assets/ac42f7f0-b327-442f-956c-447a1e03c40f" />


<H3>Result:</H3>
Thus ,the program to perform the Text summarization is executed sucessfully.


