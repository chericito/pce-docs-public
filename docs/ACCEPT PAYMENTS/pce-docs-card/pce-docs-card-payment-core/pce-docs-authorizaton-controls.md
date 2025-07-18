---
title: Authorization Controls
excerpt: >-
  Manage and refine payment authorizations with granular controls for dynamic
  transaction scenarios.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Explore PCE’s authorization management toolkit, offering incremental auth, voids, and adjustments to match real-world billing needs.

### Prerequisites

* Active merchant account with card processing enabled
* PCI DSS Level 1 compliance for authorization operations

### Limitations

* Capture must occur within card-scheme validity windows (7–10 days)

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

# Incremental Authorization

Increase the authorized amount on an existing transaction before it’s captured, ensuring coverage for additional costs.

**Use cases**

* Hotel stays (mini-bar charges)
* Car rentals (fuel fees)

**Workflow**

1. Initial Auth: Guest checks in; authorize $300 for a two-night stay.
2. Incremental Auth: Guest orders $50 dinner; request additional $50 authorization (total $350).
3. Another Incremental Auth: Guest incurs $25 breakfast; request additional $25 (total $375).
4. Capture: At checkout, capture final amount of $375.

# Void Authorization

Cancel an existing authorization that hasn’t been captured to release held funds and avoid unnecessary fees.

**Benefits**

* Avoids refund-related transaction fees
* Prevents settled charges from appearing on customer statements

**Workflow**

1. Identify the original authorization ID.
2. Send a void request referencing that authorization.

* [Void Transaction](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-void-transaction)
* [Void Capture](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-capture-transaction#e-void-capture)

# Authorization Adjustments

Adjust an existing authorization amount—either up or down—before capture to correct or finalize charges.

**Use cases**

* Tipping or service fees
* Final price adjustments based on weight, quantity, or additional services

**Workflow**

1. Authorize initial amount.
2. For each change in amount, send an adjustment request (increase or decrease).
3. After the last adjustment, capture the final authorized amount.

**API Reference:** [Adjust Transaction](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-adjust-transaction)