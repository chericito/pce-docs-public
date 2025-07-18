---
title: Webhooks
deprecated: false
hidden: false
metadata:
  robots: index
---


# Event Name

## customer.individual.create

\{&#x20;&#x20;
&#x20;   "id": 15140,
&#x20;   "eventType": "customer.individual.create",
&#x20;   "eventTimeStamp": "05/13/2025 01:03:00",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "customer",
&#x20;           "url": "/v1/customer/id/4009402",
&#x20;           "id": 4009402,
&#x20;           "tags": \[
&#x20;               "grade A customer"
&#x20;           ],
&#x20;           "externalId": "TSC0567890",
&#x20;           "metaData": \{
&#x20;               "acceptedDraftAmount": "$333.50"
&#x20;           },
&#x20;           "type": "INDIVIDUAL",
&#x20;           "individual": \{
&#x20;               "firstName": "John",
&#x20;               "middleName": "K",
&#x20;               "lastName": "Smith",
&#x20;               "fullName": "John K Smith",
&#x20;               "last4ssn": "9578",
&#x20;               "dob": "06/25/2000",
&#x20;               "homePhone": "573-986-1372",
&#x20;               "mobilePhone": "235-247-4107",
&#x20;               "workPhone": "838-900-9290",
&#x20;               "mailingAddress": \[
&#x20;                   \{
&#x20;                       "resourceName": "address",
&#x20;                       "url": "/v1/customer/id/4009402/mailingAddress/id/1033532",
&#x20;                       "id": 1033532,
&#x20;                       "externalId": "P94567A221",
&#x20;                       "addressLine1": "999",
&#x20;                       "addressLine2": "GT1 KMB",
&#x20;                       "city": "San Jose",
&#x20;                       "state": "CA",
&#x20;                       "zip": "95311",
&#x20;                       "isPrimary": true
&#x20;                   }
&#x20;               ],
&#x20;               "verification": \{
&#x20;                   "ofacStatus": "PENDING\_VERIFICATION",
&#x20;                   "ofacStatusReason": "PENDING\_VERIFICATION",
&#x20;                   "ofacStatusDate": "12/03/2022 07:49:48",
&#x20;                   "cipStatus": "IGNORED",
&#x20;                   "cipStatusReason": "IGNORED ON\_USER\_REQUEST",
&#x20;                   "cipStatusDate": "12/03/2022 07:49:48"
&#x20;               },
&#x20;               "createdOn": "12/03/2022 07:49:48",
&#x20;               "lastUpdatedOn": "12/03/2022 07:49:48"
&#x20;           },
&#x20;           "isPaperless": false,
&#x20;           "status": "ACTIVE",
&#x20;           "statusReason": "ON\_USER\_REQUEST",
&#x20;           "statusDate": "12/03/2022 07:49:48",
&#x20;           "account": \{
&#x20;               "resourceName": "account",
&#x20;               "url": "/v1/customer/id/4009402/account"
&#x20;           },
&#x20;           "externalAccount": \{
&#x20;               "resourceName": "externalAccount",
"url": "/v1/customer/id/4009402/externalAccount"
&#x20;           },
&#x20;           "linkedDocument": \[
&#x20;               \{
&#x20;                   "id": 24658,
&#x20;                   "purpose": "AUTHORIZATION",
&#x20;                   "status": "PENDING\_VERIFICATION",
&#x20;                   "document": \{
&#x20;                       "resourceName": "document",
&#x20;                       "url": "/v1/document/id/4023765",
&#x20;                       "id": 4023765,
&#x20;                       "type": "SPAA",
&#x20;                       "name": "abc.pdf"
&#x20;                   },
&#x20;                   "linkedOn": "12/03/2022 07:49:48",
&#x20;                   "linkedBy": \{
&#x20;                       "userType": "API\_USER",
&#x20;                       "username": "FyPtDp\@test.com",
&#x20;                       "status": "ACTIVE"
&#x20;                   }
&#x20;               }
&#x20;           ],
&#x20;           "createdOn": "12/03/2022 07:49:48",
&#x20;           "createdBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "FyPtDp\@test.com",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "12/03/2022 07:49:48",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "FyPtDp\@test.com",
&#x20;               "status": "ACTIVE"
&#x20;           }
&#x20;       }
&#x20;   ]
}


## customer.business.create

&#x20;&#x20;

\{
&#x20;   "id": 15140,
&#x20;   "eventType": "customer.business.create",
&#x20;   "eventTimeStamp": "05/13/2025 01:03:00",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,

&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "customer",
&#x20;           "url": "/v1/customer/id/4007317",
&#x20;           "id": 4007317,
&#x20;           "externalId": "PMAcceptance-Mar26",
&#x20;           "type": "BUSINESS",
&#x20;           "business": \{
&#x20;               "legalName": "AMEX",
&#x20;               "ein": "22-2015690",
&#x20;               "doingBusinessAs": "American Express",
&#x20;               "phone": "213-233-1731",
&#x20;               "email": "businesstest567\@gmail.com",
&#x20;               "website": "www\.amex.com",
&#x20;               "mailingAddress": \[
&#x20;                   \{
&#x20;                       "resourceName": "address",
&#x20;                       "url": "/v1/customer/id/4007317/mailingAddress/id/1021541",
&#x20;                       "id": 1021541,
&#x20;                       "externalId": "PA09090991",
&#x20;                       "addressLine1": "Ap 4891",
&#x20;                       "addressLine2": "Conference Centre Ste 1020",
&#x20;                       "city": "Sugar Notch",
&#x20;                       "state": "PA",
&#x20;                       "zip": "18706",
&#x20;                       "isPrimary": true,
&#x20;                       "usage": \{
&#x20;                           "isPayorAddress": false
&#x20;                       }
&#x20;                   }
&#x20;               ],
&#x20;               "verification": \{
&#x20;                   "ofacStatus": "PENDING\_VERIFICATION",
&#x20;                   "ofacStatusReason": "PENDING\_VERIFICATION",
&#x20;                   "ofacStatusDate": "03/26/2023 06:46:41",
&#x20;                   "cipStatus": "IGNORED",
&#x20;                   "cipStatusReason": "IGNORED ON\_USER\_REQUEST",
&#x20;                   "cipStatusDate": "03/26/2023 06:46:41"
&#x20;               },
&#x20;               "stateOfIncorporation": "CA",
&#x20;               "businessCategory": "LLC",
&#x20;               "dateOfIncorporation": "12/20/2000",
&#x20;               "beneficialOwner": \[
&#x20;                   \{
&#x20;                       "id": 7522,
&#x20;                       "firstName": "Amelia",
&#x20;                       "lastName": "Connor",
&#x20;                       "fullName": "Amelia Connor",
&#x20;                       "last4ssn": "2023",
&#x20;                       "dob": "10/01/2000",
&#x20;                       "homePhone": "530-986-1172",
&#x20;                       "mobilePhone": "235-237-4107",
&#x20;                       "workPhone": "838-900-9090",
&#x20;                       "email": "botest56789\@gmail.com",
&#x20;                       "mailingAddress": \[
&#x20;                           \{
&#x20;                               "id": 1021542,
&#x20;                               "externalId": "PC30945678911",
&#x20;                               "addressLine1": "Ap 4391",
&#x20;                               "addressLine2": "Conference Centre Ste 1020",
&#x20;                               "city": "Sugar Notch",
&#x20;                               "state": "PA",
&#x20;                               "zip": "18706",
&#x20;                               "isPrimary": true
&#x20;                           }
&#x20;                       ],
&#x20;                       "verification": \{
&#x20;                           "ofacStatus": "PENDING\_VERIFICATION",
&#x20;                           "ofacStatusReason": "PENDING\_VERIFICATION",
&#x20;                           "ofacStatusDate": "03/26/2023 06:46:41",
&#x20;                           "cipStatus": "PENDING\_VERIFICATION",
&#x20;                           "cipStatusReason": "PENDING\_VERIFICATION",
&#x20;                           "cipStatusDate": "03/26/2023 06:53:19"
&#x20;                       },
&#x20;                       "isUSCitizen": true,
&#x20;                       "actAsAuthorizedSignatory": true,
&#x20;                       "businessDetails": \{
&#x20;                           "ownershipPercentage": 50.0,
&#x20;                           "title": "Secretary"
&#x20;                       },
&#x20;                       "secondaryIdentification": \{
&#x20;                           "lastFourId": "2905",
&#x20;                           "id": "48832905",
&#x20;                           "type": "DRIVER\_LICENSE",
&#x20;                           "stateOfIssuance": "CA"
&#x20;                       },
&#x20;                       "pullCreditReport": false
&#x20;                   }
&#x20;               ]
&#x20;           },
&#x20;           "isPaperless": true,
&#x20;           "status": "ACTIVE",
&#x20;           "statusReason": "ON\_USER\_REQUEST",
&#x20;           "statusDate": "03/26/2023 06:46:41",
&#x20;           "account": \{
&#x20;               "resourceName": "account",
&#x20;               "url": "/v1/customer/id/4007317/account"
&#x20;           },
&#x20;           "externalAccount": \{
&#x20;               "resourceName": "externalAccount",
&#x20;               "url": "/v1/customer/id/4007317/externalAccount"
&#x20;           },
&#x20;           "card": \{
&#x20;               "resourceName": "card",
&#x20;               "url": "/v1/customer/id/4007317/card"
&#x20;           },
&#x20;           "merchant": \{
&#x20;               "resourceName": "merchant",
&#x20;               "url": "/v1/customer/id/4007317/merchant"
&#x20;           },
&#x20;           "createdOn": "03/26/2023 06:46:41",
&#x20;           "createdBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "passportqa+420938505985\@prth.com",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "03/26/2023 06:46:41",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "passportqa+420938505985\@prth.com",
&#x20;               "status": "ACTIVE"
&#x20;           }
&#x20;       }
&#x20;   ]
}

## customer.jointTendancy.create

&#x20;&#x20;

\{
&#x20;   "id": 15140,
&#x20;   "eventType": "customer.jointtenancy.create",
&#x20;   "eventTimeStamp": "05/13/2025 01:03:00",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "customer",
&#x20;           "url": "/v1/customer/id/4006644",
&#x20;           "id": 4006644,
&#x20;           "type": "JOINT\_TENANCY",
&#x20;           "isPaperless": true,
&#x20;           "status": "ACTIVE",
&#x20;           "statusReason": "ON\_USER\_REQUEST",
&#x20;           "statusDate": "05/01/2024 09:55:57",
&#x20;           "account": \{
&#x20;               "resourceName": "account",
&#x20;               "url": "/v1/customer/id/4006644/account"
&#x20;           },
&#x20;           "externalAccount": \{
&#x20;               "resourceName": "externalAccount",
&#x20;               "url": "/v1/customer/id/4006644/externalAccount"
&#x20;           },
&#x20;           "card": \{
&#x20;               "resourceName": "card",
&#x20;               "url": "/v1/customer/id/4006644/card"
&#x20;           },
&#x20;           "ppi": \{
&#x20;               "resourceName": "ppi",
&#x20;               "ppi": "aditya.dhawan\@ppi",
&#x20;               "url": "/v1/customer/id/4006644/ppi"
&#x20;           },
&#x20;           "createdOn": "05/01/2024 09:55:57",
&#x20;           "createdBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "passportqa+aDePqJ\@prth.com",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "05/01/2024 10:34:43",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "portalAccess": \{
&#x20;               "grantAccess": true,
&#x20;               "username": "aditya.dhawan\@prth.com",
&#x20;               "role": \[
&#x20;                   \{
&#x20;                       "resourceName": "role",
&#x20;                       "url": "/v1/customer/id/4006644/role",
&#x20;                       "id": 5991
&#x20;                   }
&#x20;               ]
&#x20;           },
&#x20;           "owners": \[
&#x20;               \{
&#x20;                   "id": 18528,
&#x20;                   "isPrimaryOwner": true,
&#x20;                   "firstName": "Aryan",
&#x20;                   "lastName": "Sharma",
&#x20;                   "fullName": "Aryan Sharma",
&#x20;                   "last4ssn": "8292",
&#x20;                   "dob": "02/07/1935",
&#x20;                   "mobilePhone": "869-995-2968",
"email": "aditya.dhawan\@prth.com",
&#x20;                   "mailingAddress": \[
&#x20;                       \{
&#x20;                           "resourceName": "address",
&#x20;                           "id": 1021289,
&#x20;                           "addressLine1": "house no 8989",
&#x20;                           "city": "Newyork",
&#x20;                           "state": "HI",
&#x20;                           "zip": "10001",
&#x20;                           "isPrimary": true,
&#x20;                           "usage": \{
&#x20;                               "isPayorAddress": false
&#x20;                           }
&#x20;                       }
&#x20;                   ],
&#x20;                   "verification": \{
&#x20;                       "ofacStatus": "IGNORED",
&#x20;                       "ofacStatusReason": "IGNORED ON\_USER\_REQUEST",
&#x20;                       "ofacStatusDate": "05/01/2024 09:54:31",
&#x20;                       "cipStatus": "VERIFIED",
&#x20;                       "cipStatusReason": "Verified",
&#x20;                       "cipStatusDate": "05/01/2024 12:36:18"
&#x20;                   },
&#x20;                   "portalAccess": \{
&#x20;                       "grantAccess": true,
&#x20;                       "username": "aditya.dhawan\@prth.com"
&#x20;                   },
&#x20;                   "createdOn": "05/01/2024 09:55:57",
&#x20;                   "lastUpdatedOn": "05/01/2024 09:55:57",
&#x20;                   "userId": 4008293
&#x20;               },
&#x20;               \{
&#x20;                   "id": 18529,
&#x20;                   "isPrimaryOwner": false,
&#x20;                   "firstName": "Himanshu",
&#x20;                   "middleName": "",
&#x20;                   "lastName": "Invitation Joint Tenancy",
&#x20;                   "fullName": "Himanshu Invitation Joint Tenancy",
&#x20;                   "last4ssn": "6345",
&#x20;                   "dob": "02/07/1935",
&#x20;                   "mobilePhone": "142-124-5465",
&#x20;                   "email": "aditya.dhawan+101010\@prth.com",
&#x20;                   "mailingAddress": \[
&#x20;                       \{
&#x20;                           "resourceName": "address",
&#x20;                           "id": 1021285,
&#x20;                           "addressLine1": "6789",
&#x20;                           "addressLine2": "",
&#x20;                           "city": "califronia",
&#x20;                           "state": "CA",
&#x20;                           "zip": "45678",
&#x20;                           "isPrimary": true,
&#x20;                           "usage": \{
&#x20;                               "isPayorAddress": false
&#x20;                           }
&#x20;                       }
&#x20;                   ],
&#x20;                   "verification": \{
&#x20;                       "ofacStatus": "IGNORED",
"ofacStatusReason": "IGNORED ON\_USER\_REQUEST",
&#x20;                       "ofacStatusDate": "05/01/2024 09:54:31",
&#x20;                       "cipStatus": "VERIFIED",
&#x20;                       "cipStatusReason": "Verified",
&#x20;                       "cipStatusDate": "05/01/2024 10:34:43"
&#x20;                   },
&#x20;                   "portalAccess": \{
&#x20;                       "grantAccess": false
&#x20;                   },
&#x20;                   "createdOn": "05/01/2024 09:55:57",
&#x20;                   "lastUpdatedOn": "05/01/2024 09:55:57"
&#x20;               }
&#x20;           ],
&#x20;           "verification": \{
&#x20;               "ofacStatus": "IGNORED",
&#x20;               "ofacStatusReason": "IGNORED ON\_USER\_REQUEST",
&#x20;               "ofacStatusDate": "05/01/2024 09:54:31",
&#x20;               "cipStatus": "VERIFIED",
&#x20;               "cipStatusReason": "Verified",
&#x20;               "cipStatusDate": "05/01/2024 12:36:18"
&#x20;           }
&#x20;       }
&#x20;   ]
}

## customer.business.update

&#x20;&#x20;

\{
&#x20;   "id": 15140,
&#x20;   "eventType": "customer.business.update",
&#x20;   "eventTimeStamp": "05/13/2025 01:03:00",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "customer",
&#x20;           "url": "/v1/customer/id/4007317",
&#x20;           "id": 4007317,
&#x20;           "externalId": "PMAcceptance-Mar26",
&#x20;           "type": "BUSINESS",
&#x20;           "business": \{
&#x20;               "legalName": "AMEX",
&#x20;               "ein": "22-2015690",
&#x20;               "doingBusinessAs": "American Express",
&#x20;               "phone": "213-233-1731",
&#x20;               "email": "businesstest567\@gmail.com",
&#x20;               "website": "www\.amex.com",
&#x20;               "mailingAddress": \[
&#x20;                   \{
&#x20;                       "resourceName": "address",
&#x20;                       "url": "/v1/customer/id/4007317/mailingAddress/id/1021541",
&#x20;                       "id": 1021541,
&#x20;                       "externalId": "PA09090991",
&#x20;                       "addressLine1": "Ap 4891",
&#x20;                       "addressLine2": "Conference Centre Ste 1020",
&#x20;                       "city": "Sugar Notch",
&#x20;                       "state": "PA",
&#x20;                       "zip": "18706",
&#x20;                       "isPrimary": true,
&#x20;                       "usage": \{
&#x20;                           "isPayorAddress": false
&#x20;                       }
&#x20;                   }
&#x20;               ],
&#x20;               "verification": \{
&#x20;                   "ofacStatus": "PENDING\_VERIFICATION",
&#x20;                   "ofacStatusReason": "PENDING\_VERIFICATION",
&#x20;                   "ofacStatusDate": "03/26/2023 06:46:41",
&#x20;                   "cipStatus": "IGNORED",
&#x20;                   "cipStatusReason": "IGNORED ON\_USER\_REQUEST",
&#x20;                   "cipStatusDate": "03/26/2023 06:46:41"
&#x20;               },
&#x20;               "stateOfIncorporation": "CA",
&#x20;               "businessCategory": "LLC",
&#x20;               "dateOfIncorporation": "12/20/2000",
&#x20;               "beneficialOwner": \[
&#x20;                   \{
&#x20;                       "id": 7522,
&#x20;                       "firstName": "Amelia",
&#x20;                       "lastName": "Connor",
&#x20;                       "fullName": "Amelia Connor",
&#x20;                       "last4ssn": "2023",
&#x20;                       "dob": "10/01/2000",
&#x20;                       "homePhone": "530-986-1172",
&#x20;                       "mobilePhone": "235-237-4107",
&#x20;                       "workPhone": "838-900-9090",
&#x20;                       "email": "botest56789\@gmail.com",
&#x20;                       "mailingAddress": \[
&#x20;                           \{
&#x20;                               "id": 1021542,
"externalId": "PC30945678911",
&#x20;                               "addressLine1": "Ap 4391",
&#x20;                               "addressLine2": "Conference Centre Ste 1020",
&#x20;                               "city": "Sugar Notch",
&#x20;                               "state": "PA",
&#x20;                               "zip": "18706",
&#x20;                               "isPrimary": true
&#x20;                           }
&#x20;                       ],
&#x20;                       "verification": \{
&#x20;                           "ofacStatus": "PENDING\_VERIFICATION",
&#x20;                           "ofacStatusReason": "PENDING\_VERIFICATION",
&#x20;                           "ofacStatusDate": "03/26/2023 06:46:41",
&#x20;                           "cipStatus": "PENDING\_VERIFICATION",
&#x20;                           "cipStatusReason": "PENDING\_VERIFICATION",
&#x20;                           "cipStatusDate": "03/26/2023 06:53:19"
&#x20;                       },
&#x20;                       "isUSCitizen": true,
&#x20;                       "actAsAuthorizedSignatory": true,
&#x20;                       "businessDetails": \{
&#x20;                           "ownershipPercentage": 50.0,
&#x20;                           "title": "Secretary"
&#x20;                       },
&#x20;                       "secondaryIdentification": \{
&#x20;                           "lastFourId": "2905",
&#x20;                           "id": "48832905",
&#x20;                           "type": "DRIVER\_LICENSE",
&#x20;                           "stateOfIssuance": "CA"
&#x20;                       },
&#x20;                       "pullCreditReport": false
&#x20;                   }
&#x20;               ]
&#x20;           },
&#x20;           "isPaperless": true,
&#x20;           "status": "ACTIVE",
&#x20;           "statusReason": "ON\_USER\_REQUEST",
&#x20;           "statusDate": "03/26/2023 06:46:41",
&#x20;           "account": \{
&#x20;               "resourceName": "account",
&#x20;               "url": "/v1/customer/id/4007317/account"
&#x20;           },
&#x20;           "externalAccount": \{
&#x20;               "resourceName": "externalAccount",
&#x20;               "url": "/v1/customer/id/4007317/externalAccount"
&#x20;           },
&#x20;           "card": \{
&#x20;               "resourceName": "card",
&#x20;               "url": "/v1/customer/id/4007317/card"
&#x20;           },
&#x20;           "merchant": \{
&#x20;               "resourceName": "merchant",
&#x20;               "url": "/v1/customer/id/4007317/merchant"
&#x20;           },
&#x20;           "createdOn": "03/26/2023 06:46:41",
&#x20;           "createdBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "passportqa+420938505985\@prth.com",
"status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "03/26/2023 06:46:41",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "passportqa+420938505985\@prth.com",
&#x20;               "status": "ACTIVE"
&#x20;           }
&#x20;       }
&#x20;   ]
}

## customer.individual.update

&#x20;&#x20;

\{
&#x20;   "id": 3013,
&#x20;   "eventType": "customer.individual.update",
&#x20;   "eventTimeStamp": "06/10/2024 19:08:33",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "customer",
&#x20;           "url": "/v1/customer/id/4048848",
&#x20;           "id": 4048848,
&#x20;           "type": "INDIVIDUAL",
&#x20;           "individual": \{
&#x20;               "firstName": "Jon",
&#x20;               "lastName": "Williams",
&#x20;               "mobilePhone": "123-456-7890",
&#x20;               "countryCode": "91",
&#x20;               "fullName": "Jon Smith Williams",
&#x20;               "lastUpdatedOn": "06/10/2024 19:08:33",
&#x20;               "middleName": "Smith",
&#x20;               "createdOn": "05/30/2024 08:39:47",
&#x20;               "email": "passportqa+76564168576255988299\@prth.com",
&#x20;               "verification": \{
&#x20;                   "ofacStatus": "IGNORED",
&#x20;                   "cipStatus": "UNVERIFIED",
&#x20;                   "cipStatusDate": "05/30/2024 08:39:47",
&#x20;                   "cipStatusReason": "UNVERIFIED",
&#x20;                   "ofacStatusDate": "06/10/2024 19:08:33",
&#x20;                   "ofacStatusReason": "IGNORED ON\_USER\_REQUEST"
&#x20;               }
&#x20;           },
&#x20;           "portalAccess": \{
&#x20;               "role": \[
&#x20;                   \{
&#x20;                       "resourceName": "role",
&#x20;                       "id": 14305,
&#x20;                       "url": "/v1/customer/id/4048848/role"
&#x20;                   }
&#x20;               ],
&#x20;               "grantAccess": true,
&#x20;               "username": "passportqa+76564168576255988299\@prth.com"
&#x20;           },
&#x20;           "statusReason": "ON\_USER\_REQUEST",
&#x20;           "isPaperless": false,
&#x20;           "statusDate": "05/30/2024 08:39:47",
&#x20;           "externalAccount": \{
&#x20;               "resourceName": "externalAccount",
&#x20;               "url": "/v1/customer/id/4048848/externalAccount"
&#x20;           },
&#x20;           "account": \{
&#x20;               "resourceName": "account",
&#x20;               "url": "/v1/customer/id/4048848/account"
&#x20;           },
&#x20;           "card": \{
&#x20;               "resourceName": "card",
&#x20;               "url": "/v1/customer/id/4048848/card"
&#x20;           },
&#x20;           "status": "ACTIVE",
&#x20;           "createdBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "DCMRQQ\@test.com",
&#x20;               "status": "ACTIVE"
},
&#x20;           "createdOn": "05/30/2024 08:39:47",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "06/10/2024 19:08:33"
&#x20;       }
&#x20;   ]
}

## customer.jointtenancy.update

&#x20;&#x20;

\{
&#x20;   "id": 3019,
&#x20;   "eventType": "customer.jointtenancy.update",
&#x20;   "eventTimeStamp": "06/10/2024 19:18:12",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "customer",
&#x20;           "url": "/v1/customer/id/4048556",
&#x20;           "id": 4048556,           &#x20;
&#x20;           "statusDate": "05/09/2024 07:59:20",
&#x20;           "portalAccess": \{
&#x20;               "grantAccess": false
&#x20;           },
&#x20;           "externalId": "CustJ12",
&#x20;           "owners": \[
&#x20;               \{
&#x20;                   "lastName": "Smith",
&#x20;                   "lastUpdatedBy": \{
&#x20;                       "userType": "INTERNAL",
&#x20;                       "username": "DEFAULT\_USER",
&#x20;                       "status": "ACTIVE"
&#x20;                   },
&#x20;                   "last4ssn": "4344",
&#x20;                   "homePhone": "131-312-4444",
&#x20;                   "portalAccess": \{
&#x20;                       "grantAccess": false
&#x20;                   },
&#x20;                   "externalId": "Ownerj2ext",
&#x20;                   "fullName": "Kewin Smith",
&#x20;                   "createdOn": "05/09/2024 07:59:20",
&#x20;                   "isPrimaryOwner": true,
&#x20;                   "firstName": "Kewin",
&#x20;                   "linkedDocument": \[
&#x20;                       \{
&#x20;                           "purpose": "IDENTIFICATION\_PROOF",
&#x20;                           "linkedBy": \{
&#x20;                               "userType": "INTERNAL",
&#x20;                               "username": "DEFAULT\_USER",
&#x20;                               "status": "ACTIVE"
&#x20;                           },
&#x20;                           "document": \{
&#x20;                               "name": "images (1) (1).jpg",
&#x20;                               "resourceName": "document",
&#x20;                               "id": 4117906,
&#x20;                               "type": "PASSPORT",
&#x20;                               "url": "/v1/document/id/4117906"
&#x20;                           },
&#x20;                           "id": 132848,
&#x20;                           "linkedOn": "Thu May 09 07:59:20 UTC 2024",
&#x20;                           "status": "PENDING\_VERIFICATION"
&#x20;                       }
&#x20;                   ],
&#x20;                   "mailingAddress": \[
&#x20;                       \{
&#x20;                           "zip": "12313",
&#x20;                           "city": "new",
&#x20;                           "isPrimary": true,
&#x20;                           "usage": \{
&#x20;                               "isPayorAddress": false
&#x20;                           },
&#x20;                           "addressLine1": "test",
&#x20;                           "resourceName": "address",
&#x20;                           "id": 1205304,
&#x20;                           "state": "AL"
&#x20;                       }
&#x20;                   ],
&#x20;                   "createdBy": \{
&#x20;                       "userType": "INTERNAL",
&#x20;                       "username": "DEFAULT\_USER",
&#x20;                       "status": "ACTIVE"
&#x20;                   },
&#x20;                   "dob": "05/12/1937",
&#x20;                   "secondaryIdentification": \{
&#x20;                       "stateOfIssuance": "AK",
&#x20;                       "id": "13134312432",
&#x20;                       "type": "DRIVER\_LICENSE"
&#x20;                   },
&#x20;                   "lastUpdatedOn": "05/09/2024 07:59:20",
&#x20;                   "id": 113569,
&#x20;                   "email": "ctr.abcdd+233\@prth.com",
&#x20;                   "verification": \{
&#x20;                       "ofacStatus": "IGNORED",
&#x20;                       "cipStatus": "UNVERIFIED",
&#x20;                       "cipStatusDate": "06/10/2024 19:18:11",
&#x20;                       "cipStatusReason": "UNVERIFIED",
&#x20;                       "ofacStatusDate": "06/10/2024 19:18:11",
&#x20;                       "ofacStatusReason": "IGNORED ON\_USER\_REQUEST"
&#x20;                   }
&#x20;               }
&#x20;           ],
&#x20;           "type": "JOINT\_TENANCY",
&#x20;           "createdOn": "05/09/2024 07:59:20",
&#x20;           "statusReason": "ON\_USER\_REQUEST",
&#x20;           "createdBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "isPaperless": false,
&#x20;           "externalAccount": \{
&#x20;               "resourceName": "externalAccount",
&#x20;               "url": "/v1/customer/id/4048556/externalAccount"
&#x20;           },
&#x20;           "lastUpdatedOn": "06/10/2024 19:18:11",
&#x20;           "programAffiliate": \{
&#x20;               "name": "ANSHULPARTNER",
&#x20;               "id": 1296
&#x20;           },
&#x20;           "account": \{
&#x20;               "resourceName": "account",
&#x20;               "url": "/v1/customer/id/4048556/account"
&#x20;           },
&#x20;           "card": \{
&#x20;               "resourceName": "card",
&#x20;               "url": "/v1/customer/id/4048556/card"
&#x20;           },
&#x20;           "verification": \{
&#x20;               "ofacStatus": "IGNORED",
&#x20;               "cipStatus": "UNVERIFIED",
&#x20;               "cipStatusDate": "06/10/2024 19:18:11",
&#x20;               "cipStatusReason": "UNVERIFIED",
&#x20;               "ofacStatusDate": "06/10/2024 19:18:11",
&#x20;               "ofacStatusReason": "IGNORED ON\_USER\_REQUEST"
&#x20;           },
&#x20;           "status": "ACTIVE"
&#x20;       }
&#x20;   ]
}

## account.create

&#x20;&#x20;

\{
&#x20;   "id": 15140,
&#x20;   "eventType": "account.create",
&#x20;   "eventTimeStamp": "06/10/2024 19:08:33",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "account",
&#x20;           "url": "v1/customer/id/4007825/account/id/4003513",
&#x20;           "id": 4003513,
&#x20;           "externalId": "E22343422234125678654",
&#x20;           "nickName": "Jhon",
&#x20;           "accountNumber": "8125001200000346",
&#x20;           "status": "INACTIVE",
&#x20;           "statusReason": "PENDING\_VERIFICATION",
&#x20;           "statusDate": "06/08/2023 06:11:10",
&#x20;           "balance": \{
&#x20;               "amount": "0.00",
&#x20;               "asOn": "06/08/2023 06:11:26"
&#x20;           },
&#x20;           "availableBalance": \{
&#x20;               "amount": "0.00",
&#x20;               "asOn": "06/08/2023 06:11:26"
&#x20;           },
&#x20;           "purpose": "FEE",
&#x20;           "routableAccount": \{
&#x20;               "accountNumber": "76650000004347",
&#x20;               "routingNumber": "053101561",
&#x20;               "wireRoutingNumber": "122287251",
&#x20;               "wireAccountNumber": "13976650000004347",
&#x20;               "wireMemo": "Alex Johnson 13976650000004347",
&#x20;               "memo": "Alex Johnson 76650000004347"
&#x20;           },
&#x20;           "linkedDocument": \[
&#x20;               \{
&#x20;                   "id": 15339,
&#x20;                   "purpose": "AUTHORIZATION",
&#x20;                   "status": "PENDING\_VERIFICATION",
&#x20;                   "document": \{
&#x20;                       "resourceName": "document",
&#x20;                       "url": "/v1/document/id/4014696",
&#x20;                       "id": 4014696,
&#x20;                       "type": "SPAA",
&#x20;                       "name": "spaa-blank.pdf"
&#x20;                   },
&#x20;                   "linkedOn": "06/08/2023 06:09:06",
&#x20;                   "linkedBy": \{
&#x20;                       "userType": "API\_USER",
&#x20;                       "username": "passportqa+374732976396\@prth.com",
&#x20;                       "status": "ACTIVE"
&#x20;                   }
&#x20;               }
&#x20;           ],
&#x20;           "createdOn": "06/08/2023 06:09:05",
&#x20;           "createdBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "passportqa+374732976396\@prth.com",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "06/08/2023 06:11:10",
&#x20;           "isCustomerOwned": true,
&#x20;           "activationDate": "09/14/2023 06:09:46",
&#x20;           "isPrimary": false,
&#x20;           "totalCredit": \{
&#x20;               "amount": "0.00",
&#x20;               "asOn": "03/13/2024 05:23:47"
&#x20;           },
&#x20;           "totalDebit": \{
&#x20;               "amount": "0.00",
&#x20;               "asOn": "03/13/2024 05:23:47"
&#x20;           }
&#x20;       }
&#x20;   ]
}

## account.update

&#x20;&#x20;

\{
&#x20;   "id": 15140,
&#x20;   "eventType": "account.update",
&#x20;   "eventTimeStamp": "06/10/2024 19:08:33",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "account",
&#x20;           "url": "v1/customer/id/4007825/account/id/4003513",
&#x20;           "id": 4003513,
&#x20;           "externalId": "E22343422234125678654",
&#x20;           "nickName": "Jhon",
&#x20;           "accountNumber": "8125001200000346",
&#x20;           "status": "INACTIVE",
&#x20;           "statusReason": "PENDING\_VERIFICATION",
&#x20;           "statusDate": "06/08/2023 06:11:10",
&#x20;           "balance": \{
&#x20;               "amount": "0.00",
&#x20;               "asOn": "06/08/2023 06:11:26"
&#x20;           },
&#x20;           "availableBalance": \{
&#x20;               "amount": "0.00",
&#x20;               "asOn": "06/08/2023 06:11:26"
&#x20;           },
&#x20;           "purpose": "FEE",
&#x20;           "routableAccount": \{
&#x20;               "accountNumber": "76650000004347",
&#x20;               "routingNumber": "053101561",
&#x20;               "wireRoutingNumber": "122287251",
&#x20;               "wireAccountNumber": "13976650000004347",
&#x20;               "wireMemo": "Alex Johnson 13976650000004347",
&#x20;               "memo": "Alex Johnson 76650000004347"
&#x20;           },
&#x20;           "linkedDocument": \[
&#x20;               \{
&#x20;                   "id": 15339,
&#x20;                   "purpose": "AUTHORIZATION",
&#x20;                   "status": "PENDING\_VERIFICATION",
&#x20;                   "document": \{
&#x20;                       "resourceName": "document",
&#x20;                       "url": "/v1/document/id/4014696",
&#x20;                       "id": 4014696,
&#x20;                       "type": "SPAA",
&#x20;                       "name": "spaa-blank.pdf"
&#x20;                   },
&#x20;                   "linkedOn": "06/08/2023 06:09:06",
&#x20;                   "linkedBy": \{
&#x20;                       "userType": "API\_USER",
&#x20;                       "username": "passportqa+374732976396\@prth.com",
&#x20;                       "status": "ACTIVE"
&#x20;                   }
&#x20;               }
&#x20;           ],
&#x20;           "createdOn": "06/08/2023 06:09:05",
&#x20;           "createdBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "passportqa+374732976396\@prth.com",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
},
&#x20;           "lastUpdatedOn": "06/08/2023 06:11:10",
&#x20;           "isCustomerOwned": true,
&#x20;           "activationDate": "09/14/2023 06:09:46",
&#x20;           "isPrimary": false,
&#x20;           "totalCredit": \{
&#x20;               "amount": "0.00",
&#x20;               "asOn": "03/13/2024 05:23:47"
&#x20;           },
&#x20;           "totalDebit": \{
&#x20;               "amount": "0.00",
&#x20;               "asOn": "03/13/2024 05:23:47"
&#x20;           }
&#x20;       }
&#x20;   ]
}

## externalaccount.create

&#x20;&#x20;

\{
&#x20;  "id": 66031067,
&#x20;  "eventType": "externalaccount.create",
&#x20;   "eventTimeStamp": "06/10/2024 19:08:33",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "externalAccount",
&#x20;          "url": "/v1/customer/id/4227120/externalAccount/id/4020708",
&#x20;          "id": 4020708,
&#x20;          "externalId": "3454354376",
&#x20;          "holderName": "Ujjwal Patel",
&#x20;          "holderPhone": "870-736-2752",
&#x20;          "holderAddress": \{
&#x20;              "zip": "52142",
&#x20;              "city": "San diego",
&#x20;              "addressLine1": "3653",
&#x20;              "addressLine2": "Kingston",
&#x20;              "state": "NE"
&#x20;          },
&#x20;          "accountNumberLast4": "6488",
&#x20;          "encryptedAccountNumber": "LlvcjlqdXZ6ShVjQu+EEsQ==",
&#x20;          "routingNumber": "021210002",
&#x20;          "purpose": "Fee External Account",
&#x20;          "type": "SAVINGS",
&#x20;          "statusDate": "07/19/2024 07:26:41",
&#x20;          "statusReason": "External Account Pending Verification",
&#x20;          "verification": \{
&#x20;              "ofacStatus": "PENDING\_VERIFICATION",
&#x20;              "ofacStatusDate": "07/19/2024 07:26:41",
&#x20;              "ofacStatusReason": "Pending Verification"
&#x20;          },
&#x20;          "bankInfo": \{
&#x20;              "routingNumber": "021210002",
&#x20;              "address": "1460 VALLEY RD,WAYNE,NJ,07470",
&#x20;              "contactNumber": " ",
&#x20;              "name": "VALLEY NATIONAL BANK"
&#x20;          },
&#x20;          "validateAccount": \[
&#x20;              \{
&#x20;                  "ews": \{
&#x20;                      "statusDate": "07/19/2024 07:26:41",
&#x20;                      "statusReason": "PENDING",
&#x20;                      "status": "PENDING"
&#x20;                  }
&#x20;              }
&#x20;          ],
&#x20;          "microDeposit": \{
&#x20;              "microDepositValidation": "NEVER"
&#x20;          },
&#x20;          "prenote": \{
&#x20;              "prenoteValidation": "NEVER"
&#x20;          },
&#x20;          "createdBy": \{
&#x20;              "userType": "INTERNAL",
&#x20;              "username": "DEFAULT\_USER",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "createdOn": "07/19/2024 07:26:41",
&#x20;          "lastUpdatedOn": "07/19/2024 07:26:41",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "INTERNAL",
&#x20;              "username": "DEFAULT\_USER",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "holderType": "CORPORATE",
&#x20;          "status": "INACTIVE"
&#x20;      }
&#x20;  ]
}

## externalaccount.update

&#x20;&#x20;

\{
&#x20;  "id": 66031073,
&#x20;  "eventType": "externalaccount.update",
&#x20;  "eventTimeStamp": "06/10/2024 19:08:33",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "externalAccount",
&#x20;          "url": "/v1/customer/id/4227120/externalAccount/id/4020708",
&#x20;          "id": 4020708,
&#x20;          "externalId": "3454354376",
&#x20;          "holderName": "Ujjwal Patel",
&#x20;          "holderPhone": "870-736-2752",
&#x20;          "holderAddress": \{
&#x20;              "zip": "52142",
&#x20;              "city": "San diego",
&#x20;              "addressLine1": "3653",
&#x20;              "addressLine2": "Kingston",
&#x20;              "state": "NE"
&#x20;          },
&#x20;          "accountNumberLast4": "6488",
&#x20;          "purpose": "Fee External Account",
&#x20;          "type": "SAVINGS",
&#x20;          "statusReason": "External Account Pending Verification",
&#x20;          "verification": \{
&#x20;              "ofacStatus": "VERIFIED",
&#x20;              "ofacStatusDate": "07/19/2024 07:26:43",
&#x20;              "ofacStatusReason": "Verified"
&#x20;          },
&#x20;          "bankInfo": \{
&#x20;              "routingNumber": "021210002",
&#x20;              "address": "1460 VALLEY RD,WAYNE,NJ,07470",
&#x20;              "contactNumber": " ",
&#x20;              "name": "VALLEY NATIONAL BANK"
&#x20;          },
&#x20;          "validateAccount": \[
&#x20;              \{
&#x20;                  "ews": \{
&#x20;                      "statusDate": "07/19/2024 07:26:41",
&#x20;                      "statusReason": "PENDING",
&#x20;                      "status": "PENDING"
&#x20;                  }
&#x20;              }
&#x20;          ],
&#x20;          "microDeposit": \{
&#x20;              "microDepositValidation": "NEVER"
&#x20;          },
&#x20;          "prenote": \{
&#x20;              "prenoteValidation": "NEVER"
&#x20;          },
&#x20;          "encryptedAccountNumber": "LlvcjlqdXZ6ShVjQu+EEsQ==",
&#x20;          "routingNumber": "021210002",
&#x20;          "holderType": "CORPORATE",
&#x20;          "statusDate": "07/19/2024 07:26:41",
&#x20;          "status": "PENDING\_VERIFICATION",
&#x20;          "createdBy": \{
&#x20;              "userType": "INTERNAL",
&#x20;              "username": "DEFAULT\_USER",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "createdOn": "07/19/2024 07:26:41",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "SYSTEM",
&#x20;              "username": "SYSTEM",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "07/19/2024 07:26:43"
&#x20;      }
&#x20;  ]
}

## internationalexternalaccount.create

&#x20;&#x20;


* \*\*For USD International External Account\*\*  &#x20;&#x20;


  \{
  &#x20;  "id": 65819061,
  &#x20;  "eventType": "internationalexternalaccount.create",
  &#x20;  "eventTimeStamp": "06/21/2024 06:32:54",
  &#x20;  "eventId": "0001709618091430001",
  &#x20;  "eventCreated": 1747098180090,
  &#x20;  "payload": \[
  &#x20;      \{
  &#x20;          "url": "/v1/customer/id/4225975/internationalExternalAccount/id/4019518",
  &#x20;          "id": 4019518,
  &#x20;          "statusDate": "06/21/2024 06:32:54",
  &#x20;          "holderName": "Ujjwal patel",
  &#x20;          "purpose": "FEE",
  &#x20;          "swiftCode": "USBKUS44IMT",
  &#x20;          "holderAddress": \{
  &#x20;              "zip": "33126",
  &#x20;              "country": "AF",
  &#x20;              "city": "Miami",
  &#x20;              "addressLine1": "5505 Blue Lagoon Dr",
  &#x20;              "addressLine2": "Main St",
  &#x20;              "state": "NY"
  &#x20;          },
  &#x20;          "type": "CHECKING",
  &#x20;          "createdOn": "06/21/2024 06:32:54",
  &#x20;          "acceptedCurrency": \[
  &#x20;              "USD"
  &#x20;          ],
  &#x20;          "statusReason": "External Account Pending Verification",
  &#x20;          "accountNumberLast4": "3232",
  &#x20;          "createdBy": \{
  &#x20;              "userType": "CUSTOMER",
  &#x20;              "userName": "ujjwal.patel+362\@prth.com",
  &#x20;              "status": "ACTIVE"
  &#x20;          },
  &#x20;          "lastUpdatedBy": \{
  &#x20;              "userType": "CUSTOMER",
  &#x20;              "userName": "ujjwal.patel+362\@prth.com",
  &#x20;              "status": "ACTIVE"
  &#x20;          },
  &#x20;          "lastUpdatedOn": "06/21/2024 06:32:54",
  &#x20;          "holderType": "CORPORATE",
  &#x20;          "verification": \{
  &#x20;              "ofacStatus": "PENDING\_VERIFICATION",
  &#x20;              "ofacStatusDate": "06/21/2024 06:32:54",
  &#x20;              "ofacStatusReason": "Pending Verification"
  &#x20;          },
  &#x20;          "status": "INACTIVE"
  &#x20;      }
  &#x20;  ]
  }


  * \*\*For non- USD International External Account\*\*    &#x20;&#x20;

    \{
    &#x20;   "id": 67856626,
    &#x20;   "eventType": "internationalexternalaccount.create",
    &#x20;   "eventTimeStamp": "06/12/2025 06:04:10",
    &#x20;   "eventCreated": 1749708250797,
    &#x20;   "eventId": "0198840000000785690001",
    &#x20;   "payload": \[
    &#x20;       \{
    &#x20;           "url": "/v1/customer/id/4258731/internationalExternalAccount/id/4063258",
    &#x20;           "id": 4063258,
    &#x20;           "statusDate": "06/12/2025 06:04:09",
    &#x20;           "holderName": "Testing",
    &#x20;           "holderEmail": "abcd4175\@gmail.com",
    &#x20;           "purpose": "Testing1",
    &#x20;           "externalId": "ET2082237231121",
    &#x20;           "holderPhone": "812236216",
    &#x20;           "swiftCode": "BKCHCNBJXXX",
    &#x20;           "holderAddress": \{
    &#x20;               "zip": "T9X",
    &#x20;               "country": "CN",
    &#x20;               "city": "Albert",
    &#x20;               "addressLine1": "#1223, hazel street",
    &#x20;               "addressLine2": "Temple",
    &#x20;               "state": "CN"
    &#x20;           },
    &#x20;           "type": "CHECKING",
    &#x20;           "additionalDetail": \{
    &#x20;               "taxID": "2815"
    &#x20;           },
    &#x20;           "acceptedCurrency": \[
    &#x20;               "CNY"
    &#x20;           ],
    &#x20;           "statusReason": "External Account Pending Verification",
    &#x20;           "accountNumberLast4": "4512",
    &#x20;           "internationalRoutingCode": "92345",
    &#x20;           "holderType": "CORPORATE",
    &#x20;           "verification": \{
    &#x20;               "ofacStatus": "PENDING\_VERIFICATION",
    &#x20;               "ofacStatusDate": "06/12/2025 06:04:09",
    &#x20;               "ofacStatusReason": "Pending Verification"
    &#x20;           },
    &#x20;           "status": "INACTIVE",
    &#x20;           "lastUpdatedBy": \{
    &#x20;               "userType": "API\_USER",
    &#x20;               "userName": "nikhil.thakur+39340430393\@prth.com",
    &#x20;               "status": "ACTIVE"
    &#x20;           },
    &#x20;           "lastUpdatedOn": "06/12/2025 06:04:09",
    &#x20;           "createdOn": "06/12/2025 06:04:09",
    &#x20;           "createdBy": \{
    &#x20;               "userType": "API\_USER",
    &#x20;               "userName": "nikhil.thakur+39340430393\@prth.com",
    &#x20;               "status": "ACTIVE"
    &#x20;           }
    &#x20;       }
    &#x20;   ]
    }

## internationalexternalaccount.update

&#x20;&#x20;


* \*\*For USD International External Account\*\*  &#x20;&#x20;

  \{
  &#x20;  "id": 65819070,
  &#x20;  "eventType": "internationalexternalaccount.update",
  &#x20;  "eventTimeStamp": "06/10/2024 19:08:33",
  &#x20;  "eventId": "0001709618091430001",
  &#x20;  "eventCreated": 1747098180090,
  &#x20;  "payload": \[
  &#x20;      \{
  &#x20;          "url": "/v1/customer/id/4225975/internationalExternalAccount/id/4019518",
  &#x20;          "id": 4019518,
  &#x20;          "statusDate": "06/21/2024 06:32:54",
  &#x20;          "holderName": "Ujjwal patel",
  &#x20;          "purpose": "FEE",
  &#x20;          "swiftCode": "USBKUS44IMT",
  &#x20;          "holderAddress": \{
  &#x20;              "zip": "33126",
  &#x20;              "country": "AF",
  &#x20;              "city": "Miami",
  &#x20;              "addressLine1": "5505 Blue Lagoon Dr",
  &#x20;              "addressLine2": "Main St",
  &#x20;              "state": "NY"
  &#x20;          },
  &#x20;          "type": "CHECKING",
  &#x20;          "acceptedCurrency": \[
  &#x20;              "USD"
  &#x20;          ],
  &#x20;          "statusReason": "ACTIVE",
  &#x20;          "accountNumberLast4": "3232",
  &#x20;          "createdOn": "06/21/2024 06:32:54",
  &#x20;          "createdBy": \{
  &#x20;              "userType": "CUSTOMER",
  &#x20;              "userName": "ujjwal.patel+362\@prth.com",
  &#x20;              "status": "ACTIVE"
  &#x20;          },
  &#x20;          "lastUpdatedOn": "06/21/2024 06:37:41",
  &#x20;          "lastUpdatedBy": \{
  &#x20;              "userType": "CUSTOMER",
  &#x20;              "userName": "ujjwal.patel+362\@prth.com",
  &#x20;              "status": "ACTIVE"
  &#x20;          },
  &#x20;          "holderType": "CORPORATE",
  &#x20;          "verification": \{
  &#x20;              "ofacStatus": "VERIFIED",
  &#x20;              "ofacStatusDate": "06/21/2024 06:37:41",
  &#x20;              "ofacStatusReason": "Verified"
  &#x20;          },
  &#x20;          "status": "ACTIVE"
  &#x20;      }
  &#x20;  ]
  }


  * \*\*For non-USD International External Account\*\*    &#x20;&#x20;

    \{
    &#x20;   "id": 67856628,
    &#x20;   "eventType": "internationalexternalaccount.update",
    &#x20;   "eventTimeStamp": "06/12/2025 06:04:11",
    &#x20;   "eventCreated": 1749708251318,
    &#x20;   "eventId": "0198840000000838940001",
    &#x20;   "payload": \[
    &#x20;       \{
    &#x20;           "url": "/v1/customer/id/4258731/internationalExternalAccount/id/4063258",
    &#x20;           "id": 4063258,
    &#x20;           "holderName": "Testing",
    &#x20;           "holderEmail": "abcd4175\@gmail.com",
    &#x20;           "purpose": "Testing1",
    &#x20;           "externalId": "ET2082237231121",
    &#x20;           "holderPhone": "812236216",
    &#x20;           "swiftCode": "BKCHCNBJXXX",
    &#x20;           "holderAddress": \{
    &#x20;               "zip": "T9X",
    &#x20;               "country": "CN",
    &#x20;               "city": "Albert",
    &#x20;               "addressLine1": "#1223, hazel street",
    &#x20;               "addressLine2": "Temple",
    &#x20;               "state": "CN"
    &#x20;           },
    &#x20;           "type": "CHECKING",
    &#x20;           "additionalDetail": \{
    &#x20;               "taxID": "2815"
    &#x20;           },
    &#x20;           "acceptedCurrency": \[
    &#x20;               "CNY"
    &#x20;           ],
    &#x20;           "statusReason": "ACTIVE",
    &#x20;           "accountNumberLast4": "4512",
    &#x20;           "internationalRoutingCode": "92345",
    &#x20;           "holderType": "CORPORATE",
    &#x20;           "verification": \{
    &#x20;               "ofacStatus": "VERIFIED",
    &#x20;               "ofacStatusDate": "06/12/2025 06:04:11",
    &#x20;               "ofacStatusReason": "Verified"
    &#x20;           },
    &#x20;           "status": "ACTIVE",
    &#x20;           "statusDate": "06/12/2025 06:04:09",
    &#x20;           "createdOn": "06/12/2025 06:04:09",
    &#x20;           "createdBy": \{
    &#x20;               "userType": "API\_USER",
    &#x20;               "userName": "nikhil.thakur+39340430393\@prth.com",
    &#x20;               "status": "ACTIVE"
    &#x20;           },
    &#x20;           "lastUpdatedOn": "06/12/2025 06:04:11",
    &#x20;           "lastUpdatedBy": \{
    &#x20;               "userType": "API\_USER",
    &#x20;               "userName": "nikhil.thakur+39340430393\@prth.com",
    &#x20;               "status": "ACTIVE"
    &#x20;           }
    &#x20;       }
    &#x20;   ]
    }

## contact.create

&#x20;&#x20;

\{
&#x20;  "id": 65833765,
&#x20;  "eventType": "contact.create",
&#x20;  "eventTimeStamp": "06/10/2024 19:08:33",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "contact",
&#x20;          "url": "/v1/customer/id/4225975/contact/id/4014595",
&#x20;          "id": 4014595,
&#x20;          "legalName": "Thermo Pvt. Ltd",
&#x20;          "contactType": "BUSINESS",
&#x20;          "name": "Ujjwal Patel",
&#x20;          "email": "ujjwal.patel+386\@prth.com",
&#x20;          "externalAccount": \[
&#x20;              \{
&#x20;                  "statusDate": "06/27/2024 06:55:14",
&#x20;                  "bankInfo": \{
&#x20;                      "routingNumber": "021210002",
&#x20;                      "address": "1460 VALLEY RD,WAYNE,NJ,07470",
&#x20;                      "name": "VALLEY NATIONAL BANK",
&#x20;                      "contactNumber": " "
&#x20;                  },
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "holderName": "Thermo Pvt. Ltd",
&#x20;                  "purpose": "Fee",
&#x20;                  "validateAccount": \[
&#x20;                      \{
&#x20;                          "ews": \{
&#x20;                              "statusDate": "06/27/2024 06:55:14",
&#x20;                              "statusReason": "PENDING",
&#x20;                              "status": "PENDING"
&#x20;                          }
&#x20;                      }
&#x20;                  ],
&#x20;                  "microDeposit": \{
&#x20;                      "microDepositValidation": "NEVER"
&#x20;                  },
&#x20;                  "resourceName": "externalAccount",
&#x20;                  "type": "SAVINGS",
&#x20;                  "createdOn": "06/27/2024 06:55:14",
&#x20;                  "prenote": \{
&#x20;                      "prenoteValidation": "NEVER"
&#x20;                  },
&#x20;                  "routingNumber": "021210002",
&#x20;                  "isDefault": false,
&#x20;                  "statusReason": "External Account Pending Verification",
&#x20;                  "accountNumberLast4": "7289",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "lastUpdatedOn": "06/27/2024 06:55:14",
&#x20;                  "id": 4019819,
&#x20;                  "holderType": "CORPORATE",
&#x20;                  "verification": \{
&#x20;                      "ofacStatus": "PENDING\_VERIFICATION",
&#x20;                      "ofacStatusDate": "06/27/2024 06:55:14",
&#x20;                      "ofacStatusReason": "Pending Verification"
&#x20;                  },
&#x20;                  "status": "INACTIVE"
&#x20;              }
&#x20;          ],
&#x20;          "card": \[
&#x20;              \{
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "holderName": "Ujjwal  Patel",
&#x20;                  "expiryMonth": 6,
&#x20;                  "cardHolder": \{
&#x20;                      "firstName": "Ujjwal",
&#x20;                      "lastName": "Patel",
&#x20;                      "name": "Ujjwal  Patel"
&#x20;                  },
&#x20;                  "resourceName": "card",
&#x20;                  "expiryYear": 2025,
&#x20;                  "createdOn": "06/27/2024 06:55:14",
&#x20;                  "cardNumberLast4": "5578",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "lastUpdatedOn": "06/27/2024 06:55:14",
&#x20;                  "id": 10113014,
&#x20;                  "billingAddress": \{
&#x20;                      "zip": "12343",
&#x20;                      "city": "Kingston",
&#x20;                      "addressLine1": "309 Kingston Street",
&#x20;                      "addressLine2": "Chewbeka",
&#x20;                      "state": "AK"
&#x20;                  },
&#x20;                  "status": "ACTIVE"
&#x20;              }
&#x20;          ],
&#x20;          "internationalExternalAccount": \[
&#x20;              \{
&#x20;                  "statusDate": "06/27/2024 06:55:14",
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "holderName": "Ujjwal Patel",
&#x20;                  "purpose": "Fee",
&#x20;                  "swiftCode": "ARTSAM22XXX",
&#x20;                  "resourceName": "internationalExternalAccount",
&#x20;                  "holderAddress": \{
&#x20;                      "zip": "23433",
&#x20;                      "country": "AL",
&#x20;                      "city": "Arizona",
&#x20;                      "addressLine1": "5505 Blue Lagoon Dr",
&#x20;                      "addressLine2": "Mian",
&#x20;                      "state": "NY"
&#x20;                  },
&#x20;                  "type": "SAVINGS",
&#x20;                  "createdOn": "06/27/2024 06:55:14",
&#x20;                  "acceptedCurrency": \[
&#x20;                      "USD"
&#x20;                  ],
&#x20;                  "statusReason": "External Account Pending Verification",
&#x20;                  "accountNumberLast4": "3232",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "lastUpdatedOn": "06/27/2024 06:55:14",
&#x20;                  "id": 4019820,
&#x20;                  "holderType": "CORPORATE",
&#x20;                  "verification": \{
&#x20;                      "ofacStatus": "PENDING\_VERIFICATION",
&#x20;                      "ofacStatusDate": "06/27/2024 06:55:14",
&#x20;                      "ofacStatusReason": "Pending Verification"
&#x20;                  },
&#x20;                  "status": "INACTIVE"
&#x20;              }
&#x20;          ],
&#x20;          "mailingAddress": \[
&#x20;              \{
&#x20;                  "zip": "33126",
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "city": "Miami",
&#x20;                  "usage": \{
&#x20;                      "isPayorAddress": false
&#x20;                  },
&#x20;                  "resourceName": "address",
&#x20;                  "createdOn": "06/27/2024 06:55:14",
&#x20;                  "isDefault": false,
&#x20;                  "phone": "902-736-7234",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "countryCode": "1",
&#x20;                  "isPrimary": false,
&#x20;                  "name": "Thermo Pvt. Ltd",
&#x20;                  "addressLine1": "5505 Blue Lagoon Dr",
&#x20;                  "lastUpdatedOn": "06/27/2024 06:55:14",
&#x20;                  "addressLine2": "Main St",
&#x20;                  "id": 1176834,
&#x20;                  "state": "CO",
&#x20;                  "status": "ACTIVE"
&#x20;              }
&#x20;          ],
&#x20;          "createdOn": "06/27/2024 06:55:14",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/27/2024 06:55:14"
&#x20;      }
&#x20;  ]
}

## contact.update

&#x20;&#x20;

\{
&#x20;  "id": 65833782,
&#x20;  "eventType": "contact.update",
&#x20;  "eventTimeStamp": "06/27/2024 06:58:35",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "contact",
&#x20;          "url": "/v1/customer/id/4225975/contact/id/4014595",
&#x20;          "id": 4014595,
&#x20;          "name": "Ujjwal Patel",
&#x20;          "legalName": "Thermo Pvt. Ltd",
&#x20;          "email": "ujjwal.patel+386\@prth.com",
&#x20;          "externalAccount": \[
&#x20;              \{
&#x20;                  "statusDate": "06/27/2024 06:55:14",
&#x20;                  "bankInfo": \{
&#x20;                      "routingNumber": "021210002",
&#x20;                      "address": "1460 VALLEY RD,WAYNE,NJ,07470",
&#x20;                      "name": "VALLEY NATIONAL BANK",
&#x20;                      "contactNumber": " "
&#x20;                  },
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "SYSTEM",
&#x20;                      "username": "SYSTEM",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "holderName": "Thermo Pvt. Ltd",
&#x20;                  "purpose": "Fee",
&#x20;                  "validateAccount": \[
&#x20;                      \{
&#x20;                          "ews": \{
&#x20;                              "statusDate": "06/27/2024 06:55:14",
&#x20;                              "statusReason": "PENDING",
&#x20;                              "status": "PENDING"
&#x20;                          }
&#x20;                      }
&#x20;                  ],
&#x20;                  "microDeposit": \{
&#x20;                      "microDepositValidation": "NEVER"
&#x20;                  },
&#x20;                  "resourceName": "externalAccount",
&#x20;                  "type": "SAVINGS",
&#x20;                  "createdOn": "06/27/2024 06:55:14",
&#x20;                  "prenote": \{
&#x20;                      "prenoteValidation": "NEVER"
&#x20;                  },
&#x20;                  "routingNumber": "021210002",
&#x20;                  "isDefault": false,
&#x20;                  "statusReason": "External Account Pending Verification",
&#x20;                  "accountNumberLast4": "7289",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "lastUpdatedOn": "06/27/2024 06:58:33",
&#x20;                  "id": 4019819,
&#x20;                  "holderType": "CORPORATE",
&#x20;                  "verification": \{
&#x20;                      "ofacStatus": "VERIFIED",
&#x20;                      "ofacStatusDate": "06/27/2024 06:58:33",
&#x20;                      "ofacStatusReason": "Verified"
&#x20;                  },
&#x20;                  "status": "PENDING\_VERIFICATION"
&#x20;              }
&#x20;          ],
&#x20;          "card": \[
&#x20;              \{
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "holderName": "Ujjwal  Patel",
&#x20;                  "expiryMonth": 6,
&#x20;                  "cardHolder": \{
&#x20;                      "firstName": "Ujjwal",
&#x20;                      "lastName": "Patel",
&#x20;                      "name": "Ujjwal  Patel"
&#x20;                  },
&#x20;                  "resourceName": "card",
&#x20;                  "expiryYear": 2025,
&#x20;                  "createdOn": "06/27/2024 06:55:14",
&#x20;                  "cardNumberLast4": "5578",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "lastUpdatedOn": "06/27/2024 06:55:14",
&#x20;                  "id": 10113014,
&#x20;                  "billingAddress": \{
&#x20;                      "zip": "12343",
&#x20;                      "city": "Kingston",
&#x20;                      "addressLine1": "309 Kingston Street",
&#x20;                      "addressLine2": "Chewbeka",
&#x20;                      "state": "AK"
&#x20;                  },
&#x20;                  "status": "ACTIVE"
&#x20;              }
&#x20;          ],
&#x20;          "contactType": "BUSINESS",
&#x20;          "internationalExternalAccount": \[
&#x20;              \{
&#x20;                  "statusDate": "06/27/2024 06:55:14",
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "SYSTEM",
&#x20;                      "username": "SYSTEM",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "holderName": "Ujjwal Patel",
&#x20;                  "purpose": "Fee",
&#x20;                  "swiftCode": "ARTSAM22XXX",
&#x20;                  "resourceName": "internationalExternalAccount",
&#x20;                  "holderAddress": \{
&#x20;                      "zip": "23433",
&#x20;                      "country": "AL",
&#x20;                      "city": "Arizona",
&#x20;                      "addressLine1": "5505 Blue Lagoon Dr",
&#x20;                      "addressLine2": "Mian",
&#x20;                      "state": "NY"
&#x20;                  },
&#x20;                  "type": "SAVINGS",
&#x20;                  "createdOn": "06/27/2024 06:55:14",
&#x20;                  "acceptedCurrency": \[
&#x20;                      "USD"
&#x20;                  ],
&#x20;                  "statusReason": "ACTIVE",
&#x20;                  "accountNumberLast4": "3232",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "lastUpdatedOn": "06/27/2024 06:58:33",
&#x20;                  "id": 4019820,
&#x20;                  "holderType": "CORPORATE",
&#x20;                  "verification": \{
&#x20;                      "ofacStatus": "VERIFIED",
&#x20;                      "ofacStatusDate": "06/27/2024 06:58:33",
&#x20;                      "ofacStatusReason": "Verified"
&#x20;                  },
&#x20;                  "status": "ACTIVE"
&#x20;              }
&#x20;          ],
&#x20;          "mailingAddress": \[
&#x20;              \{
&#x20;                  "zip": "33126",
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "city": "Miami",
&#x20;                  "usage": \{
&#x20;                      "isPayorAddress": false
&#x20;                  },
&#x20;                  "resourceName": "address",
&#x20;                  "createdOn": "06/27/2024 06:55:14",
&#x20;                  "isDefault": false,
&#x20;                  "phone": "902-736-7234",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "countryCode": "1",
&#x20;                  "isPrimary": false,
&#x20;                  "name": "Thermo Pvt. Ltd",
&#x20;                  "addressLine1": "5505 Blue Lagoon Dr",
&#x20;                  "lastUpdatedOn": "06/27/2024 06:55:14",
&#x20;                  "addressLine2": "Main St",
&#x20;                  "id": 1176834,
&#x20;                  "state": "CO",
&#x20;                  "status": "ACTIVE"
&#x20;              }
&#x20;          ],
&#x20;          "createdOn": "06/27/2024 06:55:14",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/27/2024 06:55:14"
&#x20;      }
&#x20;  ]
}

## authorizeduser.create

&#x20;&#x20;

\{
&#x20;  "id": 65819811,
&#x20;  "eventType": "authorizeduser.create",
&#x20;  "eventTimeStamp": "06/21/2024 06:52:14",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,

&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "authorizedUser",
&#x20;          "url": "/v1/customer/id/4225975/authorizedUser/id/53520",
&#x20;          "id": 53520,
&#x20;          "firstName": "Ujjwal",
&#x20;          "lastName": "Patel",
&#x20;          "last4ssn": "7233",
&#x20;          "isUSCitizen": true,
&#x20;          "portalAccess": \{
&#x20;              "role": \[
&#x20;                  \{
&#x20;                      "lastUpdatedBy": \{
&#x20;                          "userType": "INTERNAL",
&#x20;                          "username": "DEFAULT\_USER",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "assignedBy": \{
&#x20;                          "userType": "CUSTOMER",
&#x20;                          "username": "ujjwal.patel+362\@prth.com",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "createdBy": \{
&#x20;                          "userType": "INTERNAL",
&#x20;                          "username": "DEFAULT\_USER",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "name": "admin",
&#x20;                      "lastUpdatedOn": "2024-06-14",
&#x20;                      "resourceName": "role",
&#x20;                      "roletype": "NON\_ADMIN",
&#x20;                      "assignedOn": "2024-06-21",
&#x20;                      "id": 11385,
&#x20;                      "createdOn": "2024-06-14",
&#x20;                      "url": "/v1/customer/id/4225975/role"
&#x20;                  }
&#x20;              ],
&#x20;              "grantAccess": true,
&#x20;              "username": "ujjwal.patel+281\_2\@prth.com"
&#x20;          },
&#x20;          "isBeneficialOwner": false,
&#x20;          "createdOn": "06/21/2024 06:52:14",
&#x20;          "userId": 4013084,
&#x20;          "mobilePhone": "938-726-7860",
&#x20;          "mailingAddress": \[
&#x20;              \{
&#x20;                  "zip": "66801",
&#x20;                  "city": "Miami",
&#x20;                  "isPrimary": true,
&#x20;                  "usage": \{
&#x20;                      "isPayorAddress": false
&#x20;                  },
&#x20;                  "addressLine1": "5505 Blue Lagoon Dr",
&#x20;                  "resourceName": "address",
&#x20;                  "addressLine2": "Main St",
&#x20;                  "id": 1176432,
&#x20;                  "state": "CT"
&#x20;              }
&#x20;          ],
&#x20;          "createdBy": \{
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "dob": "08/08/1998",
&#x20;          "countryCode": "91",
&#x20;          "lastUpdatedOn": "06/21/2024 06:52:14",
&#x20;          "email": "ujjwal.patel+281\_2\@prth.com",
&#x20;          "verification": \{
&#x20;              "ofacStatus": "PENDING\_VERIFICATION",
&#x20;              "cipStatus": "PENDING\_VERIFICATION",
&#x20;              "cipStatusDate": "06/21/2024 06:52:14",
&#x20;              "cipStatusReason": "PENDING\_VERIFICATION",
&#x20;              "ofacStatusDate": "06/21/2024 06:52:14",
&#x20;              "ofacStatusReason": "PENDING\_VERIFICATION"
&#x20;          },
&#x20;          "actAsAuthorizedSignatory": false
&#x20;      }
&#x20;  ]
}

## authorizeduser.update

&#x20;&#x20;

\{
&#x20;  "id": 65819815,
&#x20;  "eventType": "authorizeduser.update",
&#x20;  "eventTimeStamp": "06/21/2024 06:52:47",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,

&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "authorizedUser",
&#x20;          "url": "/v1/customer/id/4225975/authorizedUser/id/53520",
&#x20;          "id": 53520,
&#x20;          "firstName": "Ujjwal",
&#x20;          "lastName": "Patel",
&#x20;          "dob": "08/08/1998",
&#x20;          "countryCode": "91",
&#x20;          "mobilePhone": "938-726-7860",
&#x20;          "last4ssn": "7233",
&#x20;          "isUSCitizen": true,
&#x20;          "portalAccess": \{
&#x20;              "role": \[
&#x20;                  \{
&#x20;                      "lastUpdatedBy": \{
&#x20;                          "userType": "INTERNAL",
&#x20;                          "username": "DEFAULT\_USER",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "assignedBy": \{
&#x20;                          "userType": "CUSTOMER",
&#x20;                          "username": "ujjwal.patel+362\@prth.com",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "createdBy": \{
&#x20;                          "userType": "INTERNAL",
&#x20;                          "username": "DEFAULT\_USER",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "name": "admin",
&#x20;                      "lastUpdatedOn": "2024-06-14",
&#x20;                      "resourceName": "role",
&#x20;                      "roletype": "NON\_ADMIN",
&#x20;                      "assignedOn": "2024-06-21",
&#x20;                      "id": 11385,
&#x20;                      "createdOn": "2024-06-14",
&#x20;                      "url": "/v1/customer/id/4225975/role"
&#x20;                  }
&#x20;              ],
&#x20;              "grantAccess": true,
&#x20;              "username": "ujjwal.patel+281\_2\@prth.com"
&#x20;          },
&#x20;          "isBeneficialOwner": false,
&#x20;          "userId": 4013084,
&#x20;          "mailingAddress": \[
&#x20;              \{
&#x20;                  "zip": "66801",
&#x20;                  "city": "Miami",
&#x20;                  "isPrimary": true,
&#x20;                  "usage": \{
&#x20;                      "isPayorAddress": false
&#x20;                  },
&#x20;                  "addressLine1": "5505 Blue Lagoon Dr",
&#x20;                  "resourceName": "address",
&#x20;                  "addressLine2": "Main St",
&#x20;                  "id": 1176432,
&#x20;                  "state": "CT"
&#x20;              }
&#x20;          ],
&#x20;          "createdOn": "06/21/2024 06:52:14",
&#x20;          "createdBy": \{
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "username": "CIPWorkflowUser",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/21/2024 06:52:41",
&#x20;          "email": "ujjwal.patel+281\_2\@prth.com",
&#x20;          "verification": \{
&#x20;              "ofacStatus": "VERIFIED",
&#x20;              "cipStatus": "VERIFIED",
&#x20;              "cipStatusDate": "06/21/2024 06:52:41",
&#x20;              "cipStatusReason": "Verified",
&#x20;              "ofacStatusDate": "06/21/2024 06:52:47",
&#x20;              "ofacStatusReason": "Verified"
&#x20;          },
&#x20;          "actAsAuthorizedSignatory": false
&#x20;      }
&#x20;  ]
}

## mailingaddress.create

&#x20;&#x20;

\{
&#x20;  "id": 65816884,
&#x20;  "eventType": "mailingaddress.create",
&#x20;  "eventTimeStamp": "06/21/2024 05:26:29",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "address",
&#x20;          "url": "/v1/customer/id/4225975/mailingAddress/id/1176422",
&#x20;          "id": 1176422,
&#x20;          "externalId": "62367323",
&#x20;          "phone": "923-878-9743",
&#x20;          "isPrimary": true,
&#x20;          "name": "Ujjwal Patel",
&#x20;          "addressLine1": "637, Blue Lagoon",
&#x20;          "addressLine2": "Kingston",
&#x20;          "city": "Manhatton",
&#x20;          "state": "NY",
&#x20;          "zip": "56765",
&#x20;          "createdOn": "06/21/2024 05:26:29",
&#x20;          "createdBy": \{
&#x20;              "userType": "INTERNAL",
&#x20;              "username": "DEFAULT\_USER",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "INTERNAL",
&#x20;              "username": "DEFAULT\_USER",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/21/2024 05:26:29",
&#x20;          "usage": \{
&#x20;              "isPayorAddress": true
&#x20;          },
&#x20;          "status": "ACTIVE"
&#x20;      }
&#x20;  ]
}

## mailingaddress.update

&#x20;&#x20;

\{
&#x20;   "id": 65816882,
&#x20;   "eventType": "mailingaddress.update",
&#x20;   "eventTimeStamp": "06/21/2024 05:26:29",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "address",
&#x20;           "url": "/v1/customer/id/4225975/mailingAddress/id/1176242",
&#x20;           "id": 1176242,
&#x20;           "addressLine1": "5505 Blue Lagoon Dre",
&#x20;           "addressLine2": "Main St",
&#x20;           "city": "Miami",
&#x20;           "state": "DC",
&#x20;           "zip": "33126",
&#x20;           "isPrimary": false,
&#x20;           "usage": \{
&#x20;               "isPayorAddress": false
&#x20;           },
&#x20;           "createdOn": "06/14/2024 09:47:43",
&#x20;           "createdBy": \{
&#x20;               "userType": "CUSTOMER",
&#x20;               "username": "ujjwal.patel+361\_2\@prth.com",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "06/21/2024 05:26:29",
&#x20;           "status": "ACTIVE"
&#x20;       }
&#x20;   ]
&#x20;}

## transaction.ach.create

&#x20;&#x20;

\{
&#x20;  "id": 65816896,
&#x20;  "eventType": "transaction.ach.create",
&#x20;  "eventTimeStamp": "06/21/2024 05:34:15",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491504",
&#x20;          "id": 230491504,
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "status": "SCHEDULED",
&#x20;          "statusDate": "06/21/2024 05:34:15",
&#x20;          "amount": 23,
&#x20;          "allowDuplicate": true,
&#x20;          "method": "ACH",
&#x20;          "purpose": "Fee",
&#x20;          "nickName": "Checking",
&#x20;          "source": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915272,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915272"
&#x20;              }
&#x20;          },
&#x20;          "destination": \{
&#x20;              "externalAccount": \{
&#x20;                  "resourceName": "externalAccount",
&#x20;                  "id": 4019508,
&#x20;                  "url": "/v1/customer/id/4225975/externalAccount/id/4019508"
&#x20;              }
&#x20;          },
&#x20;          "type": "REGULAR",
&#x20;          "createdOn": "06/21/2024 05:34:15",
&#x20;          "transactionClass": "SEND",
&#x20;          "statusReason": "On User Request",
&#x20;          "processingDetail": \{
&#x20;              "quickSettle": false,
&#x20;              "addenda": \[
&#x20;                  ""
&#x20;              ],
&#x20;              "companyDescription": "Fee",
&#x20;              "authType": "WRITTEN",
&#x20;              "processingMode": "SAME\_DAY"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/21/2024 05:34:15",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          }
&#x20;      }
&#x20;  ]
}

## transaction.ach.update

&#x20;&#x20;

\{
&#x20;   "id": 65816902,
&#x20;   "eventType": "transaction.ach.update",
&#x20;   "eventTimeStamp": "06/21/2024 05:34:44",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "transaction",
&#x20;           "url": "/v1/customer/id/5784291/transaction/id/8376809",
&#x20;           "id": 8376809,
&#x20;           "statusDate": "05/08/2025 21:45:05",
&#x20;           "realizationDate": "05/08/2025 00:00:00",
&#x20;           "purpose": "Ach transaction",
&#x20;           "destination": \{
&#x20;               "account": \{
&#x20;                   "resourceName": "account",
&#x20;                   "id": 4537773,
&#x20;                   "url": "/v1/customer/id/5784291/account/id/4537773"
&#x20;               }
&#x20;           },
&#x20;           "source": \{
&#x20;               "externalAccount": \{
&#x20;                   "routingNumber": "084106768",
&#x20;                   "holderName": "Nicolai Eddy",
&#x20;                   "accountNumberLast4": "9145",
&#x20;                   "bankName": "EVOLVE BANK AND TRUST",
&#x20;                   "type": "CHECKING",
&#x20;                   "verification": \{
&#x20;                       "ofacStatus": "VERIFIED",
&#x20;                       "ofacStatusDate": "05/01/2025 22:57:18",
&#x20;                       "ofacStatusReason": "Verified"
&#x20;                   },
&#x20;                   "holderType": "CORPORATE"
&#x20;               }
&#x20;           },
&#x20;           "type": "REGULAR",
&#x20;           "statusReason": "Processed by System",
&#x20;           "methodType": "ACH\_SAME\_DAY",
&#x20;           "scheduleDate": "05/08/2025",
&#x20;           "amount": 25.66,
&#x20;           "allowDuplicate": true,
&#x20;           "method": "ACH",
&#x20;           "externalId": "PROD-3186856",
&#x20;           "transactionClass": "COLLECT",
&#x20;           "processingDetail": \{
&#x20;               "processedMode": "SAME\_DAY",
&#x20;               "traceNumber": "061121025802017",
&#x20;               "quickSettle": false,
&#x20;               "companyName": "NALA Inc.",
&#x20;               "companyDescription": "Fund walle",
&#x20;               "authType": "ONLINE",
&#x20;               "processingMode": "SAME\_DAY",
&#x20;               "iin": "F531860301"
&#x20;           },
&#x20;           "processDate": "05/08/2025 17:51:42",
&#x20;           "expectedCompletionDate": "05/08/2025",
&#x20;           "status": "COMPLETED",
&#x20;           "createdOn": "05/08/2025 16:01:30",
&#x20;           "createdBy": \{
&#x20;               "userType": "API\_USER",
&#x20;               "username": "API\@SILA.com",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "05/08/2025 21:45:05",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "SYSTEM",
&#x20;               "username": "SYSTEM",
&#x20;               "status": "ACTIVE"
&#x20;           }
&#x20;       }
&#x20;   ]
}

## transaction.check.create

&#x20;&#x20;

\{
&#x20;  "id": 65816890,
&#x20;  "eventType": "transaction.check.create",
&#x20;  "eventTimeStamp": "06/21/2024 05:32:22",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491503",
&#x20;          "id": 230491503,
&#x20;          "statusDate": "06/21/2024 05:32:22",
&#x20;          "amount": 73,
&#x20;          "allowDuplicate": false,
&#x20;          "method": "CHECK",
&#x20;          "purpose": "Fee",
&#x20;          "nickName": "Checking Account",
&#x20;          "destination": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking Account",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915275,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915275"
&#x20;              }
&#x20;          },
&#x20;          "type": "REGULAR",
&#x20;          "linkedDocument": \[
&#x20;              \{
&#x20;                  "purpose": "CHECK\_DEPOSIT",
&#x20;                  "linkedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "document": \{
&#x20;                      "name": "Check\_Front.jpg",
&#x20;                      "resourceName": "document",
&#x20;                      "id": 4054176,
&#x20;                      "type": "CHECK\_IMAGE\_FRONT",
&#x20;                      "url": "/v1/document/id/4054176"
&#x20;                  },
&#x20;                  "id": 44700,
&#x20;                  "linkedOn": "06/21/2024 05:32:22",
&#x20;                  "status": "PENDING\_VERIFICATION"
&#x20;              },
&#x20;              \{
&#x20;                  "purpose": "CHECK\_DEPOSIT",
&#x20;                  "linkedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "document": \{
&#x20;                      "name": "Check\_Back.jpg",
&#x20;                      "resourceName": "document",
&#x20;                      "id": 4054177,
&#x20;                      "type": "CHECK\_IMAGE\_BACK",
&#x20;                      "url": "/v1/document/id/4054177"
&#x20;                  },
&#x20;                  "id": 44701,
&#x20;                  "linkedOn": "06/21/2024 05:32:23",
&#x20;                  "status": "PENDING\_VERIFICATION"
&#x20;              }
&#x20;          ],
&#x20;          "transactionClass": "COLLECT",
&#x20;          "status": "SCHEDULED",
&#x20;          "statusReason": "On User Request",
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "processingDetail": \{
&#x20;              "quickSettle": false,
&#x20;              "checkVerification": \{
&#x20;                  "statusReason": "PENDING\_VERIFICATION",
&#x20;                  "checkDetail": \{},
&#x20;                  "status": "PENDING"
&#x20;              }
&#x20;          },
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "createdOn": "06/21/2024 05:32:22",
&#x20;          "lastUpdatedOn": "06/21/2024 05:32:22",
&#x20;          "expectedCompletionDate": "06/25/2024"
&#x20;      }
&#x20;  ]
}

## transaction.check.update

&#x20;&#x20;

\{
&#x20;  "id": 65816892,
&#x20;  "eventType": "transaction.check.update",
&#x20;  "eventTimeStamp": "06/21/2024 05:32:24",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491503",
&#x20;          "id": 230491503,
&#x20;          "status": "SCHEDULED",
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "statusDate": "06/21/2024 05:32:24",
&#x20;          "amount": 73,
&#x20;          "method": "CHECK",
&#x20;          "purpose": "Fee",
&#x20;          "nickName": "Checking Account",
&#x20;          "destination": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking Account",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915275,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915275"
&#x20;              }
&#x20;          },
&#x20;          "type": "REGULAR",
&#x20;          "linkedDocument": \[
&#x20;              \{
&#x20;                  "purpose": "CHECK\_DEPOSIT",
&#x20;                  "linkedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "document": \{
&#x20;                      "name": "Check\_Front.jpg",
&#x20;                      "resourceName": "document",
&#x20;                      "id": 4054176,
&#x20;                      "type": "CHECK\_IMAGE\_FRONT",
&#x20;                      "url": "/v1/document/id/4054176"
&#x20;                  },
&#x20;                  "id": 44700,
&#x20;                  "linkedOn": "06/21/2024 05:32:22",
&#x20;                  "status": "PENDING\_VERIFICATION"
&#x20;              },
&#x20;              \{
&#x20;                  "purpose": "CHECK\_DEPOSIT",
&#x20;                  "linkedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "document": \{
&#x20;                      "name": "Check\_Back.jpg",
&#x20;                      "resourceName": "document",
&#x20;                      "id": 4054177,
&#x20;                      "type": "CHECK\_IMAGE\_BACK",
&#x20;                      "url": "/v1/document/id/4054177"
&#x20;                  },
&#x20;                  "id": 44701,
&#x20;                  "linkedOn": "06/21/2024 05:32:23",
&#x20;                  "status": "PENDING\_VERIFICATION"
&#x20;              }
&#x20;          ],
&#x20;          "transactionClass": "COLLECT",
&#x20;          "statusReason": "Check amount mismatch",
&#x20;          "processingDetail": \{
&#x20;              "quickSettle": false,
&#x20;              "checkVerification": \{
&#x20;                  "statusReason": "IQA verified.",
&#x20;                  "checkDetail": \{
&#x20;                      "routingNumber": "121000015",
&#x20;                      "checkNumber": "602",
&#x20;                      "checkAmount": 3.95,
&#x20;                      "accountNumber": "998777-6655"
&#x20;                  },
&#x20;                  "status": "IQA\_VERIFIED"
&#x20;              }
&#x20;          },
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "createdOn": "06/21/2024 05:32:22",
&#x20;          "lastUpdatedOn": "06/21/2024 05:32:24",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "expectedCompletionDate": "06/25/2024"
&#x20;      }
&#x20;  ]
}

## transaction.card.create

&#x20;&#x20;

\{
&#x20;  "id": 65818336,
&#x20;  "eventType": "transaction.card.create",
&#x20;  "eventTimeStamp": "06/21/2024 06:23:33",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491510",
&#x20;          "id": 230491510,
&#x20;          "purpose": "Fee",
&#x20;          "method": "CARD",
&#x20;          "nickName": "Checking",
&#x20;          "source": \{
&#x20;              "card": \{
&#x20;                  "holderName": "Ujjwal Patel",
&#x20;                  "cardNumberLast4": "5578",
&#x20;                  "form": "VIRTUAL",
&#x20;                  "expiryMonth": 6,
&#x20;                  "cardType": "CREDIT",
&#x20;                  "expiryYear": 2025,
&#x20;                  "brand": "VISA"
&#x20;              }
&#x20;          },
&#x20;          "destination": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915272,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915272"
&#x20;              }
&#x20;          },
&#x20;          "type": "REGULAR",
&#x20;          "statusReason": "Payment Captured Successfully",
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "statusDate": "06/21/2024 06:23:33",
&#x20;          "amount": 23,
&#x20;          "authCode": "PPSf3a",
&#x20;          "allowDuplicate": true,
&#x20;          "isCaptured": true,
&#x20;          "transactionClass": "COLLECT",
&#x20;          "processingDetail": \{
&#x20;              "quickSettle": false,
&#x20;              "statementDescriptor": "PRT\*Thermo Pvt. Ltd-Transportation Fee",
&#x20;              "merchant": \{
&#x20;                  "resourceName": "merchant",
&#x20;                  "id": 4005758,
&#x20;                  "url": "/v1/customer/id/4225975/merchant/id/4005758"
&#x20;              },
&#x20;              "device": \{
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "inputCapability": "KEYED\_ONLY",
&#x20;                  "partialApprovalSupport": "NOT\_SUPPORTED",
&#x20;                  "transactionSecurity": "NORMAL",
&#x20;                  "createdOn": "06/21/2024",
&#x20;                  "accountCaptureMethod": "MANUAL",
&#x20;                  "cardholderPresence": "ECOM",
&#x20;                  "catLevel": "ECOM",
&#x20;                  "posId": "PP0001",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "lastUpdatedOn": "06/21/2024",
&#x20;                  "location": "HOME\_PC",
&#x20;                  "attendance": "HOME\_PC",
&#x20;                  "cardPresent": false
&#x20;              },
&#x20;              "order": \{
&#x20;                  "invoice": \{
&#x20;                      "number": "0000000001000000000097425",
&#x20;                      "lastUpdatedBy": \{
&#x20;                          "userType": "CUSTOMER",
&#x20;                          "username": "ujjwal.patel+362\@prth.com",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "lineItem": \[
&#x20;                          \{
&#x20;                              "productCode": "099",
&#x20;                              "quantity": 1,
&#x20;                              "unitOfMeasure": "EACH",
&#x20;                              "extendedAmount": 23,
&#x20;                              "unitCost": 23,
&#x20;                              "description": "Passport"
&#x20;                          }
&#x20;                      ],
&#x20;                      "shipmentDetail": \{
&#x20;                          "address": \{}
&#x20;                      },
&#x20;                      "createdBy": \{
&#x20;                          "userType": "CUSTOMER",
&#x20;                          "username": "ujjwal.patel+362\@prth.com",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "lastUpdatedOn": "06/21/2024",
&#x20;                      "createdOn": "06/21/2024"
&#x20;                  }
&#x20;              }
&#x20;          },
&#x20;          "processDate": "06/21/2024 06:23:33",
&#x20;          "isAutoCapture": true,
&#x20;          "expectedCompletionDate": "06/21/2024",
&#x20;          "pendingCaptureAmount": 0,
&#x20;          "status": "CAPTURED",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "createdOn": "06/21/2024 06:23:33",
&#x20;          "lastUpdatedOn": "06/21/2024 06:23:33",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          }
&#x20;      }
&#x20;  ]
}

## transaction.card.update

&#x20;&#x20;

\{
&#x20;  "id": 65818692,
&#x20;  "eventType": "transaction.card.update",
&#x20;  "eventTimeStamp": "06/21/2024 06:25:38",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491510",
&#x20;          "id": 230491510,
&#x20;          "type": "REGULAR",
&#x20;          "statusReason": "Incorrectly Charged",
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "amount": 23,
&#x20;          "authCode": "PPSf3a",
&#x20;          "allowDuplicate": true,
&#x20;          "method": "CARD",
&#x20;          "nickName": "Checking",
&#x20;          "statusDate": "06/21/2024 06:25:38",
&#x20;          "purpose": "Fee",
&#x20;          "source": \{
&#x20;              "card": \{
&#x20;                  "holderName": "Ujjwal Patel",
&#x20;                  "cardNumberLast4": "5578",
&#x20;                  "form": "VIRTUAL",
&#x20;                  "expiryMonth": 6,
&#x20;                  "cardType": "CREDIT",
&#x20;                  "expiryYear": 2025,
&#x20;                  "brand": "VISA"
&#x20;              }
&#x20;          },
&#x20;          "destination": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915272,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915272"
&#x20;              }
&#x20;          },
&#x20;          "isCaptured": true,
&#x20;          "transactionClass": "COLLECT",
&#x20;          "processingDetail": \{
&#x20;              "quickSettle": false,
&#x20;              "statementDescriptor": "PRT\*Thermo Pvt. Ltd-Transportation Fee",
&#x20;              "merchant": \{
&#x20;                  "resourceName": "merchant",
&#x20;                  "id": 4005758,
&#x20;                  "url": "/v1/customer/id/4225975/merchant/id/4005758"
&#x20;              },
&#x20;              "device": \{
&#x20;                  "lastUpdatedBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "inputCapability": "KEYED\_ONLY",
&#x20;                  "partialApprovalSupport": "NOT\_SUPPORTED",
&#x20;                  "transactionSecurity": "NORMAL",
&#x20;                  "createdOn": "06/21/2024",
&#x20;                  "accountCaptureMethod": "MANUAL",
&#x20;                  "cardholderPresence": "ECOM",
&#x20;                  "catLevel": "ECOM",
&#x20;                  "posId": "PP0001",
&#x20;                  "createdBy": \{
&#x20;                      "userType": "CUSTOMER",
&#x20;                      "username": "ujjwal.patel+362\@prth.com",
&#x20;                      "status": "ACTIVE"
&#x20;                  },
&#x20;                  "lastUpdatedOn": "06/21/2024",
&#x20;                  "location": "HOME\_PC",
&#x20;                  "attendance": "HOME\_PC",
&#x20;                  "cardPresent": false
&#x20;              },
&#x20;              "order": \{
&#x20;                  "invoice": \{
&#x20;                      "number": "0000000001000000000097425",
&#x20;                      "lastUpdatedBy": \{
&#x20;                          "userType": "CUSTOMER",
&#x20;                          "username": "ujjwal.patel+362\@prth.com",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "lineItem": \[
&#x20;                          \{
&#x20;                              "productCode": "099",
&#x20;                              "quantity": 1,
&#x20;                              "unitOfMeasure": "EACH",
&#x20;                              "extendedAmount": 23,
&#x20;                              "unitCost": 23,
&#x20;                              "description": "Passport"
&#x20;                          }
&#x20;                      ],
&#x20;                      "shipmentDetail": \{
&#x20;                          "address": \{}
&#x20;                      },
&#x20;                      "createdBy": \{
&#x20;                          "userType": "CUSTOMER",
&#x20;                          "username": "ujjwal.patel+362\@prth.com",
&#x20;                          "status": "ACTIVE"
&#x20;                      },
&#x20;                      "lastUpdatedOn": "06/21/2024",
&#x20;                      "createdOn": "06/21/2024"
&#x20;                  }
&#x20;              }
&#x20;          },
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "createdOn": "06/21/2024 06:23:33",
&#x20;          "lastUpdatedOn": "06/21/2024 06:25:38",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "processDate": "06/21/2024 06:23:33",
&#x20;          "isAutoCapture": true,
&#x20;          "expectedCompletionDate": "06/21/2024",
&#x20;          "pendingCaptureAmount": 0,
&#x20;          "status": "VOIDED"
&#x20;      }
&#x20;  ]
}

## transaction.wire.create

&#x20;&#x20;

\{
&#x20;  "id": 65817243,
&#x20;  "eventType": "transaction.wire.create",
&#x20;  "eventTimeStamp": "06/21/2024 05:36:10",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491505",
&#x20;          "id": 230491505,
&#x20;          "status": "SCHEDULED",
&#x20;          "amount": 2,
&#x20;          "allowDuplicate": false,
&#x20;          "method": "WIRE",
&#x20;          "purpose": "Fee",
&#x20;          "nickName": "Checking",
&#x20;          "destination": \{
&#x20;              "externalAccount": \{
&#x20;                  "resourceName": "externalAccount",
&#x20;                  "id": 4019508,
&#x20;                  "url": "/v1/customer/id/4225975/externalAccount/id/4019508"
&#x20;              }
&#x20;          },
&#x20;          "source": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915272,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915272"
&#x20;              }
&#x20;          },
&#x20;          "type": "REGULAR",
&#x20;          "transactionClass": "SEND",
&#x20;          "statusReason": "On User Request",
&#x20;          "processingDetail": \{
&#x20;              "memo": "Fee"
&#x20;          },
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "statusDate": "06/21/2024 05:36:10",
&#x20;          "createdOn": "06/21/2024 05:36:10",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/21/2024 05:36:10"
&#x20;      }
&#x20;  ]
}

## transaction.wire.update

&#x20;&#x20;

\{
&#x20;  "id": 65818671,
&#x20;  "eventType": "transaction.wire.update",
&#x20;  "eventTimeStamp": "06/21/2024 06:24:55",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491505",
&#x20;          "id": 230491505,
&#x20;          "type": "REGULAR",
&#x20;          "method": "WIRE",
&#x20;          "purpose": "Fee",
&#x20;          "nickName": "Checking",
&#x20;          "status": "PENDING",
&#x20;          "statusDate": "06/21/2024 06:24:55",
&#x20;          "amount": 21,
&#x20;          "allowDuplicate": false,
&#x20;          "source": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915272,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915272"
&#x20;              }
&#x20;          },
&#x20;          "destination": \{
&#x20;              "externalAccount": \{
&#x20;                  "resourceName": "externalAccount",
&#x20;                  "id": 4019508,
&#x20;                  "url": "/v1/customer/id/4225975/externalAccount/id/4019508"
&#x20;              }
&#x20;          },
&#x20;          "transactionClass": "SEND",
&#x20;          "statusReason": "External Account Pending Verification",
&#x20;          "processingDetail": \{
&#x20;              "memo": "Fee"
&#x20;          },
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "createdOn": "06/21/2024 05:36:10",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "SYSTEM",
&#x20;              "username": "SYSTEM",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/21/2024 06:24:55"
&#x20;      }
&#x20;  ]
}

## transaction.internationalwire.create

&#x20;&#x20;


* \*\*For USD International External Account\*\*  &#x20;&#x20;

  \{
  &#x20;  "id": 65819088,
  &#x20;  "eventType": "transaction.internationalwire.create",
  &#x20;  "eventTimeStamp": "06/21/2024 06:45:31",
  &#x20;  "eventId": "0001709618091430001",
  &#x20;  "eventCreated": 1747098180090,
  &#x20;  "payload": \[
  &#x20;      \{
  &#x20;          "resourceName": "transaction",
  &#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491516",
  &#x20;          "id": 230491516,
  &#x20;          "status": "SCHEDULED",
  &#x20;          "amount": 23,
  &#x20;          "allowDuplicate": false,
  &#x20;          "method": "INTERNATIONAL\_WIRE",
  &#x20;          "purpose": "Fee",
  &#x20;          "nickName": "Checking",
  &#x20;          "source": \{
  &#x20;              "account": \{
  &#x20;                  "nickName": "Checking",
  &#x20;                  "resourceName": "account",
  &#x20;                  "id": 9915327,
  &#x20;                  "url": "/v1/customer/id/4225975/account/id/9915327"
  &#x20;              }
  &#x20;          },
  &#x20;          "destination": \{
  &#x20;              "internationalExternalAccount": \{
  &#x20;                  "resourceName": "internationalExternalAccount",
  &#x20;                  "id": 4019518,
  &#x20;                  "url": "/v1/customer/id/4225975/internationalExternalAccount/id/4019518"
  &#x20;              }
  &#x20;          },
  &#x20;          "type": "REGULAR",
  &#x20;          "transactionClass": "SEND",
  &#x20;          "statusReason": "On User Request",
  &#x20;          "processingDetail": \{
  &#x20;              "memo": "Transportation Fee"
  &#x20;          },
  &#x20;          "scheduleDate": "06/21/2024",
  &#x20;          "currency": "USD",
  &#x20;          "statusDate": "06/21/2024 06:45:31",
  &#x20;          "createdOn": "06/21/2024 06:45:31",
  &#x20;          "createdBy": \{
  &#x20;              "userType": "CUSTOMER",
  &#x20;              "username": "ujjwal.patel+362\@prth.com",
  &#x20;              "status": "ACTIVE"
  &#x20;          },
  &#x20;          "lastUpdatedOn": "06/21/2024 06:45:31",
  &#x20;          "lastUpdatedBy": \{
  &#x20;              "userType": "CUSTOMER",
  &#x20;              "username": "ujjwal.patel+362\@prth.com",
  &#x20;              "status": "ACTIVE"
  &#x20;          }
  &#x20;      }
  &#x20;  ]
  }


  * \*\*For non - USD International External Account\*\*    &#x20;&#x20;


    \{
    &#x20;   "id": 67863490,
    &#x20;   "eventType": "transaction.internationalwire.create",
    &#x20;   "eventId": "0201640000000584310001",
    &#x20;   "payload": \[
    &#x20;       \{
    &#x20;           "statusDate": "06/13/2025 05:14:44",
    &#x20;           "purpose": "charges",
    &#x20;           "destination": \{
    &#x20;               "internationalExternalAccount": \{
    &#x20;                   "resourceName": "internationalExternalAccount",
    &#x20;                   "id": 4063347,
    &#x20;                   "url": "/v1/customer/id/4258731/internationalExternalAccount/id/4063347"
    &#x20;               }
    &#x20;           },
    &#x20;           "source": \{
    &#x20;               "account": \{
    &#x20;                   "resourceName": "account",
    &#x20;                   "id": 9939650,
    &#x20;                   "url": "/v1/customer/id/4258731/account/id/9939650"
    &#x20;               }
    &#x20;           },
    &#x20;           "type": "REGULAR",
    &#x20;           "createdOn": "06/13/2025 05:14:44",
    &#x20;           "amountOriginType": "DESTINATION",
    &#x20;           "statusReason": "On User Request",
    &#x20;           "methodType": "WIRE",
    &#x20;           "scheduleDate": "06/13/2025",
    &#x20;           "lastUpdatedOn": "06/13/2025 05:14:44",
    &#x20;           "currency": "CNY",
    &#x20;           "id": 230558472,
    &#x20;           "lastUpdatedBy": \{
    &#x20;               "userType": "API\_USER",
    &#x20;               "username": "nikhil.thakur+39340430393\@prth.com",
    &#x20;               "status": "ACTIVE"
    &#x20;           },
    &#x20;           "amount": 12.5,
    &#x20;           "allowDuplicate": true,
    &#x20;           "method": "INTERNATIONAL\_WIRE",
    &#x20;           "isTaxPayment": false,
    &#x20;           "externalId": "ET2342234832",
    &#x20;           "resourceName": "transaction",
    &#x20;           "url": "/v1/customer/id/4258731/transaction/id/230558472",
    &#x20;           "transactionClass": "SEND",
    &#x20;           "processingDetail": \{
    &#x20;               "fxQuote": \{
    &#x20;                   "fxRate": "0.140747",
    &#x20;                   "fee": 0,
    &#x20;                   "destination": \{
    &#x20;                       "amount": 12.5,
    &#x20;                       "currency": "CNY"
    &#x20;                   },
    &#x20;                   "resourceName": "fxQuote",
    &#x20;                   "id": 90,
    &#x20;                   "source": \{
    &#x20;                       "amount": 1.76,
    &#x20;                       "currency": "USD"
    &#x20;                   },
    &#x20;                   "url": "/v1/customer/id/4258731/transaction/fxQuote/id/90"
    &#x20;               },
    &#x20;               "memo": "transaction"
    &#x20;           },
    &#x20;           "createdBy": \{
    &#x20;               "userType": "API\_USER",
    &#x20;               "username": "nikhil.thakur+39340430393\@prth.com",
    &#x20;               "status": "ACTIVE"
    &#x20;           },
    &#x20;           "status": "SCHEDULED"
    &#x20;       }
    &#x20;   ],
    &#x20;   "eventTimeStamp": "06/13/2025 05:14:44",
    &#x20;   "eventCreated": 1749791684805
    }

## ransaction.internationalwire.update

&#x20;&#x20;


* \*\*For USD International External Account\*\*  &#x20;&#x20;

  \{
  &#x20;  "id": 65819256,
  &#x20;  "eventType": "transaction.internationalwire.update",
  &#x20;  "eventTimeStamp": "06/21/2024 06:46:34",
  &#x20;  "eventId": "0001709618091430001",
  &#x20;  "eventCreated": 1747098180090,
  &#x20;  "payload": \[
  &#x20;      \{
  &#x20;          "resourceName": "transaction",
  &#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491516",
  &#x20;          "id": 230491516,
  &#x20;          "status": "PROCESSING",
  &#x20;          "amount": 23,
  &#x20;          "allowDuplicate": false,
  &#x20;          "method": "INTERNATIONAL\_WIRE",
  &#x20;          "purpose": "Fee",
  &#x20;          "nickName": "Checking",
  &#x20;          "source": \{
  &#x20;              "account": \{
  &#x20;                  "nickName": "Checking",
  &#x20;                  "resourceName": "account",
  &#x20;                  "id": 9915327,
  &#x20;                  "url": "/v1/customer/id/4225975/account/id/9915327"
  &#x20;              }
  &#x20;          },
  &#x20;          "destination": \{
  &#x20;              "internationalExternalAccount": \{
  &#x20;                  "resourceName": "internationalExternalAccount",
  &#x20;                  "id": 4019518,
  &#x20;                  "url": "/v1/customer/id/4225975/internationalExternalAccount/id/4019518"
  &#x20;              }
  &#x20;          },
  &#x20;          "type": "REGULAR",
  &#x20;          "transactionClass": "SEND",
  &#x20;          "statusReason": "Processing In Transit",
  &#x20;          "currency": "USD",
  &#x20;          "statusDate": "06/21/2024 06:46:34",
  &#x20;          "processingDetail": \{
  &#x20;              "memo": "Transportation Fee",
  &#x20;              "originator": "Thermo Pvt. Ltd c/o Finxera"
  &#x20;          },
  &#x20;          "processDate": "06/21/2024 06:46:33",
  &#x20;          "scheduleDate": "06/21/2024",
  &#x20;          "createdOn": "06/21/2024 06:45:31",
  &#x20;          "createdBy": \{
  &#x20;              "userType": "CUSTOMER",
  &#x20;              "username": "ujjwal.patel+362\@prth.com",
  &#x20;              "status": "ACTIVE"
  &#x20;          },
  &#x20;          "lastUpdatedOn": "06/21/2024 06:46:34",
  &#x20;          "lastUpdatedBy": \{
  &#x20;              "userType": "SYSTEM",
  &#x20;              "username": "SYSTEM",
  &#x20;              "status": "ACTIVE"
  &#x20;          }
  &#x20;      }
  &#x20;  ]
  }


  * \*\*For non-USD International External Account\*\*    &#x20;&#x20;

    \{
    &#x20;   "id": 67863492,
    &#x20;   "eventType": "transaction.internationalwire.update",
    &#x20;   "eventId": "0201650000000303880001",
    &#x20;   "payload": \[
    &#x20;       \{
    &#x20;           "statusDate": "06/13/2025 05:14:44",
    &#x20;           "purpose": "fees for payment",
    &#x20;           "destination": \{
    &#x20;               "internationalExternalAccount": \{
    &#x20;                   "resourceName": "internationalExternalAccount",
    &#x20;                   "id": 4063347,
    &#x20;                   "url": "/v1/customer/id/4258731/internationalExternalAccount/id/4063347"
    &#x20;               }
    &#x20;           },
    &#x20;           "source": \{
    &#x20;               "account": \{
    &#x20;                   "resourceName": "account",
    &#x20;                   "id": 9939650,
    &#x20;                   "url": "/v1/customer/id/4258731/account/id/9939650"
    &#x20;               }
    &#x20;           },
    &#x20;           "type": "REGULAR",
    &#x20;           "createdOn": "06/13/2025 05:14:44",
    &#x20;           "amountOriginType": "DESTINATION",
    &#x20;           "statusReason": "On User Request",
    &#x20;           "methodType": "WIRE",
    &#x20;           "scheduleDate": "06/13/2025",
    &#x20;           "lastUpdatedOn": "06/13/2025 05:19:56",
    &#x20;           "currency": "CNY",
    &#x20;           "id": 230558472,
    &#x20;           "lastUpdatedBy": \{
    &#x20;               "userType": "API\_USER",
    &#x20;               "username": "nikhil.thakur+39340430393\@prth.com",
    &#x20;               "status": "ACTIVE"
    &#x20;           },
    &#x20;           "amount": 12.5,
    &#x20;           "allowDuplicate": true,
    &#x20;           "method": "INTERNATIONAL\_WIRE",
    &#x20;           "isTaxPayment": false,
    &#x20;           "externalId": "ET2342234832",
    &#x20;           "resourceName": "transaction",
    &#x20;           "url": "/v1/customer/id/4258731/transaction/id/230558472",
    &#x20;           "transactionClass": "SEND",
    &#x20;           "processingDetail": \{
    &#x20;               "fxQuote": \{
    &#x20;                   "fxRate": "0.140747",
    &#x20;                   "fee": 0,
    &#x20;                   "destination": \{
    &#x20;                       "amount": 12.5,
    &#x20;                       "currency": "CNY"
    &#x20;                   },
    &#x20;                   "resourceName": "fxQuote",
    &#x20;                   "id": 90,
    &#x20;                   "source": \{
    &#x20;                       "amount": 1.76,
    &#x20;                       "currency": "USD"
    &#x20;                   },
    &#x20;                   "url": "/v1/customer/id/4258731/transaction/fxQuote/id/90"
    &#x20;               },
    &#x20;               "memo": "transaction"
    &#x20;           },
    &#x20;           "createdBy": \{
    &#x20;               "userType": "API\_USER",
    &#x20;               "username": "nikhil.thakur+39340430393\@prth.com",
    &#x20;               "status": "ACTIVE"
    &#x20;           },
    &#x20;           "status": "SCHEDULED"
    &#x20;       }
    &#x20;   ],
    &#x20;   "eventTimeStamp": "06/13/2025 05:19:56",
    &#x20;   "eventCreated": 1749791996755
    }

## transaction.book.create

&#x20;&#x20;

\{
&#x20;  "id": 65835612,
&#x20;  "eventType": "transaction.book.create",
&#x20;  "eventTimeStamp": "06/28/2024 11:37:23",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491671",
&#x20;          "id": 230491671,
&#x20;          "statusDate": "06/28/2024 11:37:23",
&#x20;          "amount": 10,
&#x20;          "allowDuplicate": true,
&#x20;          "method": "BOOK",
&#x20;          "processInstantly": false,
&#x20;          "purpose": "Fee",
&#x20;          "nickName": "Checking",
&#x20;          "source": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915327,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915327"
&#x20;              }
&#x20;          },
&#x20;          "destination": \{
&#x20;              "account": \{
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915275,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915275"
&#x20;              }
&#x20;          },
&#x20;          "type": "REGULAR",
&#x20;          "status": "SCHEDULED",
&#x20;          "transactionClass": "SEND",
&#x20;          "statusReason": "On User Request",
&#x20;          "processingDetail": \{
&#x20;              "memo": "Fee"
&#x20;          },
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "scheduleDate": "06/28/2024",
&#x20;          "createdOn": "06/28/2024 11:37:23",
&#x20;          "lastUpdatedOn": "06/28/2024 11:37:23",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          }
&#x20;      }
&#x20;  ]
}

## transaction.book.update

&#x20;&#x20;

\{
&#x20;  "id": 65835625,
&#x20;  "eventType": "transaction.book.update",
&#x20;  "eventTimeStamp": "06/28/2024 11:38:44",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491507",
&#x20;          "id": 230491507,
&#x20;          "statusDate": "06/28/2024 11:38:44",
&#x20;          "amount": 3,
&#x20;          "allowDuplicate": true,
&#x20;          "method": "BOOK",
&#x20;          "processInstantly": true,
&#x20;          "purpose": "Account Setup",
&#x20;          "nickName": "Checking",
&#x20;          "source": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915326,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915326"
&#x20;              }
&#x20;          },
&#x20;          "destination": \{
&#x20;              "account": \{
&#x20;                  "resourceName": "account",
&#x20;                  "id": 4003201,
&#x20;                  "url": "/v1/customer/id/423062/account/id/4003201"
&#x20;              }
&#x20;          },
&#x20;          "type": "REGULAR",
&#x20;          "status": "COMPLETED",
&#x20;          "transactionClass": "SYSTEM\_FEE",
&#x20;          "statusReason": "Processed by System",
&#x20;          "createdBy": \{
&#x20;              "userType": "SYSTEM",
&#x20;              "username": "SYSTEM",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "createdOn": "06/21/2024 05:58:53",
&#x20;          "processDate": "06/28/2024 11:38:44",
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "lastUpdatedOn": "06/28/2024 11:38:44",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "SYSTEM",
&#x20;              "username": "SYSTEM",
&#x20;              "status": "ACTIVE"
&#x20;          }
&#x20;      }
&#x20;  ]
}

## transaction.virtualcard.create

&#x20;&#x20;

\{
&#x20;  "id": 65819444,
&#x20;  "eventType": "transaction.virtualcard.create",
&#x20;  "eventTimeStamp": "06/21/2024 06:48:36",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491517",
&#x20;          "id": 230491517,
&#x20;          "statusDate": "06/21/2024 06:48:36",
&#x20;          "amount": 2,
&#x20;          "allowDuplicate": false,
&#x20;          "method": "VIRTUAL\_CARD",
&#x20;          "purpose": "Fee",
&#x20;          "nickName": "Checking",
&#x20;          "source": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915327,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915327"
&#x20;              }
&#x20;          },
&#x20;          "destination": \{
&#x20;              "email": "kavya.sharma+100\@prth.com"
&#x20;          },
&#x20;          "type": "REGULAR",
&#x20;          "transactionClass": "SEND",
&#x20;          "statusReason": "On User Request",
&#x20;          "processingDetail": \{
&#x20;              "virtualCard": \{
&#x20;                  "resourceName": "virtualCard",
&#x20;                  "id": 901011645,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915327/virtualCard/id/901011645"
&#x20;              }
&#x20;          },
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "status": "SCHEDULED",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "createdOn": "06/21/2024 06:48:36",
&#x20;          "lastUpdatedOn": "06/21/2024 06:48:36",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          }
&#x20;      }
&#x20;  ]
}

## transaction.virtualcard.update

&#x20;&#x20;

\{
&#x20;  "id": 65819800,
&#x20;  "eventType": "transaction.virtualcard.update",
&#x20;  "eventTimeStamp": "06/21/2024 06:49:33",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "transaction",
&#x20;          "url": "/v1/customer/id/4225975/transaction/id/230491517",
&#x20;          "id": 230491517,
&#x20;          "amount": 2,
&#x20;          "allowDuplicate": false,
&#x20;          "method": "VIRTUAL\_CARD",
&#x20;          "purpose": "Fee",
&#x20;          "nickName": "Checking",
&#x20;          "source": \{
&#x20;              "account": \{
&#x20;                  "nickName": "Checking",
&#x20;                  "resourceName": "account",
&#x20;                  "id": 9915327,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915327"
&#x20;              }
&#x20;          },
&#x20;          "destination": \{
&#x20;              "email": "kavya.sharma+100\@prth.com"
&#x20;          },
&#x20;          "type": "REGULAR",
&#x20;          "transactionClass": "SEND",
&#x20;          "statusReason": "Processing In Transit",
&#x20;          "processingDetail": \{
&#x20;              "virtualCard": \{
&#x20;                  "resourceName": "virtualCard",
&#x20;                  "id": 901011645,
&#x20;                  "url": "/v1/customer/id/4225975/account/id/9915327/virtualCard/id/901011645"
&#x20;              }
&#x20;          },
&#x20;          "processDate": "06/21/2024 06:49:31",
&#x20;          "scheduleDate": "06/21/2024",
&#x20;          "status": "PROCESSING",
&#x20;          "statusDate": "06/21/2024 06:49:31",
&#x20;          "createdOn": "06/21/2024 06:48:36",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+362\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/21/2024 06:49:31",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "SYSTEM",
&#x20;              "username": "SYSTEM",
&#x20;              "status": "ACTIVE"
&#x20;          }
&#x20;      }
&#x20;  ]
}

## ledger.create

&#x20;&#x20;

For ACH transaction:&#x20;
\{
&#x20;   "id": 67810538,
&#x20;   "eventCreated": 1748425349095,
&#x20;   "eventType": "ledger.create",
&#x20;   "eventTimeStamp": "05/28/2025 09:42:29",
&#x20;   "eventId": "0159110000000183330002",
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "id": 3613372,
&#x20;           "amount": 5400,
&#x20;           "account": \{
&#x20;               "resourceName": "account",
&#x20;               "id": 9917435,
&#x20;               "url": "/v1/customer/id/4228222/account/id/9917435"
&#x20;           },
&#x20;           "ledgerDate": "05/28/2025",
&#x20;           "method": "ACH",
&#x20;           "groupId": "230556705T",
&#x20;           "type": "CREDIT",
&#x20;           "narration": "Deposit from \*7288 fEE Ref: 230556705",
&#x20;           "schedule": \{
&#x20;               "resourceName": "transaction",
&#x20;               "id": 230556705,
&#x20;               "url": "/v1/transaction/id/230556705"
&#x20;           },
&#x20;           "scheduleClass": "COLLECT",
&#x20;           "createdOn": "05/28/2025 09:42:29",
&#x20;           "createdBy": \{
&#x20;               "userType": "SYSTEM",
&#x20;               "username": "SYSTEM",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "SYSTEM",
&#x20;               "username": "SYSTEM",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "05/28/2025 09:42:29"
&#x20;       }
&#x20;   ]
}
For Debit Card:&#x20;
\{
&#x20;   "id": 570719385,
&#x20;   "eventType": "ledger.create",
&#x20;   "eventTimeStamp": "05/28/2025 19:08:51",
&#x20;   "eventCreated": 1748459331990,
&#x20;   "eventId": "3934530000003903500002",
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "id": 14911785,
&#x20;           "amount": 5,
&#x20;           "ledgerDate": "05/28/2025",
&#x20;           "method": "CARD",
&#x20;           "account": \{
&#x20;               "resourceName": "account",
&#x20;               "id": 4350958,
&#x20;               "url": "/v1/customer/id/5686406/account/id/4350958"
&#x20;           },
&#x20;           "narration": "Pending To \*3440 - BIRD APP\* PENDING.BIRD +18662052442 FLUS",
&#x20;           "groupId": "1030648CET",
&#x20;           "type": "DEBIT",
&#x20;           "ledgerType": "HOLD",
&#x20;           "createdOn": "05/28/2025 19:08:51",
&#x20;           "createdBy": \{
&#x20;               "userType": "SYSTEM",
&#x20;               "username": "SYSTEM",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "05/28/2025 19:08:51",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "SYSTEM",
&#x20;               "username": "SYSTEM",
&#x20;               "status": "ACTIVE"
&#x20;           }
&#x20;       }
&#x20;   ]
}

## debitcard.create

&#x20;&#x20;

For "Expose Debit card sensitive data" setting as TRUE

\{
&#x20;  "id": 1363188,
&#x20;  "eventType": "debitcard.create",
&#x20;  "eventTimeStamp": "06/27/2024 09:36:24",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "debitCard",
&#x20;          "url": "v1/customer/id/4049187/account/id/4034426/debitCard/id/610",
&#x20;          "id": 610,
&#x20;          "statusDate": "06/27/2024 09:36:24",
&#x20;          "cardHolder": \{
&#x20;              "name": "Ujjwal Patel",
&#x20;              "id": 115203,
&#x20;              "type": "BENEFICIAL\_OWNER"
&#x20;          },
&#x20;          "type": "PLASTIC",
&#x20;          "cardProgram": "PM CORP STD PB PL CARD2pGLBQ",
&#x20;          "shippingDetail": \{
&#x20;              "address": \{
&#x20;                  "zip": "33126",
&#x20;                  "city": "Miami",
&#x20;                  "addressLine1": "5505 Blue Lagoon Dr",
&#x20;                  "addressLine2": "",
&#x20;                  "id": 1206720,
&#x20;                  "state": "CO",
&#x20;                  "status": "ACTIVE"
&#x20;              },
&#x20;              "expressDelivery": true
&#x20;          },
&#x20;          "status": "PENDING",
&#x20;          "statusReason": "Debit Card Request submitted",
&#x20;          "properties": \{
&#x20;              "isDigitalFirst": false
&#x20;          },
&#x20;          "createdOn": "06/27/2024 09:36:24",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+375\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+375\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/27/2024 09:36:24"
&#x20;      }
&#x20;  ]
}


For "Expose Debit card sensitive data" setting as FALSE

\{
&#x20;  "id": 1368698,
&#x20;  "eventType": "debitcard.create",
&#x20;  "eventTimeStamp": "07/18/2024 05:38:20",
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "debitCard",
&#x20;          "url": "v1/customer/id/4049198/account/id/4034496/debitCard/id/657",
&#x20;          "id": 657,
&#x20;          "externalId": "35435235",
&#x20;          "cardHolder": \{
&#x20;              "name": "Ujjwal Patel1",
&#x20;              "id": 115238,
&#x20;              "type": "BENEFICIAL\_OWNER"
&#x20;          },
&#x20;          "cardNumber": "\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*",
&#x20;          "cvv": "\*\*\*",
&#x20;          "cardIssuanceId": "1058",
&#x20;          "type": "DIGITAL",
&#x20;          "cardProgram": "CORP STD PB V CARDXaoVK",
&#x20;          "shippingDetail": \{
&#x20;              "address": \{
&#x20;                  "zip": "46014",
&#x20;                  "city": "kingston",
&#x20;                  "addressLine1": "2683",
&#x20;                  "addressLine2": "Sector 4 MDC",
&#x20;                  "id": 1206763,
&#x20;                  "state": "AR",
&#x20;                  "status": "ACTIVE"
&#x20;              },
&#x20;              "expressDelivery": false
&#x20;          },
&#x20;          "isReissuedOnce": false,
&#x20;          "properties": \{
&#x20;              "isDigitalFirst": false
&#x20;          },
&#x20;          "status": "ACTIVE"
&#x20;      }
&#x20;  ],
&#x20;  "statusReason": "Debit Card activated",
&#x20;  "statusDate": "07/18/2024 05:38:20",
&#x20;  "createdOn": "07/18/2024 05:38:20",
&#x20;  "lastUpdatedBy": \{
&#x20;      "userType": "INTERNAL",
&#x20;      "username": "DEFAULT\_USER",
&#x20;      "status": "ACTIVE"
&#x20;  },
&#x20;  "createdBy": \{
&#x20;      "userType": "INTERNAL",
&#x20;      "username": "DEFAULT\_USER",
&#x20;      "status": "ACTIVE"
&#x20;  },
&#x20;  "lastUpdatedOn": "07/18/2024 05:38:20"
}

## debitcard.update

&#x20;&#x20;

\{
&#x20;  "id": 1363189,
&#x20;  "eventType": "debitcard.update",
&#x20;  "eventTimeStamp": "06/27/2024 09:46:13",
&#x20;  "eventId": "0001709618091430001",
&#x20;  "eventCreated": 1747098180090,
&#x20;  "payload": \[
&#x20;      \{
&#x20;          "resourceName": "debitCard",
&#x20;          "url": "v1/customer/id/4049187/account/id/4034426/debitCard/id/610",
&#x20;          "id": 610,
&#x20;          "cardHolder": \{
&#x20;              "name": "Ujjwal Patel",
&#x20;              "id": 115203,
&#x20;              "type": "BENEFICIAL\_OWNER"
&#x20;          },
&#x20;          "type": "PLASTIC",
&#x20;          "cardProgram": "PM CORP STD PB PL CARD2pGLBQ",
&#x20;          "shippingDetail": \{
&#x20;              "address": \{
&#x20;                  "zip": "33126",
&#x20;                  "city": "Miami",
&#x20;                  "addressLine1": "5505 Blue Lagoon Dr",
&#x20;                  "addressLine2": "",
&#x20;                  "id": 1206720,
&#x20;                  "state": "CO",
&#x20;                  "status": "ACTIVE"
&#x20;              },
&#x20;              "expressDelivery": true
&#x20;          },
&#x20;          "statusReason": "Debit Card Request submitted",
&#x20;          "cardNumber": "3626",
&#x20;          "properties": \{
&#x20;              "isDigitalFirst": false
&#x20;          },
&#x20;          "status": "ACTIVE",
&#x20;          "statusDate": "06/27/2024 09:36:24",
&#x20;          "createdOn": "06/27/2024 09:36:24",
&#x20;          "createdBy": \{
&#x20;              "userType": "CUSTOMER",
&#x20;              "username": "ujjwal.patel+375\@prth.com",
&#x20;              "status": "ACTIVE"
&#x20;          },
&#x20;          "lastUpdatedOn": "06/27/2024 09:46:13",
&#x20;          "lastUpdatedBy": \{
&#x20;              "userType": "SYSTEM",
&#x20;              "username": "SYSTEM",
&#x20;              "status": "ACTIVE"
&#x20;          }
&#x20;      }
&#x20;  ]
}

## moneygram.deposit.initiated

&#x20;&#x20;

\{
&#x20;   "id": 1368904,
&#x20;   "eventType": "moneygram.deposit.initiated",
&#x20;   "eventTimeStamp": "07/31/2024 12:54:20",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "source": "MONEYGRAM",
&#x20;           "accountNumber": "CMG12345",
&#x20;           "referenceNumber": "4026596520240731",
&#x20;           "amount": 20.6,
&#x20;           "processDate": "07/31/2024 12:54:20"
&#x20;       }
&#x20;   ]
}

## merchant.directfunded.create

&#x20;&#x20;

\{
&#x20;   "id": 66287814,
&#x20;   "eventType": "merchant.directfunded.create",
&#x20;   "eventTimeStamp": "07/31/2024 12:32:19",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "merchant",
&#x20;           "url": "/v1/customer/id/4227607/merchant/id/4006291",
&#x20;           "id": 4006291,
&#x20;           "externalId": "73267632",
&#x20;           "statusDate": "07/31/2024 12:32:18",
&#x20;           "configuration": \{
&#x20;               "quickSettle": false,
&#x20;               "passportFunding": \{
&#x20;                   "enable": false
&#x20;               }
&#x20;           },
&#x20;           "priorBankruptcy": false,
&#x20;           "type": "DIRECT\_FUNDED",
&#x20;           "cardNotPresent": \{
&#x20;               "billingMethod": \{
&#x20;                   "monthly": 10,
&#x20;                   "yearly": 10,
&#x20;                   "onetime": 80
&#x20;               },
&#x20;               "advertisingMethod": "Online",
&#x20;               "internetBusinessType": "ADVERTISEMENT"
&#x20;           },
&#x20;           "categoryCode": "0742",
&#x20;           "saleDetails": \{
&#x20;               "saleMethod": \{
&#x20;                   "ecom": 25,
&#x20;                   "pos": 50,
&#x20;                   "moto": 25
&#x20;               },
&#x20;               "averageDeliveryTime": "WEEK",
&#x20;               "averagePurchase": 100,
&#x20;               "productDescription": "Agriculture department",
&#x20;               "averageSalesVolumes": 100
&#x20;           },
&#x20;           "processor": \{
&#x20;               "name": "TSYS"
&#x20;           },
&#x20;           "underwritingStatus": "PENDING",
&#x20;           "categoryType": "Agricultural Services",
&#x20;           "linkedDocument": \[
&#x20;               \{
&#x20;                   "purpose": "UNDERWRITING",
&#x20;                   "linkedBy": \{
&#x20;                       "userType": "INTERNAL",
&#x20;                       "username": "DEFAULT\_USER",
&#x20;                       "status": "ACTIVE"
&#x20;                   },
&#x20;                   "document": \{
&#x20;                       "name": "Kreacher.png",
&#x20;                       "resourceName": "document",
&#x20;                       "id": 4056254,
&#x20;                       "type": "MERCHANT\_AGREEMENT",
&#x20;                       "url": "/v1/document/id/4056254"
&#x20;                   },
&#x20;                   "id": 46410,
&#x20;                   "linkedOn": "07/31/2024 12:32:19",
&#x20;                   "status": "PENDING\_VERIFICATION"
&#x20;               }
&#x20;           ],
&#x20;           "amex": \{
&#x20;               "optBlue": true
&#x20;           },
&#x20;           "discover": \{
&#x20;               "fullAcquiring": true
&#x20;           },
&#x20;           "merchantAccount": \{
&#x20;               "resourceName": "account",
&#x20;               "id": 9916199,
&#x20;               "accountNumber": "8125071400006678",
&#x20;               "url": "/v1/customer/id/4227607/account/id/9916199"
&#x20;           },
&#x20;           "underwritingStatusDate": "07/31/2024 12:32:18",
&#x20;           "location": \{
&#x20;               "resourceName": "location",
&#x20;               "url": "/v1/customer/id/4227607/merchant/id/4006291/location"
&#x20;           },
&#x20;           "status": "INACTIVE",
&#x20;           "createdOn": "07/31/2024 12:32:18",
&#x20;           "createdBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "07/31/2024 12:32:18",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           }
&#x20;       }
&#x20;   ]
}

## merchant.directfunded.update

&#x20;&#x20;

\{
&#x20;   "id": 66287821,
&#x20;   "eventType": "merchant.directfunded.update",
&#x20;   "eventTimeStamp": "07/31/2024 12:33:49",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "merchant",
&#x20;           "url": "/v1/customer/id/4227607/merchant/id/4006291",
&#x20;           "id": 4006291,
&#x20;           "externalId": "73267632",
&#x20;           "configuration": \{
&#x20;               "quickSettle": false,
&#x20;               "passportFunding": \{
&#x20;                   "enable": false
&#x20;               }
&#x20;           },
&#x20;           "priorBankruptcy": false,
&#x20;           "type": "DIRECT\_FUNDED",
&#x20;           "discover": \{
&#x20;               "fullAcquiring": true
&#x20;           },
&#x20;           "amex": \{
&#x20;               "optBlue": true
&#x20;           },
&#x20;           "cardNotPresent": \{
&#x20;               "billingMethod": \{
&#x20;                   "monthly": 10,
&#x20;                   "yearly": 10,
&#x20;                   "onetime": 80
&#x20;               },
&#x20;               "advertisingMethod": "Online",
&#x20;               "internetBusinessType": "ADVERTISEMENT"
&#x20;           },
&#x20;           "categoryCode": "0742",
&#x20;           "saleDetails": \{
&#x20;               "saleMethod": \{
&#x20;                   "ecom": 25,
&#x20;                   "pos": 50,
&#x20;                   "moto": 25
&#x20;               },
&#x20;               "averageDeliveryTime": "WEEK",
&#x20;               "averagePurchase": 100,
&#x20;               "productDescription": "Agriculture department",
&#x20;               "averageSalesVolumes": 80
&#x20;           },
&#x20;           "processor": \{
&#x20;               "name": "TSYS"
&#x20;           },
&#x20;           "statusDate": "07/31/2024 12:32:18",
&#x20;           "underwritingStatus": "PENDING",
&#x20;           "categoryType": "Agricultural Services",
&#x20;           "linkedDocument": \[
&#x20;               \{
&#x20;                   "purpose": "UNDERWRITING",
&#x20;                   "linkedBy": \{
&#x20;                       "userType": "INTERNAL",
&#x20;                       "username": "DEFAULT\_USER",
&#x20;                       "status": "ACTIVE"
&#x20;                   },
&#x20;                   "document": \{
&#x20;                       "name": "Kreacher.png",
&#x20;                       "resourceName": "document",
&#x20;                       "id": 4056254,
&#x20;                       "type": "MERCHANT\_AGREEMENT",
&#x20;                       "url": "/v1/document/id/4056254"
&#x20;                   },
&#x20;                   "id": 46410,
&#x20;                   "linkedOn": "07/31/2024 12:32:19",
&#x20;                   "status": "PENDING\_VERIFICATION"
&#x20;               }
&#x20;           ],
&#x20;           "merchantAccount": \{
&#x20;               "resourceName": "account",
&#x20;               "id": 9916199,
&#x20;               "accountNumber": "8125071400006678",
&#x20;               "url": "/v1/customer/id/4227607/account/id/9916199"
&#x20;           },
&#x20;           "underwritingStatusDate": "07/31/2024 12:32:18",
&#x20;           "location": \{
&#x20;               "resourceName": "location",
&#x20;               "url": "/v1/customer/id/4227607/merchant/id/4006291/location"
&#x20;           },
&#x20;           "status": "INACTIVE",
&#x20;           "createdOn": "07/31/2024 12:32:18",
&#x20;           "createdBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "07/31/2024 12:33:48",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           }
&#x20;       }
&#x20;   ]
}

## merchant.payfac.create

&#x20;&#x20;

\{
&#x20;   "id": 66287825,
&#x20;   "eventType": "merchant.payfac.create",
&#x20;   "eventTimeStamp": "07/31/2024 12:37:23",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "merchant",
&#x20;           "url": "/v1/customer/id/4227607/merchant/id/4006292",
&#x20;           "id": 4006292,
&#x20;           "externalId": "38728366",
&#x20;           "statusDate": "07/31/2024 12:37:23",
&#x20;           "underwritingStatusDate": "07/31/2024 12:37:23",
&#x20;           "status": "INACTIVE",
&#x20;           "configuration": \{
&#x20;               "passportFunding": \{
&#x20;                   "enable": false
&#x20;               }
&#x20;           },
&#x20;           "priorBankruptcy": false,
&#x20;           "categoryCode": "3000",
&#x20;           "type": "PAYFAC",
&#x20;           "saleDetails": \{
&#x20;               "saleMethod": \{
&#x20;                   "ecom": 25,
&#x20;                   "pos": 50,
&#x20;                   "moto": 25
&#x20;               },
&#x20;               "averageDeliveryTime": "WEEK",
&#x20;               "averagePurchase": 170,
&#x20;               "productDescription": "Arline services",
&#x20;               "averageSalesVolumes": 170
&#x20;           },
&#x20;           "underwritingStatus": "PENDING",
&#x20;           "categoryType": "Airlines",
&#x20;           "linkedDocument": \[
&#x20;               \{
&#x20;                   "purpose": "UNDERWRITING",
&#x20;                   "linkedBy": \{
&#x20;                       "userType": "INTERNAL",
&#x20;                       "username": "DEFAULT\_USER",
&#x20;                       "status": "ACTIVE"
&#x20;                   },
&#x20;                   "document": \{
&#x20;                       "name": "Kreacher.png",
&#x20;                       "resourceName": "document",
&#x20;                       "id": 4056256,
&#x20;                       "type": "MERCHANT\_AGREEMENT",
&#x20;                       "url": "/v1/document/id/4056256"
&#x20;                   },
&#x20;                   "id": 46412,
&#x20;                   "linkedOn": "07/31/2024 12:37:23",
&#x20;                   "status": "PENDING\_VERIFICATION"
&#x20;               }
&#x20;           ],
&#x20;           "merchantAccount": \{
&#x20;               "resourceName": "account",
&#x20;               "id": 9916199,
&#x20;               "accountNumber": "8125071400006678",
&#x20;               "url": "/v1/customer/id/4227607/account/id/9916199"
&#x20;           },
&#x20;           "location": \{
&#x20;               "resourceName": "location",
&#x20;               "url": "/v1/customer/id/4227607/merchant/id/4006292/location"
&#x20;           },
&#x20;           "createdOn": "07/31/2024 12:37:23",
&#x20;           "createdBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "07/31/2024 12:37:23"
&#x20;       }
&#x20;   ]
}

## merchant.payfac.update

&#x20;&#x20;

\{
&#x20;   "id": 66287837,
&#x20;   "eventType": "merchant.payfac.update",
&#x20;   "eventTimeStamp": "07/31/2024 12:44:41",
&#x20;   "eventId": "0001709618091430001",
&#x20;   "eventCreated": 1747098180090,
&#x20;   "payload": \[
&#x20;       \{
&#x20;           "resourceName": "merchant",
&#x20;           "url": "/v1/customer/id/4227607/merchant/id/4006292",
&#x20;           "id": 4006292,
&#x20;           "externalId": "38728366",
&#x20;           "statusDate": "07/31/2024 12:37:23",
&#x20;           "configuration": \{
&#x20;               "passportFunding": \{
&#x20;                   "enable": false
&#x20;               }
&#x20;           },
&#x20;           "priorBankruptcy": false,
&#x20;           "categoryCode": "3000",
&#x20;           "type": "PAYFAC",
&#x20;           "saleDetails": \{
&#x20;               "saleMethod": \{
&#x20;                   "ecom": 25,
&#x20;                   "pos": 50,
&#x20;                   "moto": 25
&#x20;               },
&#x20;               "averageDeliveryTime": "WEEK",
&#x20;               "averagePurchase": 170,
&#x20;               "productDescription": "Arline service",
&#x20;               "averageSalesVolumes": 170
&#x20;           },
&#x20;           "underwritingStatus": "PENDING",
&#x20;           "categoryType": "Airlines",
&#x20;           "linkedDocument": \[
&#x20;               \{
&#x20;                   "purpose": "UNDERWRITING",
&#x20;                   "linkedBy": \{
&#x20;                       "userType": "INTERNAL",
&#x20;                       "username": "DEFAULT\_USER",
&#x20;                       "status": "ACTIVE"
&#x20;                   },
&#x20;                   "document": \{
&#x20;                       "name": "Kreacher.png",
&#x20;                       "resourceName": "document",
&#x20;                       "id": 4056256,
&#x20;                       "type": "MERCHANT\_AGREEMENT",
&#x20;                       "url": "/v1/document/id/4056256"
&#x20;                   },
&#x20;                   "id": 46412,
&#x20;                   "linkedOn": "07/31/2024 12:37:23",
&#x20;                   "status": "PENDING\_VERIFICATION"
&#x20;               }
&#x20;           ],
&#x20;           "merchantAccount": \{
&#x20;               "resourceName": "account",
&#x20;               "id": 9916199,
&#x20;               "accountNumber": "8125071400006678",
&#x20;               "url": "/v1/customer/id/4227607/account/id/9916199"
&#x20;           },
&#x20;           "createdOn": "07/31/2024 12:37:23",
&#x20;           "createdBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "lastUpdatedOn": "07/31/2024 12:44:41",
&#x20;           "lastUpdatedBy": \{
&#x20;               "userType": "INTERNAL",
&#x20;               "username": "DEFAULT\_USER",
&#x20;               "status": "ACTIVE"
&#x20;           },
&#x20;           "underwritingStatusDate": "07/31/2024 12:37:23",
&#x20;           "location": \{
&#x20;               "resourceName": "location",
&#x20;               "url": "/v1/customer/id/4227607/merchant/id/4006292/location"
&#x20;           },
&#x20;           "status": "INACTIVE"
&#x20;       }
&#x20;   ]
}




return.wire.create