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

Based on these scores, we have multiple strategies to select the tokens to complete the sentence. The easiest being to always take the token with the maximum score. But there are more advanced decoding strategies. For example, _beam search_ explores multiple candidate sequences to find the one with the maximum total score–even if some individual tokens have lower scores.
#### Parameters for *Beam Search*:
- **Sentence to decode from** (`inputs`): the input sequence to your decoder.
- **Number of steps** (`max_new_tokens`): the number of tokens to generate.
- **Number of beams** (`num_beams`): the number of beams to use.
- **Length penalty** (`length_penalty`): the length penalty to apply to outputs. `length_penalty` > 0.0 promotes longer sequences, while `length_penalty` < 0.0 encourages shorter sequences. This parameter will not impact the beam search paths, but only influence the choice of sequences in the end towards longer or shorter sequences.
- **Number of return sequences** (`num_return_sequences`): the number of sequences to be returned at the end of generation. Should be `<= num_beams`.

If you want to know more about decoding, you can take a look at the [NLP course](https://huggingface.co/learn/nlp-course).

## Attention is all you need
A key aspect of the Transformer architecture is **Attention**. When predicting the next word, not every word in a sentence is equally important; words like “France” and “capital” in the sentence _“The capital of France is …”_ carry the most meaning.

![[Pasted image 20250320110233.png]]

This process of identifying the most relevant words to predict the next token has proven to be incredibly effective.

Although the basic principle of LLMs—predicting the next token—has remained consistent since GPT-2, there have been significant advancements in scaling neural networks and making the attention mechanism work for longer and longer sequences.

If you’ve interacted with LLMs, you’re probably familiar with the term _context length_, which refers to the maximum number of tokens the LLM can process, and the maximum _attention span_ it has.

## Prompting the LLM is important
Considering that the only job of an LLM is to predict the next token by looking at every input token, and to choose which tokens are “important”, the wording of your input sequence is very important.

The input sequence you provide an LLM is called _a prompt_. Careful design of the prompt makes it easier **to guide the generation of the LLM toward the desired output**.

## How are LLMs trained?
LLMs are trained on large datasets of text, where they learn to predict the next word in a sequence through a self-supervised or masked language modeling objective.

From this unsupervised learning, the model learns the structure of the language and **underlying patterns in text, allowing the model to generalize to unseen data**.

After this initial _pre-training_, LLMs can be fine-tuned on a supervised learning objective to perform specific tasks. For example, some models are trained for conversational structures or tool usage, while others focus on classification or code generation.

## How can I use LLMs?

You have two main options:

1. **Run Locally** (if you have sufficient hardware).
2. **Use a Cloud/API** (e.g., via the Hugging Face Serverless Inference API).

Throughout this course, we will primarily use models via APIs on the Hugging Face Hub. Later on, we will explore how to run these models locally on your hardware.