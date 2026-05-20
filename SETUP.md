# MediBot — Setup Instructions

## Step 1: Install Ollama
Download from: https://ollama.ai
Run the installer. After installation, open Command Prompt and run:

    ollama serve
    ollama pull llama3

Keep the Ollama window open. This runs the LLM locally on your machine.

## Step 2: Install Python dependencies
Open a NEW Command Prompt in the project folder and run:

    pip install -r requirements.txt

This may take 5-10 minutes (downloads sentence-transformers model ~90MB).

## Step 3: Run the app

    python app.py

## Step 4: Open the app
Go to: http://localhost:5000

---

## Project Structure

    medical_chatbot/
    ├── app.py              # Main Flask application
    ├── requirements.txt    # Python dependencies
    ├── SETUP.md            # This file
    ├── templates/
    │   └── index.html      # Chat UI
    ├── uploads/            # Uploaded PDFs stored here
    └── chroma_db/          # Vector database (auto-created)

---

## How to use

1. CHAT MODE    — Ask any medical question in the chat box
2. SYMPTOM MODE — Click "Symptom Checker", describe symptoms, get assessment
3. PDF UPLOAD   — Upload any medical PDF (textbooks, reports) to expand knowledge
4. SOURCES      — Hover over source chips to see which document answered your question

---

## Troubleshooting

Problem: "LLM Error" in chat
Solution: Make sure Ollama is running (ollama serve) and llama3 is downloaded

Problem: Slow first response
Solution: Normal — Llama3 takes 10-30 seconds on first load

Problem: Import errors
Solution: pip install -r requirements.txt again

Problem: Port 5000 already in use
Solution: Change port in app.py last line: app.run(port=5001)
