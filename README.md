# AI Skill Template

Rules and task brief templates for AI coding assistants.

---

## Files

| File | Purpose |
|------|---------|
| `universal.md` | Base rules for all stacks (anti-hallucination, working method, DoD, output format) |
| `laravel.md` | Laravel-specific rules — extends universal.md (PSR, Artisan, Pest, migrations, authz) |
| `task-brief.md` | Task brief template — fill per task, paste alongside skill files |

---

## How to Use

### Laravel project
Paste both files at session start:
```
[universal.md content]
[laravel.md content]
[filled task-brief.md]
```

### Other stack
Paste only universal + task brief:
```
[universal.md content]
[filled task-brief.md]
```

---

## Adding a New Stack

1. Copy `laravel.md` as starting point
2. Replace Laravel-specific sections (Artisan, PSR, Pest) with stack equivalents
3. Reference in `task-brief.md` constraints section
