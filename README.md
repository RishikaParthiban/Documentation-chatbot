# 📘 Documentation Chatbot  
An interactive chatbot that helps you **search, summarize, and query your PDF documents** using embeddings, ChromaDB, and Google Gemini.  
This project lets you upload one or more PDFs, automatically parses them into chunks, stores them in a vector database, and answers your questions with relevant context.  

## 🚀 Features  
- 📂 **Upload PDFs** directly in Colab  
- 📑 **Automatic text extraction** from all PDF pages  
- 🧩 **Chunk storage in ChromaDB** with embeddings  
- 🔎 **Semantic search & retrieval** using `sentence-transformers`  
- 🤖 **Answer generation** powered by Google Gemini (`gemini-2.5-flash`)  
- 💬 **Interactive Q&A loop** for follow-up questions  

## 🛠️ Installation  

Clone this repository and install dependencies:  

```bash
git clone https://github.com/your-username/documentation-chatbot.git
cd documentation-chatbot
pip install -r requirements.txt
Or if running on Google Colab, dependencies are installed automatically:

python
Copy code
!pip install -q PyPDF2 sentence-transformers chromadb google-generativeai
⚙️ Setup
Google Gemini API Key
Get an API key from Google AI Studio.
Replace the placeholder in the script:
python
Copy code
GEN_API_KEY = "your_api_key_here"
ChromaDB Persistence
Vector embeddings are stored locally in docs_db/.
This allows reusing the database without re-processing PDFs.

▶️ Usage
1. Upload PDFs
python
Copy code
from google.colab import files
uploaded = files.upload()
2. Parse and Store in DB
python
Copy code
json_file = parse_folder("uploaded_pdfs")
count = store_in_vector_db(json_file)
print(f"✅ Stored {count} chunks from uploaded PDFs.")
3. Ask Questions
python
Copy code
query = "Summarize all uploaded documents."
results = retrieve(query, n_results=8)
print(generate_answer(query, results))
Or interactively:

python
Copy code
while True:
    query = input("❓ Ask a question (or type 'exit'): ")
    if query.lower() in ["exit", "quit"]:
        break
    results = retrieve(query, n_results=8)
    print("\n🤖 Answer:\n", generate_answer(query, results), "\n")
📂 Project Structure
graphql
Copy code
📁 documentation-chatbot
 ├── Documentation Chatbot.ipynb   # Main Colab notebook
 ├── parsed_pdfs.json              # Extracted PDF chunks (auto-generated)
 ├── docs_db/                      # ChromaDB persistent storage
 ├── uploaded_pdfs/                # Uploaded PDF files
 └── README.md                     # Project documentation
📦 Requirements
Python 3.8+

PyPDF2
sentence-transformers
chromadb
google-generativeai

🔒 Notes
Make sure your API key is kept private (don’t commit it to GitHub).
Large PDFs may take time to process due to embedding generation.

🙌 Acknowledgements
Sentence Transformers for embeddings
ChromaDB for vector storage
Google Gemini for LLM-powered answers
