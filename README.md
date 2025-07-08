# 🤖 RAG (Retrieval-Augmented Generation) System

A simple implementation of a Retrieval-Augmented Generation system using OpenAI's GPT-4o, sentence transformers, and FAISS for efficient similarity search.

## 📖 Overview

This project demonstrates how to build a RAG system that:
- 📝 Splits text into sentences for better granular retrieval
- 🔗 Creates embeddings using SentenceTransformers
- 🗃️ Stores embeddings in a FAISS index for fast similarity search
- 🔍 Retrieves relevant context for user queries
- 🤖 Generates responses using OpenAI's GPT-4o with proper citations

## ✨ Features

- 🔐 **Environment-based configuration** - API keys stored securely in `.env` file 
- 📖 **Sentence-level retrieval** - Fine-grained context retrieval using NLTK tokenization 
- ⚡ **Efficient similarity search** - FAISS indexing for fast vector search 
- 📚 **Citation support** - Generated responses include source citations 
- 📊 **Confidence scoring** - AI-generated confidence scores for answers 
- 🚀 **Modern OpenAI API** - Compatible with OpenAI Python library v1.0+ 

## 📋 Prerequisites

- 🐍Python 3.7+ 
- 🔑OpenAI API key 
- 📓Jupyter Notebook or JupyterLab 

## 🚀 Installation

1. 📁**Clone or download this repository** 

2. 📦**Install required packages:** 
   ```bash
   pip install openai sentence-transformers faiss-cpu nltk tiktoken python-dotenv
   ```

3. 🔐**Set up your environment variables:** 
   
   Create a `.env` file in the project directory:
   ```
   OPENAI_API_KEY=sk-your-actual-api-key-here
   ```
   
   ⚠️ **Important**: Replace `sk-your-actual-api-key-here` with your actual OpenAI API key.

## 💻 Usage

### 🔴 Running the Notebook

1. **Open the Jupyter notebook:** 📓
   ```bash
   jupyter notebook RAG.ipynb
   ```

2. ⚡**Execute the cells in order:** 
   - 📦Cell 1: Install dependencies 
   - 🔧Cell 2: Import libraries and load environment variables 
   - 🔍Cell 3: Process text (split, embed, index) 
   - 📝Cell 4: Define retrieval function 
   - 🤖Cell 5: Define answer generation function 
   - ❓Cell 6: Test with example query 

### 💡 Example Query

```python
query = "What is RAG and how does it reduce hallucinations?"
print(generate_answer(query))
```

✨**Expected Output:** 
```
Retrieval-Augmented Generation (RAG) is a method that improves large language models by allowing them to retrieve information from external documents [1]. It reduces hallucinations by first looking up relevant information and then generating a response using that retrieved context [3]. This approach makes the answers more fact-based [2].

Confidence Score: 1
```

## ⚙️ How It Works

### 1. 📝 Text Processing
- **Tokenization**: Uses NLTK's sentence tokenizer to split documents into sentences 📖
- **Embedding**: Converts each sentence to a vector using `all-MiniLM-L6-v2` model 🔢

### 2. 🗃️ Indexing
- **FAISS Index**: Creates an efficient L2 distance-based index for similarity search 🎯
- **Storage**: Embeddings are stored in memory for fast retrieval 💾

### 3. 🔍 Retrieval
- **Query Embedding**: User queries are converted to the same vector space 🔄
- **Similarity Search**: FAISS finds the most similar sentences 🎯
- **Ranking**: Results are ranked by cosine similarity distance 📊

### 4. 🤖 Generation
- **Context Assembly**: Retrieved sentences are formatted with citation numbers 📝
- **Prompt Engineering**: Structured prompt guides the AI to cite sources and provide confidence 🎯
- **Response Generation**: OpenAI GPT-4o generates the final answer ✨

## 📁 Project Structure

```
RAG/
├── RAG.ipynb           # Main Jupyter notebook with implementation 📓
├── .env                # Environment variables (API keys) 🔐
├── README.md           # This file 📖
└── requirements.txt    # Python dependencies (optional) 📦
```

## 🔧 Key Components

### 📦 Dependencies
- `openai` - OpenAI API client for GPT-4o 🤖
- `sentence-transformers` - For creating sentence embeddings 🔢
- `faiss-cpu` - Efficient similarity search and clustering 🎯
- `nltk` - Natural language processing toolkit 📝
- `python-dotenv` - Environment variable management 🔐
- `tiktoken` - OpenAI's tokenization library ⚡

### 🛠️ Main Functions

- `retrieve_sentences(query, top_k=4)` - Retrieves most relevant sentences 🔍
- `format_context(snippets)` - Formats retrieved sentences with citations 📝
- `generate_answer(query)` - Generates final answer with citations and confidence 🤖

## 🎨 Customization

### 🔄 Changing the Embedding Model
```python
embedder = SentenceTransformer("your-preferred-model")
```

### ⚙️ Adjusting Retrieval Parameters
```python
top_snippets = retrieve_sentences(query, top_k=6)  # Retrieve more context
```

### 🎯 Modifying the Prompt
Edit the prompt in the `generate_answer` function to change response style or requirements.

## 🔒 Security Notes

- 🔐 API keys are stored in `.env` file (not in code) 
- 📝 Add `.env` to your `.gitignore` file 
- ⛔ Never commit API keys to version control 
- 🏭 Use environment variables in production 

## 🐛 Troubleshooting

### ⚠️ Common Issues

1. **NLTK Data Missing** 📚
   ```
   LookupError: Resource punkt_tab not found
   ```
   **Solution**: The notebook automatically downloads required NLTK data ✅

2. **OpenAI API Error** 🤖
   ```
   APIRemovedInV1: You tried to access openai.ChatCompletion
   ```
   **Solution**: Code uses the new OpenAI v1.0+ API syntax ✅

3. **Missing API Key** 🔑
   ```
   ValueError: OPENAI_API_KEY not found in environment variables
   ```
   **Solution**: Check your `.env` file and ensure the API key is correct ✅

### 🚀 Performance Tips

- For larger documents, consider chunking strategies 📄
- Use GPU-accelerated FAISS for better performance with large datasets ⚡
- Consider caching embeddings for frequently accessed documents 💾

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Feel free to submit issues, feature requests, or pull requests to improve this RAG implementation.

## 🙏 Acknowledgments

- [OpenAI](https://openai.com/) for GPT-4o 🤖
- [Sentence Transformers](https://www.sbert.net/) for embedding models 🔢
- [FAISS](https://faiss.ai/) for efficient similarity search 🎯
- [NLTK](https://www.nltk.org/) for text processing 📝
