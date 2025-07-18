---
title: Value Added Transactions
excerpt: >-
  Enhance payments with tips and other post-sale features to elevate customer
  experience and service revenue.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Value-added transactions let you append extra charges—like gratuities or service fees—to a base payment. Use these features to streamline tipping, cover incidentals, or support custom billing scenarios.

### Prerequisites

* Active merchant account with authorization adjustment or over-capture enabled
* PCI DSS Level 1 compliance for all related operations

### Limitations

* Card network limits on over-capture amounts (typically up to 15–20% above auth)

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

# Tips

Enable customers to add a gratuity or service fee alongside their payment.

**Implementation Options**

* **Authorization Adjustment:** After initial auth, send an `adjust-transaction` request to increase the authorized amount by the tip value before capture.
* **Over-Capture:** When capturing, specify an amount higher than the original auth (within scheme limits) to include tip in a single capture call.