# AGENTS.md — alumineu-channel-shopify

**Агент:** SHP · Storefront (`shp-storefront`)
**Префикс (GitHub):** `[SHP]`

> **Старт:** прочитай этот файл целиком. Управление — chat-first.
> Hub: [COMMUNICATION_LANGUAGE_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/COMMUNICATION_LANGUAGE_CANON.md) · [AGENT_BOUNDARY_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENT_BOUNDARY_CANON.md) · [AGENT_IDENTITY_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENT_IDENTITY_CANON.md) · [HANDOFF_PROMPTS](https://github.com/krvzdrv/alumineu-os/blob/main/docs/HANDOFF_PROMPTS.md) · [AGENTS_MD_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENTS_MD_CANON.md) · [REPO_DATA_CONTRACT_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/REPO_DATA_CONTRACT_CANON.md)

---

## За что отвечаю (бизнес)

- Shopify storefront и channel logic для **US / американского рынка** (живой канал)
- Theme/app, Admin/Storefront API, webhooks, channel automation
- Не product SSOT (CAT), не OS-правила (GOV), не бизнес-модель (MDL)

---

## Язык и коммуникация

Канон (все агенты): [`COMMUNICATION_LANGUAGE_CANON`](https://github.com/krvzdrv/alumineu-os/blob/main/docs/COMMUNICATION_LANGUAGE_CANON.md).

- Чат, docs, бэклог, handoff — по канону (русский, без сленга и лишних англицизмов).
- Код, SQL, API — как в системе.

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

- **`docs/DOC_INDEX.md`** — карта живых SSOT vs archive

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

<!-- zone-route:v1 -->

### Если задача не моя

Стоп **до инструментов**. Одна фраза Owner + один code block (hub `HANDOFF_PROMPTS`). Исключение — «сделай в этом чате, зона не важна».
Полная таблица: hub [`AGENT_BOUNDARY_CANON` §3a](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENT_BOUNDARY_CANON.md).

| Видишь | Иди к |
|--------|-------|
| SKU / контент / медиа-мастера | CAT · Forge (`alumineu-product-catalog`) |
| alumineu.nl / Next.js | WEB · Signal (`alumineu-channel-web`) |
| Meta Pixel Tilda | MTA · Radar (`alumineu-channel-meta`) |
| Google Merchant | GGL · Merchant (`alumineu-channel-google`) |

## Нужен другой агент?

Мы — **команда** (chat-first). Чужой repo **не править**.

Если нужна помощь другого агента:
1. Напиши Owner **готовый промпт** в **одном fenced code block** в этом чате (кнопка Copy) — в т.ч. удобно для терминальных агентов, без открытия файлов.
2. Owner вставляет блок в **новый чат** target repo.
3. Шаблоны: hub [`HANDOFF_PROMPTS`](https://github.com/krvzdrv/alumineu-os/blob/main/docs/HANDOFF_PROMPTS.md) — секция «SHP → CAT».

**Запрещено** для передачи задачи: создавать `docs/*HANDOFF*`, `docs/handoffs/*` и прочие «письма агенту» в git. Это мусор. Контекст — только в промпте в чате. Живые SSOT (контракты, API) — отдельно, не как handoff.


---

## Бэклог (только этот repo)

| Файл | Назначение |
|------|------------|
| `docs/BACKLOG.md` | Свои задачи; обновлять после сессии |

---

## Конец сессии

- [ ] Бизнес-результат
- [ ] Если трогали API — `REPO_DATA_CONTRACT.md` + § Data & API обновлены
- [ ] Свои правки — commit + push **сам**, без вопроса. В чат: `git status`, hash, куда запушил. Секреты и чужой хвост не коммитить. Молчаливый dirty / unpushed = не Done
- [ ] Changelog при изменениях

---

## Гигиена (раз в 2–4 недели)

- [ ] `./scripts/adhoc_cleanup.sh` + очистить `scratch/`

- [ ] Push веток
- [ ] Сверить `REPO_DATA_CONTRACT.md` с живым Shopify admin (apps, scopes)
- [ ] Ephemeral notes > 30 дней

---

## Changelog

| Дата | Изменение |
|------|-----------|
| 2026-08-18 | Конец сессии: commit + push сам (hub `AGENT_BOUNDARY_CANON` §7); без «спроси Owner» |
| 2026-08-13 | Граница на входе: session-start зона + «не моё → кто»; git status Owner (GOV-018) |
| 2026-07-09 | Ephemeral: scratch/ + docs/adhoc/ + EPHEMERAL_WORK_CANON |
| 2026-07-09 | Язык: hub COMMUNICATION_LANGUAGE_CANON + DOC_INDEX |
| 2026-07-09 | Status: Production US market (not scaffold); Data & API hard rule |
| 2026-07-09 | REPO_DATA_CONTRACT.md initial |
| 2026-05-29 | Initial AGENTS.md |
