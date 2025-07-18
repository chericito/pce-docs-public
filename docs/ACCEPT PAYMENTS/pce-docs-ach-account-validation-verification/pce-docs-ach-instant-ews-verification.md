---
title: Instant EWS Verification
excerpt: >-
  Instantly confirm a customer’s bank account status and ownership via Early
  Warning Services (EWS) to minimize ACH return risk and meet Nacha
  “commercially reasonable” requirements.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Overview

Before initiating an ACH debit, you need to ensure the customer’s account is open, valid, and authorized for debits. PCE’s EWS integration offers real-time verification—eliminating wait times and manual steps—to dramatically reduce returns (e.g. R02, R03, R04) and satisfy Nacha rules for WEB-initiated debits.

**In this guide you’ll learn**

* How Instant EWS Verification works and why it matters for WEB entries
* Key integration considerations and fallback strategies
* How to interpret and act on EWS response codes

### Prerequisites & Limitations

* You must have EWS access enabled on your PCE merchant profile
* Customer must provide account number, routing number, and account type
* Coverage: real-time for U.S. consumer and most business accounts; fallback needed for unlisted FI’s

# Compliance / Regulation Mandates

* **Nacha “Commercially Reasonable” Requirement:** WEB SEC code mandates use of automated fraud-detection or validation (e.g., EWS).
* **Return Mitigation:** Early validation helps avoid costly returns within two banking days.

# Feature Table

| Feature                    | Description                                                |
| -------------------------- | ---------------------------------------------------------- |
| Instant EWS Verification   | Real-time “is account open and owned by this name?” check  |
| Ownership Confirmation     | Verifies that the name on the account matches the customer |
| Negative‐History Screening | Flags accounts with recent returns or blocks               |

# Key Details

## How Instant EWS Verification Works

When you collect routing and account numbers in your UI, call PCE’s EWS endpoint to confirm:

1. **Account Status** (OPEN vs. CLOSED)
2. **Ownership Match** (name vs. account holder file)
3. **Negative History** (recent returns, freezes, or blocks)

If verification passes, proceed with debit origination. If it fails (e.g. `ACCOUNT_CLOSED` or `NAME_MISMATCH`), prompt the customer to correct their details or choose another payment method.

### Possible Response Codes

* `VERIFIED` – OK to debit
* `ACCOUNT_CLOSED` – reject or re-collect details
* `NAME_MISMATCH` – prompt user to update name
* `NEGATIVE_HISTORY` – decline or require manual review
* `EWS_UNAVAILABLE` – fallback to Prenote or micro-deposit

## Integration Considerations

* **Fallback Strategy:** Always implement a secondary path (prenote or micro-deposits) for accounts that EWS cannot verify.
* **User Experience:** For high-volume consumer apps, front-load EWS to reduce drop-off; for B2B, micro-deposits may be acceptable if coverage gaps exist.
* **Error Handling:** Handle `EWS_UNAVAILABLE` gracefully—queue the transaction for delayed verification rather than outright decline.
* **Security:** Transmit verification requests over TLS and never log full account details in plaintext.
