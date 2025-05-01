

# AI - Chatbot Medico

This is an AI-powered medico chatbot designed to provide symptom-based diagnostic suggestions and healthcare guidance through natural language conversations. Built using LLaMA 2, LangChain, and Chainlit, the system is optimized to run on CPU-based machines for broad accessibility.

How It Works:
	1.	User Interaction:
Users describe their symptoms via a real-time chat interface powered by Chainlit.
	2.	Symptom Processing:
The input is converted into vector embeddings using SentenceTransformers, capturing semantic meaning.
	3.	Knowledge Retrieval:
The embeddings are compared against a pre-indexed medical knowledge base (fine-tuned from the Gale Encyclopedia of Medicine) using FAISS for fast similarity search.
	4.	Response Generation:
The most relevant medical chunks are passed as context to the LLaMA 2 model, which generates diagnostic suggestions and follow-up questions.
	5.	Contextual Dialogue:
LangChain orchestrates multi-turn conversations, maintaining symptom context and refining responses interactively.

Key Features:
	•	Works efficiently on standard CPUs (quantized model).
	•	Real-time chat UI for intuitive user experience.
	•	Medical context awareness from trusted encyclopedia data.
	•	Expandable via new medical PDFs and embeddings.

Steps to incorporate other PDFs of published journals and documents such as prescription/medical report into Knowledge Base:-

1. Parse the PDF
Extract readable content from the PDF using a library like PyPDF2, pdfplumber, or PyMuPDF.

2.Preprocess the Extracted Text
You want to clean the text and chunk it into smaller parts for embedding.

3. Generate Embeddings
Use SentenceTransformers to turn chunks into vector embeddings.

4. Store in FAISS Vector Database
Use FAISS to store embeddings for fast similarity search later.

5. Update Metadata (Text Lookup)
You need to maintain a mapping of embeddings to their original text chunks into vectorstore.

6. Connect the Updated Knowledge Base to the Chatbot
Modify your LangChain retriever (or whatever framework you’re using) to:
	•	Load the updated FAISS index
	•	Load the corresponding text chunks
	•	Run similarity search on user input
	•	Return top-matching chunks to LLaMA 2 for generation



![image](https://github.com/user-attachments/assets/ad618197-0eb7-42eb-a381-da813d7d3ab4)

