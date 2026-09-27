# Dream Sale - Ecommerce Platform

A modern, full-stack ecommerce platform built with React, Node.js, Express, and PostgreSQL.

## Features

### Customer Features
- Home page with Dream Sale branding
- Product catalog with Clothes and Electrical categories
- Product search and filtering
- Product details with images
- Shopping cart management
- Secure checkout
- Razorpay payment integration
- Order history and tracking
- Mobile-responsive design

### Admin Features
- Secure admin login
- Product management (create, read, update, delete)
- Product image uploads
- Category management
- Order management and status tracking
- Sales analytics

## Tech Stack

**Frontend:**
- React 18
- Vite
- Tailwind CSS
- Axios

**Backend:**
- Node.js
- Express.js
- PostgreSQL
- Prisma ORM
- JWT Authentication

**Payment:**
- Razorpay

## Prerequisites

- Node.js (v16 or higher)
- PostgreSQL (v12 or higher)
- npm or yarn

## Project Structure

```
dream-sale/
├── frontend/               # React frontend application
│   ├── src/
│   ├── public/
│   └── package.json
├── backend/               # Express backend API
│   ├── src/
│   ├── prisma/
│   └── package.json
├── .env.example           # Environment variables template
└── README.md
```

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/udaybhan1428-source/Dream-sale.git
cd Dream-sale
```

### 2. Setup Backend

```bash
cd backend

# Install dependencies
npm install

# Create .env file (see Environment Variables section)
cp .env.example .env

# Run database migrations
npm run db:migrate

# Seed database (optional - adds sample data)
npm run db:seed

# Start backend server
npm run dev
```

Backend runs on: `http://localhost:5000`

### 3. Setup Frontend

```bash
cd frontend

# Install dependencies
npm install

# Create .env file (see Environment Variables section)
cp .env.example .env

# Start development server
npm run dev
```

Frontend runs on: `http://localhost:5173`

## Environment Variables

### Backend (.env)

```
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/dream_sale

# JWT
JWT_SECRET=your-secret-key-here
JWT_EXPIRE=7d

# Razorpay
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret

# Admin
ADMIN_DEFAULT_PASSWORD=secure-admin-password

# Server
PORT=5000
NODE_ENV=development
```

### Frontend (.env)

```
VITE_API_URL=http://localhost:5000
```

## Database Setup

```bash
# Create PostgreSQL database
createdb dream_sale

# Run migrations
cd backend
npm run db:migrate

# (Optional) Seed with sample data
npm run db:seed
```

## Running the Application

### Development Mode

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```

### Production Build

**Frontend:**
```bash
cd frontend
npm run build
```

**Backend:**
```bash
cd backend
npm run build
npm start
```

## API Documentation

### Authentication
- POST `/api/auth/register` - Register new customer
- POST `/api/auth/login` - Login customer
- POST `/api/auth/admin-login` - Admin login
- POST `/api/auth/refresh` - Refresh token

### Products
- GET `/api/products` - List all products
- GET `/api/products/:id` - Get product details
- GET `/api/categories` - List categories
- GET `/api/products?category=clothes` - Filter by category

### Cart
- GET `/api/cart` - Get user's cart
- POST `/api/cart/add` - Add item to cart
- PUT `/api/cart/update/:itemId` - Update cart item
- DELETE `/api/cart/remove/:itemId` - Remove from cart

### Orders
- POST `/api/orders` - Create order
- GET `/api/orders` - Get user's orders
- GET `/api/orders/:id` - Get order details

### Payments
- POST `/api/payments/create-order` - Create Razorpay order
- POST `/api/payments/verify` - Verify payment signature

### Admin
- POST `/api/admin/products` - Create product
- PUT `/api/admin/products/:id` - Update product
- DELETE `/api/admin/products/:id` - Delete product
- GET `/api/admin/orders` - View all orders
- PUT `/api/admin/orders/:id/status` - Update order status

## Security Measures

✅ Passwords hashed with bcryptjs
✅ JWT-based authentication
✅ Protected admin routes
✅ Razorpay signature verification
✅ Input validation on all endpoints
✅ Environment variable protection
✅ CORS enabled for frontend
✅ Rate limiting on authentication endpoints

## Features Implementation Status

- ✅ Frontend project setup
- ✅ Backend API server
- ✅ Database schema
- ✅ Authentication system
- ✅ Product management
- ✅ Categories (Clothes, Electrical)
- ✅ Shopping cart
- ✅ Checkout flow
- ✅ Razorpay integration
- ✅ Admin panel
- ✅ Order management
- ✅ Mobile responsive design
- ✅ Dream Sale branding

## Troubleshooting

### Port Already in Use
```bash
# Backend (5000)
lsof -i :5000
kill -9 <PID>

# Frontend (5173)
lsof -i :5173
kill -9 <PID>
```

### Database Connection Issues
- Verify PostgreSQL is running
- Check DATABASE_URL in .env
- Ensure database exists: `psql -l`

### Razorpay Integration Not Working
- Verify RAZORPAY_KEY_ID and RAZORPAY_KEY_SECRET are correct
- Check that payment endpoint is accessible
- Review payment verification logs

## Support

For issues or questions, please create an issue in the repository.

## License

MIT
