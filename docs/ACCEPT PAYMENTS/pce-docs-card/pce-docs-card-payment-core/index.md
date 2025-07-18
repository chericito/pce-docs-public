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
# Overview

This page outlines PCE’s Payment Core suite, empowering you to handle direct sales, separate authorizations and captures, advanced controls, refunds, tipping, and secure tokenization. Whether you need instant captures or staged workflows, PCE delivers the flexibility and compliance you require.

**In this guide you’ll learn**

* The end-to-end flows for authorizing, capturing, and refunding payments
* How to apply advanced authorization and capture controls
* Techniques for value-added transactions and secure card storage

### Prerequisites & limitations

* Active merchant account configured for card processing
* PCI DSS Level 1 compliance for payment operations
* Bank and network agreements for settlements, staged captures, and refunds

# Feature table

| Feature                         | Description                                             |
| ------------------------------- | ------------------------------------------------------- |
| Direct Sale (Immediate Capture) | Authorize and capture funds in a single API call        |
| Separate auth and captures      | Split authorization and capture into two distinct steps |
| Authorization Controls          | Incremental auth, voids, and adjustments before capture |
| Capture Controls                | Full, partial (single/multi), and over captures         |
| Refunds                         | Full and partial refunds                                |
| Value-Added Transactions        | Tip                                                     |
| Card Detail Storage             | Secure PCI-compliant tokenization and vaulting          |

# Key details

## [Direct Sale (Immediate Capture)](doc:pce-docs-direct-sale)

Process a payment with a single API call that authorizes and captures funds immediately—ideal for instant order fulfillment.

## [Separate Authorization & Capture](doc:pce-docs-separate-authorization-capture)

Authorize funds to place a hold, then capture later when goods ship or services are delivered—perfect for pre-orders and staged fulfillment.

## [Authorization Controls](doc:pce-docs-authorization-controls)

* Incremental Authorization
* Void Authorization
* Authorization Adjustments

## [Capture Controls](doc:pce-docs-capture-controls)

* Full Captures
* Single & Multi Partial Captures
* Over Capture

## [Refunds](doc:pce-docs-refunds)

* Full Refunds
* Partial Refunds (Single/Multiple)

## [Value-Added Transactions](doc:pce-docs-value-added-transactions)

* Tip

## [Card Detail Storage](doc:pce-docs-card-detail-storage)

Securely tokenize and vault customer payment details to enable subscriptions, top-ups, and faster checkouts.

***

## Card Transaction Status Lifecycle

Refer to the [Card Transaction Statuses & Reasons API guide](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-transaction#1132-card-transaction-statuses--status-reasons) for full details.

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