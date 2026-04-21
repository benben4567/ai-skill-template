# AI Skill Template

Rules and task brief templates for AI coding assistants.

---

## Structure

```
skills/
  laravel.md       ← standalone skill for Laravel projects
  universal.md     ← standalone skill for non-Laravel stacks
  _new-stack.md    ← scaffold: copy this to add a new stack
context/
  task-brief.md    ← fill per task
README.md
```

---

## How to Use

Copy relevant files into your project's `.ai/` folder:

### Laravel project
```
.ai/
  SKILL.md     ← copy from skills/laravel.md
  CONTEXT.md   ← copy from context/task-brief.md (fill per task)
```

### Other stack
```
.ai/
  SKILL.md     ← copy from skills/universal.md
  CONTEXT.md   ← copy from context/task-brief.md (fill per task)
```

Then paste both files at the start of your AI session.

---

## Adding a New Stack

1. Copy `skills/_new-stack.md` → `skills/{stack}.md`
2. Fill in all `<!-- ... -->` placeholders and stack-specific sections
3. Make it standalone — do not depend on universal.md
