CURA – AI Medical Chatbot 🩺🤖

CURA is an AI-powered medical chatbot that uses a Retrieval-Augmented Generation (RAG) pipeline to provide accurate, context-aware healthcare Q&A.
It integrates Flask (backend), LangChain, HuggingFace embeddings, Pinecone vector DB, and Google Gemini LLM.

🚀 Features

RAG Pipeline: Retrieves relevant knowledge chunks before generating an answer.

Vector Search: Pinecone for semantic similarity search over medical PDFs.

Generative AI: Google Gemini (via LangChain) for context-aware responses.

Web Interface: Flask + HTML/CSS front-end for interactive Q&A.

Extensible: Modular design with custom prompts and retriever/LLM chaining.

Containerized: Deployable with Docker and Google Cloud Run.

📂 Project Structure
DATA/                   # Knowledge base + preprocessed embeddings
│   ├── embedding.pkl
│   ├── extracted_data.pkl
│   ├── text_chunk.pkl
│   └── The-Gale-Encyclopedia-of-Medicine.pdf

research/               # Experiments & notebooks
│   └── trials.ipynb

src/                    # Core backend modules
│   ├── __init__.py
│   ├── helper.py       # PDF loader, text splitter, embedding utils
│   └── prompt.py       # System + user prompts

static/                 # Static assets
│   └── style.css

templates/              # Frontend templates
│   └── index.html

app.py                  # Flask app with RAG pipeline
store_index.py          # Script to ingest PDFs & build Pinecone index
requirements.txt        # Python dependencies
dockerfile              # Docker instructions
app.yaml                # GCP App Engine config (optional)
setup.py                # Python packaging metadata
template.sh             # Helper script
.gcloudignore / .gitignore
README.md

⚙️ Installation
# Clone the repo
git clone https://github.com/your-username/CURA.git
cd CURA

# Setup environment
python -m venv venv
source venv/bin/activate  # (Windows: venv\Scripts\activate)

# Install dependencies
pip install -r requirements.txt

🔑 Environment Variables

Create a .env file in the root:

PINECONE_API_KEY=your_pinecone_api_key
GOOGLE_API_KEY=your_google_api_key

▶️ Usage

Prepare the index:

python store_index.py


Run the chatbot:

python app.py


or for production:

gunicorn -b 0.0.0.0:8080 app:app


Access the app at: http://localhost:8080

🐳 Docker & Cloud Run
# Build locally
docker build -t cura-chatbot .

# Run locally
docker run -p 8080:8080 cura-chatbot

# Deploy to Cloud Run
gcloud run deploy cura-chatbot --source . --allow-unauthenticated --region asia-south1

📊 Tech Stack

Backend: Flask, Gunicorn

LLM & RAG: LangChain, HuggingFace Embeddings, Google Gemini LLM

Vector DB: Pinecone

Frontend: HTML, CSS (Flask templates)

Deployment: Docker, Google Cloud Run / App Engine

👤 Author

Jatin Bagga
📧 aloc1345@gmail.com
