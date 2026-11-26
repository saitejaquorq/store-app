# Product Requirements

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start narrative -->
## Summary

### REQ-STACK · approved · source: requirements:stack

Technology stack approved by the product owner for store-app.

Backend: FastAPI 0.115. Cloud: AWS. Database: PostgreSQL 16. Frontend: React 19. Requirements version 1, delivery scope marked 'lightweight'. Design must use exactly this stack, no substitutions.

### REQ-SERVICES · approved · source: requirements:services

External/integrated services the app relies on for payment, media storage and email.

- Card payment provider used at checkout to take the grand total; no card details are stored by the store as a reusable account.
- App's own media storage on AWS for product image uploads (no external PIM/ERP integration).
- Email delivery for order confirmation emails; confirmation is sent by email only, with no SMS.

**Related:** NFR-003

### REQ-SCOPE · approved · source: requirements:scope

Defines what store-app will and will not deliver in this release.

In scope: browse apparel catalogue by category; product pages with images, descriptions, prices; size/colour variants with per-variant stock; shopping cart; guest checkout capturing email and shipping address; order placement with a unique order reference; order lookup by reference and email showing current status; order total with flat-rate shipping and a single tax rate; admin sign-in to a protected area; catalogue management (products, variants, images, prices, stock); admin order list; product image uploads to the app's own AWS media storage; admin-configurable flat-rate shipping free over a threshold; a single configurable sales-tax/VAT rate; a single country and currency (to be confirmed).
Out of scope: native mobile app (iOS/Android) -- delivered instead as a mobile-responsive web store.

### REQ-BROWSE · approved · source: requirements:feature:Browsing the store

Customers browse the catalogue by category and view product detail pages with variant stock.

- Browse catalogue by category: select a category to see its products, each with thumbnail, name and price in the store currency; an empty category shows a 'no products currently available' message.
- View product detail page: see images, description, price and selectable size/colour variants; selecting a size and colour shows whether that combination is in stock; out-of-stock combinations are shown unavailable and cannot be added to the cart.

### REQ-CART · approved · source: requirements:feature:Cart & checkout

Customers add in-stock variants to a cart, adjust it, and complete guest checkout with card payment, shipping and tax applied.

- Add a variant to the cart: add an in-stock size/colour without logging in; cart shows updated item count and total; adding more than available stock is prevented and the max available quantity is shown.
- Review and adjust the cart: see each item's product name, size, colour, unit price, quantity, line total, plus subtotal; change quantities or remove items updates the line and subtotal; empty cart shows a message and a way to keep browsing.
- Enter email and shipping address: provide email and a shipping address within the single served country, no account required; missing/invalid email or incomplete address is flagged; an address outside the served country is refused with an explanation.
- See order total with shipping and tax: checkout summary shows item subtotal, flat-rate shipping, tax amount and grand total in the store currency; shipping is free when subtotal reaches the configured threshold, otherwise charged at the flat rate.
- Pay by card at checkout: pay the grand total by card via the payment provider; on success the order is placed; a declined/failed payment issues no order reference and lets the customer retry without losing the cart; an item that sells out before payment blocks the order until the cart is adjusted.

### REQ-ORDER-TRACK · approved · source: requirements:feature:Order confirmation & tracking

Placed orders get a unique reference, trigger a confirmation email, and can be tracked by reference and email to see the current fulfilment stage.

- Receive a unique order reference: on payment success the order is given a unique, never-reused reference shown on the confirmation screen.
- Order confirmation email: on order placement, a confirmation email is sent to the checkout address with the order reference, items ordered and order total; email only, no SMS.
- Look up an order: track without logging in by entering the order reference and checkout email, to see items and current fulfilment stage.
- See current fulfilment stage: tracking page shows the current stage label (e.g. received, packed, shipped, delivered) set by admin, updated on next lookup after the admin changes it.

### REQ-ADMIN-SIGNIN · approved · source: requirements:feature:Admin sign-in

Admin team members sign in with username and password to reach a protected admin area.

Valid credentials grant access to the admin area; incorrect credentials are refused with a generic error that does not reveal which field was wrong.

**Related:** NFR-001, NFR-002

### REQ-CATALOG-MGMT · approved · source: requirements:feature:Catalogue management

Admins create and edit products, manage size/colour variants and stock, and upload/remove product images.

- Create and edit products: add/edit name, category, description and price; changes appear in the catalogue and product page; a missing name or invalid price is flagged and not saved.
- Manage variants and stock: define size/colour variants and set stock quantity per variant; available stock is reduced when an order is placed; a variant with zero stock is shown to customers as unavailable.
- Upload product images: upload one or more images per product into the app's own AWS media storage, shown on the product page; removing an image deletes it so it is no longer shown.

### REQ-ORDER-MGMT · approved · source: requirements:feature:Order management

Admins view the order list and manually advance each order's fulfilment stage.

- View the order list: see reference, customer email, order total, date and current fulfilment stage; open an order to see its items, variants, quantities, totals and shipping address.
- Advance fulfilment stages: manually move an order to a later stage (received, packed, shipped, delivered); change is recorded within the app and reflected in customer tracking; no courier/carrier integration.

### REQ-SETTINGS · approved · source: requirements:feature:Store settings

Store operates in a single country/currency with admin-configurable flat-rate shipping and a single sales-tax/VAT rate.

- Configure country and currency: all monetary values shown in the one store currency; shipping offered only within the one served country; country, currency and tax rate are recorded as 'to be confirmed' until named.
- Configure shipping: admins set a flat-rate shipping charge and a free-shipping threshold applied to all checkouts; flat rate charged below threshold, free at/above it.
- Configure sales-tax rate: admins set a single sales-tax/VAT rate used on all orders; until named it is used as a configurable rate clearly marked pending confirmation.

**Related:** NFR-005

### NFR-001 · approved · source: requirements:NFR-001

Security: admin area stays protected and sessions end on sign-out or inactivity expiry.

[security] Admin pages/actions are reachable only while signed in; anyone not signed in is redirected to sign-in. A session ends on sign-out or inactivity expiry, after which the admin must sign in again.

**Related:** REQ-ADMIN-SIGNIN

### NFR-002 · approved · source: requirements:NFR-002

Security: admin passwords are hashed and sign-in failures give a generic error.

[security] Admin passwords are stored only in hashed form and never shown back in plain text. A failed sign-in shows a generic error that does not reveal whether the username or password was wrong.

**Related:** REQ-ADMIN-SIGNIN

### NFR-003 · approved · source: requirements:NFR-003

Security: card details are never stored by the store itself.

[security] Card payments are taken through the external payment provider at checkout; no card details are stored by the store as a reusable account.

**Related:** REQ-CART, REQ-SERVICES

### NFR-004 · approved · source: requirements:NFR-004

Privacy: order lookup only succeeds when reference and email both match.

[privacy] Order details are shown only when the order reference and the checkout email both match; otherwise (mismatch or non-existent reference) no details are shown and the message does not reveal which value was at fault.

**Related:** REQ-ORDER-TRACK

### NFR-005 · approved · source: requirements:NFR-005

Compliance: customer data handling follows the served country's consumer/data-protection rules, pending confirmation of that country.

[compliance] Handling of customer data follows the consumer and data-protection rules of the single country served; that country, its currency and tax rate are still to be confirmed and are recorded as pending confirmation (open assumption).

**Related:** REQ-SETTINGS

### NFR-006 · approved · source: requirements:NFR-006

Compatibility: the store is mobile-responsive on phone browsers.

[compatibility] The store is delivered as a mobile-responsive web store; layout adapts so category listings, product pages and the cart stay usable on a small phone screen.

**Related:** REQ-BROWSE, REQ-CART
<!-- sdlc:auto:end narrative -->

<!-- sdlc:auto:start summary -->
**Requirements version:** v1  
**Delivery scope:** lightweight  
**Approved:** 2026-11-26

**Capabilities in scope:** Browse apparel catalogue by category, Product pages with images, descriptions and prices, Size and colour variants with per-variant stock, Shopping cart, Guest checkout capturing email and shipping address, Order placement with a unique order reference, Order lookup by reference and email showing current status, Order total with flat-rate shipping and a single tax rate, Admin sign-in to a protected area, Catalogue management for products, variants, images, prices and stock, Admin order list, Product image uploads held in the app's own media storage on AWS, Admin-configurable flat-rate shipping, free over a threshold, A single configurable sales-tax/VAT rate, A single country and currency, to be confirmed

**Approved technology stack:**

| Layer | Choice | Rationale |
|---|---|---|
| backend | FastAPI | — |
| cloud | AWS | — |
| database | PostgreSQL | — |
| frontend | React | — |
<!-- sdlc:auto:end summary -->

<!-- sdlc:auto:start epics -->
## EPIC-001: Customer Catalogue Browsing

Customers browse the apparel catalogue by category on a mobile-responsive web store and view product details including images, descriptions, prices and size/colour variants.

### US-001: Browse catalogue by category

**Priority:** high

> As a customer, I want to browse the apparel catalogue organised by category, so that I can find the types of clothing I am interested in.

| ID | Given | When | Then |
|---|---|---|---|
| AC-001 | the store has products assigned to categories | I open the store and select a category | I see the list of products belonging to that category, each with a thumbnail image, name and price in the store currency |
| AC-002 | a category contains no available products | I view that category | I see a message indicating there are no products currently available in it |
| AC-003 | I am using a mobile phone browser | I view the catalogue | the layout adapts responsively so the category and product listings remain usable on a small screen |

### US-002: View product detail page

**Priority:** high

> As a customer, I want to open a product and see its images, description, price and available variants, so that I can decide whether to buy it and in which size and colour.

| ID | Given | When | Then |
|---|---|---|---|
| AC-004 | a product with images, a description and a price | I open its product page | I see the product images, description, price in the store currency, and selectable size and colour variants |
| AC-005 | a product with one or more variants out of stock | I view the product page | out-of-stock size/colour combinations are shown as unavailable and cannot be added to the cart |
| AC-006 | I am viewing a product | I select a size and colour combination | the page reflects the selected variant and whether it is in stock |

## EPIC-002: Shopping Cart

Customers add product variants to a cart and review or adjust it before checkout. No login is required to use the cart.

### US-003: Add a product variant to the cart

**Priority:** high

> As a customer, I want to add a selected size and colour of a product to my cart, so that I can collect the items I intend to buy.

| ID | Given | When | Then |
|---|---|---|---|
| AC-007 | I have selected an in-stock size and colour on a product page | I choose to add it to the cart | the variant is added to my cart and the cart shows the updated item count and total |
| AC-008 | a variant has only a limited quantity in stock | I try to add more of that variant than is available | I am prevented from exceeding the available stock and told the maximum quantity available |

### US-004: Review and adjust the cart

**Priority:** high

> As a customer, I want to view my cart, change quantities and remove items, so that I can confirm what I am about to buy and its cost.

| ID | Given | When | Then |
|---|---|---|---|
| AC-009 | I have items in my cart | I open the cart | I see each item with its product name, size, colour, unit price, quantity and line total, plus the cart subtotal |
| AC-010 | I am viewing my cart | I change an item quantity or remove an item | the cart updates the affected line and the subtotal accordingly |
| AC-011 | my cart is empty | I open the cart | I see a message that the cart is empty and a way to continue browsing |

## EPIC-003: Guest Checkout and Payment

Customers check out as guests by providing an email and shipping address and paying by card. The order total combines item prices, an admin-configurable flat-rate shipping charge (free over a threshold) and a single configurable sales-tax/VAT rate. Payment is taken online via Stripe. No customer account is created or required.

### US-005: Enter email and shipping address at checkout

**Priority:** high

> As a customer, I want to provide my email and shipping address during checkout without creating an account, so that I can complete my purchase quickly and receive my order and confirmation.

| ID | Given | When | Then |
|---|---|---|---|
| AC-012 | I have items in my cart | I proceed to checkout | I am asked for my email address and a shipping address within the single served country, with no requirement to log in or register |
| AC-013 | I am on the checkout form | I submit it with a missing or invalid email or an incomplete address | I am shown which fields need correcting and the order is not placed |
| AC-014 | I provide a shipping address | the address is outside the single country the store ships to | I am told the store only ships within that country and cannot complete the order |

### US-006: See order total with shipping and tax

**Priority:** high

> As a customer, I want to see the shipping charge and tax added to my item total before I pay, so that I know the full amount I will be charged.

| ID | Given | When | Then |
|---|---|---|---|
| AC-015 | the admin has configured a flat-rate shipping charge, a free-shipping threshold and a single sales-tax/VAT rate | I reach the checkout summary | I see the item subtotal, the shipping charge, the tax amount and the grand total in the store currency |
| AC-016 | my item subtotal is at or above the configured free-shipping threshold | I view the checkout summary | the shipping charge is shown as free |
| AC-017 | my item subtotal is below the free-shipping threshold | I view the checkout summary | the configured flat-rate shipping charge is applied to the total |

### US-007: Pay by card

**Priority:** critical

> As a customer, I want to pay for my order securely by card at checkout, so that I can complete my purchase online.

| ID | Given | When | Then |
|---|---|---|---|
| AC-018 | a confirmed order total and the card payment provider configured with its key (Stripe, requiring STRIPE_API_KEY set as <stripe-api-key>) | I submit valid card details for the grand total | the payment is taken via the provider and the order is placed; no card details are stored as a reusable account |
| AC-019 | I am paying at checkout | the card payment is declined or fails | I am told the payment did not succeed, no order reference is issued, and I can retry without losing my cart |
| AC-020 | a variant in my cart sells out between adding it and paying | I attempt to place the order | I am told the item is no longer available and the order is not completed until I adjust my cart |

## EPIC-004: Order Confirmation and Reference

Each placed order receives a unique order reference. The customer is emailed an order confirmation containing that reference via a transactional email service (e.g. SendGrid, requiring an API key). No SMS is sent.

### US-008: Receive a unique order reference

**Priority:** high

> As a customer, I want my completed order to be given a unique order reference, so that I can identify and track my order later without an account.

| ID | Given | When | Then |
|---|---|---|---|
| AC-021 | my payment has succeeded | the order is placed | a unique order reference is generated and shown to me on the confirmation screen |
| AC-022 | multiple orders are placed | each order is created | each receives a distinct order reference that is not reused |

### US-009: Receive order confirmation by email

**Priority:** high

> As a customer, I want to receive an email confirming my order and its reference, so that I have a record of my purchase and the reference needed to track it.

| ID | Given | When | Then |
|---|---|---|---|
| AC-023 | the transactional email service is configured with its API key (e.g. SendGrid, set as <sendgrid-api-key>) | my order is placed successfully | a confirmation email is sent to the email I provided, containing the order reference, the items ordered and the order total |
| AC-024 | an order has been placed | the confirmation email is generated | it is sent only by email, with no SMS message, to the address captured at checkout |

## EPIC-005: Order Tracking by Reference and Email

Customers track an order without logging in by entering both the order reference and the email used at checkout, then see the current manually-set fulfilment stage. Requiring both values prevents guessing of others' orders.

### US-010: Look up an order with reference and email

**Priority:** high

> As a customer, I want to enter my order reference and email to view my order status, so that I can see how my order is progressing without an account.

| ID | Given | When | Then |
|---|---|---|---|
| AC-025 | I have a valid order reference and the email used at checkout | I submit both on the order tracking page | I see the current fulfilment stage of that order and the items it contains |
| AC-026 | I enter an order reference with an email that does not match that order | I submit the tracking form | I am not shown any order details and am told the reference and email do not match |
| AC-027 | I enter a reference that does not exist | I submit the tracking form | I am told no matching order was found, without revealing whether the reference or email was at fault |

### US-011: See current fulfilment stage

**Priority:** medium

> As a customer, I want to see which fulfilment stage my order has reached, so that I know whether it is received, packed, shipped or delivered.

| ID | Given | When | Then |
|---|---|---|---|
| AC-028 | an order whose stage the admin has set (e.g. received, packed, shipped, delivered) | I view it on the tracking page | I see the current stage label reflecting the latest stage set by the admin |
| AC-029 | the admin advances my order to a later stage | I next look up the order | the tracking page shows the updated stage |

## EPIC-006: Admin Sign-In and Protected Area

The admin team signs in with a username and password to reach a protected admin area for managing the catalogue and orders. Customers never log in. Passwords are stored hashed and sessions end on sign-out or expiry.

### US-012: Admin sign-in to the protected area

**Priority:** high

> As a member of the admin team, I want to sign in with a username and password, so that I can access the admin area to manage the store.

| ID | Given | When | Then |
|---|---|---|---|
| AC-030 | I am a registered admin with valid credentials | I submit my username and password | I am signed in and can reach the admin area |
| AC-031 | I submit an incorrect username or password | I attempt to sign in | I am refused access and shown a generic error that does not reveal which field was wrong |
| AC-032 | admin credentials are stored | a password is saved | it is stored only in hashed form and never shown back in plain text |

### US-013: Protect admin area and end sessions

**Priority:** high

> As a member of the admin team, I want the admin area to be accessible only while signed in and my session to end when I sign out or it expires, so that store management stays protected from unauthorised access.

| ID | Given | When | Then |
|---|---|---|---|
| AC-033 | I am not signed in | I try to open any admin page or action | I am prevented from accessing it and directed to sign in |
| AC-034 | I am signed in | I sign out | my session ends and I must sign in again to reach the admin area |
| AC-035 | I am signed in and inactive | my session reaches its expiry | the session ends and I must sign in again to continue |

## EPIC-007: Admin Catalogue Management

The admin team manages one catalogue: products, their size and colour variants, images, prices and per-variant stock. Product images are uploaded to the app's own media storage on AWS. There is no integration with an external PIM, ERP or inventory system.

### US-014: Create and edit products with categories, descriptions and prices

**Priority:** high

> As a member of the admin team, I want to add and edit products with a category, description and price, so that the catalogue reflects what we sell.

| ID | Given | When | Then |
|---|---|---|---|
| AC-036 | I am signed in to the admin area | I create a product with a name, category, description and price | the product is saved and appears in the catalogue under its category |
| AC-037 | an existing product | I edit its name, category, description or price and save | the changes are stored and reflected on the customer-facing product page |
| AC-038 | I submit a product with a missing name or an invalid price | I try to save it | I am shown which fields need correcting and the product is not saved |

### US-015: Manage size and colour variants with per-variant stock

**Priority:** high

> As a member of the admin team, I want to define a product's size and colour variants and set the stock quantity for each, so that customers can only buy variants that are available.

| ID | Given | When | Then |
|---|---|---|---|
| AC-039 | a product in the catalogue | I add size and colour variants and set a stock quantity for each | each variant and its stock level are saved against the product |
| AC-040 | a variant with a set stock quantity | an order is placed for that variant | its available stock is reduced by the quantity ordered |
| AC-041 | a variant's stock reaches zero | customers view the product | that size/colour combination is shown as unavailable for purchase |

### US-016: Upload product images to the app's media storage

**Priority:** medium

> As a member of the admin team, I want to upload images for a product into the app's own media storage, so that customers see the product illustrated.

| ID | Given | When | Then |
|---|---|---|---|
| AC-042 | a product in the admin area | I upload one or more images for it | the images are stored in the app's own media storage on AWS and displayed on the product page |
| AC-043 | a product with uploaded images | I remove an image | it is deleted from the product and no longer shown to customers |

## EPIC-008: Admin Order Management

The admin team views placed orders in a list and processes each by advancing it manually through fulfilment stages (e.g. received, packed, shipped, delivered). There is no courier or carrier API integration.

### US-017: View the order list

**Priority:** high

> As a member of the admin team, I want to see a list of placed orders with their key details, so that I can process and keep track of them.

| ID | Given | When | Then |
|---|---|---|---|
| AC-044 | orders have been placed | I open the order list in the admin area | I see each order with its reference, customer email, order total, date and current fulfilment stage |
| AC-045 | I am viewing the order list | I open an individual order | I see its items, variants, quantities, totals, shipping address and current stage |

### US-018: Advance an order through fulfilment stages

**Priority:** high

> As a member of the admin team, I want to manually move an order to the next fulfilment stage, so that the customer's tracking reflects real progress.

| ID | Given | When | Then |
|---|---|---|---|
| AC-046 | an order at a given fulfilment stage | I set it to a later stage (e.g. received, packed, shipped, delivered) | the order's current stage is updated and reflected in the customer's order tracking |
| AC-047 | no external courier system is connected | I update an order's stage | the change is recorded manually within the app with no carrier API involved |

## EPIC-009: Store Configuration (Market, Shipping and Tax)

The store serves and ships to a single country with one currency. The admin configures the flat-rate shipping charge and free-shipping threshold and a single sales-tax/VAT rate. The specific country, currency and tax rate are not yet named and must be confirmed; privacy handling follows that country's consumer/data rules.

### US-019: Configure single country and currency

**Priority:** high

> As a member of the admin team, I want the store to operate in one confirmed country and currency, so that prices, shipping and tax are consistent for our market.

| ID | Given | When | Then |
|---|---|---|---|
| AC-048 | the store is set to a single served country and currency | customers view prices and check out | all monetary values are shown in that one currency and shipping is offered only within that one country |
| AC-049 | the specific country, currency and tax rate have not yet been named | the store is configured | the chosen country, currency and single sales-tax/VAT rate are recorded as values to be confirmed, and privacy handling follows that country's consumer/data rules (open assumption) |

### US-020: Configure flat-rate shipping and free-shipping threshold

**Priority:** medium

> As a member of the admin team, I want to set a flat shipping charge and a threshold above which shipping is free, so that customers are charged shipping consistently without carrier integrations.

| ID | Given | When | Then |
|---|---|---|---|
| AC-050 | I am in the admin configuration | I set a flat-rate shipping charge and a free-shipping threshold | those values are applied to all customer checkouts |
| AC-051 | shipping is charged as a simple flat rate rather than weight-, zone- or carrier-based rates (open assumption) | a customer checks out | the configured flat rate is applied, or free when the subtotal reaches the threshold |

### US-021: Configure a single sales-tax/VAT rate

**Priority:** medium

> As a member of the admin team, I want to set one sales-tax/VAT rate for the store, so that tax is calculated consistently on orders.

| ID | Given | When | Then |
|---|---|---|---|
| AC-052 | I am in the admin configuration | I set a single sales-tax/VAT rate | that rate is used to calculate tax on all customer orders |
| AC-053 | the specific tax rate is not yet named (open assumption) | the rate is left to be confirmed | a single configurable rate is used and is clearly marked as pending confirmation |
<!-- sdlc:auto:end epics -->
