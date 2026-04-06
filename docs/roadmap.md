# Project Roadmap

## Goal

Build a scalable headless e-commerce platform with a public storefront, customer flows, admin operations, inventory management, and webhook-driven payment processing.

The roadmap is intentionally structured around **business flows and core domains**, not only screens or isolated technical tasks.

---

## Phase 0 — Planning and Repository Setup

### Objectives
- Define the MVP scope
- Establish repository structure
- Prepare initial documentation
- Set up the local development strategy

### Tasks
- Finalize project naming and repository metadata
- Prepare README, LICENSE, and `.gitignore`
- Define initial architecture notes
- Define the first folder structure for backend and frontend
- Decide local environment strategy with Docker

### Deliverables
- GitHub repository initialized
- Base documentation committed
- Initial project structure ready

---

## Phase 1 — Foundation Setup

### Objectives
- Scaffold backend and frontend applications
- Prepare shared development environment
- Establish base technical conventions

### Tasks
- Initialize Laravel backend
- Initialize Nuxt frontend
- Configure PostgreSQL
- Configure Redis
- Prepare Docker Compose for local development
- Define environment variable strategy
- Configure base routing and API connectivity
- Prepare initial formatting and linting setup

### Deliverables
- Running local environment
- Backend and frontend bootstrapped
- Initial developer workflow established

---

## Phase 2 — Catalog Domain

### Objectives
- Build the core product browsing experience
- Implement the first catalog-related domain structures

### Tasks
- Create categories, products, variants, and images data model
- Create public catalog endpoints
- Implement storefront listing pages
- Implement product detail pages
- Add category navigation
- Add basic search
- Seed development data

### Deliverables
- Public catalog available
- Product pages working
- Category-based navigation available

---

## Phase 3 — Customer Accounts

### Objectives
- Allow customers to register and manage their account data

### Tasks
- Implement registration and login
- Implement authenticated customer area
- Add customer profile page
- Add address management
- Protect account routes
- Connect frontend auth flows with backend API

### Deliverables
- Functional customer authentication
- Account area available
- Customer addresses persisted

---

## Phase 4 — Cart

### Objectives
- Build the cart workflow as the base for checkout

### Tasks
- Create cart and cart items domain model
- Add add-to-cart action
- Add update quantity action
- Add remove item action
- Persist cart state
- Validate product availability
- Implement cart page in storefront

### Deliverables
- Functional cart workflow
- Cart data persisted correctly
- Basic stock validation in place

---

## Phase 5 — Checkout and Orders

### Objectives
- Build the order creation flow before payment confirmation

### Tasks
- Create checkout process
- Capture shipping and billing information
- Generate order records from cart
- Generate order items
- Define initial order status model
- Add customer order history
- Add customer order detail page

### Deliverables
- Checkout flow available
- Orders created in pending payment state
- Customer order history working

---

## Phase 6 — Payments and Webhooks

### Objectives
- Integrate payment provider flows correctly
- Ensure backend-controlled payment confirmation

### Tasks
- Integrate Stripe and/or Mercado Pago
- Create payment session or payment intent flow
- Add webhook endpoints
- Validate webhook signatures
- Persist payment events
- Update order status after verified payment events
- Handle failed payment flows
- Add idempotency protections where needed

### Deliverables
- Real payment flow working
- Verified webhook processing
- Orders updated by backend after payment confirmation

---

## Phase 7 — Admin Operations

### Objectives
- Add operational tools to manage the store

### Tasks
- Implement admin authentication
- Add product CRUD
- Add category CRUD
- Add inventory management views
- Add order management views
- Add order status update actions
- Add basic customer overview
- Add initial admin dashboard

### Deliverables
- Admin area working
- Store can be managed operationally
- Products, stock, and orders manageable from admin

---

## Phase 8 — Notifications, Hardening, and Deployment

### Objectives
- Stabilize the MVP and prepare it for public deployment

### Tasks
- Add transactional emails
- Add jobs and queues
- Improve validation and error handling
- Add basic automated tests
- Add rate limiting and permissions checks
- Add production-ready environment configuration
- Prepare deployment setup
- Document deployment steps

### Deliverables
- MVP deployed
- Core workflows stable
- Initial production-ready baseline available

---

## Post-MVP Enhancements

Potential improvements after the MVP:

- Advanced search
- Promotion and coupon rules
- Wishlist
- Reviews
- Inventory alerts
- ERP / CRM integrations
- Analytics dashboard
- B2B features
- Marketplace synchronization
- Mobile client support

---

## Guiding Principles

Throughout development, the project should prioritize:

- backend as the source of truth
- modular domain organization
- thin controllers and clear service boundaries
- payment confirmation via webhook validation
- maintainable production-style structure
- incremental delivery by business value