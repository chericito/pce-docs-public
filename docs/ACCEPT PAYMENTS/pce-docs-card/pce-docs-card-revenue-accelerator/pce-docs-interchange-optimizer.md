---
title: Interchange Optimizer
excerpt: "Optimize your interchange costs by supplying Level\_1–3 data in CARD transactions for reduced processing fees."
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The Interchange Optimizer feature lets merchants submit enhanced transaction details—Level 1, Level 2, and Level 3—to qualify for lower interchange rates. By providing more granular invoice, shipping, and tax information, you can reduce fees on corporate and purchase cards.

### Prerequisites

* Merchant account approved for corporate or purchase-card acceptance
* PCE with Level 2/Level 3 data enabled in your configuration
* Qualification ultimately determined by the card network and issuing bank

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

# Level 1 Processing

Basic transaction data: card number, expiration, amount, and merchant descriptor. This is the default and requires the least information.

# Level 2 Processing

Adds mid-level details to qualify for corporate rates:

* Card number, expiration, billing and shipping addresses
* Invoice number or unique purchase-order (PO) reference
* Tax amount separate from total transaction value

> *Level 2 submissions typically reduce fees on corporate and purchase cards when accepted by networks.*

# Level 3 Processing

Requires comprehensive, line-item data for the lowest interchange rates:

* All Level 2 fields
* Unit price or unit amount and unit-of-measure
* Freight, shipping, and duty amounts
* Discount amount and discount code
* Commodity or product codes
* Item description and quantity
* Unit tax and unit discount
* Ship‑from ZIP code

> **Note:** Not all transactions qualify; final eligibility is determined by the card network and issuing bank.

The customer portal and API both support adding Level 2 and Level 3 fields. Ensure your payload includes the required properties to unlock lower interchange tiers.