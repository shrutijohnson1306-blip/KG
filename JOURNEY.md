# The Journey: Building a Compliance Brain

I didn't want to build just another "chat with your PDF" bot. I wanted to build something that actually *understood* the rules of the RBI. Here’s how I got there.

### 1. The Setup (Wrestling with the Model)
I started by loading **Qwen 2.5 7B**. The first challenge was memory. A 7B model is heavy, so I used **4-bit quantization** to squeeze it into the Kaggle GPU. It worked. Suddenly, I had a high-performance LLM running locally in my notebook.

### 2. From Text to Triples
Reading a PDF is easy; understanding it is hard. I didn't just want text chunks. I forced the model to extract **"Triples"** (Subject -> Relation -> Object). This turned the RBI circular from a boring document into a web of facts.

### 3. Building the Map
I used **NetworkX** to build the brain and **Pyvis** to see it. Watching the "clusters" form—all the rules about APR grouping together, all the rules about Data Privacy in another corner—was the "Aha!" moment.

### 4. The "Stress Test" (Where the AI failed)
This was the most important part. I asked the graph: *"What’s the cooling-off period for a 10-day loan?"*
The AI struggled. It saw the words "10 days" but didn't know the **7-day threshold** rule. 

### 5. Manual Logic Injection (The Fix)
I realized that for banking, "close enough" isn't good enough. I manually coded **Logic Bridges**. I drew the lines between "10-day loan" and "3-day cooling-off" myself. I taught the graph that if a fee isn't in the KFS, it's illegal. I moved from **RAG** (guessing) to **GraphRAG** (logic).

### 6. The Result
By the end, I had a Question Box that didn't just find keywords—it followed paths. I could ask about "Convenience Fees" (which weren't even in the original PDF text) and the graph knew to block them because they were "Undisclosed Charges."

**Status: Completed. Logic secured. Repo pushed.**
