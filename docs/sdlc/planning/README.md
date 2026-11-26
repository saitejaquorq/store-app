# Planning

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start narrative -->
### EPIC-001 · approved · source: planning:EPIC-001

Customer Catalogue Browsing: customers browse the apparel catalogue by category on a mobile-responsive web store and view product details including images, descriptions, prices and size/colour variants.

**Related:** US-001, US-002

### EPIC-002 · approved · source: planning:EPIC-002

Shopping Cart: customers add product variants to a cart and review or adjust it before checkout, with no login required.

**Related:** US-003, US-004

### EPIC-003 · approved · source: planning:EPIC-003

Guest Checkout and Payment: customers check out as guests with email and shipping address and pay by card via Stripe; total combines item prices, admin-configurable flat-rate shipping (free over a threshold) and a single tax rate. No customer account is created or required.

**Related:** US-005, US-006, US-007

### EPIC-004 · approved · source: planning:EPIC-004

Order Confirmation and Reference: each placed order gets a unique reference and the customer is emailed a confirmation containing it via a transactional email service (e.g. SendGrid); no SMS is sent.

**Related:** US-008, US-009

### EPIC-005 · approved · source: planning:EPIC-005

Order Tracking by Reference and Email: customers track an order without logging in by entering both the order reference and checkout email, then see the current manually-set fulfilment stage; requiring both values prevents guessing of others' orders.

**Related:** US-010, US-011

### EPIC-006 · approved · source: planning:EPIC-006

Admin Sign-In and Protected Area: the admin team signs in with username and password to reach a protected admin area; customers never log in; passwords are stored hashed and sessions end on sign-out or expiry.

**Related:** US-012, US-013

### EPIC-007 · approved · source: planning:EPIC-007

Admin Catalogue Management: the admin team manages products, their size/colour variants, images, prices and per-variant stock; images upload to the app's own AWS media storage; no external PIM/ERP/inventory integration.

**Related:** US-014, US-015, US-016

### EPIC-008 · approved · source: planning:EPIC-008

Admin Order Management: the admin team views placed orders in a list and manually advances each through fulfilment stages, with no courier/carrier API integration.

**Related:** US-017, US-018

### EPIC-009 · approved · source: planning:EPIC-009

Store Configuration (Market, Shipping and Tax): the store serves a single country/currency; admin configures flat-rate shipping, free-shipping threshold and a single sales-tax/VAT rate. Country, currency and tax rate are not yet named and must be confirmed; privacy handling follows that country's rules.

**Related:** US-019, US-020, US-021
<!-- sdlc:auto:end narrative -->
