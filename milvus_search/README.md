# Build RAG with Milvus

This notebook demonstrates how to build a Retrieval-Augmented Generation (RAG) pipeline using Milvus vector database and OpenAI's language models.

## Overview

The RAG system combines a retrieval system with a generative model to generate contextual responses based on retrieved documents. This implementation:
- Uses Milvus as the vector database for efficient similarity search
- Leverages OpenAI's text-embedding-3-small model for generating embeddings
- Utilizes GPT-3.5-turbo for generating responses based on retrieved context

## Features

- **Document Processing**: Load and process markdown documents from Milvus documentation
- **Vector Embeddings**: Generate embeddings using OpenAI's embedding API
- **Milvus Integration**: Store and retrieve vectors efficiently using Milvus
- **RAG Pipeline**: Retrieve relevant context and generate answers using LLM

## Prerequisites

- Python 3.8+
- OpenAI API key
- Milvus instance (local or cloud)

## Dependencies

Install the required packages:

```bash
pip install --upgrade pymilvus openai requests tqdm
```

## Environment Setup

Set your OpenAI API key as an environment variable:

```bash
export OPENAI_API_KEY='your-api-key-here'
```

## Data Source

The notebook uses FAQ pages from [Milvus Documentation 2.4.x](https://github.com/milvus-io/milvus-docs/releases/download/v2.4.6-preview/milvus_docs_2.4.x_en.zip) as the knowledge base.

The documentation is automatically downloaded and extracted during notebook execution.

## Milvus Configuration

The notebook supports three connection modes:

1. **Milvus Lite** (local file-based):
   ```python
   milvus_client = MilvusClient(uri="./milvus_demo.db")
   ```

2. **Local Milvus Server**:
   ```python
   milvus_client = MilvusClient(
       uri="http://localhost:19530",
       user="root",
       password="Milvus"
   )
   ```

3. **Zilliz Cloud** (managed service):
   ```python
   milvus_client = MilvusClient(
       uri="your-cluster-endpoint",
       token="your-api-key"
   )
   ```

## Usage

1. **Run the notebook cells sequentially** to:
   - Install dependencies
   - Download and process Milvus documentation
   - Initialize embedding model
   - Create Milvus collection
   - Generate and insert embeddings
   - Query the RAG system

2. **Example Query**:
   ```python
   question = "How is data stored in milvus?"
   ```

3. **The system will**:
   - Convert the question to an embedding
   - Retrieve top-3 similar documents from Milvus
   - Generate a contextual response using GPT-3.5-turbo

## Notebook Structure

1. **Setup & Dependencies**: Install required packages
2. **Data Preparation**: Download and process Milvus documentation
3. **Embedding Model**: Initialize OpenAI embedding model
4. **Milvus Collection**: Create and configure vector database
5. **Data Insertion**: Generate embeddings and store in Milvus
6. **RAG Pipeline**: Retrieve context and generate responses

## Key Functions

- `emb_text(text)`: Generate embeddings for input text
- Milvus operations: create collection, insert data, search vectors
- RAG workflow: retrieve context + LLM generation

## Notes

- The notebook uses Inner Product (IP) distance metric for similarity search
- Embeddings are generated using OpenAI's text-embedding-3-small model (1536 dimensions)
- The system processes documents by splitting on "# " markers in markdown files

## Resources

- [Milvus Documentation](https://milvus.io/docs)
- [OpenAI API Documentation](https://platform.openai.com/docs)
- [Original Tutorial](https://github.com/milvus-io/bootcamp/blob/master/tutorials/quickstart/build_RAG_with_milvus.ipynb)

## License

This notebook is based on Milvus bootcamp tutorials and follows their licensing terms.
