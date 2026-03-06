# Content-Aware Fileserver

A locally running, AI-powered file management system that automatically 
analyzes, categorizes, and organizes files based on their content.

## Concept

Instead of manually sorting files into folders, this system analyzes 
every document automatically using local LLM models:
- What type of document is it?
- Who sent it? What date? What amount?
- What is its current status?

Based on this analysis, the system makes autonomous decisions — for example, 
moving a paid invoice automatically from `/open/` to `/paid/`.

## Goals

This project serves two purposes:
1. A hands-on learning project to build modern AI engineering skills
2. A portfolio project to support a career transition into AI/Tech

## Tech Stack

- **LLM Runtime**: LM Studio (local)
- **Model**: Llama 3.3 8B Instruct (Q8_0)
- **Language**: Python 3.12
- **Package Manager**: uv

## Project Status

🚧 Work in progress — currently in Phase 0 (Foundation)

## Phases

| Phase | Topic | Status |
|---|---|---|
| 0 | Foundation & Environment | ✅ Complete |
| 1 | Document Analysis | 🔜 Next |
| 2 | Embeddings & Semantic Search | ⏳ Planned |
| 3 | Autonomous File Management | ⏳ Planned |
| 4 | State Tracking | ⏳ Planned |
| 5 | Productization & Portfolio | ⏳ Planned |