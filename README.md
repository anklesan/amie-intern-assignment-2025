# 🌦️ AI Intern Assessment — “Weather Advisor Agent”  
### *Two-Agent System with Live Weather Data and Open-Source LLM Reasoning*

---

## 🎯 Project Overview

Build a lightweight agentic application that answers everyday weather-related **decision questions** using **live open weather data** and **a reasoning LLM agent**.

You will create two collaborating agents:

1. **Agent 1: Weather Retriever** – fetches forecast data from a free, public weather API  
2. **Agent 2: Reasoning Agent** – uses an open-source LLM to interpret the weather and answer user questions

---

## 🧾 Example Scenarios

- “Should I go hiking tomorrow in Bend?”
- “Will it be good weather for biking in Corvallis today?”
- “Should I plan an outdoor event this weekend in Eugene?”

---

## 🔁 System Architecture

```text
[User Query]
      ↓
🌐 Agent 1: Weather API Retriever
      ↓
[Hourly or Daily Weather Data]
      ↓
🧠 Agent 2: LLM Reasoning Agent
      ↓
[Helpful Natural Language Answer]
```

---

## ⚙️ Technical Requirements

### 🕷️ Agent 1: Weather Data Retrieval

- Use a **completely free**, open, no-auth weather API:
  - ✅ [Open-Meteo](https://open-meteo.com/en)
  - ✅ [wttr.in](https://github.com/chubin/wttr.in)

### 🧠 Agent 2: LLM-Based Reasoning

This agent uses an **open-source LLM from Hugging Face** to perform reasoning tasks.

| Example Model              | Description                                  | Usage Method                  |
|----------------------------|----------------------------------------------|-------------------------------|
| `google/flan-t5-small`     | Lightweight, instruction-tuned model         | Hugging Face `pipeline`       |
| `facebook/bart-large-cnn`  | Good for summarization, limited reasoning    | Hugging Face `pipeline`       |
| `tiiuae/falcon-rw-1b`      | Basic chat-style model with limited depth    | Hugging Face `transformers`   |

📦 These models can all run inside **Google Colab**:
- ✅ No login required  
- ✅ No payment necessary  
- ✅ Minimal setup

> ⚠️ **Important:**  
> You are *not* limited to the models listed above.  
> You may use **any open-source model** from Hugging Face that performs better at reasoning — for example:
> - `mistralai/Mistral-7B`
> - `microsoft/phi-2`
> - `meta-llama/Llama-2-7b-chat-hf` (requires Meta license agreement)
> - Or any other open-source model you can run locally or in Colab.

✅ Just make sure your code is **reproducible** and **well-documented**.


---

## 🛠️ Suggested Stack

| Component       | Tool/Library                        |
|------------------|-------------------------------------|
| Weather Data     | Open-Meteo or wttr.in               |
| LLM Agent        | Hugging Face Transformers           |
| Notebook/UI      | Google Colab (preferred), Streamlit |
| Language         | Python 3.x                          |

---

## 📄 Sample Code Snippets

### Agent 1 — Weather Retriever (Open-Meteo)

```python
import requests

def get_weather(lat, lon):
    url = f"https://api.open-meteo.com/v1/forecast?latitude={lat}&longitude={lon}&daily=temperature_2m_max,precipitation_sum,wind_speed_10m_max&timezone=auto"
    return requests.get(url).json()
```

### Agent 2 — Reasoning with LLM

```python
from transformers import pipeline

llm = pipeline("text2text-generation", model="google/flan-t5-small")

def reason_about_weather(data, question):
    weather_summary = f"The max temperature is {data['daily']['temperature_2m_max'][0]}°C with {data['daily']['precipitation_sum'][0]}mm rain."
    prompt = f"{weather_summary}\n\nUser question: {question}\nAnswer:"
    return llm(prompt, max_length=100)[0]['generated_text']
```

---

## ✅ Deliverables

Submit **one** of the following:

### 📁 GitHub Repo
- Code file(s) or Jupyter/Colab notebook
- `README.md` with:
  - What the project does
  - How to run it
  - Example questions + outputs

### 🔗 Google Colab Notebook
- Link to a **viewable** notebook
- Must contain:
  - Code for both agents
  - Sample runs
  - Comments and explanations

---

## 🏆 Bonus Options (Optional)

| Feature                       | Example or Tool                         |
|-------------------------------|------------------------------------------|
| 🧭 City to Coordinates Lookup | Use [Nominatim](https://nominatim.org/) or hardcoded lat/lon |
| 🗓️ Multi-day Forecast        | Let user choose number of days          |
| 🧠 Tone Modes                | “Professional”, “Friendly”, “Funny”     |
| 🌐 Streamlit UI              | Deploy as a tiny web app                |
---

## 🧠 Evaluation Criteria

| Category           | What We’re Looking For                                               |
|--------------------|----------------------------------------------------------------------|
| 📦 Functionality    | Does the system work end-to-end with live data and LLMs?             |
| 🧠 Reasoning        | Is the final answer helpful, correct, and well-written?              |
| 🛠️ Engineering     | Clean, modular code with comments                                     |
| 💬 Prompt Design   | Prompt tells the model what to do in context                          |
| 🧪 Creativity       | (Optional) Extra polish, UI, or interaction                          |

---
Feel free to use any equivalent tools, platforms, or libraries — as long as they are open-source, freely accessible, and require no payment or paid API keys.

Links

Weather Data APIs

Open-Meteo (no API key): https://open-meteo.com/en

wttr.in – Terminal-style weather API: https://github.com/chubin/wttr.in

Nominatim – OpenStreetMap Geocoding: https://nominatim.org/

Open-Source LLMs (Hugging Face)

google/flan-t5-small: https://huggingface.co/google/flan-t5-small

facebook/bart-large-cnn: https://huggingface.co/facebook/bart-large-cnn

tiiuae/falcon-rw-1b: https://huggingface.co/tiiuae/falcon-rw-1b

LLM Libraries & Tools

Hugging Face Transformers Docs: https://huggingface.co/docs/transformers/index

Transformers Pipelines: https://huggingface.co/docs/transformers/main_classes/pipelines

Development Platforms

Google Colab: https://colab.research.google.com/

Streamlit: https://streamlit.io/

Gradio: https://gradio.app/

Supporting Python Libraries

Requests (HTTP client): https://docs.python-requests.org/en/latest/

Pandas (dataframes): https://pandas.pydata.org/


🧡 Have fun combining live data with LLM reasoning!


