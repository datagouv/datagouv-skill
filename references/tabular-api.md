# Tabular API

**Base URL:** `https://tabular-api.data.gouv.fr` | Swagger: https://tabular-api.data.gouv.fr/api/doc | Per-resource: `GET /api/resources/{rid}/swagger/`

`{rid}` = resource UUID from main API (dataset's resources).

**Tabular data workflow (use in order):**

1. `GET /api/resources/{rid}/` — confirm the resource is exposed and get links.
2. `GET /api/resources/{rid}/profile/` — column types, stats, indexes.
3. `GET /api/resources/{rid}/swagger/` — allowed query params and operators per column (read before complex filters).
4. `GET /api/resources/{rid}/data/` — `page` and `page_size` (max **50**). For aggregations, check `/api/aggregation-exceptions/` first (only listed resources/columns may support groupby/count/sum, etc.).

| Method | Path | Description |
|--------|------|-------------|
| GET | `/api/resources/{rid}/` | Metadata, links to profile/data/swagger |
| GET | `/api/resources/{rid}/profile/` | Column types, formats, stats, indexes |
| GET | `/api/resources/{rid}/swagger/` | OpenAPI for data endpoint (columns, operators) |
| GET | `/api/aggregation-exceptions/` | Resource UUIDs allowed for aggregation |
| GET | `/api/resources/{rid}/data/` | Filter, sort, paginate (page, page_size max 50) |
| GET | `/api/resources/{rid}/data/csv/` | Stream CSV |
| GET | `/api/resources/{rid}/data/json/` | Stream JSON |
| GET | `/health/` | Health check |

**Data params:** `columns=col1,col2` | Filter: `column__exact`, `__differs`, `__isnull`, `__isnotnull`, `__contains`, `__notcontains`, `__in`, `__notin`, `__less`, `__greater`, `__strictly_less`, `__strictly_greater` | Sort: `column__sort=asc|desc` | Aggregation (allowed resources, indexed cols): `column__groupby`, `__count`, `__avg`, `__min`, `__max`, `__sum`. JSON columns: only isnull/isnotnull.
