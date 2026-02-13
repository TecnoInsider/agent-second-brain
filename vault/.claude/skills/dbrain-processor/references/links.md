# Wiki-Links Building

## Purpose

Build connections between notes to create a knowledge graph.

## When Saving a Thought

### Step 1: Search for Related Notes

Search thoughts/ for related content:

```
Grep "keyword1" in thoughts/**/*.md
Grep "keyword2" in thoughts/**/*.md
```

Keywords to search:
- Main topic of the thought
- Key entities (people, projects, technologies)
- Domain terms (BaZi, расшифровка, бот, контент, Николаева, дашборд)

### Step 2: Check MOC Indexes

Read relevant MOC files:

```
MOC/
├── MOC-ideas.md
├── MOC-projects.md
├── MOC-learnings.md
└── MOC-reflections.md
```

Find related entries.

### Step 3: Link to Goals

Check if thought relates to goals:

```
Read goals/1-yearly-2026.md
Find matching goal areas
```

### Step 4: Add Links to Note

In the thought file, add:

**In frontmatter:**
```yaml
related:
  - "[[thoughts/ideas/2026-02-12-bazi-webinar-format.md]]"
  - "[[goals/1-yearly-2026#Career & Business]]"
```

**In content (inline):**
```markdown
This connects to [[BaZi Dashboard MVP]] we explored earlier.
```

**In Related section:**
```markdown
## Related
- [[Previous related thought]]
- [[Project this belongs to]]
- [[Goal this supports]]
```

### Step 5: Update MOC Index

Add new note to appropriate MOC:

```markdown
# MOC: Ideas

## Recent
- [[thoughts/ideas/2026-02-15-bazi-subscription-model.md]] — Модель подписки на BaZi-сервис

## By Topic
### BaZi & Распаковка
- [[thoughts/ideas/2026-02-15-bazi-subscription-model.md]]
- [[thoughts/ideas/2026-02-12-bazi-webinar-format.md]]

### AI & Инструменты
- [[thoughts/learnings/2026-02-13-notebooklm-presentations.md]]
- [[thoughts/ideas/2026-02-12-ai-bazi-video-idea.md]]

### Контент
- [[thoughts/ideas/2026-02-14-youtube-series-bazi.md]]
```

### Step 6: Add Backlinks

In related notes, add backlink to new note if highly relevant.

## Link Format

### Internal Links
```markdown
[[Note Name]]                    # Simple link
[[Note Name|Display Text]]       # With alias
[[folder/Note Name]]             # With path
[[Note Name#Section]]            # To heading
```

### Link to Goals
```markdown
[[goals/1-yearly-2026#Career & Business]]
[[goals/1-yearly-2026#Financial]]
[[goals/3-weekly]] — ONE Big Thing
[[goals/2-monthly]] — Top 3 Priorities
```

## Report Section

Track new links created:

```
<b>🔗 Новые связи:</b>
• [[Note A]] ↔ [[Note B]]
• [[New Thought]] → [[Related Project]]
```

## Example Workflow

New thought: "NotebookLM отлично делает презентации по BaZi-расшифровкам — можно использовать для платных консультаций"

1. **Search:**
   - Grep "NotebookLM" in thoughts/ → finds [[notebooklm-presentations]]
   - Grep "BaZi" in thoughts/ → finds [[bazi-webinar-format]], [[bazi-dashboard-mvp]]
   - Grep "консультаци" in thoughts/ → finds [[bazi-offer-draft]]

2. **Check MOC:**
   - MOC-learnings.md has section "AI & Инструменты"
   - MOC-ideas.md has section "BaZi & Распаковка"

3. **Goals:**
   - 1-yearly-2026.md → "BaZi-направление → $1K/мес" ✅ match
   - 2-monthly.md → Priority 2: "Заложить фундамент BaZi-бизнеса" ✅ match

4. **Create links:**
   ```yaml
   related:
     - "[[thoughts/learnings/2026-02-13-notebooklm-presentations.md]]"
     - "[[thoughts/ideas/2026-02-12-bazi-webinar-format.md]]"
     - "[[goals/1-yearly-2026#Career & Business]]"
   ```

5. **Update MOC-learnings.md:**
   ```markdown
   ### AI & Инструменты
   - [[thoughts/learnings/2026-02-15-notebooklm-bazi-consult.md]] — NotebookLM для платных BaZi-консультаций
   ```

6. **Report:**
   ```
   <b>🔗 Новые связи:</b>
   • [[NotebookLM BaZi Consult]] ↔ [[BaZi Webinar Format]]
   • [[NotebookLM BaZi Consult]] → [[Goal: BaZi-направление]]
   ```

## Orphan Detection

A note is "orphan" if:
- No incoming links from other notes
- No related notes in frontmatter
- Not listed in any MOC

Flag orphans for review:
```
<b>⚠️ Изолированные заметки:</b>
• [[thoughts/ideas/orphan-note.md]] — Связать или архивировать?
```