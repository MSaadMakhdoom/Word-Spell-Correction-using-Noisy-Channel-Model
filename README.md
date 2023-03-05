# Spell Correction for Roman Urdu words

## Developing spell correction for Roman Urdu.Correcting non-word errors using the Noisy Channel model. This spell correction technique has been widely used by word processors and is also being used by Google in its search engine. Whenever you type in a query with a misspelled word such as corection Google would instantly return the results for correction instead.

## Implement a spell correction program for Roman Urdu in Python. Spell correction using the Noisy Channel model is based on Bayes Theorem as shown in Equation 1. Where w is the candidate word and x is the misspelled word.

# P(w|x) = P(x|w) ∗ P(w)


- Get the corrected word ˆw we perform an argmax over all candidate words to pick the word with the highest probability. The P(x) in the denominator is common for all candidate words and can be ignored.


# wˆ = argmaxw ∈ candidates P(x|w) ∗ P(w) (2)

# Data
- generating error model tables. data.txt is a collection of Roman Urdu sentences and misspellings.txt contains a list of words and their misspellings.

# Implementation Details
- The spell corrector developing contains four main components.
 
* Language Model P(w): The language model gives the probability of each word occurring in the vocabulary V determined using the corpus given in data.txt and any other corpus you can find. A simple unigram model should be trained using the provided file data.txt and any other corpus you can find. You can assume that all words given in data.txt are correctly spelled.
* Error Model P(x|w): This model used to estimate the probability of typing x when w was
intended. This error is to be modeled using character level insert, delete, transpose and substitute tables.Generating these tables using the provided list of common misspellings in Roman Urdu and any other list you can find.
* Candidate Words Generation (w ∈ candidates): The candidate model give you all the possible words w which could have been mistyped as x. The misspelling x may have seperated the word w into two tokens for example for customer the misspelling may be cus tomer. The misspelling x may have combined two words into one token for example the misspelling may be customerhain.
* Selection Model using argmax: An ensemble of word-level and character-level language models will be used to score candidate correct sentences. The final selection using argmax will be responsible for choosing the candidate corrected sentence ˆw which has the highest probability specified  ensemble of language models.
*  Generating Error Model Edit Tables
## Following are some examples:
- INSERT - Correct: ”usay” Wrong: ”usaye” Increment entry for ”y” and ”e” in insert table
- DELETE - Correct: ”usay” Wrong: ”usy” Increment entry for ”s” and ”a” in delete table
- SUBSTITUTE - Correct: ”usay” Wrong: ”usau” Increment entry for ”y” and ”u” in substitute table
- TRANSPOSE - Correct: ”usay” Wrong: ”suay” Increment entry for ”u” and ”s” in transpose table
## Steps
- For calculating P(x|w) for delete and transpose tables.


- Train a uni-gram model using the corpus provided in data.txt.

- Create insert, delete, substitution and transposition tables for alphabets a-z using the provided misspellings.txt. The tables can be implemented using Python dictionaries.

- Create a function that calculates P(x|w) using the Error Model tables.
- Create a function that returns the set of candidate correct words for a given word x. The set of candidate words must be a subset of the vocabulary V . This means that for each candiate word w, P(w) > 0.
- Create a function that returns a list of candidate correct sentences created using all combinations of your
candidate correct words and the original sentence.
- Train an ensemble of atleast one character-level language model and atleast one word-level language model
using the corpus provided in data.txt.
- Create a function that takes a list of candidate correct sentences as input and returns the candidate correct
sentence with the highest probability according to your ensemble of language models.

