---
title: Direct Sale (Immediate Capture)
excerpt: >-
  Process and settle payments instantly with a single API call—ideal for
  immediate-order fulfillment.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The Direct Sale (Immediate Capture) method authorizes and captures funds in one step, delivering fast, straightforward payment processing for merchants fulfilling orders right away—such as digital goods, event tickets, or in-stock products.

### Prerequisites

* Active merchant account with card processing enabled
* PCI DSS Level 1 compliance
* Network permissions for enhanced data (L1, L2 & L3) when collecting detailed line-item information

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

# Direct Sale (Immediate Capture)

A “Direct Sale” or “Sale” transaction combines authorization and capture into a single step. This method is best when you need to charge the customer’s card and begin transferring funds as soon as the transaction is approved.

Use this method when you want a fast, one-step payment flow that immediately settles funds into your account.

1. Customer submits payment details.
2. Merchant server sends one `CREATE_TRANSACTION` API request to PCE, including amount, payment data, and optional L2/L3 fields.
3. PCE contacts card networks to authorize and immediately capture funds.
4. PCE returns a synchronous response indicating success or failure.

**Reference documentation**

* [Create Transaction API Reference](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-create-transaction)
* [API Guide: Transaction entity (CARD method)](https://documentation.prioritypassport.com/passport-docs/v2.0.0/docs/pm-entities)