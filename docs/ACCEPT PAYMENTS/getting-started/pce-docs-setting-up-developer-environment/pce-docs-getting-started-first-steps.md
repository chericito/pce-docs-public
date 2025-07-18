---
title: 'Getting Started: First Steps'
excerpt: >-
  Kickstart your PCE integration by obtaining credentials, authenticating
  requests, and familiarizing yourself with core API operations.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
````markdown
# Overview

This page guides you through the initial steps to call PCE Sandbox APIs: from authentication to basic CRUD and listing workflows.

**In this guide you’ll learn**

- How to authenticate using a Bearer token  
- The standard patterns for creating, updating, retrieving, and listing entities  
- Best practices around pagination and error handling  

### Prerequisites & Limitations

- A provisioned PCE Sandbox account with valid API‐User credentials  
- All API calls must be made over HTTPS; HTTP is not supported  
- API rate limit: 1000 requests per 10 seconds (exceeding this returns 429)  

# Key Details

## Authentication

All PCE Sandbox API requests must include a valid Bearer token in the `Authorization` header over HTTPS. Requests without authentication or made over plain HTTP will be rejected.

```http
GET /v1/customer HTTP/1.1
Host: api.sandbox.pce.example.com
Authorization: Bearer abc123xyz
Content-Type: application/json
````

To get started:

1. **Obtain your API bearer token** from your PCE representative. This token will authenticate all subsequent calls.
2. **Make a test request** against the sandbox environment to verify your integration is working end-to-end.

> **Note:** All examples in this documentation use placeholder data.

### Authentication Rules

* **HTTPS Only:** All calls must be made over TLS; HTTP is not supported.
* **Mandatory Header:** Every request must include `Authorization: Bearer <token>`.
* **Rate Limits:** 1,000 requests per 10 seconds. Exceeding this returns a `429 Too Many Requests` and drops further calls until the window resets.

## Working with the API

*All figures and data in this document are representational. Contact your PCE representative for access to production data.*

### Request Header

Every request must include the Bearer token in the `Authorization` header:

```http
Authorization: Bearer <JWT token>
```

### Create Entities

Use **HTTP POST** to create any entity.

* **Success:** `201 Created`
* **Response Header:** `Location: /v1/{entity}/{id}`

### Update Entities

Use **HTTP POST** to update an existing entity.

* **Success:** `204 No Content`
* **Notes:**

  1. Include only the fields you wish to change.
  2. To delete a non-mandatory field, pass its value as `null`.
  3. To remove an associated object, use the delink API endpoint.

### Retrieve Entities

Use **HTTP GET** to fetch an entity by its system‐assigned ID or by its `externalId`.

* The full set of attributes is returned (excluding any null, non-mandatory fields).
* System fields like `createdOn`, `createdBy`, `lastUpdatedOn`, and `lastUpdatedBy` are always included.
* Any associations are returned as objects containing only their URLs—you must invoke additional GET calls to retrieve their details.

### List Entities

All “list” operations use **HTTP POST** to ensure secure transmission of sensitive data. Bulk-fetch top-level resources (e.g., customers, transactions) with filters, sorting, and pagination.

* **Filters:** Support multiple conditions on any supported field.
* **Sorting:** Defaults to descending `lastUpdatedOn` if no sort criteria are provided.
* **Response:** Returns matching records plus metadata (`totalCount`, `returnedCount`, `offset`).
* **Data Lag:** List APIs may lag by up to 30 minutes.

#### Table 1: List Response Attributes

| Field      | Required | Description                                     |
| ---------- | :------: | ----------------------------------------------- |
| `criteria` |    Yes   | List of filters applied in this list operation. |
| `filter`   |    Yes   | A single filter definition:                     |

* **key**: the field name to filter on
* **operator**: one of `eq`, `ne`, `lt`, `gt`, `lte`, `gte`, `in`, `like`
* **values**: comma-separated list of filter values  |
  \| `sortOptions`   |    No    | Controls ordering of results.                                                                                                                                                                              |
  \| `sortBy`        |   Yes    | Field name to sort on.                                                                                                                                                                                     |
  \| `sortOrder`     |    No    | Sorting direction: `ASC` or `DESC`.                                                                                                                                                                        |
  \| `limit`         |    No    | Max number of records to return (1–100). Default: 100.                                                                                                                                                     |
  \| `offset`        |    No    | ID of the last record returned in the previous call. Requires sorting by ID.                                                                                                                               |
  \| `pageSize`      |    No    | Records per page. Default: 100.                                                                                                                                                                            |
  \| `pageNumber`    |    No    | Page number to retrieve.                                                                                                                                                                                   |
  \| `getTotalCount` |    No    | Include the total count of records matching the filters. To use, set to `true` and pass `lastUpdatedOn`, `startDate`, and `endDate` (max range 90 days). Default: false.                                  |

### `metaData` Attribute

Each entity supports a free-form `metaData` map of up to 20 key–value pairs. This is ideal for partner IDs or other structured data.

> **Do not** store sensitive information (e.g. account numbers, card details) in metadata.

### `tags` Attribute

Entities can be labeled with one or more text tags to facilitate grouping and search. You can later retrieve all entities that share a given tag.

### Authorization Documents

Most entities require supporting documents (e.g., SPAA for KYC, debit authorizations). Two upload methods are supported:

1. **Document API**: Upload once, then link the document to multiple entities.
2. **Inline Base64**: Embed `base64EncodedContent` on creation/update—Passport will upload and link it automatically.

## Pagination

The API supports pagination using four parameters: `pageSize`, `pageNumber`, `limit`, and `offset`. All are optional—if none are provided, `pageSize` and `pageNumber` will control the result set.

* **pageNumber**
  Default: `1`
  Specifies which “page” of results to return.

* **pageSize**
  Default: `1000` (maximum `1000`)
  Number of records per page.

* **limit**
  Default: `100` (maximum `100`)
  If specified without `pageNumber`/`pageSize`/`offset`, controls the total records returned.

* **offset**
  An entity ID indicating where to start the next page of results.
  Requires sorting by the ID field.

**Precedence rules**

1. If `pageSize` and `pageNumber` are provided, they take priority over `limit` and `offset`.
2. If only `limit` is provided, it governs the size of the result set, regardless of other parameters.
3. If none are provided, the API defaults to `pageSize=1000` and `pageNumber=1`.

## Errors & Warnings

PCE uses standard HTTP response codes and structured API error codes to indicate the outcome of each request.

---

### HTTP Status Codes

| Code | Description                                                                                       |
| ---- | ------------------------------------------------------------------------------------------------- |
| 200  | OK – Request completed successfully (used for GETs)                                               |
| 201  | Created – Resource created; URL returned in `Location` header                                     |
| 202  | Accepted – Request accepted for processing; may not be acted upon immediately (e.g. Promise Mode) |
| 204  | No Content – Request processed successfully; no response body (used for updates and deletes)      |
| 299  | Warning – Request processed, but with a warning that may affect subsequent operations             |
| 400  | Bad Request – Malformed syntax or missing required parameter                                      |
| 401  | Unauthorized – Authentication failed (invalid or missing token)                                   |
| 404  | Not Found – Resource does not exist                                                               |
| 405  | Method Not Allowed – HTTP method not supported for this endpoint                                  |
| 415  | Unsupported Media Type – Request body format not supported                                        |
| 422  | Unprocessable Entity – Well-formed request but semantic or business validation failed             |
| 429  | Too Many Requests – Rate limit exceeded; “Retry-After” header may indicate when to retry          |
| 5xx  | Server Error – Unexpected problem on PCE’s servers                                                |

---

### API Error Code Categories

| Category     | Description                                            |
| ------------ | ------------------------------------------------------ |
| EC-AUTH-XXXX | Authorization errors (e.g. login, token failures)      |
| EC-VA-XXXX   | Validation errors (e.g. missing or invalid parameters) |
| EC-BL-XXXX   | Business logic errors (entity-specific rules)          |

---

### Authorization Error Codes

| Code             | Message                                                               |
| ---------------- | --------------------------------------------------------------------- |
| **EC-AUTH-0001** | User authorization attempt failed. User needs to confirm credentials. |

---

### Header Validation Error Codes

| Code           | Message                               |
| -------------- | ------------------------------------- |
| **EC-VA-0001** | Missing header parameter: `[object]`. |
| **EC-VA-0002** | Invalid header parameter: `[object]`. |

---

### User Verification & Security Validation Errors

| Code           | Message                                                     |
| -------------- | ----------------------------------------------------------- |
| **EC-VA-0106** | Three security questions are required.                      |
| **EC-VA-0107** | At least one of new password or security question required. |

---

### API Validation Error Codes

| Code           | Message                                      |
| -------------- | -------------------------------------------- |
| **EC-VA-0004** | `[jsonString]`                               |
| **EC-VA-0005** | Validation failed.                           |
| **EC-VA-0006** | Invalid value `[value]` for field `[field]`. |
| **EC-VA-0007** | Invalid value `[value]`.                     |
| **EC-VA-0008** | Invalid field `[value]`.                     |

> **Note:** Business-Logic errors (`EC-BL-XXXX`) are entity-specific and documented under each entity’s “Business Validations” section.

---

### Warning Messages

PCE may return HTTP 299 with warning headers to convey non-blocking issues or deprecations. Inspect the `Warning` response header for details and recommended actions.

```
```
