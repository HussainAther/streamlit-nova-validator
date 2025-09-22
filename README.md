# Radiology Report Validator (Amazon Nova + Streamlit)

This repository contains a lightweight **Streamlit app** that validates radiology free-text reports against structured fields.  
It can use **Amazon Nova (Bedrock)** for structured extraction or a simple **local regex fallback** for offline testing.

---

## 🎯 Why this matters

This project is part of my broader journey with **Ray-by-Ray Computed Tomography (RBYRCT)** at **Janus Sphere Innovations**.  
RBYRCT aims to revolutionize breast cancer detection through steerable X-rays and advanced reconstruction algorithms.  

While RBYRCT focuses on **hardware & algorithms**, this project complements it by focusing on **report validation**:

- Ensures **clinical reports are consistent** with structured fields (important for trials and FDA submissions).  
- Bridges **medical imaging + AI/cloud infrastructure**.  
- Demonstrates **AWS-certified expertise** (8x AWS certifications).  
- Provides a **usable demo tool** for radiologists, researchers, and data engineers.  

Together, these projects highlight a **full-stack vision**: better imaging technology and better data integrity.

---

## ✨ Features

- Upload a CSV with these columns:
  - `patient_id`
  - `report_text`
  - `structured_laterality`
  - `structured_quadrant`
  - `structured_finding`
  - `structured_microcalcifications`
  - `structured_size_mm`
- Backend options:
  - **AWS Nova (Bedrock)** → LLM-based extraction
  - **Local regex fallback** → offline demo mode
- Configurable **size tolerance (mm)**
- Color-coded validation results
- Downloadable CSV of mismatches

---

## 🚀 Quickstart

```bash
# Clone repo
git clone https://github.com/<your-username>/streamlit-nova-validator.git
cd streamlit-nova-validator

# Create environment
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# (Optional) Configure AWS Nova
export BEDROCK_REGION=us-east-1
export BEDROCK_MODEL_ID=amazon.nova-pro-v1:0
# Ensure your AWS creds allow Bedrock InvokeModel

# Run app
streamlit run app.py
````

Open [http://localhost:8501](http://localhost:8501) to interact.

---

## 🗂 Example CSV

See [`sample_data/sample_reports.csv`](sample_data/sample_reports.csv):

```csv
patient_id,report_text,structured_laterality,structured_quadrant,structured_finding,structured_microcalcifications,structured_size_mm
P001,"Digital breast tomosynthesis of the left breast demonstrates a 3 mm spiculated mass in the upper outer quadrant with associated microcalcifications.","left","upper outer","mass",True,3.0
P002,"Right breast shows no suspicious mass or suspicious microcalcifications.","right","upper inner","no suspicious finding",False,
```

---

## ☁️ Deployment

* **Local demo:** `streamlit run app.py`
* **Docker + ECS/App Runner:** containerize for cloud hosting
* **Lambda + Step Functions:** extend for batch validation pipelines
* **QuickSight dashboard:** visualize mismatch trends at scale

---

## 🔒 Security

* Run inside **private VPC endpoints** for PHI handling.
* Redact logs in production.
* Use `temperature=0.0` for deterministic Nova outputs.

---

## 📜 License

MIT

```

---

# 📂 Repo Structure

streamlit-nova-validator/
├── app.py                     # Streamlit web app
├── extractor\_bedrock.py       # AWS Nova (Bedrock) client
├── extractor\_regex.py         # Local regex fallback
├── validator.py                # Validation logic
├── requirements.txt            # Dependencies
├── README.md                   # Documentation
├── .gitignore                  # Ignore venv, cache, logs, etc.
└── sample\_data/
└── sample\_reports.csv      # Example CSV for testing

```
