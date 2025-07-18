---
title: Prenotification
excerpt: >-
  Confirm bank account ownership by sending two small, random test deposits that
  users verify—widely supported and reliable across all banks.
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

Micro-deposit verification sends two nominal credit amounts (typically under \$1.00) to a customer’s bank account to prove ownership. After 1–2 business days, the customer retrieves these amounts from their statement and submits them back in your app. Once confirmed, the same amounts are debited back, completing the validation cycle.

**In this guide you’ll learn**

* How micro-deposits establish account access securely
* The typical timelines and customer experience flow
* Best practices for handling failures and timeouts

### Prerequisites & Limitations

* Merchant must have permission to debit and credit small test amounts
* Accurate routing and account numbers are required at submission
* Introduces at least a 1–2 business-day delay before live transactions
* Relies on customer action—higher friction than instant methods

# Compliance / Regulation Mandates

* **Nacha Rules**: Micro-deposits count as live ACH credits and must follow standard SEC code requirements and return windows.
* **Customer Consent**: Written or digital authorization must cover these zero-net transactions.
* **CIP Documentation**: Recording this validation step supports Customer Identification Program compliance.

# Feature Table

| Feature                 | Description                                                        |
| ----------------------- | ------------------------------------------------------------------ |
| Dual Random Deposits    | Send two small, unique credits (<\$1 each) to the customer account |
| User Verification       | Customer inputs both deposit amounts to confirm account access     |
| Automated Cleanup       | System pulls back the test deposits once verification completes    |
| Universal Bank Coverage | Works with nearly all U.S. financial institutions                  |

# Key Details

Micro-deposit verification is ideal when you need universal bank coverage and can tolerate a brief onboarding delay. Unlike instant methods, it doesn’t rely on third-party connectivity—any bank that processes ACH credits will accept the test deposits.

1. **Initiate Test Deposits**
   Use your ACH debit API to send two credit entries of random values (e.g., \$0.12 and \$0.47) to the customer’s external account, flagged as verification entries.

2. **Await Customer Action**
   After 1–2 business days, the customer logs into your application and enters the exact amounts they see on their bank statement. This step proves they have access to the account.

3. **Verify and Confirm**
   Match the submitted values against the amounts you sent. If they match, mark the account as verified. Otherwise, prompt the customer to retry or choose another verification method.

4. **Automated Reversal**
   Once verification succeeds, immediately initiate two debit entries for the same amounts to remove the test deposits, so the customer’s balance returns to its original level.

5. **Failure Handling**

   * If the customer submits incorrect amounts three times, expire the micro-deposit session and require re-submission.
   * If no match is received within seven days, automatically cancel the verification and notify the customer to restart the process.

**When to Use Micro-Deposits**
Choose micro-deposits when bank coverage is paramount and you can accept a slight delay and extra customer effort. For high-trust B2B integrations or platforms prioritizing inclusive bank support, this method strikes the right balance between reliability and cost.