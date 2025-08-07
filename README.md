# AI Engineer Assignment – LangGraph + RAG + Weather App

This project is a simple AI pipeline that does two main things:

-  **Fetches real-time weather data**
-  **Answers questions from a PDF document** using **RAG** (Retrieval-Augmented Generation)

##  Tech Stack

-  **LangGraph** – decides what the user is asking
-  **LangChain** – processes the data
-  **LLM** – Mistral via OpenRouter
-  **Embeddings** – HuggingFace
-  **Qdrant** – vector store for PDF content
-  **LangSmith** – tracing and evaluation
-  **Streamlit** – chat UI for user interaction

###  Project Structure
-  anud/
-  │
-  ├── backend.py                # LangGraph setup and state logic
-  ├── backend_func_rag.py       # RAG pipeline using LangChain and Qdrant
-  ├── backend_func_weather.py   # Weather data fetch using OpenWeatherMap API
-  ├── backend_route.py          # Router to classify between 'weather' and 'rag'
-  ├── frontend.py               # Streamlit UI for chat
-  ├── .env                      # Contains API keys and LangSmith setup
-  └── store/                    # Local Qdrant vector database files

## Setup Instructions

### 1. Clone or unzip the project

If you got a `.zip` file:

```bash
unzip anud.zip
cd anud
Or clone if it's in GitHub:
git clone <repo-link>
cd anud
```

### 2. Create a virtual environment
-  python -m venv venv
-  source venv/bin/activate

### 3. Install dependencies
```bash
pip install -r requirements.txt
# If requirements.txt is missing, install manually:
pip install langchain langgraph streamlit openai qdrant-client \
            langchain-openai langsmith python-dotenv \
            langchain-community langchain-huggingface \
            sentence-transformers
```
### 4. Add your .env file
-  Make a file called .env in the root folder and add the following
-  env
-  OPENWEATHERMAP_API_KEY=your_openweathermap_key

-  LANGSMITH_TRACING=true
-  LANGSMITH_ENDPOINT=https://api.smith.langchain.com
-  LANGSMITH_API_KEY=your_langsmith_key
-  LANGSMITH_PROJECT=default

Replace the keys with your actual:
-  OpenWeatherMap API key
-  LangSmith API key

### 5. Run the App
After setup is complete, run:
-  streamlit run frontend.py

You’ll see a simple chat interface.

How it Works:
You type a message in the chat (e.g., "What's the weather in Delhi?" or "Tell me about heart disease").

The LangGraph router classifies your message:

If it's about weather → it calls OpenWeatherMap.

If it’s a question → it uses RAG to search the PDF data stored in Qdrant.

It uses Mistral LLM to answer your query.

The conversation is shown in Streamlit UI.

LangSmith is used to trace and evaluate LLM performance (automatically done if enabled in .env).

### 6. Features
- Intelligent routing using LLM

- Real-time weather data from OpenWeatherMap

- PDF-based question answering via RAG

- LangSmith evaluation support

- Unit-test friendly structure (separate logic files)

- Streamlit-based chat interface



