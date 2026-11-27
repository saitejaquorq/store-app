# Sprint Plan

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start sprints -->
## Sprint 1: Sprint 1

Admin can sign in to a protected area and the store's country, shipping and tax configuration exists

Capacity: 20 points · Committed: 20

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-012 | Story | Admin sign-in to the protected area | 8 | backend-agent | — |
| ↳ US-012-T1 | Task | Add admin_user and admin_session schema | — | backend-agent | — |
| ↳ US-012-T2 | Task | Implement POST /admin/login endpoint | — | backend-agent | — |
| ↳ US-012-T3 | Task | Build admin sign-in screen | — | frontend-agent | — |
| US-013 | Story | Protect admin area and end sessions | 5 | security-agent | US-012 |
| US-019 | Story | Configure single country and currency | 3 | backend-agent | US-013 |
| US-020 | Story | Configure flat-rate shipping and free-shipping threshold | 2 | backend-agent | US-019 |
| US-021 | Story | Configure a single sales-tax/VAT rate | 2 | backend-agent | US-019 |

## Sprint 2: Sprint 2

Admins can create products and define variants with stock in the catalogue

Capacity: 20 points · Committed: 16

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-014 | Story | Create and edit products with categories, descriptions and prices | 8 | backend-agent | US-013 |
| ↳ US-014-T1 | Task | Add product and category schema | — | backend-agent | — |
| ↳ US-014-T2 | Task | Implement product CRUD endpoints | — | backend-agent | — |
| ↳ US-014-T3 | Task | Build admin product management screen | — | frontend-agent | — |
| US-015 | Story | Manage size and colour variants with per-variant stock | 8 | backend-agent | US-014 |
| ↳ US-015-T1 | Task | Add product_variant schema with stock column | — | backend-agent | — |
| ↳ US-015-T2 | Task | Implement variant management endpoint | — | backend-agent | — |
| ↳ US-015-T3 | Task | Build variant and stock editor UI | — | frontend-agent | — |

## Sprint 3: Sprint 3

Customers can browse categories and view product detail pages with images and variants

Capacity: 20 points · Committed: 18

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-001 | Story | Browse catalogue by category | 8 | frontend-agent | US-014 |
| ↳ US-001-T1 | Task | Implement category listing endpoints | — | backend-agent | — |
| ↳ US-001-T2 | Task | Build responsive category browsing UI | — | frontend-agent | — |
| US-002 | Story | View product detail page | 5 | frontend-agent | US-001, US-015 |
| US-016 | Story | Upload product images to the app's media storage | 5 | integration-agent | US-014 |

## Sprint 4: Sprint 4

Customers can build a cart and complete the checkout form with shipping and tax totals

Capacity: 20 points · Committed: 18

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-003 | Story | Add a product variant to the cart | 5 | frontend-agent | US-002 |
| US-004 | Story | Review and adjust the cart | 3 | frontend-agent | US-003 |
| US-005 | Story | Enter email and shipping address at checkout | 5 | frontend-agent | US-004, US-019 |
| US-006 | Story | See order total with shipping and tax | 5 | backend-agent | US-005, US-020, US-021 |

## Sprint 5: Sprint 5

Customers can pay by card and receive an order reference and confirmation email

Capacity: 20 points · Committed: 16

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-007 | Story | Pay by card | 8 | integration-agent | US-006 |
| ↳ US-007-T1 | Task | Integrate Stripe charge in checkout endpoint | — | integration-agent | — |
| ↳ US-007-T2 | Task | Add stock re-validation at checkout | — | backend-agent | — |
| ↳ US-007-T3 | Task | Build payment form with retry handling | — | frontend-agent | — |
| US-008 | Story | Receive a unique order reference | 3 | backend-agent | US-007 |
| US-009 | Story | Receive order confirmation by email | 5 | integration-agent | US-008 |

## Sprint 6: Sprint 6

Admins can process orders and customers can track fulfilment stage by reference and email

Capacity: 20 points · Committed: 16

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-010 | Story | Look up an order with reference and email | 5 | backend-agent | US-008 |
| US-011 | Story | See current fulfilment stage | 3 | frontend-agent | US-010, US-018 |
| US-017 | Story | View the order list | 5 | backend-agent | US-009, US-013 |
| US-018 | Story | Advance an order through fulfilment stages | 3 | backend-agent | US-017 |

## Unscheduled

_Nothing unscheduled._
<!-- sdlc:auto:end sprints -->
