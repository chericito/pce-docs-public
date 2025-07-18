---
title: Separate Authorization and Capture
excerpt: >-
  The Separate Authorization & Capture workflow lets you verify payment details
  and reserve funds at the time of order, then capture those funds later—ideal
  for delayed fulfillment, pre-orders, or conditional services.
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

The Separate Authorization & Capture workflow lets you verify payment details and reserve funds at the time of order, then capture those funds later—ideal for delayed fulfillment, pre-orders, or conditional services.

**In this guide you’ll learn**

* How to perform and manage separate auth and capture flows
* Card-scheme validity windows and capture timing
* Differences between automatic and manual capture modes

### Prerequisites & Limitations

* Active merchant account with card processing enabled
* PCI DSS Level 1 compliance
* Capture must occur within card-scheme authorization windows (e.g., Visa/MC: 7–10 days)

# Compliance / Regulation Mandates

- **PCI DSS Level 1**: Ensure all authorization and capture operations comply with PCI DSS Level 1 standards to protect cardholder data.  
- **PSD2 Strong Customer Authentication**: EU authorizations require two-factor authentication under PSD2 for customer-initiated payments.  
- **AML & KYC**: Apply risk-based anti-money laundering controls and customer due diligence before placing or capturing holds on funds.  
- **GDPR Data Protection**: Adhere to GDPR principles—data minimization, explicit consent, and secure handling—when processing EU citizens’ payment information.  

# Feature Table

| Feature                      | Description                                                       |
| ---------------------------- | ----------------------------------------------------------------- |
| Two-Step Processing          | Separate `authorize` and `capture` API calls                      |
| Automatic Capture            | Default: capture immediately after authorization                  |
| Manual Capture               | Trigger capture via explicit API request when you’re ready        |
| Card-Scheme Validity Windows | AMEX: 7 days; Mastercard: 7 days; Visa: 10 days; Discover: 7 days |

# Key Details

## Authorization

* Verify shopper payment details with the issuer and reserve funds for the transaction.
* Authorization holds funds but does not transfer them to your account until capture.

## Capture

* Transfer reserved funds from the shopper to your account by issuing a `capture` API call.
* Default mode is **Automatic Capture**, which behaves like a Direct Sale (Immediate Capture).
* **Manual Capture** requires you to explicitly invoke the capture endpoint after order fulfillment.

## Card-Scheme Validity

Each card network enforces a hold window for authorizations:

* **AMEX**: 7 days
* **Mastercard**: 7 days
* **Visa**: 10 days
* **Discover**: 7 days

> **Note:** Capture must occur within the network’s authorization window to avoid expired holds.

## Typical Flow Example

1. Customer submits payment details.
2. Merchant sends `authorize` request with `capture=false`, placing a hold on funds.
3. Authorization remains valid for the card-scheme window.
4. Upon shipping or service delivery, merchant sends `capture` request referencing the original auth.
5. PCE processes the capture and returns a confirmation of the fund transfer.

---

> **Use case:** Cancel or modify orders before capture by issuing a `void` on the authorization if complications arise prior to fund transfer.