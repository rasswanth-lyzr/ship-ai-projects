# The 90-second scan

A reviewer (recruiter, hiring manager, or the engineer who screens take-homes) gives your repo about a minute and a half. This is roughly what they look at, in order. Build your README to match it.

| Time | They look at | What should be there |
|---|---|---|
| 0–10 s | Repo name, description, first screen of the README | One sentence on what it does, **one headline number with a baseline**, and a diagram or hero chart |
| 10–40 s | Results table | Numbers with baselines, sample sizes, and CIs, plus a link to how they were measured |
| 40–70 s | "What broke" and "Key decisions" | Real failures you hit, and tradeoffs you made deliberately |
| 70–90 s | The code | Clear layout, tests, a passing CI badge, a commit history that shows the work |

If the first screen doesn't show a number, most reviewers won't scroll down to find one.

## Ship checklist

Go through this before you post the link anywhere.

### README
- [ ] The first screen has a one-line description, a headline number **with a baseline**, and a diagram or chart
- [ ] Every number has a sample size and a pointer to how it was measured
- [ ] A "What broke" section with at least 2 real stories
- [ ] A "Key decisions" table with alternatives you considered
- [ ] A "Limitations and next steps" section. Honesty here reads as seniority
- [ ] No placeholder text (`XX`, `<...>`, `TODO`) left over from the template

### Reproducibility
- [ ] `git clone` → `cp .env.example .env` → **one command** runs a demo
- [ ] Pinned dependencies (`uv.lock`, `poetry.lock`, or `requirements.txt` with versions)
- [ ] Results regenerate from a script, not from a notebook cell someone has to find
- [ ] Datasets are committed (if small and licensed), or there's a download script plus the license noted

### Code
- [ ] Clear layout (`app/`, `evals/`, `ops/`, `routers/`, ...). No 900-line `main.py`
- [ ] Tests for the logic you own: graders, router decision, retry policy
- [ ] CI runs on push, and the badge is green
- [ ] **No secrets in git history.** Run [`gitleaks`](https://github.com/gitleaks/gitleaks) (`gitleaks detect`) before making the repo public

### Proof
- [ ] A 2-minute screen recording of the most interesting moment (failover drill, a failure going through the fix loop, routing demo)
- [ ] Links to concrete evidence: a blocked PR, a trace, a postmortem, a run report

### Repo hygiene
- [ ] Repo description and topics set on GitHub (e.g. `llmops`, `evals`, `llm-routing`)
- [ ] A commit history that shows iteration. A single "initial commit" with 8,000 lines looks copied
- [ ] Pinned on your GitHub profile

## README anti-patterns

- **The badge wall.** Twelve shields.io badges and no numbers.
- **The feature list.** "Supports OpenAI, Anthropic, Gemini, Mistral, ..." describes the library you used, not the work you did.
- **The tutorial.** Three screens explaining what RAG is. The reviewer already knows.
- **The screenshot-only README.** A UI screenshot with no measurements.
- **Unqualified superlatives.** "Blazing fast", "highly accurate", "production-ready" with no numbers next to them.
