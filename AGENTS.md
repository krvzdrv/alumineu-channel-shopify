# AGENTS.md — alumineu-channel-shopify

**Агент:** SHP · Storefront  
**Префикс (GitHub):** `[SHP]`

> **Старт:** прочитай этот файл. **GitHub Project не используется** как очередь.  
> Hub: [AGENT_BOUNDARY_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENT_BOUNDARY_CANON.md) · [HANDOFF_PROMPTS](https://github.com/krvzdrv/alumineu-os/blob/main/docs/HANDOFF_PROMPTS.md) · [AGENTS_MD_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENTS_MD_CANON.md)

---

## За что отвечаю (бизнес)

- Будущий Shopify storefront (aluminus.store)
- Channel-specific theme/app — **scaffold**
---

## Откуда беру данные (upstream)

| Источник | Repo / система | Что именно |
|----------|----------------|------------|
| CAT · Forge | alumineu-product-catalog | product data (planned) |
---

## Кому отдаю (downstream)

- Shopify storefront customers (future)
---

## Умею делать (capabilities)

- *(planned)* Theme, Admin API sync, webhooks
- `.env.example` documents required Shopify vars
---

## Доступы (имена env / API — без значений)

| Доступ | Read | Write | Где настроить |
|--------|------|-------|---------------|
| Shopify Admin API | ✓ (planned) | ✓ (planned) | `SHOPIFY_*` in `.env.example` |

Секреты: GitHub Secrets / локальный `.env` (не коммитить). OAuth Google часто через `alumineu-finance-ops` (`GOOGLE_AUTH_ROOT`).

---

## Ключевая документация

- `README.md`, `AGENTS.md`
- Hub `HANDOFF_PROMPTS` — SHP sections when added
---

## Состояние repo

**Scaffold** — No theme/app code yet; env template only.

---

## Никогда не делаю в этом repo

- Product SSOT in this repo
- Web SEO execution (WEB)
---

## Нужен другой агент?

Сформируй **Handoff** для владельца (не правь чужой repo):  
→ `alumineu-os/docs/HANDOFF_PROMPTS.md` — секция «SHP → CAT»


## Конец сессии

- [ ] Бизнес-результат, не рефакторинг структуры
- [ ] `git commit` + `git push`
- [ ] Обнови § Changelog и § Умею делать / Доступы / Состояние при изменениях

---

## Гигиена (раз в 2–4 недели)

- [ ] Push веток с работой
- [ ] Удалить ephemeral notes старше 30 дней
- [ ] Актуализировать upstream/downstream и § Состояние repo

---

## Changelog

| Дата | Изменение |
|------|-----------|
| 2026-05-29 | Initial AGENTS.md (docs-only operating system) |
| 2026-05-19 | Полный профиль: capabilities, доступы, docs index, состояние repo |
