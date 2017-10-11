# NLP
In this notebook we use natural language methods to study Yelp data challenge. We predict ratings of each review by its text review. Our main goal is to implement the word2vec algorithm and deep learning method such as RNN and compare it with traditional methods such as TF-IDF.
#### Data:  
The size orignal data is about 5 gb of json files, which is a liitle bit too large for a laptop. Here we will just use a part of the data set to illustrate the idea. To my personal interst, I choose the restaurants with 'Chinese' in its business category.

#### Methods:
The major method we are interested in is word2vec, an algorithm to find a distribution representation of a word in a document. More precisely, the algorithm will give the probability of a word having silmilar meaning with a given word. For example, 'friendly' is silmilar to 'polite' with probability 74%. 

The basic idea of word2vec is autoencoding, that is, a neural network with one hidden layer with the same input and out put level. To get the distribution part, we just plug in the output into softmax functions. So there is two sets of weights word2vec will estimate, and we will only use the first set of weights. 

#### Result: 
| Methods       | Accuracy         | 
| ------------- |:-------------:| 
| TF-IDF + Random Forest    | 0.39| 
| Word2Vec + Random Forest    | 0.52     |
| Word2Vec + Neural Network | 0.48     |
| Word2Vec + RNN | 0.52 |


The accuracy of fine-grained (with 5 different labels) is about 53%, and the accuracy of positive-negative is about 82%. They don't look very impressive, but we note that many major algorithms perform more or less like this figure on the IMDB dataset. Maybe it is just because NLP is difficult. In our dataset, the major mistake is our algorithm classify more than 50% of 3 stars rating as 4 stars.

#### Possible iprovments:
* Finer cluster: we may make some cluster, for example, by city.
* Combining TFIDF with word2vec: After get the features of each word by word2vec, to get the feature of a text review we just take the average. We may miss lot of information here. For example if a word is used in lot of reviews, that may imply that that word is not that important. We should give it a lower weight.
* We have tried RNN+ Word2Vec, which means we have took order of words into consideration. But the result is 
not different from Word2Vec+RF. A possible reason is that we didn't tune the RNN very well since we don't have enough computing resources. 
* Order of words: We may group words in a sentence together.
