# Rag_originbluy


# Retrieval-Augmented Generation (RAG) System with Mistral & ChromaDB

This project implements a lightweight Retrieval-Augmented Generation (RAG) pipeline using a local LLM (Mistral 7B) and ChromaDB as the vector store. The system is designed to run seamlessly in Kaggle environments and supports PDF, image, DOCX, and text files.

##  Project Structure

- **Input files**: `.pdf`, `.docx`, `.txt`, image files
- **Document processing**: Text extraction using EasyOCR, pdf2image, and PyMuPDF
- **Embedding generation**: HuggingFace Embeddings
- **Vector Store**: ChromaDB
- **LLM Integration**: Local Mistral 7B model
- **RAG Pipeline**: LangChain components

##  Features

- Accepts multi-format input documents
- Extracts and splits text into chunks
- Embeds chunks and stores in ChromaDB
- Retrieves relevant chunks using semantic similarity
- Answers queries using a local Mistral model

##  Dependencies

Install the required libraries in Kaggle or locally:

```bash
pip install -q langchain chromadb huggingface_hub pdf2image pymupdf easyocr python-docx opencv-python
```

Make sure your local model is available under:

```
/kaggle/input/mistral/pytorch/7b-instruct-v0.1-hf/1
```


## 📚 How It Works

1. **Load Documents**  
   Supported formats include `.pdf`, `.docx`, `.txt` files.Provide path to your documents in main() to documents_paths[].

2. **Extract Text**  
   OCR is used for scanned PDFs and images via `EasyOCR`. Text-based PDFs are parsed using `PyMuPDF`.Docx and TXTs are also processed.

3. **Split and Embed**  
   Documents are split , and vector embeddings are created via HuggingFace models.

4. **Store in ChromaDB**  
   Chunks are stored in ChromaDB with corresponding metadata.

5. **Querying**  
   On user query, top 3 srelevant chunks are retrieved and passed to Mistral 7B using LangChain’s RAG chain.

## 🧪 Example Query and  Demo Video

Watch the full demo of the RAG pipeline in action here:

🔗 [RAG System Demo – Google Drive](https://drive.google.com/file/d/1gf1Y0_CAo2j5m5X9CXcZ-Gsv4JLl7UQ7/view?usp=drive_link)

## 🧠 Model Details

- **Model**: [Mistral 7B Instruct](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.1)
- **Embedding Model**: Sentence Transformers from HuggingFace
- **Vector Store**: ChromaDB (persistent and in-memory)

##  Notes

- For scanned PDFs, ensure OCR is enabled.
- Clear old data between runs if needed: delete files in `/mnt/data` or reset ChromaDB.

