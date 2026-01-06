**FactCheck-Agent: Autonomous Verification System with LangGraph**

**Overview**
FactCheck-Agent adalah sebuah sistem AI otonom yang dirancang untuk memverifikasi klaim berita dan mendeteksi hoaks secara real-time. 
Sistem ini dibangun menggunakan arsitektur Graph-based (LangGraph) yang memungkinkan model untuk berpikir, memutuskan apakah perlu mencari data eksternal, 
melakukan validasi, dan memberikan kesimpulan terstruktur (VALID/HOAX/MISLEADING).

Proyek ini mendemonstrasikan implementasi Agentic AI modern dengan kemampuan tool-calling dan cyclic reasoning.

**Key Features**
- Cyclic Graph Architecture: Menggunakan StateGraph untuk membuat alur kerja non-linear (Loop: Reason → Tool Call → Search → Reason → Final Answer).
- High-Speed Inference: Terintegrasi dengan Groq API menggunakan model Llama-3.3-70b-versatile untuk latensi rendah.
- Fact-Checking Guardrails: Dilengkapi dengan System Prompt yang ketat untuk memastikan output objektif dan berbasis referensi terpercaya (Kompas, Detik, CNN, dll).

**Tech Stack & Engineering Concepts**
- Orchestrator: LangGraph (State Management, Cyclic Graphs, Conditional Edges)
- LLM Inference: ChatGroq (Cloud Inference, Model Binding)
- Tool: Tavily Search (Function Calling, External API Integration)
- Framework: LangChain (Prompt Engineering, Message History Handling)

**System Architecture**
Alur kerja agent didefinisikan dalam sebuah graf (StateGraph) sebagai berikut:
Start: User memberikan klaim/query.
Chatbot Node: LLM menganalisis input. Apakah ini klaim faktual?
  - Decision: Jika butuh fakta -> Panggil ToolNode.
  - Decision: Jika obrolan biasa -> Langsung ke End.
Tool Node: Mengeksekusi pencarian ke internet menggunakan Tavily API (memfilter domain terpercaya).
Loop Back: Hasil pencarian dikembalikan ke Chatbot Node untuk disintesis menjadi kesimpulan.

<img width="216" height="249" alt="image" src="https://github.com/user-attachments/assets/a46cf784-7cd0-40a5-9747-f27b42ec1059" />
