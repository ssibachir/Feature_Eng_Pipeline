# End-to-End MLOps Pipeline: AWS & Hopsworks

This project implements a robust MLOps pipeline leveraging **AWS SageMaker** for scalable compute and **Hopsworks** as a centralized Feature Store. This architecture unifies feature engineering to ensure data consistency, enabling a seamless transition from historical training to low-latency real-time inference.

---

## 🏗 Architecture

The following diagram illustrates the data flow from ingestion to inference:

![Architecture Diagram](./FeatureEng_diagram.png)

### Workflow Overview

1. **Data Ingestion (AWS):**  
   Raw data from S3, RDS, or Kinesis is processed using **AWS Glue/EMR**.

2. **Feature Store (Hopsworks):**  
   Cleaned features are ingested into Hopsworks.
   - **Offline Store:** Used for generating training datasets.
   - **Online Store (RonDB):** Used for low-latency feature retrieval during serving.

3. **Model Training (SageMaker):**  
   Models are trained on AWS SageMaker using data snapshots from the Offline Store.

4. **Inference:**  
   The deployed SageMaker Endpoint fetches real-time feature vectors from the Online Store to generate predictions.

---

## 🛠 Tech Stack

- **Language:** Python 3.9+
- **Feature Store:** Hopsworks
- **Cloud Infrastructure:** AWS (S3, Glue, SageMaker)
- **Orchestration:** Apache Airflow / AWS MWAA
- **ML Frameworks:** Scikit-Learn / TensorFlow / PyTorch

---

## 🚀 Getting Started

### Prerequisites

- AWS CLI configured with appropriate permissions.
- Hopsworks API Key.
- Python environment (see `requirements.txt`).

### Installation

```bash
pip install -r requirements.txt
```

---

## 📂 Project Structure

```
.
├── notebooks/              # Jupyter notebooks for exploration
├── scripts/                # ETL and Training scripts
├── FeatureEng_diagram.png  # Architecture visualization
├── README.md
└── requirements.txt
```

---

## 🖼️ Note on the Architecture Diagram

The following line in the Markdown ensures the image is displayed:

```markdown
![Architecture Diagram](./FeatureEng_diagram.png)
```

The `./` indicates that the image is in the **same folder** as the README. If the image does not display immediately in your code editor (e.g., VS Code, PyCharm), it will render correctly on GitHub, GitLab, or in "Preview" mode.

---

Feel free to customize this template further to fit your project's specifics!
