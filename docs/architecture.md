# Architecture Notes

## Project Overview

Velora Commerce is a headless e-commerce platform designed to provide a scalable and maintainable foundation for modern online commerce.

The system is intended to support:

- SEO-friendly storefront pages
- Decoupled backend API
- Product catalog and category management
- Customer accounts and addresses
- Cart and checkout workflows
- Payment integrations with webhook-based confirmation
- Inventory management
- Administrative operations
- Future integrations with analytics, ERP/CRM systems, automation, and mobile clients

The architecture is designed to prioritize clarity, modularity, and production-style evolution over quick tutorial-style implementation.

---

## Architectural Style

The project follows a **modular headless architecture**.

The main building blocks are:

- **Frontend storefront**: public-facing user experience
- **Backend API**: business logic and source of truth
- **Database**: relational persistence
- **Async processes**: queues, notifications, webhook handling
- **External services**: payment providers, email services, future third-party integrations

This separation allows each layer to evolve independently while keeping business rules centralized in the backend.

---

## High-Level Components

### Frontend
The frontend is built with **Nuxt** and is responsible for:

- public storefront pages
- customer account pages
- cart and checkout UI
- consuming backend API endpoints
- rendering SEO-sensitive pages efficiently

### Backend
The backend is built with **Laravel** and is responsible for:

- authentication and authorization
- product, category, and inventory management
- cart and checkout orchestration
- order lifecycle management
- payment session creation
- webhook validation and processing
- transactional notifications
- admin-facing operations

### Database
The project uses **PostgreSQL** as the primary relational database for:

- users
- customer profiles
- products
- variants
- categories
- carts
- orders
- payments
- stock movements
- promotions

### Infrastructure Support
The project uses **Redis** for:

- queues
- cache
- rate limiting
- future session or background processing support

---

## Core Architectural Principles

### 1. Backend as the source of truth
Critical commerce events must be validated and persisted by the backend.  
For example, an order should only move to a paid state after successful webhook validation from the payment provider.

### 2. Clear separation of concerns
Frontend presentation, backend business logic, and infrastructure concerns should remain clearly separated.

### 3. Modular domain design
The system should be organized by business domains instead of growing as a flat collection of controllers and components.

### 4. Progressive scalability
The architecture should allow future additions such as search engines, ERP/CRM integrations, B2B features, analytics, and mobile applications without major rewrites.

### 5. Production-oriented workflows
Payments, inventory, notifications, and order states should be modeled as real workflows, not as simplified demo-only interactions.

---

## Planned Technology Stack

### Frontend
- Nuxt
- Vue 3
- Tailwind CSS
- Pinia

### Backend
- Laravel
- REST API
- Form Requests for validation
- Jobs / Queues
- Events / Listeners
- Policies / Middleware for authorization

### Data & Infrastructure
- PostgreSQL
- Redis
- Docker

### External Integrations
- Stripe
- Mercado Pago
- Brevo

---

## Main Domains

The system is planned around the following business domains:

- **Catalog**
- **Inventory**
- **Customers**
- **Cart**
- **Checkout**
- **Orders**
- **Payments**
- **Notifications**
- **Promotions**
- **Admin**

---

## Main Business Flow

### Purchase Flow
1. A customer browses the catalog
2. A product is added to the cart
3. The customer proceeds to checkout
4. The backend creates an order in a pending payment state
5. The backend creates a payment session or payment intent
6. The customer completes the payment process
7. The payment provider sends a webhook to the backend
8. The backend validates the webhook
9. The order status is updated accordingly
10. Notifications are dispatched asynchronously

This ensures that payment confirmation does not rely on the frontend.

---

## Order Status Model

The initial order lifecycle is expected to include:

- `pending_payment`
- `paid`
- `payment_failed`
- `processing`
- `shipped`
- `completed`
- `cancelled`
- `refunded`

These states may evolve as the shipping and operational workflows become more detailed.

---

## Initial Data Model

The first relational model is expected to include tables such as:

- users
- customer_profiles
- addresses
- categories
- products
- product_variants
- product_images
- inventory_items
- stock_movements
- carts
- cart_items
- orders
- order_items
- payments
- payment_events
- coupons
- coupon_usages

---

## API Design Direction

The backend API will initially follow a REST approach.

Expected API areas include:

### Public API
- catalog browsing
- product detail
- category navigation
- search
- authentication
- customer profile
- cart operations
- checkout
- orders

### Webhooks
- Stripe webhook endpoint
- Mercado Pago webhook endpoint

### Admin API
- product management
- category management
- inventory management
- order operations
- customer overview

---

## Frontend Structure Direction

The frontend is planned to be separated into:

- public storefront pages
- customer account area
- shared UI components
- API service layer
- state management stores
- route middleware where needed

The initial focus is not on visual complexity, but on building a maintainable structure that supports real commerce workflows.

---

## Backend Structure Direction

The backend is planned to evolve around domain-oriented modules.

The implementation should avoid placing all logic directly in controllers.  
Controllers should remain thin and delegate business rules to application and domain layers.

The backend should gradually distinguish between:

- HTTP layer
- application services / use cases
- domain logic
- infrastructure integrations

---

## Non-Goals for the MVP

The MVP will intentionally exclude:

- mobile applications
- marketplace multi-vendor support
- advanced recommendation systems
- ERP synchronization
- advanced analytics
- multi-region infrastructure
- complex B2B pricing rules

These may be added after the core commerce flow is stable.

---

## Evolution Path

After the MVP, the architecture should be able to expand toward:

- advanced search
- promotion rules
- inventory alerts
- analytics dashboards
- marketplace synchronization
- ERP / CRM integration
- B2B capabilities
- mobile clients
- automation workflows

---

## Current Status

The project is currently in the planning and repository setup phase.

The immediate next steps are:

1. define repository structure
2. scaffold backend and frontend projects
3. prepare local Docker environment
4. model the initial catalog and authentication flows
5. build the MVP incrementally by domain