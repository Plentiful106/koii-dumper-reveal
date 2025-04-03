# Koii Blockchain Transaction Analysis Node API

## 1. Project Overview

The Koii Blockchain Transaction Analysis Node is an open-source backend service designed to monitor, analyze, and provide insights into KOII token transactions on the Koii blockchain. This API enables real-time tracking of significant wallet activities, exchange interactions, and potential token dumping behaviors.

### Key Features
- Real-time blockchain transaction monitoring
- Exchange deposit address tracking
- Large transfer detection
- Verifiable transaction flagging
- RESTful API for transaction queries

### Use Cases
- Cryptocurrency market analysis
- Token movement tracking
- Detecting potential market manipulation
- Transparent blockchain activity insights

## 2. Getting Started

### Prerequisites
- Node.js (v14+ recommended)
- npm or yarn
- Git

### Installation
1. Clone the repository:
```bash
git clone https://github.com/YOUR-ORG/koii-analysis-node.git
cd koii-analysis-node
```

2. Install dependencies:
```bash
npm install
```

3. Configure environment variables:
Create a `.env` file in the project root with the following variables:
```bash
KOII_RPC_ENDPOINT=https://mainnet.koii.network
TRANSACTION_THRESHOLD=10000  # KOII tokens
```

4. Start the development server:
```bash
npm run dev
```

## 3. API Documentation

### Available Endpoints

#### 1. Flagged Transactions
- **GET** `/api/flagged-transactions`
  - Retrieves a list of flagged transactions
  - Query Parameters:
    - `limit`: Number of transactions to return (default: 100)
    - `offset`: Pagination offset

  **Example Response:**
  ```json
  {
    "transactions": [
      {
        "transactionId": "abc123...",
        "from": "wallet_address_1",
        "to": "exchange_deposit_address",
        "amount": 50000,
        "timestamp": "2023-06-15T10:30:45Z",
        "nodeSignature": "signature_hash"
      }
    ]
  }
  ```

#### 2. Wallet Activity
- **GET** `/api/wallet/{address}`
  - Retrieves historical activity for a specific wallet
  
  **Example Response:**
  ```json
  {
    "address": "wallet_address",
    "totalTransactions": 42,
    "exchangeInteractions": 5,
    "largeTransfers": [
      {
        "amount": 25000,
        "timestamp": "2023-06-10T15:22:33Z",
        "type": "outgoing"
      }
    ]
  }
  ```

#### 3. Real-time Alerts
- **GET** `/api/alerts`
  - Streams real-time alerts for major transfers

## 4. Authentication

The API uses API key-based authentication:

- Include your API key in the request header:
```http
Authorization: Bearer YOUR_API_KEY
```

- API keys can be generated through the Koii developer portal
- Rate limits apply based on your access tier

## 5. Project Structure
```
koii-analysis-node/
├── src/
│   ├── controllers/    # Request handlers
│   ├── models/         # Data models
│   ├── routes/         # API route definitions
│   ├── services/       # Business logic
│   └── utils/          # Utility functions
├── tests/              # Unit and integration tests
├── .env                # Environment configuration
└── package.json        # Project metadata and scripts
```

## 6. Technologies Used
- Node.js
- Express.js
- TypeScript
- Koii JSON-RPC
- WebSocket for real-time updates
- Jest (testing)

## 7. Deployment

### Docker Deployment
```bash
docker build -t koii-analysis-node .
docker run -p 3000:3000 koii-analysis-node
```

### Cloud Platforms
Supported platforms:
- AWS EC2
- Google Cloud Run
- Heroku

Recommended cloud deployment steps are available in `DEPLOYMENT.md`

## 8. License

This project is licensed under the MIT License. See `LICENSE` file for details.

---

## Contribution

Contributions are welcome! Please read our [Contribution Guidelines](CONTRIBUTING.md) before submitting a pull request.

Join our community discussions on [Koii Network Discord](https://discord.gg/koii).