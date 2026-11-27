# Planning

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start narrative -->
### EPIC-001 · approved · source: planning:EPIC-001

Customer Catalogue Browsing.

Customers browse the apparel catalogue by category on a mobile-responsive web store and view product details including images, descriptions, prices and size/colour variants.

**Related:** US-001, US-002

### EPIC-002 · approved · source: planning:EPIC-002

Shopping Cart.

Customers add product variants to a cart and review or adjust it before checkout. No login is required to use the cart.

**Related:** US-003, US-004

### EPIC-003 · approved · source: planning:EPIC-003

Guest Checkout and Payment.

Customers check out as guests by providing an email and shipping address and paying by card. The order total combines item prices, an admin-configurable flat-rate shipping charge (free over a threshold) and a single configurable sales-tax/VAT rate. Payment is taken online via Stripe. No customer account is created or required.

**Related:** US-005, US-006, US-007

### EPIC-004 · approved · source: planning:EPIC-004

Order Confirmation and Reference.

Each placed order receives a unique order reference. The customer is emailed an order confirmation containing that reference via a transactional email service (e.g. SendGrid, requiring an API key). No SMS is sent.

**Related:** US-008, US-009

### EPIC-005 · approved · source: planning:EPIC-005

Order Tracking by Reference and Email.

Customers track an order without logging in by entering both the order reference and the email used at checkout, then see the current manually-set fulfilment stage. Requiring both values prevents guessing of others' orders.

**Related:** US-010, US-011

### EPIC-006 · approved · source: planning:EPIC-006

Admin Sign-In and Protected Area.

The admin team signs in with a username and password to reach a protected admin area for managing the catalogue and orders. Customers never log in. Passwords are stored hashed and sessions end on sign-out or expiry.

**Related:** US-012, US-013

### EPIC-007 · approved · source: planning:EPIC-007

Admin Catalogue Management.

The admin team manages one catalogue: products, their size and colour variants, images, prices and per-variant stock. Product images are uploaded to the app's own media storage on AWS. There is no integration with an external PIM, ERP or inventory system.

**Related:** US-014, US-015, US-016

### EPIC-008 · approved · source: planning:EPIC-008

Admin Order Management.

The admin team views placed orders in a list and processes each by advancing it manually through fulfilment stages (e.g. received, packed, shipped, delivered). There is no courier or carrier API integration.

**Related:** US-017, US-018

### EPIC-009 · approved · source: planning:EPIC-009

Store Configuration (Market, Shipping and Tax).

The store serves and ships to a single country with one currency. The admin configures the flat-rate shipping charge and free-shipping threshold and a single sales-tax/VAT rate. The specific country, currency and tax rate are not yet named and must be confirmed; privacy handling follows that country's consumer/data rules.

**Related:** US-019, US-020, US-021
<!-- sdlc:auto:end narrative -->
