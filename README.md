# Loyverse (loyverse)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
