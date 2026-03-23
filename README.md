# Banking AI Knowledge Graph System

## Overview

This project implements an end-to-end AI system for banking customer support by combining:

* **Intent classification (NLP)**
* **Ontology engineering (Protégé)**
* **Knowledge graph reasoning (Neo4j)**
* **Retrieval-Augmented Generation (RAG) with LLMs**
* **Multi-agent architecture**

The system simulates how modern financial institutions structure AI-driven customer service pipelines.

## System Architecture

User Query
    ↓
Intent Classification (ML)
    ↓
Ontology Mapping
    ↓
Knowledge Graph (Neo4j)
    ↓
Graph Retrieval
    ↓
LLM (RAG)
    ↓
Response Generation

## Key Components

### 1. Intent Classification

* Model: TF-IDF + Logistic Regression
* Dataset: Banking77 (77 intent categories)
* Output: Structured intent labels (e.g., `lost_card`, `activate_card`)

### 2. Ontology (Protégé / WebProtégé)

Defines the semantic structure of the system:

* Classes: `Intent`, `ServiceFlow`, `Product`, `Verification`
* Relationships:

  * `Intent → triggers → ServiceFlow`
  * `Intent → relatesTo → Product`
  * `ServiceFlow → requiresVerification → Verification`

Example:

LostCardIntent → CardReplacementProcess → IdentityVerification

### 3. Knowledge Graph (Neo4j Aura)

Implements ontology as a graph database:

* Nodes: Intent, ServiceFlow, Product, Verification
* Relationships: TRIGGERS, RELATES_TO, REQUIRES

Supports reasoning via Cypher queries.

### 4. NLP → Graph Pipeline

Maps user queries to graph reasoning:

"My card was stolen"
    ↓
lost_or_stolen_card (ML)
    ↓
LostCard (mapped)
    ↓
Graph query
    ↓
CardReplacement + IdentityVerification

### 5. RAG (Retrieval-Augmented Generation)

* Uses Groq (LLaMA-based models)
* Combines graph output with LLM generation
* Produces natural, context-aware responses

### 6. Multi-Agent System

Modular AI agents:

* **Intent Agent** → detects user intent
* **Graph Agent** → retrieves knowledge
* **Response Agent** → generates answer

### 7. Data Governance

Validation rules implemented using Cypher:

* Every `Intent` must trigger a `ServiceFlow`
* Every `ServiceFlow` must require `Verification`

## Example

**Input:**

My credit card was stolen

**Output:**

We will initiate a card replacement process. Please complete identity verification to proceed.

## Dataset

This project uses the **Banking77 dataset** for intent classification.

* Source: https://github.com/PolyAI-LDN/task-specific-datasets
* Description: 13,000+ customer queries across 77 banking intent categories
* Authors: Casanueva et al. (2020)

## Project Structure

banking-ai-knowledge-system/
│
├── dataset/
├── taxonomy/
├── ontology/
├── graph/
├── nlp_model/
├── notebooks/
├── src/
├── requirements.txt
└── README.md

## Technologies Used

* Python
* scikit-learn
* NLTK
* Neo4j Aura
* Protégé / WebProtégé
* Groq API (LLaMA models)

## Setup Instructions

To run this project:

1. **Create a Neo4j Aura database**
2. **Obtain a Groq API key**

Then update the following in the code:

* Neo4j URI, username, password
* `GROQ_API_KEY`

## Notes

* This project uses publicly available datasets
* No sensitive or personal user data is included
* Model files (`.pkl`) may be excluded; retrain using provided notebooks if needed

## Author

Adrij Ghosh
Srimoyee Bhowmick
