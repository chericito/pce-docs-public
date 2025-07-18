---
title: Integration Methods
excerpt: >-
  Choose between direct API integration or secure client-side encryption with
  PCE’s JavaScript SDK for your payment flows.
deprecated: false
hidden: false
metadata:
  robots: index
---
This guide covers two integration methods for handling card data with PCE: direct REST APIs and in-browser encryption via our JavaScript SDK. Both approaches protect sensitive data, reduce PCI scope, and simplify compliance.

### Prerequisites & Limitations

* Active PCE account with API credentials
* HTTPS-enabled website for JS SDK integration
* PCI DSS Level 1 compliance for server-side storage and processing
* Customer consent and data-handling policies in place

# Compliance / Regulation Mandates

* **PCI DSS Level 1:** All card data in transit and at rest must meet PCI Level 1 security standards.
* **PSD2 Strong Customer Authentication:** EU customer-initiated flows require two-factor authentication.
* **AML & KYC:** Apply risk-based anti-money laundering checks and customer due diligence for high-risk transactions.
* **GDPR Data Protection:** Collect only necessary personal data, secure it, and obtain explicit consent for processing.

# Feature Table

| Feature                  | Description                                                                           |
| ------------------------ | ------------------------------------------------------------------------------------- |
| APIs only                | Call PCE’s REST endpoints directly to tokenize, charge, and manage payments           |
| Card Encryption using JS | Use the PCE JavaScript SDK to encrypt card details in the browser before tokenization |

# Key Details

## APIs only

Use PCE’s REST APIs to handle the full payment lifecycle on your server. You send raw or tokenized payment data over HTTPS, receive synchronous responses, and manage your own PCI environment.

## Card Encryption using JS

Leverage PCE’s JavaScript SDK to collect and encrypt card details client-side so sensitive data never touches your servers.

### Overview

Card tokenization replaces sensitive card data with a non-reversible token. PCE’s JS SDK captures card information on the client, returns a token, and keeps raw PANs out of your environment.

**Benefits of Card Tokenization**

* Safe PCI compliance and security
* Reduced liability by never storing raw card data

**Pre-requisites**

* Whitelist your application URL with PCE to allow SDK usage on that domain

### Steps to Tokenize Card

**Import the JS SDK**Include the appropriate script tag for your environment:

```html
<!-- Production -->
<script src="https://js.prioritypassport.com/"></script>

<!-- Sandbox -->
<script src="https://js.sandbox.prioritypassport.com/"></script>
```

**Collect Card Information**Use secure input fields named exactly as shown to let the SDK encrypt:

| Field          | Optional/Mandatory | Description                            |
| -------------- | ------------------ | -------------------------------------- |
| cardNumber     | Mandatory          | 13–17 digit card number                |
| cvv            | Mandatory          | 3–4 digit CVV                          |
| brand          | Optional           | Card brand name                        |
| expiryMonth    | Mandatory          | Month of expiry (01–12)                |
| expiryYear     | Mandatory          | Year of expiry (YYYY, not in the past) |
| holderName     | Optional           | Cardholder’s name                      |
| addressLine1   | Optional           | Billing address line 1                 |
| city           | Optional           | Billing city                           |
| state          | Optional           | Billing state                          |
| zip            | Optional           | 5- or 9-digit postal code              |
| billingAddress | Optional           | Recommended for AVS                    |

**Sample HTML Form**

```html
<form action="" id="card">
  <!-- ... form fields as defined above ... -->
  <input class="btn btn-success" type="button" onclick="submitForm()" value="Submit">
</form>
```

**Generate a Token**

```javascript
const ps = new PassportCheckout();
const response = await ps.getToken(
  document.forms.card,
  { secureform: true, bindToken: true }
);
if (response.status === 1) {
  alert('Token generated successfully: ' + response.token);
} else {
  alert('Error occurred: ' + response.errorMessage);
}
```

* **secureform:** true clears fields after tokenization
* **bindToken:** true injects a hidden `token` field in the form

### Store and Use the Token

* **Success:** `response = { status: 1, token: "$extractedSecret" }`
* **Failure:** `response = { status: 0, errorMessage: "$errorMessage" }`

Use the token for a single charge or to vault the card via PCE APIs.

### Decrypting the Token

Base64-decode the token to extract:

* Last 4 digits
* Card type (CREDIT, DEBIT, UNKNOWN)
* Card brand (VISA, MASTERCARD, etc.)
* Token ID and expiry date

> ![](https://files.readme.io/6949cfa-card_token_1_im.png)*Decoding Token from Base64*
>
> ![](https://files.readme.io/3f7ba73-output_bin_lookup_-_card_token.png)*Output of Decode*