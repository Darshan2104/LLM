# LLM Based projects 

**Tech :**
````
* Openai apis
* open source llm Llama-2 (7B)
* Langchain
* Datasets 
* Vectore DB
* Sentecen T
````

1. Interact with pdf files.ipynb

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


2. llama_2_+_RAG_.ipynb

```
- Dataset : jamescalam/llama-2-arxiv-papers-chunked
- Model : meta-llama/Llama-2-7b-chat-hf (7 billion parameters)
- Vector Database : Pinecone
- Text representation : all-MiniLM-L6-v2 (sentence transformer)
- Framework : Langchain
```
```
We've employed the Sentence Transformer MiniLM to represent our text data. By creating vector representations of our documents, we store them in Pinecone vector DB. This enables us to perform efficient search operations. Our dataset comprises approximately 4838 rows, and we've chunked it into batches of size 32 for storage in Pinecone in vector format (dimension: 384).

For the language model, we've utilized Meta's open-source LLM Llama-2, boasting 7 billion parameters. We've harnessed the Hugging Face library to load this model. In our experiments, we've explored two approaches:

1. Direct queries to the LLM: This involves querying the language model directly.
2. Queries to the LLM with the context of relevant documents: Here, we provide the LLM with additional context from relevant documents.

Second apprach gave us more relevent response compared to first one for the given user query.
```
