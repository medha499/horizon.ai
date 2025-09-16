## Horizon.AI – Voice of Customer (VoC) Analytics Platform

> _Note:_ Example datasets are synthetic; the system supports both anonymized and production pipelines with standard governance controls. Also, all API keys have been redacted for privacy reasons.
## Summary ## 
Delivering exceptional customer experiences requires more than just collecting feedback: it demands actionable insights and seamless execution. Traditional feedback management tools provide valuable data but often do not drive timely and effective solutions, leading to higher churn rates and lower retention. Companies with high churn rates struggle to grow, as they must replace lost customers just to break even [1]. In short, churn and retention are critical metrics for any subscription or recurring revenue business because they directly affect revenue, customer lifetime value, and overall profitability.
Horizon.AI, powered by advanced AI and Large Language Models (LLMs), is a game changer. By automating feedback analysis and integrating insights across teams, this tool enables organizations to identify root causes, assign tasks with clarity, and act with speed and precision.
This innovation not only solves customer pain points efficiently, but also creates a proactive feedback loop that fosters trust and loyalty. With Horizon.AI, organizations can transition from passive feedback collection to a dynamic, action-driven approach, enhancing customer satisfaction, strengthening brand loyalty, and unlocking new growth opportunities.
AI-driven solutions have already shown significant impact: 69% of businesses report better consumer service, 55% experience reduced waiting times, and 54% achieve streamlined workflows after adopting AI technologies [2].
This white paper explores the limitations of current customer feedback systems and demonstrates how Horizon.AI transforms these challenges into opportunities for delivering superior customer satisfaction and business growth, boosting retention, and ultimately increasing customer lifetime value.


---

## Proposed Solution (MVP)
1) **Multi-Cloud Ingestion Layer**  
   Ingest feedback from web/app, support, surveys, social, and product logs across **AWS/Azure/GCP** (plus on-prem). Standardize into a unified data lake; **Kafka** planned for real-time streaming.

2) **LLM-Powered Task Assignment**  
   Fine-tuned transformer (BERT variant) classifies feedback (bug, feature, policy, CX issue), then routes work to teams with priority/severity. Two-stage hierarchy: coarse category → specific subtype.

3) **Automated Clustering & Summarization**  
   **BERTopic + KMeans** group semantically similar items; clusters are summarized to key themes and sentiment trends. **GPT-4** proposes next-best actions; proprietary heuristics ensure concise, on-brand output.

4) **Cross-Channel Correlation**  
   Merge signals across sources (e.g., social negative spikes ↔ support tickets ↔ product telemetry) to surface true root causes and quantify impact.

5) **Actionable Insights & Reporting**  
   Interactive Streamlit dashboards show themes, trends, backlog, cost-to-impact scoring, owners, and SLA risk—so teams can decide and act quickly.

---


## Data Flow Diagram ## 
<img width="892" height="445" alt="Screenshot 2025-09-15 at 11 36 29 PM" src="https://github.com/user-attachments/assets/87050081-2623-4608-a3e5-4ca18459580c" />

---
## Results & Impact
- **Throughput:** Pipelines handle **250K+ multilingual feedback records/month** (streaming + batch).  
- **Classification quality:** Hybrid classifier (proprietary + OpenAI + LLaMA-2 with TF-IDF/KMeans + logistic regression) reaches **F1 = 0.87** across **18** themes; **+11 pts** minority-class F1 via active learning + vector search (**Sentence-Transformers + FAISS**).  
- **Retrieval speed:** Root-cause retrieval **< 200 ms**.  
- **Ops outcomes:** CX/Product triage **35% faster**; NPS interventions improved by **28%**.  
- **Cost/perf:** **41%** optimization via cascaded inference (small models first, LLM fallback), Parquet compaction, and Snowflake auto-suspend.

---

## Architecture Highlights
- **Pipelines:** Airflow • Kafka • Spark • Snowflake • MongoDB  
- **NLP/LLM:** Sentence-Transformers • FAISS • BERTopic • LLaMA-2 • OpenAI (RAG + action suggestions)  
- **App:** Streamlit insights UI (drilldowns, trends, cost-to-impact)  
- **Governance:** Task lineage, owner routing, SLA tracking, and audit logs

---

## Selected Engineering Notes
- Built scalable pipelines for **250K+/month** feedback; supports both streaming and batch.  
- Hybrid classifier with proprietary models + OpenAI + LLaMA-2; **F1 0.87** across **18** themes.  
- Active learning + vector search boosted minority-class F1 by **+11 pts**; **<200 ms** root-cause retrieval.  
- Streamlit app enabled teams to triage **35% faster** and lift NPS interventions by **28%**.  
- Cut compute/storage cost by **41%** with cascaded inference and warehouse optimizations.


## White Paper
For methodology and experiments, see the full write-up:  

[Horizon_AI__NLP_and_LLM_Powered_Feedback_Analytics_Tool.pdf](https://github.com/user-attachments/files/22352809/Horizon_AI__NLP_and_LLM_Powered_Feedback_Analytics_Tool.pdf)

