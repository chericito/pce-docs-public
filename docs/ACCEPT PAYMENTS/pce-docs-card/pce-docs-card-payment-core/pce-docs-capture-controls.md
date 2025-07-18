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
Capture Controls let you finalize payment settlements precisely: from capturing the full amount immediately to splitting captures across multiple shipments or even adjusting captures above the original authorization.

### Prerequisites

* Active merchant account with capture permissions
* PCI DSS Level 1 compliance

### Limitations

* Authorization must be captured within card-scheme validity (Visa: 10 days; MC/AMEX/Discover: 7 days)
* Over-capture limits subject to network rules (typically up to 15–20%)

### Compliance / Regulation Mandates

<Cards columns={4}>
  <Card title="PCI DSS Level 1" icon="fa-shield-alt">
    All card data handling—authorization, capture, routing, and tokenization—must comply with PCI DSS Level 1 standards to secure cardholder information.
  </Card>

  <Card title="PSD2 Strong Customer Authentication" icon="fa-mobile-alt">
    Two-factor authentication under PSD2 is required for EU card payments initiated by customers.
  </Card>

  <Card title="AML & KYC" icon="fa-user-check">
    Implement risk-based anti-money laundering controls and customer due diligence for card transactions, especially high-value or cross-border.
  </Card>

  <Card title="GDPR Data Protection" icon="fa-user-shield">
    Ensure personal and payment data processed in card workflows adheres to GDPR principles, including minimization, consent, and secure handling.
  </Card>
</Cards>

# Full Capture

Capture the full amount that was originally authorized. This is the most common and straightforward capture scenario.

# Partial Capture

## Single Partial Capture

Capture less than the total authorized amount in one call. You can repeat this until you’ve captured the full amount.

## Multi Capture

Useful for scenarios like e‑commerce shipments or unified commerce across channels. Each shipment or service event triggers a separate partial capture.

> **Note:** If `isFinalCapture=true` on a partial capture, the system voids any remaining authorized funds automatically.
>
> **Scheme Note:** Capturing Mastercard authorizations after expiration (7 days) may succeed but incur late-capture fees. Capturing Visa after 10 days can fail and trigger integrity fees.

**API Reference:** [Capture Transaction](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-capture-transaction)

# Over Capture

Capture an amount slightly higher than the initially authorized value—commonly used for tips, incidentals, or service charges.

**Important:** Over-capture is limited by card network rules (often up to 15–20% above auth).

**Workflow:** Specify the higher `amount` field in your capture request.

**API Reference:** [Capture Transaction](https://documentation.prioritypassport.com/passport-sandbox-docs/v3.0.0/docs/doc-capture-transaction)