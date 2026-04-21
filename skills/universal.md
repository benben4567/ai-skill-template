# SKILL — Universal AI Coding Assistant (Project-Scoped Rules)

This document is a working contract for any AI assistant contributing code to this repository.
Goals: avoid hallucinated context, follow best practices, stay simple & maintainable, be production-ready, pass tests, and update README docs when needed.

---

## 0) Core Principles
- **Context-first:** the AI must inspect the repo structure and configuration before proposing solutions.
- **Simple over clever:** the simplest solution that meets requirements wins.
- **Production-ready:** include baseline validation, authorization, and error handling; cover key edge cases.
- **Verified:** work is only “done” when **tests pass** and verification steps are clearly stated.
- **Docs:** changes that affect running/configuration must be reflected in README (all relevant sections).

---

## 1) Non-Negotiable Constraints
- **Forbidden:** `git commit`, `push`, `merge`, creating PRs, or rewriting git history.
- **Forbidden:** inventing requirements, tables, endpoints, flows, or files that are not explicitly requested or present in the repo.
- **Forbidden:** adding new packages/dependencies without explicit approval.
- **Forbidden:** running destructive commands without explicit approval (see Section 6).
- **No secrets:** never output real key/secret values. Use placeholders + instructions.

---

## 2) Required Working Method
### Step A — Repo Recon (anti-hallucination)
Before coding, the AI must:
1) Identify the actual stack (framework, language, test runner, linter/formatter).
2) Follow existing repo conventions: naming, folder structure, and architecture patterns.
3) Find existing patterns for similar features.

**Required short output (single block):**
- Detected stack:
- Key repo conventions:
- Areas/files likely touched:

### Step B — Plan (concise, actionable)
The AI must produce a plan including:
- Requirement summary (bullets).
- Files to create/modify.
- DB impact (if any).
- API/UI impact (if any).
- Key edge/error cases.
- Test plan (what tests will be added/updated).

### Step C — Implement incrementally
Default order (adjust to repo conventions):
1) data layer (schema/model)
2) authz/policy/permissions
3) business logic
4) interface (API/UI/CLI)
5) tests
6) docs (README)

### Step D — Verify (run tests)
The AI **may run local commands** for verification, provided:
- they are non-destructive
- they match the repo’s stack
- results are reported briefly (pass/fail + commands run)

---

## 3) Default Best Practices (cross-project)
- Follow the official style guide for the language/framework (e.g., PHP PSR-12, JS/TS lint rules, etc.).
- Use typing where it improves clarity, but avoid overengineering.
- Avoid duplicated logic; refactor only when it improves maintainability.
- Keep error handling consistent with repo patterns.
- Log only where meaningful (error paths / audits), avoid noisy logs.

---

## 4) Laravel Repos
If this is a Laravel repo, also load **laravel.md** — it overrides and extends this file for all Laravel-specific rules (PSR, Artisan, test commands, authorization, etc.).

---

## 5) Anti-Overkill Guardrails (Required)
The AI must NOT introduce:
- large architectural patterns not already present (DDD/CQRS/event-driven),
- extra abstraction layers (repository/DTO) for simple problems,
- custom “mini frameworks”,
unless:
1) it already exists as a repo convention, or
2) there is a strong reason and explicit approval.

When in doubt: choose the most straightforward solution.

---

## 6) Command Execution Policy (Local Runs Allowed)
### Allowed (generally safe)
- Install deps:
  - `composer install`
  - `npm install` / `pnpm install` / `yarn`
- Build/lint/test:
  - `composer test` / `vendor/bin/pest` / `vendor/bin/phpunit`
  - `php artisan pint` (if present)
  - `npm test` / `npm run lint` / `npm run build`
- Laravel non-destructive:
  - `php artisan config:clear`, `route:clear`, `cache:clear`
  - `php artisan migrate` (only for safe new migrations)

### Forbidden unless explicitly approved (destructive / risky)
- `php artisan migrate:fresh`
- `php artisan db:wipe`
- `php artisan migrate:refresh`
- Mass deletions, DB resets, large seeding runs
- Any scripts that modify production data or sensitive environments

If a forbidden command is needed:
- stop and request explicit approval.

---

## 7) Test Runner Detection (when not Laravel / unclear)
The AI must detect the correct test runner before running tests, in this order:
1) inspect config files:
   - PHP: `composer.json` (scripts), `phpunit.xml`, `pest.php`
   - JS: `package.json` (test/lint/build scripts)
   - Python: `pyproject.toml`, `pytest.ini`, `requirements.txt`
2) inspect common folders: `tests/`, `.github/workflows/`, `.gitlab-ci.yml`
3) choose the most “official” test command (prefer repo scripts)

Rules:
- If `composer test` exists → use it.
- If CI config exists → follow CI steps for tests.

---

## 8) Definition of Done (DoD)
A task is done when:
- ✅ meets acceptance criteria
- ✅ test suite passes
- ✅ respects repo conventions
- ✅ does not add dependencies without approval
- ✅ README is updated if execution/config changed

---

## 9) README Update Policy (Required)
If changes affect running, configuration, or dependencies:
- Update README with **all relevant sections**:
  - brief project overview
  - requirements
  - installation
  - local development
  - testing
  - configuration / env vars (no secret values)
  - troubleshooting (if needed)

If not impacted: still output `README: no changes required`.

---

## 10) Assumptions Policy (Always Required)
The AI **must always include an Assumptions section** in every output.
- If none: write `Assumptions: none`.
- If ambiguity exists: list numbered assumptions and request confirmation before major changes.

---

## 11) Required Output Format After Implementation
The AI must close with:
1) **Change summary** (bullets)
2) **Files changed/added**
3) **Verification commands** executed (and brief results)
4) **Assumptions** (always; at minimum `none`)
5) **Risks/impact** (if any)
6) **README update** (what changed, or `no changes required`)
