---
title: Cost Recovery
excerpt: >-
  Offset card processing costs with PCE’s flexible surcharge and cost recovery
  features.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
We’re excited to introduce enhanced surcharge capabilities for both Card Present and Card Not Present transactions. PCE now automatically calculates and applies merchant-configured surcharges, providing transparency, reducing manual effort, and ensuring compliance across jurisdictions.

### Prerequisites

* Merchant account with surcharge feature enabled in MX Connect
* Merchant location must be outside surcharge-prohibited jurisdictions
* Card network and state laws must permit surcharging for credit cards

### Limitations

* **No Surcharge on Adjustments or Over Captures:** You cannot apply a surcharge to authorization adjustments or over-capture transactions. The surcharge amount on a capture cannot exceed the amount originally calculated and displayed to the customer at purchase.
* **Funding Split Rules:** Surcharge splitting behavior varies by level:
  * **Customer Level:**
    * Sale transactions: Surcharge is split according to your configured rules.
    * Sale-referenced refunds: Surcharge is split proportionally based on the refund amount.
  * **Partner Level:**
    * Surcharge splitting applies only to sale transactions; refunds are not yet supported.
  * **Program Manager (PM) Level:**
    * Surcharge splitting applies only to sale transactions; refunds are not yet supported.
* **Adhoc Refunds Not Supported for Surcharge Splitting:** Non-referenced (adhoc) refunds cannot include surcharge splitting at any level; only sale-linked refunds carry surcharge amounts.

> **Note**: The surcharge feature is currently in a pilot phase, and as such, certain restrictions may apply or functionality may evolve.

### Compliance / Regulation Mandates

* **Eligible Cards**: Surcharges only allowed on Visa, Mastercard, and Discover credit cards.
* **Prohibited Cards**: Debit or prepaid cards cannot incur surcharges, even if processed as credit.
* **State Restrictions**: No surcharging in Connecticut, Maine, Massachusetts, or Puerto Rico; Colorado capped at 2%; other permissible states capped at 3%.
* **Disclosure Requirements**: Merchants must clearly notify customers of surcharge at entry, checkout, and show it as a separate receipt line item.

# Highlights

* **Easy Opt-In:** Enable the Mx Advantage feature in MXC’s Mx Merchant product—just make sure your business address isn’t in a surcharge-prohibited jurisdiction.
* **Eligibility Rules:** Surcharging follows card network regulations and state laws, so verify your location’s requirements before applying.
* **Preview API:** Use the PCE “Preview” API to calculate and display the surcharge amount before the transaction is finalized.
* **Automatic Application:** Once configured, surcharges are applied automatically according to your funding rules.
* **Built-In Validations:** The system enforces checks on card type, jurisdiction, rate accuracy, and rounding to ensure compliance.
* **Pilot Limitations:** Certain surcharge features remain in pilot—review restrictions before full rollout.
* **Clear Integration Guide:** All required API fields and rounding rules are documented for both new and existing merchants.

## Feature Details

Getting started with surcharge configuration is simple:

1. Log in to MX Connect.
2. Navigate to MX Merchant → Features tab.
3. Enable **MX Advantage** and set your desired surcharge percentage.

This syncs your surcharge settings automatically across Card Present and Card Not Present APIs.

## Regulation Nuances

* **Allowed Card Types:** Only Visa, Mastercard, and Discover credit cards may carry a surcharge.
* **Prohibited Cards:** Debit and prepaid cards—regardless of processing method—cannot incur surcharges.
* **State Restrictions:**
  * **Prohibited:** Connecticut, Maine, Massachusetts, Puerto Rico
  * **Colorado:** Maximum surcharge 2%
  * **All Other States:** Maximum surcharge 3%
* **Disclosure Requirements:** Merchants must clearly notify customers of surcharges at entry, during checkout, and itemize the surcharge as a separate line on receipts.

## Applying Surcharge

Applying a surcharge involves passing specific parameters in your API requests:

## Card Present (CP)

* Once the card is presented and identified as eligible (credit card, not in a prohibited state), use the "Preview Surcharge" API, then send the returned surchargeAmount and the originalAmount in the transaction request.
* The receipt must clearly itemize the surcharge amount.

## Card Not Present (CNP)

* After the customer enters their card details, use the "Preview Surcharge" API. Display the surcharge transparently.
* In the payment processing API call, include the surchargeAmount and originalAmount.
* The surcharge amount must be clearly displayed on the checkout page before final submission and itemized on the digital receipt.

## Surcharge Validations

Our system enforces the following rules when processing transactions with surcharges. Understanding these is crucial for successful integration and compliance:

* The surchargeAmount can only be passed (with a value greater than zero) if the surcharge feature is explicitly enabled for the merchant in Mx Connect.
* Any attempts to apply a surcharge to debit card or prepaid card payments will be declined by the system. Surcharging is only permissible on eligible credit card transactions.
* **Configured Rate Adherence:** If a merchant's surcharge configuration is set to a specific percentage (e.g., 3%), the surchargeAmount passed in the transaction request must be the exact result of applying that configured percentage to the originalAmount (after applying Banker's Rounding, as detailed in "Recommended Integration Practices"). Merchants cannot dynamically alter the surcharge percentage per transaction (e.g., charging 2.99% or 3.01% if 3% is configured). The system will validate the surchargeAmount against the fixed configured rate.
* If the surcharge feature is enabled for a merchant, they cannot choose to selectively not apply the surcharge to eligible credit card transactions. The configured surcharge will be expected on all qualifying transactions.
* **Refunds:** Any refunds processed against a sale transaction that included a surcharge will automatically include the proportional surchargeAmount. The system will calculate and include the appropriate surcharge portion in the refund.

## Recommended Integration Practices

### Use the Preview API

Integrations should call the PCE **Preview Surcharge** API to dynamically retrieve accurate surcharge values based on card details (or token). This guarantees compliance and removes guesswork from surcharge calculations.

### Transaction Request Fields

#### `surchargeAmount`

Always include the `surchargeAmount` returned by the Preview API in your sale or auth requests.

* If surcharge is disabled for a merchant, either set `surchargeAmount` to 0 or omit the field entirely.

#### `originalAmount`

Pass the `originalAmount` node in sale/auth requests. This represents the base transaction amount before any surcharge.

### Backward Compatibility

#### Legacy Amount Field

To support existing integrations that only send an `amount` field (total including surcharge):

* If you supply both `amount` and `surchargeAmount`, the system infers `originalAmount` = `amount` − `surchargeAmount`.
* Example: `amount` = $103, `surchargeAmount` = $3 → system assumes `originalAmount` = $100.
* Note: Any `tipAmount` passed is excluded from surcharge calculation.
  * Example: `amount` = $133, `surchargeAmount` = $3, `tipAmount` = $30 → `originalAmount` assumed = $100.

#### Interim Surcharge Validation Override (IGNORE\_SURCHARGE\_VALIDATION)

A new toggle at the Program Manager (PM) level to ease integration migrations:

* **When`IGNORE_SURCHARGE_VALIDATION = TRUE`**
  * The system will accept the provided `surchargeAmount` without mismatch errors.
  * Transactions proceed even if the amount differs from the system’s internal calculation.

* **When`IGNORE_SURCHARGE_VALIDATION = FALSE` (default)**
  * The system validates your `surchargeAmount` against its own calculation (based on `originalAmount` and your configured rate, using Banker’s Rounding).
  * An error is thrown if there is any mismatch.

> **Note:** We strongly recommend transitioning to explicitly passing both `originalAmount` and `surchargeAmount` (retrieved via the Preview API and rounded correctly) so you can disable this override flag.

### Banker’s Rounding (Half to Even)

PCE enforces “round half to even” rounding for surcharge calculations. Integrations must match this to avoid errors:

* When the fractional part is exactly 0.5, round to the nearest even digit:
  * 3.455 → 3.46 (preceding digit 5 is odd, round up)
  * 3.465 → 3.46 (preceding digit 6 is even, round down)
* Other cases follow normal rounding rules:
  * 3.454 → 3.45
  * 3.456 → 3.46
* **Example:** For a $115.17 sale with a 3% surcharge:
  * Calculation: 115.17 × 0.03 = 3.4551
  * Rounded: **$3.46**

> **Note:** Any discrepancy between your pre-calculated surcharge and PCE’s calculation will cause transaction failures—ensure your system mirrors this rounding precisely.

### Customer Portal Enhancements

The “Create Collect” screen now includes a **Review Details** step, displaying the calculated surcharge before final submission so merchants can confirm amounts with their customers.