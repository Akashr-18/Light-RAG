# Light-RAG
Creating this simple to share my knowledge base on Light RAG.

This repository hosts the code of LightRAG. The structure of this code is based on [nano-graphrag](https://github.com/gusye1234/nano-graphrag).
![请添加图片描述](https://i-blog.csdnimg.cn/direct/b2aaf634151b4706892693ffb43d9093.png)
</div>

## Install

* Install from source

```bash
cd LightRAG
pip install -e .
```
* Install from PyPI
```bash
pip install lightrag-hku
```

## Quick Start

* Set OpenAI API key in environment if using OpenAI models: `export OPENAI_API_KEY="sk-...".`
* Download the demo text "A Christmas Carol by Charles Dickens":
```bash
curl https://raw.githubusercontent.com/gusye1234/nano-graphrag/main/tests/mock_data.txt > ./book.txt
```

### Using Hugging Face Models
If you want to use Hugging Face models, you only need to set LightRAG as follows:
```python
from lightrag.llm import hf_model_complete, hf_embedding
from transformers import AutoModel, AutoTokenizer

# Initialize LightRAG with Hugging Face model
rag = LightRAG(
    working_dir=WORKING_DIR,
    llm_model_func=hf_model_complete,  # Use Hugging Face complete model for text generation
    llm_model_name='meta-llama/Llama-3.1-8B-Instruct',  # Model name from Hugging Face
    # Use Hugging Face embedding function
    embedding_func=EmbeddingFunc(
        embedding_dim=384,
        max_token_size=5000,
        func=lambda texts: hf_embedding(
            texts, 
            tokenizer=AutoTokenizer.from_pretrained("sentence-transformers/all-MiniLM-L6-v2"),
            embed_model=AutoModel.from_pretrained("sentence-transformers/all-MiniLM-L6-v2")
        )
    ),
)
```
### Batch Insert
```python
# Batch Insert: Insert multiple texts at once
rag.insert(["TEXT1", "TEXT2",...])
```
### Incremental Insert

```python
# Incremental Insert: Insert new documents into an existing LightRAG instance
rag = LightRAG(working_dir="./dickens")

with open("./newText.txt") as f:
    rag.insert(f.read())
```
