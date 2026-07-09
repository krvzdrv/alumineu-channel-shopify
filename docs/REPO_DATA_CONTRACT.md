```yaml
repo: alumineu-channel-shopify
agent: SHP-Storefront
purpose: Будущий Shopify storefront (aluminus.store) — theme/app scaffold
updated_at: 2026-07-08
inbound:
  - source: alumineu-product-catalog (CAT · Forge)
    what: product data (planned)
    interface: Postgres view / CSV / repo read (planned)
    auth: уточнить при первом подключении
    env: []
    token_file: null
    access: read
    status: planned
outbound:
  - consumer: Shopify storefront customers
    what: storefront products, cart, checkout (future)
    interface: Shopify Storefront API (future)
    contract_ref: null
    access: read+write
stores:
  - .env.example (env template)
  - theme/app scaffold (planned)
```

## Purpose

Будущий Shopify storefront (aluminus.store). Repo сейчас — scaffold: нет theme/app кода, только env template (`.env.example`).

## Inbound — откуда берём данные

| Source | What | Interface | Auth/env | Access | Notes |
|--------|------|-----------|----------|--------|-------|
| CAT · Forge (alumineu-product-catalog) | product data | Postgres view / CSV / repo read | уточнить при первом подключении | read | planned — sync ещё не реализован |

## Outbound — кому отдаём

| Consumer | What | Interface | Contract_ref | Access | Notes |
|----------|------|-----------|--------------|--------|-------|
| Shopify storefront customers | storefront products, cart, checkout | Shopify Storefront API | — | read+write | future — storefront не запущен |

## Internal stores

- `.env.example` — required Shopify vars (`SHOPIFY_*`)
- theme/app scaffold (planned, ещё нет кода)

## Data flow

```
CAT (product data, planned)
   │
   ▼
[alumineu-channel-shopify]  (scaffold)
   │  Theme + Admin API sync (planned)
   ▼
Shopify storefront customers (future)
```

## Boundaries

**Делает:**
- Shopify storefront theme/app (planned)
- Admin API sync, webhooks (planned)
- Env template для `SHOPIFY_*`

**Не делает:**
- Product SSOT in this repo (CAT)
- Web SEO execution (WEB)

## Connection cheat-sheet

### Shopify Admin API
- **Where token lives:** `SHOPIFY_*` vars в локальном `.env` (см. `.env.example`; **не коммитить**).
- **Connect (~1 min):** `cp .env.example .env`, fill `SHOPIFY_SHOP`, `SHOPIFY_ACCESS_TOKEN` (Admin API token из Shopify Partner dashboard → App → API credentials). Admin API access scoped per app.
- **Refresh when expired:** Admin API access tokens долгоживущие; rotate через Shopify Partner dashboard → App → API credentials → reinstall app if revoked. Уточнить конкретный flow при первом подключении (storefront ещё не создан).
