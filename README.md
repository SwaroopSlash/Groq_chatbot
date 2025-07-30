# Llama-Powered MultiPDF Chatbot

A Streamlit-based chatbot application that allows users to upload multiple PDF documents and ask questions about their content using the power of Llama 3 language model and vector embeddings.

## Features

- **Multi-PDF Support**: Upload and process multiple PDF files simultaneously
- **Intelligent Q&A**: Ask questions about the content of uploaded PDFs
- **Vector Search**: Uses FAISS for efficient similarity search across document chunks
- **LLM Integration**: Powered by Llama 3 8B model via Groq API
- **Embeddings**: Uses HuggingFace sentence transformers for text embeddings
- **User-Friendly Interface**: Clean Streamlit web interface

## Prerequisites

- Python 3.8 or higher
- Groq API key

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd pdf-chatbot
```

2. Install required dependencies:
```bash
pip install streamlit PyPDF2 langchain langchain-groq langchain-community transformers torch faiss-cpu python-dotenv
```

3. Create a `.env` file in the root directory and add your Groq API key:
```
GROQ_API_KEY=your_groq_api_key_here
```

## Usage

1. Run the Streamlit application:
```bash
streamlit run app.py
```

2. Open your web browser and navigate to the provided local URL (typically `http://localhost:8501`)

3. Using the application:
   - Use the sidebar to upload one or more PDF files
   - Click "Submit & Process" to process the uploaded PDFs
   - Wait for the processing to complete
   - Ask questions about the PDF content in the main text input field
   - Get detailed answers based on the document content

## How It Works

### Document Processing
1. **PDF Text Extraction**: Extracts text from uploaded PDF files using PyPDF2
2. **Text Chunking**: Splits the extracted text into manageable chunks (1000 characters with 100 character overlap)
3. **Vector Embeddings**: Converts text chunks into vector embeddings using HuggingFace's sentence-transformers
4. **Vector Storage**: Stores embeddings in a FAISS vector database for efficient retrieval

### Question Answering
1. **Query Processing**: Converts user questions into vector embeddings
2. **Similarity Search**: Finds relevant document chunks using FAISS similarity search
3. **Context Building**: Provides relevant chunks as context to the language model
4. **Answer Generation**: Uses Llama 3 via Groq API to generate detailed answers

## Technical Components

- **Streamlit**: Web interface framework
- **PyPDF2**: PDF text extraction
- **LangChain**: Framework for LLM applications and document processing
- **FAISS**: Vector database for similarity search
- **HuggingFace Transformers**: Sentence embeddings model
- **Groq**: API access to Llama 3 language model

## Configuration

The application uses the following default settings:
- **Chunk Size**: 1000 characters
- **Chunk Overlap**: 100 characters
- **Embedding Model**: sentence-transformers/all-MiniLM-L6-v2
- **LLM Model**: Llama3-8b-8192 via Groq
- **Vector Store**: FAISS with local persistence

## File Structure

```
├── app.py                 # Main application file
├── .env                   # Environment variables (API keys)
├── requirements.txt       # Python dependencies
├── faiss_index/          # FAISS vector store (created after processing)
└── README.md             # This file
```

## Error Handling

The application includes basic error handling:
- Validates PDF file uploads
- Handles cases where answers are not available in the provided context
- Provides user feedback during processing

## Limitations

- Requires active internet connection for Groq API access
- Processing time depends on PDF size and number of documents
- Answer quality depends on the content and structure of uploaded PDFs
- FAISS index is stored locally and persists between sessions

## Getting Groq API Key

1. Visit [Groq Console](https://console.groq.com/)
2. Sign up or log in to your account
3. Navigate to API Keys section
4. Generate a new API key
5. Add the key to your `.env` file

## Contributing

Feel free to submit issues and enhancement requests. Pull requests are welcome!

## License

This project is open source. Please check the license file for details.
 
