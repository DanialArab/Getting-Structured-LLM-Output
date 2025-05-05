# Getting Structured LLM Output


1. [Introduction](#1)
2. [Structured Output Generation](#2)
   1. [Work with proprietary APIs to get structured outputs](#3)
      1. [Pros and cons](#4)
   2. [Re-prompting](#5)
      1. [Pros and cons](#6)
   3. [Structured Generation (aka Constrained Decoding)](#7)
      1. [Pros and cons](#8)
   4. [Journey to AI engineering from Prompt Hacking](#9)
3. [Instructor open-source library - to generate structured output from model providers that don't support formal structured outputs](#10)
   1. [Instructor](#11)


<a name="1"></a>
## Introduction

When building software using LLMs it is really hard to parse the unstructured text output. So as opposed to interacting with LLM through a chat interface where unstructured output may seem fine, when building software we do need to structure output in a format like JSON format to be easily parsable. If we want an LLM to read a product review and generates a couple of fields like the product name, whether the sentiment is +ive or -ive, then outputting those 2 fields in JSON lets downstream software reads and processes these fields reliably. Here, we see how to get structured outputs using several approaches. Specifically, we use regular expressions as an efficient way to get an LLM to reliably generate outputs in that specific format because regex can be used to enforce constraints on the next token to be generated one token at a time. 

Some key points to consider:
- **Some models support structured responses and some others do not**.
- There are some limitations to these approaches that we will go over, to deal with these limitations we use some open-source libraries like **instructor** that **re-prompts the model until a valid JSON structure is produced**. We will also go over the **constrained decoding** as the underlying concept behind another great open-source library called **outlines**. This library can strengthen the model output at the token level by intercepting the logits, the probabilities the model assigns to the next token outlines blocks any token that don't fit our defined schema or format. This guarantees a valid output without any do-overs 
- We also learn how to generate beyond JSON, to generate valid phone numbers, email addresses, ASCII tic-tac-toe boards and basically, any format you can express in regex. 

<a name="2"></a>
## Structured Output Generation

For scalable software development with LLMs, we do need structured outputs. These structured outputs allow us to go all the way from prompt hacking all the way to AI engineering, below figure:


To build an LLM Application we cannot just simply pass the raw text output to the API, as depicted below:

![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/1.png)

but instead, we do need to have a layer between the LLM and the API. The naive solution to this problem is to add a layer that parses the output, which is a very common first pass but it is:
- time-consuming
- error-prone
- not easily extensible

So the solution is to modify the LLM output to get it structured:

![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/2.png) 

but HOW?

<a name="3"></a>
### Work with proprietary APIs to get structured outputs

The easiest way to get the structured output is to work with proprietary APIs. Every inference provider offers a different solution to how they provide structured outputs:

![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/3.png)

![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/4.png)

<a name="4"></a>
#### Pros and cons

Pros and cons of working with proprietary API:

![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/5.png)

<a name="5"></a>
### Re-prompting

One solution to the above cons is to use re-prompting libraries. **Proprietary models only work with a specific API, but the re-prompting libraries are designed to work with any major LLM providers**. Some examples of these type of tools are:
- Instructor
- LangChain

How re-prompting works?

![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/6.png)

<a name="6"></a>
#### Pros and cons

![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/7.png)

<a name="7"></a>
### Structured Generation (aka Constrained Decoding)

It works with the model at the point of token generation to ensure that models can only sample exactly the structure we define. Here are some libraries to implement this:

- Outlines (from .txt)
- SGLang
- Guidance
- XGrammar

<a name="8"></a>
#### Pros and cons

![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/8.png)

<a name="9"></a>
### Journey to AI engineering from Prompt Hacking

![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/9.png)


<a name="10"></a>
## Instructor open-source library - to generate structured output from model providers that don't support formal structured outputs

<a name="11"></a>
### Instructor 

- It is an open-source re-prompting-based structured output library
- If the model output does not match the format we requested, try again, as depicted below

 ![](https://github.com/DanialArab/images/blob/main/structured_llm_outputs/10.png)






<a name="10"></a>
References <a href="https://www.deeplearning.ai/short-courses/getting-structured-llm-output/">Getting Structured LLM Output - Deeplearning.ai</a>
