---
title: Split Payouts
excerpt: >-
  Split incoming funds across multiple accounts or recipients using customizable
  funding rules in PCE.
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

PCE’s Split Payouts feature lets you define funding rules to distribute transaction proceeds automatically among various accounts—ideal for marketplaces, partners, or multi-entity settlements.

**In this guide you’ll learn**

* How to create and manage funding rules for multiple recipients
* The methods and boundaries supported for splitting payouts
* How reversals and recoupment flows work under funding rules

### Prerequisites & Limitations

* Active merchant or partner account with Split Payouts enabled

### Compliance / Mandates

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

# Compliance / Regulation Mandates

* **PCI DSS Level 1**: Ensure secure handling of card and account data across split payout workflows.
* **AML & KYC**: Perform risk-based due diligence and identity verification for each payout recipient.
* **PSD2 Strong Customer Authentication**: In EU, two-factor authentication is required for funds release in customer-initiated flows.
* **GDPR Data Protection**: Protect and minimize personal data in payout configurations, obtaining explicit consent where necessary.

# Feature Table

| Feature                 | Description                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Rules Management        | Define, clone, and enforce funding rules at customer, partner, or PM levels                                        |
| Supported Methods       | ACH, Card, Check, Wire, and CASH payout splits                                                                     |
| Active Rules Boundaries | One active rule per transaction method/component per customer (e.g., CARD:TIP and CARD:SURCHARGE allowed together) |
| Reversals & Recoupment  | Handle chargebacks, refunds, and returns with configurable recoupment flows when splits were applied               |

# Key Details

## Key Features

* **Intuitive Rule Creation:** End users—whether customers, partners, or program managers—can easily define or clone funding rules directly from their portal dashboards.
* **Override Hierarchies:** Authoritative entities can lock rules to prevent changes, or allow subordinate levels to adjust cloned rules as needed.
* **Tag-Based Splitting:** Use transaction metadata tags (e.g., TIP, SURCHARGE, TRUST) to automatically direct portions of a payment to the appropriate accounts.

## Use Cases in Scope

* **Legal Trust Accounting:** Automatically route incoming card payments into “Trust” and “Operational” ledgers by matching tags flagged as TRUST.
* **Surcharge Allocation:** Divide the surcharge component of a transaction into a separate account designated for fee recovery.
* **Tip Distribution:** Direct gratuity amounts to individual service provider accounts within PCE.

## Customer Funding Rule Setup

1. In the customer portal, click your user initials in the bottom-left corner to open **Funding Rules**.
2. Select **Add New** to begin rule configuration:
   * **Rule Condition:** Choose whether the rule applies to all transactions or filter by specific tags (for example, TIP or SURCHARGE).
   * **Rule Action:** Assign recipient account tags and specify the percentage or fixed amount to split to each account.
3. Review the **Linked Transactions** list to verify which payments have been processed under this rule.

## Program Manager Funding Rule Management

Program Managers can establish and oversee rules for their customers and associated partners:

* Navigate to the **Funding Rules** section of the PM portal.
* Click **Add** to create a new rule, with options to set override permissions and target recipient accounts.

## Configurations

### Portal Toggles

* **PM Portal Toggle:** Enable `Show Funding Rule PM Portal` to give program managers access to create and manage rules for their downstream partners and customers.
* **Partner Portal Toggle:** Enable `Show Funding Rule Partner Portal` to allow partners to configure rules for their linked customers.
* **Customer Portal Toggle:** Enable `Show Funding Rule Customer Portal` to let customers manage their own funding rules.

## Recouping Funds

In the event of a reversal (chargeback, refund, or return) on a split transaction:

1. The system first attempts to debit the customer’s default account.
2. If additional funds need recoupment, it withdraws from the other split accounts according to the original funding rule.
3. If internal balances are insufficient, the system pulls the remaining amount from the customer’s external bank account.

## Additional Remarks

* Access to create or edit funding rules is governed by role-based permissions—only authorized users will see the rule management features.
* When splitting **CARD** transactions, you can separate by TIP, SURCHARGE, or SUBTOTAL components; for ACH, Cash, Wire, and Check methods, splits apply only to the TOTAL AMOUNT.
* If you define a multi-method rule that includes CARD, but only configure the TOTAL AMOUNT component, that total will apply across all specified methods.