---
name: grill-with-docs
description: A guided design interview that explains decisions, stress-tests the plan, and records domain language and ADRs.
disable-model-invocation: true
---

Read and follow `skill://grilling` and `skill://domain-modeling`.

Adapt the interview for a non-expert decision-maker:

- Ask one question per round by default. Ask at most two when both are independent and need only short explanations.
- Present each question in this order:
  1. **Question** — state the undecided decision in one sentence.
  2. **Why** — explain why it matters, followed by one short, neutral example.
  3. **Concepts** — define only unfamiliar terms required to answer; omit this section when none are needed.
  4. **Options** — state the practical consequence of each option.
  5. **Recommendation** — recommend the option that best fits the user's stated goal, including the reason and assumptions.
- Ground examples in verified project facts when available. Otherwise label the example **Hypothetical** and use it only to explain, not as evidence.
- Treat confusion as an unsettled prerequisite: explain the missing concept, then re-ask instead of advancing.
- Record glossary terms and ADRs only after the user answers without unresolved confusion.
