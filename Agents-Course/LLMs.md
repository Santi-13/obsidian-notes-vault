#HuggingFace #AI
#### By: Hugging Face
---
# What are LLMs?
An LLM is a type of AI model that excels at **understanding and generating human language**. They are trained on vast amounts of text data, allowing them to learn patterns, structure, and even nuance in language. These models typically consist of many millions of parameters.

Most LLMs nowadays are **built on the Transformer architecture**—a deep learning architecture based on the “Attention” algorithm, that has gained significant interest since the release of BERT from Google in 2018. The original Transformer architecture looked like this, with an encoder on the left and a decoder on the right:

![[Pasted image 20250320104544.png|]]

There are 3 types of transformers:

1. **Encoders**  
    An encoder-based Transformer takes text (or other data) as input and outputs a dense representation (or embedding) of that text.
    
    - **Example**: BERT from Google
    - **Use Cases**: Text classification, semantic search, Named Entity Recognition
    - **Typical Size**: Millions of parameters
2. **Decoders**  
    A decoder-based Transformer focuses **on generating new tokens to complete a sequence, one token at a time**.
    
    - **Example**: Llama from Meta
    - **Use Cases**: Text generation, chatbots, code generation
    - **Typical Size**: Billions (in the US sense, i.e., 10^9) of parameters
3. **Seq2Seq (Encoder–Decoder)**  
    A sequence-to-sequence Transformer _combines_ an encoder and a decoder. The encoder first processes the input sequence into a context representation, then the decoder generates an output sequence.
    
    - **Example**: T5, BART
    - **Use Cases**: Translation, Summarization, Paraphrasing
    - **Typical Size**: Millions of parameters

Although Large Language Models come in various forms, LLMs are typically decoder-based models with billions of parameters.

The underlying principle of an LLM is simple yet highly effective: **its objective is to predict the next token, given a sequence of previous tokens**. A “token” is the unit of information an LLM works with. You can think of a “token” as if it was a “word”, but for efficiency reasons LLMs don’t use whole words.

Each LLM has some **special tokens** specific to the model. The LLM uses these tokens to open and close the structured components of its generation. For example, to indicate the start or end of a sequence, message, or response. Moreover, the input prompts that we pass to the model are also structured with special tokens. The most important of those is the **End of sequence token** (EOS).

The forms of special tokens are highly diverse across model providers.

The table below illustrates the diversity of special tokens.

| **Model**       | **Provider**                | **EOS Token**           | **Functionality**             |
| --------------- | --------------------------- | ----------------------- | ----------------------------- |
| **GPT4**        | OpenAI                      | `<\|endoftext\|>`       | End of message text           |
| **Llama 3**     | Meta (Facebook AI Research) | `<\|eot_id\|>`          | End of sequence               |
| **Deepseek-R1** | DeepSeek                    | `<\|end_of_sentence\|>` | End of message text           |
| **SmolLM2**     | Hugging Face                | `<\|im_end\|>`          | End of instruction or message |
| **Gemma**       | Google                      | `<end_of_turn>`         | End of conversation turn      |
## Understanding next token prediction.
LLMs are said to be **autoregressive**, meaning that **the output from one pass becomes the input for the next one**. This loop continues until the model predicts the next token to be the EOS token, at which point the model can stop.

![[Pasted image 20250320105350.png]]

In other words, an LLM will decode text until it reaches the EOS. But what happens during a single decoding loop?

While the full process can be quite technical for the purpose of learning agents, here’s a brief overview:

- Once the input text is **tokenized**, the model computes a representation of the sequence that captures information about the meaning and the position of each token in the input sequence.
- This representation goes into the model, which outputs scores that rank the likelihood of each token in its vocabulary as being the next one in the sequence.

![[Pasted image 20250320105533.png]]

