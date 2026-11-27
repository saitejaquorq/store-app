# Data Model

<!-- sdlc:auto:start entities -->
### category

| Field | Type | PK | FK | Nullable |
|---|---|---|---|---|
| id | uuid | True | — | False |
| name | varchar | False | — | False |
| slug | varchar | False | — | False |

### product

| Field | Type | PK | FK | Nullable |
|---|---|---|---|---|
| id | uuid | True | — | False |
| category_id | uuid | False | category.id | False |
| name | varchar | False | — | False |
| description | text | False | — | True |
| price | numeric(10,2) | False | — | False |
| is_active | boolean | False | — | False |
| created_at | timestamptz | False | — | False |

### product_variant

| Field | Type | PK | FK | Nullable |
|---|---|---|---|---|
| id | uuid | True | — | False |
| product_id | uuid | False | product.id | False |
| size | varchar | False | — | False |
| colour | varchar | False | — | False |
| stock_quantity | integer | False | — | False |
| sku | varchar | False | — | True |

### product_image

| Field | Type | PK | FK | Nullable |
|---|---|---|---|---|
| id | uuid | True | — | False |
| product_id | uuid | False | product.id | False |
| s3_key | varchar | False | — | False |
| position | integer | False | — | False |

### order

| Field | Type | PK | FK | Nullable |
|---|---|---|---|---|
| id | uuid | True | — | False |
| reference | varchar | False | — | False |
| email | varchar | False | — | False |
| shipping_name | varchar | False | — | False |
| shipping_address_line1 | varchar | False | — | False |
| shipping_address_line2 | varchar | False | — | True |
| shipping_city | varchar | False | — | False |
| shipping_postcode | varchar | False | — | False |
| shipping_country | varchar | False | — | False |
| subtotal | numeric(10,2) | False | — | False |
| shipping_amount | numeric(10,2) | False | — | False |
| tax_amount | numeric(10,2) | False | — | False |
| grand_total | numeric(10,2) | False | — | False |
| currency | varchar | False | — | False |
| fulfilment_stage | varchar | False | — | False |
| payment_reference | varchar | False | — | True |
| created_at | timestamptz | False | — | False |

### order_item

| Field | Type | PK | FK | Nullable |
|---|---|---|---|---|
| id | uuid | True | — | False |
| order_id | uuid | False | order.id | False |
| variant_id | uuid | False | product_variant.id | True |
| product_name | varchar | False | — | False |
| size | varchar | False | — | False |
| colour | varchar | False | — | False |
| unit_price | numeric(10,2) | False | — | False |
| quantity | integer | False | — | False |
| line_total | numeric(10,2) | False | — | False |

### admin_user

| Field | Type | PK | FK | Nullable |
|---|---|---|---|---|
| id | uuid | True | — | False |
| username | varchar | False | — | False |
| password_hash | varchar | False | — | False |
| is_active | boolean | False | — | False |
| created_at | timestamptz | False | — | False |

### admin_session

| Field | Type | PK | FK | Nullable |
|---|---|---|---|---|
| token | varchar | True | — | False |
| admin_user_id | uuid | False | admin_user.id | False |
| created_at | timestamptz | False | — | False |
| expires_at | timestamptz | False | — | False |
| revoked_at | timestamptz | False | — | True |

### store_config

| Field | Type | PK | FK | Nullable |
|---|---|---|---|---|
| id | integer | True | — | False |
| country | varchar | False | — | True |
| currency | varchar | False | — | True |
| tax_rate | numeric(5,4) | False | — | True |
| flat_shipping_amount | numeric(10,2) | False | — | True |
| free_shipping_threshold | numeric(10,2) | False | — | True |
| pending_confirmation | boolean | False | — | False |
<!-- sdlc:auto:end entities -->

<!-- sdlc:auto:start relationships -->
| Source | Target | Type |
|---|---|---|
| category | product | one-to-many |
| product | product_variant | one-to-many |
| product | product_image | one-to-many |
| order | order_item | one-to-many |
| product_variant | order_item | one-to-many |
| admin_user | admin_session | one-to-many |
<!-- sdlc:auto:end relationships -->

<!-- sdlc:auto:start er-diagram -->
```mermaid
erDiagram
  category {
    uuid id PK
    varchar name
    varchar slug
  }
  product {
    uuid id PK
    uuid category_id FK
    varchar name
    text description
    numeric_10_2_ price
    boolean is_active
    timestamptz created_at
  }
  product_variant {
    uuid id PK
    uuid product_id FK
    varchar size
    varchar colour
    integer stock_quantity
    varchar sku
  }
  product_image {
    uuid id PK
    uuid product_id FK
    varchar s3_key
    integer position
  }
  order {
    uuid id PK
    varchar reference
    varchar email
    varchar shipping_name
    varchar shipping_address_line1
    varchar shipping_address_line2
    varchar shipping_city
    varchar shipping_postcode
    varchar shipping_country
    numeric_10_2_ subtotal
    numeric_10_2_ shipping_amount
    numeric_10_2_ tax_amount
    numeric_10_2_ grand_total
    varchar currency
    varchar fulfilment_stage
    varchar payment_reference
    timestamptz created_at
  }
  order_item {
    uuid id PK
    uuid order_id FK
    uuid variant_id FK
    varchar product_name
    varchar size
    varchar colour
    numeric_10_2_ unit_price
    integer quantity
    numeric_10_2_ line_total
  }
  admin_user {
    uuid id PK
    varchar username
    varchar password_hash
    boolean is_active
    timestamptz created_at
  }
  admin_session {
    varchar token PK
    uuid admin_user_id FK
    timestamptz created_at
    timestamptz expires_at
    timestamptz revoked_at
  }
  store_config {
    integer id PK
    varchar country
    varchar currency
    numeric_5_4_ tax_rate
    numeric_10_2_ flat_shipping_amount
    numeric_10_2_ free_shipping_threshold
    boolean pending_confirmation
  }
  category ||--o{ product : "one-to-many"
  product ||--o{ product_variant : "one-to-many"
  product ||--o{ product_image : "one-to-many"
  order ||--o{ order_item : "one-to-many"
  product_variant ||--o{ order_item : "one-to-many"
  admin_user ||--o{ admin_session : "one-to-many"
```
<!-- sdlc:auto:end er-diagram -->
