# Loyverse (loyverse)

Loyverse is a free point of sale (POS) platform for small and independent retail stores, cafes, bars, and restaurants. The product suite includes the Loyverse POS app (iOS/Android), the Back Office dashboard, Kitchen Display, and Customer Display. The Loyverse API is a documented REST API at `https://api.loyverse.com/v1.0` that exposes the same POS data — items and variants, categories, receipts (sales), customers and loyalty, inventory levels, stores, employees, payment types, taxes, discounts, modifiers, suppliers, POS devices, and shifts — so developers can build integrations for accounting, e-commerce order sync, inventory synchronization, loyalty and marketing, e-invoicing compliance, and custom reporting.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/loyverse/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/loyverse/refs/heads/main/apis.yml)

## Access Model

The Loyverse POS, Dashboard, Kitchen Display, and Customer Display apps are free. Paid add-ons (Employee Management, Advanced Inventory, and Unlimited Sales History) are billed per store. The API is available to all accounts and is accessed over HTTPS.

Two authentication methods are supported:

- **Personal access token (Bearer).** Generated in the Back Office under Settings → Access Tokens (up to 20 per account, each with an optional expiration date). A personal token grants unlimited access to all resources of the account that created it, and is passed as `Authorization: Bearer YOUR_ACCESS_TOKEN`. Best for a merchant integrating their own account.
- **OAuth 2.0 (authorization code).** For third-party apps acting on behalf of other merchants. Register an app in the Loyverse developer dashboard to obtain a `client_id`/`client_secret`, send users to `https://api.loyverse.com/oauth/authorize`, and exchange the code at `https://api.loyverse.com/oauth/token`. Access is limited to the scopes granted (for example `ITEMS_READ`, `RECEIPTS_WRITE`, `INVENTORY_WRITE`, `CUSTOMERS_READ`, `STORES_READ`, `MERCHANT_READ`).

All endpoints are request/response REST over HTTPS with cursor-based pagination. Loyverse also supports webhooks (for example receipt and inventory events); webhooks created through an OAuth app include an `X-Loyverse-Signature` header for verification.

## Tags

- Point of Sale
- POS
- Retail
- Inventory
- Cafe and Restaurant
- Loyalty
- Payments
- Commerce

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Loyverse Items API

Manage the product catalog behind the point of sale — list, create or update, retrieve, and delete items, including their variants, SKUs, pricing, categories, taxes, and modifiers. The core catalog surface for keeping products in sync between Loyverse and e-commerce, ERP, or accounting systems.

- **Human URL:** [https://developer.loyverse.com/docs/#tag/Items](https://developer.loyverse.com/docs/#tag/Items)
- **Base URL:** `https://api.loyverse.com/v1.0`

#### Tags

- Items
- Catalog
- Variants
- Retail
- Inventory

#### Properties

- [Documentation](https://developer.loyverse.com/docs/)
- [API Reference](https://developer.loyverse.com/docs/#tag/Items)
- [OpenAPI](openapi/loyverse-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyverse.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyverse.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Loyverse Categories API

List, create or update, retrieve, and delete the merchandising categories used to organize items across the POS and Back Office reporting.

- **Human URL:** [https://developer.loyverse.com/docs/#tag/Categories](https://developer.loyverse.com/docs/#tag/Categories)
- **Base URL:** `https://api.loyverse.com/v1.0`

#### Tags

- Categories
- Catalog
- Merchandising
- Retail

#### Properties

- [API Reference](https://developer.loyverse.com/docs/#tag/Categories)
- [OpenAPI](openapi/loyverse-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyverse.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyverse.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Loyverse Receipts API

Read sales history and post new sales — list receipts (with line items, payments, taxes, discounts, and refunds), retrieve a single receipt by number, and create receipts to push orders from e-commerce and delivery platforms into Loyverse as sales.

- **Human URL:** [https://developer.loyverse.com/docs/#tag/Receipts](https://developer.loyverse.com/docs/#tag/Receipts)
- **Base URL:** `https://api.loyverse.com/v1.0`

#### Tags

- Receipts
- Sales
- Orders
- Transactions
- Point of Sale

#### Properties

- [API Reference](https://developer.loyverse.com/docs/#tag/Receipts)
- [OpenAPI](openapi/loyverse-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyverse.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyverse.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Loyverse Customers API

Manage the customer directory and loyalty program — list, create or update, retrieve, and delete customers along with their contact details, total visits and spend, and loyalty points, to sync CRM data and run personalized campaigns.

- **Human URL:** [https://developer.loyverse.com/docs/#tag/Customers](https://developer.loyverse.com/docs/#tag/Customers)
- **Base URL:** `https://api.loyverse.com/v1.0`

#### Tags

- Customers
- Loyalty
- CRM
- Marketing

#### Properties

- [API Reference](https://developer.loyverse.com/docs/#tag/Customers)
- [OpenAPI](openapi/loyverse-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyverse.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyverse.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Loyverse Inventory API

Read and set stock on hand per item variant and store — get inventory levels and post updated counts to keep stock synchronized across Loyverse and other platforms such as online stores and warehouses.

- **Human URL:** [https://developer.loyverse.com/docs/#tag/Inventory](https://developer.loyverse.com/docs/#tag/Inventory)
- **Base URL:** `https://api.loyverse.com/v1.0`

#### Tags

- Inventory
- Stock Levels
- Retail
- Warehousing

#### Properties

- [API Reference](https://developer.loyverse.com/docs/#tag/Inventory)
- [OpenAPI](openapi/loyverse-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyverse.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyverse.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Loyverse Stores API

List and retrieve the merchant's stores (locations), providing the `store_id` values that scope receipts, inventory, POS devices, and employees across a multi-location business.

- **Human URL:** [https://developer.loyverse.com/docs/#tag/Stores](https://developer.loyverse.com/docs/#tag/Stores)
- **Base URL:** `https://api.loyverse.com/v1.0`

#### Tags

- Stores
- Locations
- Multi-Location
- Retail

#### Properties

- [API Reference](https://developer.loyverse.com/docs/#tag/Stores)
- [OpenAPI](openapi/loyverse-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyverse.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyverse.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Loyverse Employees API

List, create or update, retrieve, and delete employees who operate the POS, including their roles and store assignments (Employee Management add-on features surface here).

- **Human URL:** [https://developer.loyverse.com/docs/#tag/Employees](https://developer.loyverse.com/docs/#tag/Employees)
- **Base URL:** `https://api.loyverse.com/v1.0`

#### Tags

- Employees
- Staff
- Access Control
- Point of Sale

#### Properties

- [API Reference](https://developer.loyverse.com/docs/#tag/Employees)
- [OpenAPI](openapi/loyverse-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyverse.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyverse.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Authentication](authentication/loyverse-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/loyverse)
- [Website](https://loyverse.com)
- [Documentation](https://developer.loyverse.com/docs/)
- [Sign Up](https://developer.loyverse.com)
- [Plans](plans/loyverse-plans-pricing.yml)
- [Rate Limits](rate-limits/loyverse-rate-limits.yml)
- [Fin Ops](finops/loyverse-finops.yml)
- [Support](https://help.loyverse.com/help/api-marketplace)
- [Community](https://loyverse.town/clubs/2-loyverse-api/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
