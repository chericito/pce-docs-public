---
title: Direct Sale (Immediate Capture)
excerpt: >-
  Process and settle payments instantly with a single API call—ideal for
  immediate-order fulfillment.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The Direct Sale (Immediate Capture) method authorizes and captures funds in one step, delivering fast, straightforward payment processing for merchants fulfilling orders right away—such as digital goods, event tickets, or in-stock products.

### Prerequisites

* Active merchant account with card processing enabled
* PCI DSS Level 1 compliance
* Network permissions for enhanced data (L1, L2 & L3) when collecting detailed line-item information

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

# Direct Sale (Immediate Capture)

A “Direct Sale” or “Sale” transaction combines authorization and capture into a single step. This method is best when you need to charge the customer’s card and begin transferring funds as soon as the transaction is approved.

Use this method when you want a fast, one-step payment flow that immediately settles funds into your account.

1. Customer submits payment details.
2. Merchant server sends one `CREATE_TRANSACTION` API request to PCE, including amount, payment data, and optional L2/L3 fields.
3. PCE contacts card networks to authorize and immediately capture funds.
4. PCE returns a synchronous response indicating success or failure.

# Payloads

> 📘 POST /v1/transaction HTTP/1.1 &#x20;
> Host: \<hostname>
> Authorization: Bearer
> Content-Type: application/json

## From Third-party to PCE Account - One-Time Transaction

```json
{
    "amountDetails": {
        "tipAmount": "9.00",
        "surchargeAmount": "4.05",
        "originalAmount": "135.11"
    },
    "method": "CARD",
    "purpose": "AnPCP",
    "isAutoCapture": true,
    "funding": {
        "tags": {
            "type": "Trust"
        }
    },	
    "source": {
        "card": {
            "form": "Plastic",
            "holderName": "test",
            "cardNumber": "5555555555554444",
            "expiryMonth": "3",
            "expiryYear": "2027",
            "cvv": "837",
            "accountType": "SAVINGS",
            "avs": {
                "zip": "27492",
                "addressLine1": "HIGHSTREET",
                "firstName": "tarun",
                "middleName": "s",
                "lastName": "chopra",
                "phone": "678-472-5829",
                "email": "fbjibf@gmail.com"
            },
            "cardHolder": {
                "name": "johnmark",
                "firstName": "john",
                "lastName": "mark",
                "ipAddress": "10MM0006",
                "hostName": "testdemoorg",
                "browserType": "chrometest",
                "phone": "987-654-3210",
                "email": "pps@io.com",
                "number": "9876543"
            },
            "billingAddress": {
                "addressLine1": "Street53",
                "city": "Alpharetta",
                "state": "GA",
                "zip": "30004",
                "country": "USA"
            }
        }
    },
    "type": "REGULAR",
    "processingDetail": {
        "statementDescriptor": "descriptor card",
        "businessApplication": "Consumerbillpayment",
        "device": {
            "posId": "ps9220",
            "type": "mobile",
            "accountCaptureMethod": "Manual",
            "cardPresent": "false",
            "cardholderPresence": "Present",
            "attendance": "Attended",
            "location": "Server",
            "catLevel": "None",
            "transactionSecurity": "Normal",
            "transactionStatus": "Normal",
            "partialApprovalSupport": "Supported"
        },
        "merchant": {
            "id": 4005163
        },
        "order": {
            "invoice": {
                "number": "601104043838334",
                "discountRate": "0.05",
                "discountAmount": "10",
                "taxAmount": "15",
                "taxRate": "0.08",
                "taxExempt": "false",
                "shipmentDetail": {
                    "freightTaxRate": "0.05",
                    "destinationPostalCode": "12345",
                    "sourcePostalCode": "67890",
                    "dutyAmount": "5",
                    "freightAmount": "20",
                    "freightTaxAmount": "1",
                    "address": {
                        "country": "USA",
                        "addressLine1": "123MainSt",
                        "addressLine2": "Apt101",
                        "city": "New York",
                        "state": "NY",
                        "zip": "10001"
                    }
                },
                "lineItem": [
                    {
                        "commodityCode": "ABCD1234567890",
                        "description": "ProductA",
                        "productCode": "PRODA",
                        "unitOfMeasure": "pcs",
                        "quantity": "5",
                        "unitCost": "10",
                        "discountRate": "0.1",
                        "discountAmount": "5",
                        "taxRate": "0.08",
                        "taxAmount": "4",
                        "dutyAmount": "0.5",
                        "extendedAmount": "45"
                    },
                    {
                        "commodityCode": "EFGH9876543210",
                        "description": "ProductB",
                        "productCode": "PRODB",
                        "unitOfMeasure": "pcs",
                        "quantity": "10",
                        "unitCost": "15",
                        "discountRate": "0.05",
                        "discountAmount": "7.5",
                        "taxRate": "0.08",
                        "taxAmount": "9.6",
                        "dutyAmount": "1",
                        "extendedAmount": "142.5"
                    }
                ]
            },
            "lodging": {
                "purchaseId": "580",
                "folio": "fn304",
                "customerPhone": "490-337-5094",
                "recordCharge": "ho58",
                "propertyPhone": "837-459-0902",
                "programCode": "7",
                "rooms": [
                    {
                        "checkin": "03/31/2024",
                        "checkout": "03/31/2024",
                        "amount": "67.2",
                        "duration": "7"
                    },
                    {
                        "checkin": "03/31/2024",
                        "checkout": "03/31/2024",
                        "amount": "7.3",
                        "duration": "3"
                    }
                ]
            }
        }
    }
}

```

## From Third-party to PCE Account - Mapping card details into a TOKEN

```json
{

    "type": "REGULAR",
    "method": "CARD",
    "processingDetail": {
        "merchant": {
            "id": 4001995
        },
        "statementDescriptor": "services"
    },
    "source": {
        "card": {
            "token": "eyJjYXJkVHlwZSI6IlVOS05PV04iLCJ0b2tlbkV="
        }
    },
    "destination": {
        "account": {
            "id": "4000407"
        }
    },
    "amount": "30.50",
    "purpose": "Collect funds"

}
```

## From Contact to PCE Account

```json

{
    "method": "CARD",
    "type": "REGULAR",
    "amount": "31",
    "allowDuplicate": "true",
    "purpose": "services",
    "source": {
        "contact": {
            "id": 925,
            "card": {
                "id": 1897,
                "cvv": 323
            }
        }
    },
    "destination": {
        "account": {
            "id": 4019941
        }
    },
    "processingDetail": {
        "merchant": {
            "id": 4001309
        },
        "statementDescriptor": "services"
    }
}


```

## From Third-Party to PCE Account - Pre-existing Entity

```json

{
    "externalId": "EID188118842194616366200",
    "amount": "100.00",
    "allowDuplicate": "true",
    "method": "CARD",
    "type": "Regular",
    "purpose": "Fee",
    "source": {
        "card": {
            "id": "529"
        }
    },
    "destination": {
        "account": {
            "id": "4000407"
        }
    },
    "processingDetail": {
        "merchant": {
            "id": 4001995
        },
        "location": {
                    "id": 2062
                },
        "statementDescriptor": "services"
    },
    "comment": "Deposit created"
}

```

## Adhoc Refund - Without Sale Transaction

```json

{
    "type": "REFUND",
    "reason": "RETAIN_CUSTOMER",
    "amount": "12.00",
    "method": "CARD",
    "processingDetail": {
        "merchant": {
            "id": "4005163"
        }
    },
    "purpose": "test transaction collect",
    "destination": {
        "card": {
            "holderName": "test",
            "cardNumber": "378282246310005",
            "expiryMonth": "3",
            "expiryYear": "2029",
            "cvv": "8378",
            "billingAddress": {
                "addressLine1": "Street53",
                "city": "Alpharetta",
                "state": "GA",
                "zip": "30004",
                "country": "USA"
            }
        }
    }
}


```

## Sale Terminal Transaction with Amount

```json
{
    "type": "REGULAR",
    "amount": "25.02",
    "method": "CARD",
    "processingDetail": {
        "merchant": {
            "id": "4007497"
        },
        "terminal": {
            "id": "DA08333B-CBA7-440A-943D-49813C51C793"
        }
    },
    "purpose": "Terminal Work Purpose",
    "isAutoCapture": true
}
```

## Sale Terminal Transaction with Original Amount

```json
{
    "type": "REGULAR",
    "method": "CARD",
    "processingDetail": {
        "merchant": {
            "id": "4000759"
        },
        "terminal": {
            "id": "D3203595-E861-4F65-8EE8-AE6C95A2B47B"
        }
    },
    "amountDetails": {
        "originalAmount": "100"
    },
    "isAutoCapture": "true",
    "purpose": "test ekam"
}
```