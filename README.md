# 💬 General Health Query Chatbot — Prompt Engineering & LLM

> A conversational AI chatbot that answers general health questions using a Large Language Model, with engineered safety filters and emergency detection.

![Type](https://img.shields.io/badge/Type-Prompt%20Engineering-5b8fff?style=flat-square&labelColor=0b0d11)
![Model](https://img.shields.io/badge/Model-LLaMA%203.1%208B-a78bfa?style=flat-square&labelColor=0b0d11)
![API](https://img.shields.io/badge/API-Groq%20%2B%20HuggingFace-f0c060?style=flat-square&labelColor=0b0d11)
![Due Date](https://img.shields.io/badge/Due%20Date-3%20April%202026-4ade80?style=flat-square&labelColor=0b0d11)

> Part of the **DevelopersHub Corporation AI/ML Engineering Internship** — Project 04
> 👉 [View all other projects here](https://github.com/ArmanAdilMangat/developershub-aiml-internship)

---

## 📋 Project Overview

**Objective:** Build a chatbot that answers general health-related questions using a Large Language Model, with carefully engineered prompts and safety filters to ensure responsible responses.

**Tools Used:**
| Tool | Purpose |
|------|---------|
| Groq API — LLaMA 3.1 8B Instant | Primary LLM (fast, free tier) |
| Hugging Face Inference API — Mistral-7B | Fallback open-source LLM |
| `python-dotenv` | Secure API key management |

---

## 📁 Project Structure

```
developershub-health-chatbot/
├── main (1).py          # Primary version — Groq API / LLaMA 3.1
├── main.py              # Fallback version — HuggingFace / Mistral-7B
├── requirements.txt     # All dependencies
├── .env.example         # Template for API keys (safe to commit)
└── README.md            # This file
```

---

## 🧠 How It Works

### Two Implementations

**Version 1 — Groq API** (`main (1).py`)
- Uses LLaMA 3.1 8B Instant via Groq's free API
- Faster responses, cleaner output
- Recommended version to run

**Version 2 — HuggingFace** (`main.py`)
- Uses Mistral-7B via HuggingFace Serverless Inference
- Fully open-source, no paid API needed
- Uses `[INST]...[/INST]` instruction-tuned prompt format

---

## 🛡️ Safety Design

### Emergency Keyword Detector
Before every LLM call, the chatbot scans the query for emergency keywords. If detected, it **bypasses the LLM entirely** and returns an immediate emergency response — no delay, no API cost.

```python
EMERGENCY_KEYWORDS = [
    "chest pain", "heart attack", "stroke", "can't breathe",
    "severe bleeding", "unconscious", "overdose", "suicide",
    "poisoning", "dying", "not breathing", "emergency"
]
```

### System Prompt Safety Rules
```
You are a helpful, empathetic, and informative general medical assistant.

CRITICAL SAFETY RULES:
1. Never provide specific medical diagnoses or personalized treatment plans.
2. If asked about personal symptoms, clearly state you are an AI — not a doctor.
3. Always advise consulting a qualified healthcare professional.
4. For life-threatening emergencies, instruct the user to call emergency services immediately.
5. Always be warm, clear, and easy to understand.
6. Keep responses concise — 3 to 5 sentences unless more detail is truly needed.
```

---

## 💡 Example Queries

```
You: What causes a sore throat?
Chatbot: A sore throat is most commonly caused by viral infections such as
the common cold or flu. Bacterial infections like strep throat, allergies,
dry air, and acid reflux can also cause throat irritation. Most viral sore
throats resolve on their own within a week. If symptoms are severe or
persistent, it's best to consult a healthcare professional.

---

You: I'm having severe chest pain right now.
Chatbot: ⚠️ This sounds like a medical emergency!
Please call emergency services (911 or your local emergency number)
or go to the nearest emergency room IMMEDIATELY.
Do not wait — get help right now.
```

---

## ⚙️ Setup & Installation

**Step 1 — Install dependencies**
```bash
pip install -r requirements.txt
```

**Step 2 — Set up your API key**

Create a `.env` file in the project folder:
```
GROQ_API_KEY=your_groq_key_here
HF_TOKEN=your_huggingface_token_here
```

Get a free Groq API key at: [console.groq.com](https://console.groq.com)
Get a free HuggingFace token at: [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)

**Step 3 — Run the chatbot**
```bash
# Groq version (recommended)
python "main (1).py"

# HuggingFace version
python main.py
```

---

## 🧠 Skills Demonstrated

| Category | Skills |
|----------|--------|
| **Prompt Engineering** | System prompt design, safety rule embedding, tone control |
| **LLM Integration** | Groq API, HuggingFace Inference API, instruction-tuned prompts |
| **Safety Design** | Keyword-based emergency filter, response length control |
| **Python** | API calls, environment variables, interactive CLI loops |

---

## 👤 Author

**Arman Adil Mangat**
AI/ML Engineering Intern — DevelopersHub Corporation
