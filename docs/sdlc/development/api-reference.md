# API Reference

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start endpoints -->
| Method | Path | Handler | Source | Summary |
|---|---|---|---|---|
| GET | /health | health | `backend/app/main.py:84` | Liveness probe, and the only route here that is not a stub. |
<!-- sdlc:auto:end endpoints -->

<!-- sdlc:auto:start drift -->
**Designed but missing:**

- DELETE /admin/products/{id}/images/{image_id}
- GET /admin/config
- GET /admin/orders
- GET /admin/orders/{id}
- GET /admin/products
- GET /categories
- GET /categories/{slug}/products
- GET /products/{id}
- PATCH /admin/orders/{id}/stage
- POST /admin/login
- POST /admin/logout
- POST /admin/products
- POST /admin/products/{id}/images
- POST /admin/products/{id}/variants
- POST /checkout
- POST /checkout/quote
- POST /orders/track
- PUT /admin/config
- PUT /admin/products/{id}
<!-- sdlc:auto:end drift -->

<!-- sdlc:auto:start source -->
Generated from commit `c460a7c`
<!-- sdlc:auto:end source -->
