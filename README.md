# TECHNICAL & STORE – ADVANCED E-COMMERCE PLATFORM

> Complete, modern, full-stack electronics and technical services e-commerce ecosystem built with **HTML5, CSS3, Vanilla JavaScript, Node.js, Express.js, and MySQL (with instant auto-fallback storage)**.

---

## 🌟 Key Features

### 🛍️ Public Customer Storefront (`/frontend`)
- **Modern Homepage:** Dynamic flagship slider, category cards, featured & deal carousels, customer testimonials, and trust features.
- **Catalog & Search:** Live keyword search, category filter sidebar, price slider/inputs, stock filter, multiple sorting algorithms.
- **Product Details:** Multi-image gallery with zoom/thumbnails, real-time stock indicator, tabbed specifications, customer review ratings, and review submission form.
- **Shopping Cart:** Quantity increment/decrement, live subtotal, dynamic shipping calculation, promo code verification (`TECH10` for 10% off), and persistent LocalStorage sync.
- **Checkout Flow:** Customer contact form, address destination, cash on delivery, bank wire, or direct WhatsApp ordering with instant order number generation (e.g. `TS-849201`).
- **Technical Services:** Certified lab repairs, custom liquid cooling build, forensic data rescue, enterprise network setup with instant WhatsApp service booking.
- **WhatsApp Integration:** Full order summary and direct customer chat using the official business phone number configured in Admin Settings.
- **Contact Desk:** Customer inquiries with direct message delivery to Admin Portal.

### 🛡️ Secure Admin Dashboard (`/admin`)
- **Dashboard Overview:** 6 real-time stat cards (Total Gross Sales, Total Orders, Total Products, Total Customers, Pending Orders, Low Stock Alerts).
- **Revenue Analytics:** 6-month visual revenue chart and best-selling product lists.
- **Inventory Management:** Full CRUD operations for products (image upload with Multer, specifications builder, regular/discount pricing, stock controls, featured flags).
- **Category Management:** Create, list, and delete custom product categories with FontAwesome icons.
- **Order Management:** View all incoming orders, filter by 6 statuses (`Pending`, `Confirmed`, `Processing`, `Shipped`, `Delivered`, `Cancelled`), direct WhatsApp customer chat, and **Print Commercial Invoices** (with print CSS styling).
- **Customer Management:** Buyer profiles, contact information, lifetime spend, and purchase history.
- **Inquiry Management:** Read customer contact inquiries, mark as read, and reply directly via WhatsApp or Email.
- **Reports & CSV Exports:** Instant one-click CSV downloads for Sales, Orders, Inventory, and Customers.
- **Website Settings:** Customize Business Name, official WhatsApp Business Number, support phone/email, currency, shipping fees, free shipping threshold, and Admin password change.

---

## ⚙️ Technology Stack

| Layer | Technologies |
|---|---|
| **Frontend** | HTML5, CSS3 (Custom Variables, Responsive Grid, Flexbox), Vanilla JavaScript (Modular ES6+) |
| **Backend** | Node.js, Express.js, JWT (`jsonwebtoken`), Password Hashing (`bcryptjs`), File Uploads (`multer`), CORS, Rate Limiting |
| **Database** | MySQL (via `mysql2/promise`) + Built-in Persistent Relational Fallback Engine |
| **Styling** | Dark Navy (`#0a1128`), Electric Blue (`#0066ff`), Electric Cyan (`#00d2ff`), White (`#ffffff`), Light Gray (`#f8fafc`) |

---

## 🚀 Quick Start Guide

### 1. Prerequisites
- **Node.js** v18+ installed on your machine.
- (Optional) **MySQL** server running if you wish to use MySQL directly.

### 2. Installation
Open your terminal in the project directory:

```bash
# Navigate to the project root
cd "c:\Users\Eng Ismail\Desktop\technical&store"

# Install dependencies
npm install
```

### 3. Environment Setup
The project includes pre-configured `.env.example` and `.env` files.
To customize settings, edit `.env`:

```env
PORT=5000
NODE_ENV=development
JWT_SECRET=technical_and_store_secure_jwt_token_key_2026_xyz987
JWT_EXPIRE=24h

# Database Configuration:
# Set to 'mysql' or 'auto' (auto detects MySQL, falls back to persistent store if MySQL is offline)
DB_TYPE=auto
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=
DB_NAME=technical_store

# Official WhatsApp Number for Orders & Support (Country code without symbols, e.g. 15551234567)
DEFAULT_WHATSAPP_NUMBER=15551234567
DEFAULT_BUSINESS_NAME=TECHNICAL & STORE
DEFAULT_CURRENCY=$
DEFAULT_SHIPPING_FEE=15.00
DEFAULT_FREE_SHIPPING_MIN=150.00
```

### 4. Database Setup

#### Option A: Automatic Out-of-the-Box Mode (Zero Configuration)
If MySQL is not installed or running, the platform automatically boots using its built-in persistent relational engine (`database/store.json`). It seeds 12+ demo tech products, categories, technical services, customer orders, and default admin credentials immediately.

#### Option B: MySQL Mode
1. Open your MySQL client (e.g. phpMyAdmin, MySQL Workbench, or CLI).
2. Execute the provided SQL schema script:
   ```bash
   mysql -u root -p < database/schema.sql
   ```
3. Update your `DB_USER` and `DB_PASSWORD` in `.env`.
4. Run the seeder to populate demo data:
   ```bash
   npm run seed
   ```

### 5. Starting the Server
```bash
# Start production server
npm start

# Or start with auto-reload (development mode)
npm run dev
```

The server will display:
```
================================================================
🚀 TECHNICAL & STORE platform active on http://localhost:5000
🛍️ Customer Website:   http://localhost:5000
🛡️ Admin Dashboard:    http://localhost:5000/admin/login.html
📊 Active DB Engine:   JSON / MYSQL
================================================================
```

---

## 🔑 Default Admin Credentials

| Role | Email | Password |
|---|---|---|
| **Administrator** | `admin@technicalstore.com` | `Admin@123456` |

*Tip: On the Admin Login page (`/admin/login.html`), you can click **"Autofill Credentials"** to quickly log in with one click.*

---

## 📱 WhatsApp Ordering Workflow

1. Customer adds products to the shopping cart.
2. At checkout, the customer enters their delivery information and selects **"Direct WhatsApp Order & Instant Verification"** or clicks **"Order on WhatsApp"** on any product page.
3. The platform saves the order with status `Pending` in the database, generates a unique Order Number (e.g. `TS-749201`), and constructs a formatted message:
   ```text
   🛒 *NEW ORDER: #TS-749201*
   ━━━━━━━━━━━━━━━━━━━━━━
   👤 *Customer Details:*
   • *Name:* Alexander Wright
   • *Phone:* +1 415 555 0192
   • *Address:* 450 Mission Street, Apt 12B, San Francisco

   📦 *Ordered Items:*
    1. 1x TitanPro Stealth 16" Gaming Laptop — $2,299.00

   💰 *Order Summary:*
   • *Subtotal:* $2,299.00
   • *Shipping:* FREE Shipping
   • *Grand Total:* *$2,299.00*
   • *Payment Method:* WhatsApp Order
   ━━━━━━━━━━━━━━━━━━━━━━
   _Thank you for ordering with TECHNICAL & STORE!_
   ```
4. The system automatically launches WhatsApp (Desktop or Web) directing to the business phone number set in **Admin Settings**.
5. The Administrator can view the order in the Admin Dashboard, change status to `Confirmed` / `Shipped`, and click **"Chat Customer"** on WhatsApp at any time.

---

## 🖨️ Printing Invoices

In the Admin Dashboard under **Orders** (`/admin/orders.html`), click **Details** on any order and then click **"Print Invoice"**. The system renders a clean commercial invoice including:
- Company Branding & Support Contacts
- Invoice Number and Order Timestamp
- Customer Billing & Delivery Information
- Itemized Products Table with Line Totals
- Subtotal, Shipping, Taxes, and Grand Total
- 2-Year Official Warranty Guarantee and Terms

---

## 📂 Project Architecture

```
technical-store/
├── .env                  # Live environment variables
├── .env.example          # Example environment template
├── package.json          # Node dependencies & scripts
├── README.md             # Complete documentation
│
├── database/
│   ├── schema.sql        # MySQL complete relational schema DDL
│   ├── seed.js           # Seeder script with rich demo catalog
│   └── store.json        # Auto-persisting local relational store
│
├── backend/
│   ├── server.js         # Main Express API entrypoint
│   ├── config/
│   │   └── db.js         # Unified MySQL / persistent DB connector
│   ├── controllers/      # REST API controllers
│   │   ├── authController.js
│   │   ├── productController.js
│   │   ├── categoryController.js
│   │   ├── orderController.js
│   │   ├── customerController.js
│   │   ├── messageController.js
│   │   ├── reviewController.js
│   │   ├── serviceController.js
│   │   ├── settingsController.js
│   │   └── reportController.js
│   ├── models/
│   │   └── dbModels.js   # Unified entity models & queries
│   ├── routes/           # Express endpoint definitions
│   ├── middleware/
│   │   ├── auth.js       # JWT Admin authentication guard
│   │   └── upload.js     # Multer image file upload handler
│   └── uploads/          # Uploaded product media files
│
├── frontend/             # Customer Website
│   ├── index.html        # Modern homepage with hero, categories & deals
│   ├── products.html     # Catalog with search, filter & sorting
│   ├── product-details.html # Product gallery, specs & reviews
│   ├── cart.html         # Shopping cart manager & promo codes
│   ├── checkout.html     # Order form & WhatsApp checkout
│   ├── about.html        # Company introduction & technical lab
│   ├── contact.html      # Contact form & FAQ accordion
│   ├── css/
│   │   └── style.css     # Premium dark navy & electric blue stylesheet
│   └── js/
│       ├── api.js        # Frontend REST API client
│       ├── cart.js       # LocalStorage reactive cart engine
│       └── main.js       # Global UI handlers & WhatsApp triggers
│
└── admin/                # Secure Administration Portal
    ├── login.html        # Admin authentication with one-click demo
    ├── dashboard.html    # Statistics, charts & recent orders
    ├── products.html     # Product inventory CRUD & image uploads
    ├── categories.html   # Category manager with icons
    ├── orders.html       # Order processing & printable invoices
    ├── customers.html    # Customer directory & order histories
    ├── messages.html     # Inquiries with WhatsApp/email reply
    ├── reports.html      # Financial summaries & CSV export downloads
    ├── settings.html     # Store settings, WhatsApp number & password change
    ├── css/
    │   └── admin.css     # Admin dashboard modern stylesheet
    └── js/
        ├── admin-api.js  # Authenticated Admin API client
        └── admin.js      # Admin UI controls & session guards
```

---

## 🔒 Security Best Practices Implemented
- Passwords encrypted with **Bcrypt** cryptographic salt rounds.
- Admin endpoints protected by **JWT Bearer Token** authentication.
- API requests guarded with **Rate Limiting** to prevent brute-force attacks.
- Inputs sanitized and parameterized against SQL injection.
- Database credentials stored exclusively in secure environment variables.
- Cross-Origin Resource Sharing (CORS) configured.
