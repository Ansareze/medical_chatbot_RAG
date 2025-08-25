# Medical Chatbot with RAG (Retrieval-Augmented Generation)

A medical chatbot that uses Retrieval-Augmented Generation to provide accurate medical information based on a medical encyclopedia PDF.

## Recent Updates

**Important Change**: Switched from Hugging Face Inference API to local model loading to resolve compatibility issues.

### What Changed:
- **Before**: Used `HuggingFaceEndpoint` with Mistral-7B-Instruct-v0.3 (required paid API)
- **After**: Uses `HuggingFacePipeline` with Microsoft DialoGPT-medium (free, local)

### Benefits of the New Approach:
- ✅ **No API compatibility issues**
- ✅ **Faster responses** (no network latency)
- ✅ **More control** over model parameters
- ✅ **Free to use** (no API costs or rate limits)
- ✅ **Works offline** once model is downloaded

### Files Updated:
- `medical_chatbot.py` - Main Streamlit application
- `connect_memory_with_LLM.ipynb` - Jupyter notebook for testing
- `memory_for_LLM.ipynb` - Vector store creation (unchanged)

## Setup

1. Install dependencies:
```bash
pip install streamlit langchain langchain-huggingface transformers torch faiss-cpu
```

2. Set up your `.env` file with:
```
HF_TOKEN=your_huggingface_token_here
```

3. Run the Streamlit app:
```bash
streamlit run medical_chatbot.py
```

## How It Works

1. **Document Processing**: Loads medical encyclopedia PDF and creates text chunks
2. **Vector Embeddings**: Uses sentence-transformers to create embeddings
3. **FAISS Storage**: Stores embeddings in a local FAISS vector database
4. **RAG Chain**: Combines retrieval with local LLM generation
5. **User Interface**: Streamlit-based chat interface

## Model Information

- **Embedding Model**: `sentence-transformers/all-MiniLM-L6-v2`
- **LLM**: `microsoft/DialoGPT-medium` (local)
- **Vector Store**: FAISS with local storage