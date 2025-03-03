

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
