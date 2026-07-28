# AgroVerse Nepal — B2B Agriculture Wholesale Marketplace

A demo-data scaffold for a bulk-only agriculture wholesale marketplace, built
with HTML5, CSS3 and vanilla JavaScript (ES6+), following the structure in
the project brief. This is a **skeleton**: folders, sample JSON data, shared
components and a handful of fully-built representative pages, ready to be
filled out and connected to a real backend.

## Running it locally

Fetching local JSON files with `fetch()` doesn't work when you open
`index.html` directly (`file://` URLs block it). Serve the folder instead:

```bash
# Option 1
npx serve .

# Option 2
python3 -m http.server 8080
```

Then open `http://localhost:3000` (or `:8080`) in your browser.

## Folder structure

```
agroverse-nepal/
├── index.html                # Homepage (all sections wired to sample data)
├── robots.txt, sitemap.xml   # SEO basics
├── css/
│   ├── base.css              # Design tokens, resets, buttons, cards, forms
│   ├── layout.css            # Header, mega menu, footer
│   ├── components.css        # Hero, product cards, ticker, FAQ, etc.
│   └── admin.css             # Shared admin/dashboard shell (incl. dark mode)
├── js/
│   ├── data-service.js       # ONLY place that knows where data comes from
│   ├── utils.js               # formatNPR, toast, debounce, escapeHTML…
│   ├── cart.js                # Demo bulk cart + wishlist (localStorage)
│   ├── components/            # Reusable UI: header, footer, product card,
│   │                           # category slider, price ticker, FAQ/back-to-top,
│   │                           # admin sidebar, dashboard sidebar
│   ├── pages/                 # Per-page scripts (home, products, product-detail)
│   └── admin/                 # Admin dashboard + manage-products example
├── data/                      # Sample JSON: products, categories, users,
│                               # orders, districts/provinces, market-prices
├── pages/                     # Public pages (products, product-detail, login,
│                               # register, about, contact, policies, etc.)
├── admin/                     # Admin panel shell (overview + Manage Products)
├── dashboard/
│   ├── farmer/                # Farmer dashboard overview
│   ├── buyer/                 # Buyer dashboard overview
│   └── wholesaler/            # Wholesaler dashboard overview
├── assets/images, assets/icons
└── api/                       # README describing backend integration points
```

## What's fully built vs. scaffolded

**Fully built (real interactivity, wired to sample JSON):**
- Homepage — hero, search, category slider, market price table, 8 product
  rails (featured/trending/seasonal/organic/wholesale/flash/daily/recent),
  top farmers/cooperatives, news, testimonials, partners, FAQ accordion,
  newsletter, footer.
- Product catalog (`pages/products.html`) — category/district/price/organic/
  rating filters, sorting, live result count.
- Product detail (`pages/product-detail.html`) — gallery, tabs, quantity
  stepper respecting MOQ/max order, add-to-cart, wishlist, quote request.
- Login / Register — role selection, OTP tab, Google login placeholder.
- Admin dashboard — stat cards, 7-day order chart, recent orders table, dark
  mode toggle, and one full CRUD-style listing (`manage-products.html`) you
  can copy for the other "Manage X" screens in the sidebar.
- Farmer / Buyer / Wholesaler dashboards — role-specific sidebar and an
  overview page reading each role's own orders/products from sample data.

**Scaffolded (header/footer + design system wired, content is placeholder):**
- About, Contact, FAQ, Market Price, Blog, Wholesale Deals, District
  Products, Become a Seller, Farmer Registration, Support, Compare, and all
  policy pages (Privacy, Terms, Refund, Shipping), plus Forgot Password.
- Every other "Manage X" admin screen listed in the sidebar (Manage
  Categories, Farmers, Buyers, Wholesalers, Cooperatives, Orders, Delivery,
  Reviews, Coupons, Blogs, Banners, FAQ, Districts, Roles, Taxes, Settings) —
  build them the same way as `manage-products.html`.
- The rest of each dashboard's sub-pages (Profile, Inventory, Payments,
  Certificates, Analytics for Farmer; Wishlist, Quotations, Invoices, Saved
  Suppliers for Buyer; Purchase Requests, Bulk Orders, Customers, Reports for
  Wholesaler) — the sidebar already links to them, the pages just need to be
  created following the `index.html` pattern in each folder.

## Extending to a real backend

All data flows through `js/data-service.js`. To connect Firebase, Supabase,
Node.js or Laravel, only that file needs to change — every component and
page calls `DataService.getX()` and never touches `fetch()` directly. See
`api/README.md` for suggested endpoints.

## Notes

- Cart/wishlist state uses `localStorage` for this demo — swap for real
  backend calls when ready.
- Icons: Font Awesome (CDN). Fonts: Poppins (Google Fonts CDN). Animation:
  AOS (CDN) is wired on the homepage; add GSAP/Lottie the same way if needed.
- Payment gateways (eSewa, Khalti, FonePay, IME Pay) are named as placeholders
  per the brief — no real payment integration is included.
