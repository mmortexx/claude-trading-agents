# Contributing to claude-trading-agents

We welcome contributions that improve the committee's rigor, add missing domain expertise, or fix bugs in agent logic.

---

## Types of Contributions

### 1. New Agent
- Domain expertise not covered by existing 24 agents
- Must have institutional background (ex-hedge fund, exchange, data vendor)
- Must define specific veto criteria (3 minimum)
- Must specify coordination rules with existing agents

### 2. Enhanced Veto Criteria
- Add specific thresholds to existing criteria
- Must include empirical justification
- Must not contradict existing committee rules

### 3. New Cross-Domain Rule
- Coordination rules, escalation paths
- Requires approval from both affected domain auditors

### 4. Documentation
- Fix unclear descriptions
- Improve examples
- Add usage patterns from real deployments

---

## Not Accepted

- Agents without institutional background
- Criteria that weaken existing vetoes
- Personal trading strategies as "evidence"
- Blog posts as peer-review substitutes

---

## Process

1. **Fork** this repo
2. Create a branch: `agent/[domain]` or `fix/[issue]`
3. Add agent or modify criteria
4. Submit PR with:
   - Rationale for change
   - Affected agents (coordination matrix update)
   - New veto criteria if applicable
5. Two approvals from auditors required before merge

---

## Quality Standards

All agent descriptions must include:
- Formal institutional background
- ≥3 specific veto criteria
- ≥2 coordination rules
- Formal audit output format
- Examples of when to invoke

See any existing agent in `agents/AUDITORS/` as template.
