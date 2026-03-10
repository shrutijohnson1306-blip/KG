# 🛡️ RBI Digital Lending Compliance: GraphRAG Logic Engine

This project transforms the complex **RBI Guidelines on Digital Lending (2022-2024)** into a deterministic, queryable Knowledge Graph. By combining **LLM-based extraction** with **Graph-based reasoning**, this engine eliminates the "hallucination" risks of standard AI when dealing with strict financial regulations.

### 🛠️ The Tech Stack
* **LLM Engine**: `Qwen/Qwen2.5-7B-Instruct` (Quantized to **4-bit** via `BitsAndBytes` for GPU efficiency).
* **Graph Framework**: `NetworkX` (Internal logic storage and triple management).
* **Visualization**: `Pyvis` (Interactive D3.js based compliance mapping).
* **Data Format**: `GraphML` & `JSON` (For cross-platform integration).
* **Environment**: Kaggle GPU (T4/P100) / Python 3.12.

### 🧠 Key Innovations
* **GraphRAG Architecture**: Instead of basic vector search, we use a Knowledge Graph to map relationships between Regulated Entities (REs), LSPs, and Borrowers.
* **Logic Injection**: Manually bridged gaps in LLM reasoning to enforce mathematical boundaries (e.g., specific cooling-off periods for loans < 7 days vs >= 7 days).
* **Blanket Prohibition Rules**: Hard-coded logic ensuring that any fee not explicitly disclosed in the Key Fact Statement (KFS) is flagged as unrecoverable.

### 📁 Project Structure
- `/notebooks`: The core logic, PDF parsing, and model quantization code.
- `/data`: Exported `GraphML` and `JSON` files containing the "Logic Engine."
- `/visualization`: The standalone `digital_lending_graph.html` interactive map.
