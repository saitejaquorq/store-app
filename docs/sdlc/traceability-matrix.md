# Traceability Matrix

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start legend -->
Built from recorded links, not written by a model: requirement key → plan item (`source_stable_key`) → development ticket (`stable_key`) → the ticket's test steps → the last live deployment that started after the work finished. **AC tests** counts the story's acceptance criteria that have a test case, and those whose test cases all passed in the latest finished E2E run. **Tests** counts the tests written for the story, and **Result** how many last passed, how many failed and when, as of this page's generation; the Documentation tab shows them live.
<!-- sdlc:auto:end legend -->

<!-- sdlc:auto:start matrix -->
| Requirement | Epic | Title | Plan items | Sprint | Design | Code | Commits | Ticket | Test step | Tests | Result | AC tests | Deployed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| US-001 | EPIC-001 | Browse catalogue by category | US-001, US-001-T1, US-001-T2, US-001-T3, US-001-T4 | 1 | GET /categories, GET /categories/{slug}/products, api, category, db, product, spa | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-002 | EPIC-001 | View product detail page | US-002 | 2 | GET /products/{id}, api, product, product_image, product_variant, spa | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-003 | EPIC-002 | Add a product variant to the cart | US-003 | 3 | product_variant, spa | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
| US-004 | EPIC-002 | Review and adjust the cart | US-004 | 3 | product_variant, spa | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-005 | EPIC-003 | Enter email and shipping address at checkout | US-005 | 3 | POST /checkout/quote, api, customer_order, spa, store_config | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-006 | EPIC-003 | See order total with shipping and tax | US-006 | 4 | POST /checkout/quote, api, store_config | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-007 | EPIC-003 | Pay by card | US-007, US-007-T1, US-007-T2, US-007-T3, US-007-T4 | 4 | POST /checkout, api, customer_order, db, order_item, payment, product_variant, spa | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-008 | EPIC-004 | Receive a unique order reference | US-008 | 4 | POST /checkout, api, customer_order, db | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
| US-009 | EPIC-004 | Receive order confirmation by email | US-009 | 4 | POST /checkout, api, customer_order, email, order_item | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
| US-010 | EPIC-005 | Look up an order with reference and email | US-010 | 5 | POST /orders/track, api, customer_order, db, order_item | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-011 | EPIC-005 | See current fulfilment stage | US-011 | 5 | POST /orders/track, api, customer_order, spa | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
| US-012 | EPIC-006 | Admin sign-in to the protected area | US-012 | 1 | POST /admin/login, admin_session, admin_user, api, db, spa | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-013 | EPIC-006 | Protect admin area and end sessions | US-013 | 1 | POST /admin/logout, admin_session, api, spa | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-014 | EPIC-007 | Create and edit products with categories, descriptions and prices | US-014 | 2 | GET /admin/products, POST /admin/products, PUT /admin/products/{id}, api, category, db, product, spa | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-015 | EPIC-007 | Manage size and colour variants with per-variant stock | US-015 | 2 | POST /admin/products/{id}/variants, api, db, product_variant | — | — | not started | not run | 0 | No tests | 0/3 tested · 0/3 passing | — |
| US-016 | EPIC-007 | Upload product images to the app's media storage | US-016 | 3 | DELETE /admin/products/{id}/images/{image_id}, POST /admin/products/{id}/images, api, media_store, product_image, spa | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
| US-017 | EPIC-008 | View the order list | US-017 | 5 | GET /admin/orders, GET /admin/orders/{id}, api, customer_order, order_item, spa | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
| US-018 | EPIC-008 | Advance an order through fulfilment stages | US-018 | 5 | PATCH /admin/orders/{id}/stage, api, customer_order, spa | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
| US-019 | EPIC-009 | Configure single country and currency | US-019 | 1 | GET /admin/config, PUT /admin/config, api, db, store_config | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
| US-020 | EPIC-009 | Configure flat-rate shipping and free-shipping threshold | US-020 | 2 | GET /admin/config, PUT /admin/config, api, store_config | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
| US-021 | EPIC-009 | Configure a single sales-tax/VAT rate | US-021 | 2 | GET /admin/config, PUT /admin/config, api, store_config | — | — | not started | not run | 0 | No tests | 0/2 tested · 0/2 passing | — |
<!-- sdlc:auto:end matrix -->
