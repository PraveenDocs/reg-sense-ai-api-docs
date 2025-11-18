# POST /v1/trialdata/ingest

The `/ingest` endpoint is the primary method for submitting raw, structured clinical trial data for AI-driven regulatory compliance validation via Reg-Sense AI.

## 1. Overview

This endpoint initiates the automated compliance audit and PII (Personally Identifiable Information) risk assessment, which is mandatory before final submission to regulatory bodies. Data must adhere to the JSON schema defined below.

## 2. Request Details

| Method | Endpoint | Authentication | Rate Limit |
| :--- | :--- | :--- | :--- |
| `POST` | `/v1/trialdata/ingest` | Bearer Token (Required) | 50 requests/min |

## 3. Request Body (Payload)

The request body must be a JSON object containing the trial metadata and the patient data array.

### Schema: `trialData` Object

| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `trial_id` | String | Yes | Unique identifier for the clinical trial (e.g., `PHASE3-DRG001`). |
| `protocol_version` | String | Yes | The protocol version used for the study. |
| `patient_records` | Array[Object] | Yes | An array containing all patient-level data. |
| `client_checksum` | String | No | SHA-256 hash of the payload for data integrity verification. |

### Patient Record Sub-Schema

| Field | Type | Required | Compliance Note |
| :--- | :--- | :--- | :--- |
| `patient_hash` | String | Yes | **Mandatory** anonymized patient ID (PII protection). |
| `icd_code` | String | Yes | Primary ICD-10 or ICD-11 code for the condition. |
| `adverse_events` | Array[String] | No | List of observed adverse events. |

## 4. Example Request

Use a modern API client (like cURL or Postman) to submit the data.

```bash
curl --location '[https://api.reg-sense.io/v1/trialdata/ingest](https://api.reg-sense.io/v1/trialdata/ingest)' \
--header 'Authorization: Bearer YOUR_API_KEY_HERE' \
--header 'Content-Type: application/json' \
--data '{
    "trial_id": "DRUG-A-2025-01",
    "protocol_version": "1.3",
    "patient_records": [
        {
            "patient_hash": "a1b2c3d4e5f6g7h8",
            "icd_code": "I10",
            "adverse_events": ["headache", "nausea"]
        }
    ]
}'