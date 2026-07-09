```yaml
repo: alumineu-channel-shopify
agent: SHP-Storefront
purpose: Shopify storefront + channel logic for US / American market (live)
updated_at: 2026-07-09
inbound:
  - source: alumineu-product-catalog (CAT · Forge)
    what: product identity, content, prices for channel projection
    interface: Postgres view / export / sync (уточнить актуальный path)
    auth: per CAT contract / shared Supabase read if used
    env: []
    token_file: null
    access: read
    status: active
  - source: Shopify Admin API
    what: products, collections, orders, inventory, apps config
    interface: REST / GraphQL Admin API
    auth: env / private app token
    env: [SHOPIFY_SHOP, SHOPIFY_ACCESS_TOKEN]
    token_file: null
    access: read+write
    status: active
  - source: Shopify Storefront API
    what: catalog browse, cart, checkout session
    interface: Storefront GraphQL
    auth: storefront access token
    env: [SHOPIFY_STOREFRONT_TOKEN]
    token_file: null
    access: read+write
    status: active
outbound:
  - consumer: US storefront customers
    what: storefront UX, cart, checkout
    interface: Shopify Online Store / custom storefront
    contract_ref: null
    access: read+write
  - consumer: Owner / ops
    what: orders and channel ops surfaces in Shopify admin
    interface: Shopify Admin
    contract_ref: null
    access: read+write
stores:
  - theme / app code (this repo and/or Shopify-hosted theme)
  - .env / GitHub Secrets for SHOPIFY_* (never commit secrets)
  - docs/REPO_DATA_CONTRACT.md — SSOT подключений
```

## Purpose

`alumineu-channel-shopify` — **живой** Shopify-канал для американского рынка (US).
Implementation storefront/channel; не product SSOT и не company OS.

> **Owner note (2026-07-09):** US site raised via this channel.  
> Агент SHP обязан сверить YAML/таблицы ниже с фактическими apps, scopes и sync path от CAT
> и поправить `status`/env names в той же сессии, когда расхождение найдено.

## Inbound — откуда берём данные

| Source | What | Interface | Auth/env | Access | Notes |
|--------|------|-----------|----------|--------|-------|
| CAT · Forge | product projection | view / export / sync | per CAT | read | Product SSOT остаётся в CAT |
| Shopify Admin API | catalog ops, orders | Admin REST/GraphQL | `SHOPIFY_SHOP`, `SHOPIFY_ACCESS_TOKEN` | read+write | Имена env сверить с `.env.example` / Secrets |
| Shopify Storefront API | storefront data | Storefront GraphQL | `SHOPIFY_STOREFRONT_TOKEN` | read+write | |

## Outbound — кому отдаём

| Consumer | What | Interface | Access | Notes |
|----------|------|-----------|--------|-------|
| US customers | storefront | Shopify storefront | read+write | Live US market |
| Owner / ops | orders, apps | Shopify Admin | read+write | |

## Internal stores

- Theme/app и channel automation в этом repo (и/или Shopify-hosted theme)
- Secrets только в `.env` / GitHub Secrets
- Этот контракт — SSOT «к чему подключены»

## Data flow

```
CAT (product master) ──read──► SHP · Storefront ──► Shopify (US)
                                      │
                                      ├── Admin API
                                      └── Storefront API
                                              │
                                              ▼
                                         US customers
```

## Boundaries

**Делает:**
- US Shopify storefront / theme / apps / webhooks
- Channel sync от CAT (не дублируя product SSOT)
- Актуализация этого контракта при смене API

**Не делает:**
- Product master / price facts (CAT)
- Pricing policy (PRC)
- ETL CRM/WMS (DAT)
- OS canons / business model / BPMN

## Connection cheat-sheet

### Shopify Admin API
- **Env:** `SHOPIFY_SHOP`, `SHOPIFY_ACCESS_TOKEN` (точные имена — сверить `.env.example`)
- **Где:** локальный `.env` / GitHub Secrets — **не коммитить**
- **Connect:** Partner/Admin → App → API credentials → scopes для US store
- **Refresh:** rotate token в Shopify Admin → обновить secret → smoke Admin GraphQL

### Shopify Storefront API
- **Env:** `SHOPIFY_STOREFRONT_TOKEN` (сверить)
- **Refresh:** Headless/Storefront API token в admin → обновить env

### CAT
- Read-only product projection; при смене контракта — handoff CAT + обновить Inbound здесь
