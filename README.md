# 🔥 Ember & Ash — Restaurant Website

> A fully responsive, production-ready restaurant website with a dynamic menu, smart cart system, and a complete multi-method payment gateway — built entirely with vanilla HTML, CSS, and JavaScript.

---

## 📸 Preview

![Bhai G & Cafe Hero](https://images.unsplash.com/photo-1544025162-d76594e3d3e0?w=1200&q=80)

---

## ✨ Features

### 🍽️ Menu & Discovery
- Full-page hero section with animated entrance
- Sticky navigation bar with smooth scroll
- 15 menu items across 5 categories — Starters, Mains, From the Grill, Desserts, and Drinks
- Category filter buttons with animated card transitions
- Item badges — Chef's Pick, Signature, Veg, Spicy, New, Non-Alc

### 🛒 Cart System
- Slide-in cart drawer from the right
- Add / remove items with live quantity controls
- Real-time subtotal, 8% tax, and service charge calculation
- Cart badge in nav with bounce animation on update
- Empty state with prompt to browse

### 💳 3-Step Payment Gateway

| Step | Description |
|------|-------------|
| **Step 1 — Details** | Name, email, phone, order type (Dine In / Takeaway / Home Delivery), table number, address, and special instructions |
| **Step 2 — Payment** | Choose from Card, UPI, Digital Wallet, or Cash on Delivery |
| **Step 3 — Review** | Full order summary, delivery details, and payment confirmation before placing |

### 💰 Payment Methods Supported
- **💳 Credit / Debit Card** — real-time number formatting, expiry auto-format, CVV, card brand detection (Visa / Mastercard / Amex)
- **📱 UPI** — UPI ID entry with live verification + shortcut buttons for GPay, PhonePe, Paytm, BHIM
- **👛 Digital Wallet** — Apple Pay, Google Pay, PayPal, Amazon Pay
- **💵 Cash on Delivery** — with order confirmation flow

### ⚡ UX & Animations
- Animated spinner during payment processing
- Order confirmation screen with unique Order ID
- Toast notifications for every cart action
- CSS-only page-load staggered animations
- Hover effects and micro-interactions throughout

---

## 🗂️ Project Structure

```
Bhai G & Cafe/
│
├── index.html          # Single-file application (HTML + CSS + JS)
└── README.md           # Project documentation
```

> This is a single-file project — everything lives in `index.html` with no external dependencies.

---

## 🚀 Getting Started

### Option 1 — Open Directly
Just open `index.html` in any modern browser. No build step, no server required.

```bash
# Clone the repository
git clone https://github.com/your-username/ember-and-ash.git

# Navigate into the project
cd Bhai-G-Cafe-Restaurant

# Open in browser
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

### Option 2 — Live Server (Recommended for Development)
If you have VS Code, use the [Live Server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) for hot-reload during development.

---

## 🛠️ Tech Stack

| Technology | Usage |
|------------|-------|
| **HTML5** | Semantic structure and layout |
| **CSS3** | Animations, transitions, CSS variables, Grid & Flexbox |
| **Vanilla JavaScript** | Cart logic, payment flow, form validation, DOM manipulation |
| **Google Fonts** | Cormorant Garamond (display) + DM Sans (body) |
| **Unsplash** | Food photography via CDN |

> **Zero dependencies.** No frameworks, no npm, no bundler.

---

## 💡 How to Customize

### Change Restaurant Name & Branding
Edit the name, tagline, and address directly in `index.html`:
```html
<!-- Hero -->
<h1>Bhai G <br><em>&amp; Cafe</em></h1>
<p class="hero-sub">Fire-kissed cuisine · Artisanal ingredients · Soulful ambiance</p>

<!-- Footer -->
<div>Sudpura Kashganj, Uttar Pradesh · Mon–Sun 9am–10pm</div>
```

### Change Color Theme
Update CSS variables at the top of the `<style>` block:
```css
:root {
  --cream:    #f5f0e8;   /* background */
  --charcoal: #1a1a18;   /* dark / text */
  --ember:    #c4622d;   /* primary accent */
  --gold:     #b89a5a;   /* secondary accent */
}
```

### Add / Edit Menu Items
Each menu card follows this pattern:
```html
<div class="card"
  data-cat="mains"
  data-name="Your Dish Name"
  data-price="25"
  data-img="https://your-image-url.com/photo.jpg">

  <div class="card-img" style="background-image:url('...')">
    <span class="card-badge new">New</span>
  </div>

  <div class="card-body">
    <div class="card-category">Mains</div>
    <div class="card-title">Your Dish Name</div>
    <div class="card-desc">Short description of the dish.</div>
    <div class="card-footer">
      <div class="price">$25 <span>/ plate</span></div>
      <button class="add-btn" onclick="addToCart(this)">+</button>
    </div>
  </div>
</div>
```

**Available badge types:**
```html
<span class="card-badge new">New</span>      <!-- ember red -->
<span class="card-badge veg">Veg</span>      <!-- green -->
<span class="card-badge spicy">Spicy</span>  <!-- dark red -->
<span class="card-badge">Custom</span>       <!-- charcoal (default) -->
```

### Adjust Tax & Service Charge
Find these two functions in the `<script>` block:
```javascript
function getTax()   { return getSubtotal() * 0.08; }  // 8% tax
function getTotal() { return getSubtotal() + getTax() + 2; }  // $2 service charge
```

---

## 🔌 Connecting a Real Payment Gateway

This project uses a **simulated front-end payment flow**. To process real payments, integrate one of these:

| Gateway | Best For | Docs |
|---------|----------|------|
| [Stripe](https://stripe.com/docs) | Global card payments | [stripe.com/docs](https://stripe.com/docs) |
| [Razorpay](https://razorpay.com/docs) | India (UPI, cards, wallets) | [razorpay.com/docs](https://razorpay.com/docs) |
| [PayPal](https://developer.paypal.com) | Global PayPal & card | [developer.paypal.com](https://developer.paypal.com) |
| [Square](https://developer.squareup.com) | POS + online | [developer.squareup.com](https://developer.squareup.com) |

**Example — Adding Stripe.js:**
```html
<script src="https://js.stripe.com/v3/"></script>
<script>
  const stripe = Stripe('YOUR_PUBLISHABLE_KEY');
  // Replace processPayment() with Stripe's confirmCardPayment()
</script>
```

> ⚠️ Always handle payment processing **server-side** to keep secret keys secure. Never expose secret keys in front-end code.

---

## 📱 Responsive Design

| Breakpoint | Behaviour |
|------------|-----------|
| Desktop (> 768px) | Full nav, 3-column menu grid, side-by-side about section |
| Mobile (≤ 768px) | Hamburger-style nav hidden, 1-column grid, stacked about section, single-column checkout form |

---

## 🧪 Testing the Payment Flow

Use these test details to walk through the full checkout:

| Field | Value |
|-------|-------|
| Card Number | `4242 4242 4242 4242` |
| Expiry | Any future date (e.g. `12 / 27`) |
| CVV | Any 3 digits (e.g. `123`) |
| UPI ID | Any string with `@` (e.g. `test@okaxis`) |

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🙌 Acknowledgements

- Food photography by [Unsplash](https://unsplash.com)
- Typography — [Cormorant Garamond](https://fonts.google.com/specimen/Cormorant+Garamond) & [DM Sans](https://fonts.google.com/specimen/DM+Sans) via Google Fonts

---


