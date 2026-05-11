---
title: "Candidate Matcher"
summary: "Semantic resume ranking using MiniLM embeddings and cosine similarity, with LLM-generated match summaries."
tags:
  - Python
  - MiniLM
  - Sentence Transformers
  - NLP
  - Streamlit
date: "2024-01-01"

links:
  - type: code
    url: https://github.com/jaypolra/candidate-matcher
---

Keyword overlap misses semantic alignment. A resume can match a job description on surface terms and still be irrelevant.

Built ATS-style ranking using MiniLM embeddings and cosine similarity. LLM-generated summaries explain the match rather than just scoring it. Robust multi-format parsing pipeline for PDF, DOCX, and TXT files with fallback extraction logic. Deployed on Streamlit Cloud with Gemma 2B for summarization and Flan-T5 as a CPU-compatible fallback.
