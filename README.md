Mini RAG Q&A System 🌌

A lightweight implementation of a Retrieval-Augmented Generation (RAG) system designed to answer questions about the Solar System. This project demonstrates the core components of a RAG pipeline: embedding generation, vector similarity search, context-aware answer generation, and automated evaluation.


🚀 Features

Vector Search: Uses FAISS and Sentence Transformers to perform semantic search over a text knowledge base.

Generative AI: Integrates Google's Gemini 2.5 Flash model to generate natural language answers based only on retrieved context.

Automated Evaluation: Includes a "Judge" LLM feature that evaluates the relevance and faithfulness of the system's answers on a 1-5 scale.

Interactive CLI: Simple command-line loop for testing queries in real-time.

🛠️ Tech Stack

Python 3.x

Sentence Transformers: For generating dense vector embeddings (all-MiniLM-L6-v2).

FAISS: For efficient similarity search and clustering of dense vectors.

Google Generative AI SDK: For accessing the Gemini API.

📦 Installation

Clone the repository:

git clone [https://github.com/yourusername/mini-rag-system.git](https://github.com/yourusername/mini-rag-system.git)
cd mini-rag-system


Install the required Python packages:

pip install faiss-cpu sentence_transformers google-generativeai numpy


⚙️ Configuration

To use the generative and evaluation features, you need a Google AI Studio API key.

Get an API key from Google AI Studio.

The script looks for the key in your environment variables or prompts you for it at runtime.

Option A: Set Environment Variable (Recommended)

export GEMINI_API_KEY="your_api_key_here"


Option B: Runtime Input
Simply run the script, and it will ask you to paste your key if it's not found in the environment.

📖 Usage

You can run the system directly as a Python script or within a Jupyter Notebook.

python rag_system.py
# Or open the notebook
jupyter notebook Samith_Kamarthi_NLP_Assignment_Mini_RAG_Q&A_System.ipynb


Example Interaction

❓ Enter your question: which is the largest planet
   🔎 Retrieving relevant chunks...

   📄 Retrieved Context:
      1. Jupiter is the largest planet in the Solar System...
      2. Neptune is the eighth and farthest-known Solar planet...

   🤖 Generating Answer...
   >> Answer: Jupiter is the largest planet in the Solar System.

   ⚖️  Evaluating Response...
   >> Evaluation:
   Score: 5
   Explanation: The retrieved context directly answers the user's question...


🧠 How It Works

The system follows a standard RAG architecture:

Knowledge Base: A curated list of facts about the Solar System is loaded.

Embedding: The all-MiniLM-L6-v2 model converts these text chunks into numerical vectors.

Indexing: FAISS builds an index (IndexFlatL2) to allow for fast Euclidean distance searches.

Retrieval: When a user asks a question, it is embedded, and the top-k most similar chunks are retrieved from the index.

Generation: A prompt is constructed containing the user's question and the retrieved text. The Gemini model is instructed to answer using only that context.

Evaluation: A separate LLM call acts as a judge, rating the answer's quality based on context relevance and hallucination checks.

📄 License

This project is open-source and available for educational purposes.