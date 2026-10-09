# Resume, interview, and posting

## Resume bullets

**Formula:** *Built [system] that [does what]* → *measured on [what, how much data]* → *[result vs baseline]*.

Put the project at the top of your Projects section with 2–3 bullets and a repo link. Fill in **your real numbers**. Interviewers will ask how you measured every one of them.

### Before / after

| Pile one | Pile two |
|---|---|
| "Built a chatbot using LangChain and GPT-4" | "Built a support-triage LLM service with an eval gate in CI that blocked X regressions; held p95 latency at X.X s at X RPS and cut cost/request XX% through prompt caching" |
| "Implemented evaluation for an AI agent" | "Built an eval system for a tool-using agent (XX tasks, n=4 trials each); validated the hallucination judge against XX human labels (κ = 0.XX); raised holdout success from XX% to XX% over 3 gated iterations" |
| "Created an LLM router" | "Built a kNN-based LLM router over 4 models; kept XX% of frontier-model quality at XX% of the cost on XX held-out prompts, beating a static per-task baseline by X pts" |

### Templates (replace every XX)

**01 LLM Ops**
- Deployed a <task> LLM service (FastAPI, LiteLLM, OpenTelemetry, Prometheus/Grafana) with versioned prompts, multi-provider failover, and canary rollouts. XX.X% availability, p95 X.X s at X RPS.
- Added an eval gate to CI (XX-example golden set) that blocks merges on > X pt accuracy or > XX% cost/latency regression. It caught X bad changes before production.
- Reduced cost per 1k requests from $X.XX to $X.XX via <change>, with no measurable accuracy change.

**02 Agent Evals**
- Built a tool-using <domain> agent and an eval harness with state, trajectory, and policy graders plus claim-level hallucination detection over XX tasks × 4 trials.
- Validated LLM judges against XX hand labels (TPR 0.XX / TNR 0.XX / κ 0.XX). Built a failure taxonomy from XX failed traces.
- Ran a failure → dataset → fix loop gated on a frozen holdout. Success went from XX% to XX% (p < 0.05) and hallucination rate from XX% to XX%, with no category regressing.

**03 Auto Routing**
- Built a routing matrix (XX prompts × M models × 2 runs, X task types) and kNN and learned routers that predict per-model success.
- At ≥ 98% of always-best quality, cut cost XX%. Beat the static per-task-type baseline by X pts at equal cost and closed XX% of the oracle gap.
- Served it as an OpenAI-compatible `model="auto"` endpoint with fallback, decision logging, and shadow-evaluated retraining. Adds XX ms at p95.

## The 2-minute interview walkthrough

When they say "tell me about this project", use this structure and practice it out loud:

1. **Problem (15 s).** What the system does and why it's hard to get right.
2. **System (20 s).** One sentence per component. Draw the diagram if there's a whiteboard.
3. **How you measured (25 s).** Dataset, graders, baselines, noise floor. **This is the part that separates pile one from pile two.**
4. **The most interesting failure (30 s).** What broke, how you found it, and what you changed.
5. **A tradeoff (15 s).** "I chose X over Y because Z, and here's what it cost me."
6. **What's next (15 s).** The honest limitation and how you'd fix it.

Each brief ends with the interview questions you're likely to get for that project. Answer them out loud before the interview, not for the first time in it.

## Posting it (LinkedIn / X template)

```
I built <project> to answer one question: <the question, e.g. "how often is my agent actually wrong?">

What I measured:
• <headline number vs baseline>
• <second number>
• <the surprising finding>

What broke: <one-line failure story>

The part I'd do differently: <honest lesson>

Repo (with how to reproduce every number): <link>
```

Tag [@skiptheline.ai](https://www.instagram.com/skiptheline.ai/) if you build one of these. I'd like to see it.
