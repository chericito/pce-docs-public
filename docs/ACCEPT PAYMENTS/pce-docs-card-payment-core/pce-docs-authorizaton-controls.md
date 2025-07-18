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
# Overview

Explore PCE’s authorization management toolkit, offering incremental auth, voids, and adjustments to match real-world billing needs.

**In this guide you’ll learn**

* How to increase held funds post-authorization
* When and how to void pending authorizations
* Steps to adjust authorization amounts before capture

### Prerequisites & Limitations

* Active merchant account with card processing enabled
* PCI DSS Level 1 compliance for authorization operations
* Capture must occur within card-scheme validity windows (7–10 days)

# Compliance / Regulation Mandates

- **PCI DSS Level 1**: All card data storage, processing, and transmission must meet PCI DSS requirements to protect cardholder data.  
- **PSD2 Strong Customer Authentication**: EU transactions require SCA under PSD2 for customer-initiated e-commerce payments, ensuring two-factor authentication.  
- **AML & KYC**: Implement risk-based Anti-Money Laundering controls, including CIP, CDD, and EDD to comply with global AML regulations.  
- **GDPR Data Protection**: Personal and payment data storage must adhere to GDPR principles—data minimization, explicit consent, and security-by-design—when handling EU citizen data.  

# Feature Table

| Feature                   | Description                                                         |
| ------------------------- | ------------------------------------------------------------------- |
| Incremental Authorization | Increase an authorization amount without creating a new transaction |
| Void Authorization        | Cancel a pending authorization to release held funds                |
| Authorization Adjustments | Modify authorized amounts (up or down) prior to capture             |

# Key Details

## Incremental Authorization

Increase the authorized amount on an existing transaction before it’s captured, ensuring coverage for additional costs.

**Use cases**

* Hotel stays (mini-bar charges)
* Car rentals (fuel fees)

**Workflow**

1. Initial Auth: Guest checks in; authorize \$300 for a two-night stay.
2. Incremental Auth: Guest orders \$50 dinner; request additional \$50 authorization (total \$350).
3. Another Incremental Auth: Guest incurs \$25 breakfast; request additional \$25 (total \$375).
4. Capture: At checkout, capture final amount of \$375.

## Void Authorization

Cancel an existing authorization that hasn’t been captured to release held funds and avoid unnecessary fees.

**Benefits**

* Avoids refund-related transaction fees
* Prevents settled charges from appearing on customer statements

**Workflow**

1. Identify the original authorization ID.
2. Send a void request referencing that authorization.

**API References**

* [Void Transaction](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-void-transaction)
* [Void Capture](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-capture-transaction#e-void-capture)

## Authorization Adjustments

Adjust an existing authorization amount—either up or down—before capture to correct or finalize charges.

**Use cases**

* Tipping or service fees
* Final price adjustments based on weight, quantity, or additional services

**Workflow**

1. Authorize initial amount.
2. For each change in amount, send an adjustment request (increase or decrease).
3. After the last adjustment, capture the final authorized amount.

**API Reference:** [Adjust Transaction](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-adjust-transaction)