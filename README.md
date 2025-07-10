# PDFassistant


This project is an AI-powered assistant that reads a PDF, understands it, and answers questions about its content. It’s built using a multi-agent approach in Python and uses smart tools like vector databases and language models to work efficiently.

What It Does:

- Reads and splits a PDF file into smaller pieces (chunks)
- Converts each chunk into embeddings using Nomic Embed Text
- Stores those embeddings in a PostgreSQL database using pgvector
- When you ask a question, it finds the most relevant chunks
- Sends those chunks to the Groq LLaMA 3 language model
- Returns a helpful, accurate answer based on the PDF content

Tools and Technologies:

- Python: Core programming language
- Jupyter Notebook: To run the assistant step by step
- Nomic Embed Text: Free service to turn text into vector embeddings
- pgvector + PostgreSQL: Stores and retrieves chunks by similarity
- Groq (LLaMA 3): Fast and powerful AI model for answering questions
- LangChain & LangGraph: Frameworks used to chain everything together


Why Use pgvector and Embeddings?
We don’t send the full PDF to the AI model because:

- Language models have a token limit (e.g., Groq LLaMA 3 supports only ~8192 tokens max)
- Long PDFs are often too big to send entirely
- It would be slow and expensive

Instead, we:
1. Break the PDF into small parts
2. Convert each part into an embedding
3. Store those embeddings in pgvector (a smart database)
4. Retrieve only the relevant chunks when a question is asked
5. Send those to the AI model for a fast and accurate answer

This approach is:
-  Faster
-  Cheaper
-  Smarter
-  Scalable (can handle large or multiple PDFs)

How to Use:

1. Install Docker Desktop and run PostgreSQL with pgvector, run the following piece  of code on bash and you're good to go;

   docker run -d \
     -p 5532:5432 \
     -e POSTGRES_DB=ai \
     -e POSTGRES_USER=ai \
     -e POSTGRES_PASSWORD=ai \
     agnohq/pgvector:16
