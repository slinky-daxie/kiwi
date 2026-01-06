# LLM Architecture Decision Log

*Agent-Assisted Customer Support System for Pineapple Travel*

---

## TL;DR (All Decisions)
- Use multiple models: fast GPT-4o mini for classification, Claude Sonnet for reasoning.
- RAG over fine-tuning for MVP; open-source embeddings; hybrid (vector + keyword) search.
- Human-in-the-loop for MVP; full decision trace; three-tier confidence signals.
- Prompt-injected rule book (editable, auditable) instead of hard-coded validation.

---

## Decision 1: Multi-Model Strategy (Not Single LLM)

**Date**: January 2026  
**Status**: Proposed for MVP

### Context
Different steps need different qualities (speed, cost, deep reasoning).

### Decision
Use specialised LLMs: GPT-4o mini for classification; Claude Sonnet for reasoning; open-source embeddings for retrieval.

### Rationale (short)
- Optimises speed + cost for high-volume tasks.
- Keeps best-quality model for complex reasoning.
- Adds some operational complexity.

---

## Decision 2: Claude Sonnet for Resolution Reasoning

**Date**: January 2026  
**Status**: Proposed for MVP

### Context
Core engine must handle multi-constraint travel resolutions with explainability.

### Decision
Use Claude 3.5 Sonnet as the primary reasoning engine.

### Rationale (short)
- Strong chain-of-thought and structured outputs.
- Better at explaining decisions (needed for compliance/trust).
- Higher cost than GPT-4o, justified for this critical step.

---

## Decision 3: RAG Over Fine-Tuning for MVP

**Date**: January 2026  
**Status**: Proposed for MVP

### Context
Need to inject policies, laws, and historical cases without large training data.

### Decision
Use retrieval-augmented generation; defer fine-tuning to a later phase.

### Rationale (short)
- Update policies instantly without retraining.
- Citable sources increase transparency.
- Fine-tuning can wait until we have real labelled data.

---

## Decision 4: Open-Source Embeddings (Not OpenAI)

**Date**: January 2026  
**Status**: Proposed for MVP

### Context
Need embeddings for policies and cases; want low cost and data control.

### Decision
Host open-source embeddings (e.g., bge-large-en-v1.5) internally.

### Rationale (short)
- Zero API cost, better data privacy.
- Modern open-source quality is sufficient.
- Requires minimal infra to host.

---

## Decision 5: Hybrid Search (Vector + Keyword)

**Date**: January 2026  
**Status**: Proposed for MVP

### Context
Queries mix semantic intent and exact terms (flight numbers, booking IDs).

### Decision
Use hybrid search: vector similarity + keyword (BM25) with score fusion.

### Rationale (short)
- Covers both semantic and exact-match needs.
- Improves recall vs either method alone.
- Minor latency overhead acceptable.

---

## Decision 6: Human-in-the-Loop for All MVP Decisions

**Date**: January 2026  
**Status**: Proposed for MVP

### Context
Need trust, safety, and learning before any autonomy.

### Decision
All LLM suggestions require agent approval in MVP.

### Rationale (short)
- Builds agent trust and accountability.
- Collects high-quality training data.
- Avoids costly mistakes while models are new.

---

## Decision 7: Full Decision Trace (Not Summary)

**Date**: January 2026  
**Status**: Proposed for MVP

### Context
Explainability, audit, and improvement need full visibility.

### Decision
Log the complete trace: inputs, retrieved policies, prompts, responses, reasoning, confidence, human action, outcome.

### Rationale (short)
- Essential for compliance and debugging.
- Creates training data for future improvements.
- Storage cost is negligible relative to value.

---

## Decision 8: Confidence Thresholds (Not Binary)

**Date**: January 2026  
**Status**: Proposed for MVP

### Context
Agents need to know when to trust vs scrutinise LLM output.

### Decision
Three-tier confidence signals: 🟢 High, 🟡 Medium, 🔴 Low.

### Rationale (short)
- Guides agent attention and review depth.
- Supports future selective automation.
- Simple enough to be usable.

---

## Decision 9: Prompt-Injected Rule Book (Not Hard-Coded Validation)

**Date**: January 3, 2026  
**Status**: Proposed for MVP

### Context
LLM must follow policies/guarantee/legal rules, but rules change often.

### Decision
Inject a version-controlled rule book into the prompt instead of hard-coding validation.

### Rationale (short)
- Update rules in minutes without code deploys.
- Auditable and testable; LLM can cite rules.
- Slightly weaker enforcement than hard-coded, but far more flexible for MVP iteration.

---

## Future Decisions (To Be Made)

### Fine-Tuning Strategy (Phase 2)
- When to fine-tune vs continue with RAG?
- Which base model to fine-tune?
- How much training data is enough?
- How to maintain fine-tuned models?

### Autonomous Resolution Criteria (Phase 2)
- Which case types eligible for autonomy?
- What confidence threshold for auto-resolution?
- How to handle customer override ("I want a human")?
- Error budget for autonomous decisions?

### Multi-Language Support (Phase 3)
- Translate policies or use multilingual models?
- Which languages to prioritise?
- How to maintain quality across languages?

### Advanced Features (Future)
- Sentiment analysis for escalation?
- Customer intent prediction?
- Proactive issue detection before customer contact?
- Predictive rebooking for likely-to-miss connections?

---

## Decision Framework Template

For future decisions, use this structure:

```markdown
## Decision N: [Title]

**Date**: [Date]  
**Status**: [Proposed/Approved/Implemented/Deprecated]

### Context
[What problem are we solving? What are the constraints?]

### Decision
[What did we decide? Be specific.]

### Rationale
[Why this decision? What evidence supports it?]
```

