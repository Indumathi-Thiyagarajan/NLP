* Attention helos language model to understand whole context of the text instead of one word at a time. 
* Embeddings -> words become numbers. Words with similar category are located close to each other in coordinates. 
* One ambiguity with these embeddings is, when consider just a word chances are it might not be able to know what context word refers to. 
* Example : apple a brand vs apple a fruit both if consider just the word will be located closer in coord which is not right. 
* Inorder to sovle the problem attention mechanism will be helpful where it considers other words in sentence to know entire meaning. 
* In the below image u can consider that, all words of a sentence are like plannets in a galaxy. words that add categorical meaning to the sentence or words that are similar are pulled together or let say gravitated together. 
Below example if the sentence is apple released a new phone. Phone and apple will be attracted closer that other words

![image](https://github.com/user-attachments/assets/0bd907fc-de02-48db-9070-25083a148c07)


**Multi-Head Attention**:

