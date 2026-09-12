# 🦜️ LangChain Preparation

A comprehensive learning and experimentation repository for mastering **LangChain** concepts, RAG (Retrieval Augmented Generation), and building AI-powered applications with Google GenAI.

## 📚 Overview

This repository serves as a structured preparation guide for LangChain development, covering everything from foundational concepts to advanced patterns like Retrieval Augmented Generation (RAG). Whether you're getting started with LLMs or building sophisticated AI applications, this repo provides practical examples and well-documented code.

## 🎯 What's Inside

### 📂 Project Structure

```
Langchain_Preparation/
├── basic_Langchain/          # Foundational LangChain concepts
│   └── Core components and getting started examples
├── chains_in_langchain/       # Building and composing chains
│   └── Sequential, parallel, and custom chain implementations
├── RAG/                       # Retrieval Augmented Generation
│   └── Document processing, embedding, and retrieval patterns
├── src/                       # Utility modules and helpers
└── pyproject.toml            # Project configuration and dependencies
```

### 📖 Learning Modules

#### 1. **Basic LangChain** (`basic_Langchain/`)
- LLM initialization and prompting
- Message and chat interfaces
- Output parsing
- Basic prompt templates
- Model integration with Google GenAI

#### 2. **Chains in LangChain** (`chains_in_langchain/`)
- Simple and sequential chains
- Branching and conditional chains
- Tool use and function calling
- Chain composition patterns
- Memory management in chains

#### 3. **RAG Implementation** (`RAG/`)
- Document loading and preprocessing
- Text splitting and chunking
- Embedding generation
- Vector store operations
- Semantic search and retrieval
- End-to-end RAG pipeline

## 🚀 Quick Start

### Prerequisites

- **Python**: 3.12 or higher
- **uv**: Package manager (recommended) or pip
- **API Keys**: Google Generative AI API key

### Installation

#### Using `uv` (Recommended)
```bash
# Clone the repository
git clone https://github.com/KomalKumarma/Langchain_Preparation.git
cd Langchain_Preparation

# Install dependencies
uv sync
```

#### Using pip
```bash
# Clone the repository
git clone https://github.com/KomalKumarma/Langchain_Preparation.git
cd Langchain_Preparation

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Environment Setup

Create a `.env` file in the root directory with your API credentials:

```bash
# .env
GOOGLE_API_KEY=your_google_genai_api_key_here
```

Obtain your Google API key from [Google AI Studio](https://makersuite.google.com/app/apikey).

## 🔧 Core Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| `langchain` | ≥0.1.0 | Core LangChain framework |
| `langchain-community` | ≥0.4.2 | Community integrations |
| `langchain-google-genai` | 4.3.7 | Google Generative AI integration |
| `pypdf` | ≥6.18.0 | PDF processing for RAG |
| `wikipedia` | ≥1.4.0 | Wikipedia API integration |
| `python-dotenv` | ≥0.9.9 | Environment variable management |

## 💡 Usage Examples

### Basic LLM Invocation
```python
from langchain_google_genai import ChatGoogleGenerativeAI
from langchain_core.prompts import ChatPromptTemplate

# Initialize the model
llm = ChatGoogleGenerativeAI(model="gemini-pro")

# Create a prompt template
prompt = ChatPromptTemplate.from_template(
    "What is a good name for a company that makes {product}?"
)

# Create a simple chain
chain = prompt | llm

# Invoke the chain
response = chain.invoke({"product": "colorful socks"})
print(response.content)
```

### Building a Chain
```python
from langchain_core.runnables import RunnableSequence

# Chain multiple components
chain = (
    {"topic": RunnablePassthrough()}
    | prompt_template
    | llm
    | output_parser
)

result = chain.invoke("machine learning")
```

### Simple RAG Pipeline
```python
from langchain_community.document_loaders import PyPDFLoader
from langchain_text_splitters import RecursiveCharacterTextSplitter
from langchain_community.vectorstores import FAISS
from langchain_google_genai import GoogleGenerativeAIEmbeddings

# Load documents
loader = PyPDFLoader("document.pdf")
documents = loader.load()

# Split documents
splitter = RecursiveCharacterTextSplitter(chunk_size=1000)
chunks = splitter.split_documents(documents)

# Create embeddings
embeddings = GoogleGenerativeAIEmbeddings()

# Build vector store
vectorstore = FAISS.from_documents(chunks, embeddings)

# Query
results = vectorstore.similarity_search("your query")
```

## 📝 Features

✅ **Comprehensive Examples** - From basics to advanced patterns  
✅ **RAG Implementation** - Full-stack retrieval augmented generation  
✅ **Google GenAI Integration** - Ready-to-use Google Generative AI setup  
✅ **PDF Processing** - Extract and process document content  
✅ **Well-Documented** - Clear comments and docstrings throughout  
✅ **Production-Ready** - Best practices and patterns included  
✅ **Environment Configuration** - Easy setup with .env files  

## 🎓 Learning Path

1. **Start Here**: `basic_Langchain/` - Understand LLM fundamentals
2. **Build Chains**: `chains_in_langchain/` - Master composition and orchestration
3. **Advanced Patterns**: `RAG/` - Implement retrieval and augmentation
4. **Experiment**: Use `src/` utilities to build your own applications

## 📚 Resources

- [LangChain Documentation](https://python.langchain.com/)
- [Google Generative AI](https://ai.google.dev/)
- [LangChain Cookbook](https://github.com/langchain-ai/langchain/blob/master/COOKBOOK.md)
- [RAG Explained](https://arxiv.org/abs/2307.09288)

## 🔍 Running Examples

To run any example file:

```bash
# Using Python directly
python basic_Langchain/example_file.py

# Or using uv
uv run basic_Langchain/example_file.py
```

## 🛠️ Development

### Code Structure
- Clean, modular code with single responsibility principle
- Comprehensive error handling
- Type hints throughout
- Detailed docstrings and comments

### Best Practices
- Always load environment variables before API calls
- Use structured prompt templates
- Implement proper error handling for API calls
- Test with small datasets first
- Monitor token usage for cost efficiency

## 📋 Checklist for Beginners

- [ ] Set up environment and install dependencies
- [ ] Create and configure `.env` file with API keys
- [ ] Run a basic LLM example from `basic_Langchain/`
- [ ] Create your first simple chain
- [ ] Experiment with different prompt templates
- [ ] Implement a basic RAG example
- [ ] Explore Google GenAI capabilities
- [ ] Build your own project using these patterns

## ⚠️ Important Notes

1. **API Keys**: Never commit `.env` files or API keys to version control
2. **Rate Limits**: Be aware of API rate limits when experimenting
3. **Costs**: Monitor your API usage as it may incur costs
4. **Python Version**: Requires Python 3.12+
5. **Dependencies**: All dependencies are pinned in `uv.lock` for reproducibility

## 🚨 Troubleshooting

### Common Issues

**Import Error: `langchain_google_genai` not found**
```bash
# Reinstall dependencies
uv sync --reinstall
# or
pip install langchain-google-genai==4.3.7
```

**API Key Not Found**
- Ensure `.env` file exists in the root directory
- Verify the variable name matches: `GOOGLE_API_KEY`
- Check that the API key is valid

**Python Version Mismatch**
```bash
# Check your Python version
python --version

# If needed, install Python 3.12+
```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the MIT License.

## 👤 Author

**Komal Kumar**

- GitHub: [@KomalKumarma](https://github.com/KomalKumarma)
- Institution: Sri Siddhartha Institute of Technology (SSIT), Karnataka, India

## 🙋 Support

Have questions or issues? 

- 📖 Check the [LangChain docs](https://python.langchain.com/)
- 🐛 Open an [Issue](https://github.com/KomalKumarma/Langchain_Preparation/issues)
- 💬 Start a [Discussion](https://github.com/KomalKumarma/Langchain_Preparation/discussions)

## 🌟 Acknowledgments

- LangChain team for the amazing framework
- Google for the Generative AI API
- Open source community for libraries and tools

---

**Happy Learning! 🚀**

*Last Updated: 2024 | Made with ❤️ for the LLM community*
