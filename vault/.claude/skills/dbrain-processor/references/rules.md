# Critical Processing Rules

See [ABOUT.md](ABOUT.md) for user context and preferences.

## Rule 1: Skip Processed Entries

```
If entry contains `<!-- ✓ processed` → SKIP COMPLETELY
```

Check AFTER each `## HH:MM` header for the marker.

## Rule 2: Every Task = Date

**NEVER create a task without `dueString`:**

| Text | dueString |
|------|-----------|
| завтра | tomorrow |
| в пятницу | friday |
| на этой неделе | friday |
| в четверг | thursday |
| 15 января | January 15 |
| срочно | today |
| NOT SPECIFIED | in 3 days |

## Rule 3: Check Duplicates

**BEFORE creating any task:**

1. Call `find-tasks` with key words from task
2. If similar task exists → **DO NOT CREATE**
3. Mark as: `<!-- ✓ processed: task (duplicate) -->`

## Rule 4: Consider Workload

**BEFORE creating tasks:**

1. Call `find-tasks-by-date` with `startDate: "today"`, `daysCount: 7`
2. Count tasks per day
3. If target day has 3+ tasks → shift to next day with less load
4. Exception: 🔴 Red tasks (Николаева, платежи) always go to specified date regardless of load

## Rule 5: Mark After Processing

After EACH processed entry, add marker:

```markdown
<!-- ✓ processed: {category} -->
```

For tasks with details:
```markdown
<!-- ✓ processed: task → Todoist: {name} {priority} {date} -->
```

## Rule 6: Apply Decision Filters

Before saving any thought or task, check (from About User):

1. **Двигает к $3K/мес и Валенсии?** Нет → понизить приоритет или → ideas/someday
2. **Сколько активных проектов?** Если 3 → новый проект НЕ создаётся → ideas/someday
3. **Это 🔴/🟡/🟢?** Приоритет по светофору (см. goals-integration)
4. **Это импульс?** Если запись после 21:00 + новая идея → ⏳ пометить «вернуться утром», НЕ создавать задачу
5. **Можно на 80%?** Если да → пометить «правило 80%»

**Дополнительно (2+ да → повысить приоритет):**
- Усиливает BaZi-экспертизу или бренд?
- Приближает к запуску BaZi-сервиса?
- Создаёт кейс/отзыв для продаж?
- Приводит подписчиков?

## Rule 7: Avoid Anti-Patterns

NEVER create:
- Абстрактные задачи без конкретного действия ("Подумать о...", "Изучить тему...")
- Хаотичные списки без приоритетов
- Повторы без синтеза
- Теория без привязки к BaZi-бизнесу, контенту или доходу
- Новые проекты без проверки Decision Filters
- Задачи из вечерних импульсов (после 21:00) как срочные

**ALWAYS transform:**
- Outcome goals → Process goals (см. process-goals.md)
- "Надо сделать X" → конкретный первый шаг с датой и временем
- "Классная идея!" → записать в ideas/, проверить через 24 часа

See [ABOUT.md](ABOUT.md) → Anti-Patterns section.

## Rule 8: Detect Bug Patterns

When processing entries, watch for:

**🐓 Баг Петуха (перфекционизм):**
- Слова: "ещё не готово", "надо доделать", "не идеально", "переделать"
- Action: Мягко напомнить «Правило 80%. Можно выпустить сейчас?»

**🐷 Баг Свиньи (растекание):**
- Признаки: 4+ разных проектов/областей за день, новая идея каждые 2 часа
- Action: «Сегодня задачи из {N} разных областей. Фокус: 1–2 области в день.»

**🌙 Вечерний залип:**
- Записи после 21:00 с новыми идеями или желанием «ещё чуть-чуть доделать»
- Action: «Записал. Это может подождать до утра? Отбой до 23:00.»

**💸 Обесценивание:**
- Слова: "это все знают", "ничего нового", "кто я такой"
- Action: «Напоминание: то, что тебе кажется очевидным — для 95% людей откровение. Продолжай.»

---

## Checklist Before Completion

- [ ] All new entries processed
- [ ] No duplicates in Todoist
- [ ] All tasks have dates and concrete actions (process goals, not outcomes)
- [ ] Decision filters applied (5 вопросов)
- [ ] Traffic light checked (🔴🟡🟢)
- [ ] Anti-patterns avoided
- [ ] Bug patterns checked
- [ ] MOC files updated
- [ ] Report generated