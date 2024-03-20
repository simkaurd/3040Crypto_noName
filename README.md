# 3040Crypto Wallet API Documentation

## API Description

The 3040Crypto Wallet API is designed to provide a comprehensive suite of services for managing cryptocurrency wallets. It enables users to create new wallets, check balances, and view transaction histories, ensuring a seamless and user-friendly experience. This API aims to establish 3040Crypto as the premier choice for secure and efficient cryptocurrency management.

## Endpoints with Parameters

### 1. Register User
**Description:** Streamlines the process of registering new users by collecting vital information to set up a secure and tailored account.
- **Endpoint:** `/api/user/register`
- **Operation:** POST
- **Parameters:**
  - `username`: Desired username, must be unique.
  - `email`: Email address for account verification and communication.
  - `password`: Account password, adhering to defined security standards.
  - `fullName`: Full name of the user for personalization.
  - `phoneNumber`: Phone number for account recovery and additional security options.

### 2. Create New Wallet
**Description:** Enables the initiation of a new cryptocurrency wallet, providing a unique identifier for the wallet that is crucial for future transactions and inquiries.
- **Endpoint:** `/api/wallet/create`
- **Operation:** POST
- **Parameters:**
  - `user_id`: The unique identifier for the user.
  - `email`: The user's email address for notifications and recovery purposes.

### 3. Get Wallet Balance
**Description:** Facilitates the retrieval of the current balance for a chosen cryptocurrency within the user's wallet, supporting effective financial oversight.
- **Endpoint:** `/api/wallet/balance`
- **Operation:** GET
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
