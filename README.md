# Banking AI Knowledge Graph System

## Overview

This project builds an AI system for banking customer support using:

* Intent classification (NLP)
* Ontology (Protégé)
* Knowledge Graph (Neo4j)
* RAG (LLM-based responses)

## Workflow

User Query → Intent Model → Knowledge Graph → Response

## Key Components

### Ontology (Protégé)

Defines relationships between:

* Intents
* Services
* Verification steps

### Knowledge Graph (Neo4j)

Stores:

* Intent → Service mappings
* Service → Verification rules

### Example

Input:
"My card was stolen"

Output:
"We will initiate a card replacement. Please verify your identity."

## Tools Used

* Python
* scikit-learn
* Neo4j 
* Protégé 
* Groq API

## Author

Adrij Ghosh 
Srimoyee Bhowmick
