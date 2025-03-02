Tranformer geneates text one word at a time. 
Up untill transformer comes, the next word prediction wasnt that great. 
Because neural network can shorter memory and couldnt remember longer context and more words. 
Then came the attention mechanism which gave more context with more words window.

![image](https://github.com/user-attachments/assets/50a67cc1-bb53-4d8e-8242-ecdf910e9545)


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

## Attention Mechanism: 

    Can appear many times in architecture followed by feed forward / NN layer. 

    
