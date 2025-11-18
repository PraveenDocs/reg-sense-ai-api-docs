# API Error Handling

The Reg-Sense AI API uses standard HTTP response codes to indicate the success or failure of an API call. Errors are returned as a JSON object containing a brief message and a unique error code for debugging.

## 1. Common HTTP Status Codes

| Status Code | Reason Phrase | Description | Recommended Action |
| :--- | :--- | :--- | :--- |
| `200` | OK / Accepted | Successful processing, or job queued. | Check the response body for `job_id`. |
| `400` | Bad Request | Invalid JSON format or missing required fields (`trial_id`, `patient_records`). | Review the Request Body schema in the API endpoint documentation. |
| `401` | Unauthorized | Missing or invalid API key (Bearer Token). | Verify the `Authorization` header and PAT. |
| `403` | Forbidden | API key is valid but lacks access permissions to the requested resource. | Contact support to adjust API permissions. |
| `429` | Too Many Requests | Rate limit exceeded (50 requests/min). | Implement exponential backoff retry logic. |
| `500` | Internal Server Error | An unexpected server condition occurred. | Retry the request; if persistent, contact Reg-Sense AI support. |

## 2. Example Error Response

All non-200 responses follow this consistent JSON structure:

```json
{
    "error_code": "RS-400-003",
    "message": "Required parameter 'patient_records' is missing from the request body.",
    "timestamp": "2025-11-18T16:15:00Z",
    "documentation_url": "[https://docs.reg-sense.ai/errors#RS-400-003](https://docs.reg-sense.ai/errors#RS-400-003)"
}