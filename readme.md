# MERN Ecommerce

A full-stack ecommerce application built with MongoDB, Express, React, and Node.js. The frontend uses Redux Toolkit for state management and Material UI for the interface.

![Ecommerce homepage](https://res.cloudinary.com/dh5fjdce9/image/upload/v1707365755/front_inhzp9.png)

## Features

### Customer experience

- Browse products by category, brand, search, and filters.
- Manage a cart, quantities, subtotals, wishlist items, and wishlist notes.
- Create orders and review order history.
- Add, edit, and remove product reviews with rating summaries.
- Manage profile details and multiple delivery addresses.
- Sign up, log in, verify accounts with OTP, reset passwords, and log out.

### Admin tools

- Create, update, and delete products.
- Soft-delete products and restore them when needed.
- Manage brands and categories.
- View orders and update their status through the fulfillment workflow.

## Tech stack

| Layer | Technologies |
| --- | --- |
| Frontend | React 18, React Router, Redux Toolkit, Material UI, Axios, Framer Motion |
| Backend | Node.js, Express, Mongoose, JWT, bcryptjs, Nodemailer |
| Database | MongoDB |

## Requirements

- Node.js 18 or newer (Node.js 21.1.0+ is also supported)
- npm
- A MongoDB database, local or hosted
- SMTP credentials if you want to test OTP and password-reset emails

## Quick start

### 1. Install dependencies

From the project root:

```bash
npm install
cd backend && npm install
cd ../frontend && npm install
```

### 2. Configure environment variables

Create `backend/.env`:

```env
MONGO_URI=mongodb://127.0.0.1:27017/mern-ecommerce
ORIGIN=http://localhost:3000
PORT=8000
SECRET_KEY=replace-with-a-long-random-secret
EMAIL=your-email@example.com
PASSWORD=your-email-password
LOGIN_TOKEN_EXPIRATION=30d
OTP_EXPIRATION_TIME=120000
PASSWORD_RESET_TOKEN_EXPIRATION=2m
COOKIE_EXPIRATION_DAYS=30
PRODUCTION=false
```

Create `frontend/.env`:

```env
REACT_APP_BASE_URL=http://localhost:8000
```

Use an app password or provider-specific SMTP credential where required. Never commit either `.env` file; they are ignored by the repository’s `.gitignore`.

### 3. Seed sample data

Make sure MongoDB is running, then run:

```bash
cd backend
npm run seed
```

The seed creates sample users, products, brands, categories, addresses, carts, wishlists, reviews, and orders. Run it against a development database because it inserts fixed sample records.

### 4. Start the application

The root script starts both services together:

```bash
cd ..
npm run dev
```

Alternatively, use separate terminals:

```bash
# Terminal 1
cd backend
npm run dev

# Terminal 2
cd frontend
npm start
```

The backend’s `dev` script uses the local `nodemon` dependency, so a global installation is not required.

## Local URLs

- Frontend: <http://localhost:3000>
- Backend: <http://localhost:8000>
- Database health check: <http://localhost:8000/database>

The root backend endpoint returns a small server status response at <http://localhost:8000/>.

## Demo account

After seeding the database, use:

```text
Email: demo@gmail.com
Password: helloWorld@123
```

The demo account does not have a real inbox, so use a newly registered account with a valid email address to test OTP verification and password reset.

## Available scripts

| Location | Command | Purpose |
| --- | --- | --- |
| Root | `npm run dev` | Run frontend and backend concurrently |
| Backend | `npm run dev` | Start the API with Nodemon |
| Backend | `npm start` | Start the API without Nodemon |
| Backend | `npm run seed` | Insert sample data into MongoDB |
| Frontend | `npm start` | Start the React development server |
| Frontend | `npm run build` | Create a production frontend build |
| Frontend | `npm test` | Run frontend tests |

## Project structure

```text
backend/    Express API, MongoDB models, routes, controllers, and seed data
frontend/   React application, Redux slices, pages, and reusable components
```

## Troubleshooting

- **Database connection errors:** confirm MongoDB is running and `MONGO_URI` points to the intended database.
- **CORS or cookie errors:** make sure `ORIGIN` exactly matches the frontend URL and restart the backend after changing `.env`.
- **Email errors:** verify SMTP credentials and use a real account for OTP and password-reset testing.
- **Frontend cannot reach the API:** confirm `REACT_APP_BASE_URL` is set and restart the React development server.

## Contributing

1. Create a feature branch.
2. Keep frontend and backend changes focused and consistent with existing patterns.
3. Run the relevant build or test commands before opening a pull request.
4. Do not commit credentials, generated files, or local `.env` files.

## Author

[Mayank Kumar](https://github.com/codeXmayank)