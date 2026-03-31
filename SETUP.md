# BRUKIBAR Website — Setup Guide

## 📸 Adding Your Product Photos

Your website references 3 product images. Save your 3 bottle photos to the `images/` folder with these exact names:

```
images/
  bottle1.jpg   ← single bottle photo (used in hero section + cart)
  bottle2.jpg   ← 2-bottle photo
  bottle3.jpg   ← angled shot photo
```

The website will automatically display them once saved there.

---

## 🚀 Push to GitHub (Step-by-Step)

### Step 1 — Install Git (if not already installed)
Download from: https://git-scm.com/downloads

### Step 2 — Create a GitHub account
Go to https://github.com and sign up (free)

### Step 3 — Create a new repository
1. Click the **+** button → **New repository**
2. Name it: `brukibar` (or `brukibar-website`)
3. Set to **Public**
4. Do NOT check "Add README" (you already have files)
5. Click **Create repository**

### Step 4 — Open Terminal / Command Prompt
Navigate to your BRUKIBAR folder and run these commands **one by one**:

```bash
# Initialize git
git init

# Add all files
git add .

# First commit
git commit -m "Launch BRUKIBAR website"

# Connect to your GitHub repo (replace YOUR-USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR-USERNAME/brukibar.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 5 — Enable GitHub Pages (Free Hosting!)
1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (left sidebar)
3. Under **Source**, select **Deploy from a branch**
4. Choose **main** branch → **/ (root)** → click **Save**
5. Wait ~2 minutes, then your site will be live at:
   `https://YOUR-USERNAME.github.io/brukibar/`

---

---

## 💳 Paystack Mobile Money Setup (REQUIRED to accept payments)

The website uses **Paystack** to process MTN Mobile Money payments. You need a free Paystack account to receive real money.

### Step 1 — Create your Paystack account
Go to https://paystack.com/gh/signup and sign up (it's free for Ghanaian businesses)

### Step 2 — Get your Public Key
1. Log in to your Paystack dashboard at https://dashboard.paystack.com
2. Go to **Settings → API Keys & Webhooks**
3. Copy your **Live Public Key** (it looks like: `pk_live_xxxxxxxxxxxxxxxx`)

### Step 3 — Add your key to the website
Open `index.html` and find this line near the top of the `<script>` section:

```javascript
const PAYSTACK_PUBLIC_KEY = 'pk_test_REPLACE_WITH_YOUR_PAYSTACK_PUBLIC_KEY';
```

Replace it with your actual live key:

```javascript
const PAYSTACK_PUBLIC_KEY = 'pk_live_xxxxxxxxxxxxxxxx';
```

### Step 4 — Set up your settlement account
In your Paystack dashboard, go to **Settings → Bank Accounts** and add your MTN Mobile Money number (0551456448) so payments are settled directly to your account.

> **Note:** For testing before going live, use your test key (`pk_test_...`) which lets you do test transactions without real money.

---

## 📱 Notification System
When a customer pays, Paystack verifies the payment and then a **WhatsApp message** automatically opens to your number (+233551456448) with the full confirmed order details.

When a bulk order form is submitted, WhatsApp also opens with the full request.
