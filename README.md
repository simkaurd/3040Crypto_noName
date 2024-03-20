# 3040Crypto Wallet API Documentation

## API Description

The 3040Crypto Wallet API is designed to provide a comprehensive suite of services for managing cryptocurrency wallets. It enables users to create new wallets, check balances, and view transaction histories, ensuring a seamless and user-friendly experience. This API aims to establish 3040Crypto as the premier choice for secure and efficient cryptocurrency management.

## Endpoints with Parameters

### 1. Create New Wallet
**Description:** This is a POST method that allows users to create a new cryptocurrency wallet, which returns a unique wallet ID for subsequent transactions and queries.
- **Endpoint:** `/api/wallet/create`
- **Parameters:**
  - `user_id` (required): The unique identifier for the user.
  - `email` (optional): The user's email address for notifications and recovery purposes.

### 2. Get Wallet Balance
**Description:** This is a GET method that retrieves the current balance of the specified cryptocurrency in the user's wallet, allowing for real-time financial management.
- **Endpoint:** `/api/wallet/balance`
- **Parameters:**
  - `wallet_id` (required): The unique identifier of the user's wallet.
  - `currency` (optional): The specific cryptocurrency to check the balance for. Defaults to Bitcoin (BTC) if not specified.

### 3. Transaction History
**Description:** This is a GET method that provides a detailed history of all transactions associated with the user's wallet, including amounts, dates, and transaction statuses, facilitating transparent record-keeping and financial tracking.
- **Endpoint:** `/api/wallet/transactions/history`
- **Parameters:**
  - `wallet_id` (required): The unique identifier of the user's wallet.
  - `start_date` (optional): The beginning date for the transaction history query.
  - `end_date` (optional): The ending date for the transaction history query.

## Description of Resources

```json
{
  "Wallet": {
    "wallet_id": "string",
    "user_id": "string",
    "email": "string",
    "balances": [
      {
        "currency": "string",
        "amount": "number"
      }
    ]
  },
  "Transaction": {
    "transaction_id": "string",
    "wallet_id": "string",
    "amount": "number",
    "currency": "string",
    "timestamp": "datetime",
    "status": "string"
  }
}
```

## Sample Request with Sample Response

### Create New Wallet
**Request:** POST `/api/wallet/create` with body `{"user_id": "12345", "email": "user@example.com"}`

**Response:**

```json
{
  "wallet_id": "abcde12345",
  "message": "Wallet successfully created."
}
```

### Get Wallet Balance
**Request:** GET `/api/wallet/balance?wallet_id=abcde12345&currency=BTC`

**Response:**

```json
{
  "wallet_id": "abcde12345",
  "currency": "BTC",
  "balance": 1.5
}
```

### Transaction History
**Request:** GET `/api/wallet/transactions/history?wallet_id=abcde12345&start_date=2024-01-01&end_date=2024-03-01`

**Response:**

```json
{
  "transactions": [
    {
      "transaction_id": "t1",
      "amount": 1202.0,
      "currency": "ETH",
      "timestamp": "2024-03=19T9:00:00Z",
      "status": "completed"
    },
    {
      "transaction_id": "t2",
      "amount": 1.0,
      "currency": "USDT",
      "timestamp": "2024-03=20-20T16:30:00Z",
      "status": "completed"
    }
  ]
}
```
