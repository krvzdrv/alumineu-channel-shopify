# AGENTS.md — alumineu-channel-shopify

**Агент:** SHP · Storefront  
**Префикс (GitHub):** `[SHP]`

> **Старт:** прочитай этот файл. **GitHub Project не используется** как очередь.  
> Hub: [AGENT_BOUNDARY_CANON](https://github.com/krvzdrv/alumineu-os/blob/main/docs/AGENT_BOUNDARY_CANON.md) · [HANDOFF_PROMPTS](https://github.com/krvzdrv/alumineu-os/blob/main/docs/HANDOFF_PROMPTS.md)

---

## За что отвечаю (бизнес)

- Shopify storefront, theme, apps

---

## Откуда беру данные (upstream)

| Источник | Repo | Что именно |
|----------|------|------------|
| CAT | alumineu-product-catalog | product identity |

---

## Кому отдаю (downstream)

- Shopify storefront

---

## Никогда не делаю в этом repo

- Product master SSOT
- DAT ETL

---

## Нужен другой агент?

Сформируй **Handoff** для владельца (не правь чужой repo):  
→ `alumineu-os/docs/HANDOFF_PROMPTS.md` — секция «SHP → CAT»

---

## Конец сессии

- [ ] Бизнес-результат, не рефакторинг структуры
- [ ] `git commit` + `git push`
- [ ] Обнови § Changelog если менялись границы

---

## Гигиена (раз в 2–4 недели)

- [ ] Push веток с работой
- [ ] Удалить `docs/notes/*` старше 30 дней
- [ ] Проверить upstream/downstream таблицы

---

## Changelog

| Дата | Изменение |
|------|-----------|
| 2026-05-29 | Initial AGENTS.md (docs-only operating system) |
