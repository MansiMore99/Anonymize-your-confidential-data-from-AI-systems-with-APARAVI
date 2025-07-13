# 🔐 APARAVI: Anonymize Your Confidential Data for AI Pipelines

[![License](https://img.shields.io/badge/license-MIT-blue.svg)]()
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)]()

## 🚀 Overview

**APARAVI** is a cool, privacy-first pipeline that **classifies** text and **anonymizes** sensitive info (PII) *before* converting content into vectors for AI systems. Stay compliant, build trust, and never miss a beat.

---

## ✨ Features

- **🔍 Classification**: Categorizes text for smarter downstream processing.  
- **🛡 PII Masking**: Automatically replaces names, numbers, emails with placeholders.  
- **📄 Chunking & Embedding**: Splits text and encodes it into vector embeddings.  
- **📊 Vector Store Support**: Out-of-the-box Qdrant support for semantic search.  
- **🤖 Modular Pipeline**: Plug in custom models and data sources (e.g. S3, Google Drive).

---

## 🏗 Architecture

```mermaid
flowchart LR
    A[Data Source Node]
    B[Parser Node]
    C[Text Classification]
    D[Text Anonymizer]
    E[Preprocessor → Chunking]
    F[Embedding (Transformer)]
    G[Qdrant Vector Store]
    A --> B --> C --> D --> E --> F --> G

## 🎥 **Usage Demo**
Here’s a quick example:

```text
Before: "Contact Sarah at sarah@example.com or 415‑555‑1234."
After:  "Contact █████ at █████████████ or ████████████."

