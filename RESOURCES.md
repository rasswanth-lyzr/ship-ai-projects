# Resources

A short, curated list. Every link was checked when this repo was published. If one breaks, open an issue.

## Start here (one read per project)

- **LLM Ops:** Chip Huyen, [Building A Generative AI Platform](https://huyenchip.com/2024/07/25/genai-platform.html). The full production stack: gateway, guardrails, caching, observability.
- **Agent Evals:** Hamel Husain, [Your AI Product Needs Evals](https://hamel.dev/blog/posts/evals/), then the [LLM Evals FAQ](https://hamel.dev/blog/posts/evals-faq/) (with Shreya Shankar).
- **Auto Routing:** LMSYS, [RouteLLM: An Open-Source Framework for Cost-Effective LLM Routing](https://www.lmsys.org/blog/2024-07-01-routellm/).

## General

- Anthropic, [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents): workflows vs agents, and why simple wins.
- Eugene Yan, [Patterns for Building LLM-based Systems & Products](https://eugeneyan.com/writing/llm-patterns/): evals, caching, guardrails, feedback loops.

## LLM Ops

- [OpenTelemetry GenAI semantic conventions](https://github.com/open-telemetry/semantic-conventions-genai): the standard `gen_ai.*` span and metric attributes. Still in *Development* status, so pin a version.
- Google SRE, [Service Level Objectives](https://sre.google/sre-book/service-level-objectives/) and [Alerting on SLOs](https://sre.google/workbook/alerting-on-slos/) (burn-rate alerts).
- [LiteLLM](https://github.com/BerriAI/litellm): OpenAI-compatible gateway/SDK over 100+ providers, with retries, fallbacks, and budgets.
- [Langfuse](https://langfuse.com/docs): open-source tracing, prompt management, datasets, evals.
- [Arize Phoenix](https://github.com/Arize-ai/phoenix): OpenTelemetry-native tracing and evals.
- [vLLM](https://docs.vllm.ai/): high-throughput serving with an OpenAI-compatible server and Prometheus metrics.
- [k6](https://grafana.com/docs/k6/latest/): load testing.
- [promptfoo](https://github.com/promptfoo/promptfoo): eval and red-team runner that plugs into CI.
- [gitleaks](https://github.com/gitleaks/gitleaks): scans git history for secrets before you make a repo public.

## Agent Evals

**How-to**
- Hamel Husain, [Using LLM-as-a-Judge For Evaluation](https://hamel.dev/blog/posts/llm-judge/): build a judge, then validate it against human labels.
- Anthropic, [Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents).

**Papers**
- Yao et al., [τ-bench](https://arxiv.org/abs/2406.12045): tool-agent-user benchmark that introduced **pass^k**. Follow-up: [τ²-bench](https://arxiv.org/abs/2506.07982) ([code](https://github.com/sierra-research/tau2-bench)).
- Shankar et al., [Who Validates the Validators?](https://arxiv.org/abs/2404.12272): aligning LLM judges with human preferences.
- Min et al., [FActScore](https://arxiv.org/abs/2305.14251): atomic-claim factuality scoring, the basis for claim-level hallucination checks.
- Zhu et al., [Establishing Best Practices for Building Rigorous Agentic Benchmarks](https://arxiv.org/abs/2507.02825): how benchmarks get task and grader validity wrong.
- [Towards a Science of AI Agent Reliability](https://arxiv.org/abs/2602.16666): measuring consistency, not just one-shot success.

**Tools**
- [Inspect AI](https://inspect.aisi.org.uk/): eval framework from the UK AI Security Institute.
- [DeepEval](https://github.com/confident-ai/deepeval): pytest-style LLM and agent metrics.
- [DSPy](https://dspy.ai/): programmatic prompt optimization (MIPROv2, GEPA).
- [Berkeley Function Calling Leaderboard](https://gorilla.cs.berkeley.edu/leaderboard.html): function-calling accuracy reference.

## Auto Routing

**Papers**
- Ong et al., [RouteLLM](https://arxiv.org/abs/2406.18665) ([code](https://github.com/lm-sys/RouteLLM)): preference-data routers and the APGR metric.
- Hu et al., [RouterBench](https://arxiv.org/abs/2403.12031) ([dataset](https://huggingface.co/datasets/withmartian/routerbench)): 405k+ precomputed outputs from 11 models.
- [LLMRouterBench](https://arxiv.org/abs/2601.07206) (2026): 400k+ instances, 21 datasets, 33 models, 10 baseline routers.
- [RouterArena](https://arxiv.org/abs/2510.00202) (ICLR 2026): open platform for comparing routers.
- Li, [When Simple kNN Beats Complex Learned Routers](https://arxiv.org/abs/2505.12601). Read this before building anything fancy.
- Lee, [Most of the LLM Routing Gap Is Task Type](https://arxiv.org/abs/2608.23023) (2026): static per-task-type tables, and how run-to-run noise compares with routing gains.
- Chen et al., [FrugalGPT](https://arxiv.org/abs/2305.05176): LLM cascades.
- [Dynamic Model Routing and Cascading for Efficient LLM Inference: A Survey](https://arxiv.org/abs/2603.04445) (2026).

**Code**
- [LLMRouter](https://github.com/ulab-uiuc/LLMRouter): open-source library implementing many routing methods.
- [Awesome-Routing-LLMs](https://github.com/MilkThink-Lab/Awesome-Routing-LLMs): a running list of routing papers.

## Datasets

| Dataset | Use it for |
|---|---|
| [Bitext customer support](https://huggingface.co/datasets/bitext/Bitext-customer-support-llm-chatbot-training-dataset) | 01 ticket triage |
| [CORD v2 receipts](https://huggingface.co/datasets/naver-clova-ix/cord-v2) | 01 document extraction |
| [Chinook database](https://github.com/lerocha/chinook-database) | 02 analytics agent |
| [BIRD text-to-SQL](https://bird-bench.github.io/) | 02 analytics agent (harder) |
| [SEC EDGAR full-text search](https://www.sec.gov/edgar/search/) | 02 research agent corpus |
| [GSM8K](https://huggingface.co/datasets/openai/gsm8k) | 03 math prompts |
| [MBPP](https://huggingface.co/datasets/google-research-datasets/mbpp) | 03 code prompts (unit-test graded) |
| [MMLU-Pro](https://huggingface.co/datasets/TIGER-Lab/MMLU-Pro) | 03 knowledge and reasoning prompts |

Check each dataset's license before you redistribute any of it in your repo.
