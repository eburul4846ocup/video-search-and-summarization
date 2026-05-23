# Video Search and Summarization

A fork of [NVIDIA AI Blueprints: Video Search and Summarization](https://github.com/NVIDIA-AI-Blueprints/video-search-and-summarization) that enables intelligent video search and AI-powered summarization using NVIDIA's multimodal models.

## Overview

This blueprint demonstrates how to build a video search and summarization application leveraging:

- **NVIDIA NIM microservices** for vision-language models
- **Multimodal embeddings** for semantic video search
- **RAG (Retrieval-Augmented Generation)** pipeline for accurate summarization
- **Vector database** for efficient similarity search across video frames

## Features

- 🎥 Ingest and index video content (local files or streaming sources)
- 🔍 Natural language search across video libraries
- 📝 AI-generated summaries of video segments
- 🖼️ Frame-level visual understanding and captioning
- 🚀 GPU-accelerated processing with NVIDIA hardware

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend (React)                      │
└─────────────────────────┬───────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────┐
│                   API Gateway (FastAPI)                   │
└──────┬──────────────────┬──────────────────┬────────────┘
       │                  │                  │
┌──────▼──────┐  ┌────────▼───────┐  ┌──────▼──────────┐
│   Ingestion  │  │  Search Engine │  │  Summarization  │
│   Service   │  │   (FAISS/Milvus)│  │    Service      │
└──────┬──────┘  └────────────────┘  └─────────────────┘
       │
┌──────▼──────────────────────────────────────────────────┐
│              NVIDIA NIM Microservices                    │
│   (VILA, CLIP embeddings, LLM summarization)            │
└─────────────────────────────────────────────────────────┘
```

## Prerequisites

- Python 3.10+
- Docker & Docker Compose
- NVIDIA GPU (A100, H100, or RTX series recommended)
- NVIDIA AI Enterprise license or NGC API key
- CUDA 12.0+

## Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/your-org/video-search-and-summarization.git
cd video-search-and-summarization
```

### 2. Configure Environment

```bash
cp .env.example .env
# Edit .env with your NGC API key and configuration
```

### 3. Launch with Docker Compose

```bash
docker compose up -d
```

### 4. Access the Application

Open your browser and navigate to `http://localhost:3000`

## Configuration

See [docs/configuration.md](docs/configuration.md) for detailed configuration options.

## Development

```bash
# Install dependencies
pip install -r requirements.txt

# Run tests
pytest tests/

# Start development server
uvicorn src.main:app --reload
```

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) and review our [pull request template](.github/PULL_REQUEST_TEMPLATE.md) before submitting changes.

To report bugs or request features, use the appropriate [issue template](.github/ISSUE_TEMPLATE/).

## License

This project is licensed under the Apache 2.0 License — see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Original blueprint by [NVIDIA AI Blueprints](https://github.com/NVIDIA-AI-Blueprints)
- Built on [NVIDIA NIM](https://developer.nvidia.com/nim) microservices
