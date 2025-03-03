

**Embeddings are specific types of vectors that are learned to represent complex data meaningfully, 
while vectors are just general mathematical objects used to represent any form of data.**


## Encoder:
The encoder's role is to process the input sequence and create embedding which capture the meaning and context of the input.
It consists of a stack of identical layers, each containing Self-attention + Feed-forward neural network
    
## Decoder:
The decoder's role is to generate an output sequence. Decoder has Masked self-attention + Encoder-decoder attention + Feed-forward neural network

    1) Masked Self-Attention: The decoder can only look at the words it has already generated—not the future words—when generating the next word.
    2) Encoder-Decoder Attention: The decoder can look at the entire input sentence (the encoded sentence from the encoder) to help generate each word.

**Encoder: Self-attention + Feed-forward neural network
Decoder: Masked self-attention + Encoder-decoder attention + Feed-forward neural network**

Example of encoder decoder in translation:

        Consider sentence "how are you" translated to tamil. 

        Encoder -> entire english sentence is encoded capturing relationship of all words in sentence using self attention mechanis and NN
        Decoder -> generates output sequence with one word at a time. Now, the decoder moves on to the third word, which is "you" in English. It generates the Tamil word "நீங்கள்" for "you."
            1) Masked self-attention makes sure that when generating "நீங்கள்" (for "you"), the decoder only looks at the words it has already generated (like "எப்படி" and "உங்கள்").So it looks at "எப்படி" and "உங்கள்" (which are already generated) and decides that "you" corresponds to "நீங்கள்" in Tamil.
            
            2)Encoder-Decoder Attention:The decoder again looks at the encoded input ("How are you?") and decides that the third word in the sentence is "you." It uses this to guide the generation of the Tamil word "நீங்கள்".
            At the end of Step 4, the decoder has generated:
            "எப்படி" "உங்கள்" "நீங்கள்" (Tamil for "How are you?")
        
# Transformer Model Classifications:

Based on the presence and arrangement of encoders and decoders, Transformer models are often classified into three main categories:

## Encoder-Decoder Transformers:
When you need to transform one sequence into another either translatng or summarization, converting the data structure,
    
Models : BART, T5, Original transformer

    Use case: Text generation, summarization, translation, question answering, classification

## Encoder-Only Transformers:
Encoder-only models are primarily used for tasks that involve deep understanding of the input text rather than the generation of new text. These models process the entire input sequence and produce a representation of it, but they do not generate new text.

Models : BERT, RoBERTa, Albert, DistilBERT

    Use Cases for Encoder-Only Models:
        Understanding Tasks: When your primary goal is to extract meaningful representations or insights from an input sequence.
        Classification: When you need to categorize or label input sequences (e.g., sentiment analysis, spam detection).
        Information Retrieval: When you need to find relevant information within a large corpus of text.
        Named Entity Recognition (NER): When you need to identify and classify entities (people, places, organizations) within text.
        Question Answering (Extractive): When you need to identify the answer to a question within a given text passage.
        Tasks Where the Output Is a Label or a Span of the Input: When the desired output is a simple label or a selection of a portion of the input text.
    

## Decoder-Only Transformers:
Decoder-only models are designed for text generation tasks where model generates one token at a time with masked self attention.

Models : GPT, Transfomer-XL

        Use case: 
            Generation Tasks: When your primary goal is to generate new sequences of text, code, or other data.
        Language Modeling: When you need to predict the next word in a sequence.




![image](https://github.com/user-attachments/assets/916981ef-bafe-4f7b-8d9e-f2d0ecc106c1)


