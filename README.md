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
anud/
│
├── backend.py                # LangGraph setup and state logic
├── backend_func_rag.py       # RAG pipeline using LangChain and Qdrant
├── backend_func_weather.py   # Weather data fetch using OpenWeatherMap API
├── backend_route.py          # Router to classify between 'weather' and 'rag'
├── frontend.py               # Streamlit UI for chat
├── .env                      # Contains API keys and LangSmith setup
└── store/                    # Local Qdrant vector database files
