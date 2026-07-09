# AGENTS.md — alumineu-channel-shopify

**Агент:** SHP · Storefront
**Префикс (GitHub):** `[SHP]`

> **Старт:** прочитай этот файл целиком. Управление — chat-first.
> Hub: [AGENT_BOUNDARY_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENT_BOUNDARY_CANON.md) · [HANDOFF_PROMPTS](https://github.com/krvzdrv/alumineu-os/blob/main/docs/HANDOFF_PROMPTS.md) · [AGENTS_MD_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENTS_MD_CANON.md) · [REPO_DATA_CONTRACT_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/REPO_DATA_CONTRACT_CANON.md)

---

## За что отвечаю (бизнес)

- Shopify storefront и channel logic для **US / американского рынка** (живой канал)
- Theme/app, Admin/Storefront API, webhooks, channel automation
- Не product SSOT (CAT), не OS-правила (GOV), не бизнес-модель (MDL)

---

## Data & API

Полный контракт подключений: **`docs/REPO_DATA_CONTRACT.md`** (SSOT).

**Правило:** новое/изменённое API → обновить контракт + эту сводку в той же сессии (иначе не Done).
Канон: `alumineu-os/docs/REPO_DATA_CONTRACT_CANON.md` §0.

- **Inbound:** CAT (product projections); Shopify Admin/Storefront APIs
- **Outbound:** US storefront customers; channel events per contract
- **Internal SSOT:** theme/app, Shopify apps config, env (`SHOPIFY_*`)
- **Граница данных:** channel execution only — product master в CAT

Подключение и обновление токенов — в `docs/REPO_DATA_CONTRACT.md` → § Connection cheat-sheet.

---

## Умею делать (capabilities)

- Shopify theme / app / Admin API sync / webhooks (US storefront)
- Держать `docs/REPO_DATA_CONTRACT.md` в sync с реальными apps и scopes

---

## Доступы (имена env / API — без значений)

| Доступ | Read | Write | Где настроить |
|--------|------|-------|---------------|
| Shopify Admin API | ✓ | ✓ | `SHOPIFY_*` в `.env` / Secrets |
| Shopify Storefront API | ✓ | ✓ (cart/checkout) | `SHOPIFY_*` |
| CAT product data | ✓ | ✗ | per contract / handoff CAT |

Секреты: только GitHub Secrets / локальный `.env` (не коммитить).

---

## Ключевая документация

- `README.md`, `docs/REPO_DATA_CONTRACT.md`, `docs/BACKLOG.md`
- Hub: `REPO_PORTFOLIO.md`, `HANDOFF_PROMPTS.md`

---

## Состояние repo

**Production** — US / американский рынок live (storefront).  
Контракт API обязан отражать фактические apps/tokens (см. Next в backlog).

---

## Граница (не делаю в этом repo)

- Product SSOT / price facts (CAT)
- Pricing policy (PRC)
- ETL Planfix/MoySklad (DAT)
- Organic SEO / Next.js PL site (WEB)
- OS canons / business model / BPMN

---

## Нужен другой агент?

Сформируй **Handoff** для Owner:
→ `alumineu-os/docs/HANDOFF_PROMPTS.md` — секция «SHP → CAT»

---

## Бэклог (только этот repo)

| Файл | Назначение |
|------|------------|
| `docs/BACKLOG.md` | Свои задачи; обновлять после сессии |

---

## Конец сессии

- [ ] Бизнес-результат
- [ ] Если трогали API — `REPO_DATA_CONTRACT.md` + § Data & API обновлены
- [ ] `git commit` + `git push`
- [ ] Changelog при изменениях

---

## Гигиена (раз в 2–4 недели)

- [ ] Push веток
- [ ] Сверить `REPO_DATA_CONTRACT.md` с живым Shopify admin (apps, scopes)
- [ ] Ephemeral notes > 30 дней

---

## Changelog

| Дата | Изменение |
|------|-----------|
| 2026-07-09 | Status: Production US market (not scaffold); Data & API hard rule |
| 2026-07-09 | REPO_DATA_CONTRACT.md initial |
| 2026-05-29 | Initial AGENTS.md |
