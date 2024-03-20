# 3040Crypto Wallet API Documentation

## API Description

The 3040Crypto Wallet API is designed to provide a comprehensive suite of services for managing cryptocurrency wallets. It enables users to create new wallets, check balances, and view transaction histories, ensuring a seamless and user-friendly experience. This API aims to establish 3040Crypto as the premier choice for secure and efficient cryptocurrency management.

## Endpoints with Parameters

### 1. Register User
**Description:** This POST endpoint facilitates new user registrations, capturing essential information to create a secure and personalized account.
- **Endpoint:** `/api/user/register`
- **Parameters:**
  - `username`: Desired username, must be unique.
  - `email`: Email address for account verification and communication.
  - `password`: Account password, adhering to defined security standards.
  - `fullName`: Full name of the user for personalization.
  - `phoneNumber`: Phone number for account recovery and additional security options.

### 2. Create New Wallet
**Description:** This is a POST method that allows users to create a new cryptocurrency wallet, which returns a unique wallet ID for subsequent transactions and queries.
- **Endpoint:** `/api/wallet/create`
- **Parameters:**
  - `user_id`: The unique identifier for the user.
  - `email`: The user's email address for notifications and recovery purposes.

### 3. Get Wallet Balance
**Description:** This is a GET method that retrieves the current balance of the specified cryptocurrency in the user's wallet, allowing for real-time financial management.
- **Endpoint:** `/api/wallet/balance`
- **Parameters:**
  - `wallet_id`: The unique identifier of the user's wallet.
  - `currency`: The specific cryptocurrency to check the balance for. Defaults to Bitcoin (BTC) if not specified.

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

### Register User
**Request:** POST `/api/user/register` with body `{"username": "newUser123", "email": "newuser@example.com", "password": "SecurePa$$w0rd"}`

**Response:**

```json
{
  "message": "User registration successful. Please verify your email to complete the setup.",
  "userId": "newUserId67890",
  "username": "newUser123"
}
```

### Create New Wallet
**Request:** POST `/api/wallet/create` with body `{"user_id": "65373", "email": "sample@example.com"}`

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
