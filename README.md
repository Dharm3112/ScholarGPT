# 🧠 ScholarGPT: Chat with Your Data

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-1.32-red)
![LangChain](https://img.shields.io/badge/LangChain-RAG-green)
![HuggingFace](https://img.shields.io/badge/HuggingFace-Mistral--7B-yellow)

**ScholarGPT** is a Generative AI application that acts as a personal research assistant. It uses **Retrieval-Augmented Generation (RAG)** to allow users to upload PDF documents (textbooks, research papers, notes) and ask questions about them in natural language.

Unlike standard chatbots, ScholarGPT answers based *only* on the document you provide, eliminating hallucinations and making it perfect for academic study.

---

## ⚙️ How It Works (The "Crazy" Tech)
This project implements a sophisticated RAG pipeline:

1.  **Ingestion:** The PDF text is extracted using `pypdf`.
2.  **Chunking:** Text is split into smaller chunks (1000 characters) to fit into the AI's context window.
3.  **Embedding:** We use **HuggingFace Embeddings** (`all-MiniLM-L6-v2`) to convert text chunks into numerical vectors.
4.  **Vector Store:** These vectors are stored in a local **FAISS** database for ultra-fast similarity search.
5.  **Retrieval & Generation:** When you ask a question, the system finds the most relevant text chunks and sends them—along with your question—to the **Mistral-7B** LLM via HuggingFace Inference API to generate a precise answer.



---

## 🛠️ Tech Stack
* **Language:** Python
* **Frontend:** Streamlit (Custom Dark Theme)
* **LLM Orchestration:** LangChain
* **Generative Model:** Mistral-7B (via HuggingFace Hub)
* **Embeddings:** Sentence-Transformers (HuggingFace)
* **Vector Database:** FAISS (Facebook AI Similarity Search)

---

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone [https://github.com/Dharm3112/ScholarGPT.git](https://github.com/Dharm3112/ScholarGPT.git)
cd ScholarGPT

```

### 2. Create a Virtual Environment (Recommended)

```bash
# Windows
python -m venv .venv
.\.venv\Scripts\activate

# Mac/Linux
python3 -m venv .venv
source .venv/bin/activate

```

### 3. Install Dependencies

```bash
pip install -r requirements.txt

```

### 4. Set Up API Keys

1. Get a free Access Token from [HuggingFace](https://huggingface.co/settings/tokens).
2. Create a file named `.env` in the project root.
3. Add your token inside:
```
HUGGINGFACEHUB_API_TOKEN=hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxx

```



---

## 🏃‍♂️ Usage

Run the application using Streamlit:

```bash
streamlit run app.py

```

1. The app will open in your browser (`http://localhost:8501`).
2. Use the sidebar to **Upload** your PDF files.
3. Click **"Process"** and wait for the "Done!" notification.
4. Ask any question in the chat box!

---

## 📂 Project Structure

```
ScholarGPT/
├── app.py                # Main application logic
├── htmlTemplates.py      # CSS and HTML for Chat UI
├── requirements.txt      # Project dependencies
├── .env                  # API keys (Not uploaded to GitHub)
├── .gitignore            # Files to ignore (env, venv, etc.)
└── README.md             # Project documentation

```

---

## 🐛 Troubleshooting

* **`ModuleNotFoundError`:** Ensure your virtual environment is activated (`(.venv)` should appear in your terminal).
* **Push Rejected by GitHub:** Check if you accidentally committed your `.env` file. If so, use `git reset` to remove it from history.
* **HuggingFace Error:** Ensure your API token has "Read" permissions and is pasted correctly in `.env` without quotes.

---

## 🔮 Future Improvements

* Add "Memory" so the bot remembers context from previous questions.
* Deploy to Streamlit Cloud for public access.
* Add support for DOCX and TXT files.

---

## 📜 License

This project is open-source and available under the [MIT License](https://github.com/Dharm3112/ScholarGPT/blob/main/LICENSE).
