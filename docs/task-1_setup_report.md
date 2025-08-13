# Task 1 — GCP Foundation Setup Report
**Project:** Multilingual Education RAG  
**Date:** 2025-08-13 (IST)

---

## 1) Inputs (decisions & config)
- **Project ID:** `nervesparks-ai-assignment`
- **Primary Region:** `asia-south1` (Mumbai)
- **Bucket (GCS):** `nervesparks-ai-assignment-rag-data`
- **Service Account:** `rag-app-sa@nervesparks-ai-assignment.iam.gserviceaccount.com`
- **Artifact Registry repo:** `rag-repo` (Docker, region: `asia-south1`)
- **Secret (Secret Manager):** `APP_CONFIG`
- **BigQuery dataset:** `rag_eval` (region: `asia-south1`)

---

## 2) What we created (commands run conceptually)
- **APIs enabled:** Vertex AI, Cloud Run, Cloud Build, Artifact Registry, Cloud Storage, Secret Manager, Logging, Monitoring, Cloud Scheduler.
- **Service Account:** `rag-app-sa` and bound project roles:
  - `roles/aiplatform.user`
  - `roles/storage.objectAdmin`
  - `roles/run.admin`
  - `roles/iam.serviceAccountUser`
  - `roles/artifactregistry.admin`
  - `roles/secretmanager.secretAccessor`
  - `roles/logging.logWriter`
  - `roles/monitoring.metricWriter`
- **GCS bucket:** `gs://nervesparks-ai-assignment-rag-data` with prefixes: `raw/`, `processed/`, `indexes/`, `ui_assets/`.
- **Artifact Registry:** `rag-repo` (Docker) in `asia-south1`.
- **Secret Manager:** Secret `APP_CONFIG` with an initial value (placeholder).
- **BigQuery:** Dataset `rag_eval` in `asia-south1`.

---

## 3) Verification (final state)
### 3.1 Enabled APIs
All required APIs show **PASS**:
```
aiplatform.googleapis.com
run.googleapis.com
cloudbuild.googleapis.com
artifactregistry.googleapis.com
storage.googleapis.com
secretmanager.googleapis.com
logging.googleapis.com
monitoring.googleapis.com
cloudscheduler.googleapis.com
```

### 3.2 Service Account & Roles
- **Service Account exists:** `rag-app-sa@nervesparks-ai-assignment.iam.gserviceaccount.com`
- **Roles confirmed:**
```
roles/aiplatform.user
roles/artifactregistry.admin
roles/iam.serviceAccountUser
roles/logging.logWriter
roles/monitoring.metricWriter
roles/run.admin
roles/secretmanager.secretAccessor
roles/storage.objectAdmin
```

### 3.3 Cloud Storage (GCS)
- **Bucket:** `gs://nervesparks-ai-assignment-rag-data`
- **Location:** `asia-south1`
- **Prefixes present:**
```
/indexes/.keep
/processed/.keep
/raw/.keep
/ui_assets/.keep
```
- **Seed files uploaded (under /raw/):**
```
biology_photosynthesis_en.txt
biology_photosynthesis_hi.txt
english_grammar_en.txt
math_fractions_es.txt
```

### 3.4 Artifact Registry
- **Repository:** `rag-repo`
- **Format:** Docker
- **Region:** `asia-south1`

### 3.5 Secret Manager
- **Secret:** `APP_CONFIG`
- **Status:** Present with ≥ 1 version.

### 3.6 BigQuery
- **Dataset:** `rag_eval`
- **Region:** `asia-south1`
- **Status:** Present.

---

## 4) Notes
- Bucket names are global; chosen name is available and created.
- Service Account has the minimum set of roles needed for this project’s build & deploy flow.

---

## 5) Next Step (Task 2)
Proceed to **Vertex AI embeddings + Vector Search index**:
1. Choose multilingual embedding model in Vertex AI.
2. Prepare chunking/metadata plan.
3. Create Vector Search index & upsert vectors.
4. Test a sample query end-to-end.

---

*Prepared for: nervesparks-ai-assignment | Generated from Cloud Shell session state.*
