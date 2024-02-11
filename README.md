The dataset consists of the articles published by NOS which is one of the biggest news organizations in the Netherlands. Here we have intended to create a Deep Neural Network classification
model which classifies the news Articles into corresponding topics. There were over 100 categories which were transformd to 10 basis fequency along with Others category.

We used **RobBERT** Dutch embeddings for each of the words and when the classifer was initially created, it gave an accuracy of 56%. 
After that, we intended to apply H**eirarachial attention Model** on the articles. It works as follows:- 

First a representation of a sentence is learnt given the words basis attention mechanism. Hence this Attention Layer represents a sentence with learned attention weights on words.
The second Attention layer learns representation of a paragraph from the learned attention weights of sentences. 

Attention mechanism improved the accuracy from **56%** to **72%**.
