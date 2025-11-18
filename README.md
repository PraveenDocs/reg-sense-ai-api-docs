# 🩺 Reg-Sense AI API Documentation

This repository hosts the full technical documentation for the **Reg-Sense AI Compliance API**, a cloud-based service designed to automate regulatory compliance and PII (Personally Identifiable Information) risk assessment for clinical trial data.

Our service ensures data integrity and adherence to global regulatory standards (e.g., ICD-10, PII standards) before final submission to agencies like the FDA or EMA.

---
## 🗺️ Documentation Map

For a comprehensive overview and direct links to all technical and regulatory guides, see the [Table of Contents (TOC)](TOC.md).

---
## 🚀 Getting Started

Follow these steps to quickly integrate and begin using the Reg-Sense AI API.

### 1. Authentication

The API requires a **Bearer Token** passed in the `Authorization` header.

For details on acquiring and using your API key, see the dedicated guide:
[auth.md](api/auth.md)

### 2. Quick Start Endpoint

The primary method for submitting raw, structured clinical trial data is the ingestion endpoint.

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/v1/trialdata/ingest` | Submits data for automated compliance auditing and queuing. |

View the full request schema and data models here:
[ingestion.md](api/ingestion.md)

### 3. Error Handling

All non-200 responses return a consistent JSON structure for easy debugging.

* **Reference:** Consult the [errors.md](api/errors.md) guide for a full list of status codes and troubleshooting steps.

---

## 🔗 Repository Structure

This repository uses a Docs-as-Code structure to keep documentation close to the code base.