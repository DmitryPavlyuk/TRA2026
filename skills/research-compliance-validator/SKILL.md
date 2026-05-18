---
name: research-compliance-validator
description: >
  Validate research projects against GDPR, EU AI Act, and Responsible AI / ethics requirements.
  Use this skill whenever a user wants to check, audit, review, or validate their research project,
  files, documents, datasets, code, or notebooks for compliance, ethics, data protection, privacy,
  AI regulation, or responsible AI. Trigger on phrases like "validate my project", "check GDPR",
  "AI Act compliance", "ethics review", "responsible AI audit", "is my research compliant",
  "review my data practices", or any time research files are uploaded alongside compliance questions.
  Also trigger when the user mentions IRB, consent forms, personal data, data processing, model training
  data, bias, fairness, transparency, or EU regulation in a research context.
---

# Research Compliance Validator

A skill that audits research project files against **GDPR**, **EU AI Act**, and **Responsible AI / Ethics** requirements, then renders an interactive checklist widget in chat.

---

## Workflow

### Step 1 — Inventory files

Before reading anything, list what the user has provided:
- Uploaded files (`/mnt/user-data/uploads/`)
- File paths or descriptions mentioned in chat
- Project descriptions given as text

If no files are present, ask the user to share files or describe the project before proceeding.

### Step 2 — Read and analyse each file

Use the appropriate reading approach per file type:

| Type | How to read |
|---|---|
| `.pdf` | Use pdf-reading skill or `bash_tool` with `pdftotext` |
| `.docx` | Use `python-docx` via `bash_tool` |
| `.xlsx` / `.csv` | Use `pandas` via `bash_tool` — read headers, sample rows, check for PII columns |
| `.py` / `.R` / `.ipynb` | Read source directly; scan for data loading, model training, logging, external calls |
| `.txt` / `.md` | Read directly |

**What to look for per file type:**
- **Documents/papers**: data collection methods, consent mentions, data subjects, purpose limitation, retention policy, model descriptions, fairness/bias mentions, transparency statements
- **Datasets/spreadsheets**: column names suggesting PII (name, email, ID, location, health, age, gender, race, income), sample values, anonymisation indicators
- **Code**: hardcoded credentials or PII, data logging, model training on personal data, automated decision-making, lack of explainability hooks, external API calls with data
- **Consent/survey forms**: what is disclosed, opt-out mechanisms, data subject rights, purpose clarity

### Step 3 — Score against the three frameworks

Evaluate findings against the reference files. Load them as needed:
- `references/gdpr.md` — GDPR checklist (Articles 5, 6, 7, 9, 13, 17, 25, 30, 35)
- `references/ai-act.md` — EU AI Act checklist (risk tiers, transparency, human oversight, data governance)
- `references/responsible-ai.md` — Responsible AI / Ethics checklist (fairness, accountability, transparency, explainability, privacy, safety, inclusivity)

For each checklist item assign one of:
- ✅ **Pass** — evidence found in project files
- ⚠️ **Partial** — some evidence but gaps remain
- ❌ **Fail** — no evidence or clear violation found
- ➖ **N/A** — not applicable to this project type

### Step 4 — Render the interactive checklist widget

Call `show_widget` with an HTML interactive checklist. See **Widget Spec** below.

---

## Widget Spec

Build a single self-contained HTML widget (no external dependencies except optional CDN fonts).

### Layout

```
┌─────────────────────────────────────────────┐
│  🔬 Research Compliance Audit               │
│  [project name / files scanned]             │
│  Overall score: ██████░░ 67%                │
├─────────────────────────────────────────────┤
│  [GDPR] [AI Act] [Responsible AI]  tabs     │
├─────────────────────────────────────────────┤
│  ✅ Item label          [Finding detail ▼]  │
│  ⚠️  Item label          [Finding detail ▼]  │
│  ❌ Item label          [Finding detail ▼]  │
├─────────────────────────────────────────────┤
│  📋 Key Actions Needed (auto-generated)     │
│  1. ...                                     │
│  2. ...                                     │
└─────────────────────────────────────────────┘
```

### Interactivity requirements
- **Tabs** for each framework (GDPR / AI Act / Responsible AI) — show only relevant section
- **Expandable rows** — click any checklist item to expand a panel showing the specific finding from the user's files and a recommended fix
- **Progress bar** per tab showing pass rate
- **Overall score** at the top (weighted: Responsible AI 40%, GDPR 35%, AI Act 25%)
- **"Key Actions" section** at the bottom listing only ❌ Fail and ⚠️ Partial items as numbered action points
- **Print / Export button** that triggers `window.print()` so the user can save as PDF
- Use CSS variables for theming; respect light/dark backgrounds

### Widget style notes
- Clean, professional — suitable for academic or institutional review
- Status colours: green (#22c55e) for ✅, amber (#f59e0b) for ⚠️, red (#ef4444) for ❌, grey for ➖
- Monospace font for file names and code snippets in finding panels
- Keep widget height bounded with scroll on the checklist area

---

## Output format

After the widget, add a **brief prose summary** (3–5 sentences) covering:
1. Overall compliance posture
2. The single most critical issue found
3. One concrete next step

Do NOT produce a long bulleted report — the widget is the primary output.

---

## Edge cases

- **No files, only a description**: Run the audit on the description text alone; mark most items ⚠️ Partial with note "Unable to verify — no files provided"
- **Large dataset files**: Do not read entire file; sample first 100 rows + column headers only
- **Encrypted or unreadable files**: Note in widget as "File could not be read" and mark as ➖ N/A
- **Non-EU research**: Note that GDPR and AI Act are EU-specific but still highlight best-practice gaps under Responsible AI
- **Multiple projects in one session**: Produce one widget per project; do not merge findings

---

## Important notes

- You are not providing legal advice. Always add a disclaimer: *"This audit is for informational purposes only and does not constitute legal or regulatory advice. Consult a qualified professional for formal compliance assessment."*
- Be specific: always quote or reference the actual file and line/section where evidence was or wasn't found
- Be constructive: for every ❌ Fail, suggest a concrete remediation step
