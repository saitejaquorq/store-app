# Planning

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start narrative -->
### EPIC-001 · approved · source: planning:EPIC-001

Customers browse the apparel catalogue by category on a mobile-responsive web store and view product details including images, descriptions, prices and size/colour variants.

Epic goal as approved: enable category-based browsing and a product detail view (images, description, price, variants) on a responsive layout. Backlog item is epic-level (no points, role unassigned); delivery is tracked via its stories US-001 and US-002.

**Related:** US-001, US-002

### EPIC-002 · approved · source: planning:EPIC-002

Customers add product variants to a cart and review or adjust it before checkout, with no login required.

Epic goal as approved: let customers add an in-stock size/colour variant to a cart and review/adjust quantities or remove items before checking out. Epic-level backlog item has no points and no assigned role; stories US-003 and US-004 carry the work.

**Related:** US-003, US-004

### EPIC-003 · approved · source: planning:EPIC-003

Customers check out as guests (email plus shipping address, no account) and pay by card via Stripe, with the order total combining item price, admin-configured flat shipping and a single tax/VAT rate.

Epic goal as approved: guest checkout capturing email and shipping address, computing grand total from item subtotal, admin-configured flat-rate shipping (free above a threshold) and one configurable sales-tax/VAT rate, then taking payment online via Stripe with no stored reusable card details and no customer account. Epic-level backlog item has no points/role; stories US-005, US-006 and US-007 carry the work.

**Related:** US-005, US-006, US-007

### EPIC-004 · approved · source: planning:EPIC-004

Each placed order receives a unique order reference, and the customer is emailed a confirmation containing that reference via a transactional email service.

Epic goal as approved: generate a distinct, non-reused order reference per successful order and send an email-only confirmation (no SMS) containing the reference, items and total via a transactional email provider (e.g. SendGrid) requiring an API key. Epic-level backlog item has no points/role; stories US-008 and US-009 carry the work.

**Related:** US-008, US-009

### EPIC-005 · approved · source: planning:EPIC-005

Customers track an order without logging in by entering both the order reference and the checkout email, and see the current manually-set fulfilment stage.

Epic goal as approved: require both order reference and email to prevent guessing of others' orders, and surface the admin-set fulfilment stage (received, packed, shipped, delivered) on lookup. Epic-level backlog item has no points/role; stories US-010 and US-011 carry the work.

**Related:** US-010, US-011

### EPIC-006 · approved · source: planning:EPIC-006

The admin team signs in with a username and password to reach a protected admin area for managing the catalogue and orders; customers never log in.

Epic goal as approved: admin authentication gating access to the admin area, hashed password storage, and session termination on sign-out or expiry. Epic-level backlog item has no points/role; stories US-012 and US-013 carry the work.

**Related:** US-012, US-013

### EPIC-007 · approved · source: planning:EPIC-007

The admin team manages one catalogue of products, their size/colour variants, images and per-variant stock, with images uploaded to the app's own AWS media storage and no external PIM/ERP/inventory integration.

Epic goal as approved: product CRUD with category/description/price, variant definition with per-variant stock that gates purchasability, and image upload/removal against the app's own media storage. Epic-level backlog item has no points/role; stories US-014, US-015 and US-016 carry the work.

**Related:** US-014, US-015, US-016

### EPIC-008 · approved · source: planning:EPIC-008

The admin team views placed orders in a list and processes each by manually advancing it through fulfilment stages, with no courier/carrier API integration.

Epic goal as approved: an order list and detail view, plus manual stage advancement (e.g. received, packed, shipped, delivered) that is reflected in customer tracking, recorded entirely within the app. Epic-level backlog item has no points/role; stories US-017 and US-018 carry the work.

**Related:** US-017, US-018

### EPIC-009 · approved · source: planning:EPIC-009

The store serves and ships to a single country with one currency; the admin configures flat-rate shipping, a free-shipping threshold and a single sales-tax/VAT rate.

Epic goal as approved: single-country/single-currency operation, admin-configurable flat shipping charge and free-shipping threshold, and one configurable tax/VAT rate. The specific country, currency and tax rate are explicitly flagged in the input as not yet named/open assumptions pending confirmation, with privacy handling to follow that country's consumer/data rules once chosen. Epic-level backlog item has no points/role; stories US-019, US-020 and US-021 carry the work.

**Related:** US-019, US-020, US-021

### SPRINT-1 · approved · source: planning:Sprint 1

Sprint 1 goal: admin can sign in to a protected area and the store's country, shipping and tax configuration exists.

Capacity: 20 points. Plan v1, approved. Goal text maps to EPIC-006 (admin sign-in/session protection, US-012, US-013) and EPIC-009 (country/currency, shipping and tax configuration, US-019, US-020, US-021); the plan input lists backlog items without an explicit per-sprint item assignment, so this mapping is inferred from the stated sprint goal rather than taken from an explicit ticket-to-sprint field.

**Related:** EPIC-006, US-012, US-013, EPIC-009, US-019, US-020, US-021

### SPRINT-2 · approved · source: planning:Sprint 2

Sprint 2 goal: admins can create products and define variants with stock in the catalogue.

Capacity: 20 points. Plan v1, approved. Goal text maps to EPIC-007 stories US-014 (product CRUD) and US-015 (variant/stock management); image upload (US-016) is not mentioned in this sprint's goal text so is not linked here. Mapping inferred from goal text, as the plan input does not give an explicit per-sprint item assignment.

**Related:** EPIC-007, US-014, US-015

### SPRINT-3 · approved · source: planning:Sprint 3

Sprint 3 goal: customers can browse categories and view product detail pages with images and variants.

Capacity: 20 points. Plan v1, approved. Goal text maps directly to EPIC-001 stories US-001 (category browsing) and US-002 (product detail page). Mapping inferred from goal text, as the plan input does not give an explicit per-sprint item assignment.

**Related:** EPIC-001, US-001, US-002

### SPRINT-4 · approved · source: planning:Sprint 4

Sprint 4 goal: customers can build a cart and complete the checkout form with shipping and tax totals.

Capacity: 20 points. Plan v1, approved. Goal text maps to EPIC-002 (cart: US-003, US-004) and part of EPIC-003 (checkout form and totals: US-005, US-006); payment itself (US-007) is covered in Sprint 5. Mapping inferred from goal text, as the plan input does not give an explicit per-sprint item assignment.

**Related:** EPIC-002, US-003, US-004, EPIC-003, US-005, US-006

### SPRINT-5 · approved · source: planning:Sprint 5

Sprint 5 goal: customers can pay by card and receive an order reference and confirmation email.

Capacity: 20 points. Plan v1, approved. Goal text maps to US-007 (Stripe card payment, from EPIC-003) and EPIC-004 (US-008 order reference, US-009 confirmation email). Mapping inferred from goal text, as the plan input does not give an explicit per-sprint item assignment.

**Related:** US-007, EPIC-004, US-008, US-009

### SPRINT-6 · approved · source: planning:Sprint 6

Sprint 6 goal: admins can process orders and customers can track fulfilment stage by reference and email.

Capacity: 20 points. Plan v1, approved. Goal text maps to EPIC-008 (order list and stage advancement: US-017, US-018) and EPIC-005 (tracking by reference and email: US-010, US-011). Mapping inferred from goal text, as the plan input does not give an explicit per-sprint item assignment.

**Related:** EPIC-008, US-017, US-018, EPIC-005, US-010, US-011
<!-- sdlc:auto:end narrative -->
