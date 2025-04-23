# Legal AEye-Opener

## Overview
Legal AEye-Opener is an AI-powered legal assistant designed to help users navigate and understand legal texts from the BNS (Bharatiya Nyaya Sanhita) laws. The application allows users to search for specific sections or ask legal questions and get AI-generated responses with relevant legal context.

## Features
- **Section-Based Search**: Easily search for specific sections of the BNS law by number (e.g., "Section 121" or "Sections 100-105")
- **Natural Language Queries**: Ask questions in plain English and get AI-generated responses
- **AI-Powered Insights**: Uses Groq's LLama3-70B model to provide relevant and accurate legal information
- **Chat History**: Keeps track of your conversation for context and future reference
- **Source Citations**: Provides links to the original legal documents

## Technical Architecture
### Backend Components
- **Flask Web Server**: Handles HTTP requests and renders the web interface
- **Sentence Transformers**: Provides embeddings for semantic search capabilities
- **ChromaDB**: Vector database for storing and retrieving legal document embeddings
- **Groq LLM Integration**: Connects to Groq's LLM API for generating responses
- **Document Processing**: Extracts, processes, and summarizes legal texts

### Database
- **ChromaDB**: A persistent vector database that stores:
  - Legal document embeddings
  - Section metadata
  - Section summaries
  - Source URLs

## Installation

### Prerequisites
- Python 3.9 or higher
- Pip package manager
- A Groq API key (get one at [https://console.groq.com](https://console.groq.com))

### Setup
1. Clone the repository:
   ```
   git clone https://github.com/Rhushya/legal-ai.git
   cd legal-ai
   
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Set up your environment variables:
   ```
   # Linux/Mac
   export GROQ_API_KEY="your_groq_api_key"
   
   # Windows (Command Prompt)
   set GROQ_API_KEY=your_groq_api_key
   
   # Windows (PowerShell)
   $env:GROQ_API_KEY="your_groq_api_key"
   ```
   you need to add groq api key in groq_llm and app.py file or you can create a env file and then intergrate with it also
    

## Usage

1. Start the Flask application:
   ```
   python app.py
   ```

2. Open your web browser and navigate to:
   ```
   http://127.0.0.1:5000/
   ```

3. Use the application by:
   - Asking specific section-based questions (e.g., "Show me section 302")
   - Requesting section ranges (e.g., "From section 120 to section 130")
   - Asking natural language questions (e.g., "What is the punishment for theft?")

## Data Update Process

To update the legal database with fresh information:

1. Run the database update script:
   ```
   python update_chromadb.py
   ```

This script:
- Scrapes legal sections from the source website (devgan.in)
- Processes and extracts structured data
- Generates embeddings and summaries
- Saves everything to ChromaDB and backup files

## Project Structure
- `app.py` - Main Flask application
- `update_chromadb.py` - Script to update the legal database
- `requirements.txt` - Python dependencies
- `llms/groq_llm.py` - Groq LLM integration class
- `templates/` - HTML templates for the web interface
- `chroma_db/` - ChromaDB vector database files

## Technologies Used
- **Flask**: Web framework
- **Sentence Transformers**: Embedding model
- **ChromaDB**: Vector database
- **Groq API**: LLM provider
- **LangChain**: LLM integration framework
- **Beautiful Soup**: Web scraping
- **FAISS**: Vector similarity search (backup)
- **Hugging Face Transformers**: Text summarization

## Limitations
- Currently only covers BNS (Bharatiya Nyaya Sanhita) laws
- Maximum of 358 sections available
- Query context limited to 6000 characters

## Future Improvements
- Add support for additional legal codes (IPC, CPC, etc.)
- Implement multi-modal capabilities (document image analysis)
- Enhance UI with responsive design
- Add user authentication and session persistence
- Implement citation verification and fact-checking


## Acknowledgments
- Data sourced from devgan.in legal repository
- Powered by Groq's LLama3-70B model