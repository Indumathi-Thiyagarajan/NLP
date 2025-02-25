* Attention helps language model to understand whole context of the text instead of one word at a time. 
* Embeddings -> words become numbers. Words with similar category are located close to each other in coordinates. 
* One ambiguity with these embeddings is, when consider just a word chances are it might not be able to know what context word refers to. 
* Example : apple a brand vs apple a fruit both if consider just the word will be located closer in coord which is not right. 
* Inorder to sovle the problem attention mechanism will be helpful where it considers other words in sentence to know entire meaning. 
* In the below image u can consider that, all words of a sentence are like plannets in a galaxy. words that add categorical meaning to the sentence or words that are similar are pulled together or let say gravitated together. 
Below example if the sentence is apple released a new phone. Phone and apple will be attracted closer that other words

![image](https://github.com/user-attachments/assets/0bd907fc-de02-48db-9070-25083a148c07)

**Linear Transformation**:

if you apply a linear transformation to a vector, it might change its direction from input to output by changing its, size, or orientation, but it will always do so in a consistent, linear way.

In the below image, if we apply linear transformation to the embedding (left one), it will turn into middle and if we again apply linear transformation it turns as right most. **A GOOD EMBEDDING IS ONE THAT SEPERATES or DISTINGUISHES DIFFERNT CATEGORIES CLEARLY**. 
In the below, we see the right most seperates the apples well, so embedding score for that one is the best. 

![image](https://github.com/user-attachments/assets/7f89fc1c-84bf-454a-9af4-76302213eef2)


**Multi-Head Attention**:

1) Lets consider a sentence " Please buy an apple and orange, apple unveiled new phones". Each words in the above sentence gets turned into embeddings aka vectors.
2) **LINEAR TRANSFORMATION**: These embeddings are transformed using linear transformation. the input sequence (e.g., a sentence) is transformed into queries (Q), keys (K), and values (V). These transformations are done using weight matrices. 
       Queries (Q): The part of the input that you want to focus on (the "question" you're asking about the input).
        Keys (K): The part of the input that you're comparing the queries to (like "answers" or references for your question).
        Values (V): The actual data or information that will be passed along after attention is computed.

Example:
Let’s use a simple sentence to explain the concept:
"The cat sat on the mat."

Imagine we want to focus on the word "cat" and how it relates to other words in the sentence.

      Queries (Q):
      
      Suppose we are focusing on the word "cat" (let’s say it's the word we care about or the word we want to understand better).
      We create a query (Q) for "cat". The query is like a question:
      "How does this word relate to other words in the sentence?"
      So, the query represents the focus of our attention, asking how relevant other words are to "cat".
      Keys (K):
      
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
                   
   Now we need to create lot more embedding with transformation using linear transformations.

4) **Compute Attention Scores:**
   Once we have our queries (Q), keys (K), and values (V), the attention mechanism does the following:

Compute Attention Scores:

      We compare the query for "cat" to each of the keys for other words (the comparison is typically done by calculating the dot product between Q and K).
      This tells us how much focus (or attention) we should give to each word.
      The higher the score, the more attention the word should get.
      For example:
      
      Query for "cat" and Key for "sat" might have a high score because "sat" describes an action that the cat is doing, so it is relevant.
      Query for "cat" and Key for "on" might have a lower score because "on" is not directly related to "cat" (though it is in the context of the sentence, it is not as relevant).
      Apply Attention Weights:
      
      After getting the attention scores, we normalize them (usually by applying a softmax function) to turn them into weights.
      These weights tell us how much of each value should be passed along based on the attention score.
      Combine Values Using Attention Weights:
      
      We then combine the values based on the attention weights. This weighted sum of values represents the information we care about after computing attention.
      For example:
      
      If the word "sat" has a high attention weight, its value might contribute more to the final output.
      If the word "on" has a low attention weight, its value will contribute less to the final output.
  

6) Scaled dot product is a way to help the model decide how much focus or "attention" each part of the input (like a word or token) should give to every other part. A dot product is a simple mathematical operation that compares two vectors (which are just lists of numbers). If two vectors are similar, the dot product is a large number; if they're not similar, the dot product is small. So, when we compute the dot product between the "query" word (the word we're focusing on) and the "key" word (the word we're comparing it to), it tells us how similar they are. To get attention score, we do scaling by diving the dot product by the square root of size of the vector, Next we do softmax which turns the probability value between 0 and 1.

With the above obtained attention score, we can tell how much information each word carries. words with higher attention score contribute more to the output. 

In multihead attention all the above steps, transformations, 
![image](https://github.com/user-attachments/assets/e1b298c9-4fd8-42c7-a25c-7b058a8af0ae)

