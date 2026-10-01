# 🌿 7Seasonsplants - Complete Site & Database Backup

> **Live Production E-Commerce Application for Exotic Plants, Combos & Gardening Care**

---

## 📦 What is Included in this Full Site Backup

1. **Frontend Application (`src/`)**:
   - Modern React 19 SPA powered by Vite & TypeScript
   - Tailwind CSS v4 styling with custom animations & botanical emerald/rose color palette
   - Full botanical e-commerce catalog (Combos, Products, Categories, Daily Deals, Wishlist, Cart)
   - Real-time Order Tracking, State Delivery Restrictions (Kerala & Tamil Nadu express logistics)
   - Customer Reviews system with Admin Moderation
   - AI Plant Doctor & Botanical Care Chatbot (powered by Gemini API)
   - Interactive plant care guides, nursery blogs, and dynamic hero banners
   - Mobile-first responsive UI with touch gestures and bottom mobile navigation

2. **Backend Server (`server.ts` & `server/`)**:
   - Express server with integrated Vite middleware
   - Google Gemini API AI endpoint (`/api/gemini/chat`) with botanical knowledge base fallback
   - Secure Razorpay payment gateway integration (`/api/razorpay/create-order`, `/api/razorpay/verify-payment`)
   - SMTP Email service with OTP generation & order confirmation notifications
   - Image upload pipeline (`/api/upload`)
   - Instant Backup Download service (`/api/backup/download` & `/api/backup/info`)

3. **Complete Database & Data Backup (`database_backup/`)**:
   - Consolidated master database dump: `full_database_backup.json`
   - Individual Firestore collections: `combos.json`, `products.json`, `categories.json`, `orders.json`, `users.json`, `banners.json`, `coupons.json`, `dailyDeals.json`, `plantCareGuides.json`, `blogs.json`, `storeSettings.json`
   - Seed & fallback data: `seed_reviews.json`, `seed_products.json`, `seed_combos.json`, etc.

4. **Security & Configuration**:
   - `firebase-applet-config.json` & `firestore.rules` for Cloud Firestore and Firebase Auth
   - `.env.example` with complete environment variable template
   - `vercel.json` for one-click Vercel deployment

---

## 🚀 Quick Start (Running Locally)

### Prerequisites
- Node.js (v18 or higher recommended, Node v20/22 verified)
- npm, yarn, or pnpm

### 1. Extract the Backup Archive
If you received the `.zip` or `.tar.gz` file:
```bash
# For zip:
unzip 7seasonsplants-full-site-backup.zip
cd 7seasonsplants-backup

# Or for tar.gz:
tar -xzf 7seasonsplants-full-site-backup.tar.gz
cd 7seasonsplants-backup
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Setup Environment Variables
Copy `.env.example` to `.env`:
```bash
cp .env.example .env
```
Fill in any optional services (Razorpay, Gemini API, SMTP email) as needed. The site functions with built-in fallbacks if optional keys are omitted.

### 4. Start Development Server
```bash
npm run dev
```
Open your browser at [http://localhost:3000](http://localhost:3000).

---

## 🏗️ Production Build & Deployment

### Build for Production
```bash
npm run build
```
This compiles the Vite frontend into `dist/` and bundles `server.ts` into `dist/server.cjs`.

### Run Production Server
```bash
npm start
```

### Deploying to Vercel (Hobby Plan Friendly)
This project is pre-configured and 100% optimized for the **Vercel Hobby Plan**:
1. **Single Serverless Function Architecture**: Consolidated into `api/index.js`, using only **1 of 12** allowed Serverless Functions on the Hobby tier (92% free headroom).
2. **Sub-second Response Times & Timeout Resilience**: Optimized to complete well within Vercel Hobby's 10-second function limit, with in-memory caching and resilient fallbacks.
3. **Stateless Ephemeral Storage**: Uploaded plant photos and backups are safely handled via `/tmp` cache and permanently preserved in Cloud Firestore (`uploaded_images`), preventing `EROFS` errors.
4. **Instant Edge Caching**: Vite static assets (`/assets/*`) receive 1-year immutable cache headers, minimizing compute usage and bandwidth on the Hobby plan.

**Steps to Deploy on Vercel:**
1. Push your repository to GitHub or GitLab.
2. Go to [vercel.com](https://vercel.com) and click **"Add New Project"**.
3. Import the repository. Vercel will automatically detect `Vite` as the framework preset and `dist` as the output directory.
4. Add your Environment Variables in the Vercel project settings (from `.env.example`).
5. Click **"Deploy"**. The site and all API routes (`/api/*`) will be live immediately!

### Deploying to Cloud Run / Docker / VPS
- **Docker / Cloud Run**: A standard Node.js Docker container running `npm run build && npm start` on port 3000.
- **Firebase Hosting**: Connect with `firebase deploy --only hosting,firestore:rules`.

---

## 🗄️ Database Information
- Database: Google Cloud Firestore (`season-445ff`)
- Security Rules: Defined in `firestore.rules`
- Backup Location: `database_backup/` contains all exported JSON files.

---

© 2026 7Seasonsplants. All rights reserved.
