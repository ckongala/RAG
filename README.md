# Building My Own RAG Model: Meet “MICROBOT”

Artificial Intelligence is evolving at lightning speed, and one of the hottest concepts powering real-world applications today is **RAG — Retrieval-Augmented Generation**.

Sounds technical? Don’t worry. In this blog, I’ll break it down in **simple terms**, walk you through **how I built my own RAG model (MICROBOT)**, and show you why it’s such a **game-changer** in the AI space.

## What is RAG (Retrieval-Augmented Generation)?

At its core, RAG is about making AI systems **smarter and more reliable**.

Without RAG, a Large Language Model (LLM) answers based only on what it learned during training. That often leads to **hallucinations** answers that *sound* correct but aren’t grounded in real data.

With RAG:

* **Retrieval**: The system pulls relevant chunks of information from a custom **data store** (like your documents, PDFs, or databases).
* **Augmented Generation**: These retrieved chunks are added to the **prompt** and passed to the LLM for **text generation**.

This combination gives **factual, contextrich, and optimized responses**.

Think of RAG as an **AI pipeline** that reduces the hallucination of LLMs by connecting them directly to your **source of truth**.

## My Project: MICROBOT

To make things practical, I decided to **build a RAG model based on my resume and personal data**.

The result? **MICROBOT** — a personal AI assistant that:

* Retrieves relevant chunks from my resume
* Parses the data to answer queries about my skills, projects, and background
* Generates clear, context-aware answers

Now, instead of scrolling through my resume, you can simply ask:

* “What cloud tools has Chinni worked with?”
* “Tell me about his data engineering projects.”

And MICROBOT will respond instantly with accurate, grounded answers.

## Architecture 
<img width="1280" height="1600" alt="image" src="https://github.com/user-attachments/assets/f1a6568d-1e8f-4c44-956f-0addea88a772" />
Image Credits: KODEKLOUD

## The Pipeline Behind MICROBOT

Let’s break down the **end-to-end RAG pipeline** I used 

### 1️⃣ Data Ingestion & Parsing

The process starts with **data ingestion**. I fed my **resume PDF** and personal documents into the system.

Using **LangChain’s loader**, I performed **data parsing** to extract meaningful text.

### 2️⃣ Chunking the Data

Large documents aren’t efficient to search directly.
So the parsed data was split into **chunks** (small pieces of text).

Why chunking matters:

* Each chunk is easier to retrieve later
* It keeps responses accurate and focused
* Prevents the model from being overloaded with irrelevant context

### 3️⃣ Embeddings: Turning Text into Vectors

I used the **All-MiniLM-L6-v2 model** to convert chunks into **embeddings** — numerical representations of text.

This step makes the text **searchable in vector space**.
So when a user query comes in, the system can quickly find **similar embeddings** (aka the most relevant chunks).

### 4️⃣ Vector Store & Retriever

I stored these embeddings in **ChromaDB** — an open-source **vector store** optimized for similarity search.

* **Retriever**: Acts as the “search engine” of the pipeline.
* It finds the top chunks that best match the user query.

Alternative: FAISS (another popular open-source vector store).

### 5️⃣ Query + Context + Prompt → LLM

Here’s where the magic happens:

1. The **user query** is embedded
2. The **retriever** pulls the top-matching chunks from the vector store
3. These chunks are added as **context** to the **prompt**
4. The **LLM API** generates a response based on both query + retrieved data

This step ensures the **text generation** is grounded in reality, reducing hallucination and optimizing the quality of answers.

## Optimization & Open-Source Options

Everything in this setup is **open-source** except the **LLM API**.

* For embeddings: **All-MiniLM-L6-v2** (open-source, lightweight)
* For vector store: **ChromaDB** (fast, reliable)
* For pipeline orchestration: **LangChain** (flexible, modular)
* For text generation: I used an external API, but you can also try **Ollama** with LLaMA or Mistral models if you have enough compute power.

This makes the solution **cost-effective** and highly customizable.

## Why RAG Matters

RAG isn’t just about building personal bots like MICROBOT. It has **wide applications**:

* **Customer Support**: Answer FAQs with verified company data
* **Healthcare**: Retrieve patient history for quick medical insights
* **Education**: Create AI-powered study assistants
* **Enterprise**: Connect LLMs with proprietary data securely

The main advantage? **Optimization of responses by grounding them in trusted data, reducing hallucinations, and improving reliability.**

## Final Thoughts

RAG is the **bridge between static knowledge in LLMs and dynamic, real-world information**.
By combining **retrieval, chunking, embeddings, vector stores, and optimized text generation**, we can build AI systems that are not only smart but also **trustworthy**.

For me, building **MICROBOT** was more than just a fun project — it’s a way to **showcase my skills in action**.

If you’re curious about me or want to build your own RAG-powered assistant, feel free to **ping MICROBOT**.

The future of AI isn’t just about models — it’s about **data ingestion, retrieval, and grounding.**
And RAG is leading the way.

🔥 This version now includes **all the keywords naturally** (data ingestion, pipeline, parsing, chunking, embeddings, retriever, vector store, hallucination reduction, query, context, prompt, optimization, text generation).

Do you also want me to **add a simple diagram/flowchart** of the RAG pipeline (User Query → Retriever → Vector Store → Context → LLM → Response) so it’s visually appealing on Medium?
