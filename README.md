# LLM Based projects 

**Tech :**
````
* Openai apis
* open source llm Llama-2 (7B)
* Langchain
* Datasets 
* Vectore DB
* Sentence Transformer
````

## **1. Interact with pdf files.ipynb**

```
- Text representation : OpenAI embedding
- Model : GPT-3.5 -turbo
- Framework : Langchain
```
```
1. Langchain framework teams up with GPT-3.5 to handle PDF question-answering.
2. To find the right stuff in the documents, we bring in Facebook's Fassi library for similarity search.
3. Once we've got the closest matches, we picked out the top 4 most relevant chunks.
4. These chosen bits, along with user's question, get sent over to GPT-3.5-turbo for an answer.
5. Prompt engineering used to get the accurate response.
6. Voilà! You get a quick, accurate response straight from those PDFs.

```
### Experiments :

Experimented with below areas:

1. Instead of using seperate vectorstore we directly find best k(in our case k=4) chucks from document, based on given user query, and pass it with the prompt as context.
2. Experimented with different prompts.

### Obeservations :

- For larger chunck, faced error, due to context window size.
- Sometimes, our results were incomplete, due to restriction in number of tokens.
- Better and more precised prompts gave us good and upto the point results.
- For text from the document it worked well, but when with table data it failed, it gave some unusal results in terms of digits.


## **2. llama_2_+_RAG_.ipynb**

```
- Dataset : jamescalam/llama-2-arxiv-papers-chunked
- Model : meta-llama/Llama-2-7b-chat-hf (7 billion parameters)
- Vector Database : Pinecone
- Text representation : all-MiniLM-L6-v2 (sentence transformer)
- Framework : Langchain
```
```
We've employed the Sentence Transformer MiniLM to represent our text data. 
By creating vector representations of our documents, we store them in Pinecone vector DB. 
This enables us to perform efficient search operations. 
Our dataset comprises approximately 4838 rows, and we've chunked it into batches of size 32 for storage in Pinecone in vector format (dimension: 384).

For the language model, we've utilized Meta's open-source LLM Llama-2, boasting 7 billion parameters. 
We've harnessed the Hugging Face library to load this model with 4bit quantization by bitsandbytes library.

```

### Experiments :

In our experiments, we've explored two approaches:

1. Direct queries to the LLM: This involves querying the language model directly.
2. RAG pipeline : Queries to the LLM with the context of relevant documents. Based on user query, we retrived top 3 most relevent documents from chromadb and created ragpipline with vectorstore and llama-2 model.

### Obeservations :

- Direct queries to llm, without zero context, gave us none relevent results.
- RAG appraoch worked well, Second one, it gave us more relevent response compared to first one for the given user query.