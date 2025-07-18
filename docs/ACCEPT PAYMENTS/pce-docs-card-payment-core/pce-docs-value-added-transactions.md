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
# Overview

Value-added transactions let you append extra charges—like gratuities or service fees—to a base payment. Use these features to streamline tipping, cover incidentals, or support custom billing scenarios.

**In this guide you’ll learn**

* How to add tips during or after authorization
* Implementation options using authorization adjustments or over-capture
* Best practices and API considerations

### Prerequisites & Limitations

* Active merchant account with authorization adjustment or over-capture enabled
* PCI DSS Level 1 compliance for all related operations
* Card network limits on over-capture amounts (typically up to 15–20% above auth)

# Compliance / Regulation Mandates

- **PCI DSS Level 1**: All value-added transactions—including tips added via adjustments or over-capture—must comply with PCI DSS Level 1 to ensure secure handling of payment data.  
- **PSD2 Strong Customer Authentication**: In the EU, tipping and service-fee flows require two-factor authentication under PSD2 for customer-initiated charges.  
- **AML & KYC**: Perform risk-based anti-money laundering controls and customer due diligence before enabling gratuities or service charges.  
- **GDPR Data Protection**: Any personal data used in tipping functionality must adhere to GDPR principles—data minimization, explicit consent, and secure storage.  

# Feature Table

| Feature | Description                                                                     |
| ------- | ------------------------------------------------------------------------------- |
| Tip     | Allow customers to include a gratuity or service charge on top of a transaction |

# Key Details

## Tip

Enable customers to add a gratuity or service fee alongside their payment.

**Implementation Options**

* **Authorization Adjustment:** After initial auth, send an `adjust-transaction` request to increase the authorized amount by the tip value before capture.
* **Over-Capture:** When capturing, specify an amount higher than the original auth (within scheme limits) to include tip in a single capture call.

**API Reference:** See the [Create Transaction API’s Card Transactions section](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-create-transaction#a-card-transactions) for details on adjusting and capturing with extra amounts.