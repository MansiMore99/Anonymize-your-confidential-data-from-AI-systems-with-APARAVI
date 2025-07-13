# 🔐 APARAVI: Anonymize Your Confidential Data for AI Pipelines

[![License](https://img.shields.io/badge/license-MIT-blue.svg)]()
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)]()

## 🚀 Overview

**APARAVI** is a cool, privacy-first pipeline that **classifies** text and **anonymizes** sensitive info (PII) *before* converting content into vectors for AI systems. Stay compliant, build trust, and never miss a beat.

![Uploading Screenshot 2025-07-13 at 3.08.23 AM.png…]()

---

## ✨ Features

- **🔍 Classification**: Categorizes text for smarter downstream processing.  
- **🛡 PII Masking**: Automatically replaces names, numbers, emails with placeholders.  
- **📄 Chunking & Embedding**: Splits text and encodes it into vector embeddings.  
- **📊 Vector Store Support**: Out-of-the-box Qdrant support for semantic search.  
- **🤖 Modular Pipeline**: Plug in custom models and data sources (e.g. S3, Google Drive).

---

## 🏗 Architecture

```
flowchart LR
    A[Data Source Node]
    B[Parser Node]
    C[Text Classification]
    D[Text Anonymizer]
    E[Preprocessor → Chunking]
    F[Embedding (Transformer)]
    G[Qdrant Vector Store]
    A --> B --> C --> D --> E --> F --> G
```

## 🎥 **Usage Demo**
Here’s a quick example:

```text
Before: "Contact Sarah at sarah@example.com or 415‑555‑1234."
After:  "Contact █████ at █████████████ or ████████████."
```

<img width="3279" height="860" alt="Classify and Anonymize" src="https://github.com/user-attachments/assets/0631fab3-55ee-499e-ad4c-3e00b218ba65" />

This is a Classification and Anonymization pipeline that processes text for privacy and categorization before embedding.

#### How the APARAVI Pipeline Works (And Why It’s Awesome) ✨

**1. Data Source Node**
This node pulls your source files (e.g., Google Drive, S3, local docs).

**2. Data Parser Node**
In this node, we extract the content from the files. In this scenario, we are extracting text.

**How it works**

* Receives “Data” from the Sample Data node.
* Splits into multiple channels: Text, Table, Image, Audio, Video.

**3. Text Classification Node**
Analyzes and categorizes text into predefined classes or categories.

**4. Text Anonymizer Node**
The Text Anonymizer node identifies and masks personally identifiable information (PII) in text to ensure privacy and compliance.

How it works

* Scans text for PII, including names, emails, phone numbers, addresses, and other sensitive information.
* Replaces identified PII with generic tokens or masks.
* Preserves the semantic structure of the text while removing sensitive data.
  
**5. Preprocessor — General Text**
This node splits large text blocks into smaller "documents" ready for embedding. Here, we’ll take the large text segments and split them up into documents that can be embedded.

**How it works**

* Takes parser output, applies sanitization, chunking, and metadata tagging.
* Emits a stream of document objects.
  
**6. Embedding — Transformer**

The Embedding - Sentence Transformer node is responsible for converting text (such as document segments or user questions) into vector embeddings, which are essential for semantic search and retrieval in a RAG pipeline.

How it works
* Document transformer: turns each text chunk into a vector.
  
Available Options:

* Custom model: Use your own pre-trained or fine-tuned model.
* miniAll: A general-purpose model, suitable for a variety of tasks.
* miniLM: Optimized for general use, offering a good balance between performance and speed.
* mpnet: Another high-quality model, often providing strong results on semantic similarity tasks.
  
**7. Vector Store (Qdrant) Node**

The Qdrant Vector Store node is critical in a RAG pipeline. It is responsible for storing and retrieving vector embeddings, enabling efficient semantic search and context retrieval for downstream language models.

How it works

* Ingests document embeddings + metadata.
* On query, it computes the similarity between the question vector and stored vectors.
* Returns top-K relevant document segments.

--- 

Hit the Play Button ▶️

---
