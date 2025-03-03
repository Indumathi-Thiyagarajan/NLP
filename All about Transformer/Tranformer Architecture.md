# Why tranformer compared to seq2seq models:

Tranformer geneates text one word at a time. 
Up untill transformer comes, the next word prediction wasnt that great. 
Because neural network can shorter memory and couldnt remember longer context and more words. 
Then came the attention mechanism which gave more context with more words window.

![image](https://github.com/user-attachments/assets/83b06464-6ba3-41e2-979b-c4a6ff85d652)

## Parallel vs seq processing:

    * Sequential processing in NLP means processing one token at a time, with each token depending on the previous one. This is the case for models like RNNs and LSTMs. While effective for many tasks, sequential models are slower and struggle with long-range dependencies. Use case: machine translation, text summarization, speech recognition, and image captioning.
    * Parallel processing in NLP means processing all tokens simultaneously, with each token attending to every other token using mechanisms like self-attention. This approach is used in models like transformers (BERT, GPT), which are much faster, more efficient, and better at handling long-term dependencies.

    Sentence: "She enjoys playing tennis."
    
    1. In an RNN or LSTM, the model processes it one token at a time:
    
        First, it processes "She".
        It then processes "enjoys", using the hidden state from "She" to understand the word in context.
        Next, it processes "playing", using the hidden state from "enjoys", and so on.
        The model has to process each token in sequence, making it slower.
        If we are consider a bigger paragragh with 1000 words, then each word is processed and the model maintains internal state or hidden state or context vector. Model cannot look entire pragraph at once, it has to process one word at a time. 
        
    2. Parallel Processing with Transformer (e.g., BERT):
    
        The entire sentence "She enjoys playing tennis" is processed in parallel.
        The self-attention mechanism looks at all words simultaneously and determines how each word should relate to others in the sentence.
        The model generates a rich contextual understanding of the sentence much more efficiently.
        If we are considering larger para with 1000 words, All 1000 words converted to tokens to embeddings to positional enocding. Self attention mechanism calculated how much attention to pay for each word in seq including before and after. All tokens are processed at once. 

        For example, in the sentence:

        Sentence: "The quick brown fox jumps over the lazy dog."
        The word "quick" might attend to:
            "The" (to learn context like the sentence starting with an article).
            "brown" (to capture more specific context related to color).
            "fox" (for subject and noun context).
            "jumps" (to learn the verb that connects "fox" to the action).
            
        Similarly, all other words ("The", "brown", "fox", etc.) are attending to each other at the same time, which allows the model to capture rich dependencies and contextual relationships between words in parallel.

        For each token, the transformer computes attention scores with all other tokens, which represent how much focus a word should place on each other word in the sequence. These scores are calculated using Query (Q), Key (K), and Value (V) matrices. This computation of attention is done for all tokens simultaneously. The result is a weighted sum of values (V) based on the attention scores, which allows the model to gather information from all other words in the sequence.

        For predicting the next word, the model looks at the output representations of all tokens and uses them to make a prediction.
   
    
![image](https://github.com/user-attachments/assets/50a67cc1-bb53-4d8e-8242-ecdf910e9545)

# Architecture Deep Dive:

![image](https://github.com/user-attachments/assets/97c69f80-f246-4a92-8c45-bf6483f7ee80)


## Tokenizer:

    Tokenizer takes the input text and breaks them into individual pieces. These are words or either parts of words. 
    There are several trained tokenizer where I have tried some in tokenization notebook . Different trained tokenizer behave differently, So we have to chose the tokenizer based on our usecase.

## Embedding:

    Embeddings are dense, numerical vector representations of tokens.
    Can be done by varios methods like bagofwords or words2vec. 
    They capture the semantic meaning and context of words, allowing machines to understand relationships between words. 
    
## Positional Encoding:

    Positional encoding is used to provide information about the position of a word within a sequence.
    This is crucial for models like Transformers, which process sequences in parallel and don't inherently have a sense of word order.

*Embedding captures meaning of the word, encoding captures the positions of the word in sequence*

## Feed forward NN:

    Helps with prediction of next word. NN alone not enough because of short range dependency. So we add attention layer inbetween NN layer. This will help with providing context

## Attention Mechanism: 

    Output from this is going to give scores for each word.Attention scores help the model understand the relationships between the current word and previous words in the sequence (e.g., which words are important to focus on when predicting the next word).

## Logits:

    The logits are the raw predictions for each word in the vocabulary based on the entire processed input sequence. attention scores calculated at every layer help generate better context representations, while logits computed by the final layer of the model to  are used for final predictions. The logits are essentially a vector of scores, one for each word in the vocabulary. These scores represent the raw likelihood of each word being the correct next word (or token) but haven't yet been normalized into probabilities.
    
## Softmax:

    We apply softmax to the logits to get stochastic or probability values. we are raising e to the score which will make all numbers raised irrespective of the positive or nega sign to positive value so negative numbers will be close to 0. 

ALL this process to predict next word. 


# Untrained vs Pre-trained Models:

    Untrained Transformer models don’t know any words or patterns. They need to be trained on data to learn relationships between words. So, an untrained model cannot predict words correctly until it undergoes training on large corpora of text.
    Pre-trained models like GPT already have knowledge of language patterns from massive datasets and can predict the next word based on context.



    
