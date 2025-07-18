---
title: Payment Core
excerpt: >-
  Explore PCE’s core payment processing features—from Direct Sale through secure
  card storage—to manage every step of the payment lifecycle.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
This page outlines PCE’s Payment Core suite, empowering you to handle direct sales, separate authorizations and captures, advanced controls, refunds, tipping, and secure tokenization. Whether you need instant captures or staged workflows, PCE delivers the flexibility and compliance you require.

### Prerequisites

* Active merchant account configured for card processing
* PCI DSS Level 1 compliance for payment operations
* Bank and network agreements for settlements, staged captures, and refunds

***

# [Direct Sale (Immediate Capture)](doc:pce-docs-direct-sale)

Process a payment with a single API call that authorizes and captures funds immediately—ideal for instant order fulfillment.

# [Separate Authorization & Capture](doc:pce-docs-separate-authorization-capture)

Authorize funds to place a hold, then capture later when goods ship or services are delivered—perfect for pre-orders and staged fulfillment.

# [Authorization Controls](doc:pce-docs-authorization-controls)

* Incremental Authorization
* Void Authorization
* Authorization Adjustments

# [Capture Controls](doc:pce-docs-capture-controls)

* Full Captures
* Single & Multi Partial Captures
* Over Capture

# [Refunds](doc:pce-docs-refunds)

* Full Refunds
* Partial Refunds (Single/Multiple)

# [Value-Added Transactions](doc:pce-docs-value-added-transactions)

* Tip

# [Card Detail Storage](doc:pce-docs-card-detail-storage)

Securely tokenize and vault customer payment details to enable subscriptions, top-ups, and faster checkouts.

***

# Card Transaction Status Lifecycle

| Status              | Description                                                                                                       |
| ------------------- | ----------------------------------------------------------------------------------------------------------------- |
| UNCAPTURED          | Default state after authorization.                                                                                |
| PARTIALLY\_CAPTURED | Some or all funds captured but `isFinalCapture` not set; can revert if a capture is voided.                       |
| CAPTURED            | When captured amount equals or exceeds auth, or when a lesser amount is captured with final capture set.          |
| COMPLETED           | Post realization (good-funds) interval or upon successful refund completion.                                      |
| FAILED              | Network or processor failure response.                                                                            |
| VOIDED              | Auth or capture voided by merchant before settlement.                                                             |
| APPROVED            | Default on creation of capture or refund transactions; previous INITIATED status used only by older integrations. |

> **Note:** New integrations will see captures and refunds created directly in **APPROVED** status. Legacy integrations may still surface **INITIATED**.