Markdown
# PrismRAG 
> **Multimodal Retrieval-Augmented Generation (RAG) Engine** for Complex PDF Documents

PrismRAG is an advanced Multimodal RAG pipeline built with **LangChain**, **Unstructured**, **ChromaDB**, and **Google Gemini**. Just as a prism refracts light into its constituent spectrum, PrismRAG breaks down complex, heterogeneous documents (PDFs) into their core structured elements,narrative text, multi-row tables, embedded images, and figure captions indexing them seamlessly for hyper-accurate context retrieval and multimodal reasoning.

---

##  Key Features

- **Complex Document Layout Parsing**: Utilizes `Unstructured` to parse PDFs while preserving layout structure, section headings, text blocks, tables, and embedded images.
- **Multimodal Element Extraction**:
  - **Narrative Text & Captions**: Chunked and structured by document hierarchy.
  - **Tables**: Preserved in raw HTML/Markdown format for relational structured retrieval.
  - **Embedded Images**: Base64-encoded and processed via Google Gemini for multimodal summary generation and indexing.
- **Vector Search & Indexing**: Powered by **ChromaDB** for fast, high-density vector similarity retrieval.
- **Google Gemini Integration**: Employs Gemini for both multimodal embedding extraction and context-aware natural language generation.

---



## Quickstart Guide
1. Prerequisites
Ensure you have Python 3.10+ installed along with system dependencies required for PDF parsing and OCR:

Bash
# Ubuntu / Debian
sudo apt-get update
sudo apt-get install -y poppler-utils tesseract-ocr
2. Installation
Clone the repository and install required dependencies:

Bash
git clone (https://github.com/ayush-yogi11/PrismRAG)
cd PrismRAG

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

pip install -r requirements.txt
3. Environment Configuration
Create a .env file in the root directory of your project and add your Google Gemini API Key:

Code snippet
# .env file
GEMINI_API_KEY=your_google_gemini_api_key_here
 Important: You must provide your own Gemini API key in the .env file for multimodal summarization, embedding generation, and query answering. You can obtain a free key from Google AI Studio.

 Usage
1. Document Ingestion & Indexing
Run the indexing pipeline to process your documents, extract multimodal elements, and store embeddings in ChromaDB:

Python
from prismrag.pipeline import PrismRAGPipeline

# Initialize PrismRAG pipeline
pipeline = PrismRAGPipeline(data_dir="./data/pdfs")

# Process documents and index into ChromaDB
pipeline.ingest_and_index()
2. Querying the Pipeline
Retrieve context across text, tables, and images to generate structured multimodal answers:

Python
query = "What does Figure 3 show regarding performance, and what are the matching numbers in Table 2?"

response = pipeline.query(query)
print("Answer:\n", response)
 Tech Stack
Framework: LangChain / LangChain-Community

Parsing: Unstructured PDF Loader & Layout Analyzer

Multimodal LLM: Google Gemini (gemini-3.6-flash)

Vector Store: ChromaDB

Environment Management: python-dotenv

