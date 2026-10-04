# Secure Enterprise RAG Platform

A production-ready, full-stack Retrieval-Augmented Generation (RAG) platform tailored for enterprise environments. This project provides a secure way for teams to upload, index, and query documents with granular access controls and audit logging.

## ✨ Enterprise Features (Roadmap)
- **Role-Based Access Control (RBAC):** Restrict system access based on user roles (Admin, Manager, User).
- **Document-Level Permissions:** Authorization-aware retrieval ensures users can only query documents they have explicit access to.
- **Audit Logging:** Comprehensive tracking of all document uploads, queries, and system actions.
- **Authentication:** Secure integration with enterprise identity providers (JWT / OAuth2).

## 🏗️ Architecture

### Tech Stack
- **Backend:** FastAPI (Python 3.11), LangChain, Pydantic
- **Frontend:** React 18, TypeScript, Vite
- **Vector Store:** ChromaDB
- **LLM/Embeddings:** Anthropic Claude (or OpenAI), Sentence Transformers

### Document Ingestion & Retrieval
1. **Ingestion:** Uploaded documents (PDF, TXT, DOCX) are chunked and converted into embeddings via local Sentence Transformers (`all-MiniLM-L6-v2`).
2. **Storage:** Embeddings are stored securely in ChromaDB along with ownership and permission metadata.
3. **Retrieval:** User queries are matched against authorized documents in ChromaDB using semantic search.
4. **Generation:** The context is sent to the configured LLM to generate a cited response.

## 🚀 Setup Instructions

### Prerequisites
- Python 3.11 (Required for `chromadb` compatibility)
- Node.js 18+

### 1. Backend Setup
```bash
cd backend

# Create and activate virtual environment (Must use Python 3.11)
py -3.11 -m venv venv
venv\Scripts\activate  # Windows
# source venv/bin/activate  # macOS/Linux

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env
```

Edit `.env` to include your LLM provider API keys.

```bash
# Start the server
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```
The backend API documentation will be available at `http://localhost:8000/docs`.

### 2. Frontend Setup
Open a new terminal window:
```bash
cd frontend

# Install dependencies
npm install

# Configure environment variables (if required)
cp .env.example .env

# Start development server
npm run dev
```
The frontend will be available at `http://localhost:5173`.

## 📝 License
This project is licensed under the MIT License.
