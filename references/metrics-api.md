# Metrics API

**Base URL:** `https://metric-api.data.gouv.fr` | Swagger: https://metric-api.data.gouv.fr/api/doc

| Method | Path | Description |
|--------|------|-------------|
| GET | `/api/{model}/data/` | Paginated metrics rows (JSON). Params: page, page_size, column__sort, column__exact, column__contains, column__less, column__greater |
| GET | `/api/{model}/data/csv/` | Metrics **export** for `{model}` as CSV (same column filters as JSON where applicable; **not** the Tabular API resource CSV format) |
| GET | `/health/` | Health check |

`{model}` = table name (e.g. site, organization, dataset). See Swagger for models and columns.
