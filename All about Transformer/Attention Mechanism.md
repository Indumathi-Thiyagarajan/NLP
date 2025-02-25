* Embeddings -> words become numbers. Words with similar category are located close to each other in coordinates. 
* One ambiguity with these embeddings is, when considering just a word chances are it might not be able to know what context word refers to. 
* Example : apple a brand vs apple a fruit both if consider just the word will be located closer in coord which is not right. 
* Inorder to sovle the problem attention mechanism will be helpful where it considers other words in sentence to know entire meaning.
* Attention helps language model to understand whole context of the text instead of one word at a time. 
* In the below image u can consider that, all words of a sentence are like plannets in a galaxy. words that add categorical meaning to the sentence or words that are similar are pulled together or let say gravitated together. 
Below example if the sentence is apple released a new phone. Phone and apple will be attracted closer that other words

![image](https://github.com/user-attachments/assets/0bd907fc-de02-48db-9070-25083a148c07)

**Linear Transformation**:

if you apply a linear transformation to a vector, it might change its direction from input to output by changing its, size, or orientation, but it will always do so in a consistent, linear way ie shape doesnt change from linear to curve. 

In the below image, if we apply linear transformation to the embedding (left one), it will turn into middle and if we again apply linear transformation it turns as right most. **A GOOD EMBEDDING IS ONE THAT SEPERATES or DISTINGUISHES DIFFERNT CATEGORIES CLEARLY**. 
In the below, we see the right most seperates the apples well, so embedding score for that one is the best. 

![image](https://github.com/user-attachments/assets/7f89fc1c-84bf-454a-9af4-76302213eef2)


**Multi-Head Attention**:

1) Lets consider a sentence " Please buy an apple and orange, apple unveiled new phones". Each words in the above sentence gets turned into embeddings aka vectors.
2)  **LINEAR TRANSFORMATION**: These embeddings are transformed using linear transformation. the input sequence (e.g., a sentence) is transformed into queries (Q), keys (K), and values (V). These transformations are done using weight matrices. 
       Queries (Q): The part of the input that you want to focus on (the "question" you're asking about the input).
       keys (K): The part of the input that you're comparing the queries to (like "answers" or references for your question).
       Values (V): The actual data or information that will be passed along after attention is computed.

   Example:
       
       Let’s use a simple sentence to explain the concept:
       "The cat sat on the mat."

      **Queries (Q):**
      
      Suppose we are focusing on the word "cat" (let’s say it's the word we care about or the word we want to understand better).
      We create a query (Q) for "cat". The query is like a question:
      "How does this word relate to other words in the sentence?"
      So, the query represents the focus of our attention, asking how relevant other words are to "cat".
      
      **Keys (K):**
      
      For each word in the sentence, we create a key. A key represents the "answer" to the query, helping us decide how much attention each word should get.
      The key for each word in the sentence is like an answer to the question of how much each word should be attended to. Each key is a reference to each word's relationship with the query word.
      For example:
      The key for "the" might say, "I'm not very related to 'cat'."
      The key for "sat" might say, "I'm somewhat related to 'cat' because I describe an action involving the cat."
      The key for "on" might say, "I'm not closely related to 'cat'."
      The key for "mat" might say, "I'm more related to 'cat' because 'cat' is on 'mat'."
      Values (V):
      
      The values represent the actual data or information that will be passed along after we compute the attention. In other words, the values are the real content or context that we want to keep track of after we focus on certain parts of the sentence.
      For example:
      The value for "the" might be a very basic representation of the word itself, providing little context.
      The value for "sat" might be a richer representation of the action or verb.
      The value for "on" might be a preposition representation, and so on.
      The value for "mat" might provide information about the object that the cat is interacting with (the mat).



4) **Compute Attention Scores:**
   Attention score are calculated with dot product of query and key vectors.

                 Attention score=Q⋅K where Q and K are query and key vectors.
   This values are then passed through softmax to get probabilitic values between 0 and 1. 

   Example to Illustrate Attention Scores:
              
              Sentence: "The cat sat on the mat."
              
              Step 1: Word Embeddings (Values, Queries, Keys)
              Let’s say we represent each word with a 2-dimensional vector (just for simplicity).
              
              Value ("the") = [0.1, 0.2], Query ("the") = [0.1, 0.3], Key ("the") = [0.2, 0.1]
              Value ("cat") = [0.4, 0.6], Query ("cat") = [0.5, 0.7], Key ("cat") = [0.3, 0.2]
              Value ("sat") = [0.7, 0.5], Query ("sat") = [0.6, 0.8], Key ("sat") = [0.4, 0.3]
              Value ("on") = [0.5, 0.3], Query ("on") = [0.2, 0.4], Key ("on") = [0.1, 0.4]
              Value ("mat") = [0.8, 0.5], Query ("mat") = [0.4, 0.5], Key ("mat") = [0.7, 0.3]

              ![image](https://github.com/user-attachments/assets/049f8931-1bab-4c8c-aaa4-28718fff868b)


5) **Weighted Sum of Values:**
   The weighted sum of values is calculated by multiplying each word’s value (embedding) by its corresponding attention weight (after applying softmax to the attention scores).
   
   ![image](https://github.com/user-attachments/assets/d7d5a78c-ddb9-4429-b76c-f0c17a87c770)


**Multi head attention Mechanism**:
              
              In multi-head attention, we create multiple sets of queries (Q), keys (K), and values (V), each from the same input embeddings, but with different weight matrices. These weight matrices allow each head to focus on different aspects of the sentence. Each head will have different Q, K, and V matrices, so even though they are using the same input, each head will focus on different parts of the input.
       
       Now, each head will perform the above attention mechanism separately but in parallel.
       
       For simplicity, let's assume we are using two heads in this example.
       
       Head 1 might give a context vector [0.2, 0.3] for "cat" (focusing on syntax).(like grammatical relationships between words).
       Head 2 might give a context vector [0.6, 0.4] for "cat" (focusing on semantics).(like meaning-based relationships between words).
       Now, we combine these vectors from both heads into a single vector by concatenating them (in this case, [0.2, 0.3, 0.6, 0.4]). This final vector gives us a richer, more complete representation of "cat" because it combines both syntactical and semantic information.
       
       Once the outputs of all heads are combined, they are passed through a linear transformation (via a weight matrix) to project the concatenated vectors back to the desired dimensionality. The output of this process is the final, context-aware representation of each word, which can then be passed on to the next layer of the model (like in a Transformer architecture).
       
       In multihead attention all the above steps, transformations, 
       ![image](https://github.com/user-attachments/assets/e1b298c9-4fd8-42c7-a25c-7b058a8af0ae)

       


***In simpler words, each head is focusing on each word. For each attention head we create one query and multiple key and values. Consider the sentence " Cat sat on the mat". Query is asking how does this word eg: CAT relate to the other words of the sentence. So we ask this query to each word of the sentence and multiple keys and values are found.  Key is the answer to query eg: The is not related to CAT. Value are embeddings or 2 dimensional vectors of actual word eg: the belongs to coordinates [0.5,0.2]. Attention score is calculated with dot product of query and all key vectors of the sentence which then passed through softmax to get probabilitic value between 0 and 1. After we have the attention scores (probabilities), we use them to compute the weighted sum of values which is attention socre multiplied by corresponding embedding. The higher the attention score, the more weight that word's value will contribute. We do this for each word in the sentence, producing a weighted sum of values that represents how much "attention" the word is paying to the other words. After computing the attention scores for all words, the weighted sum of values for a single word will be based on all other words in the sentence, not just the ones it is directly compared with. For instance, the weighted sum for "cat" considers how much attention "cat" should pay to "the," "sat," "on," and "mat." This is the process for single head attention mechanism. 
Multi-head attention involves multiple sets of queries, keys, and values, where each head learns to focus on different relationships (e.g., syntax, semantics). The outputs of all heads are concatenated and passed through a linear transformation to produce the final output.***

