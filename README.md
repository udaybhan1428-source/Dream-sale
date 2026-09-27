# Dream Sale

Dream Sale is a mobile-first ecommerce storefront for Clothes and Electrical products, with a secure admin panel and Razorpay-ready checkout.

## Tech stack
- Frontend: React + Vite + CSS
- Backend: Node.js + Express + Prisma + SQLite for local development
- Database: Prisma schema for users, products, categories, cart, orders, payments, and admin users
- Payments: Razorpay-ready server-side verification

## Project structure

```text
Dream-sale/
├── backend/
│   ├── prisma/
│   ├── src/
│   ├── .env.example
│   └── package.json
├── frontend/
│   ├── public/
│   ├── src/
│   ├── .env.example
│   ├── index.html
│   └── package.json
├── .gitignore
├── README.md
└── .nvmrc
```

## Local setup

### 1. Backend
```bash
cd backend
npm install
cp .env.example .env
npx prisma generate
npx prisma migrate dev --name init
npm run db:seed
npm run dev
```

The API runs on http://localhost:5000.

### 2. Frontend
```bash
cd frontend
npm install
cp .env.example .env
npm run dev
```

The app runs on http://localhost:5173.

## Environment variables

Backend `.env` must include:

```bash
DATABASE_URL="file:./prisma/dev.db"
JWT_SECRET=replace_with_a_strong_random_secret
PORT=5000
ADMIN_EMAIL=admin@dreamsale.com
ADMIN_PASSWORD=change_this_to_a_strong_admin_password
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret
```

Frontend `.env` can include:

```bash
VITE_API_URL=http://localhost:5000
```

Important: never commit real secrets to GitHub. Keep them in local environment files only.

## Included features
- Dream Sale branding and responsive storefront
- Product categories: Clothes and Electrical only
- Search, filtering, and product detail pages
- Cart with quantity selection
- Checkout with customer information
- Order creation and confirmation flow
- Secure admin login
- Admin product management, order status update, and product image controls
- Razorpay order creation and server-side signature verification
- SQLite-backed local development database

## Admin access
Use the default admin credentials from your backend `.env` file after setup. Change them immediately in production.

## Production notes
- Use a hosted database such as PostgreSQL in production
- Keep Razorpay keys in environment variables only
- Review the backend routes before exposing the app publicly
- Run the frontend and backend behind a secure reverse proxy in deployment

## Important payment note
The Razorpay integration is fully wired for secure backend verification, but live payment processing requires valid `RAZORPAY_KEY_ID` and `RAZORPAY_KEY_SECRET`. Until those credentials are configured, checkout will fail with a clear configuration message instead of using fake values.
