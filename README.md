# CISC-451-Individual-Project

Potential Proposals:

## Extending CoDial (lowest risk, lab already owns the moving parts: schema -> heterogeneous graph -> Colang, CoDial_free/structured, human-feedback loop, ACL 2026):
    - Feedback-loop scaling: LLM-as-critic vs human corrections, measured as a cost-to-accuracy curve across 3 domains. Question: how many corrections to reach CoDial_structured quality, and where does the curve flatten? Cheap, uses the existing harness, publishes as a short paper.
    - Unseen-schema transfer + disambiguation: hold out an entire domain, feed it a new schema cold, and add a clarifying-question stage when a user request maps to 2+ flows. This is the multi-domain legal intake gap, and "new tasks" is literally the ask.
    - Generator faithfulness: does the LLM writing the Colang actually condition on graph structure, or is it pattern-matching schema strings? Perturb edges, permute node labels, ablate prompt sections, measure behavior drift.
**CoDial for agents: retarget from dialogue schemas to tool/API schemas, i.e. Colang guardrails for tool-calling.**
    - Dr. Tian says this idea is safest
    - Benchmarking CoDial like a LLM, check for issues
    - Make it better/extend it, or make benchmark more robust
    - We really need to read dthis paper... lol...
    - Changing standalone LLM to Agent is alraedy a contribution, we can get more
    - Most people are doing benchmarking (even in class)
        - e.g. agentic workflow in github analysis, extending text-to-sql for agents/data agents, collecting new data/analyzing data, using agents for encoding, labelling, automatic analysis, new insights, multimodality extensions, long horizon extensions, reasoning & explainability, reducing hallucinations
        - take inspiration from papers already presented

## Pretraining-side:
    - Seed-variance-aware speedrun ablation: take a few nanoGPT speedrun optimizations and re-run with n>=5 seeds at fixed budget, report effect sizes with CIs. My guess is a chunk of the "gains" are noise, and proving that is a real contribution you can finish on one GPU.
    - One-variable scale test (tokenizer, or dedup ratio, or data order) at ~10M params, 3 seeds. Question: does the effect survive small scale, or is it a big-model artifact?
    - Depth-recurrent vs deep at matched FLOPs: best pretraining cred, worst compute risk. Only if you have a real GPU budget.
**Tokenizer-free LLMs proven scalabe via NanoGPT (or smth similar)**

## Mech interp that fits 6 months part-time:
    - SAE feature transfer across fine-tunes: train SAEs on a small base model (Pythia-160m class), compare against instruction-tuned and LoRA-legal variants. Do features persist, rotate, or get reweighted? Single-GPU scale, genuinely open question.
    - Abstention/uncertainty direction in a post-trained legal LLM: find a linear direction, steer it, measure whether abstention on unanswerable legal QA improves without tanking accuracy. Small, safety-flavored, directly relevant to CAL.
**Replication + seed variance of a headline interp claim (induction-head necessity, some published circuit). Low novelty, near-zero risk of not finishing, legitimately useful to the field.**
    - Anthropic Jacobians (https://github.com/anthropics/jacobian-lens) + next steps + address criticism

## New Benchmark: Needs to be Domain-Niche
    - Benchmarks are very crowded
    - Spend time checking what is and isn't covered
    - We must know task very well
    - e.g. Code translation benchmark, new and novel benchmark
