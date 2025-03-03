

**Embeddings are specific types of vectors that are learned to represent complex data meaningfully, 
while vectors are just general mathematical objects used to represent any form of data.**

## Encoder:
The encoder's role is to process the input sequence and create a representation of it.
It consists of a stack of identical layers, each containing self-attention and a feed-forward network.
The encoder takes the input sequence (e.g., a sentence) and produces a set of encoded representations, which capture the meaning and context of the input.
Output of encoder is embedding
    
## Decoder:
The decoder's role is to generate an output sequence, given the encoded representation from the encoder.
It also consists of a stack of layers, but with some key differences:
It includes a "masked self-attention" layer, which prevents the decoder from attending to future words in the output sequence. This is crucial for generating sequences one word at a time.
It includes an "encoder-decoder attention" layer, which allows the decoder to attend to the encoded representations from the encoder.
The decoder is used to generate the output sequence, one token at a time, until the end of the sequence token is generated.

Encoder: Self-attention + Feed-forward neural network
Decoder: Masked self-attention + Encoder-decoder attention + Feed-forward neural network
Encoder-decoder is a mechanism or a pattern of how to process sequential data, specifically for tasks that require transforming one sequence into another. It's a conceptual framework.   
Transformer is an architecture that can be used to implement that encoder-decoder mechanism, and it does so very effectively due to its attention-based design. We can say Bert is a transformed based encoder decoder mdoel


# Transformer Model Classifications:

Based on the presence and arrangement of encoders and decoders, Transformer models are often classified into three main categories:

## Encoder-Decoder Transformers:

These models have both an encoder and a decoder.
They are used for sequence-to-sequence tasks, such as:
Machine translation (e.g., translating English to French)
Text summarization (e.g., generating a summary of a long document)
The encoder processes the input sequence, and the decoder generates the output sequence.

## Encoder-Only Transformers:

These models consist only of an encoder.
They are used for tasks that involve understanding the input sequence itself, such as:
Text classification (e.g., sentiment analysis)
Named entity recognition (e.g., identifying people, places, and organizations in text)
BERT (Bidirectional Encoder Representations from Transformers) is a prominent example of an encoder-only Transformer.

## Decoder-Only Transformers:

These models consist only of a decoder.
They are used for tasks that involve generating sequences, such as:
Language modeling (e.g., predicting the next word in a sentence)
Text generation (e.g., writing creative text)
GPT (Generative Pre-trained Transformer) is a well-known example of a decoder-only Transformer.
In summary:
