---
title: Card Detail Storage
excerpt: >-
  Securely vault and tokenize card details to accelerate checkouts and minimize
  PCI scope.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Card Detail Storage lets you securely save customer payment information in a PCI-compliant vault, enabling faster checkouts, subscription billing, and automatic top-ups—without handling raw card data.

### Prerequisites

* Active merchant account with card-vaulting enabled
* PCI DSS Level 1 compliance
* Shopper consent for storing payment details

### Limitations

* Token operations subject to network and regional data rules

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

# Card Details Storage

Securely store customer payment details to streamline future purchases. We provide a fully PCI DSS Level 1–compliant vault using tokenization to protect card data, reduce your PCI scope, and simplify compliance. With shopper consent, you can store one or more payment methods per customer.

We refer to saved payment details as **tokens**, and the process as **tokenization**.

**Benefits of tokenization**

* Let shoppers store payment details for one-click or recurring payments.
* Support subscriptions, installment plans, and automatic account top-ups.
* Remove sensitive data handling from your systems—shrink your PCI footprint.

**Use cases**

* E-commerce platforms offering saved cards for returning customers.
* SaaS and membership billing with recurring charges.
* Prepaid account reloads or wallet top-ups without re-entering card data.

**API Reference:** Refer to the tokenization section in the Appendix of the API guide:\
[Card Tokenization API](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-card-tokenization)