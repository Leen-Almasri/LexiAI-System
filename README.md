
# LexiAI System

<p align="center">
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Python-3.9+-blue?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/FastAPI-Backend-009688?style=for-the-badge&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/OpenAI-GPT--4o--mini-412991?style=for-the-badge&logo=openai&logoColor=white" />
  <img src="https://img.shields.io/badge/Frontend-HTML%2FCSS%2FJS-E34F26?style=for-the-badge&logo=html5&logoColor=white" />
  <img src="https://img.shields.io/badge/Platform-Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white" />
</p>

<p align="center">
  <i>An end-to-end AI pipeline that cleans, enriches, and serves an AI terminology glossary with an interactive web interface.</i>
</p>



---

## 📌 Project Overview

LexiAI is a complete AI pipeline that transforms a raw AI terminology dataset into a structured, enriched, and searchable glossary.

Each term is enhanced with:

* Simple definition (plain English)
* Real-world example
* Analogy for easier understanding

All enrichments are generated using **GPT-4o-mini** and served through both:

* REST API (FastAPI)
* Interactive web interface

---

## 🔁 Pipeline Architecture

```
Raw Dataset
   ↓
Phase 1: EDA (Analysis)
   ↓
Phase 2: Data Cleaning
   ↓
Phase 3: LLM Enrichment (GPT-4o-mini)
   ↓
Phase 4: FastAPI Backend
   ↓
Phase 5: Web Frontend
```

---

## 🔄 Pipeline Breakdown

| Phase | Component       | Output                    | Required to Run |
| ----- | --------------- | ------------------------- | --------------- |
| 1     | EDA             | Dataset quality report    | ❌ No            |
| 2     | Cleaning        | ai_glossary.json          | ❌ No            |
| 3     | LLM Enrichment  | ai_glossary_enhanced.json | ❌ No            |
| 4     | FastAPI Backend | REST API                  | ✅ Yes           |
| 5     | Frontend UI     | Interactive web app       | ✅ Yes           |

---

## 🧠 Key Techniques Used

### 1. Exploratory Data Analysis (EDA)

* Null value detection
* Duplicate analysis
* Definition length distribution
* Data quality profiling

### 2. Regex-Based Cleaning

* Removal of Arabic diacritics (Unicode range)
* Cleaning redundant phrases (e.g., "Also called")

### 3. Redirect Deduplication

* Removed alias/redirect entries
* Prevented duplicate LLM processing

### 4. Prompt Engineering (Structured Output)

GPT-4o-mini was constrained to return:

```json
{
  "simple_definition": "",
  "example": "",
  "analogy": ""
}
```

This ensures consistent and machine-readable output.

---

### 5. Batch Processing with Auto-Save

* Processes data in batches (100 terms)
* Saves progress after each batch
* Prevents API loss or interruption failure

---

### 6. REST API Design (FastAPI)

* Case-insensitive term search
* Clean HTTP error handling (404 for missing terms)

---

### 7. Lightweight Data Storage

* Uses JSON as primary storage
* Loaded once into memory for fast response time

---

### 8. Interactive Frontend Features

* Live search (instant filtering)
* Tabbed UI (Definition / Example / Analogy)
* Category filtering
* Sorting (A–Z, Z–A)
* Copy-to-clipboard support
* Quick-access tags
* Performance stats dashboard

---

## 🚀 How to Run

### Prerequisites

* Python 3.9+
* `ai_glossary_enhanced.json`
* Modern browser

---

### 1. Install Dependencies

```bash
pip install fastapi uvicorn
```

---

### 2. Start Backend

```bash
uvicorn fastapi_backend:app --host 0.0.0.0 --port 8000
```

---

### 3. Open Frontend

Simply open:

```
index.html
```

---

## 🌐 API Endpoints

### Health Check

```bash
GET /
```

Response:

```json
{ "message": "API is running" }
```

---

### Term Lookup

```bash
GET /term/{term_name}
```

Example:

```bash
GET /term/neural%20network
```

Response:

```json
{
  "term": "Neural Network",
  "original_definition": "...",
  "simple_definition": "...",
  "example": "...",
  "analogy": "..."
}
```

---

## 📁 Project Structure

```
LexiAI_System/
├── index.html                 # Frontend UI
├── fastapi_backend.py        # API server (Phase 4)
├── ai_glossary_project.py    # Phases 1–3 pipeline
├── ai_glossary.json          # Clean dataset
├── ai_glossary_enhanced.json # Enriched dataset
└── README.md
```

---

## 🛠️ Tech Stack

* Python 3.x
* Pandas
* Regex (re)
* OpenAI GPT-4o-mini
* FastAPI
* Uvicorn
* HTML / CSS / JavaScript
* Google Colab

---

## 👩‍💻 Team

* Leen Almasri
* Noura Alshaigi
* Rahaf Alshammari
* Rawan Alotaibi

---

<p align="center">
  Made with ❤️ · LexiAI System · All rights reserved
</p>


  Made with ❤️ &nbsp;·&nbsp; LexiAI System &nbsp;·&nbsp; All rights reserved
</p>
