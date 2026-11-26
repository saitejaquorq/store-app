# Planning

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start narrative -->
### EPIC-001 · approved · source: planning:EPIC-001

Customers browse the apparel catalogue by category on a mobile-responsive web store and view product detail pages with images, descriptions, prices and size/colour variants.

Epic goal: enable category-based browsing and detailed product viewing so customers can find and evaluate clothing items, with responsive layout for mobile. Comprises stories US-001 (browse by category) and US-002 (view product detail page).

**Related:** US-001, US-002

### EPIC-002 · approved · source: planning:EPIC-002

Customers add product variants to a cart and review or adjust it before checkout, with no login required.

Epic goal: let customers collect selected size/colour variants in a cart and adjust quantities or remove items before purchase. Comprises stories US-003 (add variant to cart) and US-004 (review and adjust cart).

**Related:** US-003, US-004

### EPIC-003 · approved · source: planning:EPIC-003

Customers check out as guests with email and shipping address and pay by card; order total combines item price, configurable flat-rate shipping (free above a threshold) and a single configurable tax/VAT rate, via Stripe. No account is created.

Epic goal: deliver a guest checkout and payment flow without account creation, surfacing shipping and tax in the total and processing payment through Stripe. Comprises stories US-005 (email/shipping address entry), US-006 (see order total with shipping and tax) and US-007 (pay by card).

**Related:** US-005, US-006, US-007

### EPIC-004 · approved · source: planning:EPIC-004

Each placed order receives a unique order reference, communicated to the customer via a transactional confirmation email (e.g. SendGrid); no SMS is sent.

Epic goal: generate a unique, non-reused order reference per order and notify the customer by email only, including the reference, items and total. Comprises stories US-008 (unique order reference) and US-009 (order confirmation email).

**Related:** US-008, US-009

### EPIC-005 · approved · source: planning:EPIC-005

Customers track an order without logging in by supplying both order reference and checkout email, then view the current manually-set fulfilment stage.

Epic goal: provide reference+email order lookup (requiring both to prevent guessing) and display the current fulfilment stage as set by admin. Comprises stories US-010 (look up order with reference and email) and US-011 (see current fulfilment stage).

**Related:** US-010, US-011

### EPIC-006 · approved · source: planning:EPIC-006

The admin team signs in with username/password to reach a protected admin area; passwords are stored hashed and sessions end on sign-out or expiry. Customers never log in.

Epic goal: secure the admin area behind authentication with hashed credential storage and session expiry/sign-out handling. Comprises stories US-012 (admin sign-in) and US-013 (protect admin area and end sessions).

**Related:** US-012, US-013

### EPIC-007 · approved · source: planning:EPIC-007

The admin team manages the catalogue: products, size/colour variants, images and per-variant stock, with images uploaded to the app's own AWS media storage; no external PIM/ERP/inventory integration.

Epic goal: give admins full CRUD over products, variants with per-variant stock, and product images stored in-app on AWS, keeping the catalogue self-contained. Comprises stories US-014 (create/edit products), US-015 (manage size/colour variants with stock) and US-016 (upload product images).

**Related:** US-014, US-015, US-016

### EPIC-008 · approved · source: planning:EPIC-008

The admin team views placed orders in a list and manually advances each through fulfilment stages (received, packed, shipped, delivered); no courier/carrier API integration.

Epic goal: let admins see and process orders, manually updating fulfilment stage so customer tracking reflects real progress, without any carrier system connection. Comprises stories US-017 (view order list) and US-018 (advance order through fulfilment stages).

**Related:** US-017, US-018

### EPIC-009 · approved · source: planning:EPIC-009

The store serves a single country and currency; admin configures a flat-rate shipping charge, free-shipping threshold, and a single sales-tax/VAT rate. The specific country, currency and tax rate are not yet named and remain open assumptions pending confirmation.

Epic goal: establish single-market configuration (country/currency) plus admin-configurable flat shipping/free-shipping threshold and one tax/VAT rate; privacy handling is to follow the eventual country's consumer/data rules once confirmed. Comprises stories US-019 (configure country/currency), US-020 (configure shipping/threshold) and US-021 (configure tax/VAT rate).

**Related:** US-019, US-020, US-021

### SPRINT-1 · approved · source: planning:SPRINT-1

First sprint (capacity 20) targets store configuration, admin sign-in, and category catalogue browsing.

Plan v1, Sprint 1 goal: 'Store configuration, admin sign-in, and category catalogue browsing'; capacity 20 points. Based on goal wording this aligns with US-019 (single country/currency configuration), US-012 and US-013 (admin sign-in and session protection), and US-001 (browse catalogue by category, including its tasks US-001-T1 through T4).

**Related:** US-019, US-012, US-013, US-001

### SPRINT-2 · approved · source: planning:SPRINT-2

Second sprint (capacity 20) targets shipping/tax configuration, product detail pages, and admin product/variant management.

Plan v1, Sprint 2 goal: 'Shipping/tax configuration, product detail pages, and admin product/variant management'; capacity 20 points. Based on goal wording this aligns with US-020 (flat-rate shipping and free-shipping threshold), US-021 (sales-tax/VAT rate), US-002 (product detail page), US-014 (create/edit products) and US-015 (manage size/colour variants with stock).

**Related:** US-020, US-021, US-002, US-014, US-015

### SPRINT-3 · approved · source: planning:SPRINT-3

Third sprint (capacity 20) targets product images, shopping cart, and checkout address entry.

Plan v1, Sprint 3 goal: 'Product images, shopping cart, and checkout address entry'; capacity 20 points. Based on goal wording this aligns with US-016 (upload product images), US-003 (add variant to cart), US-004 (review and adjust cart) and US-005 (email/shipping address entry at checkout).

**Related:** US-016, US-003, US-004, US-005

### SPRINT-4 · approved · source: planning:SPRINT-4

Fourth sprint (capacity 20) targets checkout totals, card payment, order reference generation, and confirmation email.

Plan v1, Sprint 4 goal: 'Checkout totals, card payment, order reference, and confirmation email'; capacity 20 points. Based on goal wording this aligns with US-006 (order total with shipping/tax), US-007 (pay by card, including tasks US-007-T1 through T4), US-008 (unique order reference) and US-009 (order confirmation email).

**Related:** US-006, US-007, US-008, US-009

### SPRINT-5 · approved · source: planning:SPRINT-5

Fifth sprint (capacity 20) targets order tracking and admin order management.

Plan v1, Sprint 5 goal: 'Order tracking and admin order management'; capacity 20 points. Based on goal wording this aligns with US-010 (look up order by reference and email), US-011 (see fulfilment stage), US-017 (view order list) and US-018 (advance order through fulfilment stages).

**Related:** US-010, US-011, US-017, US-018
<!-- sdlc:auto:end narrative -->
