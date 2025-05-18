# 🧠 Local RAG Stack with Ollama + AnythingLLM + ChromaDB

This project sets up a **local private Retrieval-Augmented Generation (RAG)** system using Docker Compose. It's designed to work on **Windows with WSL2 installed**, and provides a simple, secure, and fast way to:

- Serve **LLMs locally** using [Ollama](https://ollama.com). It can be changed on the docker-compose.yml based on the hardware where it is going to be deployed.
- Use **AnythingLLM** as a web-based interface to interact with the local LLM and for document ingestion to be able to query it using the LLM.
- System to store and search documents using **ChromaDB**.
- Run everything **100% locally and privately**—no API keys required (except for optional features).

---

## 🚀 Features

- 🧩 **Modular setup**: Ollama, AnythingLLM, and ChromaDB in isolated Docker containers.
- 🤖 **Changeable LLM model**: Swap out the model in `docker-compose.yml` (e.g., `llama3.1`, `mistral`, etc.).
- 🔐 **Private and local**: No cloud dependencies or telemetry.
- 📄 **Document upload and Q&A** through AnythingLLM's interface.

---

## ✅ Prerequisites

Make sure you have the following installed on **Windows with WSL2**:

- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- WSL2 with Ubuntu (or any Linux distro)
- GPU with CUDA support (for Ollama + NVIDIA GPU access)

---

## 🛠️ Setup

1. **Clone the repository**:

```bash
git clone https://github.com/ErickF13/selfhosted-rag-llm-compose
cd selfhosted-rag-llm-compose
```

2. **(Optional) Edit the LLM model** you want Ollama to use:

In `docker-compose.yml`, modify this section under `ollama`:

```yaml
ollama pull llama3.1 &&  # <-- change this to any supported Ollama model
```

Supported models: [`llama3`, `mistral`, `nomic-embed-text`, etc.](https://ollama.com/library)

3. **Build the containers**:

```bash
docker-compose build
```

4. **Run the containers**:

```bash
docker-compose up -d
```

> The first run will take longer as it pulls the models and builds containers.

5. **Access the UI**:

- Open your browser and go to: [http://localhost:3001](http://localhost:3001)
- You’ll find the AnythingLLM interface to upload documents and chat with your LLM.

---

## 🛑 Stopping the System

To stop and clean up the containers:

```bash
docker-compose down
```

If you want to stop only (without removing volumes):

```bash
docker-compose stop
```

---

## 📜 License

MIT – use freely, modify, and improve!

---

## 🤝 Acknowledgments

- [Ollama](https://ollama.com) for fast local LLM serving.
- [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) for the document UI.
- [ChromaDB](https://www.trychroma.com/) for local vector storage.
