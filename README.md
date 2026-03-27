# RAG — Circular Economy & Fungi

A Retrieval-Augmented Generation (RAG) system for querying documents on circular economy and fungi-based chemical precursors for industrial applications (e.g., chitosan, organic acids).

**Stack:** Python · LangChain · ChromaDB · FastAPI

---

## Roadmap

### Phase 1 — Scaffolding ✅
- [x] Define project structure
- [x] Create `src/` modules: `config.py`, `ingest.py`, `retriever.py`, `chain.py`
- [x] Create `api/` app: `main.py`, `schemas.py`
- [x] Set up `data/` folders (`pdfs/`, `web/`, `texts/`)
- [x] Set up `tests/` and `nbooks/`
- [x] Configure `.gitignore`

### Phase 2 — Core Logic Implementation
- [ ] Implement `src/config.py` — centralise model names, chunk size, paths, and LLM provider switch
- [ ] Implement `src/_embeddings.py` — shared helper returning OpenAI or Ollama embeddings
- [ ] Implement `src/ingest.py` — load documents, chunk, embed, and persist to ChromaDB
- [ ] Implement `src/retriever.py` — similarity search wrapper over the persisted vectorstore
- [ ] Implement `src/chain.py` — LangChain RAG chain (retriever → prompt → LLM → output)

### Phase 3 — API Layer
- [ ] Implement `api/schemas.py` — Pydantic `QueryRequest` / `QueryResponse` models
- [ ] Implement `api/main.py` — FastAPI app with `/health` and `/query` endpoints
- [ ] Write `requirements.txt` and `.env.example`

### Phase 4 — Data Ingestion
- [ ] Collect PDF documents relevant to fungi and circular economy → `data/pdfs/`
- [ ] Scrape and cache key web pages → `data/web/`
- [ ] Add plain text / Markdown references → `data/texts/`
- [ ] Run `ingest.py` and verify ChromaDB is populated correctly

### Phase 5 — Exploration & Validation
- [ ] Interactively test queries in `nbooks/exploration.ipynb`
- [ ] Evaluate retrieval quality (relevance of returned chunks)
- [ ] Tune `CHUNK_SIZE`, `CHUNK_OVERLAP`, and `TOP_K` based on results

### Phase 6 — Testing
- [ ] Write `tests/test_ingest.py` — unit tests for chunking and ingest pipeline
- [ ] Write `tests/test_chain.py` — unit tests for document formatting and chain construction
- [ ] Achieve baseline test coverage for core logic

### Phase 7 — Hardening (future)
- [ ] LLM provider swap (OpenAI ↔ Ollama) verified end-to-end via `config.py`
- [ ] Add API authentication / rate limiting
- [ ] Dockerize the application
- [ ] Set up CI/CD pipeline
- [ ] Evaluate swap from local ChromaDB to managed vector DB (e.g. Pinecone)
