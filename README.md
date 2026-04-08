# 📄 AI-Powered Document Q&A Tool (RAG Application)

## 🎯 What Does This Project Do?

Imagine you have hundreds of documents. Instead of reading all of them, you just ask a question and get an instant answer.

**Example:**
- You have documents about Google, Microsoft, Tesla
- You ask: "What is Google's mission?"
- The system automatically finds the answer from the documents

---

## 🧠 How Does It Work? (Simple Version)
Step 1: Upload Documents
Step 2: System breaks documents into small pieces
Step 3: System stores these pieces in a database
Step 4: You ask a question
Step 5: System finds relevant pieces
Step 6: AI reads those pieces and gives you an answer

---

## 📂 What Files Are in This Project?
Project Folder/
│
├── docs/                    (Your documents go here)
│   ├── Google.txt
│   ├── Microsoft.txt
│   ├── Tesla.txt
│   └── research-paper.pdf
│
├── db/                      (Database - stores document pieces)
│
├── Python Files             (Code that does the work)
└── Jupyter Notebooks        (Interactive experiments)

---

## 📝 Explanation of Each File (Simple Language)

### **File 1: `1_ingestion_pipeline.py`**

**What it does:**
- Reads your documents
- Breaks them into small chunks (like cutting a pizza into slices)
- Converts each chunk into numbers (embeddings)
- Saves everything in a database

**Why we need it:**
Computers can't understand text directly. We need to convert text into numbers first.

**How to run:**
```bash
python3 1_ingestion_pipeline.py
```

**What happens:**
Your document → Break into chunks → Convert to numbers → Save in database

---

### **File 2: `2_retrieval_pipeline.py`**

**What it does:**
- Takes your question
- Converts it into numbers
- Searches the database for matching chunks

**Why we need it:**
This is like using Google search, but only in your documents.

**How to run:**
```bash
python3 2_retrieval_pipeline.py
```

**What happens:**
Your question → Convert to numbers → Search database → Find top 5 matching chunks

---

### **File 3: `3_answer_generation.py`**

**What it does:**
- Takes your question
- Finds relevant chunks (using File 2)
- Sends chunks + question to AI
- AI reads and generates final answer

**Why we need it:**
This completes the full cycle - from question to answer.

**How to run:**
```bash
python3 3_answer_generation.py
```

**What happens:**
Question → Find chunks → Give chunks to AI → AI generates answer

**Example:**
You ask: "What is Tesla's main product?"
System finds chunks about Tesla
AI reads and says: "Tesla's main product is electric vehicles"

---

### **File 4: `4_history_aware_generation.py`**

**What it does:**
- Remembers previous conversation
- Understands follow-up questions
- Maintains chat history

**Why we need it:**
So you can have a conversation, not just ask one question.

**How to run:**
```bash
python3 4_history_aware_generation.py
```

**Example conversation:**
You: "What is Google's mission?"
AI: "Google's mission is to organize the world's information"
You: "When was it founded?"
AI: (remembers you're asking about Google) "Google was founded in 1998"

---

### **File 5: `5_recursive_character_text_splitter.py`**

**What it does:**
- Splits documents smartly
- First tries to split by paragraph
- If paragraph is too big, splits by sentence
- If sentence is too big, splits by word

**Why we need it:**
We need chunks that are not too big and not too small.

**How to run:**
```bash
python3 5_recursive_character_text_splitter.py
```

**Example:**
Big document → Try splitting by paragraph → Still too big? → Split by sentence

---

### **File 6: `6_semantic_chunking.py`**

**What it does:**
- Splits document by meaning/topic
- Keeps related sentences together

**Why we need it:**
Sometimes a paragraph talks about multiple topics. This splits by topic, not by size.

**How to run:**
```bash
python3 6_semantic_chunking.py
```

**Example:**
Paragraph about Tesla cars and batteries
↓
Chunk 1: About cars
Chunk 2: About batteries

---

### **File 7: `7_agentic_chunking.py`**

**What it does:**
- Uses AI to decide where to split
- AI understands context and splits intelligently

**Why we need it:**
This is the smartest way to split - AI decides the best places.

**How to run:**
```bash
python3 7_agentic_chunking.py
```

---

### **File 9: `9_retrieval_methods.py`**

**What it does:**
Shows different ways to search:
1. **Similarity Search** - Find most similar chunks
2. **Score Threshold** - Only show results above certain score
3. **MMR** - Find similar but diverse results

**Why we need it:**
Different questions need different search methods.

**How to run:**
```bash
python3 9_retrieval_methods.py
```

---

### **File 10: `10_multi_query_retrieval.py`**

**What it does:**
- Takes your one question
- Rephrases it into 3-5 different questions
- Searches with all questions
- Combines all results

**Why we need it:**
Sometimes one question is not enough. Multiple questions find more information.

**How to run:**
```bash
python3 10_multi_query_retrieval.py
```

**Example:**
Your question: "What does Google do?"
System creates:

"What is Google's business?"
"What products does Google make?"
"What services does Google provide?"

Searches with all 3, combines results

---

### **File 11: `11_reciprocal_rank_fusion.py`**

**What it does:**
- Combines results from multiple searches
- Ranks them properly
- Removes duplicates

**Why we need it:**
When you search with multiple questions (File 10), you need to merge results.

**How to run:**
```bash
python3 11_reciprocal_rank_fusion.py
```

---

### **File 12: `12_hybrid_search.ipynb`**

**What it does:**
- Combines two search types:
  1. Vector search (meaning-based)
  2. Keyword search (exact word match)

**Why we need it:**
Sometimes you want exact words, sometimes you want meaning.

**How to run:**
Open in Jupyter Notebook

---

### **File 13: `13_reranker.ipynb`**

**What it does:**
- Takes search results
- Uses AI to re-rank them
- Puts most relevant on top

**Why we need it:**
Sometimes search results are not in perfect order. This fixes it.

**How to run:**
Open in Jupyter Notebook

---

### **File 8: `8_multi_modal_rag.ipynb`**

**What it does:**
- Works with PDFs that have:
  - Text
  - Tables
  - Images

**Why we need it:**
Real documents have more than just text.

**How to run:**
Open in Jupyter Notebook

---

## 🔄 Complete Flow (Step by Step)

### **Step 1: First Time Setup**
Run File 1 → Reads documents → Stores in database

### **Step 2: Ask Questions**
Run File 3 → Ask question → Get answer

### **Step 3: Have Conversation**
Run File 4 → Ask multiple questions → System remembers context

---

## 📊 Simple Summary Table

| File Number | File Name | What It Does | When to Use |
|-------------|-----------|--------------|-------------|
| 1 | ingestion_pipeline | Loads and stores documents | First time setup |
| 2 | retrieval_pipeline | Searches documents | When you want to search only |
| 3 | answer_generation | Gets full answer | When you want complete answer |
| 4 | history_aware | Chat with memory | When you want conversation |
| 5 | recursive_splitter | Smart splitting | Learning about chunking |
| 6 | semantic_chunking | Topic-based splitting | Learning about chunking |
| 7 | agentic_chunking | AI-based splitting | Learning about chunking |
| 9 | retrieval_methods | Different search types | Learning about search |
| 10 | multi_query | Multiple question search | Better search results |
| 11 | rank_fusion | Merge results | Combine multiple searches |
| 12 | hybrid_search | Vector + keyword | Best search method |
| 13 | reranker | Improve ranking | Better result order |
| 8 | multi_modal | PDF with images/tables | Complex documents |

---

## ⚙️ How to Start (For Beginners)

### **Step 1: Install Python**
Make sure you have Python 3.8 or higher

### **Step 2: Download This Project**
```bash
git clone <project-link>
cd project-folder
```

### **Step 3: Install Required Libraries**
```bash
pip install -r requirements.txt
```

### **Step 4: Add Your API Key**
Create a file named `.env` and add:
HF_TOKEN=your_token_here

### **Step 5: Load Your Documents**
```bash
python3 1_ingestion_pipeline.py
```

### **Step 6: Ask Questions**
```bash
python3 3_answer_generation.py
```

---

## 🎓 Learning Path

**If you're new to this:**

1. Start with File 1 (Load documents)
2. Then File 3 (Ask questions, get answers)
3. Then File 4 (Have conversations)
4. Explore other files to learn advanced techniques

**If you want to learn chunking:**
- Files 5, 6, 7

**If you want to learn search:**
- Files 9, 10, 11, 12, 13

---

## 🤔 Common Questions

### **Q1: Which file should I run first?**
File 1 - It loads all documents into database

### **Q2: Which file gives me answers?**
File 3 or File 4 (File 4 is better for conversations)

### **Q3: Do I need to run all files?**
No. Files 5-13 are for learning. Main files are 1, 3, 4.

### **Q4: What are Jupyter notebooks (.ipynb)?**
These are interactive files. You open them in Jupyter and run step by step.

### **Q5: What documents can I use?**
Text files (.txt), PDFs (.pdf), Word files (.docx)

---

## 💡 Key Concepts (Simple Definitions)

### **RAG (Retrieval-Augmented Generation)**
Fancy name for: Search documents + Give to AI + Get answer

### **Embeddings**
Converting text into numbers so computers can understand

### **Chunks**
Small pieces of documents (like cutting a book into chapters)

### **Vector Database**
Storage for embeddings (numbered versions of text)

### **Retrieval**
Searching for relevant information

---

## 🎯 What You'll Learn

✅ How to build a document Q&A system  
✅ How AI searches through documents  
✅ How to split documents smartly  
✅ How to improve search results  
✅ How to build a chatbot with memory  

---

## 📌 Final Notes

- **Files 1, 3, 4** → Main files you'll use
- **Files 5-7** → Learn about splitting documents
- **Files 9-13** → Learn about better searching
- **Notebooks** → Experiments and learning

---

## 🚀 Quick Start (3 Commands)

```bash
# 1. Install
pip install -r requirements.txt

# 2. Load documents
python3 1_ingestion_pipeline.py

# 3. Ask questions
python3 3_answer_generation.py
```

---
