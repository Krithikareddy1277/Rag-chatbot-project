# PDF Chatbot with Retrieval-Augmented Generation

A command-line chatbot that answers questions about a PDF using a manual retrieval-augmented generation (RAG) pipeline. It extracts PDF text, splits it into chunks, creates sentence embeddings, searches ChromaDB for relevant chunks, and sends the retrieved context to an OpenRouter chat model.

## Requirements

- Python
- An OpenRouter API key
- A PDF to use as the chatbot's knowledge source

## Setup

1. Clone the repository and open a terminal in its directory.
2. Create and activate a virtual environment:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

3. Install dependencies:

   ```powershell
   pip install -r requirements.txt
   ```

4. Create your local environment file from the template:

   ```powershell
   Copy-Item .env.example .env
   ```

   Edit `.env` and set `OPENROUTER_API_KEY` to your own key. Do not commit or share `.env`.

5. Put the PDF you want to query at `data/sample.pdf`. Create the `data` directory if needed. The PDF is not included in this repository.

## Run

From the repository directory, run:

```powershell
python app.py
```

Ask questions in the terminal. Type `exit` to stop the chatbot. The first run may download the `all-MiniLM-L6-v2` embedding model. ChromaDB stores its generated database in `chroma_db/`.

## Configuration

- `OPENROUTER_API_KEY` — required API key used to generate answers.
- The chat model is configured in `config.py`.
- The embedding model and PDF path are configured in the project source.

## Notes

The chatbot uses retrieved PDF chunks as context for its answers. For best results, use a text-based PDF with extractable text.