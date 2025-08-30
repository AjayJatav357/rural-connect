# Rural Connect — Mini Full-Stack Prototype

A simple platform to help rural communities find and access essential products and services.

## Tech Stack
- **Frontend:** React + Vite, React Router
- **Backend:** Node.js + Express
- **Database:** MongoDB (Mongoose)
- **Auth:** JWT
- **Deployment (optional):** Vercel/Netlify (client) & Render/Railway (server)

## Features Covered
- Attractive responsive homepage with:
  - Navbar (Logo, Home, Services, Products, Contact)
  - **Our Services** (≥5 with icons)
  - **Available Products** (≥6 with price + icons)
  - **News & Updates** (static 2–3 headlines)
  - **Contact Us** (address, helpline, form)
- Signup/Login (JWT)
- User Dashboard (welcome + bookings list)
- Product search/filter
- Add to cart and place **booking** (saved in DB)
- Edit profile (display name, phone)
- API endpoints:
  - `GET /api/services`
  - `GET /api/products?q=term`
  - `GET /api/news`
  - `POST /api/register`
  - `POST /api/login`
  - `POST /api/contact`
  - `POST /api/bookings` (auth)
  - `GET /api/bookings` (auth)
  - `PUT /api/profile` (auth)

## How to Run Locally

### 1) Prerequisites
- Node.js 18+
- MongoDB running locally or Atlas connection string

### 2) Setup Server
```bash
cd server
cp .env.example .env
# edit .env to set MONGO_URI and JWT_SECRET
npm install
npm run seed   # seed products & services (optional but recommended)
npm run dev
```
Server will run at `http://localhost:5000`.

### 3) Setup Client
```bash
cd ../client
npm install
npm run dev
```
Client dev server at `http://localhost:5173` with proxy to `/api`.

### Demo Login
- Register a new account in the UI (`/register`), or use the same email/password you set at signup to login.

## Folder Structure
```
rural-connect/
  server/
    src/
      models/ (User, Product, Service, Booking, Contact)
      routes/ (auth, products, services, news, contact, bookings)
      middleware/auth.js
      index.js
      seed.js
  client/
    src/
      pages/ (Home, Login, Register, Dashboard, Products, Services, Profile, Contact)
      components/ (ProtectedRoute, ProductCard, ServiceCard)
      App.jsx, main.jsx, styles.css, api.js
```
## Deploy Tips
- **Client:** Build and deploy with Netlify/Vercel. Set `VITE_API_BASE` if you later move API.
- **Server:** Deploy on Render/Railway. Set environment variables `PORT`, `MONGO_URI`, `JWT_SECRET`.
