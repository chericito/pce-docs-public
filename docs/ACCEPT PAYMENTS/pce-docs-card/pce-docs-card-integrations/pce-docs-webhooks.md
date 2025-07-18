---
title: "Webhooks"
slug: "pce-docs-webhooks"
excerpt: "Receive real-time notifications for critical system events by subscribing to PCE webhooks—set up your endpoints, confirm subscriptions, and handle signed payloads reliably."
hidden: false
parentDoc: "PARENTDOC_ID"
category: "CATEGORY_ID"
updatedAt: "UPDATED_AT_KEY"
order: 1
---

# Overview

Learn how to configure and manage webhook subscriptions in PCE, confirm your endpoint, and process incoming event notifications.

**In this guide you’ll learn**

* How to subscribe and confirm a webhook endpoint
* Best practices for authenticating and securing webhook messages
* How to parse and handle common PCE event payloads

### Prerequisites & Limitations

* PCE account with Program Manager portal access
* Publicly accessible HTTPS endpoint for receiving notifications
* Ability to validate AWS SNS signatures or your chosen delivery mechanism
* Endpoints must respond within 5 seconds to avoid retries

# Compliance / Regulation Mandates

* **TLS & Data Security:** Endpoints must use HTTPS (TLS 1.2+) and enforce strict cipher suites.
* **Signature Validation:** Verify each message signature to ensure authenticity (e.g. AWS SNS X-Amz-Sns-Signature).
* **Idempotency & Retry Handling:** Design handlers to safely ignore duplicate deliveries and handle retry semantics.

# Feature Table

| Feature               | Description                                                        |
| --------------------- | ------------------------------------------------------------------ |
| Webhook Subscriptions | Configure and confirm endpoints to receive PCE event notifications |
| Event Payloads        | Structured JSON payloads for resource lifecycle events             |

# Key Details

## Setup for Webhook Subscription

1. **Navigate** to the Webhooks section in the Program Manager portal.
2. **Enter** your HTTPS endpoint URL and create the subscription.
3. **Receive** a `SubscriptionConfirmation` message:

   ```json
   {
     "Type": "SubscriptionConfirmation",
     "MessageId": "e7caa54f-7380-42ff-bf41-1a847b5db5a9",
     "Token": "2336412f37fb687ff41a9668e",
     "TopicArn": "arn:aws:sns:us-east-1:9853074181:test-topic1",
     "Message": "You have chosen to subscribe…",
     "SubscribeURL": "https://sns.us-east-1.amazonaws.com/?Action=ConfirmSubscription…",
     "Timestamp": "2024-05-15T08:53:04.873Z",
     "SignatureVersion": "1",
     "Signature": "KwtRZ0gNGtk…",
     "SigningCertURL": "https://sns.us-east-1.amazonaws.com/SimpleNotificationService-…pem"
   }
   ```
4. **Confirm** by issuing an HTTP GET to the `SubscribeURL`.
5. **Authenticated Endpoints:**

   * First respond `401` with header `WWW-Authenticate: Basic`.
   * Then perform the GET to `SubscribeURL`.

6. **Subscription Active:** After confirmation, events will arrive at your endpoint within \~1 hour.

**Sample Node.js Handler**

```js
app.post('/sns-endpoint', authMiddleware, (req, res) => {
  const auth = req.headers.authorization;
  if (!auth) {
    res.setHeader('WWW-Authenticate', 'Basic');
    return res.status(401).send('Authentication required.');
  }
  const type = req.headers['x-amz-sns-message-type'];
  if (type === 'SubscriptionConfirmation') {
    const url = req.body.SubscribeURL;
    console.log(`Confirming subscription: ${url}`);
    // e.g., await axios.get(url);
  } else if (type === 'Notification') {
    console.log(`Received notification: ${req.body.Message}`);
  }
  res.sendStatus(200);
});
```

## Instant Webhook Events & Their Payload

<table>
<thead>
<tr>
<td width="284">
<p><strong>Event Name</strong></p>
</td>
<td width="375">
<p><strong>Payload</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td width="284">
<p><strong>customer.individual.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 15140,
    "eventType": "customer.individual.create",
    "eventTimeStamp": "05/13/2025 01:03:00",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "customer",
            "url": "/v1/customer/id/4009402",
            "id": 4009402,
            "tags": [
                "grade A customer"
            ],
            "externalId": "TSC0567890",
            "metaData": {
                "acceptedDraftAmount": "$333.50"
            },
            "type": "INDIVIDUAL",
            "individual": {
                "firstName": "John",
                "middleName": "K",
                "lastName": "Smith",
                "fullName": "John K Smith",
                "last4ssn": "9578",
                "dob": "06/25/2000",
                "homePhone": "573-986-1372",
                "mobilePhone": "235-247-4107",
                "workPhone": "838-900-9290",
                "mailingAddress": [
                    {
                        "resourceName": "address",
                        "url": "/v1/customer/id/4009402/mailingAddress/id/1033532",
                        "id": 1033532,
                        "externalId": "P94567A221",
                        "addressLine1": "999",
                        "addressLine2": "GT1 KMB",
                        "city": "San Jose",
                        "state": "CA",
                        "zip": "95311",
                        "isPrimary": true
                    }
                ],
                "verification": {
                    "ofacStatus": "PENDING_VERIFICATION",
                    "ofacStatusReason": "PENDING_VERIFICATION",
                    "ofacStatusDate": "12/03/2022 07:49:48",
                    "cipStatus": "IGNORED",
                    "cipStatusReason": "IGNORED ON_USER_REQUEST",
                    "cipStatusDate": "12/03/2022 07:49:48"
                },
                "createdOn": "12/03/2022 07:49:48",
                "lastUpdatedOn": "12/03/2022 07:49:48"
            },
            "isPaperless": false,
            "status": "ACTIVE",
            "statusReason": "ON_USER_REQUEST",
            "statusDate": "12/03/2022 07:49:48",
            "account": {
                "resourceName": "account",
                "url": "/v1/customer/id/4009402/account"
            },
            "externalAccount": {
                "resourceName": "externalAccount",
"url": "/v1/customer/id/4009402/externalAccount"
            },
            "linkedDocument": [
                {
                    "id": 24658,
                    "purpose": "AUTHORIZATION",
                    "status": "PENDING_VERIFICATION",
                    "document": {
                        "resourceName": "document",
                        "url": "/v1/document/id/4023765",
                        "id": 4023765,
                        "type": "SPAA",
                        "name": "abc.pdf"
                    },
                    "linkedOn": "12/03/2022 07:49:48",
                    "linkedBy": {
                        "userType": "API_USER",
                        "username": "FyPtDp@test.com",
                        "status": "ACTIVE"
                    }
                }
            ],
            "createdOn": "12/03/2022 07:49:48",
            "createdBy": {
                "userType": "API_USER",
                "username": "FyPtDp@test.com",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "12/03/2022 07:49:48",
            "lastUpdatedBy": {
                "userType": "API_USER",
                "username": "FyPtDp@test.com",
                "status": "ACTIVE"
            }
        }
    ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>customer.business.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 15140,
    "eventType": "customer.business.create",
    "eventTimeStamp": "05/13/2025 01:03:00",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,

    "payload": [
        {
            "resourceName": "customer",
            "url": "/v1/customer/id/4007317",
            "id": 4007317,
            "externalId": "PMAcceptance-Mar26",
            "type": "BUSINESS",
            "business": {
                "legalName": "AMEX",
                "ein": "22-2015690",
                "doingBusinessAs": "American Express",
                "phone": "213-233-1731",
                "email": "businesstest567@gmail.com",
                "website": "www.amex.com",
                "mailingAddress": [
                    {
                        "resourceName": "address",
                        "url": "/v1/customer/id/4007317/mailingAddress/id/1021541",
                        "id": 1021541,
                        "externalId": "PA09090991",
                        "addressLine1": "Ap 4891",
                        "addressLine2": "Conference Centre Ste 1020",
                        "city": "Sugar Notch",
                        "state": "PA",
                        "zip": "18706",
                        "isPrimary": true,
                        "usage": {
                            "isPayorAddress": false
                        }
                    }
                ],
                "verification": {
                    "ofacStatus": "PENDING_VERIFICATION",
                    "ofacStatusReason": "PENDING_VERIFICATION",
                    "ofacStatusDate": "03/26/2023 06:46:41",
                    "cipStatus": "IGNORED",
                    "cipStatusReason": "IGNORED ON_USER_REQUEST",
                    "cipStatusDate": "03/26/2023 06:46:41"
                },
                "stateOfIncorporation": "CA",
                "businessCategory": "LLC",
                "dateOfIncorporation": "12/20/2000",
                "beneficialOwner": [
                    {
                        "id": 7522,
                        "firstName": "Amelia",
                        "lastName": "Connor",
                        "fullName": "Amelia Connor",
                        "last4ssn": "2023",
                        "dob": "10/01/2000",
                        "homePhone": "530-986-1172",
                        "mobilePhone": "235-237-4107",
                        "workPhone": "838-900-9090",
                        "email": "botest56789@gmail.com",
                        "mailingAddress": [
                            {
                                "id": 1021542,
                                "externalId": "PC30945678911",
                                "addressLine1": "Ap 4391",
                                "addressLine2": "Conference Centre Ste 1020",
                                "city": "Sugar Notch",
                                "state": "PA",
                                "zip": "18706",
                                "isPrimary": true
                            }
                        ],
                        "verification": {
                            "ofacStatus": "PENDING_VERIFICATION",
                            "ofacStatusReason": "PENDING_VERIFICATION",
                            "ofacStatusDate": "03/26/2023 06:46:41",
                            "cipStatus": "PENDING_VERIFICATION",
                            "cipStatusReason": "PENDING_VERIFICATION",
                            "cipStatusDate": "03/26/2023 06:53:19"
                        },
                        "isUSCitizen": true,
                        "actAsAuthorizedSignatory": true,
                        "businessDetails": {
                            "ownershipPercentage": 50.0,
                            "title": "Secretary"
                        },
                        "secondaryIdentification": {
                            "lastFourId": "2905",
                            "id": "48832905",
                            "type": "DRIVER_LICENSE",
                            "stateOfIssuance": "CA"
                        },
                        "pullCreditReport": false
                    }
                ]
            },
            "isPaperless": true,
            "status": "ACTIVE",
            "statusReason": "ON_USER_REQUEST",
            "statusDate": "03/26/2023 06:46:41",
            "account": {
                "resourceName": "account",
                "url": "/v1/customer/id/4007317/account"
            },
            "externalAccount": {
                "resourceName": "externalAccount",
                "url": "/v1/customer/id/4007317/externalAccount"
            },
            "card": {
                "resourceName": "card",
                "url": "/v1/customer/id/4007317/card"
            },
            "merchant": {
                "resourceName": "merchant",
                "url": "/v1/customer/id/4007317/merchant"
            },
            "createdOn": "03/26/2023 06:46:41",
            "createdBy": {
                "userType": "API_USER",
                "username": "passportqa+420938505985@prth.com",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "03/26/2023 06:46:41",
            "lastUpdatedBy": {
                "userType": "API_USER",
                "username": "passportqa+420938505985@prth.com",
                "status": "ACTIVE"
            }
        }
    ]
}


```

</td>
</tr>

<tr>
<td width="284">
<p><strong>customer.jointTendancy.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}

{
    "id": 15140,
    "eventType": "customer.jointtenancy.create",
    "eventTimeStamp": "05/13/2025 01:03:00",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "customer",
            "url": "/v1/customer/id/4006644",
            "id": 4006644,
            "type": "JOINT_TENANCY",
            "isPaperless": true,
            "status": "ACTIVE",
            "statusReason": "ON_USER_REQUEST",
            "statusDate": "05/01/2024 09:55:57",
            "account": {
                "resourceName": "account",
                "url": "/v1/customer/id/4006644/account"
            },
            "externalAccount": {
                "resourceName": "externalAccount",
                "url": "/v1/customer/id/4006644/externalAccount"
            },
            "card": {
                "resourceName": "card",
                "url": "/v1/customer/id/4006644/card"
            },
            "ppi": {
                "resourceName": "ppi",
                "ppi": "aditya.dhawan@ppi",
                "url": "/v1/customer/id/4006644/ppi"
            },
            "createdOn": "05/01/2024 09:55:57",
            "createdBy": {
                "userType": "API_USER",
                "username": "passportqa+aDePqJ@prth.com",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "05/01/2024 10:34:43",
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "portalAccess": {
                "grantAccess": true,
                "username": "aditya.dhawan@prth.com",
                "role": [
                    {
                        "resourceName": "role",
                        "url": "/v1/customer/id/4006644/role",
                        "id": 5991
                    }
                ]
            },
            "owners": [
                {
                    "id": 18528,
                    "isPrimaryOwner": true,
                    "firstName": "Aryan",
                    "lastName": "Sharma",
                    "fullName": "Aryan Sharma",
                    "last4ssn": "8292",
                    "dob": "02/07/1935",
                    "mobilePhone": "869-995-2968",
"email": "aditya.dhawan@prth.com",
                    "mailingAddress": [
                        {
                            "resourceName": "address",
                            "id": 1021289,
                            "addressLine1": "house no 8989",
                            "city": "Newyork",
                            "state": "HI",
                            "zip": "10001",
                            "isPrimary": true,
                            "usage": {
                                "isPayorAddress": false
                            }
                        }
                    ],
                    "verification": {
                        "ofacStatus": "IGNORED",
                        "ofacStatusReason": "IGNORED ON_USER_REQUEST",
                        "ofacStatusDate": "05/01/2024 09:54:31",
                        "cipStatus": "VERIFIED",
                        "cipStatusReason": "Verified",
                        "cipStatusDate": "05/01/2024 12:36:18"
                    },
                    "portalAccess": {
                        "grantAccess": true,
                        "username": "aditya.dhawan@prth.com"
                    },
                    "createdOn": "05/01/2024 09:55:57",
                    "lastUpdatedOn": "05/01/2024 09:55:57",
                    "userId": 4008293
                },
                {
                    "id": 18529,
                    "isPrimaryOwner": false,
                    "firstName": "Himanshu",
                    "middleName": "",
                    "lastName": "Invitation Joint Tenancy",
                    "fullName": "Himanshu Invitation Joint Tenancy",
                    "last4ssn": "6345",
                    "dob": "02/07/1935",
                    "mobilePhone": "142-124-5465",
                    "email": "aditya.dhawan+101010@prth.com",
                    "mailingAddress": [
                        {
                            "resourceName": "address",
                            "id": 1021285,
                            "addressLine1": "6789",
                            "addressLine2": "",
                            "city": "califronia",
                            "state": "CA",
                            "zip": "45678",
                            "isPrimary": true,
                            "usage": {
                                "isPayorAddress": false
                            }
                        }
                    ],
                    "verification": {
                        "ofacStatus": "IGNORED",
"ofacStatusReason": "IGNORED ON_USER_REQUEST",
                        "ofacStatusDate": "05/01/2024 09:54:31",
                        "cipStatus": "VERIFIED",
                        "cipStatusReason": "Verified",
                        "cipStatusDate": "05/01/2024 10:34:43"
                    },
                    "portalAccess": {
                        "grantAccess": false
                    },
                    "createdOn": "05/01/2024 09:55:57",
                    "lastUpdatedOn": "05/01/2024 09:55:57"
                }
            ],
            "verification": {
                "ofacStatus": "IGNORED",
                "ofacStatusReason": "IGNORED ON_USER_REQUEST",
                "ofacStatusDate": "05/01/2024 09:54:31",
                "cipStatus": "VERIFIED",
                "cipStatusReason": "Verified",
                "cipStatusDate": "05/01/2024 12:36:18"
            }
        }
    ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>customer.business.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 15140,
    "eventType": "customer.business.update",
    "eventTimeStamp": "05/13/2025 01:03:00",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "customer",
            "url": "/v1/customer/id/4007317",
            "id": 4007317,
            "externalId": "PMAcceptance-Mar26",
            "type": "BUSINESS",
            "business": {
                "legalName": "AMEX",
                "ein": "22-2015690",
                "doingBusinessAs": "American Express",
                "phone": "213-233-1731",
                "email": "businesstest567@gmail.com",
                "website": "www.amex.com",
                "mailingAddress": [
                    {
                        "resourceName": "address",
                        "url": "/v1/customer/id/4007317/mailingAddress/id/1021541",
                        "id": 1021541,
                        "externalId": "PA09090991",
                        "addressLine1": "Ap 4891",
                        "addressLine2": "Conference Centre Ste 1020",
                        "city": "Sugar Notch",
                        "state": "PA",
                        "zip": "18706",
                        "isPrimary": true,
                        "usage": {
                            "isPayorAddress": false
                        }
                    }
                ],
                "verification": {
                    "ofacStatus": "PENDING_VERIFICATION",
                    "ofacStatusReason": "PENDING_VERIFICATION",
                    "ofacStatusDate": "03/26/2023 06:46:41",
                    "cipStatus": "IGNORED",
                    "cipStatusReason": "IGNORED ON_USER_REQUEST",
                    "cipStatusDate": "03/26/2023 06:46:41"
                },
                "stateOfIncorporation": "CA",
                "businessCategory": "LLC",
                "dateOfIncorporation": "12/20/2000",
                "beneficialOwner": [
                    {
                        "id": 7522,
                        "firstName": "Amelia",
                        "lastName": "Connor",
                        "fullName": "Amelia Connor",
                        "last4ssn": "2023",
                        "dob": "10/01/2000",
                        "homePhone": "530-986-1172",
                        "mobilePhone": "235-237-4107",
                        "workPhone": "838-900-9090",
                        "email": "botest56789@gmail.com",
                        "mailingAddress": [
                            {
                                "id": 1021542,
"externalId": "PC30945678911",
                                "addressLine1": "Ap 4391",
                                "addressLine2": "Conference Centre Ste 1020",
                                "city": "Sugar Notch",
                                "state": "PA",
                                "zip": "18706",
                                "isPrimary": true
                            }
                        ],
                        "verification": {
                            "ofacStatus": "PENDING_VERIFICATION",
                            "ofacStatusReason": "PENDING_VERIFICATION",
                            "ofacStatusDate": "03/26/2023 06:46:41",
                            "cipStatus": "PENDING_VERIFICATION",
                            "cipStatusReason": "PENDING_VERIFICATION",
                            "cipStatusDate": "03/26/2023 06:53:19"
                        },
                        "isUSCitizen": true,
                        "actAsAuthorizedSignatory": true,
                        "businessDetails": {
                            "ownershipPercentage": 50.0,
                            "title": "Secretary"
                        },
                        "secondaryIdentification": {
                            "lastFourId": "2905",
                            "id": "48832905",
                            "type": "DRIVER_LICENSE",
                            "stateOfIssuance": "CA"
                        },
                        "pullCreditReport": false
                    }
                ]
            },
            "isPaperless": true,
            "status": "ACTIVE",
            "statusReason": "ON_USER_REQUEST",
            "statusDate": "03/26/2023 06:46:41",
            "account": {
                "resourceName": "account",
                "url": "/v1/customer/id/4007317/account"
            },
            "externalAccount": {
                "resourceName": "externalAccount",
                "url": "/v1/customer/id/4007317/externalAccount"
            },
            "card": {
                "resourceName": "card",
                "url": "/v1/customer/id/4007317/card"
            },
            "merchant": {
                "resourceName": "merchant",
                "url": "/v1/customer/id/4007317/merchant"
            },
            "createdOn": "03/26/2023 06:46:41",
            "createdBy": {
                "userType": "API_USER",
                "username": "passportqa+420938505985@prth.com",
"status": "ACTIVE"
            },
            "lastUpdatedOn": "03/26/2023 06:46:41",
            "lastUpdatedBy": {
                "userType": "API_USER",
                "username": "passportqa+420938505985@prth.com",
                "status": "ACTIVE"
            }
        }
    ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>customer.individual.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 3013,
    "eventType": "customer.individual.update",
    "eventTimeStamp": "06/10/2024 19:08:33",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "customer",
            "url": "/v1/customer/id/4048848",
            "id": 4048848,
            "type": "INDIVIDUAL",
            "individual": {
                "firstName": "Jon",
                "lastName": "Williams",
                "mobilePhone": "123-456-7890",
                "countryCode": "91",
                "fullName": "Jon Smith Williams",
                "lastUpdatedOn": "06/10/2024 19:08:33",
                "middleName": "Smith",
                "createdOn": "05/30/2024 08:39:47",
                "email": "passportqa+76564168576255988299@prth.com",
                "verification": {
                    "ofacStatus": "IGNORED",
                    "cipStatus": "UNVERIFIED",
                    "cipStatusDate": "05/30/2024 08:39:47",
                    "cipStatusReason": "UNVERIFIED",
                    "ofacStatusDate": "06/10/2024 19:08:33",
                    "ofacStatusReason": "IGNORED ON_USER_REQUEST"
                }
            },
            "portalAccess": {
                "role": [
                    {
                        "resourceName": "role",
                        "id": 14305,
                        "url": "/v1/customer/id/4048848/role"
                    }
                ],
                "grantAccess": true,
                "username": "passportqa+76564168576255988299@prth.com"
            },
            "statusReason": "ON_USER_REQUEST",
            "isPaperless": false,
            "statusDate": "05/30/2024 08:39:47",
            "externalAccount": {
                "resourceName": "externalAccount",
                "url": "/v1/customer/id/4048848/externalAccount"
            },
            "account": {
                "resourceName": "account",
                "url": "/v1/customer/id/4048848/account"
            },
            "card": {
                "resourceName": "card",
                "url": "/v1/customer/id/4048848/card"
            },
            "status": "ACTIVE",
            "createdBy": {
                "userType": "API_USER",
                "username": "DCMRQQ@test.com",
                "status": "ACTIVE"
},
            "createdOn": "05/30/2024 08:39:47",
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "06/10/2024 19:08:33"
        }
    ]
}

```

</td>
</tr>

<tr>
<td width="284">
<p><strong>customer.jointtenancy.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 3019,
    "eventType": "customer.jointtenancy.update",
    "eventTimeStamp": "06/10/2024 19:18:12",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "customer",
            "url": "/v1/customer/id/4048556",
            "id": 4048556,            
            "statusDate": "05/09/2024 07:59:20",
            "portalAccess": {
                "grantAccess": false
            },
            "externalId": "CustJ12",
            "owners": [
                {
                    "lastName": "Smith",
                    "lastUpdatedBy": {
                        "userType": "INTERNAL",
                        "username": "DEFAULT_USER",
                        "status": "ACTIVE"
                    },
                    "last4ssn": "4344",
                    "homePhone": "131-312-4444",
                    "portalAccess": {
                        "grantAccess": false
                    },
                    "externalId": "Ownerj2ext",
                    "fullName": "Kewin Smith",
                    "createdOn": "05/09/2024 07:59:20",
                    "isPrimaryOwner": true,
                    "firstName": "Kewin",
                    "linkedDocument": [
                        {
                            "purpose": "IDENTIFICATION_PROOF",
                            "linkedBy": {
                                "userType": "INTERNAL",
                                "username": "DEFAULT_USER",
                                "status": "ACTIVE"
                            },
                            "document": {
                                "name": "images (1) (1).jpg",
                                "resourceName": "document",
                                "id": 4117906,
                                "type": "PASSPORT",
                                "url": "/v1/document/id/4117906"
                            },
                            "id": 132848,
                            "linkedOn": "Thu May 09 07:59:20 UTC 2024",
                            "status": "PENDING_VERIFICATION"
                        }
                    ],
                    "mailingAddress": [
                        {
                            "zip": "12313",
                            "city": "new",
                            "isPrimary": true,
                            "usage": {
                                "isPayorAddress": false
                            },
                            "addressLine1": "test",
                            "resourceName": "address",
                            "id": 1205304,
                            "state": "AL"
                        }
                    ],
                    "createdBy": {
                        "userType": "INTERNAL",
                        "username": "DEFAULT_USER",
                        "status": "ACTIVE"
                    },
                    "dob": "05/12/1937",
                    "secondaryIdentification": {
                        "stateOfIssuance": "AK",
                        "id": "13134312432",
                        "type": "DRIVER_LICENSE"
                    },
                    "lastUpdatedOn": "05/09/2024 07:59:20",
                    "id": 113569,
                    "email": "ctr.abcdd+233@prth.com",
                    "verification": {
                        "ofacStatus": "IGNORED",
                        "cipStatus": "UNVERIFIED",
                        "cipStatusDate": "06/10/2024 19:18:11",
                        "cipStatusReason": "UNVERIFIED",
                        "ofacStatusDate": "06/10/2024 19:18:11",
                        "ofacStatusReason": "IGNORED ON_USER_REQUEST"
                    }
                }
            ],
            "type": "JOINT_TENANCY",
            "createdOn": "05/09/2024 07:59:20",
            "statusReason": "ON_USER_REQUEST",
            "createdBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "isPaperless": false,
            "externalAccount": {
                "resourceName": "externalAccount",
                "url": "/v1/customer/id/4048556/externalAccount"
            },
            "lastUpdatedOn": "06/10/2024 19:18:11",
            "programAffiliate": {
                "name": "ANSHULPARTNER",
                "id": 1296
            },
            "account": {
                "resourceName": "account",
                "url": "/v1/customer/id/4048556/account"
            },
            "card": {
                "resourceName": "card",
                "url": "/v1/customer/id/4048556/card"
            },
            "verification": {
                "ofacStatus": "IGNORED",
                "cipStatus": "UNVERIFIED",
                "cipStatusDate": "06/10/2024 19:18:11",
                "cipStatusReason": "UNVERIFIED",
                "ofacStatusDate": "06/10/2024 19:18:11",
                "ofacStatusReason": "IGNORED ON_USER_REQUEST"
            },
            "status": "ACTIVE"
        }
    ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>account.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 15140,
    "eventType": "account.create",
    "eventTimeStamp": "06/10/2024 19:08:33",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "account",
            "url": "v1/customer/id/4007825/account/id/4003513",
            "id": 4003513,
            "externalId": "E22343422234125678654",
            "nickName": "Jhon",
            "accountNumber": "8125001200000346",
            "status": "INACTIVE",
            "statusReason": "PENDING_VERIFICATION",
            "statusDate": "06/08/2023 06:11:10",
            "balance": {
                "amount": "0.00",
                "asOn": "06/08/2023 06:11:26"
            },
            "availableBalance": {
                "amount": "0.00",
                "asOn": "06/08/2023 06:11:26"
            },
            "purpose": "FEE",
            "routableAccount": {
                "accountNumber": "76650000004347",
                "routingNumber": "053101561",
                "wireRoutingNumber": "122287251",
                "wireAccountNumber": "13976650000004347",
                "wireMemo": "Alex Johnson 13976650000004347",
                "memo": "Alex Johnson 76650000004347"
            },
            "linkedDocument": [
                {
                    "id": 15339,
                    "purpose": "AUTHORIZATION",
                    "status": "PENDING_VERIFICATION",
                    "document": {
                        "resourceName": "document",
                        "url": "/v1/document/id/4014696",
                        "id": 4014696,
                        "type": "SPAA",
                        "name": "spaa-blank.pdf"
                    },
                    "linkedOn": "06/08/2023 06:09:06",
                    "linkedBy": {
                        "userType": "API_USER",
                        "username": "passportqa+374732976396@prth.com",
                        "status": "ACTIVE"
                    }
                }
            ],
            "createdOn": "06/08/2023 06:09:05",
            "createdBy": {
                "userType": "API_USER",
                "username": "passportqa+374732976396@prth.com",
                "status": "ACTIVE"
            },
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "06/08/2023 06:11:10",
            "isCustomerOwned": true,
            "activationDate": "09/14/2023 06:09:46",
            "isPrimary": false,
            "totalCredit": {
                "amount": "0.00",
                "asOn": "03/13/2024 05:23:47"
            },
            "totalDebit": {
                "amount": "0.00",
                "asOn": "03/13/2024 05:23:47"
            }
        }
    ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>account.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 15140,
    "eventType": "account.update",
    "eventTimeStamp": "06/10/2024 19:08:33",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "account",
            "url": "v1/customer/id/4007825/account/id/4003513",
            "id": 4003513,
            "externalId": "E22343422234125678654",
            "nickName": "Jhon",
            "accountNumber": "8125001200000346",
            "status": "INACTIVE",
            "statusReason": "PENDING_VERIFICATION",
            "statusDate": "06/08/2023 06:11:10",
            "balance": {
                "amount": "0.00",
                "asOn": "06/08/2023 06:11:26"
            },
            "availableBalance": {
                "amount": "0.00",
                "asOn": "06/08/2023 06:11:26"
            },
            "purpose": "FEE",
            "routableAccount": {
                "accountNumber": "76650000004347",
                "routingNumber": "053101561",
                "wireRoutingNumber": "122287251",
                "wireAccountNumber": "13976650000004347",
                "wireMemo": "Alex Johnson 13976650000004347",
                "memo": "Alex Johnson 76650000004347"
            },
            "linkedDocument": [
                {
                    "id": 15339,
                    "purpose": "AUTHORIZATION",
                    "status": "PENDING_VERIFICATION",
                    "document": {
                        "resourceName": "document",
                        "url": "/v1/document/id/4014696",
                        "id": 4014696,
                        "type": "SPAA",
                        "name": "spaa-blank.pdf"
                    },
                    "linkedOn": "06/08/2023 06:09:06",
                    "linkedBy": {
                        "userType": "API_USER",
                        "username": "passportqa+374732976396@prth.com",
                        "status": "ACTIVE"
                    }
                }
            ],
            "createdOn": "06/08/2023 06:09:05",
            "createdBy": {
                "userType": "API_USER",
                "username": "passportqa+374732976396@prth.com",
                "status": "ACTIVE"
            },
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
},
            "lastUpdatedOn": "06/08/2023 06:11:10",
            "isCustomerOwned": true,
            "activationDate": "09/14/2023 06:09:46",
            "isPrimary": false,
            "totalCredit": {
                "amount": "0.00",
                "asOn": "03/13/2024 05:23:47"
            },
            "totalDebit": {
                "amount": "0.00",
                "asOn": "03/13/2024 05:23:47"
            }
        }
    ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>externalaccount.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 66031067,
   "eventType": "externalaccount.create",
    "eventTimeStamp": "06/10/2024 19:08:33",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "externalAccount",
           "url": "/v1/customer/id/4227120/externalAccount/id/4020708",
           "id": 4020708,
           "externalId": "3454354376",
           "holderName": "Ujjwal Patel",
           "holderPhone": "870-736-2752",
           "holderAddress": {
               "zip": "52142",
               "city": "San diego",
               "addressLine1": "3653",
               "addressLine2": "Kingston",
               "state": "NE"
           },
           "accountNumberLast4": "6488",
           "encryptedAccountNumber": "LlvcjlqdXZ6ShVjQu+EEsQ==",
           "routingNumber": "021210002",
           "purpose": "Fee External Account",
           "type": "SAVINGS",
           "statusDate": "07/19/2024 07:26:41",
           "statusReason": "External Account Pending Verification",
           "verification": {
               "ofacStatus": "PENDING_VERIFICATION",
               "ofacStatusDate": "07/19/2024 07:26:41",
               "ofacStatusReason": "Pending Verification"
           },
           "bankInfo": {
               "routingNumber": "021210002",
               "address": "1460 VALLEY RD,WAYNE,NJ,07470",
               "contactNumber": " ",
               "name": "VALLEY NATIONAL BANK"
           },
           "validateAccount": [
               {
                   "ews": {
                       "statusDate": "07/19/2024 07:26:41",
                       "statusReason": "PENDING",
                       "status": "PENDING"
                   }
               }
           ],
           "microDeposit": {
               "microDepositValidation": "NEVER"
           },
           "prenote": {
               "prenoteValidation": "NEVER"
           },
           "createdBy": {
               "userType": "INTERNAL",
               "username": "DEFAULT_USER",
               "status": "ACTIVE"
           },
           "createdOn": "07/19/2024 07:26:41",
           "lastUpdatedOn": "07/19/2024 07:26:41",
           "lastUpdatedBy": {
               "userType": "INTERNAL",
               "username": "DEFAULT_USER",
               "status": "ACTIVE"
           },
           "holderType": "CORPORATE",
           "status": "INACTIVE"
       }
   ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>externalaccount.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 66031073,
   "eventType": "externalaccount.update",
   "eventTimeStamp": "06/10/2024 19:08:33",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "externalAccount",
           "url": "/v1/customer/id/4227120/externalAccount/id/4020708",
           "id": 4020708,
           "externalId": "3454354376",
           "holderName": "Ujjwal Patel",
           "holderPhone": "870-736-2752",
           "holderAddress": {
               "zip": "52142",
               "city": "San diego",
               "addressLine1": "3653",
               "addressLine2": "Kingston",
               "state": "NE"
           },
           "accountNumberLast4": "6488",
           "purpose": "Fee External Account",
           "type": "SAVINGS",
           "statusReason": "External Account Pending Verification",
           "verification": {
               "ofacStatus": "VERIFIED",
               "ofacStatusDate": "07/19/2024 07:26:43",
               "ofacStatusReason": "Verified"
           },
           "bankInfo": {
               "routingNumber": "021210002",
               "address": "1460 VALLEY RD,WAYNE,NJ,07470",
               "contactNumber": " ",
               "name": "VALLEY NATIONAL BANK"
           },
           "validateAccount": [
               {
                   "ews": {
                       "statusDate": "07/19/2024 07:26:41",
                       "statusReason": "PENDING",
                       "status": "PENDING"
                   }
               }
           ],
           "microDeposit": {
               "microDepositValidation": "NEVER"
           },
           "prenote": {
               "prenoteValidation": "NEVER"
           },
           "encryptedAccountNumber": "LlvcjlqdXZ6ShVjQu+EEsQ==",
           "routingNumber": "021210002",
           "holderType": "CORPORATE",
           "statusDate": "07/19/2024 07:26:41",
           "status": "PENDING_VERIFICATION",
           "createdBy": {
               "userType": "INTERNAL",
               "username": "DEFAULT_USER",
               "status": "ACTIVE"
           },
           "createdOn": "07/19/2024 07:26:41",
           "lastUpdatedBy": {
               "userType": "SYSTEM",
               "username": "SYSTEM",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "07/19/2024 07:26:43"
       }
   ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>internationalexternalaccount.create</strong></p>
</td>
<td width="375">

- **For USD International External Account**

```json Example Request - {Payload}

{
   "id": 65819061,
   "eventType": "internationalexternalaccount.create",
   "eventTimeStamp": "06/21/2024 06:32:54",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "url": "/v1/customer/id/4225975/internationalExternalAccount/id/4019518",
           "id": 4019518,
           "statusDate": "06/21/2024 06:32:54",
           "holderName": "Ujjwal patel",
           "purpose": "FEE",
           "swiftCode": "USBKUS44IMT",
           "holderAddress": {
               "zip": "33126",
               "country": "AF",
               "city": "Miami",
               "addressLine1": "5505 Blue Lagoon Dr",
               "addressLine2": "Main St",
               "state": "NY"
           },
           "type": "CHECKING",
           "createdOn": "06/21/2024 06:32:54",
           "acceptedCurrency": [
               "USD"
           ],
           "statusReason": "External Account Pending Verification",
           "accountNumberLast4": "3232",
           "createdBy": {
               "userType": "CUSTOMER",
               "userName": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "userName": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 06:32:54",
           "holderType": "CORPORATE",
           "verification": {
               "ofacStatus": "PENDING_VERIFICATION",
               "ofacStatusDate": "06/21/2024 06:32:54",
               "ofacStatusReason": "Pending Verification"
           },
           "status": "INACTIVE"
       }
   ]
}
```

- **For non- USD International External Account**

```json Example Request - {Payload}
{
    "id": 67856626,
    "eventType": "internationalexternalaccount.create",
    "eventTimeStamp": "06/12/2025 06:04:10",
    "eventCreated": 1749708250797,
    "eventId": "0198840000000785690001",
    "payload": [
        {
            "url": "/v1/customer/id/4258731/internationalExternalAccount/id/4063258",
            "id": 4063258,
            "statusDate": "06/12/2025 06:04:09",
            "holderName": "Testing",
            "holderEmail": "abcd4175@gmail.com",
            "purpose": "Testing1",
            "externalId": "ET2082237231121",
            "holderPhone": "812236216",
            "swiftCode": "BKCHCNBJXXX",
            "holderAddress": {
                "zip": "T9X",
                "country": "CN",
                "city": "Albert",
                "addressLine1": "#1223, hazel street",
                "addressLine2": "Temple",
                "state": "CN"
            },
            "type": "CHECKING",
            "additionalDetail": {
                "taxID": "2815"
            },
            "acceptedCurrency": [
                "CNY"
            ],
            "statusReason": "External Account Pending Verification",
            "accountNumberLast4": "4512",
            "internationalRoutingCode": "92345",
            "holderType": "CORPORATE",
            "verification": {
                "ofacStatus": "PENDING_VERIFICATION",
                "ofacStatusDate": "06/12/2025 06:04:09",
                "ofacStatusReason": "Pending Verification"
            },
            "status": "INACTIVE",
            "lastUpdatedBy": {
                "userType": "API_USER",
                "userName": "nikhil.thakur+39340430393@prth.com",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "06/12/2025 06:04:09",
            "createdOn": "06/12/2025 06:04:09",
            "createdBy": {
                "userType": "API_USER",
                "userName": "nikhil.thakur+39340430393@prth.com",
                "status": "ACTIVE"
            }
        }
    ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>internationalexternalaccount.update</strong></p>
</td>
<td width="375">

- **For USD International External Account**

```json Example Request - {Payload}
{
   "id": 65819070,
   "eventType": "internationalexternalaccount.update",
   "eventTimeStamp": "06/10/2024 19:08:33",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "url": "/v1/customer/id/4225975/internationalExternalAccount/id/4019518",
           "id": 4019518,
           "statusDate": "06/21/2024 06:32:54",
           "holderName": "Ujjwal patel",
           "purpose": "FEE",
           "swiftCode": "USBKUS44IMT",
           "holderAddress": {
               "zip": "33126",
               "country": "AF",
               "city": "Miami",
               "addressLine1": "5505 Blue Lagoon Dr",
               "addressLine2": "Main St",
               "state": "NY"
           },
           "type": "CHECKING",
           "acceptedCurrency": [
               "USD"
           ],
           "statusReason": "ACTIVE",
           "accountNumberLast4": "3232",
           "createdOn": "06/21/2024 06:32:54",
           "createdBy": {
               "userType": "CUSTOMER",
               "userName": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 06:37:41",
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "userName": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "holderType": "CORPORATE",
           "verification": {
               "ofacStatus": "VERIFIED",
               "ofacStatusDate": "06/21/2024 06:37:41",
               "ofacStatusReason": "Verified"
           },
           "status": "ACTIVE"
       }
   ]
}
```

- **For non-USD International External Account**

```json Example Request - {Payload}
{
    "id": 67856628,
    "eventType": "internationalexternalaccount.update",
    "eventTimeStamp": "06/12/2025 06:04:11",
    "eventCreated": 1749708251318,
    "eventId": "0198840000000838940001",
    "payload": [
        {
            "url": "/v1/customer/id/4258731/internationalExternalAccount/id/4063258",
            "id": 4063258,
            "holderName": "Testing",
            "holderEmail": "abcd4175@gmail.com",
            "purpose": "Testing1",
            "externalId": "ET2082237231121",
            "holderPhone": "812236216",
            "swiftCode": "BKCHCNBJXXX",
            "holderAddress": {
                "zip": "T9X",
                "country": "CN",
                "city": "Albert",
                "addressLine1": "#1223, hazel street",
                "addressLine2": "Temple",
                "state": "CN"
            },
            "type": "CHECKING",
            "additionalDetail": {
                "taxID": "2815"
            },
            "acceptedCurrency": [
                "CNY"
            ],
            "statusReason": "ACTIVE",
            "accountNumberLast4": "4512",
            "internationalRoutingCode": "92345",
            "holderType": "CORPORATE",
            "verification": {
                "ofacStatus": "VERIFIED",
                "ofacStatusDate": "06/12/2025 06:04:11",
                "ofacStatusReason": "Verified"
            },
            "status": "ACTIVE",
            "statusDate": "06/12/2025 06:04:09",
            "createdOn": "06/12/2025 06:04:09",
            "createdBy": {
                "userType": "API_USER",
                "userName": "nikhil.thakur+39340430393@prth.com",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "06/12/2025 06:04:11",
            "lastUpdatedBy": {
                "userType": "API_USER",
                "userName": "nikhil.thakur+39340430393@prth.com",
                "status": "ACTIVE"
            }
        }
    ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>contact.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65833765,
   "eventType": "contact.create",
   "eventTimeStamp": "06/10/2024 19:08:33",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "contact",
           "url": "/v1/customer/id/4225975/contact/id/4014595",
           "id": 4014595,
           "legalName": "Thermo Pvt. Ltd",
           "contactType": "BUSINESS",
           "name": "Ujjwal Patel",
           "email": "ujjwal.patel+386@prth.com",
           "externalAccount": [
               {
                   "statusDate": "06/27/2024 06:55:14",
                   "bankInfo": {
                       "routingNumber": "021210002",
                       "address": "1460 VALLEY RD,WAYNE,NJ,07470",
                       "name": "VALLEY NATIONAL BANK",
                       "contactNumber": " "
                   },
                   "lastUpdatedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "holderName": "Thermo Pvt. Ltd",
                   "purpose": "Fee",
                   "validateAccount": [
                       {
                           "ews": {
                               "statusDate": "06/27/2024 06:55:14",
                               "statusReason": "PENDING",
                               "status": "PENDING"
                           }
                       }
                   ],
                   "microDeposit": {
                       "microDepositValidation": "NEVER"
                   },
                   "resourceName": "externalAccount",
                   "type": "SAVINGS",
                   "createdOn": "06/27/2024 06:55:14",
                   "prenote": {
                       "prenoteValidation": "NEVER"
                   },
                   "routingNumber": "021210002",
                   "isDefault": false,
                   "statusReason": "External Account Pending Verification",
                   "accountNumberLast4": "7289",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "lastUpdatedOn": "06/27/2024 06:55:14",
                   "id": 4019819,
                   "holderType": "CORPORATE",
                   "verification": {
                       "ofacStatus": "PENDING_VERIFICATION",
                       "ofacStatusDate": "06/27/2024 06:55:14",
                       "ofacStatusReason": "Pending Verification"
                   },
                   "status": "INACTIVE"
               }
           ],
           "card": [
               {
                   "lastUpdatedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "holderName": "Ujjwal  Patel",
                   "expiryMonth": 6,
                   "cardHolder": {
                       "firstName": "Ujjwal",
                       "lastName": "Patel",
                       "name": "Ujjwal  Patel"
                   },
                   "resourceName": "card",
                   "expiryYear": 2025,
                   "createdOn": "06/27/2024 06:55:14",
                   "cardNumberLast4": "5578",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "lastUpdatedOn": "06/27/2024 06:55:14",
                   "id": 10113014,
                   "billingAddress": {
                       "zip": "12343",
                       "city": "Kingston",
                       "addressLine1": "309 Kingston Street",
                       "addressLine2": "Chewbeka",
                       "state": "AK"
                   },
                   "status": "ACTIVE"
               }
           ],
           "internationalExternalAccount": [
               {
                   "statusDate": "06/27/2024 06:55:14",
                   "lastUpdatedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "holderName": "Ujjwal Patel",
                   "purpose": "Fee",
                   "swiftCode": "ARTSAM22XXX",
                   "resourceName": "internationalExternalAccount",
                   "holderAddress": {
                       "zip": "23433",
                       "country": "AL",
                       "city": "Arizona",
                       "addressLine1": "5505 Blue Lagoon Dr",
                       "addressLine2": "Mian",
                       "state": "NY"
                   },
                   "type": "SAVINGS",
                   "createdOn": "06/27/2024 06:55:14",
                   "acceptedCurrency": [
                       "USD"
                   ],
                   "statusReason": "External Account Pending Verification",
                   "accountNumberLast4": "3232",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "lastUpdatedOn": "06/27/2024 06:55:14",
                   "id": 4019820,
                   "holderType": "CORPORATE",
                   "verification": {
                       "ofacStatus": "PENDING_VERIFICATION",
                       "ofacStatusDate": "06/27/2024 06:55:14",
                       "ofacStatusReason": "Pending Verification"
                   },
                   "status": "INACTIVE"
               }
           ],
           "mailingAddress": [
               {
                   "zip": "33126",
                   "lastUpdatedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "city": "Miami",
                   "usage": {
                       "isPayorAddress": false
                   },
                   "resourceName": "address",
                   "createdOn": "06/27/2024 06:55:14",
                   "isDefault": false,
                   "phone": "902-736-7234",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "countryCode": "1",
                   "isPrimary": false,
                   "name": "Thermo Pvt. Ltd",
                   "addressLine1": "5505 Blue Lagoon Dr",
                   "lastUpdatedOn": "06/27/2024 06:55:14",
                   "addressLine2": "Main St",
                   "id": 1176834,
                   "state": "CO",
                   "status": "ACTIVE"
               }
           ],
           "createdOn": "06/27/2024 06:55:14",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/27/2024 06:55:14"
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>contact.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}

{
   "id": 65833782,
   "eventType": "contact.update",
   "eventTimeStamp": "06/27/2024 06:58:35",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "contact",
           "url": "/v1/customer/id/4225975/contact/id/4014595",
           "id": 4014595,
           "name": "Ujjwal Patel",
           "legalName": "Thermo Pvt. Ltd",
           "email": "ujjwal.patel+386@prth.com",
           "externalAccount": [
               {
                   "statusDate": "06/27/2024 06:55:14",
                   "bankInfo": {
                       "routingNumber": "021210002",
                       "address": "1460 VALLEY RD,WAYNE,NJ,07470",
                       "name": "VALLEY NATIONAL BANK",
                       "contactNumber": " "
                   },
                   "lastUpdatedBy": {
                       "userType": "SYSTEM",
                       "username": "SYSTEM",
                       "status": "ACTIVE"
                   },
                   "holderName": "Thermo Pvt. Ltd",
                   "purpose": "Fee",
                   "validateAccount": [
                       {
                           "ews": {
                               "statusDate": "06/27/2024 06:55:14",
                               "statusReason": "PENDING",
                               "status": "PENDING"
                           }
                       }
                   ],
                   "microDeposit": {
                       "microDepositValidation": "NEVER"
                   },
                   "resourceName": "externalAccount",
                   "type": "SAVINGS",
                   "createdOn": "06/27/2024 06:55:14",
                   "prenote": {
                       "prenoteValidation": "NEVER"
                   },
                   "routingNumber": "021210002",
                   "isDefault": false,
                   "statusReason": "External Account Pending Verification",
                   "accountNumberLast4": "7289",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "lastUpdatedOn": "06/27/2024 06:58:33",
                   "id": 4019819,
                   "holderType": "CORPORATE",
                   "verification": {
                       "ofacStatus": "VERIFIED",
                       "ofacStatusDate": "06/27/2024 06:58:33",
                       "ofacStatusReason": "Verified"
                   },
                   "status": "PENDING_VERIFICATION"
               }
           ],
           "card": [
               {
                   "lastUpdatedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "holderName": "Ujjwal  Patel",
                   "expiryMonth": 6,
                   "cardHolder": {
                       "firstName": "Ujjwal",
                       "lastName": "Patel",
                       "name": "Ujjwal  Patel"
                   },
                   "resourceName": "card",
                   "expiryYear": 2025,
                   "createdOn": "06/27/2024 06:55:14",
                   "cardNumberLast4": "5578",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "lastUpdatedOn": "06/27/2024 06:55:14",
                   "id": 10113014,
                   "billingAddress": {
                       "zip": "12343",
                       "city": "Kingston",
                       "addressLine1": "309 Kingston Street",
                       "addressLine2": "Chewbeka",
                       "state": "AK"
                   },
                   "status": "ACTIVE"
               }
           ],
           "contactType": "BUSINESS",
           "internationalExternalAccount": [
               {
                   "statusDate": "06/27/2024 06:55:14",
                   "lastUpdatedBy": {
                       "userType": "SYSTEM",
                       "username": "SYSTEM",
                       "status": "ACTIVE"
                   },
                   "holderName": "Ujjwal Patel",
                   "purpose": "Fee",
                   "swiftCode": "ARTSAM22XXX",
                   "resourceName": "internationalExternalAccount",
                   "holderAddress": {
                       "zip": "23433",
                       "country": "AL",
                       "city": "Arizona",
                       "addressLine1": "5505 Blue Lagoon Dr",
                       "addressLine2": "Mian",
                       "state": "NY"
                   },
                   "type": "SAVINGS",
                   "createdOn": "06/27/2024 06:55:14",
                   "acceptedCurrency": [
                       "USD"
                   ],
                   "statusReason": "ACTIVE",
                   "accountNumberLast4": "3232",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "lastUpdatedOn": "06/27/2024 06:58:33",
                   "id": 4019820,
                   "holderType": "CORPORATE",
                   "verification": {
                       "ofacStatus": "VERIFIED",
                       "ofacStatusDate": "06/27/2024 06:58:33",
                       "ofacStatusReason": "Verified"
                   },
                   "status": "ACTIVE"
               }
           ],
           "mailingAddress": [
               {
                   "zip": "33126",
                   "lastUpdatedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "city": "Miami",
                   "usage": {
                       "isPayorAddress": false
                   },
                   "resourceName": "address",
                   "createdOn": "06/27/2024 06:55:14",
                   "isDefault": false,
                   "phone": "902-736-7234",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "countryCode": "1",
                   "isPrimary": false,
                   "name": "Thermo Pvt. Ltd",
                   "addressLine1": "5505 Blue Lagoon Dr",
                   "lastUpdatedOn": "06/27/2024 06:55:14",
                   "addressLine2": "Main St",
                   "id": 1176834,
                   "state": "CO",
                   "status": "ACTIVE"
               }
           ],
           "createdOn": "06/27/2024 06:55:14",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/27/2024 06:55:14"
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>authorizeduser.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65819811,
   "eventType": "authorizeduser.create",
   "eventTimeStamp": "06/21/2024 06:52:14",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,

   "payload": [
       {
           "resourceName": "authorizedUser",
           "url": "/v1/customer/id/4225975/authorizedUser/id/53520",
           "id": 53520,
           "firstName": "Ujjwal",
           "lastName": "Patel",
           "last4ssn": "7233",
           "isUSCitizen": true,
           "portalAccess": {
               "role": [
                   {
                       "lastUpdatedBy": {
                           "userType": "INTERNAL",
                           "username": "DEFAULT_USER",
                           "status": "ACTIVE"
                       },
                       "assignedBy": {
                           "userType": "CUSTOMER",
                           "username": "ujjwal.patel+362@prth.com",
                           "status": "ACTIVE"
                       },
                       "createdBy": {
                           "userType": "INTERNAL",
                           "username": "DEFAULT_USER",
                           "status": "ACTIVE"
                       },
                       "name": "admin",
                       "lastUpdatedOn": "2024-06-14",
                       "resourceName": "role",
                       "roletype": "NON_ADMIN",
                       "assignedOn": "2024-06-21",
                       "id": 11385,
                       "createdOn": "2024-06-14",
                       "url": "/v1/customer/id/4225975/role"
                   }
               ],
               "grantAccess": true,
               "username": "ujjwal.patel+281_2@prth.com"
           },
           "isBeneficialOwner": false,
           "createdOn": "06/21/2024 06:52:14",
           "userId": 4013084,
           "mobilePhone": "938-726-7860",
           "mailingAddress": [
               {
                   "zip": "66801",
                   "city": "Miami",
                   "isPrimary": true,
                   "usage": {
                       "isPayorAddress": false
                   },
                   "addressLine1": "5505 Blue Lagoon Dr",
                   "resourceName": "address",
                   "addressLine2": "Main St",
                   "id": 1176432,
                   "state": "CT"
               }
           ],
           "createdBy": {
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "dob": "08/08/1998",
           "countryCode": "91",
           "lastUpdatedOn": "06/21/2024 06:52:14",
           "email": "ujjwal.patel+281_2@prth.com",
           "verification": {
               "ofacStatus": "PENDING_VERIFICATION",
               "cipStatus": "PENDING_VERIFICATION",
               "cipStatusDate": "06/21/2024 06:52:14",
               "cipStatusReason": "PENDING_VERIFICATION",
               "ofacStatusDate": "06/21/2024 06:52:14",
               "ofacStatusReason": "PENDING_VERIFICATION"
           },
           "actAsAuthorizedSignatory": false
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>authorizeduser.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
  
{
   "id": 65819815,
   "eventType": "authorizeduser.update",
   "eventTimeStamp": "06/21/2024 06:52:47",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,

   "payload": [
       {
           "resourceName": "authorizedUser",
           "url": "/v1/customer/id/4225975/authorizedUser/id/53520",
           "id": 53520,
           "firstName": "Ujjwal",
           "lastName": "Patel",
           "dob": "08/08/1998",
           "countryCode": "91",
           "mobilePhone": "938-726-7860",
           "last4ssn": "7233",
           "isUSCitizen": true,
           "portalAccess": {
               "role": [
                   {
                       "lastUpdatedBy": {
                           "userType": "INTERNAL",
                           "username": "DEFAULT_USER",
                           "status": "ACTIVE"
                       },
                       "assignedBy": {
                           "userType": "CUSTOMER",
                           "username": "ujjwal.patel+362@prth.com",
                           "status": "ACTIVE"
                       },
                       "createdBy": {
                           "userType": "INTERNAL",
                           "username": "DEFAULT_USER",
                           "status": "ACTIVE"
                       },
                       "name": "admin",
                       "lastUpdatedOn": "2024-06-14",
                       "resourceName": "role",
                       "roletype": "NON_ADMIN",
                       "assignedOn": "2024-06-21",
                       "id": 11385,
                       "createdOn": "2024-06-14",
                       "url": "/v1/customer/id/4225975/role"
                   }
               ],
               "grantAccess": true,
               "username": "ujjwal.patel+281_2@prth.com"
           },
           "isBeneficialOwner": false,
           "userId": 4013084,
           "mailingAddress": [
               {
                   "zip": "66801",
                   "city": "Miami",
                   "isPrimary": true,
                   "usage": {
                       "isPayorAddress": false
                   },
                   "addressLine1": "5505 Blue Lagoon Dr",
                   "resourceName": "address",
                   "addressLine2": "Main St",
                   "id": 1176432,
                   "state": "CT"
               }
           ],
           "createdOn": "06/21/2024 06:52:14",
           "createdBy": {
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "username": "CIPWorkflowUser",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 06:52:41",
           "email": "ujjwal.patel+281_2@prth.com",
           "verification": {
               "ofacStatus": "VERIFIED",
               "cipStatus": "VERIFIED",
               "cipStatusDate": "06/21/2024 06:52:41",
               "cipStatusReason": "Verified",
               "ofacStatusDate": "06/21/2024 06:52:47",
               "ofacStatusReason": "Verified"
           },
           "actAsAuthorizedSignatory": false
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>mailingaddress.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65816884,
   "eventType": "mailingaddress.create",
   "eventTimeStamp": "06/21/2024 05:26:29",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "address",
           "url": "/v1/customer/id/4225975/mailingAddress/id/1176422",
           "id": 1176422,
           "externalId": "62367323",
           "phone": "923-878-9743",
           "isPrimary": true,
           "name": "Ujjwal Patel",
           "addressLine1": "637, Blue Lagoon",
           "addressLine2": "Kingston",
           "city": "Manhatton",
           "state": "NY",
           "zip": "56765",
           "createdOn": "06/21/2024 05:26:29",
           "createdBy": {
               "userType": "INTERNAL",
               "username": "DEFAULT_USER",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "userType": "INTERNAL",
               "username": "DEFAULT_USER",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 05:26:29",
           "usage": {
               "isPayorAddress": true
           },
           "status": "ACTIVE"
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>mailingaddress.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
   {
    "id": 65816882,
    "eventType": "mailingaddress.update",
    "eventTimeStamp": "06/21/2024 05:26:29",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "address",
            "url": "/v1/customer/id/4225975/mailingAddress/id/1176242",
            "id": 1176242,
            "addressLine1": "5505 Blue Lagoon Dre",
            "addressLine2": "Main St",
            "city": "Miami",
            "state": "DC",
            "zip": "33126",
            "isPrimary": false,
            "usage": {
                "isPayorAddress": false
            },
            "createdOn": "06/14/2024 09:47:43",
            "createdBy": {
                "userType": "CUSTOMER",
                "username": "ujjwal.patel+361_2@prth.com",
                "status": "ACTIVE"
            },
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "06/21/2024 05:26:29",
            "status": "ACTIVE"
        }
    ]
 }
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.ach.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65816896,
   "eventType": "transaction.ach.create",
   "eventTimeStamp": "06/21/2024 05:34:15",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491504",
           "id": 230491504,
           "scheduleDate": "06/21/2024",
           "status": "SCHEDULED",
           "statusDate": "06/21/2024 05:34:15",
           "amount": 23,
           "allowDuplicate": true,
           "method": "ACH",
           "purpose": "Fee",
           "nickName": "Checking",
           "source": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915272,
                   "url": "/v1/customer/id/4225975/account/id/9915272"
               }
           },
           "destination": {
               "externalAccount": {
                   "resourceName": "externalAccount",
                   "id": 4019508,
                   "url": "/v1/customer/id/4225975/externalAccount/id/4019508"
               }
           },
           "type": "REGULAR",
           "createdOn": "06/21/2024 05:34:15",
           "transactionClass": "SEND",
           "statusReason": "On User Request",
           "processingDetail": {
               "quickSettle": false,
               "addenda": [
                   ""
               ],
               "companyDescription": "Fee",
               "authType": "WRITTEN",
               "processingMode": "SAME_DAY"
           },
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 05:34:15",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           }
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.ach.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 65816902,
    "eventType": "transaction.ach.update",
    "eventTimeStamp": "06/21/2024 05:34:44",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "transaction",
            "url": "/v1/customer/id/5784291/transaction/id/8376809",
            "id": 8376809,
            "statusDate": "05/08/2025 21:45:05",
            "realizationDate": "05/08/2025 00:00:00",
            "purpose": "Ach transaction",
            "destination": {
                "account": {
                    "resourceName": "account",
                    "id": 4537773,
                    "url": "/v1/customer/id/5784291/account/id/4537773"
                }
            },
            "source": {
                "externalAccount": {
                    "routingNumber": "084106768",
                    "holderName": "Nicolai Eddy",
                    "accountNumberLast4": "9145",
                    "bankName": "EVOLVE BANK AND TRUST",
                    "type": "CHECKING",
                    "verification": {
                        "ofacStatus": "VERIFIED",
                        "ofacStatusDate": "05/01/2025 22:57:18",
                        "ofacStatusReason": "Verified"
                    },
                    "holderType": "CORPORATE"
                }
            },
            "type": "REGULAR",
            "statusReason": "Processed by System",
            "methodType": "ACH_SAME_DAY",
            "scheduleDate": "05/08/2025",
            "amount": 25.66,
            "allowDuplicate": true,
            "method": "ACH",
            "externalId": "PROD-3186856",
            "transactionClass": "COLLECT",
            "processingDetail": {
                "processedMode": "SAME_DAY",
                "traceNumber": "061121025802017",
                "quickSettle": false,
                "companyName": "NALA Inc.",
                "companyDescription": "Fund walle",
                "authType": "ONLINE",
                "processingMode": "SAME_DAY",
                "iin": "F531860301"
            },
            "processDate": "05/08/2025 17:51:42",
            "expectedCompletionDate": "05/08/2025",
            "status": "COMPLETED",
            "createdOn": "05/08/2025 16:01:30",
            "createdBy": {
                "userType": "API_USER",
                "username": "API@SILA.com",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "05/08/2025 21:45:05",
            "lastUpdatedBy": {
                "userType": "SYSTEM",
                "username": "SYSTEM",
                "status": "ACTIVE"
            }
        }
    ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>transaction.check.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65816890,
   "eventType": "transaction.check.create",
   "eventTimeStamp": "06/21/2024 05:32:22",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491503",
           "id": 230491503,
           "statusDate": "06/21/2024 05:32:22",
           "amount": 73,
           "allowDuplicate": false,
           "method": "CHECK",
           "purpose": "Fee",
           "nickName": "Checking Account",
           "destination": {
               "account": {
                   "nickName": "Checking Account",
                   "resourceName": "account",
                   "id": 9915275,
                   "url": "/v1/customer/id/4225975/account/id/9915275"
               }
           },
           "type": "REGULAR",
           "linkedDocument": [
               {
                   "purpose": "CHECK_DEPOSIT",
                   "linkedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "document": {
                       "name": "Check_Front.jpg",
                       "resourceName": "document",
                       "id": 4054176,
                       "type": "CHECK_IMAGE_FRONT",
                       "url": "/v1/document/id/4054176"
                   },
                   "id": 44700,
                   "linkedOn": "06/21/2024 05:32:22",
                   "status": "PENDING_VERIFICATION"
               },
               {
                   "purpose": "CHECK_DEPOSIT",
                   "linkedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "document": {
                       "name": "Check_Back.jpg",
                       "resourceName": "document",
                       "id": 4054177,
                       "type": "CHECK_IMAGE_BACK",
                       "url": "/v1/document/id/4054177"
                   },
                   "id": 44701,
                   "linkedOn": "06/21/2024 05:32:23",
                   "status": "PENDING_VERIFICATION"
               }
           ],
           "transactionClass": "COLLECT",
           "status": "SCHEDULED",
           "statusReason": "On User Request",
           "scheduleDate": "06/21/2024",
           "processingDetail": {
               "quickSettle": false,
               "checkVerification": {
                   "statusReason": "PENDING_VERIFICATION",
                   "checkDetail": {},
                   "status": "PENDING"
               }
           },
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "createdOn": "06/21/2024 05:32:22",
           "lastUpdatedOn": "06/21/2024 05:32:22",
           "expectedCompletionDate": "06/25/2024"
       }
   ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>transaction.check.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65816892,
   "eventType": "transaction.check.update",
   "eventTimeStamp": "06/21/2024 05:32:24",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491503",
           "id": 230491503,
           "status": "SCHEDULED",
           "scheduleDate": "06/21/2024",
           "statusDate": "06/21/2024 05:32:24",
           "amount": 73,
           "method": "CHECK",
           "purpose": "Fee",
           "nickName": "Checking Account",
           "destination": {
               "account": {
                   "nickName": "Checking Account",
                   "resourceName": "account",
                   "id": 9915275,
                   "url": "/v1/customer/id/4225975/account/id/9915275"
               }
           },
           "type": "REGULAR",
           "linkedDocument": [
               {
                   "purpose": "CHECK_DEPOSIT",
                   "linkedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "document": {
                       "name": "Check_Front.jpg",
                       "resourceName": "document",
                       "id": 4054176,
                       "type": "CHECK_IMAGE_FRONT",
                       "url": "/v1/document/id/4054176"
                   },
                   "id": 44700,
                   "linkedOn": "06/21/2024 05:32:22",
                   "status": "PENDING_VERIFICATION"
               },
               {
                   "purpose": "CHECK_DEPOSIT",
                   "linkedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "document": {
                       "name": "Check_Back.jpg",
                       "resourceName": "document",
                       "id": 4054177,
                       "type": "CHECK_IMAGE_BACK",
                       "url": "/v1/document/id/4054177"
                   },
                   "id": 44701,
                   "linkedOn": "06/21/2024 05:32:23",
                   "status": "PENDING_VERIFICATION"
               }
           ],
           "transactionClass": "COLLECT",
           "statusReason": "Check amount mismatch",
           "processingDetail": {
               "quickSettle": false,
               "checkVerification": {
                   "statusReason": "IQA verified.",
                   "checkDetail": {
                       "routingNumber": "121000015",
                       "checkNumber": "602",
                       "checkAmount": 3.95,
                       "accountNumber": "998777-6655"
                   },
                   "status": "IQA_VERIFIED"
               }
           },
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "createdOn": "06/21/2024 05:32:22",
           "lastUpdatedOn": "06/21/2024 05:32:24",
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "expectedCompletionDate": "06/25/2024"
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.card.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65818336,
   "eventType": "transaction.card.create",
   "eventTimeStamp": "06/21/2024 06:23:33",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491510",
           "id": 230491510,
           "purpose": "Fee",
           "method": "CARD",
           "nickName": "Checking",
           "source": {
               "card": {
                   "holderName": "Ujjwal Patel",
                   "cardNumberLast4": "5578",
                   "form": "VIRTUAL",
                   "expiryMonth": 6,
                   "cardType": "CREDIT",
                   "expiryYear": 2025,
                   "brand": "VISA"
               }
           },
           "destination": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915272,
                   "url": "/v1/customer/id/4225975/account/id/9915272"
               }
           },
           "type": "REGULAR",
           "statusReason": "Payment Captured Successfully",
           "scheduleDate": "06/21/2024",
           "statusDate": "06/21/2024 06:23:33",
           "amount": 23,
           "authCode": "PPSf3a",
           "allowDuplicate": true,
           "isCaptured": true,
           "transactionClass": "COLLECT",
           "processingDetail": {
               "quickSettle": false,
               "statementDescriptor": "PRT*Thermo Pvt. Ltd-Transportation Fee",
               "merchant": {
                   "resourceName": "merchant",
                   "id": 4005758,
                   "url": "/v1/customer/id/4225975/merchant/id/4005758"
               },
               "device": {
                   "lastUpdatedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "inputCapability": "KEYED_ONLY",
                   "partialApprovalSupport": "NOT_SUPPORTED",
                   "transactionSecurity": "NORMAL",
                   "createdOn": "06/21/2024",
                   "accountCaptureMethod": "MANUAL",
                   "cardholderPresence": "ECOM",
                   "catLevel": "ECOM",
                   "posId": "PP0001",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "lastUpdatedOn": "06/21/2024",
                   "location": "HOME_PC",
                   "attendance": "HOME_PC",
                   "cardPresent": false
               },
               "order": {
                   "invoice": {
                       "number": "0000000001000000000097425",
                       "lastUpdatedBy": {
                           "userType": "CUSTOMER",
                           "username": "ujjwal.patel+362@prth.com",
                           "status": "ACTIVE"
                       },
                       "lineItem": [
                           {
                               "productCode": "099",
                               "quantity": 1,
                               "unitOfMeasure": "EACH",
                               "extendedAmount": 23,
                               "unitCost": 23,
                               "description": "Passport"
                           }
                       ],
                       "shipmentDetail": {
                           "address": {}
                       },
                       "createdBy": {
                           "userType": "CUSTOMER",
                           "username": "ujjwal.patel+362@prth.com",
                           "status": "ACTIVE"
                       },
                       "lastUpdatedOn": "06/21/2024",
                       "createdOn": "06/21/2024"
                   }
               }
           },
           "processDate": "06/21/2024 06:23:33",
           "isAutoCapture": true,
           "expectedCompletionDate": "06/21/2024",
           "pendingCaptureAmount": 0,
           "status": "CAPTURED",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "createdOn": "06/21/2024 06:23:33",
           "lastUpdatedOn": "06/21/2024 06:23:33",
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           }
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.card.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65818692,
   "eventType": "transaction.card.update",
   "eventTimeStamp": "06/21/2024 06:25:38",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491510",
           "id": 230491510,
           "type": "REGULAR",
           "statusReason": "Incorrectly Charged",
           "scheduleDate": "06/21/2024",
           "amount": 23,
           "authCode": "PPSf3a",
           "allowDuplicate": true,
           "method": "CARD",
           "nickName": "Checking",
           "statusDate": "06/21/2024 06:25:38",
           "purpose": "Fee",
           "source": {
               "card": {
                   "holderName": "Ujjwal Patel",
                   "cardNumberLast4": "5578",
                   "form": "VIRTUAL",
                   "expiryMonth": 6,
                   "cardType": "CREDIT",
                   "expiryYear": 2025,
                   "brand": "VISA"
               }
           },
           "destination": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915272,
                   "url": "/v1/customer/id/4225975/account/id/9915272"
               }
           },
           "isCaptured": true,
           "transactionClass": "COLLECT",
           "processingDetail": {
               "quickSettle": false,
               "statementDescriptor": "PRT*Thermo Pvt. Ltd-Transportation Fee",
               "merchant": {
                   "resourceName": "merchant",
                   "id": 4005758,
                   "url": "/v1/customer/id/4225975/merchant/id/4005758"
               },
               "device": {
                   "lastUpdatedBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "inputCapability": "KEYED_ONLY",
                   "partialApprovalSupport": "NOT_SUPPORTED",
                   "transactionSecurity": "NORMAL",
                   "createdOn": "06/21/2024",
                   "accountCaptureMethod": "MANUAL",
                   "cardholderPresence": "ECOM",
                   "catLevel": "ECOM",
                   "posId": "PP0001",
                   "createdBy": {
                       "userType": "CUSTOMER",
                       "username": "ujjwal.patel+362@prth.com",
                       "status": "ACTIVE"
                   },
                   "lastUpdatedOn": "06/21/2024",
                   "location": "HOME_PC",
                   "attendance": "HOME_PC",
                   "cardPresent": false
               },
               "order": {
                   "invoice": {
                       "number": "0000000001000000000097425",
                       "lastUpdatedBy": {
                           "userType": "CUSTOMER",
                           "username": "ujjwal.patel+362@prth.com",
                           "status": "ACTIVE"
                       },
                       "lineItem": [
                           {
                               "productCode": "099",
                               "quantity": 1,
                               "unitOfMeasure": "EACH",
                               "extendedAmount": 23,
                               "unitCost": 23,
                               "description": "Passport"
                           }
                       ],
                       "shipmentDetail": {
                           "address": {}
                       },
                       "createdBy": {
                           "userType": "CUSTOMER",
                           "username": "ujjwal.patel+362@prth.com",
                           "status": "ACTIVE"
                       },
                       "lastUpdatedOn": "06/21/2024",
                       "createdOn": "06/21/2024"
                   }
               }
           },
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "createdOn": "06/21/2024 06:23:33",
           "lastUpdatedOn": "06/21/2024 06:25:38",
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "processDate": "06/21/2024 06:23:33",
           "isAutoCapture": true,
           "expectedCompletionDate": "06/21/2024",
           "pendingCaptureAmount": 0,
           "status": "VOIDED"
       }
   ]
}

```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.wire.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65817243,
   "eventType": "transaction.wire.create",
   "eventTimeStamp": "06/21/2024 05:36:10",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491505",
           "id": 230491505,
           "status": "SCHEDULED",
           "amount": 2,
           "allowDuplicate": false,
           "method": "WIRE",
           "purpose": "Fee",
           "nickName": "Checking",
           "destination": {
               "externalAccount": {
                   "resourceName": "externalAccount",
                   "id": 4019508,
                   "url": "/v1/customer/id/4225975/externalAccount/id/4019508"
               }
           },
           "source": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915272,
                   "url": "/v1/customer/id/4225975/account/id/9915272"
               }
           },
           "type": "REGULAR",
           "transactionClass": "SEND",
           "statusReason": "On User Request",
           "processingDetail": {
               "memo": "Fee"
           },
           "scheduleDate": "06/21/2024",
           "statusDate": "06/21/2024 05:36:10",
           "createdOn": "06/21/2024 05:36:10",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 05:36:10"
       }
   ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>transaction.wire.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65818671,
   "eventType": "transaction.wire.update",
   "eventTimeStamp": "06/21/2024 06:24:55",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491505",
           "id": 230491505,
           "type": "REGULAR",
           "method": "WIRE",
           "purpose": "Fee",
           "nickName": "Checking",
           "status": "PENDING",
           "statusDate": "06/21/2024 06:24:55",
           "amount": 21,
           "allowDuplicate": false,
           "source": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915272,
                   "url": "/v1/customer/id/4225975/account/id/9915272"
               }
           },
           "destination": {
               "externalAccount": {
                   "resourceName": "externalAccount",
                   "id": 4019508,
                   "url": "/v1/customer/id/4225975/externalAccount/id/4019508"
               }
           },
           "transactionClass": "SEND",
           "statusReason": "External Account Pending Verification",
           "processingDetail": {
               "memo": "Fee"
           },
           "scheduleDate": "06/21/2024",
           "createdOn": "06/21/2024 05:36:10",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "userType": "SYSTEM",
               "username": "SYSTEM",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 06:24:55"
       }
   ]
}

```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.internationalwire.create</strong></p>
</td>
<td width="375">

- **For USD International External Account**

```json Example Request - {Payload}
{
   "id": 65819088,
   "eventType": "transaction.internationalwire.create",
   "eventTimeStamp": "06/21/2024 06:45:31",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491516",
           "id": 230491516,
           "status": "SCHEDULED",
           "amount": 23,
           "allowDuplicate": false,
           "method": "INTERNATIONAL_WIRE",
           "purpose": "Fee",
           "nickName": "Checking",
           "source": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915327,
                   "url": "/v1/customer/id/4225975/account/id/9915327"
               }
           },
           "destination": {
               "internationalExternalAccount": {
                   "resourceName": "internationalExternalAccount",
                   "id": 4019518,
                   "url": "/v1/customer/id/4225975/internationalExternalAccount/id/4019518"
               }
           },
           "type": "REGULAR",
           "transactionClass": "SEND",
           "statusReason": "On User Request",
           "processingDetail": {
               "memo": "Transportation Fee"
           },
           "scheduleDate": "06/21/2024",
           "currency": "USD",
           "statusDate": "06/21/2024 06:45:31",
           "createdOn": "06/21/2024 06:45:31",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 06:45:31",
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           }
       }
   ]
}
```

- **For non - USD International External Account**

```json Example Request - {Payload}

{
    "id": 67863490,
    "eventType": "transaction.internationalwire.create",
    "eventId": "0201640000000584310001",
    "payload": [
        {
            "statusDate": "06/13/2025 05:14:44",
            "purpose": "charges",
            "destination": {
                "internationalExternalAccount": {
                    "resourceName": "internationalExternalAccount",
                    "id": 4063347,
                    "url": "/v1/customer/id/4258731/internationalExternalAccount/id/4063347"
                }
            },
            "source": {
                "account": {
                    "resourceName": "account",
                    "id": 9939650,
                    "url": "/v1/customer/id/4258731/account/id/9939650"
                }
            },
            "type": "REGULAR",
            "createdOn": "06/13/2025 05:14:44",
            "amountOriginType": "DESTINATION",
            "statusReason": "On User Request",
            "methodType": "WIRE",
            "scheduleDate": "06/13/2025",
            "lastUpdatedOn": "06/13/2025 05:14:44",
            "currency": "CNY",
            "id": 230558472,
            "lastUpdatedBy": {
                "userType": "API_USER",
                "username": "nikhil.thakur+39340430393@prth.com",
                "status": "ACTIVE"
            },
            "amount": 12.5,
            "allowDuplicate": true,
            "method": "INTERNATIONAL_WIRE",
            "isTaxPayment": false,
            "externalId": "ET2342234832",
            "resourceName": "transaction",
            "url": "/v1/customer/id/4258731/transaction/id/230558472",
            "transactionClass": "SEND",
            "processingDetail": {
                "fxQuote": {
                    "fxRate": "0.140747",
                    "fee": 0,
                    "destination": {
                        "amount": 12.5,
                        "currency": "CNY"
                    },
                    "resourceName": "fxQuote",
                    "id": 90,
                    "source": {
                        "amount": 1.76,
                        "currency": "USD"
                    },
                    "url": "/v1/customer/id/4258731/transaction/fxQuote/id/90"
                },
                "memo": "transaction"
            },
            "createdBy": {
                "userType": "API_USER",
                "username": "nikhil.thakur+39340430393@prth.com",
                "status": "ACTIVE"
            },
            "status": "SCHEDULED"
        }
    ],
    "eventTimeStamp": "06/13/2025 05:14:44",
    "eventCreated": 1749791684805
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>ransaction.internationalwire.update</strong></p>
</td>
<td width="375">

- **For USD International External Account**

```json Example Request - {Payload}
{
   "id": 65819256,
   "eventType": "transaction.internationalwire.update",
   "eventTimeStamp": "06/21/2024 06:46:34",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491516",
           "id": 230491516,
           "status": "PROCESSING",
           "amount": 23,
           "allowDuplicate": false,
           "method": "INTERNATIONAL_WIRE",
           "purpose": "Fee",
           "nickName": "Checking",
           "source": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915327,
                   "url": "/v1/customer/id/4225975/account/id/9915327"
               }
           },
           "destination": {
               "internationalExternalAccount": {
                   "resourceName": "internationalExternalAccount",
                   "id": 4019518,
                   "url": "/v1/customer/id/4225975/internationalExternalAccount/id/4019518"
               }
           },
           "type": "REGULAR",
           "transactionClass": "SEND",
           "statusReason": "Processing In Transit",
           "currency": "USD",
           "statusDate": "06/21/2024 06:46:34",
           "processingDetail": {
               "memo": "Transportation Fee",
               "originator": "Thermo Pvt. Ltd c/o Finxera"
           },
           "processDate": "06/21/2024 06:46:33",
           "scheduleDate": "06/21/2024",
           "createdOn": "06/21/2024 06:45:31",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 06:46:34",
           "lastUpdatedBy": {
               "userType": "SYSTEM",
               "username": "SYSTEM",
               "status": "ACTIVE"
           }
       }
   ]
}
```

- **For non-USD International External Account**

```json Example Request - {Payload}
{
    "id": 67863492,
    "eventType": "transaction.internationalwire.update",
    "eventId": "0201650000000303880001",
    "payload": [
        {
            "statusDate": "06/13/2025 05:14:44",
            "purpose": "fees for payment",
            "destination": {
                "internationalExternalAccount": {
                    "resourceName": "internationalExternalAccount",
                    "id": 4063347,
                    "url": "/v1/customer/id/4258731/internationalExternalAccount/id/4063347"
                }
            },
            "source": {
                "account": {
                    "resourceName": "account",
                    "id": 9939650,
                    "url": "/v1/customer/id/4258731/account/id/9939650"
                }
            },
            "type": "REGULAR",
            "createdOn": "06/13/2025 05:14:44",
            "amountOriginType": "DESTINATION",
            "statusReason": "On User Request",
            "methodType": "WIRE",
            "scheduleDate": "06/13/2025",
            "lastUpdatedOn": "06/13/2025 05:19:56",
            "currency": "CNY",
            "id": 230558472,
            "lastUpdatedBy": {
                "userType": "API_USER",
                "username": "nikhil.thakur+39340430393@prth.com",
                "status": "ACTIVE"
            },
            "amount": 12.5,
            "allowDuplicate": true,
            "method": "INTERNATIONAL_WIRE",
            "isTaxPayment": false,
            "externalId": "ET2342234832",
            "resourceName": "transaction",
            "url": "/v1/customer/id/4258731/transaction/id/230558472",
            "transactionClass": "SEND",
            "processingDetail": {
                "fxQuote": {
                    "fxRate": "0.140747",
                    "fee": 0,
                    "destination": {
                        "amount": 12.5,
                        "currency": "CNY"
                    },
                    "resourceName": "fxQuote",
                    "id": 90,
                    "source": {
                        "amount": 1.76,
                        "currency": "USD"
                    },
                    "url": "/v1/customer/id/4258731/transaction/fxQuote/id/90"
                },
                "memo": "transaction"
            },
            "createdBy": {
                "userType": "API_USER",
                "username": "nikhil.thakur+39340430393@prth.com",
                "status": "ACTIVE"
            },
            "status": "SCHEDULED"
        }
    ],
    "eventTimeStamp": "06/13/2025 05:19:56",
    "eventCreated": 1749791996755
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.book.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65835612,
   "eventType": "transaction.book.create",
   "eventTimeStamp": "06/28/2024 11:37:23",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491671",
           "id": 230491671,
           "statusDate": "06/28/2024 11:37:23",
           "amount": 10,
           "allowDuplicate": true,
           "method": "BOOK",
           "processInstantly": false,
           "purpose": "Fee",
           "nickName": "Checking",
           "source": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915327,
                   "url": "/v1/customer/id/4225975/account/id/9915327"
               }
           },
           "destination": {
               "account": {
                   "resourceName": "account",
                   "id": 9915275,
                   "url": "/v1/customer/id/4225975/account/id/9915275"
               }
           },
           "type": "REGULAR",
           "status": "SCHEDULED",
           "transactionClass": "SEND",
           "statusReason": "On User Request",
           "processingDetail": {
               "memo": "Fee"
           },
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "scheduleDate": "06/28/2024",
           "createdOn": "06/28/2024 11:37:23",
           "lastUpdatedOn": "06/28/2024 11:37:23",
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           }
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.book.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65835625,
   "eventType": "transaction.book.update",
   "eventTimeStamp": "06/28/2024 11:38:44",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491507",
           "id": 230491507,
           "statusDate": "06/28/2024 11:38:44",
           "amount": 3,
           "allowDuplicate": true,
           "method": "BOOK",
           "processInstantly": true,
           "purpose": "Account Setup",
           "nickName": "Checking",
           "source": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915326,
                   "url": "/v1/customer/id/4225975/account/id/9915326"
               }
           },
           "destination": {
               "account": {
                   "resourceName": "account",
                   "id": 4003201,
                   "url": "/v1/customer/id/423062/account/id/4003201"
               }
           },
           "type": "REGULAR",
           "status": "COMPLETED",
           "transactionClass": "SYSTEM_FEE",
           "statusReason": "Processed by System",
           "createdBy": {
               "userType": "SYSTEM",
               "username": "SYSTEM",
               "status": "ACTIVE"
           },
           "createdOn": "06/21/2024 05:58:53",
           "processDate": "06/28/2024 11:38:44",
           "scheduleDate": "06/21/2024",
           "lastUpdatedOn": "06/28/2024 11:38:44",
           "lastUpdatedBy": {
               "userType": "SYSTEM",
               "username": "SYSTEM",
               "status": "ACTIVE"
           }
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.virtualcard.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65819444,
   "eventType": "transaction.virtualcard.create",
   "eventTimeStamp": "06/21/2024 06:48:36",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491517",
           "id": 230491517,
           "statusDate": "06/21/2024 06:48:36",
           "amount": 2,
           "allowDuplicate": false,
           "method": "VIRTUAL_CARD",
           "purpose": "Fee",
           "nickName": "Checking",
           "source": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915327,
                   "url": "/v1/customer/id/4225975/account/id/9915327"
               }
           },
           "destination": {
               "email": "kavya.sharma+100@prth.com"
           },
           "type": "REGULAR",
           "transactionClass": "SEND",
           "statusReason": "On User Request",
           "processingDetail": {
               "virtualCard": {
                   "resourceName": "virtualCard",
                   "id": 901011645,
                   "url": "/v1/customer/id/4225975/account/id/9915327/virtualCard/id/901011645"
               }
           },
           "scheduleDate": "06/21/2024",
           "status": "SCHEDULED",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "createdOn": "06/21/2024 06:48:36",
           "lastUpdatedOn": "06/21/2024 06:48:36",
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           }
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>transaction.virtualcard.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 65819800,
   "eventType": "transaction.virtualcard.update",
   "eventTimeStamp": "06/21/2024 06:49:33",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "transaction",
           "url": "/v1/customer/id/4225975/transaction/id/230491517",
           "id": 230491517,
           "amount": 2,
           "allowDuplicate": false,
           "method": "VIRTUAL_CARD",
           "purpose": "Fee",
           "nickName": "Checking",
           "source": {
               "account": {
                   "nickName": "Checking",
                   "resourceName": "account",
                   "id": 9915327,
                   "url": "/v1/customer/id/4225975/account/id/9915327"
               }
           },
           "destination": {
               "email": "kavya.sharma+100@prth.com"
           },
           "type": "REGULAR",
           "transactionClass": "SEND",
           "statusReason": "Processing In Transit",
           "processingDetail": {
               "virtualCard": {
                   "resourceName": "virtualCard",
                   "id": 901011645,
                   "url": "/v1/customer/id/4225975/account/id/9915327/virtualCard/id/901011645"
               }
           },
           "processDate": "06/21/2024 06:49:31",
           "scheduleDate": "06/21/2024",
           "status": "PROCESSING",
           "statusDate": "06/21/2024 06:49:31",
           "createdOn": "06/21/2024 06:48:36",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+362@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/21/2024 06:49:31",
           "lastUpdatedBy": {
               "userType": "SYSTEM",
               "username": "SYSTEM",
               "status": "ACTIVE"
           }
       }
   ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>ledger.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
For ACH transaction: 
{
    "id": 67810538,
    "eventCreated": 1748425349095,
    "eventType": "ledger.create",
    "eventTimeStamp": "05/28/2025 09:42:29",
    "eventId": "0159110000000183330002",
    "payload": [
        {
            "id": 3613372,
            "amount": 5400,
            "account": {
                "resourceName": "account",
                "id": 9917435,
                "url": "/v1/customer/id/4228222/account/id/9917435"
            },
            "ledgerDate": "05/28/2025",
            "method": "ACH",
            "groupId": "230556705T",
            "type": "CREDIT",
            "narration": "Deposit from *7288 fEE Ref: 230556705",
            "schedule": {
                "resourceName": "transaction",
                "id": 230556705,
                "url": "/v1/transaction/id/230556705"
            },
            "scheduleClass": "COLLECT",
            "createdOn": "05/28/2025 09:42:29",
            "createdBy": {
                "userType": "SYSTEM",
                "username": "SYSTEM",
                "status": "ACTIVE"
            },
            "lastUpdatedBy": {
                "userType": "SYSTEM",
                "username": "SYSTEM",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "05/28/2025 09:42:29"
        }
    ]
}
For Debit Card: 
{
    "id": 570719385,
    "eventType": "ledger.create",
    "eventTimeStamp": "05/28/2025 19:08:51",
    "eventCreated": 1748459331990,
    "eventId": "3934530000003903500002",
    "payload": [
        {
            "id": 14911785,
            "amount": 5,
            "ledgerDate": "05/28/2025",
            "method": "CARD",
            "account": {
                "resourceName": "account",
                "id": 4350958,
                "url": "/v1/customer/id/5686406/account/id/4350958"
            },
            "narration": "Pending To *3440 - BIRD APP* PENDING.BIRD +18662052442 FLUS",
            "groupId": "1030648CET",
            "type": "DEBIT",
            "ledgerType": "HOLD",
            "createdOn": "05/28/2025 19:08:51",
            "createdBy": {
                "userType": "SYSTEM",
                "username": "SYSTEM",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "05/28/2025 19:08:51",
            "lastUpdatedBy": {
                "userType": "SYSTEM",
                "username": "SYSTEM",
                "status": "ACTIVE"
            }
        }
    ]
}
```

</td>
</tr>

<tr>
<td width="284">
<p><strong>debitcard.create</strong></p>
</td>
<td width="375">

For "Expose Debit card sensitive data" setting as TRUE

```json Example Request - {Payload}
{
   "id": 1363188,
   "eventType": "debitcard.create",
   "eventTimeStamp": "06/27/2024 09:36:24",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "debitCard",
           "url": "v1/customer/id/4049187/account/id/4034426/debitCard/id/610",
           "id": 610,
           "statusDate": "06/27/2024 09:36:24",
           "cardHolder": {
               "name": "Ujjwal Patel",
               "id": 115203,
               "type": "BENEFICIAL_OWNER"
           },
           "type": "PLASTIC",
           "cardProgram": "PM CORP STD PB PL CARD2pGLBQ",
           "shippingDetail": {
               "address": {
                   "zip": "33126",
                   "city": "Miami",
                   "addressLine1": "5505 Blue Lagoon Dr",
                   "addressLine2": "",
                   "id": 1206720,
                   "state": "CO",
                   "status": "ACTIVE"
               },
               "expressDelivery": true
           },
           "status": "PENDING",
           "statusReason": "Debit Card Request submitted",
           "properties": {
               "isDigitalFirst": false
           },
           "createdOn": "06/27/2024 09:36:24",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+375@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+375@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/27/2024 09:36:24"
       }
   ]
}
```

For "Expose Debit card sensitive data" setting as FALSE

```json Example Request - {Payload}
{
   "id": 1368698,
   "eventType": "debitcard.create",
   "eventTimeStamp": "07/18/2024 05:38:20",
   "payload": [
       {
           "resourceName": "debitCard",
           "url": "v1/customer/id/4049198/account/id/4034496/debitCard/id/657",
           "id": 657,
           "externalId": "35435235",
           "cardHolder": {
               "name": "Ujjwal Patel1",
               "id": 115238,
               "type": "BENEFICIAL_OWNER"
           },
           "cardNumber": "****************",
           "cvv": "***",
           "cardIssuanceId": "1058",
           "type": "DIGITAL",
           "cardProgram": "CORP STD PB V CARDXaoVK",
           "shippingDetail": {
               "address": {
                   "zip": "46014",
                   "city": "kingston",
                   "addressLine1": "2683",
                   "addressLine2": "Sector 4 MDC",
                   "id": 1206763,
                   "state": "AR",
                   "status": "ACTIVE"
               },
               "expressDelivery": false
           },
           "isReissuedOnce": false,
           "properties": {
               "isDigitalFirst": false
           },
           "status": "ACTIVE"
       }
   ],
   "statusReason": "Debit Card activated",
   "statusDate": "07/18/2024 05:38:20",
   "createdOn": "07/18/2024 05:38:20",
   "lastUpdatedBy": {
       "userType": "INTERNAL",
       "username": "DEFAULT_USER",
       "status": "ACTIVE"
   },
   "createdBy": {
       "userType": "INTERNAL",
       "username": "DEFAULT_USER",
       "status": "ACTIVE"
   },
   "lastUpdatedOn": "07/18/2024 05:38:20"
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>debitcard.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
   "id": 1363189,
   "eventType": "debitcard.update",
   "eventTimeStamp": "06/27/2024 09:46:13",
   "eventId": "0001709618091430001",
   "eventCreated": 1747098180090,
   "payload": [
       {
           "resourceName": "debitCard",
           "url": "v1/customer/id/4049187/account/id/4034426/debitCard/id/610",
           "id": 610,
           "cardHolder": {
               "name": "Ujjwal Patel",
               "id": 115203,
               "type": "BENEFICIAL_OWNER"
           },
           "type": "PLASTIC",
           "cardProgram": "PM CORP STD PB PL CARD2pGLBQ",
           "shippingDetail": {
               "address": {
                   "zip": "33126",
                   "city": "Miami",
                   "addressLine1": "5505 Blue Lagoon Dr",
                   "addressLine2": "",
                   "id": 1206720,
                   "state": "CO",
                   "status": "ACTIVE"
               },
               "expressDelivery": true
           },
           "statusReason": "Debit Card Request submitted",
           "cardNumber": "3626",
           "properties": {
               "isDigitalFirst": false
           },
           "status": "ACTIVE",
           "statusDate": "06/27/2024 09:36:24",
           "createdOn": "06/27/2024 09:36:24",
           "createdBy": {
               "userType": "CUSTOMER",
               "username": "ujjwal.patel+375@prth.com",
               "status": "ACTIVE"
           },
           "lastUpdatedOn": "06/27/2024 09:46:13",
           "lastUpdatedBy": {
               "userType": "SYSTEM",
               "username": "SYSTEM",
               "status": "ACTIVE"
           }
       }
   ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>moneygram.deposit.initiated</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 1368904,
    "eventType": "moneygram.deposit.initiated",
    "eventTimeStamp": "07/31/2024 12:54:20",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "source": "MONEYGRAM",
            "accountNumber": "CMG12345",
            "referenceNumber": "4026596520240731",
            "amount": 20.6,
            "processDate": "07/31/2024 12:54:20"
        }
    ]
}

```

</td>
</tr>
<tr>
<td width="284">
<p><strong>merchant.directfunded.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 66287814,
    "eventType": "merchant.directfunded.create",
    "eventTimeStamp": "07/31/2024 12:32:19",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "merchant",
            "url": "/v1/customer/id/4227607/merchant/id/4006291",
            "id": 4006291,
            "externalId": "73267632",
            "statusDate": "07/31/2024 12:32:18",
            "configuration": {
                "quickSettle": false,
                "passportFunding": {
                    "enable": false
                }
            },
            "priorBankruptcy": false,
            "type": "DIRECT_FUNDED",
            "cardNotPresent": {
                "billingMethod": {
                    "monthly": 10,
                    "yearly": 10,
                    "onetime": 80
                },
                "advertisingMethod": "Online",
                "internetBusinessType": "ADVERTISEMENT"
            },
            "categoryCode": "0742",
            "saleDetails": {
                "saleMethod": {
                    "ecom": 25,
                    "pos": 50,
                    "moto": 25
                },
                "averageDeliveryTime": "WEEK",
                "averagePurchase": 100,
                "productDescription": "Agriculture department",
                "averageSalesVolumes": 100
            },
            "processor": {
                "name": "TSYS"
            },
            "underwritingStatus": "PENDING",
            "categoryType": "Agricultural Services",
            "linkedDocument": [
                {
                    "purpose": "UNDERWRITING",
                    "linkedBy": {
                        "userType": "INTERNAL",
                        "username": "DEFAULT_USER",
                        "status": "ACTIVE"
                    },
                    "document": {
                        "name": "Kreacher.png",
                        "resourceName": "document",
                        "id": 4056254,
                        "type": "MERCHANT_AGREEMENT",
                        "url": "/v1/document/id/4056254"
                    },
                    "id": 46410,
                    "linkedOn": "07/31/2024 12:32:19",
                    "status": "PENDING_VERIFICATION"
                }
            ],
            "amex": {
                "optBlue": true
            },
            "discover": {
                "fullAcquiring": true
            },
            "merchantAccount": {
                "resourceName": "account",
                "id": 9916199,
                "accountNumber": "8125071400006678",
                "url": "/v1/customer/id/4227607/account/id/9916199"
            },
            "underwritingStatusDate": "07/31/2024 12:32:18",
            "location": {
                "resourceName": "location",
                "url": "/v1/customer/id/4227607/merchant/id/4006291/location"
            },
            "status": "INACTIVE",
            "createdOn": "07/31/2024 12:32:18",
            "createdBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "07/31/2024 12:32:18",
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            }
        }
    ]
}

```

</td>
</tr>
<tr>
<td width="284">
<p><strong>merchant.directfunded.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 66287821,
    "eventType": "merchant.directfunded.update",
    "eventTimeStamp": "07/31/2024 12:33:49",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "merchant",
            "url": "/v1/customer/id/4227607/merchant/id/4006291",
            "id": 4006291,
            "externalId": "73267632",
            "configuration": {
                "quickSettle": false,
                "passportFunding": {
                    "enable": false
                }
            },
            "priorBankruptcy": false,
            "type": "DIRECT_FUNDED",
            "discover": {
                "fullAcquiring": true
            },
            "amex": {
                "optBlue": true
            },
            "cardNotPresent": {
                "billingMethod": {
                    "monthly": 10,
                    "yearly": 10,
                    "onetime": 80
                },
                "advertisingMethod": "Online",
                "internetBusinessType": "ADVERTISEMENT"
            },
            "categoryCode": "0742",
            "saleDetails": {
                "saleMethod": {
                    "ecom": 25,
                    "pos": 50,
                    "moto": 25
                },
                "averageDeliveryTime": "WEEK",
                "averagePurchase": 100,
                "productDescription": "Agriculture department",
                "averageSalesVolumes": 80
            },
            "processor": {
                "name": "TSYS"
            },
            "statusDate": "07/31/2024 12:32:18",
            "underwritingStatus": "PENDING",
            "categoryType": "Agricultural Services",
            "linkedDocument": [
                {
                    "purpose": "UNDERWRITING",
                    "linkedBy": {
                        "userType": "INTERNAL",
                        "username": "DEFAULT_USER",
                        "status": "ACTIVE"
                    },
                    "document": {
                        "name": "Kreacher.png",
                        "resourceName": "document",
                        "id": 4056254,
                        "type": "MERCHANT_AGREEMENT",
                        "url": "/v1/document/id/4056254"
                    },
                    "id": 46410,
                    "linkedOn": "07/31/2024 12:32:19",
                    "status": "PENDING_VERIFICATION"
                }
            ],
            "merchantAccount": {
                "resourceName": "account",
                "id": 9916199,
                "accountNumber": "8125071400006678",
                "url": "/v1/customer/id/4227607/account/id/9916199"
            },
            "underwritingStatusDate": "07/31/2024 12:32:18",
            "location": {
                "resourceName": "location",
                "url": "/v1/customer/id/4227607/merchant/id/4006291/location"
            },
            "status": "INACTIVE",
            "createdOn": "07/31/2024 12:32:18",
            "createdBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "07/31/2024 12:33:48",
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            }
        }
    ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>merchant.payfac.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 66287825,
    "eventType": "merchant.payfac.create",
    "eventTimeStamp": "07/31/2024 12:37:23",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "merchant",
            "url": "/v1/customer/id/4227607/merchant/id/4006292",
            "id": 4006292,
            "externalId": "38728366",
            "statusDate": "07/31/2024 12:37:23",
            "underwritingStatusDate": "07/31/2024 12:37:23",
            "status": "INACTIVE",
            "configuration": {
                "passportFunding": {
                    "enable": false
                }
            },
            "priorBankruptcy": false,
            "categoryCode": "3000",
            "type": "PAYFAC",
            "saleDetails": {
                "saleMethod": {
                    "ecom": 25,
                    "pos": 50,
                    "moto": 25
                },
                "averageDeliveryTime": "WEEK",
                "averagePurchase": 170,
                "productDescription": "Arline services",
                "averageSalesVolumes": 170
            },
            "underwritingStatus": "PENDING",
            "categoryType": "Airlines",
            "linkedDocument": [
                {
                    "purpose": "UNDERWRITING",
                    "linkedBy": {
                        "userType": "INTERNAL",
                        "username": "DEFAULT_USER",
                        "status": "ACTIVE"
                    },
                    "document": {
                        "name": "Kreacher.png",
                        "resourceName": "document",
                        "id": 4056256,
                        "type": "MERCHANT_AGREEMENT",
                        "url": "/v1/document/id/4056256"
                    },
                    "id": 46412,
                    "linkedOn": "07/31/2024 12:37:23",
                    "status": "PENDING_VERIFICATION"
                }
            ],
            "merchantAccount": {
                "resourceName": "account",
                "id": 9916199,
                "accountNumber": "8125071400006678",
                "url": "/v1/customer/id/4227607/account/id/9916199"
            },
            "location": {
                "resourceName": "location",
                "url": "/v1/customer/id/4227607/merchant/id/4006292/location"
            },
            "createdOn": "07/31/2024 12:37:23",
            "createdBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "07/31/2024 12:37:23"
        }
    ]
}
```

</td>
</tr>
<tr>
<td width="284">
<p><strong>merchant.payfac.update</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 66287837,
    "eventType": "merchant.payfac.update",
    "eventTimeStamp": "07/31/2024 12:44:41",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "merchant",
            "url": "/v1/customer/id/4227607/merchant/id/4006292",
            "id": 4006292,
            "externalId": "38728366",
            "statusDate": "07/31/2024 12:37:23",
            "configuration": {
                "passportFunding": {
                    "enable": false
                }
            },
            "priorBankruptcy": false,
            "categoryCode": "3000",
            "type": "PAYFAC",
            "saleDetails": {
                "saleMethod": {
                    "ecom": 25,
                    "pos": 50,
                    "moto": 25
                },
                "averageDeliveryTime": "WEEK",
                "averagePurchase": 170,
                "productDescription": "Arline service",
                "averageSalesVolumes": 170
            },
            "underwritingStatus": "PENDING",
            "categoryType": "Airlines",
            "linkedDocument": [
                {
                    "purpose": "UNDERWRITING",
                    "linkedBy": {
                        "userType": "INTERNAL",
                        "username": "DEFAULT_USER",
                        "status": "ACTIVE"
                    },
                    "document": {
                        "name": "Kreacher.png",
                        "resourceName": "document",
                        "id": 4056256,
                        "type": "MERCHANT_AGREEMENT",
                        "url": "/v1/document/id/4056256"
                    },
                    "id": 46412,
                    "linkedOn": "07/31/2024 12:37:23",
                    "status": "PENDING_VERIFICATION"
                }
            ],
            "merchantAccount": {
                "resourceName": "account",
                "id": 9916199,
                "accountNumber": "8125071400006678",
                "url": "/v1/customer/id/4227607/account/id/9916199"
            },
            "createdOn": "07/31/2024 12:37:23",
            "createdBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "07/31/2024 12:44:41",
            "lastUpdatedBy": {
                "userType": "INTERNAL",
                "username": "DEFAULT_USER",
                "status": "ACTIVE"
            },
            "underwritingStatusDate": "07/31/2024 12:37:23",
            "location": {
                "resourceName": "location",
                "url": "/v1/customer/id/4227607/merchant/id/4006292/location"
            },
            "status": "INACTIVE"
        }
    ]
}
```

<tr>
<td width="284">
<p><strong>return.wire.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 66645151,
    "eventType": "return.wire.create",
    "eventTimeStamp": "08/13/2024 07:29:04",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "return",
            "id": 20013130,
            "createdOn": "08/13/2024 06:49:48",
            "lastUpdatedBy": {
                "userType": "SYSTEM",
                "username": "SYSTEM",
                "status": "ACTIVE"
            },
            "amount": 20,
            "method": "WIRE",
            "createdBy": {
                "userType": "SYSTEM",
                "username": "SYSTEM",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "08/13/2024 07:03:34",
            "returnAgainst": {
                "resourceName": "send",
                "id": 230494370,
                "url": "/v1/transaction/id/230494370"
            },
            "account": {
                "resourceName": "account",
                "id": 9916396,
                "url": "/v1/customer/id/4228150/account/id/9916396"
            }
        }
    ]
}
```

<tr>
<td width="284">
<p><strong>return.internationalwire.create</strong></p>
</td>
<td width="375">

```json Example Request - {Payload}
{
    "id": 66645151,
    "eventType": "return.internationalwire.create",
    "eventTimeStamp": "08/13/2024 07:29:04",
    "eventId": "0001709618091430001",
    "eventCreated": 1747098180090,
    "payload": [
        {
            "resourceName": "return",
            "id": 20013137,
            "createdOn": "08/13/2024 07:29:04",
            "lastUpdatedBy": {
                "userType": "SYSTEM",
                "username": "SYSTEM",
                "status": "ACTIVE"
            },
            "amount": 30,
            "method": "INTERNATIONAL_WIRE",
            "createdBy": {
                "userType": "SYSTEM",
                "username": "SYSTEM",
                "status": "ACTIVE"
            },
            "lastUpdatedOn": "08/13/2024 07:29:04",
            "returnAgainst": {
                "resourceName": "send",
                "id": 230494420,
                "url": "/v1/transaction/id/230494420"
            },
            "account": {
                "resourceName": "account",
                "id": 9916396,
                "url": "/v1/customer/id/4228150/account/id/9916396"
            }
        }
    ]
}
```

</td>
</tr>
</tbody>
</table>

</table>