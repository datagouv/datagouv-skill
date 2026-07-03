# Dataservices (external APIs)

External administrative or public HTTP APIs were historically listed on **api.gouv.fr**; they are now represented as **dataservices** on data.gouv.fr (`GET /dataservices/`, object fields below). Catalog routes use the Main API base URL (`https://www.data.gouv.fr/api/1/`). For other Main API routes, see [main-api.md](main-api.md).

| Method | Path |
|--------|------|
| GET/POST | `/dataservices/` — GET: q, page, page_size, organization, owner, topic, tag, access_type, featured, dataset, sort |
| GET/PATCH/DELETE | `/dataservices/{id}/` — GET returns `base_api_url`, `machine_documentation_url` (OpenAPI/Swagger spec), title, description, organization, license, etc. |
| POST | `/dataservices/{id}/datasets/` — body: [{id}] |
| DELETE | `/dataservices/{id}/datasets/{dataset}/` |
| POST/DELETE | `/dataservices/{id}/featured/` |
| GET | `/dataservices/{id}/rdf`, `rdf.{_format}` |
| GET/POST/DELETE | `/dataservices/{id}/followers/` |
| GET | `/dataservices/recent.atom` |

**Access and auth:** Each object includes **`access_type`** (and related fields such as `access_type_reason`, `authorization_request_url`). Rules are **per dataservice**, not platform-wide: follow the web page (`self_web_url`), **`business_documentation_url`**, and the upstream OpenAPI for API keys, OAuth, DataPass, or other flows.

**Rate limits:** **`rate_limiting`** and **`rate_limiting_url`** describe **producer** quotas on the external API. The Main API's **`X-RateLimit-*`** headers apply only to **catalog** requests (`/dataservices/`, etc.), not to calls you make to `base_api_url`.

**Bulk export (metadata):** `GET /site/dataservices.csv` returns a site-wide CSV of dataservice rows for spreadsheets or scripts (same catalog as the JSON list).

**OpenAPI is authoritative:** Always fetch **`machine_documentation_url`** before calling the live API. Paths, parameters, and schemas come from that spec; if human text on the portal or this skill disagrees with the fetched OpenAPI, **trust the OpenAPI** (same principle as Metrics and Tabular Swaggers — see [SKILL.md](../SKILL.md#references-and-freshness)).

**To use a dataservice:** (1) Find it: MCP **`search_dataservices`** or `GET /dataservices/?q=term` (follow **`next_page`** until done). (2) GET `/dataservices/{id}/` (or the MCP equivalent) for `machine_documentation_url` and `base_api_url`. (3) Fetch `machine_documentation_url` for the OpenAPI spec. (4) Call **`base_api_url`** per that spec.
