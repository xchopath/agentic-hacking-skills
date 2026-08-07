## Revalidate Before Making a Claim

If a user-controlled URL is identified:
- Revalidate the finding to ensure it is not a false positive.
- Verify whether any URL allowlist, hostname restriction, or validation mechanism exists before the sink.
- If an allowlist exists, document the permitted URLs/domains and evaluate whether further attack vectors, such as XSS or similar issues, are applicable.

If the issue has been proven through strict code analysis, verified evidence, and factual validation.

When a scenario is not applicable based on the observed code flow and evidence, the analysis must explicitly state "NOT APPLICABLE" instead of making assumptions.

## Accepted Findings

### 1. XSS to Invoke JavaScript Bridge

Perform an additional review to determine whether any JavaScript Bridge can be leveraged as part of the exploitation path.
1. If a potentially exploitable JavaScript Bridge is identified, notify the user that further validation requires an XSS test scenario.
2. Provide an appropriate XSS payload to evaluate JavaScript Bridge interaction only when it is supported by the observed code flow and verified evidence.

### 2. Credential/Sensitive Data Theft

Identify and review whether any interceptors carry authentication data, session information, or other sensitive data. 
If sensitive data exposure is confirmed, notify the user that validation can be performed by sending a request to a controlled host under their ownership to verify whether the data is transmitted.
