# Fullstack React Laravel Product API

![Login Page](/image/page2.png)

<div align="center">
  <img src="/image/loginpage.png" width="220" alt="Login Page" />
  <img src="/image/page1.png" width="220" alt="Home Page" />
  <img src="/image/page2.png" width="220" alt="Product Page" />
  <img src="/image/page1.png" width="220" alt="Dashboard Example" />
  <img src="/image/page3.png" width="220" alt="Detail Page" />
</div>

## 📌 About the Project

This repository contains a fullstack e-commerce application with:
- A Laravel backend API for authentication, product/category management, orders, roles, and permissions.
- A React frontend built with Vite for browsing products, managing cart checkout, and admin dashboards.

The application is designed as a complete product API and storefront with modern tooling for both frontend and backend.

## 🚀 What’s Included

### Backend
- Laravel 12 RESTful API
- JWT authentication and Google login
- Product, category, and order management
- Role- and permission-based admin controls
- Public endpoints for product browsing and detail pages
- Dockerized environment with Nginx, PHP-FPM, and MySQL

### Frontend
- React 19 + Vite for fast development
- Responsive customer storefront with product listing and details
- Shopping cart flow and checkout support
- Login/register pages for customers and admin users
- Admin dashboard for managing products, users, and orders
- Charts and UI components powered by Recharts, Framer Motion, and Flowbite React

## 🌟 Main Features

- User registration, login, logout, and protected admin routes
- Product creation, update, deletion, and detail views
- Category management and listing
- Order creation, history listing, and today's order count
- Admin dashboard with chart visualizations and management pages
- Redux Toolkit + Redux Persist for frontend state management
- Tailwind CSS + Flowbite React for styling and UI consistency

## 🧰 Technologies Used

### Backend
- PHP 8.2
- Laravel 12
- Docker & Docker Compose
- Nginx
- MySQL 8.0
- PHP-FPM
- JWT Auth (`tymon/jwt-auth`)
- Laravel Socialite (`laravel/socialite`)
- Spatie Permission (`spatie/laravel-permission`)
- Midtrans Payment SDK (`midtrans/midtrans-php`)
- Laravel Sanctum

### Frontend
- React 19
- Vite
- Redux Toolkit
- Redux Persist
- Tailwind CSS
- Flowbite React
- Axios
- Recharts
- Framer Motion
- Lucide React

---

## 🔧 Setup & Run

### Prerequisites

- Docker
- Docker Compose
- Git
- Node.js and npm

### Backend Setup

1. Clone the repository:

```bash
git clone <repo-url>
cd FullstackReactLaravelProductApiApp
```

2. Copy the environment file:

```bash
copy .env.example .env
```

3. Adjust `.env` values if needed.

4. Start backend services:

```bash
docker compose up -d --build
```

5. Run migrations and seeders:

```bash
docker compose exec app php artisan key:generate

docker compose exec app php artisan migrate --seed
```

6. Create storage symlink if required:

```bash
docker compose exec app php artisan storage:link
```

### Frontend Setup

1. Open a terminal in `frontend/`:

```bash
cd frontend
npm install
```

2. Create frontend environment file:

```bash
copy .env.example .env
```

3. Start the React development server:

```bash
npm run dev
```

4. Open the URL shown by Vite in your browser.

> For local development, the frontend expects the backend API base URL in `VITE_API_URL`.

---

## 🌐 Environment Variables

### Backend `.env`

- `APP_NAME`
- `APP_URL`
- `DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`
- `JWT_SECRET`
- Google OAuth credentials for social login

### Frontend `.env`

```env
VITE_API_URL=http://localhost/api
VITE_GOOGLE_CLIENT_ID=your_google_client_id_here
```

---

## 🌐 API Base URL

- Docker: `http://localhost/api`
- Local Laravel server: `http://127.0.0.1:8000/api`

> Use `Authorization: Bearer {token}` for protected endpoints.

---

## 📘 API Endpoints

### Authentication
- `POST /api/register`
- `POST /api/login`
- `POST /api/logout` (requires auth)
- `GET /api/google/redirect`
- `GET /api/google/callback`
- `POST /api/google/token`

### Customer / Public
- `GET /api/getproduct`
- `GET /api/getcategory`
- `GET /api/detailproduct/{slug}`

### Orders
- `POST /api/order`
- `GET /api/orders`
- `GET /api/orders/today/count`

### Admin (Protected by `auth:api`)
- `GET /api/users`
- `POST /api/users`
- `GET /api/users/{id}`
- `PUT /api/users/{id}`
- `DELETE /api/users/{id}`

- `GET /api/category`
- `POST /api/category`
- `GET /api/category/{id}`
- `PUT /api/category/{id}`
- `DELETE /api/category/{id}`

- `GET /api/product`
- `POST /api/product`
- `GET /api/product/{id}`
- `PUT /api/product/{id}`
- `DELETE /api/product/{id}`

- `GET /api/roles`
- `POST /api/roles`
- `GET /api/roles/{id}`
- `PUT /api/roles/{id}`
- `DELETE /api/roles/{id}`

- `GET /api/permissions`
- `POST /api/permissions`
- `GET /api/permissions/{id}`
- `PUT /api/permissions/{id}`
- `DELETE /api/permissions/{id}`

---

## 📥 Example Requests

### Register

```bash
curl -X POST http://localhost/api/register \
  -F "name=John Doe" \
  -F "email=john@example.com" \
  -F "password=password123" \
  -F "password_confirmation=password123"
```

### Login

```bash
curl -X POST http://localhost/api/login \
  -H "Content-Type: application/json" \
  -d '{"email":"john@example.com", "password":"password123"}'
```

### Get Products

```bash
curl http://localhost/api/getproduct
```

### Create Order

```bash
curl -X POST http://localhost/api/order \
  -H "Content-Type: application/json" \
  -d '{
    "name":"John Doe",
    "email":"john@example.com",
    "total_cost":15000000,
    "items":[{"product_id":1,"quantity":2,"price":7500000}]
  }'
```

---

## 📁 Project Structure

- `backend/` - Laravel backend application code
- `backend/routes/api.php` - API route definitions
- `backend/public/` - public assets for backend
- `frontend/` - React frontend application
- `frontend/src/` - frontend source code
- `frontend/public/images/Doc/` - frontend documentation images
- `docker-compose.yml` - Docker Compose configuration
- `Dockerfile` - PHP-FPM container configuration

---

## 📎 Notes

- Make sure backend `.env` database settings match the MySQL service from `docker-compose.yml`.
- Google login requires valid OAuth credentials in the backend `.env` and `VITE_GOOGLE_CLIENT_ID` in frontend `.env`.
- The frontend is configured to talk to the backend API via `VITE_API_URL`.
- Admin routes require a valid JWT token.

---

## ✅ Ready to Use

This README combines backend and frontend documentation so you can run the fullstack React + Laravel product API app with a single reference.
