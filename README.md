# Amazon API - Backend Service

A Node.js/Express backend service for handling Stripe payment processing in the Amazon Clone application.

## 🚀 Features

- **Payment Processing**: Secure Stripe payment intent creation
- **CORS Support**: Configured for cross-origin requests from the frontend
- **Environment Configuration**: Secure API key management with dotenv
- **Error Handling**: Proper error responses for payment failures

## 🛠️ Tech Stack

- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **Stripe** - Payment processing
- **CORS** - Cross-origin resource sharing
- **Dotenv** - Environment variable management

## 📁 Project Structure

```
amazon-api/
├── index.js          # Main server file
├── package.json      # Dependencies and scripts
├── .env              # Environment variables (not committed)
├── .gitignore        # Git ignore rules
└── README.md         # This file
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v18 or higher)
- npm or yarn
- Stripe account

### Installation

1. **Clone or navigate to the amazon-api directory**

   ```bash
   cd amazon-api
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Environment Setup**
   - Create a `.env` file in the amazon-api directory
   - Add your Stripe secret key:
   ```
   STRIPE_KEY=sk_test_your_stripe_secret_key_here
   ```

### Running the Server

1. **Start the server**
   ```bash
   npm start
   # or for development with auto-restart
   npm run dev
   ```

The server will start on `http://localhost:5000`

## 📡 API Endpoints

### POST /payment/create

Creates a Stripe payment intent for processing payments.

**Query Parameters:**

- `total` (number): Total amount in cents (e.g., 1000 for $10.00)

**Response:**

```json
{
  "clientSecret": "pi_xxx_secret_xxx"
}
```

**Example Request:**

```bash
curl -X POST "http://localhost:5000/payment/create?total=1000"
```

## 🔧 Configuration

### Environment Variables

- `STRIPE_KEY`: Your Stripe secret key (starts with `sk_test_` for test mode)

### CORS Configuration

The server is configured to accept requests from the frontend. Update the CORS origin in `index.js` if needed:

```javascript
app.use(cors({ origin: "http://localhost:3000" })); // Update with your frontend URL
```

## 🔒 Security

- Stripe secret keys are stored in environment variables
- CORS is configured to restrict origins
- Input validation for payment amounts

## 🧪 Testing

Test the payment endpoint with curl:

```bash
curl -X POST "http://localhost:5000/payment/create?total=500"
```

Expected response includes a `clientSecret` for use with Stripe Elements.

## 📝 Notes

- This API is designed to work with the Amazon Clone React frontend
- All monetary values should be sent in cents (multiply dollars by 100)
- The API uses Stripe's test mode by default

## 🤝 Contributing

1. Make changes to `index.js`
2. Test thoroughly with the frontend application
3. Ensure environment variables are properly documented

## 📄 License

This project is for educational purposes.
