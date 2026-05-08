# VectorDB — Build a Vector Database from Scratch in C++

A fully working **Vector Database** built in C++ with a web UI.
Implements **HNSW**, **KD-Tree**, and **Brute Force** search algorithms, along with a **RAG pipeline** powered by Ollama.

> Educational project showing how vector databases like Pinecone, Weaviate, Chroma, and Milvus work internally.

---

# Features

| Feature                 | Description                                            |
| ----------------------- | ------------------------------------------------------ |
| **3 Search Algorithms** | HNSW, KD-Tree, Brute Force                             |
| **3 Distance Metrics**  | Cosine, Euclidean, Manhattan                           |
| **Semantic Search**     | Search similar vectors efficiently                     |
| **PCA Visualization**   | 2D scatter plot of vector clusters                     |
| **Real Embeddings**     | Generate 768D embeddings using Ollama                  |
| **RAG Pipeline**        | Retrieve document chunks and generate answers          |
| **REST API**            | Insert, delete, search, benchmark, and stats endpoints |

---

# Project Structure

```text
VectorDB/
├── main.cpp
├── httplib.h
├── index.html
└── README.md
```

---

# Requirements

Install these on Windows:

1. **MSYS2** (for g++)
2. **Git**
3. **Ollama**

---

# Setup Guide (Windows)

## Step 1 — Install MSYS2

Download from:

[MSYS2](https://www.msys2.org?utm_source=chatgpt.com)

Open **MSYS2 UCRT64** terminal and run:

```bash
pacman -Syu
```

Restart terminal if asked, then run:

```bash
pacman -S mingw-w64-ucrt-x86_64-gcc
```

Add this to Windows PATH:

```text
C:\msys64\ucrt64\bin
```

Verify installation:

```bash
g++ --version
```

---

## Step 2 — Install Git

Download from:

[Git for Windows](https://git-scm.com/download/win?utm_source=chatgpt.com)

Verify:

```bash
git --version
```

---

## Step 3 — Install Ollama

Download from:

[Ollama](https://ollama.com?utm_source=chatgpt.com)

Pull required models:

```powershell
ollama pull nomic-embed-text
```

```powershell
ollama pull llama3.2
```

Verify:

```powershell
ollama list
```

---

# Run the Project

Open **MSYS2 UCRT64** terminal.

## Step 1 — Open Project Folder

```bash
cd /c/Users/ASUS/Desktop/VectorDB-Data-Trainer
```

---

## Step 2 — Compile the Server

```bash
g++ -std=c++17 -O2 main.cpp -o db -lws2_32
```

This creates:

```text
db.exe
```

---

## Step 3 — Start the Server

```bash
./db
```

You should see:

```text
=== VectorDB Engine ===
http://localhost:8080
20 demo vectors | 16 dims | HNSW+KD-Tree+BruteForce
Ollama: ONLINE
```

---

# Open in Browser

```text
http://localhost:8080
```

---

# Application Tabs

## 1. Search

* Compare HNSW, KD-Tree, and Brute Force
* Use Cosine, Euclidean, or Manhattan distance
* Visualize vectors on PCA scatter plot

---

## 2. Documents

* Insert documents
* Generate embeddings using Ollama
* Store document chunks in HNSW index

---

## 3. Ask AI (RAG)

Pipeline:

```text
Question
   ↓
Embedding Generation
   ↓
HNSW Retrieval
   ↓
Context Selection
   ↓
LLM Answer Generation
```




# Algorithms Used

## HNSW

* Approximate nearest neighbor search
* Multilayer graph structure
* Fast high-dimensional search

## KD-Tree

* Space partitioning tree
* Efficient for low dimensions

## Brute Force

* Exact nearest neighbor search
* Baseline comparison

---

# Common Issues

| Problem                  | Fix                     |
| ------------------------ | ----------------------- |
| `g++: command not found` | Add MSYS2 to PATH       |
| `Ollama: OFFLINE`        | Run `ollama serve`      |
| Port 8080 busy           | Kill process using port |
| Slow LLM response        | Use `llama3.2:1b`       |

---

# Faster Model Option

```powershell
ollama pull llama3.2:1b
```

Change in `main.cpp`:

```cpp
std::string genModel = "llama3.2:1b";
```

Recompile and restart.

