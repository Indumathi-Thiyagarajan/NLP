BERT (Bidirectional Encoder Representations from Transformers) is a Transformer-based encoder model. Many traditional sequence models, like recurrent neural networks (RNNs), process the input sequence in a single direction, typically from left to right.
This means that when processing a word, the model only has access to the information from the words that came before it.
This limitation can hinder the model's ability to understand the full context of a word. BERT, on the other hand, processes the input sequence in both directions:
It looks at the words that came before a given word (left context).It also looks at the words that came after a given word (right context). 

During training, BERT uses a technique called Masked Language Modeling (MLM). In MLM, certain words in the input sequence are randomly masked, and the model tries to predict these masked words based on their surrounding context. For example, given the sentence "The cat sat on the [MASK] mat," BERT looks at both the words before "[MASK]" (like "sat on the") and the words after (like "mat") to predict the missing word ("rug").
