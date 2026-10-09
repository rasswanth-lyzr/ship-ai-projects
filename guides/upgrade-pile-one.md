# Upgrade a pile-one project

You don't have to delete what you've built. Most pile-one projects are missing measurement and operations, not effort. Here's how to move each one into pile two.

## RAG chatbot over PDFs → evals + ops

Right now it shows you can wire up retrieval. Here's what to add:

1. **An eval set:** 150+ questions with reference answers **and the source page/chunk** for each. Include questions the documents *can't* answer; the correct behavior there is to say so.
2. **Separate metrics for retrieval and generation:** retrieval recall@k (did the right chunk come back?), answer correctness, and **faithfulness** (is every claim supported by the retrieved chunks?). Use the claim-level hallucination approach from [Project 02, M3](../projects/02-agent-evals/BRIEF.md#m3--hallucination-detection).
3. **Error analysis:** for each failure, decide whether retrieval or generation was at fault. That split tells you whether to fix chunking/embeddings or the prompt.
4. **One measured improvement**, e.g. hybrid search, re-ranking, or different chunking, with before/after numbers and CIs.
5. *(Optional)* Wrap it in the [Project 01](../projects/01-llm-ops/BRIEF.md) stack.

**New headline:** "Retrieval recall@5 went from XX% to XX% with hybrid search + re-ranking; unsupported-claim rate dropped from XX% to XX% on 150 questions."

## "I fine-tuned Llama on a dataset" → a measured fine-tune inside a router

A fine-tune only means something when it's compared with alternatives. Here's what to add:

1. **A held-out test set** the fine-tune never saw.
2. **Baselines:** the base model zero-shot, the base model few-shot, and a prompted frontier model. Compare quality, cost per 1k requests, and latency.
3. **Route between them** ([Project 03](../projects/03-auto-routing/BRIEF.md)): the fine-tune handles in-distribution requests cheaply and the frontier model handles the rest. Report the traffic share and what it saves.

**New headline:** "My fine-tuned 8B handles XX% of traffic at 1/XX the cost of <frontier model>, with total quality within X pts."

## LangChain wrapper around GPT-4 → a real service

Whatever the wrapper does, it already has a task. Here's what to add:

1. **Define correctness** for that task and build a 200-example golden set.
2. **Swap single-provider calls for a gateway** with fallback, and run at least two models through your eval.
3. Apply [Project 01](../projects/01-llm-ops/BRIEF.md) milestones M1–M4: versioned prompts, reliability, tracing, and an eval gate in CI.

**New headline:** "Eval-gated, multi-provider service; <model B> matched <model A> within X pts at XX% lower cost, so I switched, with a canary."

## Sentiment analysis notebook → classical vs LLM, deployed

Here's what to add:

1. **Three approaches on the same test set:** TF-IDF + logistic regression, a small fine-tuned encoder, and an LLM zero-shot. Compare accuracy, **cost per 1M predictions**, and latency.
2. **Deploy the winner** behind an API, with monitoring and an input-drift check.
3. **Write up when an LLM is the wrong tool.** That's a mature conclusion and reviewers notice it.

**New headline:** "A fine-tuned encoder matched GPT-class zero-shot accuracy (±X pts) at 1/XXX the cost per prediction. Deployed with drift monitoring."

## MNIST classifier → take it off the resume

It doesn't show anything relevant to AI engineering roles in 2026, and there's nothing worth upgrading it into. Use the space for one of the three projects.
