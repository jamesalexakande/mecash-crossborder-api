# Making Cross-Border Payments

## Overview

`POST /api/v1/payments`

This endpoint allows you to initiate an international money transfer between a sender and a recipient.

## Request

### Headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| Authorization | String | Yes | Bearer token for authentication. |
| Content-Type | String | Yes | Must be `application/json`. |

### Request Body

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| amount | Number | Yes | The payment amount. |
| currency | String | Yes | Currency code (e.g., `USD`, `EUR`). |
| sender | Object | Yes | Sender details. |
| sender.name | String | Yes | Full name of the sender. |
| sender.email | String | Yes | Email address of the sender. |
| recipient | Object | Yes | Recipient details. |
| recipient.name | String | Yes | Full name of the recipient. |
| recipient.accountNumber | String | Yes | Recipient's account number. |
| recipient.bankCode | String | Yes | Bank identification code. |
| recipient.country | String | Yes | Recipient's country. |
| reference | String | Yes | Transaction initiation code. |

### Example Request

```json
{
  "amount": 100.00,
  "currency": "USD",
  "sender": {
    "name": "John Doe",
    "email": "john.doe@x.com"
  },
  "recipient": {
    "name": "Jane Smith",
    "accountNumber": "0987654321",
    "bankCode": "XYZ456",
    "country": "USA"
  },
  "reference": "INV-12345"
}
```

## Response

### Example Response body 

`Success Response (HTTP 201 Created)`

```json
{
  "transactionId": "TXN789456123",
  "status": "SUCCESS",
  "createdAt": "2025-01-12T10:15:30Z",
  "amount": 100.00,
  "currency": "USD",
  "recipient": {
    "name": "Jane Smith",
    "country": "USA"
  }
}

```
| Parameter | Type | Description |
|-----------|------|-------------|
| transactionId | String | Reference code for completed transaction. |
| status | String | Payment status |
| createdAt | String | Timestamp of transaction |
| amount | Number | Transaction amount. |
| currency | String | Transaction currency. |
| recipient | Object | Recipient details. |

## Error Handling - Common Error Responses

#### Invalid Request (HTTP 400 Bad Request)
Occurs when the request contains an incorrect/invalid entry (see below).

**Example:**
```json
{
  "error": "INVALID_REQUEST",
  "message": "Invalid bank code for the recipient."
}
```

#### Unauthorized (HTTP 401 Unauthorized)
Occurs when the API key is missing or invalid.

**Example:**
```json
{
  "error": "UNAUTHORIZED",
  "message": "Invalid API key. Please provide a valid key."
}
```

#### Forbidden (HTTP 403 Forbidden)
Occurs when the API key does not have the required permissions.

**Example:**
```json
{
  "error": "FORBIDDEN",
  "message": "You do not have permission to perform this transaction."
}
```

#### Too Many Requests (HTTP 429 Too Many Requests)
Occurs when you have exceeded the rate limit - ie. you've made too many requests.

**Example:**
```json
{
  "error": "TOO_MANY_REQUESTS",
  "message": "You've made too many requests. Please try again later."
}
```

#### Internal Server Error (HTTP 500 Internal Server Error)
Occurs when there is an issue on the server.

**Example:**
```json
{
  "error": "INTERNAL_SERVER_ERROR",
  "message": "Something happened on meCash's end. Please try again later."
}
```

## Additional Information

* This API enforces rate limits on requests to ensure system stability. You are allowed to make 100 requests per minute with each API key.
* Ensure that the **Authorization** header is included in every request.
* The `amount` field should be a positive number.
* The `currency` must be a valid ISO 4217 currency code.
* The `reference` should be unique for each transaction to avoid duplication.

## Contact

For further inquiries, contact **meCash API Support** at support@mecash.com.
