# AI-era Engineering Competency Framework

## AECF v1.0

> This document defines a competency framework for evaluating engineering skills specific to the AI era. 
> It covers hiring, career development, and team capability assessment. It is not a certification standard. 
> Version numbers are meaningful and the changelog is maintained.

## Background and motivation


Most technical hiring frameworks were built for a world where the main engineering bottleneck was writing correct code quickly. That world has changed.

The majority of professional software engineers now use AI coding tools daily. The bottleneck isn't producing code anymore — it's evaluating it, making judgment calls about when to trust it, and designing systems that don't quietly break when the model gets something wrong.

Existing frameworks — SFIA, internal engineering ladders, technical interview question banks — haven't caught up. This document names the skills that have become critical on AI-first teams, with enough specificity to actually use in a hiring rubric or a performance review.

**What this covers:** Production engineering skills that predict whether someone is effective on a team building with AI. Specifically: the range above "has used ChatGPT" and below "trains foundation models from scratch."

**What this doesn't cover:** ML research, data science, AI product management, and general software engineering fundamentals. Those are prerequisites, not replacements.

---

## Structure

Five domains. Three proficiency levels.

### Proficiency levels

| Level | Label      | Description                                                                                                                           |
|-------|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| L1    | Emerging   | Aware of the skill. Can apply it with guidance. Still building intuition through exposure.                                            |
| L2    | Practicing | Applies it independently in routine situations. Recognizes the common failure modes. Brings it to their own work without being asked. |
| L3    | Leading    | Applies it in novel or ambiguous situations. Can calibrate others. Shapes how the team works around this skill.                       |

Where a skill is marked with a minimum level, candidates at that seniority band should demonstrate it at or above that level. L3-only skills are differentiators — their absence doesn't disqualify junior or mid candidates.

---

## Domain 1: AI output judgment

Can they tell when the AI is wrong?

This is the highest-signal domain in the framework. More than any other skill area, it predicts whether an engineer ships AI-assisted work that holds up in production — or work that looks fine until it doesn't.

### Skills

---

**1.1 Hallucination detection**  
*Expected at: L1 and above*

AI outputs can be fluent, confident, and wrong. This skill is catching that — hallucinated API methods, invented library functions, incorrect package names, fabricated citations, logical structures that are syntactically fine but do the wrong thing.

| Level | Indicator                                                                                                                                                                                                                |
|-------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| L1    | Catches obvious hallucinations (non-existent library methods) when explicitly looking for errors.                                                                                                                        |
| L2    | Proactively checks AI-generated code against actual docs for libraries they know. Flags when they're in unfamiliar territory and can't verify.                                                                           |
| L3    | Has built up a mental model of where different models tend to hallucinate. Can predict likely failure points from the prompt context alone. Designs review processes that catch this systematically rather than on luck. |

---

**1.2 AI code review**  
*Expected at: L2 and above*

AI code has its own failure patterns — different from the bugs humans write, and not well-caught by standard review practices. Over-engineered solutions that miss the actual context. Security patterns that are textbook-correct but wrong for the threat model. Error handling that silently swallows failures. Off-by-ones at boundary conditions. Sections of generated code that make conflicting assumptions because they were written from different prompt contexts.

Reviewing AI code well means applying a distinct posture, not just running the same checklist.

| Level | Indicator                                                                                                                                   |
|-------|---------------------------------------------------------------------------------------------------------------------------------------------|
| L1    | Reviews AI code the same way they'd review a human-authored PR. Hasn't yet built up a separate mental model for AI-specific failures.       |
| L2    | Approaches AI-generated code with calibrated skepticism. Checks for context-appropriateness, not just correctness.                          |
| L3    | Knows the AI failure pattern taxonomy well enough to move fast without missing things. Has contributed to team norms around AI code review. |

---

**1.3 Confidence calibration**  
*Expected at: L2 and above*

AI confidence and AI accuracy aren't the same thing. Models are often most confidently wrong in areas where they have just enough training data to pattern-match, but not enough to reason correctly. This skill is developing a working sense of when to trust the output and when to verify — and not treating "sounds right" as evidence.

| Level | Indicator                                                                                                                                                   |
|-------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| L2    | Has personal heuristics for trust levels by domain and task type. Doesn't accept outputs at face value.                                                     |
| L3    | Can articulate the calibration model clearly enough to teach it. Notices when the team as a whole is over- or under-trusting AI output and corrects for it. |

---

**1.4 Failure mode literacy**  
*Expected at: L3*

Knowing *why* models fail, not just *that* they fail. Training cutoff effects, context window degradation, prompt injection, sycophancy (the model agreeing with whatever the user implies), anchoring from early context, the difference between instruction-following and completion behavior.

| Level | Indicator                                                                                                                                                                                                  |
|-------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| L3    | Can explain the mechanism behind the major failure modes. Uses that understanding to design prompts, review processes, and systems that account for known weaknesses rather than just hoping for the best. |

---


## Domain 2: Prompt and context architecture

Can they build prompt systems that hold up in production?

There's a real difference between writing a prompt that works in one session and building a prompt system that works reliably at scale, doesn't drift as context changes, and can be tested and maintained by a team. This domain is about the latter.

### Skills

---

**2.1 Prompt engineering fundamentals**  
*Expected at: L1 and above*

Chain-of-thought structuring, few-shot example design, output format specification, constraint and persona setting. The building blocks.

| Level | Indicator                                                                                                                                       |
|-------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| L1    | Can write prompts that consistently produce the right output format for well-defined tasks.                                                     |
| L2    | Designs prompts with explicit reasoning structures. Makes deliberate choices about few-shot examples. Tests against edge cases before shipping. |
| L3    | Designs prompt systems — sequences, conditionals, fallbacks — rather than individual prompts. Thinks about how components interact.             |

---

**2.2 Context window management**  
*Expected at: L2 and above*

Context windows have limits, and model performance degrades as they fill up — not linearly, and not always in obvious ways. This skill is working within those constraints deliberately: prioritizing what goes in, building retrieval strategies that don't just dump everything available, and knowing when the approach needs to change.

| Level | Indicator                                                                                                                                  |
|-------|--------------------------------------------------------------------------------------------------------------------------------------------|
| L2    | Knows that long-context degradation is real and designs retrieval to account for it. Doesn't naively max out context.                      |
| L3    | Makes quantitative decisions about context allocation. Benchmarks performance at different utilization levels for their specific use case. |

---

**2.3 RAG pipeline design**  
*Expected at: L2 and above*

Building retrieval-augmented generation systems that stay accurate as source data changes. This means thinking through chunking strategy, embedding model selection, retrieval scoring, re-ranking, hybrid search, and what happens when the underlying data gets updated.

| Level | Indicator                                                                                                                                                                         |
|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| L2    | Can build a working RAG pipeline with standard tooling. Understands the tradeoffs between chunk size, retrieval precision, and context usage.                                     |
| L3    | Designs for reliability at scale. Benchmarks retrieval quality. Can debug RAG failures — wrong context, missing context, stale context — systematically rather than by guesswork. |

---

**2.4 Prompt versioning and governance**  
*Expected at: L3*

Prompts in production are code. They need version control, change tracking, regression tests, review processes, and deployment workflows. Teams that treat them as informal one-offs accumulate invisible debt that surfaces at the worst times.

| Level | Indicator                                                                                                                                                                                                            |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| L3    | Has implemented or pushed for prompt versioning infrastructure. Can describe, from experience, what breaks in systems where prompts aren't versioned. Contributes to team standards for prompt lifecycle management. |

---

## Domain 3: AI system design and architecture

Do they design for when the AI is wrong, not just for when it's right?

AI system design is its own thing — distinct from traditional system design and distinct from model development. It means incorporating non-deterministic components into otherwise deterministic systems, which creates architectural problems that standard frameworks don't have good answers for.

### Skills

---

**3.1 Human-in-the-loop design**  
*Expected at: L2 and above*

Knowing where human review needs to sit in an AI-assisted workflow, designing the escalation path, and calibrating how much automation is appropriate for a given consequence level. Full automation is not a default — it's a decision that should be justified.

| Level | Indicator                                                                                                                                                                                                           |
|-------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| L2    | Calls out human review requirements in design docs. Doesn't assume "we'll automate it" without thinking through what happens when the automation is wrong.                                                          |
| L3    | Designs tiered oversight models based on consequence severity. Quantifies the automation/error-rate tradeoff for the specific use case. Treats the escalation path as a first-class design problem, not a footnote. |

---

**3.2 Agent architecture**  
*Expected at: L3*

Multi-step agents fail in ways that single-turn AI calls don't - reasoning loops, tool misuse, context drift over long chains, conflicting outputs across steps. Building agents that actually complete tasks reliably means thinking through memory strategy (in-context vs. external), retry and circuit breaker logic, and how the thing fails gracefully when it goes off the rails.

| Level | Indicator                                                                                                                                                                                                                         |
|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| L3    | Has built multi-step agents that work in production, not just demos. Has a principled approach to memory architecture. Designs for the failure paths, not just the happy path. Can explain where their agent designs are fragile. |

---

**3.3 AI failure isolation**  
*Expected at: L2 and above*

When an AI call fails, that failure shouldn't take down the broader system. Circuit breakers, deterministic fallbacks, graceful degradation, explicit timeouts - these patterns exist for a reason, and they matter more with non-deterministic components than with anything else.

| Level | Indicator                                                                                                         |
|-------|-------------------------------------------------------------------------------------------------------------------|
| L2    | Designs AI integrations with explicit fallback paths. Treats AI calls as unreliable by default, not by exception. |
| L3    | Maps the full failure surface of AI components systematically. Reviews team designs for unhandled failure paths.  |

---

**3.4 Latency and cost modeling**  
*Expected at: L3*

AI API calls are expensive and slow compared to most things in a system. Modeling that before implementation - caching strategies, model routing, async patterns, cost monitoring - is the difference between a product that ships on budget and one that surprises everyone six months later.

| Level | Indicator                                                                                                                                                                                                 |
|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| L3    | Can estimate API costs for a given usage pattern before writing the implementation. Designs caching and routing to hit latency requirements. Has built or run cost monitoring for AI spend in production. |

---
