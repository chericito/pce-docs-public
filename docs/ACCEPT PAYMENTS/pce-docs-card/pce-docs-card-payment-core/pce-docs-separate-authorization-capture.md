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
The Separate Authorization & Capture workflow lets you verify payment details and reserve funds at the time of order, then capture those funds later—ideal for delayed fulfillment, pre-orders, or conditional services.

### Prerequisites

* Active merchant account with card processing enabled
* PCI DSS Level 1 compliance

### Limitations

* Capture must occur within card-scheme authorization windows (e.g., Visa/MC: 7–10 days)

# Compliance / Regulation Mandates

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

# Authorization

* Verify shopper payment details with the issuer and reserve funds for the transaction.
* Authorization holds funds but does not transfer them to your account until capture.

# Capture

* Transfer reserved funds from the shopper to your account by issuing a `capture` API call.
* Default mode is **Automatic Capture**, which behaves like a Direct Sale (Immediate Capture).
* **Manual Capture** requires you to explicitly invoke the capture endpoint after order fulfillment.

# Card-Scheme Validity

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

# Use case

Cancel or modify orders before capture by issuing a `void` on the authorization if complications arise prior to fund transfer.

> 📘 Data
>
> **POST /v1/transaction HTTP/1.1**\
> **Host**: /\<hostname>
> **Authorization:** Bearer
> **Content-Type:** application/json