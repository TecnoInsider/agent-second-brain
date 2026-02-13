# Goals Integration

## ALWAYS Do First

Before processing daily entries:

1. **Read current focus:**
   ```
   Read goals/3-weekly.md → Extract ONE Big Thing
   ```

2. **Read yearly goals:**
   ```
   Read goals/1-yearly-2026.md → Know active goals by area
   ```

3. **Check monthly priorities:**
   ```
   Read goals/2-monthly.md → Top 3 priorities + правило светофора (🔴🟡🟢)
   ```

## Goal Alignment

When creating a task, ask:

1. **Does it connect to ONE Big Thing?**
   - Yes → add to task description: `→ Weekly focus`
   - No → continue checking

2. **Does it connect to monthly priority?**
   - Yes → add: `→ Monthly: [Priority name]`
   - No → continue checking

3. **Does it connect to yearly goal?**
   - Yes → add: `→ Goal: [Goal name]`
   - No → mark as "operational"

4. **Does it pass Decision Filters?** (from About User)
   - Двигает к $3K/мес и Валенсии?
   - Проектов < 3?
   - Это 🔴/🟡/🟢?
   - Импульс или стратегия? (если после 21:00 → ⏳ вернуться утром)

## Task Priority — Светофор + Goals

| Alignment | Default | Boost to | Color |
|-----------|---------|----------|-------|
| 🔴 Николаева / долги | p1-p2 | p1-p2 | Красный |
| 🟡 Жёлтый проект (добить) | p2-p3 | p2 if aligned with weekly | Жёлтый |
| ONE Big Thing | p3 | p2 | — |
| Monthly priority | p3 | p2-p3 | — |
| 🟢 BaZi/контент/обучение | p3-p4 | p3 if aligned with yearly | Зелёный |
| Yearly goal | p4 | p3 | — |
| No alignment | p4 | p4 | — |
| ⛔ Новый проект (4-й+) | — | REJECT → ideas/someday | Стоп |

## Saving Thoughts

When saving to thoughts/:

1. **Check goal relevance:**
   - Scan goals/1-yearly-2026.md for matching areas
   - If matches → add link in frontmatter:
     ```yaml
     related:
       - "[[goals/1-yearly-2026#Career & Business]]"
     ```

2. **Tag with goal area:**
   ```
   #goal/bazi-business
   #goal/content
   #goal/financial
   #goal/health
   #goal/relationships
   #goal/growth
   ```

## Goal Progress Tracking

Track goal activity by:

- Task created → goal is "active"
- Thought saved → goal is "active"
- No activity 7+ days → "stale"
- No activity 14+ days → "warning" ⚠️

**Special tracking for Vadim's bugs:**
- If 4+ different #goal/ tags in one day → ⚠️ «Растекание! Сегодня задачи из 4+ разных целей. Правило: фокус на 1–2 области в день.»
- If new project idea appears → check: «Сейчас активно 3 проекта. Записываю в ideas/someday. Вернёшься когда один из текущих закрыт.»

## Report Section

Add to report:

```
<b>📈 Прогресс по целям:</b>
{for each active yearly goal with recent activity:}
• {goal}: {progress}% {status_emoji}

<b>🚦 Светофор проектов:</b>
🔴 {red project}: {status}
🟡 {yellow project}: {status}
🟢 {green projects}: {status}

{if stale goals:}
<b>⚠️ Требует внимания:</b>
• Цель "{goal}" без активности {days} дней

{if bug patterns detected:}
<b>🐛 Паттерн замечен:</b>
• {pattern description and gentle reminder}
```

## Goal File Parsing

### 3-weekly.md — Find ONE Big Thing

Look for pattern:
```markdown
> **If I accomplish nothing else, I will:**
> [THE ONE THING]
```

### 1-yearly-2026.md — Find Active Goals

Look for table:
```markdown
## Progress Dashboard

| Area | Goal | Progress | Status |
|------|------|----------|--------|
| Career | BaZi-направление → $1K/мес | X% | 🔵/🟡/🟢 |
```

### 2-monthly.md — Find Top 3 + Traffic Light

Look for sections:
```markdown
## 🚦 Правило Светофора
🔴 **Красный — основной доход:** ...
🟡 **Жёлтый — проект на финишной прямой:** ...
🟢 **Зелёный — будущее:** ...
⛔ **Стоп — всё новое:** ...

## Top 3 Priorities
### 🟡 Priority 1: [name]
### 🟢 Priority 2: [name]
### 🔴 Priority 3: [name]
```

## Example Alignment

Entry: "Нужно добить демо-режим в калорий-боте"

Check:
- ONE Big Thing: "2 сессии калорий-бота" → ✅ Direct match
- Monthly #1: "Добить и закрыть калорий-бот" → ✅ Related
- Yearly: "BaZi-направление" → Indirect (закрытие бота освобождает время)
- Traffic Light: 🟡 Жёлтый проект

Result:
```
Task: Добить демо-режим в калорий-боте
Description: → Weekly focus → Monthly: Добить калорий-бот
Priority: p2 (boosted: ONE Big Thing + жёлтый проект)
```

---

Entry: "О, классная идея — сделать Telegram-бот для подбора диет по BaZi!"

Check:
- ONE Big Thing: "калорий-бот" → ❌ Not related
- Monthly priorities → ❌ Not in top 3
- Decision Filter: Сколько проектов активно? → 3 (Николаева, калорий-бот, BaZi-обучение)
- Time: 22:30 → ⚠️ Вечерний импульс

Result:
```
💡 Записал идею в thoughts/ideas/2026-02-12-bazi-diet-bot.md
⛔ Новый проект НЕ создан — уже 3 активных.
⏳ Вернёшься к этой идее когда калорий-бот закрыт.
Правило: «Загорелся → записал → подождал 24 часа → проверил через фильтры»
```