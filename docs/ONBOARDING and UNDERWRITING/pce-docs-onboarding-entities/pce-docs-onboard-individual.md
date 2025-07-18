---
title: Onboarding & Underwriting an Individual
excerpt: Effortless onboarding with built-in KYC and underwriting.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
An Individual Customer represents a sole consumer onboarded to the Passport platform for access to financial services. Identity verification is performed during onboarding to ensure compliance and secure access.


# Pre-requisites

<style> table.individual-req { width: 100%; border-collapse: separate; border-spacing: 0; border: 1px solid #f0f0f0; border-radius: 8px; overflow: hidden; font-size: 14px; margin-top: 1rem; } table.individual-req th, table.individual-req td { padding: 12px 16px; text-align: left; border-bottom: 1px solid #f6f6f6; vertical-align: top; } table.individual-req th { background-color: #fafafa; font-weight: 600; color: #333; } table.individual-req tr:last-child td { border-bottom: none; } </style> <table class="individual-req"> <thead> <tr> <th>Requirement</th> <th>Description</th> </tr> </thead> <tbody> <tr> <td>API Access</td> <td>Ensure API keys are configured for both Sandbox and Production.</td> </tr> <tr> <td>Customer Type</td> <td>Specify “individual” while creating the onboarding session.</td> </tr> <tr> <td>KYC Integration</td> <td>Use integrated third-party KYC providers for real-time verification.</td> </tr> <tr> <td>Webhook Setup</td> <td>Enable <code>onboarding.status.updated</code> and <code>kyc.manual.review.required</code>.</td> </tr> <tr> <td>Consent & Authentication</td> <td>Use Click Wrap, eSign, or Self-Signup with OTP-based validation as applicable.</td> </tr> </tbody> </table>


# Steps to Onboard an Individual

The individual onboarding process consists of six key steps that guide the user from initiation through verification to service activation:

- Start Session: Initiate the onboarding by calling the POST /onboarding/session endpoint. Ensure the customer type is set to “individual”.
- Collect Info: Gather required personal details such as full name, date of birth, contact information, and residential address.
- Identity Check: Perform a real-time identity verification using a supported KYC provider. This typically includes validation through SSN, national ID, or equivalent identifiers.
- Document Upload (if needed): If real-time KYC fails or returns inconclusive results, prompt the user to upload identity and address documents via the /documents/upload endpoint.
- Underwriting: The system performs automated risk checks, and in some cases, manual underwriting. A decision is then issued with the customer’s onboarding status.
- Provision Services: Once onboarding is approved, the platform automatically provisions related services such as account creation, card issuance, or wallet activation.


# Compliance Checks
<div style="border-left: 4px solid #4caf50; padding-left: 12px; background: #f9f9f9; margin-bottom: 1rem;"> All onboarding flows are subject to compliance verifications as per regulatory requirements. </div>
- Sanctions screening (OFAC, PEP, Watchlists) <br>
- Real-time or fallback manual KYC <br>
- Risk scoring based on service type and geography


# Integration Summary

| Integration Component | Endpoint / Feature                                    |
| --------------------- | ----------------------------------------------------- |
| Start onboarding      | `POST /onboarding/session`                            |
| Submit user info      | `POST /customers`                                     |
| Upload documents      | `POST /documents/upload`                              |
| Status updates        | `GET /customers/{id}` or Webhook                      |
| Track progress        | `onboarding.status.updated`, `document.review.failed` |


# Testing & Go Live
- Use sandbox data to simulate both approval and rejection flows.

- Trigger edge cases using invalid documents or incomplete profiles.

- Contact your Partner Success team to enable production onboarding.


# Limitations

- Supported document types may vary by country or region
- Certain profiles (e.g., minors, non-residents) may require additional review

# See Also