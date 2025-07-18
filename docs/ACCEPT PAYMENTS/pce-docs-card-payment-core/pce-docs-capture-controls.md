---
title: Capture Controls
excerpt: >-
  Manage how and when authorized funds are captured—full, partial, or above the
  original amount.
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

Capture Controls let you finalize payment settlements precisely: from capturing the full amount immediately to splitting captures across multiple shipments or even adjusting captures above the original authorization.

**In this guide you’ll learn**

* The differences between full, partial, and over captures
* How to perform single vs. multi-step captures
* Scheme-specific capture windows and late-capture considerations

### Prerequisites & Limitations

* Active merchant account with capture permissions
* PCI DSS Level 1 compliance
* Authorization must be captured within card-scheme validity (Visa: 10 days; MC/AMEX/Discover: 7 days)
* Over-capture limits subject to network rules (typically up to 15–20%)

# Compliance / Regulation Mandates

- **PCI DSS Level 1**: All capture and settlement operations must comply with PCI DSS Level 1 standards to ensure cardholder data security.  
- **PSD2 Strong Customer Authentication**: European capture operations require two-factor authentication under PSD2 for customer-initiated payments.  
- **AML & KYC**: Perform anti-money laundering checks and customer due diligence before authorizing or capturing high-risk transactions.  
- **GDPR Data Protection**: Ensure any personal or payment data used in capture workflows adheres to GDPR principles, including data minimization and explicit consent.  

# Feature Table

| Feature                | Description                                                            |
| ---------------------- | ---------------------------------------------------------------------- |
| Full Capture           | Capture the entire authorized amount in one operation                  |
| Single Partial Capture | Capture a portion of the auth amount, repeatable until full settlement |
| Multi Capture          | Perform multiple partial captures (e.g., per shipment or location)     |
| Over Capture           | Capture an amount above the original auth (within scheme limits)       |

# Key Details

## Full Capture

Capture the full amount that was originally authorized. This is the most common and straightforward capture scenario.

## Partial Capture

### Single Partial Capture

Capture less than the total authorized amount in one call. You can repeat this until you’ve captured the full amount.

### Multi Capture

Useful for scenarios like e‑commerce shipments or unified commerce across channels. Each shipment or service event triggers a separate partial capture.

> **Note:** If `isFinalCapture=true` on a partial capture, the system voids any remaining authorized funds automatically.

> **Scheme Note:** Capturing Mastercard authorizations after expiration (7 days) may succeed but incur late-capture fees. Capturing Visa after 10 days can fail and trigger integrity fees.

**API Reference:** [Capture Transaction](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-capture-transaction)

## Over Capture

Capture an amount slightly higher than the initially authorized value—commonly used for tips, incidentals, or service charges.

**Important:** Over-capture is limited by card network rules (often up to 15–20% above auth).

**Workflow:** Specify the higher `amount` field in your capture request.

**API Reference:** [Capture Transaction](https://documentation.prioritypassport.com/passport-sandbox-docs/v3.0.0/docs/doc-capture-transaction)