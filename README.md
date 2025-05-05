# Getting Structured LLM Output


1. [Introduction](#1)
1. [](#2)
    1. [T](#3)
       1. [](#4)
       2. [](#5)
       3. [](#6)
       4. [](#7)
    2. [](#8)
       1. [](#9)

 

<a name="1"></a>
## Introduction

When building software using LLMs it is really hard to parse the unstructured text output. So as opposed to interacting with LLM through a chat interface where unstructured output may seem fine, when building software we do need to structure output in a format like in a JSON format to be easily parsable. If we want an LLM to read a product review and generates a couple of fileds like the product name, whether the sentiment is +ive or -ive, then outputting those 2 fields in JSON lets downstream software reads and processes these fields reliably. 

<a name="10"></a>
References <a href="https://www.deeplearning.ai/short-courses/getting-structured-llm-output/">Getting Structured LLM Output - Deeplearning.ai</a>
