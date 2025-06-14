# AI-Powered Log Threat Hunting Lab

### Author: Kyrian Onyeagusi
[LinkedIn](https://www.linkedin.com/in/kyrian-onyeagusi) | [Email](mailto:kyrianoc18@gmail.com) 


### Focus: Semantic Threat Detection in Logs using OpenAI Embeddings

---

## Tools & Skills Demonstrated

* Python (pandas, numpy, scikit-learn)
* OpenAI Embedding API (text-embedding-3-small)
* Cosine Similarity & Vector Matching
* AI-Augmented Threat Detection
* Data Engineering & Log Triage
* Cloud API Integration (LLMs)
* Real-World Security Operations Skills

---

## Lab Overview

This project simulates a real-world SOC use case where AI augments human-led threat hunting. Traditional keyword detection methods often miss obfuscated or semantically reworded attacks — but large language models don’t.

I built a fully functional AI threat hunting pipeline that:

* Embeds raw log messages using OpenAI’s Embedding API
* Scores each message against known attack patterns
* Flags and visualizes the most suspicious entries

This lab stands out because it integrates advanced NLP (semantic similarity via embeddings) directly into log analysis, showing an understanding of both AI capabilities and practical security triage.

---

## Project Stages

### Step 1: Load & Inspect Logs

Structured logs were loaded from a CSV, with fields like timestamp, user, IPs, and messages:

```csv
timestamp,username,source_ip,destination_ip,action,message
2024-06-01 12:03:22,jdoe,10.0.0.4,192.168.1.10,allowed,User login succeeded
2024-06-01 12:07:54,admin,10.0.0.8,192.168.1.12,denied,SSH brute force attempt detected
```

---

### Step 2: Generate Semantic Embeddings

Each message was embedded using OpenAI’s `text-embedding-3-small` model. This turns text into 1536-dimension vectors that capture meaning.

```python
response = openai.Embedding.create(
  input="SSH brute force attempt detected",
  model="text-embedding-3-small"
)
embedding = response['data'][0]['embedding']
```

---

### Step 3: Define Threat Pattern & Score Logs

I defined a reference threat message (e.g. `suspicious root login from unknown IP`) and computed cosine similarity between its embedding and all log vectors.

```python
similarities = cosine_similarity([threat_vector], embeddings)[0]
df['threat_score'] = similarities
```

---

### Step 4: Visualize & Export Results

Ranked and displayed the top 10 most suspicious logs. Optional visualizations include a histogram of threat scores.

```python
sns.histplot(df['threat_score'], bins=50)
plt.title("Distribution of Threat Similarity Scores")
```

Results exported to `logs/scored_logs.csv`.

---

## 📊 Folder Structure

```
ai-log-anomaly-lab/
├── logs/
│   └── sample_logs.csv
├── embeddings/
│   └── embedded_logs.npy
├── notebook/
│   └── threat_hunting_ai.ipynb
├── README.md
```

---

## Why This Project Stands Out

* Combines **AI and cybersecurity** in one real lab
* Shows **practical use of OpenAI APIs** for analyst workflows
* Demonstrates **semantic detection**, not just keyword matching
* Applies **data science techniques** to a real-world SOC task
* Shows initiative, innovation, and emerging skill sets

This project highlights my ability to engineer secure, scalable, AI-driven systems — a valuable skill in modern cybersecurity environments.

---

## 🔗 Contact

**Kyrian Onyeagusi**
[LinkedIn](https://www.linkedin.com/in/kyrian-onyeagusi/) | [Email](mailto:kyrianoc18@gmail.com) 
