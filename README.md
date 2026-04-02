# AI-era Engineering Competency Framework (AECF)

**v1.0 · CC BY 4.0 · Open to contributions**

---

Most technical hiring rubrics were written before engineers spent half their day working alongside AI. 
They test whether candidates can write code from scratch. That's the wrong question in 2026.

The right questions: can they tell when AI is wrong? Can they design a system that fails gracefully when the model misbehaves? 
Can they build prompt systems that hold up in production rather than drift into inconsistency over months?

These are skills that almost nobody is hiring against, because nobody had named them clearly enough to put on a scorecard. 
This is an attempt to fix that.

---
## What's in here [Work in Progress]

**[AECF_V1.md](./framework.md)** - the framework document. Designed to be used as a hiring rubric, a career ladder input, or a self-assessment tool.

Domains:

1. **AI output judgment** - can they tell when AI is wrong before it ships?
2. **Prompt and context architecture** - can they build prompt systems that hold up in production?
3. **AI system design** - do they design for AI failure, not just AI success?

Each skill has L1 (emerging) / L2 (practicing) / L3 (leading) descriptors. 
The intent is that you can look at a specific skill and know which level descriptor matches a candidate's actual behavior - not their stated familiarity.

---

## How to use it

**In interviews:** Map the role's AI interaction level to the relevant domains. Design at least one scenario per domain — ideally putting a real AI artifact in front of the candidate and watching what they do with it, rather than asking them to describe their experience.

**In career ladders:** The L1/L2/L3 structure maps onto most existing junior/mid/senior bands. Take the 2–3 domains most relevant to your team's work and add them as explicit dimensions in your promotion criteria.

**In job descriptions:** The skill names and descriptors are intentionally specific enough to copy directly. "Demonstrates L2 AI output judgment" means something concrete; "experience with AI tools" doesn't.

**For self-assessment:** Read each level descriptor and ask which one matches what you actually do, not what you could do if you paid more attention. The most common error is conflating exposure with competency.

---

## What this isn't

It doesn't cover ML research, model training, or data science. 
It doesn't try to replace foundational software engineering evaluation - data structures, system design, and programming fundamentals are prerequisites for this framework, not alternatives to it. 
It doesn't name specific tools, because tool knowledge is volatile and the skills here should transfer as the tooling landscape shifts.

---

## Version and status

This is v1.0. The version number matters - when skill definitions change or domains are restructured, the version increments and the changelog explains what changed and why.

The framework will be wrong in places. Practitioners who work on AI-first engineering teams daily have more empirical data about what predicts performance than any document written from the outside. 
If a descriptor doesn't match what you actually see in strong engineers, open an issue and say so.

---

## Contributing

Open an issue if:
- A skill descriptor doesn't match your experience of what L2 actually looks like
- A skill is missing that you consistently hire against
- A domain doesn't apply cleanly to your team's context and you can explain why

Fork this repo and open a pull request if you want to propose specific language changes. 
Contributions from practitioners who can point to real hiring or development decisions behind their suggestions carry the most weight.

---

## License

CC BY 4.0. Use it for any purpose, including commercially. Attribution required - if you adapt it, indicate what changed.

Full license: https://creativecommons.org/licenses/by/4.0/

---

## Background

I'm a software engineer who uses AI coding tools every day - Copilot, Claude, Cursor, Devin. 
I've watched my own workflow change significantly over the past two years, and noticed that the skills that make me effective with AI are almost entirely different from the skills that got me hired.

I got curious whether anyone had written down what those skills actually are, specifically enough to be useful. Not "knows how to prompt" or "experience with LLMs" — actual competency descriptors you could use in a rubric or a performance review. 
I couldn't find anything that wasn't either too vague or too focused on ML research roles.

So I wrote this. It's a practitioner's attempt to name what good looks like for engineers who work with AI daily, not engineers who build AI.
