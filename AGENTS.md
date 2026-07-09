# AGENTS.md — alumineu-channel-shopify

**Агент:** SHP · Storefront
**Префикс (GitHub):** `[SHP]`

> **Старт:** прочитай этот файл целиком. Управление — chat-first.
> Hub: [AGENT_BOUNDARY_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENT_BOUNDARY_CANON.md) · [HANDOFF_PROMPTS](https://github.com/krvzdrv/alumineu-os/blob/main/docs/HANDOFF_PROMPTS.md) · [AGENTS_MD_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENTS_MD_CANON.md) · [REPO_DATA_CONTRACT_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/REPO_DATA_CONTRACT_CANON.md)

---

## За что отвечаю (бизнес)

- Будущий Shopify storefront (aluminus.store)
- Channel-specific theme/app — **scaffold**

---

## Data & API

Полный контракт подключений: **`docs/REPO_DATA_CONTRACT.md`** (SSOT; обновлять в той же сессии при изменении подключений).

- **Inbound:** CAT (product data, planned)
- **Outbound:** Shopify storefront customers (future)
- **Internal SSOT:** `.env.example` (env template), theme/app scaffold (planned)
- **Граница данных:** SHP хранит storefront scaffold, не product SSOT

Подключение и обновление токенов — в `docs/REPO_DATA_CONTRACT.md` → § Connection cheat-sheet.

---

## Умею делать (capabilities)

- *(planned)* Theme, Admin API sync, webhooks
- `.env.example` documents required Shopify vars

---

## Доступы (имена env / API — без значений)

| Доступ | Read | Write | Где настроить |
|--------|------|-------|---------------|
| Shopify Admin API | ✓ (planned) | ✓ (planned) | `SHOPIFY_*` in `.env.example` |

Секреты: только GitHub Secrets / локальный `.env` (не коммитить). Способ подключения и обновления токенов — в `docs/REPO_DATA_CONTRACT.md`.

---

## Ключевая документация

- `README.md`, `AGENTS.md`
- Hub `HANDOFF_PROMPTS` — SHP sections when added

---

## Состояние repo

**Scaffold** — No theme/app code yet; env template only.

---

## Граница (не делаю в этом repo)

- Product SSOT in this repo
- Web SEO execution (WEB)

---

## Нужен другой агент?

Сформируй **Handoff** для Owner (не правь чужой repo):
→ `alumineu-os/docs/HANDOFF_PROMPTS.md` — секция «SHP → CAT»

---

## Бэклог (только этот repo)

| Файл | Назначение |
|------|------------|
| `docs/BACKLOG.md` | Агент ведёт **свои** задачи; обновлять после сессии |

Канон бэклога: `alumineu-os/docs/REPO_BACKLOG_CANON.md`.

---

## Конец сессии

- [ ] Бизнес-результат, не рефакторинг структуры
- [ ] `git commit` + `git push`
- [ ] Обнови § Changelog, § Data & API / `docs/REPO_DATA_CONTRACT.md`, § Состояние при изменениях

---

## Гигиена (раз в 2–4 недели)

- [ ] Push веток с работой
- [ ] Удалить ephemeral notes старше 30 дней
- [ ] Актуализировать `docs/REPO_DATA_CONTRACT.md` и § Состояние repo

---

## Changelog

| Дата | Изменение |
|------|-----------|
| 2026-07-08 | AGENTS.md + docs/REPO_DATA_CONTRACT.md (chat-first, role-based, no people/Project) |
| 2026-05-29 | Initial AGENTS.md (docs-only operating system) |
| 2026-05-19 | Полный профиль: capabilities, доступы, docs index, состояние repo |
