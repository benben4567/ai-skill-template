# SKILL — [Stack Name] AI Coding Assistant (Standalone)

Working contract for any AI assistant contributing code to a [Stack Name] repository.
Goals: follow [stack] conventions, keep solutions simple & maintainable, be production-ready, pass tests, update README when needed.

---

## 0) Core Principles
- **[Stack] conventions first:** prefer framework conventions over custom patterns.
- **Simple over clever:** avoid overengineering; keep changes minimal and consistent.
- **Context-first:** inspect repo structure and configuration before proposing solutions.
- **Verified:** work is "done" only when **tests pass**.
- **Docs:** update README sections whenever install/run/config changes.

---

## 1) Non-Negotiable Constraints
- **Forbidden:** `git commit`, `push`, `merge`, PR creation, history rewriting.
- **Forbidden:** inventing requirements, tables, endpoints, flows, or files not explicitly requested.
- **Forbidden:** adding new packages without explicit approval.
- **No secrets:** never output real secret/key values. Use placeholders + instructions.
- **No destructive commands** without explicit approval (see Section 6).

---

## 2) Required Working Method

### Step A — Repo Recon
Before coding, the AI must:
1) Identify [stack] version, app type, auth approach.
2) Inspect repo conventions (folders, naming, existing patterns).
3) Detect tooling: test runner, linter/formatter, CI steps.

**Required short output (single block):**
- [Stack] version & app type:
- Auth/Authorization approach:
- Tooling detected (tests/format/lint):
- Areas/files likely touched:

### Step B — Plan (actionable)
Include:
- Requirement summary (bullets)
- Files to be created vs edited
- DB impact (if any)
- API/UI impact (if any)
- Authorization strategy
- Test plan (what tests will be added)
- README impact (what sections change)

### Step C — Implement (adjust order to stack conventions)
Default order:
1) Data layer (schema/model)
2) Authorization/permissions
3) Business logic
4) Interface (API/UI/CLI)
5) Tests
6) README updates

### Step D — Verify
Run tests and relevant tooling, report pass/fail.

---

## 3) Code Style (Required)
- Follow the official style guide for this stack/language.
- Do not introduce inconsistent naming conventions.
- Use typing where it improves clarity; avoid excessive abstraction.

---

## 4) General Best Practices
- Avoid duplicated logic; refactor only when it improves maintainability.
- Keep error handling consistent with repo patterns.
- Log only where meaningful (error paths / audits); avoid noisy logs.
- Find existing patterns for similar features before writing new ones.

---

## 5) [Stack]-Specific Best Practices
<!-- Fill in stack-specific rules here -->
- Validation: [preferred approach]
- Authorization: [preferred approach]
- [Other patterns specific to this stack]

---

## 6) Command Execution Policy
### Allowed (generally safe)
- Install deps: `[install command]`
- Build/lint/test: `[test command]`, `[lint command]`
- Other safe commands: ...

### Forbidden unless explicitly approved (destructive/risky)
- DB resets / data wipes
- Mass deletions
- Anything that modifies production data

If a forbidden command is needed: stop and request explicit approval.

---

## 7) Test Runner Detection
Detect correct test runner in this order:
1) Inspect config files: `[relevant config files]`
2) Inspect common folders: `tests/`, `.github/workflows/`
3) Choose the most "official" test command (prefer repo scripts)

---

## 8) Anti-Overkill Guardrails (Required)
Do NOT introduce:
- Large new architecture not already used.
- Extra abstraction layers for simple cases.
- Extra packages without approval.

When in doubt: choose the simplest approach.

---

## 9) Definition of Done (DoD)
A task is done when:
- ✅ Acceptance criteria met
- ✅ Tests pass
- ✅ Consistent with repo conventions
- ✅ No new dependencies without approval
- ✅ README updated if install/run/config changed

---

## 10) README Update Policy (Required)
If changes affect running/config/deps, update README with all relevant sections:
- Overview, Requirements, Installation, Local Development, Testing, Configuration, Troubleshooting

If not impacted: output `README: no changes required`.

---

## 11) Assumptions Policy (Always Required)
Always include an Assumptions section:
- If none: `Assumptions: none`
- If ambiguous: list numbered assumptions and request confirmation before major changes.

---

## 12) Required Output Format After Implementation
Close with:
1) Change summary (bullets)
2) Files created/changed
3) Verification commands executed (and brief results)
4) Assumptions (always; at minimum `none`)
5) Risks/impact (if any)
6) README update (what changed, or `no changes required`)
