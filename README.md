# Light-RAG
Creating this simple to share my knowledge base ON Light RAG.

This repository hosts the code of LightRAG. The structure of this code is based on [nano-graphrag](https://github.com/gusye1234/nano-graphrag).
![请添加图片描述](https://i-blog.csdnimg.cn/direct/b2aaf634151b4706892693ffb43d9093.png)
</div>

## 🎉 News 
- [x] [2024.10.15]🎯🎯📢📢LightRAG now supports Hugging Face models! 

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

### Batch Insert
```python
# Batch Insert: Insert multiple texts at once
rag.insert(["TEXT1", "TEXT2",...])
```
