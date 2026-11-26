# Sprint Plan

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start sprints -->
## Sprint 1: Sprint 1

Store configuration, admin sign-in, and category catalogue browsing

Capacity: 20 points · Committed: 19

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-001 | Story | Browse catalogue by category | 8 | backend-agent | — |
| ↳ US-001-T1 | Task | Define category/product/variant schema and migrations | — | backend-agent | — |
| ↳ US-001-T2 | Task | Implement catalogue browsing endpoints | — | backend-agent | — |
| ↳ US-001-T3 | Task | Build responsive category and product listing UI | — | frontend-agent | — |
| ↳ US-001-T4 | Task | QA responsive layout across breakpoints | — | qa-agent | — |
| US-012 | Story | Admin sign-in to the protected area | 5 | security-agent | — |
| US-013 | Story | Protect admin area and end sessions | 3 | security-agent | US-012 |
| US-019 | Story | Configure single country and currency | 3 | backend-agent | — |

## Sprint 2: Sprint 2

Shipping/tax configuration, product detail pages, and admin product/variant management

Capacity: 20 points · Committed: 19

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-002 | Story | View product detail page | 5 | frontend-agent | US-001 |
| US-014 | Story | Create and edit products with categories, descriptions and prices | 5 | backend-agent | US-001, US-012, US-013 |
| US-015 | Story | Manage size and colour variants with per-variant stock | 5 | backend-agent | US-014 |
| US-020 | Story | Configure flat-rate shipping and free-shipping threshold | 2 | backend-agent | US-019 |
| US-021 | Story | Configure a single sales-tax/VAT rate | 2 | backend-agent | US-019 |

## Sprint 3: Sprint 3

Product images, shopping cart, and checkout address entry

Capacity: 20 points · Committed: 16

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-003 | Story | Add a product variant to the cart | 3 | frontend-agent | US-002 |
| US-004 | Story | Review and adjust the cart | 3 | frontend-agent | US-003 |
| US-005 | Story | Enter email and shipping address at checkout | 5 | frontend-agent | US-004, US-019 |
| US-016 | Story | Upload product images to the app's media storage | 5 | integration-agent | US-014 |

## Sprint 4: Sprint 4

Checkout totals, card payment, order reference, and confirmation email

Capacity: 20 points · Committed: 20

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-006 | Story | See order total with shipping and tax | 5 | backend-agent | US-005, US-020, US-021 |
| US-007 | Story | Pay by card | 8 | integration-agent | US-006, US-015 |
| ↳ US-007-T1 | Task | Integrate Stripe payment intent creation and confirmation | — | integration-agent | — |
| ↳ US-007-T2 | Task | Implement POST /checkout order placement with stock re-validation | — | backend-agent | — |
| ↳ US-007-T3 | Task | Build checkout payment UI with retry handling | — | frontend-agent | — |
| ↳ US-007-T4 | Task | Test payment success, decline and sold-out scenarios | — | qa-agent | — |
| US-008 | Story | Receive a unique order reference | 2 | backend-agent | US-007 |
| US-009 | Story | Receive order confirmation by email | 5 | integration-agent | US-008 |

## Sprint 5: Sprint 5

Order tracking and admin order management

Capacity: 20 points · Committed: 15

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-010 | Story | Look up an order with reference and email | 5 | backend-agent | US-008 |
| US-011 | Story | See current fulfilment stage | 2 | frontend-agent | US-010 |
| US-017 | Story | View the order list | 5 | backend-agent | US-008, US-012, US-013 |
| US-018 | Story | Advance an order through fulfilment stages | 3 | backend-agent | US-017 |

## Unscheduled

_Nothing unscheduled._
<!-- sdlc:auto:end sprints -->
