---
title: Refunds
excerpt: >-
  Return funds securely with sale-referenced or adhoc refunds—full or
  partial—while ensuring proper validation and risk controls.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
`PCE` supports two refund workflows: **Sale Referenced Refunds**, which link directly to an original transaction for maximum security and reconciliation, and **Adhoc Refunds**, which act as standalone payouts when no original reference exists. This page details when and how to use each method, plus guidelines for full and partial refund operations.

### Prerequisites

* Merchant account with refund permissions
* PCI DSS Level 1 compliance for linked refunds
* Adhoc refunds require explicit activation and KYC checks
* Sale referenced refunds need a valid original transaction reference

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

<br />

# Feature Table

| Feature                 | Description                                                            |
| ----------------------- | ---------------------------------------------------------------------- |
| Sale Referenced Refunds | Secure refunds tied to an original transaction to prevent fraud        |
| Adhoc Refunds           | Standalone credits (payouts) for promotions, goodwill, or corrections  |
| Full Refunds            | Return the entire captured amount                                      |
| Partial Refunds         | Return part of a captured payment; multiple partials up to full amount |

# Key Details

## Sale Referenced Refunds

Sale referenced refunds link a reversal directly to its original sale transaction. This ensures you don’t refund more than the captured amount and provides automated reconciliation checks.

**When to use**

* Product returns (online or in-store)
* Partial refunds for out-of-stock items
* Service cancellations with prorated refunds

**Workflow**

1. Identify the original sale transaction ID.
2. Send a refund request with the `parent` field set to the transaction’s `id` or `externalId`.
3. PCE validates that the refund amount ≤ original capture and queues the refund.
4. Refund processes once the parent transaction reaches **COMPLETED** status.

**Validations**

* `parent` must be the correct `id` or `externalId` of the transaction.
* Refunds can be initiated when parent is in **PROCESSING**, **APPROVED**, or **COMPLETED**, but will only execute once **COMPLETED**.
* Sum of all refunds for a transaction ≤ original capture amount.

## Adhoc Refunds

Adhoc refunds (non-referenced) create standalone credit transactions not tied to any prior sale. They require additional risk controls and are disabled by default.

**When to use**

* Goodwill gestures (customer service credits)
* Promotional payouts or cashback rewards
* Error corrections without original transaction reference
* Insurance or claim payouts directly to card

**Security note**

* Requires KYC verification and explicit feature enablement
* Bypasses closed-loop protections of referenced refunds

## Full Refunds

Refund the entire captured amount in one request.

**Workflow**

* Send a refund API call referencing the original capture.

**API Reference:** [Refund Transaction](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-refund-transaction)

## Partial Refunds

Issue refunds for a portion of the captured amount; you may perform multiple partial refunds until the full amount is returned.

**Use cases**

* Customer returns one item from a multi-item order
* Prorated service cancellations

**Workflow**

* In your refund request, specify the partial `amount` to return.
* Repeat until total refunded ≤ original capture.

**API Reference:** [Refund Transaction](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-refund-transaction)

***

For card refund details and parameter definitions, see the [Card Transactions section](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-create-transaction#a-card-transactions) of the Create Transaction API guide.

### Validations

* Make sure the **parent** field uses the original transaction’s **id** or **externalId**—that’s how we know which payment to refund.
* You can request a refund when the original transaction is **PROCESSING**, **APPROVED**, or **COMPLETED**, but we’ll only process it once the transaction reaches **COMPLETED**.
* Your refund **amount** must be less than or equal to the original transaction amount for sale-referenced refunds.
* If you’re issuing multiple refunds on the same transaction, the combined refund total can’t exceed the original payment amount.