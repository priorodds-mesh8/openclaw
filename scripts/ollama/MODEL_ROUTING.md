# MODEL_ROUTING.md - Your Personal Model Routing System

**Last updated:** 2026-03-29
**Status:** Active & Validated
**System:** Ollama (Qwen) → Haiku → Opus/Sonnet

---

## Your Routing Decision Tree

### Tier 1: Ollama Qwen 2.5 7B (Local, $0)
**When to use:** ~70% of daily tasks

**Decision criteria (all must be true):**
- ✓ No multi-step orchestration needed
- ✓ No external API calls
- ✓ No deep domain reasoning required
- ✓ Task is deterministic or pattern-matching

**Task types:**
- Text summarization & extraction
- Brainstorming & ideation
- Content drafting (emails, social, markdown)
- Code snippets (non-architectural)
- Text analysis & tagging
- Formatting & cleanup
- JSON/YAML parsing

**Example prompts:**
- "Summarize this article in 2 sentences"
- "Extract all email addresses from this text"
- "Draft a professional email response to this message"
- "What are the key takeaways from this document?"

**Latency:** <1 second
**Token cost:** $0 (local compute)
**Quality level:** Good (7B model is surprisingly capable)

---

### Tier 2: Claude Haiku 4.5 (Cloud, ~$3/M input)
**When to use:** ~25% of daily tasks

**Decision criteria (at least one must be true):**
- ✓ Multi-step orchestration (combine results from multiple sources)
- ✓ Tool routing (decide which API/tool to call)
- ✓ Intermediate reasoning (2-3 steps, not complex)
- ✓ API coordination (fetch data, transform, return)

**Task types:**
- Orchestrating multiple tools/APIs
- Making routing decisions
- Combining data from different sources
- Simple reasoning chains (2-3 steps)
- Filtering/ranking tasks
- Heartbeat analysis (what changed?)

**Example prompts:**
- "Search for X, fetch Y, combine results in format Z"
- "Route this request to the appropriate handler"
- "Compare these 3 options and recommend the best"
- "Did anything new appear since the last check?"

**Latency:** 2-5 seconds
**Token cost:** ~$0.80/M input, ~$2.40/M output
**Quality level:** Reliable, fast, affordable

---

### Tier 3: Claude Opus 4.6 or Sonnet 4.0 (Cloud, $3-15/M input)
**When to use:** ~5% of daily tasks

**Decision criteria (at least one must be true):**
- ✓ Deep domain expertise needed (GTM, strategy, architecture)
- ✓ Complex multi-step reasoning (4+ steps)
- ✓ Novel problem-solving (no clear precedent)
- ✓ High-stakes decision (accuracy critical)
- ✓ Strategic insight required
- ✓ Systems thinking needed

**Task types:**
- GTM strategy & architecture
- Complex reasoning problems
- Strategic decision-making
- Novel problem analysis
- Deep technical architecture
- Complex writing (long-form, nuanced)

**Example prompts:**
- "What are failure modes in agentic lead qualification?"
- "Design a GTM system for product X"
- "Analyze the strategic implications of this market shift"
- "How do we validate agent quality without human review?"

**Latency:** 5-15 seconds
**Token cost:** ~$3/M input (Sonnet), ~$15/M input (Opus)
**Quality level:** Best-in-class, worth the cost

---

## Token Budget & Tracking

**March 2026 (Before Optimization):**
- Total tokens: 45,000,000
- Broken down: Mostly Haiku, some Opus
- Problem: Routing routine tasks through Haiku

**Projected (After Optimization):**
- Ollama work (70%): 0 tokens
- Haiku work (25%): ~7,500,000 tokens
- Opus/Sonnet work (5%): ~4,000,000 tokens
- **Total: ~11,500,000 tokens**
- **Savings: ~74% reduction**

**Monthly cost comparison:**
- Before: ~$22/month (Haiku + Opus)
- After: ~$6/month (Haiku + Opus, less volume)
- **Savings: ~$16/month**

---

## How to Use This System

**Step 1: Assess the task**
- Does it need multi-step orchestration? → Haiku
- Does it need domain reasoning? → Opus/Sonnet
- Otherwise → Ollama

**Step 2: Check the decision criteria above**
- If multiple criteria match, escalate to higher tier
- When in doubt, escalate (better to overshoot than undershoot)

**Step 3: Execute & feedback**
- If result is mediocre from lower tier, escalate next time
- If higher tier was overkill, try lower tier next time
- Track the pattern in your head (or update this file)

---

## Escalation Rules (When to Move Up Tiers)

**Ollama → Haiku when:**
- Task requires connecting multiple information sources
- Multiple decisions need to happen in sequence
- External API calls are involved
- Result quality is mediocre

**Haiku → Opus when:**
- Task requires domain-specific expertise you lack
- Multiple reasoning steps (>3) needed
- Result is used for high-stakes decisions
- Task is novel (no clear precedent)

---

## Fallback Rules (When to Move Down Tiers)

**Opus → Haiku when:**
- Task is actually simpler than expected
- You realize it's just routing/orchestration
- Cost is high relative to value delivered

**Haiku → Ollama when:**
- Task is just summarization or text analysis
- No multi-step orchestration is really needed
- Turnaround time is not critical

---

## Real-World Examples

### Example 1: "Summarize this article"
- Decision: Routine task, no orchestration
- **→ Ollama**
- Tokens: 0

### Example 2: "Search for articles on X, summarize all of them, rank by relevance"
- Decision: Multi-step (search → summarize → rank)
- **→ Haiku** (orchestration)
- Tokens: ~200

### Example 3: "I'm designing an agentic GTM system. What are the failure modes? How do we validate quality?"
- Decision: Domain expertise (GTM), complex reasoning, strategic
- **→ Opus**
- Tokens: ~400

### Example 4: "Check my reminders for new items since the last check"
- Decision: Filtering/comparison, simple logic
- **→ Ollama** (local analysis)
- Tokens: 0

### Example 5: "Create a content calendar for Q2 based on our market analysis and upcoming events"
- Decision: Strategy, planning, domain knowledge
- **→ Sonnet or Opus**
- Tokens: ~300-500

---

## Tuning Parameters (Adjust Over Time)

**Ollama thresholds:**
- Accuracy threshold: If Qwen gets >85% right on similar tasks, keep routing there
- Latency threshold: <2 seconds acceptable for routine work
- Complexity threshold: Max 1-step tasks (input → output)

**Haiku thresholds:**
- Orchestration complexity: Up to 3-step chains comfortable
- Cost tolerance: >$1 per task? Escalate to Opus
- Latency: 2-5 seconds acceptable for coordination

**Opus/Sonnet thresholds:**
- Use case confidence: Only when >80% sure it needs reasoning
- Cost justification: Must add clear value
- Fallback: Always available for hard problems

---

## Integration with OpenClaw

**In your sessions:**
- I (Merlin) will route according to this system
- You can override: `/opus`, `/haiku`, `/qwen` to force a model
- I'll flag when I'm uncertain about routing

**In heartbeat checks:**
- Ollama analyzes locally (state tracking)
- Escalate to Claude only if something actually changed

**In skill creation & publishing:**
- Use Ollama for drafting/organizing
- Use Haiku for orchestration of multiple steps
- Use Opus for strategic decisions about skill design

---

## Validation & Testing

See TEST_ROUTING.md for:
- ✅ Simple math (Ollama)
- ✅ Summarization (Ollama)
- ✅ Complex reasoning (Opus)
- ✅ Heartbeat filtering (Ollama)

All tests passed. System is working as designed.

---

## When to Revisit This

- Monthly: Review token usage vs. projections
- Quarterly: Reassess thresholds based on actual results
- Ad-hoc: When you find yourself consistently escalating/de-escalating

Update this file as you learn what works for your workflows.
